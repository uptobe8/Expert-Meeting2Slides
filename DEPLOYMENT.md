# Guía de Despliegue Completa

## Opción 1: Vercel (RECOMENDADO)

### Por qué Vercel?
- ✅ Soporte nativo para Next.js
- ✅ Serverless functions sin configuración
- ✅ Dominio gratuito
- ✅ Variables de entorno seguras
- ✅ Despliegue automático desde GitHub
- ✅ Gratis para uso personal/pequeño

### Pasos

**1. Preparar repositorio**
```bash
git init
git add .
git commit -m "Initial commit"
git push -u origin main
```

**2. Conectar a Vercel**
- Ve a [vercel.com](https://vercel.com)
- Click "New Project"
- Selecciona "Import Git Repository"
- Conecta tu cuenta GitHub
- Selecciona el repositorio

**3. Configurar variables de entorno**
En Vercel dashboard:
- Environment Variables
- Añade cada variable:
  - `NEXT_PUBLIC_ANTHROPIC_API_KEY`
  - `ANTHROPIC_API_KEY`
  - `NEXT_PUBLIC_FAL_KEY`
  - `NEXT_PUBLIC_SUPABASE_URL`
  - `NEXT_PUBLIC_SUPABASE_ANON_KEY`

**4. Deploy**
- Click "Deploy"
- Vercel construye y despliega automáticamente
- Tu app estará en: `https://tu-proyecto.vercel.app`

**5. Futuros despliegues**
Automáticos cuando hagas push a main

---

## Opción 2: GitHub Pages + Actions (Avanzado)

**Nota:** GitHub Pages es solo estático. Las API routes necesitan transformarse a Edge Functions o usar un servicio externo.

### Usando Netlify (alternativa más fácil que GitHub Pages)

```bash
# 1. Instalar CLI de Netlify
npm install -g netlify-cli

# 2. Conectar
netlify login

# 3. Deploy
netlify deploy --prod

# Configurar en Netlify UI:
# - Environment variables
# - Build command: pnpm build
# - Publish directory: .next
```

---

## Opción 3: AWS/Azure/GCP (Profesional)

Para producción a escala mayor:

```
AWS:
- App Runner (fácil) o
- ECS/Fargate + ALB o
- EC2 + GitHub Actions

Azure:
- App Service
- Container Instances

GCP:
- Cloud Run
- App Engine
```

---

## Configuración de Dominio Personalizado

### En Vercel (más fácil):
1. Settings → Domains
2. Añade tu dominio
3. Vercel te da instrucciones DNS
4. Apunta tu registrar a Vercel nameservers

### En Netlify:
1. Domain settings
2. Configura DNS o usa CNAME

---

## Actualizar el Deploy

Después de hacer cambios:

```bash
# Local
git add .
git commit -m "Update feature"
git push origin main

# Automático:
# - Vercel detecta push
# - Inicia build automático
# - Despliega a producción

# Ver logs:
# Vercel dashboard → Deployments → Ver logs
```

---

## Troubleshooting

### Build falla con "API key not found"
→ Verifica que las ENV vars están en el proyecto Vercel

### Timeout en API calls
→ Aumenta timeout en next.config.mjs

### Imágenes no se cargan
→ Revisa que Supabase URL y claves son correctas

### PDF no funciona
→ Verifica permisos de Supabase Storage

---

## Monitoreo

Vercel proporciona:
- Analytics (visitas, performance)
- Error tracking
- Performance monitoring

Netlify proporciona:
- Build logs
- Deploy history
- Analytics

---

## Próximos Pasos

1. **Custom domain**: Compra un .com
2. **SSL/HTTPS**: Automático en Vercel/Netlify
3. **CI/CD mejorado**: Añade checks antes de deploy
4. **Monitoreo**: Sentry para error tracking
5. **Backup**: GitHub como single source of truth
