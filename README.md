# Qualifica o seu professor
Final project for Computation in the internet III

## ¿Qué es la aplicación?

**Qualifica o seu professor** es una plataforma web que permite a los estudiantes calificar y comentar sobre sus profesores universitarios. La aplicación facilita un sistema de retroalimentación académica donde:

- Los **estudiantes** pueden buscar profesores por universidad, dejar comentarios y calificaciones
- Los **administradores** pueden gestionar usuarios, universidades y profesores
- Se mantiene un sistema de roles y permisos para controlar el acceso a las funcionalidades

### Funcionalidades principales:
- **Gestión de Usuarios**: Registro, autenticación y autorización con JWT
- **Gestión de Universidades**: CRUD completo de instituciones educativas
- **Gestión de Profesores**: CRUD completo de profesores asociados a universidades
- **Sistema de Comentarios**: Los estudiantes pueden calificar y comentar profesores
- **Control de Acceso**: Sistema de roles (superadmin, estudiante)

## Configuración para Tests

### Variables de Entorno para Postman

Para ejecutar los tests de Postman correctamente, necesitas configurar la variable `{{dominio}}`:

1. **Abrir Postman** y seleccionar la colección `apiExpress.postman_collection.json`
2. **Configurar la variable de entorno**:
   - Ve a **Environments** en Postman
   - Crea un nuevo environment o edita uno existente
   - Agrega la variable:
     - **Variable**: `dominio`
     - **Current Value**: `https://qualifica-o-seu-professor.onrender.com`
3. **Seleccionar el environment** antes de ejecutar los tests

### API Base URL
```
Production: https://qualifica-o-seu-professor.onrender.com
```

## Instalación y Configuración Local

### Prerrequisitos
- Node.js (v16 o superior)
- MongoDB (local o MongoDB Atlas)
- Git

### Pasos de instalación
1. **Clonar el repositorio**:
   ```bash
   git clone https://github.com/JohanDanielAguirre/qualifica-o-seu-professor.git
   cd qualifica-o-seu-professor
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   ```

3. **Configurar variables de entorno**:
   Crear un archivo `.env` en la raíz del proyecto:
   ```env
   PORT=3000
   MONGODB_URI=mongodb://localhost:27017/qualifica-professor
   JWT_SECRET=tu_jwt_secret_aqui
   NODE_ENV=development
   ```

4. **Ejecutar la aplicación**:
   ```bash
   # Desarrollo
   npm run dev
   
   # Producción
   npm start
   ```

5. **Poblar la base de datos** (opcional):
   ```bash
   npm run seed
   ```

## Objetivo: 

Desarrollar una aplicación backend robusta utilizando Node.js, TypeScript
para un tipado fuerte y MongoDB para la persistencia de datos. La aplicación debe
permitir operaciones CRUD en el módulo de usuarios y en al menos dos módulos
adicionales relacionados entre sí. Se debe implementar un sistema de autenticación y
autorización basado en JWT para controlar el acceso a las funcionalidades de la API.
Requisitos de la Asignación:
Descripción: Desarrollar una API RESTful para la aplicación propuesta por ustedes que
integre la gestión de usuarios con autenticación y autorización, y la administración de
al menos dos módulos interrelacionados (por ejemplo, Gestión de Proyectos y Gestión
de Tareas, aunque pueden adaptarse a cualquier dominio). La API permitirá realizar
operaciones CRUD en cada módulo, aplicando roles y permisos específicos que
definan las acciones permitidas para cada usuario.



## Requisitos Funcionales:


### Gestión de Usuarios:

• Los usuarios con rol de superadmin pueden crear, modificar y eliminar usuarios.
• Implementar roles de usuario: superadmin, usuario regular.
• Los usuarios autenticados pueden ver su perfil, pero sólo el superadmin puede
modificar o eliminar usuarios.


### Autenticación y Autorización:

• JWT y Middleware: Implementar un sistema de autenticación basado en JWT
para proteger las rutas CRUD de la API.
• Validación de Roles: Utilizar middleware para verificar la autenticación y los
permisos/roles de usuario en cada operación, asegurando que solo los usuarios
autorizados puedan acceder o modificar la información.


Ejemplo de módulos:
Un ejemplo de los módulos a revisar:


Módulo 1 – Gestión de Proyectos (o cualquier entidad principal):
Operaciones CRUD:

