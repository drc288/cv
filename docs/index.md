# Documentación del Proyecto CV

## 📋 Descripción del Proyecto

Este proyecto es un **resume/CV minimalista** diseñado para web y PDF, basado en el esquema JSON de [jsonresume.org](https://jsonresume.org/schema/). Es una aplicación web moderna construida con Astro que permite generar un currículum vitae profesional y responsive.

### Características Principales

- ✨ Diseño minimalista y profesional
- 🌐 Soporte para múltiples idiomas (Español e Inglés)
- 📱 Responsive design para todos los dispositivos
- 🖨️ Optimizado para impresión y exportación a PDF
- ⚡ Rendimiento optimizado con Astro
- 🔧 Fácil personalización mediante archivos JSON

## 🛠️ Stack Tecnológico

- **[Astro](https://astro.build/)** - Framework web de nueva generación para sitios estáticos
- **[TypeScript](https://www.typescriptlang.org/)** - JavaScript con tipado estático
- **[Tailwind CSS](https://tailwindcss.com/)** - Framework CSS utilitario

## 📁 Estructura del Proyecto

```
cv/
├── docs/                   # Documentación del proyecto
├── public/                 # Archivos estáticos
├── src/
│   ├── components/         # Componentes reutilizables
│   │   ├── icons/         # Iconos SVG
│   │   ├── About.astro    # Sección "Acerca de"
│   │   ├── Education.astro # Sección de educación
│   │   ├── Experience.astro # Sección de experiencia
│   │   ├── Hero.astro     # Sección principal con datos personales
│   │   ├── Projects.astro # Sección de proyectos
│   │   ├── Section.astro  # Componente base para secciones
│   │   └── Skills.astro   # Sección de habilidades
│   ├── layouts/           # Layouts de página
│   │   └── Layout.astro   # Layout principal
│   ├── pages/             # Páginas del sitio
│   │   ├── en/           # Versión en inglés
│   │   └── index.astro   # Página principal (español)
│   └── types/            # Definiciones de tipos TypeScript
│       └── resume.ts     # Tipos para el esquema JSON Resume
├── resume-es.json         # Datos del CV en español
├── resume-en.json         # Datos del CV en inglés
├── astro.config.mjs       # Configuración de Astro
├── package.json           # Dependencias del proyecto
└── tsconfig.json          # Configuración de TypeScript
```

## 🚀 Instalación y Configuración

### Prerrequisitos

- Node.js (versión 18 o superior)
- npm o yarn

### Pasos de Instalación

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/drc288/cv.git
   cd cv
   ```

2. **Instalar dependencias:**
   ```bash
   npm install
   ```

3. **Ejecutar en modo desarrollo:**
   ```bash
   npm run dev
   ```

4. **Abrir en el navegador:**
   ```
   http://localhost:4321
   ```

## 🧞 Comandos Disponibles

| Comando | Descripción |
|---------|-------------|
| `npm run dev` o `npm start` | Inicia servidor de desarrollo en `localhost:4321` |
| `npm run build` | Construye el proyecto para producción en `./dist/` |
| `npm run preview` | Previsualiza la build de producción |
| `npm run astro` | Ejecuta comandos CLI de Astro |

## 📝 Personalización del CV

### Modificar Contenido

Para personalizar tu CV, edita los archivos JSON correspondientes:

- **Español:** `resume-es.json`
- **Inglés:** `resume-en.json`

### Estructura de los Archivos JSON

Los archivos siguen el [esquema JSON Resume](https://jsonresume.org/schema/):

```json
{
  "$schema": "https://raw.githubusercontent.com/jsonresume/resume-schema/v1.0.0/schema.json",
  "basics": {
    "name": "Tu Nombre",
    "label": "Tu Título Profesional",
    "email": "tu@email.com",
    "phone": "tu-telefono",
    "url": "tu-website.com",
    "summary": "Breve descripción profesional",
    "location": { ... },
    "profiles": [ ... ]
  },
  "work": [ ... ],
  "education": [ ... ],
  "skills": [ ... ],
  "projects": [ ... ]
}
```

### Secciones Principales

1. **basics:** Información personal y de contacto
2. **work:** Experiencia laboral
3. **education:** Formación académica
4. **skills:** Habilidades técnicas
5. **projects:** Proyectos destacados
6. **languages:** Idiomas
7. **interests:** Intereses personales

### Personalizar Estilos

Los estilos se encuentran en cada componente Astro. Para modificaciones globales, edita:
- `src/layouts/Layout.astro` - Estilos globales
- Componentes individuales para estilos específicos

## 🌐 Soporte Multiidioma

El proyecto incluye soporte para español e inglés:

- **Español (por defecto):** `http://localhost:4321/`
- **Inglés:** `http://localhost:4321/en/`

La configuración de idiomas se encuentra en `astro.config.mjs`.

## 📤 Despliegue

### Build de Producción

```bash
npm run build
```

Los archivos compilados se generan en la carpeta `./dist/`.

### Opciones de Hosting

- **Netlify:** Conecta tu repositorio y deploya automáticamente
- **Vercel:** Import desde GitHub y configura el build
- **GitHub Pages:** Configura GitHub Actions para deployment automático
- **Cualquier hosting estático:** Sube el contenido de `./dist/`

### Configuración para GitHub Pages

Agrega este workflow en `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v2
        with:
          node-version: '18'
      - run: npm install
      - run: npm run build
      - uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./dist
```

## 🖨️ Exportación a PDF

Para generar una versión PDF de tu CV:

1. Abre la versión web en tu navegador
2. Presiona `Ctrl+P` (Windows/Linux) o `Cmd+P` (Mac)
3. Selecciona "Guardar como PDF"
4. Ajusta los márgenes y configuración según necesites

## 🤝 Contribuir

### Proceso de Contribución

1. Fork el repositorio
2. Crea una rama para tu feature: `git checkout -b feature/nueva-funcionalidad`
3. Realiza tus cambios y commits: `git commit -m 'Agregar nueva funcionalidad'`
4. Push a la rama: `git push origin feature/nueva-funcionalidad`
5. Abre un Pull Request

### Guías de Desarrollo

- Usa TypeScript para todo el código
- Sigue las convenciones de nombres de Astro
- Mantén los componentes pequeños y reutilizables
- Documenta funciones y componentes complejos
- Prueba los cambios en ambos idiomas

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver [LICENSE.txt](../LICENSE.txt) para más detalles.

## 🙏 Reconocimientos

- Basado en el diseño de [Bartosz Jarocki](https://github.com/BartoszJarocki/cv)
- Siguiendo la guía de [midudev](https://midu.dev)
- Esquema JSON Resume de [jsonresume.org](https://jsonresume.org/schema/)

## 📞 Soporte

Si tienes preguntas o problemas:

1. Revisa la documentación
2. Busca en los [Issues existentes](https://github.com/drc288/cv/issues)
3. Crea un nuevo Issue si no encuentras solución

---

**Desarrollado por David Rosero Calle** | [LinkedIn](https://www.linkedin.com/in/david-rosero-calle-1aa6a2126/) | [GitHub](https://github.com/drc288)