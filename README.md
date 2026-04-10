# 📱 Gestor de Gastos: Android a Notion (API)

![Notion](https://img.shields.io/badge/Notion-API-black?logo=notion) ![Android](https://img.shields.io/badge/Android-HTTP%20Shortcuts-green?logo=android) ![JSON](https://img.shields.io/badge/Data-JSON-orange)

Sistema automatizado para el registro de gastos personales directamente desde un smartphone Android hacia una base de datos en Notion, sin necesidad de servidores intermedios.

## 💡 El Proyecto
La idea original proviene de los "Atajos de iOS" (iPhone), pero como usuario de **Samsung (Android)**, adapté la solución utilizando peticiones HTTP directas.
El objetivo es reducir la fricción de anotar gastos: un toque en la pantalla de inicio, ingreso el monto, y los datos viajan automáticamente a mi tabla financiera.

## 🛠️ Stack Tecnológico
* **Frontend:** App "HTTP Request Shortcuts" (Android).
* **Backend:** Notion API (v1).
* **Protocolo:** REST API (POST Request).
* **Formato de Datos:** JSON.

## ⚙️ Cómo Funciona
1.  El usuario activa el atajo desde el widget en Android.
2.  La app solicita inputs (Nombre del gasto, Monto, Categoría).
3.  Se construye un **Payload JSON** dinámico.
4.  Se envía un `POST` a `https://api.notion.com/v1/pages`.
5.  Notion recibe la data y la inserta en la base de datos.

## 🔧 Guía de Instalación

### 1. Preparar Notion
* Crea una base de datos con las columnas: `Nombre` (Title), `Precio` (Number), `Categoria` (Select), `Fecha` (Date).
* Crea una integración en [Notion Developers](https://www.notion.so/my-integrations) y obtén tu **Internal Integration Token**.
* Dale permisos a la integración en tu base de datos (Menú "..." > Connections).

### 2. Configurar en Android
1.  Descarga la app **HTTP Request Shortcuts** (de Waboodoo).
2.  Crea un nuevo atajo tipo `POST`.
3.  **URL:** `https://api.notion.com/v1/pages`
4.  **Headers:**
    * `Authorization`: `Bearer TU_TOKEN_DE_NOTION`
    * `Notion-Version`: `2022-06-28` (o la actual)
    * `Content-Type`: `application/json`
5.  **Body (Cuerpo):** Copia y pega el contenido del archivo `body.json` de este repositorio.
6.  **Variables:** En la app, asocia `{{monto}}`, `{{nombre}}`, etc., con "Input Dialogs" para que te pregunte al ejecutar.

## 📂 Archivos del Repositorio
* `body.json`: La estructura exacta del JSON para configurar el envío.
* `README.md`: Esta documentación.

## 🤝 Créditos y Recursos
* **Inspiración y Lógica:** Basado en el método de automatización para iOS explicado por [Sofi de Eyetrade](https://www.youtube.com/watch?v=acHnDorJskg).
* **Plantilla de Notion:** Estructura de base de datos original creada por [Angel Santana](https://angelsantana.notion.site/Tracker-de-gastos-8036f109625849d891b48f0f3cb3a791).
* **Adaptación a Android:** Implementación de API y Shortcuts por **Federico Chaile**.