• Los usuarios autenticados pueden crear, visualizar, modificar y eliminar sus
propios proyectos.

• Los administradores podrán gestionar proyectos de cualquier usuario.


• Relación con Otros Módulos: Los proyectos deben poder vincularse a
elementos del módulo 2 (por ejemplo, tareas, actividades, usuarios, etc.).


Módulo 2 – Gestión de Tareas (o entidad relacionada):
Operaciones CRUD:


• Los usuarios autenticados podrán agregar, visualizar, modificar y eliminar
tareas asociadas a proyectos.

• Las tareas deben estar vinculadas a un proyecto específico y, opcionalmente,
asignarse a usuarios.

• Los administradores tendrán capacidad para gestionar tareas en cualquier
proyecto.

• Interrelación: Este módulo se relaciona directamente con el Módulo 1,
permitiendo estructurar y organizar las tareas en función del proyecto al que
pertenecen.

## Pruebas Unitarias:

• Desarrollar pruebas unitarias para cada componente individual de la aplicación
(por ejemplo, controladores, servicios, modelos y utilidades).
• Asegurar una buena cobertura de código, validando la lógica de negocio y las
funciones independientes.


• Utilizar frameworks de testing como Jest o Mocha para la implementación y
automatización de las pruebas.


## Pruebas de Integración (Postman):

• Implementar pruebas de integración para verificar el correcto funcionamiento
de las interacciones entre los diferentes módulos (usuarios, proyectos y tareas).
• Validar que los flujos de autenticación y autorización funcionen correctamente
al interactuar con las rutas protegidas.


• Simular escenarios de uso real, incluyendo la creación de relaciones entre
módulos y la verificación de permisos basados en roles.

## Cómo ejecutar los tests

### Tests Unitarios (Jest)
```bash
# Instalar dependencias
npm install

# Ejecutar todos los tests
npm test

# Ejecutar tests con coverage
npm run test:coverage

# Ejecutar tests en modo watch
npm run test:watch
```

### Tests de Integración (Postman)

1. **Importar la colección**: Importa el archivo `apiExpress.postman_collection.json` en Postman
2. **Configurar environment**:
   - Variable: `dominio`
   - Valor: `https://qualifica-o-seu-professor.onrender.com`
3. **Ejecutar tests**: Selecciona el environment configurado y ejecuta los tests

### API Endpoints Principales

- **Auth**: `/api/auth/login`, `/api/auth/register`
- **Users**: `/api/users` (CRUD completo)
- **Universities**: `/api/universities` (CRUD completo)
- **Professors**: `/api/professors` (CRUD completo)
- **Comments**: `/api/comments` (CRUD completo)

## Entrega y Presentación:
• El código fuente debe estar en un repositorio de GitHub, con un README claro
sobre cómo configurar y ejecutar el proyecto, además de una descripción de la
funcionalidad del mismo, que elementos no alcanzaron a ser desarrollados o
dificultades encontradas.


• El proyecto debe ser desplegado en nube.

• Se debe incluir archivo json de postman con las pruebas de cada funcionalidad
(debe hacer uso de variables).


• El código depositado en GitHub debe seguir unas git conventions claras
decididas por usted.


• Dentro del repositorio de GitHub debe encontrarse el enlace del despliegue del
servicio.


## Criterios de Evaluación:


• Calidad del Código y Uso de TypeScript (10%): Código bien organizado, tipado
fuertemente y comentado.


• Funcionalidad y Validaciones (40%): Cumplimiento de todas las
funcionalidades, incluyendo validaciones de entrada.


• Diseño de la Base de Datos y Uso de Modelos (10%): Correcta
implementación de los modelos de datos con TypeScript.


• Seguridad en Autenticación y Autorización (10%): Seguridad en el acceso a
rutas y operaciones CRUD.

• Documentación y Presentación (10%): Documentación completa (README de
ejecución, endpoints y tipos de documentos que reciben) y presentación clara y
detallada.


• Pruebas (20%): Cobertura en las pruebas del 80%, probar los escenarios de
éxito y de error (entradas inválidas).


---

## Guía del Seeder de datos

Para una guía exhaustiva del seeder (requisitos, variables, ejecución, troubleshooting y buenas prácticas), consulta:

- `docs/SEEDER.md`
