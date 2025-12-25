# Meeting to Presentation App

> Convierte reuniones y transcripciones en presentaciones profesionales con IA, imágenes automáticas y PDF descargable.

## Características

- ✨ Generación automática de diapositivas desde transcripciones
- 🎨 Generación de imágenes con IA (Flux Schnell)
- 📊 Diseño profesional con Tailwind CSS
- 🤖 Orquestación con Claude Sonnet 4 (Anthropic)
- 🖼️ Vista previa en tiempo real
- 📥 Descarga en PDF

## Requisitos Previos

- Node.js 18+ 
- pnpm (o npm/yarn)
- Claves API:
  - **Anthropic API** (para procesamiento de transcripción)
  - **FAL AI** (para generación de imágenes con Flux)
  - **Supabase** (para almacenamiento de imágenes)

## Instalación Local

```bash
# 1. Clonar repositorio
git clone https://github.com/tu-usuario/meeting-to-presentation-app.git
cd meeting-to-presentation-app

# 2. Instalar dependencias
pnpm install

# 3. Crear .env.local con tus claves
cp .env.example .env.local

# 4. Ejecutar dev server
pnpm dev
```

## Variables de Entorno (.env.local)

```
# Anthropic (Claude)
NEXT_PUBLIC_ANTHROPIC_API_KEY=sk-ant-...
ANTHROPIC_API_KEY=sk-ant-...

# FAL AI (Generación de imágenes)
NEXT_PUBLIC_FAL_KEY=<tu-fal-key>

# Supabase (Almacenamiento)
NEXT_PUBLIC_SUPABASE_URL=https://...supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbG...
```

## Estructura del Proyecto

```
meeting-to-presentation-app/
├── app/
│   ├── api/
│   │   ├── process-transcript/    # Procesa transcripción → estructura de slides
│   │   ├── generate-images/       # Genera imágenes con IA
│   │   └── generate-pdf/          # Convierte HTML a PDF
│   ├── page.tsx                   # Página principal
│   ├── layout.tsx
│   └── globals.css
├── components/
│   ├── presentation-form.tsx      # Formulario principal
│   ├── progress-checklist.tsx     # Checklist de pasos
│   ├── app-header.tsx
│   └── ui/                        # Componentes shadcn/ui
├── lib/
│   ├── supabase/                  # Cliente Supabase
│   └── utils.ts
├── public/                        # Assets estáticos
└── package.json
```

## Flujo de Funcionamiento

```
1. Usuario ingresa:
   ├── Prompt del sistema
   ├── Orientación de contenido
   ├── Estilo visual
   └── Transcripción (o URL de audio)

2. /api/process-transcript:
   └── Claude Sonnet 4 procesa → estructura JSON de slides

3. /api/generate-images:
   └── FAL Flux genera imagen para cada diapositiva

4. UI muestra:
   ├── Vista previa en tiempo real
   ├── Galería de imágenes
   └── Botón "Descargar PDF"

5. /api/generate-pdf:
   └── Convierte HTML presentación → PDF descargable
```

## Despliegue en GitHub Pages

**Nota:** Este es un app Next.js con rutas API. GitHub Pages es estático, por lo que necesitas:

### Opción A: Vercel (RECOMENDADO - Gratis)

```bash
# 1. Push a GitHub
git push origin main

# 2. Conectar a Vercel
# - Ve a vercel.com
# - Importa el repositorio
# - Añade las ENV vars
# - Deploy automático

# Vercel desplegará y dará URL pública
```

### Opción B: GitHub Pages (requiere ajustes)

Para usar GitHub Pages con rutas API:

```bash
# 1. Instalar @vercel/serverless
pnpm add --save-dev @vercel/serverless

# 2. Cambiar next.config.mjs para exportar estático
# (Nota: Esto requiere refactorizar API routes a edge functions)

# 3. Configurar gh-pages en package.json:
"scripts": {
  "deploy": "pnpm build && gh-pages -d out"
}

pnpm deploy
```

## Configuración Variables de Entorno en GitHub

**Si usas Vercel (RECOMENDADO):**

1. Ve a tu proyecto en Vercel
2. Settings → Environment Variables
3. Añade:
   - `NEXT_PUBLIC_ANTHROPIC_API_KEY`
   - `ANTHROPIC_API_KEY`
   - `NEXT_PUBLIC_FAL_KEY`
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`

**Si usas GitHub Secrets:**

1. Ve a tu repo → Settings → Secrets and variables → Actions
2. Crea cada variable con `REPO_` prefix

## Desarrollo Local

```bash
# Terminal 1: Dev server
pnpm dev
# Abre http://localhost:3000

# Terminal 2 (opcional): Tipo checking
pnpm type-check

# Ejecutar tests
pnpm test

# Build para producción
pnpm build
pnpm start
```

## APIs Usadas

### Anthropic Claude Sonnet 4
- **Función:** Procesar transcripción → estructura de slides
- **Endpoint:** `/api/process-transcript`
- **Docs:** https://docs.anthropic.com

### FAL Flux Schnell
- **Función:** Generar imágenes con IA
- **Endpoint:** `/api/generate-images`
- **Docs:** https://www.fal.ai

### Supabase Storage
- **Función:** Almacenar imágenes generadas
- **Docs:** https://supabase.com/docs

## Solución de Problemas

### Error: "API key not found"
→ Verifica que .env.local tiene las claves correctas

### Error: "Failed to generate image"
→ Revisa que la cuenta FAL tiene créditos disponibles

### PDF no se descarga
→ Verifica que /api/generate-pdf está retornando blob correcto

## Contribuyendo

1. Fork el repositorio
2. Crea rama: `git checkout -b feature/tu-feature`
3. Commit: `git commit -m "Add feature"`
4. Push: `git push origin feature/tu-feature`
5. Open Pull Request

## Licencia

MIT

## Autor

Creado por ti con IA | Diciembre 2025

## Links Útiles

- [Next.js Docs](https://nextjs.org/docs)
- [Anthropic API](https://docs.anthropic.com)
- [FAL Flux](https://www.fal.ai)
- [Supabase](https://supabase.com)
- [Tailwind CSS](https://tailwindcss.com)
