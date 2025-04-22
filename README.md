# 📚 App Inventario de Libros (CRUD)

Una aplicación web para gestionar un inventario de libros. Permite agregar, editar, eliminar y visualizar libros en una tabla dinámica, conectada a un backend desarrollado con JSON Server.

[![Deploy Frontend en Vercel](https://img.shields.io/badge/Frontend-Vercel-000?style=for-the-badge&logo=vercel)](https://app-inventario-de-libros.vercel.app)
[![Deploy Backend en Render](https://img.shields.io/badge/Backend-Render-3A3A3A?style=for-the-badge&logo=render)](https://app-inventario-de-libros.onrender.com/libros)

---

## 🛠️ Tecnologías usadas

- ⚙️ **Frontend**: Vue 3 + Vite
- 📦 **Backend**: JSON Server
- 🎨 **Estilos**: CSS personalizado + componentes responsivos
- 🌐 **Deploy**:
  - **Frontend**: [Vercel](https://vercel.com/)
  - **Backend**: [Render](https://render.com/)

---

## 🚀 Funcionalidades

- 📋 Listado de libros con tabla dinámica
- ➕ Agregar libros con formulario
- 📝 Editar datos de libros existentes
- ❌ Eliminar libros del inventario
- 🔄 Conexión a API externa en Render
- ✅ Interfaz simple, clara y responsiva

---

## 📂 Estructura del proyecto

app-inventario-de-libros/
├── db.json               # Base de datos simulada para JSON Server
├── index.js              # Configuración del servidor JSON Server
├── package.json          # Dependencias y scripts del proyecto
├── vue-libreria/         # Aplicación frontend en Vue.js
│   ├── src/
│   │   ├── assets/       # Recursos estáticos
│   │   ├── components/   # Componentes reutilizables
│   │   ├── views/        # Vistas principales
│   │   └── App.vue       # Componente raíz
│   └── vite.config.js    # Configuración de Vite

---

## 📡 Enlaces de despliegue

🔗 **Frontend (Vercel)**:  
👉 [https://app-inventario-de-libros.vercel.app]

🔗 **Backend (Render)**:  
👉 [https://app-inventario-de-libros.onrender.com/libros]

---

## 🧪 Cómo ejecutar localmente

1. **Clona el repositorio**:

   git clone https://github.com/AJAV-Dev/app-inventario-de-libros.git
   cd app-inventario-de-libros

2. **Instala dependencias y corre el backend**:

  npm install
  npm start
   
3. **Corree el frontend**:

  cd vue-libreria
  npm install
  npm run dev
