# Despliegue de la App PokeDex a Vercel

Este documento describe cómo fue desplegada la aplicación PokeDex en la nube pública usando Vercel y cómo se configuraron aspectos esenciales para su funcionamiento y seguridad.

---

##  Pre-requisitos

- Tener una cuenta en GitHub.
- Contar con una cuenta en [https://vercel.com](https://vercel.com).
- Tener el proyecto PokeDex alojado en un repositorio de GitHub.

---

## Preparación del Proyecto Angular

1. Ejecutar en la terminal:
   ```bash
   ng build --configuration production
2. Verificar en `angular.json` que el `outputPath` coincida:

      `"outputPath": "dist/pokedex"`
      
## Creación del archivo `vercel.json`

### ¿Para qué sirve `vercel.json`?

Este archivo permite configurar el comportamiento del despliegue en Vercel, incluyendo rutas, redirecciones y, en este caso, **cabeceras de seguridad** que mejoran la calificación del sitio web en plataformas como [securityheaders.com](https://securityheaders.com).

### ¿Cómo se creó?

 -  Se accedió al repositorio desde el navegador con la URL:
`github.dev`

 -  Es decir, desde cualquier repo se puede presionar `.` (punto) o entrar directamente con `https://github.dev/usuario/repositorio`.
    
 - Se creó un archivo en la raíz llamado `vercel.json`.
   
 - Se pegó la siguiente configuración:

 - ```json {   "headers": [ {  
   "source": "/(.*)",   "headers": [
       {
         "key": "Content-Security-Policy",
         "value": "default-src 'self'; connect-src 'self' https://pokeapi.co https://beta.pokeapi.co; script-src 'self'
   'unsafe-inline'; style-src 'self' 'unsafe-inline'
   https://fonts.googleapis.com; font-src 'self'
   https://fonts.gstatic.com; img-src 'self' data: https:"
       },
       { "key": "X-Frame-Options",           "value": "SAMEORIGIN" },
       { "key": "X-Content-Type-Options",    "value": "nosniff" },
       { "key": "Referrer-Policy",           "value": "strict-origin-when-cross-origin" },
       { "key": "Strict-Transport-Security", "value": "max-age=63072000; includeSubDomains; preload" }   ] }   ] }

**Importante:** Esta configuración permite que la aplicación pueda hacer peticiones seguras a `https://pokeapi.co` y `https://beta.pokeapi.co`, que son necesarias para el correcto funcionamiento del GraphQL de la PokeAPI.

## 🚀 Despliegue en Vercel

1.  Iniciar sesión en [https://vercel.com](https://vercel.com).
    
2.  Importar el repositorio desde GitHub.
    
3.  Configurar el build:
    
    -   **Framework**: Angular (Vercel lo detecta automáticamente).
        
    -   **Build Command**: `ng build --configuration production`
        
    -   **Output Directory**: `dist/pokedex`
        
4.  Hacer clic en **"Deploy"**.

##  Resultado

-   La aplicación quedó publicada en un dominio generado automáticamente por Vercel (https://pokedex-alpha-swart.vercel.app/).
    
-   Se verificó que los headers de seguridad estuvieran activos con una puntuación de seguridad aceptable (entre B y A): [Scan results for https://pokedex-alpha-swart.vercel.app/](https://securityheaders.com/?q=https%3A%2F%2Fpokedex-alpha-swart.vercel.app%2F&followRedirects=on).
    
-   Funciona correctamente el consumo de la API pública de Pokémon.

##  Autor

Jason Duvan Cristancho Padilla – Estudiante de Ingeniería de Sistemas apasionado por la ciberseguridad.
