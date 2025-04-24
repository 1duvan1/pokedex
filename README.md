# Pokédex Angular

Aplicación desarrollada en Angular para mostrar información de Pokémon, consumiendo datos desde la [PokeAPI](https://pokeapi.co/).

---

##  Creación de la cuenta en la nube (Vercel)

A continuación, se describe paso a paso cómo se creó la cuenta en la plataforma de despliegue Vercel:

### 1. Registro en Vercel

- Ir a: [https://vercel.com](https://vercel.com)
- Hacer clic en **"Start deploying"**.
- Iniciar sesión con una cuenta de GitHub (se recomienda usar la misma que tenga el repositorio del proyecto).

### 2. Autorización de GitHub
- Vercel solicitará permisos para acceder a los repositorios de GitHub.
- Se puede elegir autorizar solo el repositorio específico del proyecto.

### 3. Importación del proyecto
- Vercel permite importar directamente desde GitHub.
- Se selecciona el repositorio de la PokeDex App y se da clic en **"Import"**.

### 4. Configuración inicial

- Seleccionar el framework: Angular (Vercel lo detecta automáticamente).
- Build Command: `ng build --configuration production`
- Output Directory: `dist/pokedex` (asegúrate que el nombre coincida con el tuyo si lo cambiaste en angular.json).

### 5. Deploy
- Vercel realiza automáticamente el primer despliegue.
- Se genera una URL pública (ejemplo: `https://pokedex-app.vercel.app`).

---

## 👤 Autor

Jason Duvan Cristancho Padilla – Estudiante de Ingeniería de Sistemas apasionado por la ciberseguridad.

