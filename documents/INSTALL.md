# 📝 Guía de Instalación de Dependencias

## Dependencias Requeridas

Para usar esta plantilla completamente, necesitas instalar las siguientes dependencias:

### 1. Instalación Básica
```bash
npm install
```

### 2. Firebase (Backend as a Service)
```bash
npm install firebase
```

**Servicios disponibles:**
- Authentication (Google, Email, Facebook, etc.)
- Firestore (Base de datos NoSQL)
- Storage (Almacenamiento de archivos)
- Analytics
- Cloud Functions

### 3. Supabase (Alternativa Open Source)
```bash
npm install @supabase/supabase-js
```

**Servicios disponibles:**
- Authentication
- PostgreSQL Database
- Storage
- Real-time subscriptions
- Edge Functions

### 4. Tailwind CSS (Framework de CSS)
```bash
npm install -D tailwindcss postcss autoprefixer
```

### 5. PWA (Progressive Web App)
```bash
npm install -D vite-plugin-pwa
```

## 🚀 Instalación Completa (Comando Único)

Ejecuta este comando para instalar todo de una vez:

```bash
npm install && npm install firebase @supabase/supabase-js tailwindcss postcss autoprefixer vite-plugin-pwa -D
```

## ⚙️ Configuración Post-Instalación

### 1. Crear archivo de variables de entorno
```bash
cp .env.example .env.local
```

### 2. Configurar Firebase
- Ve a https://console.firebase.google.com/
- Crea un proyecto
- Copia las credenciales al archivo `.env.local`

### 3. Configurar Supabase
- Ve a https://supabase.com/
- Crea un proyecto
- Copia la URL y la API Key al archivo `.env.local`

### 4. Generar iconos PWA
Necesitarás crear dos iconos:
- `icon-192x192.png` (192x192px)
- `icon-512x512.png` (512x512px)

Colócalos en la carpeta `/public/`

## 🧪 Verificar Instalación

```bash
# Verificar que todo funcione
npm run dev
```

## 📦 Dependencias del package.json

Después de la instalación completa, tu `package.json` debería tener:

```json
{
  "dependencies": {
    "react": "^19.1.1",
    "react-dom": "^19.1.1",
    "firebase": "^latest",
    "@supabase/supabase-js": "^latest"
  },
  "devDependencies": {
    "tailwindcss": "^latest",
    "postcss": "^latest",
    "autoprefixer": "^latest",
    "vite-plugin-pwa": "^latest",
    "@vitejs/plugin-react": "^5.0.4",
    "typescript": "~5.9.3",
    "vite": "^7.1.7"
  }
}
```

## ❓ Problemas Comunes

### Error: Cannot find module 'firebase'
```bash
npm install firebase
```

### Error: Cannot find module '@supabase/supabase-js'
```bash
npm install @supabase/supabase-js
```

### Tailwind no funciona
```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

## 🔄 Actualizar Dependencias

Para mantener todo actualizado:

```bash
# Ver dependencias desactualizadas
npm outdated

# Actualizar todas las dependencias
npm update

# O usar npm-check-updates
npx npm-check-updates -u
npm install
```

## 💡 Notas Importantes

- **Firebase** y **Supabase**: Puedes usar uno u otro, o ambos
- **Tailwind**: Es opcional, puedes usar solo CSS con variables
- **PWA**: Recomendado para aplicaciones móviles
- Todas las dependencias de desarrollo (`-D`) no se incluyen en el build de producción

## 📚 Recursos Adicionales

- [Firebase Docs](https://firebase.google.com/docs)
- [Supabase Docs](https://supabase.com/docs)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [PWA Guide](https://web.dev/progressive-web-apps/)
