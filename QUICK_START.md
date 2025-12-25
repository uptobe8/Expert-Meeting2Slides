# 🚀 Quick Start - 5 Minutos

## Paso 1: Clonar el Repo (1 min)

```bash
git clone https://github.com/tu-usuario/meeting-to-presentation-app.git
cd meeting-to-presentation-app
```

## Paso 2: Instalar Dependencias (2 min)

```bash
pnpm install
# Si no tienes pnpm: npm install -g pnpm
```

## Paso 3: Configurar API Keys (1 min)

Copia `.env.example` a `.env.local`:
```bash
cp .env.example .env.local
```

Edita `.env.local` y añade tus claves:
```
NEXT_PUBLIC_ANTHROPIC_API_KEY=sk-ant-...
ANTHROPIC_API_KEY=sk-ant-...
NEXT_PUBLIC_FAL_KEY=...
NEXT_PUBLIC_SUPABASE_URL=...
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
```

### Cómo obtener las claves:

**Anthropic (Claude):**
1. Ve a [console.anthropic.com](https://console.anthropic.com)
2. Signup/Login
3. API keys → Create Key
4. Copia la clave

**FAL AI:**
1. Ve a [fal.ai](https://www.fal.ai)
2. Signup
3. Account → API Keys
4. Copia la clave

**Supabase:**
1. Ve a [supabase.com](https://supabase.com)
2. Create new project
3. Settings → API → URL y anon key
4. Copia ambas

## Paso 4: Ejecutar (1 min)

```bash
pnpm dev
```

Abre: http://localhost:3000

## ¿Qué hacer ahora?

1. **Prueba la app:**
   - Completa el formulario
   - Sube una transcripción
   - Observa las diapositivas generarse

2. **Explora el código:**
   - `app/page.tsx` - página principal
   - `components/presentation-form.tsx` - formulario
   - `app/api/process-transcript/route.ts` - lógica Claude

3. **Desplegar:**
   - Ve a [DEPLOYMENT.md](./DEPLOYMENT.md)
   - Vercel recomendado (gratuito)

## Troubleshooting

**Error: Cannot find module**
```bash
rm -rf node_modules pnpm-lock.yaml
pnpm install
```

**Error: API key not found**
→ Verifica .env.local tiene todas las claves

**Puerto 3000 ya en uso**
```bash
pnpm dev -p 3001
```

## Soporte

- Docs: [README.md](./README.md)
- Deployment: [DEPLOYMENT.md](./DEPLOYMENT.md)
- Issues: GitHub Issues

---

¡Listo! Tu app estará corriendo en 5 minutos. 🎉
