# 🧟 Laboratorio #3 — CRUD Rápido en Laravel

<div align="center">

<!-- 🎯 GIF principal del proyecto aquí -->
![gif-principal](PEGA_AQUI_URL_DE_UN_GIF_DE_LARAVEL_O_CRUD)

![Laravel](https://img.shields.io/badge/Laravel-v13.6-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-8.x-777BB4?style=for-the-badge&logo=php&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-5-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-8.0.5-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![WampServer](https://img.shields.io/badge/WampServer-3.x-orange?style=for-the-badge&logo=apache&logoColor=white)

**Universidad Tecnológica de Panamá**  
Facultad de Ingeniería en Sistemas Computacionales  
Campus Victor Levis Sasso

</div>

---

## 📋 Tabla de Contenidos

- [Objetivo del Laboratorio](#-objetivo-del-laboratorio)
- [Requisitos Previos](#-requisitos-previos)
- [Introducción MVC](#-introducción-al-patrón-mvc-en-laravel)
- [Secuencia de Comandos](#-secuencia-de-comandos-utilizados)
- [Base de Datos](#-base-de-datos)
- [Resultados Obtenidos](#-resultados-obtenidos)
- [Dificultades y Soluciones](#-dificultades-y-soluciones)
- [Referencias](#-referencias)
- [Footer](#-desarrollado-por)

---

## 🎯 Objetivo del Laboratorio

Implementar un sistema **CRUD (Create, Read, Update, Delete)** completo en Laravel para la gestión de productos, utilizando el patrón de arquitectura **Modelo–Vista–Controlador (MVC)**, el paquete `ibex/crud-generator` y una base de datos MySQL gestionada con migraciones de Artisan.

---

## 🛠️ Requisitos Previos

### Ecosistema de Desarrollo

| Tecnología | Versión | Descripción |
|---|---|---|
| ![PHP](https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=white) **PHP** | 8.x o superior | Lenguaje de programación del servidor |
| ![Composer](https://img.shields.io/badge/Composer-885630?logo=composer&logoColor=white) **Composer** | Última versión estable | Gestor de dependencias de PHP |
| ![Laravel](https://img.shields.io/badge/Laravel-FF2D20?logo=laravel&logoColor=white) **Laravel** | v13.6 | Framework PHP bajo patrón MVC |
| ![WampServer](https://img.shields.io/badge/WampServer-orange?logo=apache&logoColor=white) **WampServer** | 3.x | Entorno de desarrollo local (Apache + MySQL) |
| ![Apache](https://img.shields.io/badge/Apache-D22128?logo=apache&logoColor=white) **Apache** | Incluido en WAMP | Servidor web |
| ![MySQL](https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white) **MySQL** | 8.0 | Base de datos relacional |
| ![VSCode](https://img.shields.io/badge/VS_Code-007ACC?logo=visualstudiocode&logoColor=white) **Visual Studio Code** | Última versión | Editor de código recomendado |
| ![Node.js](https://img.shields.io/badge/NPM-CB3837?logo=npm&logoColor=white) **NPM** | Incluido con Node.js | Gestor de paquetes JavaScript (necesario para Vite) |
| ![Windows](https://img.shields.io/badge/Windows-0078D6?logo=windows&logoColor=white) **Sistema Operativo** | Windows 10/11 | SO utilizado en el laboratorio |

---

## 🦈 Introducción al Patrón MVC en Laravel

Laravel organiza su código bajo el patrón **Modelo–Vista–Controlador (MVC)**, que separa las responsabilidades de la aplicación en tres capas:

```
crud_rapido/
│
├── 📁 app/
│   ├── 📁 Http/
│   │   ├── 📁 Controllers/        ← CONTROLADORES
│   │   │   └── ProductController.php  ← CRUD de Productos
│   ├── 📁 Models/                 ← MODELOS
│   │   └── Product.php            ← Modelo de Producto
│   └── 📁 Providers/
│       └── AppServiceProvider.php
│
├── 📁 resources/
│   └── 📁 views/                  ← VISTAS (Blade Templates)
│       └── products/
│           ├── index.blade.php    ← Lista de productos
│           ├── create.blade.php   ← Crear producto
│           ├── edit.blade.php     ← Editar producto
│           └── show.blade.php     ← Ver producto
│
├── 📁 routes/
│   └── web.php                    ← RUTAS
│
├── 📁 database/
│   └── 📁 migrations/             ← MIGRACIONES
│       └── create_products_table.php
│
└── .env                           ← Variables de entorno
```

### ¿Qué hace cada capa?

| Capa | Carpeta | Función |
|---|---|---|
| 🟦 **Modelo** | `app/Models/` | Representa los datos y la lógica de negocio. Se comunica con la base de datos. |
| 🟩 **Vista** | `resources/views/` | Contiene las plantillas Blade que el usuario ve en el navegador. |
| 🟧 **Controlador** | `app/Http/Controllers/` | Recibe las solicitudes del usuario, consulta el modelo y retorna la vista. |
| 🟪 **Rutas** | `routes/web.php` | Define las URLs de la aplicación y las conecta con los controladores. |

### ¿Qué es un CRUD?

| Operación | Método HTTP | Ruta | Descripción |
|---|---|---|---|
| **C**reate | POST | `/products` | Crear un nuevo producto |
| **R**ead | GET | `/products` | Listar todos los productos |
| **U**pdate | PUT/PATCH | `/products/{id}` | Editar un producto |
| **D**elete | DELETE | `/products/{id}` | Eliminar un producto |

---

## ⚙️ Secuencia de Comandos Utilizados

<!-- 🎮 GIF de terminal/coding aquí -->
![gif-terminal](PEGA_AQUI_URL_DE_UN_GIF_DE_TERMINAL_O_CODING)

### 1️⃣ Crear el Proyecto
```bash
laravel new crud_rapido
# Opciones seleccionadas:
# - Starter Kit: None
# - Testing: PHPUnit
# - Laravel Boost: No
# - Base de datos: MySQL
# - Migraciones: Yes
```

### 2️⃣ Corrección del Error de Longitud de Cadena
```php
// En: app/Providers/AppServiceProvider.php
use Illuminate\Support\Facades\Schema;

public function boot(): void
{
    Schema::defaultStringLength(191);
}
```

### 3️⃣ Ejecutar Migraciones
```bash
cd crud_rapido
php artisan migrate:fresh
```

### 4️⃣ Crear el Modelo Product con su Migración
```bash
php artisan make:model Product -m
```

### 5️⃣ Definir los campos en la migración
```php
Schema::create('products', function (Blueprint $table) {
    $table->id();
    $table->string('description');
    $table->double('price', 8, 2);
    $table->integer('stock');
    $table->timestamps();
});
```

### 6️⃣ Correr la migración de products
```bash
php artisan migrate
```

### 7️⃣ Instalar el Generador de CRUD
```bash
composer require ibex/crud-generator --dev
```

### 8️⃣ Publicar archivos del proveedor
```bash
php artisan vendor:publish --tag=crud
```

### 9️⃣ Generar el CRUD de products
```bash
php artisan make:crud products
# Stack seleccionado: bootstrap
```

### 🔟 Agregar la ruta en web.php
```php
use App\Http\Controllers\ProductController;
Route::resource('products', ProductController::class);
```

### 1️⃣1️⃣ Actualizar el autoload
```bash
composer dump-autoload
```

### 1️⃣2️⃣ Instalar Bootstrap y dependencias front-end
```bash
composer require laravel/ui
php artisan ui bootstrap
npm install
npm run build
```

### 1️⃣3️⃣ Levantar el Servidor
```bash
php artisan serve
```

---

## 🗃️ Base de Datos

### Configuración del archivo `.env`

```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=crud_rapido
DB_USERNAME=root
DB_PASSWORD=
```

> ⚠️ **Nota:** En WampServer el usuario `root` no tiene contraseña por defecto en entornos de desarrollo local.

### Tablas creadas por las migraciones

| Tabla | Descripción | Estado |
|---|---|---|
| `users` | Almacena los usuarios del sistema | ✅ DONE |
| `products` | Almacena los productos (description, price, stock) | ✅ DONE |
| `cache` | Manejo de caché de la aplicación | ✅ DONE |
| `jobs` | Cola de trabajos en segundo plano | ✅ DONE |
| `migrations` | Registro interno de migraciones ejecutadas | ✅ DONE |

### Estructura de la tabla `products`

| Campo | Tipo | Descripción |
|---|---|---|
| `id` | BIGINT (PK) | Identificador único autoincremental |
| `description` | VARCHAR | Descripción del producto |
| `price` | DOUBLE(8,2) | Precio con 8 enteros y 2 decimales |
| `stock` | INTEGER | Cantidad disponible en inventario |
| `created_at` | TIMESTAMP | Fecha de creación |
| `updated_at` | TIMESTAMP | Fecha de última actualización |

### Comandos de Migración utilizados

```bash
# Ejecutar todas las migraciones pendientes
php artisan migrate

# Borrar todas las tablas y volver a migrar desde cero
php artisan migrate:fresh

# Ver el estado de las migraciones
php artisan migrate:status
```

---

## 📸 Resultados Obtenidos

### ✅ Lista de Productos (Index)

<!-- 🖼️ PEGA AQUÍ EL SCREENSHOT DE LA LISTA DE PRODUCTOS -->
![screenshot-index](PEGA_AQUI_URL_O_RUTA_DEL_SCREENSHOT_INDEX)

> 📌 *Acceder en:* `http://127.0.0.1:8000/products`

---

### ✅ Crear Producto (Create)

<!-- 🖼️ PEGA AQUÍ EL SCREENSHOT DEL FORMULARIO DE CREAR -->
![screenshot-create](PEGA_AQUI_URL_O_RUTA_DEL_SCREENSHOT_CREATE)

> 📌 *Acceder en:* `http://127.0.0.1:8000/products/create`

---

### ✅ Editar Producto (Edit)

<!-- 🖼️ PEGA AQUÍ EL SCREENSHOT DEL FORMULARIO DE EDITAR -->
![screenshot-edit](PEGA_AQUI_URL_O_RUTA_DEL_SCREENSHOT_EDIT)

---

### ✅ Servidor corriendo

```
INFO  Server running on [http://127.0.0.1:8000].
Press Ctrl+C to stop the server
```

---

## ⚠️ Dificultades y Soluciones

<!-- 🎮 GIF de error/bug gracioso aquí -->
![gif-bugs](PEGA_AQUI_URL_DE_UN_GIF_DE_BUG_O_ERROR_GRACIOSO)

### ❓ Dificultad 1 — Error de Longitud de Cadena en MySQL

**Error encontrado:**
```
SQLSTATE[42000]: Syntax error or access violation: 1071
Specified key was too long; max key length is 1000 bytes
```

**Causa:** La versión de MySQL instalada tiene un límite de 1000 bytes para índices.

**Solución aplicada:**
```php
// app/Providers/AppServiceProvider.php
use Illuminate\Support\Facades\Schema;

public function boot(): void
{
    Schema::defaultStringLength(191);
}
```

---

### ❓ Dificultad 2 — Class "App\Providers\ServiceProvider" not found

**Error encontrado:**
```
Class "App\Providers\ServiceProvider" not found
```

**Causa:** Al editar el `AppServiceProvider.php` le faltaba la línea `<?php` al inicio y el `use Illuminate\Support\ServiceProvider`.

**Solución aplicada:**
```php
<?php

namespace App\Providers;

use Illuminate\Support\ServiceProvider;
use Illuminate\Support\Facades\Schema;

class AppServiceProvider extends ServiceProvider
{
    public function boot(): void
    {
        Schema::defaultStringLength(191);
    }
}
```

---

### ❓ Dificultad 3 — Error de sintaxis en la migración de products

**Error encontrado:**
```
ParseError: syntax error, unexpected token "public"
```

**Causa:** Al agregar los campos en la migración, faltó cerrar correctamente el paréntesis y llave del `Schema::create`.

**Solución aplicada:** Se reemplazó el contenido completo del archivo de migración con la sintaxis correcta.

---

### ❓ Dificultad 4 — Data truncated for column 'price'

**Error encontrado:**
```
SQLSTATE[01000]: Warning: 1265 Data truncated for column 'price' at row 1
```

**Causa:** Se ingresó el precio con el símbolo `$` (ej: `14$`) cuando el campo es numérico y solo acepta números.

**Solución aplicada:** Ingresar solo el valor numérico sin símbolos (ej: `14` o `14.99`).

---

### ❓ Dificultad 5 — CSS no cargaba sin npm run dev

**Error encontrado:** El CSS de Bootstrap no cargaba al levantar solo `php artisan serve`.

**Causa:** Vite necesita estar corriendo para servir los assets en desarrollo.

**Solución aplicada:** Compilar los assets de forma permanente con:
```bash
npm run build
```

---

## 🎒 Referencias

1. **Video Proporcionado por la Profesora** — CRUD con Laravel  
   🔗 https://www.youtube.com/watch?v=yp04wvbAJPs

2. **Laravel Página Oficial**  
   🔗 https://laravel.com/docs/12.x

3. **Ibex CRUD Generator — GitHub**  
   🔗 https://github.com/awes-io/laravel-crud-generator

4. **Composer Página Oficial**  
   🔗 https://getcomposer.org/download/

5. **WampServer Official Site**  
   🔗 https://www.wampserver.com/

---

## 📅 Fecha de Ejecución del Laboratorio

| Detalle | Información |
|---|---|
| 📆 Fecha de ejecución | 28 de abril de 2026 |
| ⏱️ Duración aproximada | 2 horas |
| 💻 Entorno | Windows 11 + WampServer + VS Code |

---

<div align="center">

## 👨‍💻 Desarrollado por

<!-- 🎉 GIF de celebración para el footer -->
![gif-footer](PEGA_AQUI_URL_DE_UN_GIF_CHIDO_PARA_EL_FOOTER)

**Este laboratorio ha sido desarrollado por el estudiante de la Universidad Tecnológica de Panamá:**

| Campo | Información |
|---|---|
| 👤 **Nombre** | Abraham Magin |
| 📧 **Correo** | abraham.magin@utp.ac.pa |
| 📚 **Curso** | Desarrollo de Software VII |
| 👩‍🏫 **Instructora** | Ing. Irina Fong |
| 🏫 **Universidad** | Universidad Tecnológica de Panamá |
| 🏛️ **Facultad** | Ingeniería en Sistemas Computacionales |
| 🎓 **Carrera** | Lic. Desarrollo y Gestión de Software |

---

*Campus Victor Levis Sasso — I Semestre 2026*

</div>
