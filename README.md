# 🚀 Plantilla Base - Template

Plantilla profesional para iniciar proyectos web con React, TypeScript, Firebase, Supabase y PWA.

## 📋 Tabla de Contenidos

- [Características](#-características)
- [Tecnologías](#-tecnologías)
- [Instalación](#-instalación)
- [Configuración](#-configuración)
- [Estructura](#-estructura-del-proyecto)
- [Sistema de Colores](#-sistema-de-colores)
- [Guía para Proyectos Grandes](#-guía-para-proyectos-grandes)

## ✨ Características

- ⚡ **Vite** - Build tool ultrarrápido
- ⚛️ **React 19** - Última versión con todas las mejoras
- 🔷 **TypeScript** - Tipado estático
- 🎨 **Sistema de Colores** - Paleta centralizada y personalizable
- 💨 **Tailwind CSS** - Framework de utilidades CSS
- 🔥 **Firebase** - Backend as a Service (Auth, Firestore, Storage)
- 🗄️ **Supabase** - Backend alternativo open-source
- 📱 **PWA Ready** - Progressive Web App con Service Worker
- 🌓 **Modo Oscuro** - Soporte automático para dark mode
- 📦 **Componentes** - Footer reutilizable incluido
- 🏗️ **Arquitectura Escalable** - Estructura organizada para proyectos grandes

## 🛠️ Tecnologías

- React 19.1.1
- TypeScript 5.9.3
- Vite 7.1.7
- Tailwind CSS (latest)
- Firebase (latest)
- Supabase (latest)
- ESLint 9.36.0

## 📥 Instalación Rápida

```bash
# Clonar el repositorio
git clone https://github.com/jnaveros40/codigo_base.git
cd codigo_base

# Instalar TODAS las dependencias
npm install && npm install firebase @supabase/supabase-js tailwindcss postcss autoprefixer vite-plugin-pwa -D

# Copiar variables de entorno
copy .env.example .env.local

# Iniciar desarrollo
npm run dev
```

> 📖 Para más detalles de instalación, consulta [INSTALL.md](./INSTALL.md)

## ⚙️ Configuración

### 1. Variables de Entorno

Edita `.env.local` con tus credenciales:

```env
# Firebase
VITE_FIREBASE_API_KEY=tu_api_key
VITE_FIREBASE_AUTH_DOMAIN=tu_auth_domain
VITE_FIREBASE_PROJECT_ID=tu_project_id

# Supabase
VITE_SUPABASE_URL=tu_supabase_url
VITE_SUPABASE_ANON_KEY=tu_anon_key
```

### 2. Personalización

#### Colores
- **TypeScript**: `src/styles/colors.ts`
- **CSS**: `src/styles/variables.css`
- **Tailwind**: `tailwind.config.cjs`

#### Contenido
- **Home**: `src/pages/Home.tsx`
- **Footer**: `src/components/Footer.tsx`

### 3. Servicios Externos

- **Firebase**: [console.firebase.google.com](https://console.firebase.google.com/)
- **Supabase**: [supabase.com](https://supabase.com/)

## 🎯 Scripts

```bash
npm run dev      # Servidor de desarrollo
npm run build    # Build de producción
npm run preview  # Preview del build
npm run lint     # Ejecutar linter
```

## 📁 Estructura del Proyecto

```
src/
├── assets/               # Recursos estáticos (imágenes, fuentes)
├── components/           # Componentes reutilizables
│   ├── Footer.tsx
│   └── Footer.css
├── config/              # Configuraciones de servicios
│   ├── firebase.ts      # Setup de Firebase
│   └── supabase.ts      # Setup de Supabase
├── pages/               # Páginas de la aplicación
│   ├── Home.tsx         # Página de inicio
│   └── Home.css         # Estilos de Home
├── styles/              # Sistema de diseño
│   ├── colors.ts        # Paleta de colores (TS)
│   ├── variables.css    # Variables CSS
│   └── README.md        # Documentación
├── utils/               # Funciones utilitarias
│   └── pwa.ts          # Funciones PWA
├── App.tsx             # Componente raíz
├── App.css             # Estilos globales
├── main.tsx            # Entry point
└── index.css           # Reset CSS y base
```

## 🎨 Sistema de Colores

### Uso en TypeScript
```tsx
import colors from './styles/colors'

<div style={{ backgroundColor: colors.primary.main }}>
  <p style={{ color: colors.text.primary }}>Texto</p>
</div>
```

### Uso en CSS
```css
.elemento {
  background-color: var(--color-primary);
  color: var(--text-primary);
  border: 1px solid var(--border-light);
  padding: var(--spacing-md);
  border-radius: var(--radius-md);
}
```

### Uso con Tailwind
```tsx
<div className="bg-primary text-white rounded-lg p-4">
  Contenido
</div>
```

## 🏗️ Arquitectura

### Flujo de la Aplicación
```
main.tsx → App.tsx → pages/Home.tsx → components/Footer.tsx
```

- **main.tsx**: Entry point, renderiza App
- **App.tsx**: Componente raíz, estructura principal
- **pages/**: Contenido específico de cada página
- **components/**: Componentes compartidos

## 🎓 Guía para Proyectos Grandes

### Agregar Nuevas Páginas

```tsx
// src/pages/About.tsx
import './About.css'

const About = () => {
  return (
    <div className="about-container">
      <h1>Sobre Nosotros</h1>
    </div>
  )
}

export default About
```

### Crear Componentes Reutilizables

```tsx
// src/components/Button.tsx
import './Button.css'

interface ButtonProps {
  text: string
  onClick: () => void
  variant?: 'primary' | 'secondary'
}

const Button = ({ text, onClick, variant = 'primary' }: ButtonProps) => {
  return (
    <button className={`btn btn-${variant}`} onClick={onClick}>
      {text}
    </button>
  )
}

export default Button
```

### Implementar Rutas (React Router)

```bash
npm install react-router-dom
```

```tsx
// App.tsx
import { BrowserRouter, Routes, Route } from 'react-router-dom'
import Home from './pages/Home'
import About from './pages/About'
import Footer from './components/Footer'

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
      <Footer />
    </BrowserRouter>
  )
}

export default App
```

### Estado Global (Context API)

```tsx
// src/context/AppContext.tsx
import { createContext, useContext, useState } from 'react'

interface AppContextType {
  user: any
  setUser: (user: any) => void
}

const AppContext = createContext<AppContextType | undefined>(undefined)

export const AppProvider = ({ children }: { children: React.ReactNode }) => {
  const [user, setUser] = useState(null)

  return (
    <AppContext.Provider value={{ user, setUser }}>
      {children}
    </AppContext.Provider>
  )
}

export const useApp = () => {
  const context = useContext(AppContext)
  if (!context) throw new Error('useApp must be used within AppProvider')
  return context
}
```

## 📱 PWA (Progressive Web App)

La aplicación está lista para ser PWA:

- ✅ Service Worker configurado
- ✅ Manifest.json incluido
- ✅ Iconos preparados (192x192, 512x512)
- ✅ Funciona offline
- ✅ Instalable en dispositivos

## 🔒 Seguridad

- ⚠️ **Nunca** comitees el archivo `.env.local`
- Usa variables de entorno para credenciales
- Mantén dependencias actualizadas: `npm update`
- Revisa vulnerabilidades: `npm audit`
- Configura reglas de seguridad en Firebase/Supabase

## 🚀 Despliegue

### Vercel (Recomendado)
```bash
npm install -g vercel
vercel
```

### Netlify
```bash
npm run build
# Sube la carpeta dist/
```

### Firebase Hosting
```bash
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

## 🤝 Contribuir

1. Fork el proyecto
2. Crea tu rama (`git checkout -b feature/NuevaCaracteristica`)
3. Commit tus cambios (`git commit -m 'Agrega NuevaCaracteristica'`)
4. Push a la rama (`git push origin feature/NuevaCaracteristica`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto es una plantilla base y puede ser usado libremente en tus proyectos.

## 👨‍💻 Autor

**Ing Navs**
- 🌐 Website: [ingnavs.vercel.app](https://ingnavs.vercel.app/)
- 💬 WhatsApp: +57 302 509 1063
- 📧 Email: Contacto disponible en el website

---

<div align="center">

⭐ **¡Dale una estrella si te gusta esta plantilla!** ⭐

[Reportar Bug](https://github.com/jnaveros40/codigo_base/issues) · [Solicitar Feature](https://github.com/jnaveros40/codigo_base/issues)

</div>
#   P r e v i n n o v a  
 