# Automatización de Pruebas de API con Postman y Newman

Esta guía describe cómo implementar un sistema de automatización de pruebas de API utilizando **Postman** para el diseño de pruebas y **Newman** para su ejecución automatizada, ideal para integrarse en flujos de **CI/CD**.

---

## 📌 Objetivo

Estandarizar y automatizar la validación de APIs, asegurando la calidad de los endpoints críticos mediante pruebas reutilizables, reportes claros y fácil mantenimiento.

---

## 1️⃣ Identificación de Endpoints Críticos

Para maximizar el valor de la automatización, se deben priorizar los endpoints que representen el **Camino Feliz (Happy Path)** y los flujos críticos del negocio:

### 🔐 Autenticación
- Login
- Renovación de tokens
- Validación de sesiones

### 🧩 Operaciones CRUD Principales
- Creación de recursos (POST)
- Lectura de información (GET)
- Actualización (PUT / PATCH)
- Eliminación (DELETE)

Ejemplos:
- Usuarios
- Productos
- Pedidos

### 🔗 Integraciones
- Comunicación con servicios externos
- Pasarelas de pago
- Servicios de terceros

---

## 2️⃣ Creación y Refinamiento de Colecciones

Organiza las colecciones para que sean **escalables y mantenibles**.

### 🌍 Uso de Environments
Evita URLs o valores hardcodeados utilizando variables como:

- `{{base_url}}`
- `{{api_key}}`
- `{{user_token}}`

### 🔄 Variables Dinámicas
Genera datos únicos para evitar duplicidades:

- `{{$randomFirstName}}`
- `{{$randomEmail}}`
- `{{$guid}}`

### ⚙️ Scripts de Pre-request
Utiliza scripts para:
- Generar fechas dinámicas
- Calcular firmas
- Limpiar o inicializar variables
- Preparar headers de autenticación

---

## 3️⃣ Definición de Pruebas Automatizadas

En la pestaña **Tests** de Postman, agrega validaciones claras y robustas.

### ✅ Validar Código de Estado
```javascript
pm.test("Estado de respuesta es 200", function () {
    pm.response.to.have.status(200);
});
