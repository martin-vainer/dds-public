# Apuntes DDS - Desarrollo de Software

> Regla del apunte: **concepto -> ejemplo mínimo -> ejemplo real (repo) -> errores típicos**.

## Bitácora / Índice de lectura

Mapa rápido para navegar el apunte sin leer todo. Cada clase apunta a sus fuentes principales y, donde aplica, a la rama o referencia de código usada.

| Clase | Tema central | Repo / rama | Anclar en |
| ----- | ------------ | ----------- | --------- |
| [01](#clase-01---proceso-arquitectura-javascript-nodejs-y-npm) | Proceso, arquitectura, JS, Node.js y NPM | `ddsw-mn/web-server` (main) | requerimientos, semver, capas, Node.js, NPM |
| [02](#clase-02---httprest-asincronismo-y-git) | HTTP/REST, async, Git | `ddso-utn/ejemplo-async`, `web-server` (branches async) | callbacks/promises/async-await, merge vs rebase |
| [03](#clase-03---api-megasuper-rest-express-y-primeras-decisiones-de-arquitectura) | API MegaSuper en Express | `ddso-utn/api-megasuper-2026` (main) | `/v1/productos`, status codes, Zod, capas |
| [04](#clase-04---arquitectura-por-capas-y-orquestación-de-casos-de-uso) | Capas y orquestación | `ejercicio-megasuper-2026` / `clase4-ApiSeparadaEnCapas` | controller / service / repository / domain |
| [05](#clase-05---manejo-de-errores-y-middlewares-en-express) | Errores y middlewares | `ejercicio-megasuper-2026` / `clase5-error-handling` | `next(error)`, `AppError`, error handler |
| [06](#clase-06---testing-con-jest-supertest-y-documentación-con-openapi) | Testing y documentación | `ejercicio-megasuper-2026` / `clase6-testing` | Jest, mocks, Supertest, OpenAPI/Swagger |
| [07](#clase-07---persistencia-y-odm-con-mongoose) | Persistencia y ODM | `ejercicio-megasuper-2026` / `clase7-presistencia-odm-alojamientos` | MongoDB, schemas, populate, aggregate, soft delete |
| [08](#clase-08---frontend-inicial-html-css-accesibilidad-y-dom) | Frontend inicial | `borradores/teoria/clase-08-frontend-inicial.md` | HTML semántico, CSS, DOM, eventos |
| [09](#clase-09---fundamentos-de-react-y-routing) | Front con React pt. 1 | `ejercicio-megasuper-2026` / `clase9-front-react-pt1` | CSR, Virtual DOM, componentes, props/state, routing |
| [10](#clase-10---react-hooks-estado-y-carrito) | Front con React pt. 2 | `ejercicio-megasuper-2026` / `clase10-front-react-pt2` | Hooks, useState/useEffect, render condicional, carrito, MUI |
| [11 y 12](#clase-11-y-12---desarrollo-en-react-avanzado-parte-iii--integración-con-backend) | React avanzado + integración con backend | `clase-cirbnb/evolutivo-8-integracion` como patrón + MegaSuper PR #4/#6 | Axios, CORS, sesiones, Context API, custom hooks, SDD |
| [13](#clase-13---despliegue-cicd-contenedores-y-release) | Despliegue, CI/CD, contenedores y release | Teoría Clase 13 (sin práctica/UX por ahora) | release, pipeline, deploy strategies, infraestructura, Docker |

> Como leer este apunte:
> 1. Mira el "resumen mental" al final de cada clase para tener el discurso de examen.
> 2. Si algo no cierra, vuelve al concepto teórico y después al ejemplo de repo.
> 3. Para detalles de fuentes y repos clonados localmente, ver `./BITACORA_CURSO.md`.

## Fuentes

### Material oficial y fuentes locales
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 1 - Resumen.pdf`
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 2 - Resumen.pdf`
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 3 - Resumen.pdf`
- `Clases_Teoria/Clase 3 - Promesas.pdf`
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 6 - Resumen.pdf`
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 7 - Resumen.pdf`
- `Clases_Teoria/Clase 9 - UI.pdf`
- `Clases_Teoria/1C2026 - DDSW - MN - Clase 11 - Sesiones.pdf`
- `Clases_Practica/Clase Práctica - 01 - Js.pdf`
- `Clases_Practica/Clase Práctica - 01 - Apunte NPM.pdf`
- `Clases_Practica/Clase Práctica - 02 - ASYNC en JS.pdf`
- `Clases_Practica/Clase Práctica - 02 - GIT.pdf`
- `Clases_Practica/Clase Práctica - 04 - Capas.pdf`
- `Clases_Practica/Clase Práctica - 05- Manejo de errores.pdf`
- `Clases_Practica/Clase Práctica - 06 - testing y documentacion.pdf`
- `Clases_Practica/Clase Práctica -  07 - ODM.pdf`
- `borradores/teoria/clase-08-frontend-inicial.md`
- `Clases_Practica/Clase Práctica - 09 - Fundamentos de React.pdf`
- `Clases_Practica/Clase Práctica - 10 - React_ Hooks.pdf`
- `Clases_Practica/Clase Práctica - 11 - Integracion Front y Backend.pdf`
- `Clases_Practica/Clase Práctica - 12 (2025) - React_ Manejo del Estado Global y React Avanzado.pdf`
- `borradores/teoria/clase-09-frontend-intermedio.md`
- `borradores/teoria/clase-11-frontend-avanzado.md`
- `borradores/practica/clase-11-integracion-front-back.md`
- `borradores/practica/clase-12-react-manejo-estado.md`
- (TPs) `Clases_Practica/Clase Práctica - 01 - enunciado CirBnb.pdf`, `Clases_Practica/Clase practica - 01 - enunciado MegaSuper.pdf`

### Código (repos permitidos)
- `ddsw-mn/web-server` (branches por concepto): https://github.com/ddsw-mn/web-server
- `ddso-utn/ejemplo-async` (asincronismo pedagogico): https://github.com/ddso-utn/ejemplo-async
- `ddso-utn/api-megasuper-2026` (Clase 03 HTTP/REST): https://github.com/ddso-utn/api-megasuper-2026
- `ddso-utn/ejercicio-megasuper-2026` (Clases 04 a 07, 09, 10 y PRs de estado global): https://github.com/ddso-utn/ejercicio-megasuper-2026
- `ddso-utn/clase-cirbnb` (referencia de integración front-back adaptada pedagógicamente a MegaSuper): https://github.com/ddso-utn/clase-cirbnb/tree/evolutivo-8-integracion

> Contexto/indice de recursos: ver `./BITACORA_CURSO.md`.

---

## Clase 01 - Proceso, arquitectura, JavaScript, Node.js y NPM

Fuente teórica:
- PDF local: `Clases_Teoria/1C2026 - DDSW - MN - Clase 1 - Resumen.pdf`
- Cache textual: `_cache_pdf_text/1C2026 - DDSW - MN - Clase 1 - Resumen.txt`
- PDF práctica JS: `Clases_Practica/Clase Práctica - 01 - Js.pdf`
- Cache práctica JS: `_cache_pdf_text/Clase Práctica - 01 - Js.txt`
- PDF práctica NPM: `Clases_Practica/Clase Práctica - 01 - Apunte NPM.pdf`
- Cache práctica NPM: `_cache_pdf_text/Clase Práctica - 01 - Apunte NPM.txt`

Fuente de código:
- Repo: https://github.com/ddsw-mn/web-server
- Carpeta local: `_tmp_ddsw_web-server/`

Idea central:
> La primera clase arma el piso: cómo nace el trabajo en software, por qué necesitamos arquitectura, cómo entra JavaScript en frontend/backend, qué aporta Node.js y cómo NPM organiza un proyecto real.

Esta base ayuda a que los temas siguientes tengan sentido: Express, capas, testing y React se apoyan en estas ideas de trabajo, responsabilidades, runtime y dependencias. Cuanto mejor quede este piso, más fácil va a ser conectar lo que viene.

---

### 1) De dónde sale el trabajo: requerimientos -> tickets

#### Problema

En software no se codea "porque sí". Se codea para resolver una necesidad.

Esa necesidad puede venir como:

- un pedido de negocio;
- un bug reportado;
- una mejora técnica;
- una restricción nueva;
- una integración con otro sistema.

#### Concepto

- **Requerimiento funcional**: lo que el sistema debe hacer.
- **Requerimiento no funcional**: restricciones o cualidades del sistema: performance, seguridad, disponibilidad, tecnología, mantenibilidad.
- **Feature**: comportamiento nuevo que agrega valor.
- **Bug**: comportamiento incorrecto.
- **Deuda técnica**: costo acumulado por decisiones rápidas, incompletas o antiguas.
- **Ticket**: unidad concreta de trabajo que permite planificar, ejecutar y validar.

#### Modelo mental

```txt
necesidad del negocio
  -> requerimiento
  -> feature / bug / deuda técnica
  -> ticket
  -> código
  -> release
```

El ticket no es burocracia: es el contrato mínimo para no trabajar a ciegas.

Checklist antes de codear:

- qué hay que lograr;
- cuál es el alcance;
- qué queda afuera;
- criterios de aceptación;
- casos borde;
- prioridad;
- dependencias con otros equipos o sistemas.

#### Error típico

Pensar que un requerimiento no funcional es "detalle".

No, loco. Si te dicen "tiene que soportar 10.000 usuarios concurrentes" o "debe cumplir seguridad X", eso condiciona arquitectura, infraestructura, persistencia y pruebas.

#### Para examen

> Un requerimiento funcional describe comportamiento; uno no funcional describe cualidades o restricciones. Los tickets bajan esos requerimientos a unidades pequeñas y verificables de trabajo.

---

### 2) Metodologías: ordenar el caos

#### Problema

Sin metodología, cada persona trabaja como quiere. Eso escala pésimo: se pisan cambios, se pierde contexto y nadie sabe qué está terminado.

#### Concepto

Las metodologías intentan organizar el flujo de trabajo.

| Metodología | Idea | Ventaja | Riesgo |
|---|---|---|---|
| Cascada | fases secuenciales | previsibilidad | mala adaptación al cambio |
| Iterativo-incremental | ciclos cortos que agregan valor | feedback temprano | si no hay disciplina, improvisación |
| Scrum | sprints + roles + ceremonias | foco y cadencia | ritual vacío si no se entiende |
| Kanban | flujo continuo + tablero | visibilidad del trabajo | si no limitás WIP, se traba |

#### Modelo mental

```txt
Cascada:
relevar -> diseñar -> construir -> probar -> entregar

Iterativo:
pequeño alcance -> construir -> feedback -> ajustar -> siguiente incremento
```

Analogía simple:

- Cascada = diseñar toda la casa antes de poner un ladrillo.
- Iterativo = construir una parte habitable, aprender, y seguir.

#### Error típico

Creer que "ágil" significa "sin planificación".

No. Ágil no es improvisar; es planificar en ciclos más cortos y aprender antes.

---

### 3) Tiempo, deuda técnica y legacy

#### Problema

Todo sistema cambia. Cada cambio agrega valor, pero también puede agregar complejidad.

#### Concepto

- **Deuda técnica**: decisiones que aceleran hoy, pero encarecen mañana.
- **Legacy**: código que sigue funcionando, pero cuesta entender, modificar o probar.

Tradeoff clásico:

```txt
fix rápido ahora -> entrega antes -> más deuda después
fix de fondo    -> tarda más   -> menos costo futuro
```

No toda deuda es mala. A veces tomás deuda conscientemente para llegar a una entrega. Lo grave es no registrarla ni pagarla nunca.

#### Para examen

> La deuda técnica es un costo futuro generado por decisiones técnicas subóptimas. Legacy no significa necesariamente viejo: significa difícil de cambiar con confianza.

---

### 4) Release, ambientes, SemVer y changelog

#### Concepto

- **Release**: versión entregable del software.
- **Ambiente**: lugar donde corre el sistema: desarrollo, testing, staging, producción.
- **Rollback**: volver a una versión anterior si algo falla.

#### SemVer

SemVer usa:

```txt
MAJOR.MINOR.PATCH
```

| Parte | Cuándo cambia | Ejemplo |
|---|---|---|
| PATCH | bugfix retrocompatible | `1.2.1 -> 1.2.2` |
| MINOR | feature retrocompatible | `1.2.1 -> 1.3.0` |
| MAJOR | cambio incompatible | `1.2.1 -> 2.0.0` |

Ejemplo real de versión en `web-server`:
- https://github.com/ddsw-mn/web-server/blob/main/package.json

#### Changelog

Un changelog registra cambios relevantes por versión.

Ejemplo basado en Keep a Changelog:

```md
# Changelog

## [Unreleased]

### Added
- Nueva funcionalidad.

### Fixed
- Corrección de bug.

### Changed
- Cambio de comportamiento.
```

#### Error típico

Versionar "a ojo".

Si rompés compatibilidad y subís solo `PATCH`, estás mintiendo. Y cuando otros dependan de tu componente, los rompés.

---

### 5) Arquitectura: estilos y responsabilidades

#### Problema

A medida que el sistema crece, no alcanza con "que funcione". Necesitás saber dónde vive cada responsabilidad.

#### Concepto

La arquitectura define decisiones estructurales: cómo se organiza el sistema, cómo se comunican sus partes, qué tecnologías se usan y qué tradeoffs se aceptan.

Estilos vistos:

- monolítico;
- cliente-servidor;
- microservicios;
- backend-for-frontend (BFF).

#### Cliente-servidor

La web funciona principalmente así:

```txt
cliente -> request HTTP -> servidor
cliente <- response HTTP <- servidor
```

Ejemplo real en `web-server`: entrada del servidor.

```js
const app = require('./app');

const PORT = 3000;
const HOST = 'localhost';

app.listen(PORT, HOST, () => {
  console.log(`Servidor corriendo en http://${HOST}:${PORT}`);
});
```

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/src/server.js

#### Capas

La clase 01 ya introduce una separación que después se profundiza:

```txt
Route -> Controller -> Service -> Repository
```

- **Routes**: definen endpoints.
- **Controller**: traduce HTTP a llamadas de aplicación.
- **Service**: concentra reglas y casos de uso.
- **Repository**: accede a datos.

Ejemplo real de router:

```js
router.route('/users')
  .get((req, res, next) => userController.getUsers(req, res, next))
  .post((req, res, next) => userController.createUser(req, res, next));

router.route('/users/:code')
  .get((req, res, next) => userController.getUserByCode(req, res, next))
  .put((req, res, next) => userController.updateUserByCode(req, res, next))
  .delete((req, res, next) => userController.deleteUserByCode(req, res, next));
```

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/src/routes/user.router.js

Ejemplo real de service:

```js
createUser(payload) {
  if (!payload.name || !payload.mail || !payload.code) {
    throw new UserMissingFieldsError(payload);
  }
  if (this.userRepository.getUserByCode(payload.code)) {
    throw new UserAlreadyExistsError(payload.code);
  }
  return this.userRepository.createUser(payload);
}
```

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/src/services/user.service.js

#### Por qué importa

Separar responsabilidades permite:

- testear mejor;
- cambiar persistencia sin romper HTTP;
- evitar controllers gigantes;
- reducir acoplamiento;
- entender el flujo de un caso de uso.

---

### 6) JavaScript: qué es y por qué importa

#### Concepto

JavaScript nace como lenguaje de scripting para dar dinamismo al navegador. Hoy es de propósito general.

Características importantes:

- scripting;
- débil y dinámicamente tipado;
- multiparadigma;
- funciones de primera clase;
- objetos basados en prototipos;
- monohilo;
- naturalmente apoyado en asincronismo.

#### Navegador vs servidor

En navegador:

```txt
HTML -> DOM -> JavaScript manipula/interactúa
```

Ejemplo:

```html
<script src="index.js"></script>
```

En servidor, JavaScript necesita un runtime.

Ahí aparece Node.js.

---

### 7) Node.js: JavaScript fuera del navegador

#### Problema

Originalmente JavaScript vivía principalmente en el navegador. Si querías backend, normalmente usabas otros lenguajes: Java, PHP, Python, Ruby, etc.

#### Concepto

**Node.js** es un entorno de ejecución que permite usar JavaScript fuera del navegador, principalmente del lado servidor.

En pocas palabras:

- antes JS se usaba sobre todo en frontend;
- con Node.js podés crear servidores, APIs, herramientas CLI, scripts y aplicaciones backend;
- permite usar el mismo lenguaje en frontend y backend.

#### Ideas clave

- Usa el motor **V8**, el mismo motor de JavaScript de Chrome.
- Está pensado para I/O no bloqueante y un modelo basado en eventos.
- Es muy usado en APIs, aplicaciones web, herramientas de desarrollo y sistemas en tiempo real.

Modelo mental:

```txt
JavaScript = lenguaje
V8         = motor que ejecuta JS
Node.js    = runtime que suma APIs de sistema: fs, http, process, etc.
NPM        = gestor de paquetes del ecosistema
```

#### Ejemplo mínimo

Servidor HTTP básico con Node/Express:

```js
const express = require('express');
const app = express();

app.get('/ping', (req, res) => {
  res.json({ message: 'pong' });
});

app.listen(3000);
```

#### Ejemplo real del repo

`web-server` usa Node.js para levantar un servidor Express.

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/src/server.js
- https://github.com/ddsw-mn/web-server/blob/main/src/app.js

#### Error típico

Confundir JavaScript, Node.js y NPM.

No son lo mismo:

- JavaScript es el lenguaje.
- Node.js es el runtime.
- NPM es el gestor de paquetes/proyectos.

---

### 8) NPM: proyecto, dependencias y scripts

#### Concepto

NPM cumple tres roles:

- gestor de paquetes;
- gestor de dependencias;
- herramienta para scripts de proyecto.

#### Inicializar proyecto

```bash
npm init
```

Lanza un asistente que pregunta:

- nombre;
- versión;
- descripción;
- entry point;
- comando de tests;
- repositorio;
- keywords;
- autor;
- licencia.

Versión rápida:

```bash
npm init -y
```

Esto genera `package.json`.

#### `package.json`

Define metadata, scripts y dependencias.

Ejemplo real:

```json
{
  "name": "web-server",
  "version": "1.0.0",
  "scripts": {
    "start": "node src/server.js"
  },
  "dependencies": {
    "cors": "^2.8.6",
    "express": "^5.2.1"
  }
}
```

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/package.json

#### Dependencias

```bash
npm install express
npm install nodemon --save-dev
npm install
```

- `dependencies`: necesarias para correr la app.
- `devDependencies`: necesarias para desarrollo/testing/tooling.
- `package-lock.json`: fija versiones exactas resueltas.
- `node_modules/`: dependencias instaladas; NO se versiona.

#### CommonJS vs ES Modules

CommonJS:

```js
const express = require('express');
```

ES Modules:

```js
import express from 'express';
```

Para ES Modules en Node, suele configurarse:

```json
{
  "type": "module"
}
```

#### Scripts

```json
{
  "scripts": {
    "start": "node index.js",
    "dev": "nodemon index.js"
  }
}
```

Se ejecutan con:

```bash
npm run dev
npm start
```

#### Para examen

> NPM permite inicializar proyectos Node, instalar dependencias, fijar versiones y definir scripts reproducibles. `package.json` describe el proyecto; `package-lock.json` fija resoluciones exactas; `node_modules` se regenera y no se versiona.

---

### 9) Resumen mental de Clase 01

Si te preguntan "qué piso deja la Clase 01?", contestá:

> La Clase 01 introduce cómo se organiza el trabajo en software desde requerimientos y tickets, por qué necesitamos metodologías y arquitectura, y cómo JavaScript pasa de ser un lenguaje del navegador a poder usarse en backend gracias a Node.js. Además, NPM permite inicializar proyectos, manejar dependencias, scripts y versiones, que son la base para construir servidores como el `web-server` usado en clase.

Checklist para examen:

- Requerimiento funcional = comportamiento; no funcional = cualidad/restricción.
- Ticket = unidad pequeña de trabajo verificable.
- Deuda técnica = costo futuro por decisiones técnicas subóptimas.
- Legacy = difícil de modificar con confianza, no simplemente "viejo".
- SemVer = `MAJOR.MINOR.PATCH`.
- Arquitectura = decisiones estructurales y separación de responsabilidades.
- Cliente-servidor = cliente pide, servidor responde.
- Capas = route/controller/service/repository.
- JavaScript = lenguaje; Node.js = runtime; NPM = gestor de paquetes/proyecto.
- `npm init` crea `package.json`.
- `package-lock.json` fija versiones exactas.
- `node_modules` no se versiona.

---

## Clase 02 - HTTP/REST, asincronismo y Git

Fuente teórica:
- PDF local: `Clases_Teoria/1C2026 - DDSW - MN - Clase 2 - Resumen.pdf`
- Cache textual: `_cache_pdf_text/1C2026 - DDSW - MN - Clase 2 - Resumen.txt`
- PDF práctica async: `Clases_Practica/Clase Práctica - 02 - ASYNC en JS.pdf`
- Cache práctica async: `_cache_pdf_text/Clase Práctica - 02 - ASYNC en JS.txt`
- PDF práctica Git: `Clases_Practica/Clase Práctica - 02 - GIT.pdf`
- Cache práctica Git: `_cache_pdf_text/Clase Práctica - 02 - GIT.txt`

Fuente de código:
- Repo async: https://github.com/ddso-utn/ejemplo-async
- Carpeta local: `_tmp_ddso_ejemplo-async/`
- Repo web-server: https://github.com/ddsw-mn/web-server

Idea central:
> La Clase 02 une tres bases que después aparecen todo el tiempo: HTTP/REST para comunicar cliente-servidor, asincronismo para no bloquear operaciones lentas en JavaScript, y Git para trabajar en paralelo sin destruir el historial del proyecto.

Esta clase funciona como puente: HTTP te permite entender APIs, el asincronismo te ayuda a razonar backend en Node, y Git te da una forma ordenada de trabajar con otras personas sin perder trazabilidad.

---

### 1) HTTP: protocolo de comunicación cliente-servidor

#### Problema

Cliente y servidor necesitan una forma común de hablarse. No alcanza con "mandar datos": tienen que acordar formato, intención, headers, códigos y cuerpo del mensaje.

#### Concepto

HTTP significa **HyperText Transfer Protocol**. Define cómo viajan requests y responses entre cliente y servidor.

Request típico:

```http
GET /users HTTP/1.1
Host: localhost:3000
Accept: application/json
```

Partes de un request:

- método/verbo;
- URI;
- headers;
- body opcional.

Response típico:

```http
HTTP/1.1 200 OK
Content-Type: application/json

[{ "code": "123", "name": "Ada" }]
```

#### Modelo mental

```txt
cliente
  -> request: método + URI + headers + body
servidor
  -> response: status code + headers + body
```

#### Formatos de mensaje

La clase menciona formatos habituales:

- **JSON**: JavaScript Object Notation. El más usado en APIs web modernas.
- **XML**: eXtensible Markup Language. Más verboso, común en integraciones antiguas/enterprise.
- **YAML**: Yet Another Markup Language. Muy usado para configuración.

Ejemplo JSON:

```json
{
  "code": "999.999-9",
  "name": "Ada",
  "mail": "ada@utn.edu.ar"
}
```

#### Para examen

> HTTP es el protocolo que define cómo cliente y servidor intercambian mensajes: método, ruta, headers, body y código de respuesta.

---

### 2) API: contrato de comunicación

#### Concepto

Una **API** es una interfaz para comunicarse con un sistema.

Define:

- qué rutas existen;
- qué verbos se usan;
- qué formato tienen los mensajes;
- qué códigos se devuelven;
- qué errores pueden aparecer.

No es solo "un endpoint". Es un contrato.

#### Ejemplo

```txt
GET    /users          -> listar usuarios
POST   /users          -> crear usuario
GET    /users/:code    -> obtener usuario
PUT    /users/:code    -> reemplazar usuario
DELETE /users/:code    -> eliminar usuario
```

Fuente real:
- https://github.com/ddsw-mn/web-server/blob/main/src/routes/user.router.js

#### Error típico

Diseñar una API como si fueran acciones sueltas:

```txt
/crearUsuario
/borrarUsuario
/traerUsuario
```

En REST conviene pensar en recursos:

```txt
/users
/users/:code
```

---

### 3) Métodos HTTP y su intención

Mapeo mental con CRUD:

| Método | Intención | Body típico | Idempotencia |
|---|---|---|---|
| GET | leer | no | sí |
| POST | crear | sí | no necesariamente |
| PUT | reemplazar completo | sí | sí |
| PATCH | modificar parcial | sí | depende |
| DELETE | eliminar | no o mínimo | sí |

Otros menos usados en esta materia:

- `HEAD`;
- `OPTIONS`;
- `CONNECT`.

#### Idempotencia

Una operación es idempotente si repetirla deja el sistema en el mismo estado final.

```txt
PUT /users/123 con el mismo body 3 veces -> mismo usuario final
POST /users con el mismo body 3 veces   -> podría crear 3 usuarios
```

#### Para examen

> El verbo HTTP expresa la intención sobre un recurso. GET lee, POST crea, PUT reemplaza, PATCH modifica parcialmente y DELETE elimina.

---

### 4) Headers, body y cookies

#### Headers

Un header es metadata del mensaje HTTP. Viaja como pares clave/valor.

Ejemplos:

| Header | Para qué sirve |
|---|---|
| `Host` | dominio/host destino |
| `User-Agent` | cliente que realiza el pedido |
| `Accept` | formato esperado en la respuesta |
| `Accept-Language` | idioma preferido |
| `Content-Type` | formato del body enviado |
| `Content-Length` | tamaño del body |
| `Authorization` | credenciales/token |
| `Cookie` | cookies enviadas al servidor |

Ejemplo:

```http
Content-Type: application/json
Accept: application/json
```

#### Body

El body transporta datos adicionales. Suele aparecer en:

- `POST`: datos del recurso nuevo;
- `PUT`: representación completa del recurso;
- `PATCH`: cambios parciales.

Ejemplo:

```http
POST /users HTTP/1.1
Content-Type: application/json

{
  "code": "999.999-9",
  "name": "Ada",
  "mail": "ada@utn.edu.ar"
}
```

#### Cookies

HTTP es stateless: cada request debe traer lo necesario para ser entendido.

Una cookie permite que el servidor mande un pequeño dato al navegador, y que el navegador lo reenvíe después.

Uso típico:

- sesiones de usuario;
- preferencias;
- tracking.

Ojo: las cookies no contradicen que HTTP sea stateless. Lo que pasa es que el estado viaja en cada request o se referencia desde cada request.

---

### 5) Status codes: la respuesta también comunica

Familias:

| Familia | Significado | Ejemplos |
|---|---|---|
| 2xx | éxito | `200 OK`, `201 Created` |
| 4xx | error del cliente | `400 Bad Request`, `404 Not Found`, `409 Conflict` |
| 5xx | error del servidor | `500 Internal Server Error`, `504 Timeout` |

Ejemplos reales:

- `201` al crear recurso:
  - https://github.com/ddsw-mn/web-server/blob/main/src/controllers/user.controller.js

- errores de dominio con `400/404/409`:
  - https://github.com/ddsw-mn/web-server/blob/main/src/errors/user.errors.js

- traducción a HTTP en middleware:
  - https://github.com/ddsw-mn/web-server/blob/main/src/middlewares/error.handler.middleware.js

Ejemplo real:

```js
class UserNotFoundError extends UserError {
  constructor(code) {
    super(404, `Usuario con codigo ${code} no encontrado`);
  }
}
```

Fuente:
- https://github.com/ddsw-mn/web-server/blob/main/src/errors/user.errors.js

Regla de oro:

> No devuelvas `200 OK` con `{ error: ... }`. Eso es mentirle al cliente.

---

### 6) REST: recursos, representaciones y restricciones

#### Concepto

REST significa **Representational State Transfer**. Es un estilo de arquitectura para APIs sobre HTTP.

Una API RESTful respeta restricciones que hacen que sea predecible y evolutiva.

#### Restricciones REST vistas

| Restricción | Idea |
|---|---|
| Cliente-servidor | cliente y servidor evolucionan separados |
| Stateless | cada request trae lo necesario para resolverse |
| Cacheable | la respuesta puede declarar si se cachea |
| Interfaz uniforme | reglas consistentes para recursos y operaciones |
| Sistema en capas | el cliente no sabe si habla con servidor final o intermediario |
| Código bajo demanda | opcional; el servidor puede enviar código ejecutable |

#### Interfaz uniforme

Incluye:

- identificación de recursos mediante URI;
- manipulación mediante representaciones;
- mensajes autodescriptivos;
- HATEOAS: links para navegar estados posibles.

En esta materia lo más importante al principio es:

```txt
recurso plural -> /users
recurso puntual -> /users/:code
verbo HTTP -> intención
status code -> resultado
```

Ejemplo real:
- https://github.com/ddsw-mn/web-server/blob/main/src/routes/user.router.js

Ejemplo didáctico:

```bash
# listar
curl http://localhost:3000/users

# crear
curl -X POST http://localhost:3000/users \
  -H "Content-Type: application/json" \
  -d '{"code":"999.999-9","name":"Ada","mail":"ada@utn.edu.ar"}'

# traer uno
curl http://localhost:3000/users/999.999-9
```

#### Para examen

> REST no es una librería ni un framework: es un estilo de arquitectura para diseñar APIs usando recursos, representaciones, statelessness, interfaz uniforme y HTTP correctamente.

---

### 7) Framework vs Library

La teoría de clase 02 introduce una diferencia que después vuelve con React, Express, Redux, Spring, etc.

#### Library

Una biblioteca es una herramienta que tu código llama para resolver algo puntual.

Ejemplos:

- Material UI: importás componentes;
- una librería de fechas;
- una librería de validación.

Modelo:

```txt
tu código -> llama a la library
```

#### Framework

Un framework define una forma de trabajar. No solo lo llamás: también te impone reglas, estructura y ciclo de vida.

Ejemplos:

- Spring;
- Next.js;
- Express, en sentido práctico, para estructurar servidores HTTP;
- Redux como herramienta con reglas fuertes para estado.

Modelo:

```txt
framework -> define reglas -> tu código encaja ahí
```

#### Diferencia clave

> En una library, vos tenés el control y llamás a la herramienta. En un framework, la herramienta define el marco y tu código se adapta.

---

### 8) Asincronismo en JS: por qué existe

#### Problema

JavaScript ejecuta código en un solo hilo principal. Si una operación lenta bloqueara ese hilo, toda la aplicación quedaría congelada.

Operaciones lentas típicas:

- llamar una API;
- leer un archivo;
- consultar una base de datos;
- esperar un timer;
- escribir en disco.

#### Concepto

JavaScript es **single-threaded**, pero puede manejar tareas asincrónicas para no bloquear el programa.

Comparación:

| Modelo | Qué pasa |
|---|---|
| Síncrono | ejecuta línea por línea y espera cada operación |
| Asíncrono | inicia una tarea lenta y sigue ejecutando mientras espera resultado |

Modelo mental:

```txt
código síncrono -> se ejecuta ahora
operación lenta -> se delega
resultado async -> vuelve después por callback/promesa
```

#### Ejemplo mínimo

```js
console.log('Antes');

setTimeout(() => {
  console.log('Timer resuelto');
}, 1000);

console.log('Después');
```

Salida:

```txt
Antes
Después
Timer resuelto
```

No es magia. Es asincronismo: el timer no bloquea el flujo principal.

---

### 9) Event Loop: la base del modelo async

#### Concepto

El event loop coordina cuándo se ejecuta cada tarea.

Piezas principales:

- **Call Stack**: pila donde se ejecuta el código síncrono.
- **Web APIs / APIs del runtime**: donde se delegan timers, I/O, red, etc.
- **Task Queue / Callback Queue**: cola de macrotareas, como `setTimeout`.
- **Microtask Queue**: cola de microtareas, como callbacks de promesas.
- **Event Loop**: mueve tareas a ejecución cuando el stack está libre.

#### Flujo

```txt
1. JS ejecuta código síncrono en el Call Stack.
2. Una tarea async se delega al runtime.
3. Cuando termina, su callback queda en una cola.
4. El Event Loop espera que el Call Stack esté vacío.
5. Ejecuta primero microtasks y luego macrotasks.
```

Diagrama:

```txt
Call Stack vacío?
      |
      v
Microtask Queue tiene tareasí -> ejecutar microtasks
      |
      v
Task Queue tiene tareasí      -> ejecutar una macrotask
      |
      v
repetir
```

#### Microtasks vs macrotasks

```js
console.log('A');

setTimeout(() => console.log('B timeout'), 0);

Promise.resolve().then(() => console.log('C promise'));

console.log('D');
```

Orden esperado:

```txt
A
D
C promise
B timeout
```

¿Por qué? Porque las promesas van a microtask queue, y las microtasks tienen prioridad sobre macrotasks como `setTimeout`.

---

### 10) Callbacks: la base histórica

#### Concepto

Un callback es una función que se pasa como argumento para ejecutarse después.

Ejemplo simple:

```js
function sumar(a, b, callback) {
  const resultado = a + b;
  callback(resultado);
}

sumar(2, 3, (resultado) => {
  console.log(resultado);
});
```

#### Ejemplo real del repo async

```js
console.log("Esto está antes del llamado asíncrono.")

setTimeout(function() {
    console.log("1. Tarea asíncrona resuelta.")
    setTimeout(function() {
        console.log("2. Tarea asíncrona resuelta.")
        setTimeout(function() {
            console.log("3. Tarea asíncrona resuelta.")
        }, 1000)
    }, 1000)
}, 1000)

console.log("Esto está después del llamado asíncrono.")
```

Fuente:
- https://github.com/ddso-utn/ejemplo-async/blob/main/callbacks.js

#### Problema: callback hell

Cuando se anidan callbacks, el código se vuelve difícil de leer y mantener.

```js
getData(function(a) {
  getMoreData(a, function(b) {
    getEvenMoreData(b, function(c) {
      console.log(c);
    });
  });
});
```

Problemas:

- indentación creciente;
- manejo de errores disperso;
- flujo difícil de razonar;
- composición pobre.

---

### 11) Promesas: representar un resultado futuro

#### Concepto

Una promesa representa un valor que todavía no está disponible.

Estados:

```txt
pending -> fulfilled
pending -> rejected
```

Ejemplo mínimo:

```js
const promesa = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('ok');
  }, 1000);
});

promesa
  .then((result) => console.log(result))
  .catch((error) => console.log(error))
  .finally(() => console.log('fin'));
```

#### Ejemplo real del repo

```js
function tareaAsincrona() {
    return new Promise((resolve, reject) => {
        const random = Math.random()
        if (random <= 1) {
            resolve("Datos obtenidos.")
        } else {
            reject("Consulta fallida.")
        }
    })
}
```

Fuente:
- https://github.com/ddso-utn/ejemplo-async/blob/main/promises.js

Uso con chaining:

```js
tareaAsincrona().then(d => {
    console.log("1." + d)
    return tareaAsincrona()
}).then((d) => {
    console.log("2." + d)
    return tareaAsincrona()
}).catch((e) =>{
    console.log(e)
}).finally(() => {
    console.log("Esto se ejecuta siempre.")
})
```

#### Lectura

```txt
tareaAsincrona()
  -> si resuelve: then
  -> si falla: catch
  -> siempre: finally
```

#### Error típico

Olvidar `return` dentro de un `.then()` cuando querés encadenar otra promesa.

```js
// MAL si querés esperar la segunda tarea
.then(() => {
  tareaAsincrona();
})

// BIEN
.then(() => {
  return tareaAsincrona();
})
```

---

### 12) Métodos importantes de Promesas

| Método | Qué hace | Cuándo usarlo |
|---|---|---|
| `Promise.all` | espera que todas resuelvan; si una falla, falla todo | tareas paralelas obligatorias |
| `Promise.race` | devuelve la primera que termine, resuelta o rechazada | timeouts/competencia |
| `Promise.allSettled` | espera todas, sin importar si fallan | reporte completo de resultados |
| `Promise.any` | devuelve la primera que resuelva bien | alternativas donde alcanza una |

Ejemplo:

```js
const [usuarios, productos] = await Promise.all([
  obtenerUsuarios(),
  obtenerProductos()
]);
```

Esto ejecuta ambas tareas en paralelo.

---

### 13) Async/Await: sintaxis moderna sobre promesas

#### Concepto

`async/await` permite escribir código asincrónico con apariencia secuencial.

- `async` hace que una función devuelva una promesa.
- `await` espera la resolución de una promesa dentro de una función `async`.

Ejemplo mínimo:

```js
async function getData() {
  const response = await fetch('https://example.com/api');
  const data = await response.json();
  return data;
}
```

#### Ejemplo real del repo

```js
async function obtenerUsuarios() {
    let data
    try {
        const response = await fetch(`https://jsonplaceholder.typicode.com/users`)
        data = await response.json()
    } catch {
        data = { error: "Error al obtener los datos." }
    }
    return data
}
```

Fuente:
- https://github.com/ddso-utn/ejemplo-async/blob/main/async-await.js

#### Manejo de errores

```js
async function getData() {
  try {
    const res = await fetch('https://example.com/api');
    return await res.json();
  } catch (error) {
    console.log(error);
    throw error;
  }
}
```

`await` convierte rechazos de promesas en errores atrapables con `try/catch`.

#### Secuencial vs paralelo

Secuencial:

```js
const usuarios = await obtenerUsuarios();
const productos = await obtenerProductos();
```

Paralelo:

```js
const [usuarios, productos] = await Promise.all([
  obtenerUsuarios(),
  obtenerProductos()
]);
```

Tradeoff:

```txt
secuencial -> más simple, pero puede ser más lento
paralelo   -> mejor performance si las tareas son independientes
```

#### Para examen

> `async/await` no reemplaza las promesas: es sintaxis más legible construida sobre promesas.

---

### 14) Evolución del asincronismo

La clase muestra esta evolución:

```txt
callbacks
  -> funcionan, pero anidados complican lectura y errores
promesas
  -> representan resultado futuro y permiten chaining
async/await
  -> sintaxis más clara sobre promesas
```

Diagrama:

```txt
operación lenta
    |
    +-- callback: "avisame cuando termines"
    |
    +-- promise: "te devuelvo un resultado futuro"
    |
    `-- async/await: "escribo promesas como si fueran secuenciales"
```

#### Backend real

Persistencia en archivo con callbacks:
- https://github.com/ddsw-mn/web-server/blob/users-archivo-callback/src/repositories/user.repository.js

Persistencia en archivo con promesas:
- https://github.com/ddsw-mn/web-server/blob/users-archivo-promises/src/repositories/user.repository.js

Idea clave: leer/escribir archivos es I/O. Por eso el asincronismo importa en backend.

---

### 15) Git avanzado: ramas, merge, squash y rebase

#### Ramas

Una rama es un espacio de trabajo paralelo.

```bash
git switch -c feature/login
```

Modelo:

```txt
main:    A---B---C
              \
feature:       D---E
```

Sirve para aislar cambios hasta que estén listos.

#### Merge normal

Fusiona dos historias y puede crear un merge commit.

```bash
git switch main
git merge feature/login
```

Diagrama:

```txt
main:    A---B---C-------M
              \       /
feature:       D---E---
```

Ventaja: conserva historia real.

Costo: historial más ruidoso.

#### Merge squash

Combina todos los commits de una rama en un único commit al integrarla.

```bash
git switch main
git merge --squash feature/login
git commit -m "feat: add login"
```

Diagrama:

```txt
feature: D---E---F
              |
              v
main: A---B---C---S
              S = un commit con todo el cambio
```

Ventaja: historial limpio.

Costo: se pierde detalle fino de commits intermedios.

#### Rebase

Reaplica tus commits arriba de otra base.

```bash
git switch feature/login
git rebase main
```

Antes:

```txt
main:    A---B---C
              \
feature:       D---E
```

Después:

```txt
main:    A---B---C
                  \
feature:           D'---E'
```

Ventaja: historial lineal.

Costo: reescribe historia. Si no entendés qué estás haciendo, podés complicar a todo el equipo.

Regla mental:

> Si no podés explicar qué commits va a reescribir un rebase, no lo uses en caliente.

---

### 16) GitFlow vs GitHub Flow

La práctica menciona ambos flujos. No son comandos: son estrategias de trabajo.

#### GitFlow

Pensado para releases más formales.

Ramas típicas:

```txt
main      -> producción
master    -> producción (nombre histórico)
develop   -> integración
feature/* -> desarrollo de features
release/* -> preparación de release
hotfix/*  -> arreglo urgente de producción
```

Diagrama:

```txt
main:     A--------------------R----H
           \                  /    /
develop:    B---C---D--------E----
             \     \        /
feature:      f1    f2-----
```

Ventaja:

- ordena releases grandes;
- separa desarrollo, release y producción.

Costo:

- más ramas;
- más ceremonia;
- puede ser pesado para equipos chicos o deploy continuo.

#### GitHub Flow

Más simple. Ideal para integración continua y deploy frecuente.

```txt
main -> branch corta -> Pull Request -> review/checks -> merge -> deploy
```

Diagrama:

```txt
main:    A---B---C---M---N
              \     /
feature:       D---E
```

Ventaja:

- simple;
- rápido;
- cada cambio pasa por PR;
- encaja bien con CI/CD.

Costo:

- requiere buena disciplina de tests/reviews;
- si `main` no está protegido, se rompe fácil.

#### Diferencia breve

| Aspecto | GitFlow | GitHub Flow |
|---|---|---|
| Complejidad | alta/media | baja |
| Rama de integración | `develop` | no, se usa `main` |
| Releases | planificadas | frecuentes/continuas |
| Ideal para | ciclos formales | equipos ágiles con CI/CD |

---

### 17) Pull Requests, protección de ramas, tags y releases

#### Pull Request

Un PR es una propuesta de cambio.

Sirve para:

- revisar código;
- discutir decisiones;
- correr checks;
- dejar trazabilidad;
- evitar pushes directos a ramas protegidas.

#### Protección de ramas

En GitHub se puede proteger `main` para exigir:

- PR obligatorio;
- reviews;
- checks verdes;
- CODEOWNERS;
- bloqueo de force push.

Esto no es burocracia: es control de calidad.

#### Tag y release

- **Tag**: marca un commit específico.
- **Release**: publicación versionada, normalmente asociada a un tag.

```bash
git tag v1.2.0
git push origin v1.2.0
```

Relación con SemVer:

```txt
v1.2.0 -> versión identificable -> changelog -> release
```

---

### 18) Gotchas reales de Clase 02

1. **REST no es solo usar JSON**.
   - JSON es formato de mensaje; REST es estilo arquitectónico.

2. **HTTP stateless no significa "sin login"**.
   - Significa que cada request debe traer lo necesario para ser interpretado.

3. **`async/await` no hace que JS tenga varios hilos**.
   - Mejora la escritura de promesas; el modelo sigue basado en event loop.

4. **`Promise.all` no es siempre mejor**.
   - Sirve cuando las tareas son independientes. Si una depende de la otra, va secuencial.

5. **Rebase no es "merge más lindo"**.
   - Reescribe historia. Usarlo mal en ramas compartidas rompe flujos de equipo.

---

### 19) Resumen mental de Clase 02

Si te preguntan "qué une la Clase 02?", contestá:

> La Clase 02 explica cómo se comunican cliente y servidor mediante HTTP, cómo diseñar APIs REST usando recursos, verbos, headers, body y status codes, y cómo JavaScript maneja operaciones lentas sin bloquear gracias al event loop, callbacks, promesas y async/await. Además, introduce estrategias de Git para trabajar en equipo: ramas, merge, squash, rebase, GitFlow, GitHub Flow, PRs, tags y releases.

Checklist para examen:

- HTTP define request/response: método, URI, headers, body y status code.
- API = contrato de comunicación.
- REST = estilo arquitectónico, no framework.
- Recursos en plural: `/users`; elemento: `/users/:id`.
- GET lee, POST crea, PUT reemplaza, PATCH modifica parcial, DELETE elimina.
- 2xx éxito, 4xx error cliente, 5xx error servidor.
- Headers son metadata; body lleva datos.
- Cookies ayudan a manejar sesión/preferencias sobre HTTP stateless.
- Library = la llamás vos; framework = define el marco de trabajo.
- JS es single-threaded, pero no bloqueante para I/O gracias al event loop.
- Microtasks de promesas tienen prioridad sobre macrotasks como `setTimeout`.
- Callbacks son base histórica; promesas representan resultado futuro; async/await es sintaxis sobre promesas.
- `Promise.all` paraleliza tareas independientes.
- Merge conserva historia; squash compacta; rebase reescribe base.
- GitFlow es más formal; GitHub Flow es más simple y orientado a PR + CI/CD.

---

## Clase 03 - API MegaSuper: REST, Express y primeras decisiones de arquitectura

Fuente teórica:
- PDF local: `Clases_Teoria/1C2026 - DDSW - MN - Clase 3 - Resumen.pdf`
- PDF local: `Clases_Teoria/Clase 3 - Promesas.pdf`
- Cache textual: `_cache_pdf_text/1C2026 - DDSW - MN - Clase 3 - Resumen.txt`
- Cache textual: `_cache_pdf_text/Clase 3 - Promesas.txt`

Fuente práctica / código:
- Repositorio: https://github.com/ddso-utn/api-megasuper-2026/tree/main
- Carpeta local de consulta: `./_tmp_ddso_api-megasuper-2026`
- Archivo principal: `./_tmp_ddso_api-megasuper-2026/index.js`
- Colección Postman: `./_tmp_ddso_api-megasuper-2026/docs/megasuper.postman_collection.json`

Idea central:
> Esta clase baja HTTP/REST a una API concreta de productos y, desde la teoría, empieza a ordenar cómo conviene separar responsabilidades para que el backend no sea "todo junto en un archivo".

Por qué importa:
Venimos de entender HTTP, APIs y asincronismo. En esta clase eso se ve funcionando: Express recibe requests, las rutas representan recursos, Zod valida contratos y los status codes comunican resultados. La teoría suma el criterio arquitectónico: hoy puede estar todo en `index.js` para aprender, pero a medida que crece el sistema necesitamos separar controller, service y repository.

---

### 1) Qué suma la teoría de Clase 03

La parte teórica trabaja tres ideas que conviene tener presentes mientras miramos el código:

1. **Arquitectura por capas**: separar responsabilidades para que no quede todo mezclado.
2. **Manejo de errores en APIs REST**: responder errores claros, con status code correcto y sin exponer detalles internos.
3. **Promesas y asincronismo**: entender cómo JavaScript maneja tareas que no terminan inmediatamente, especialmente llamadas a APIs externas.

No hace falta profundizar todo de nuevo acá: HTTP y asincronismo ya venían de clases anteriores, y capas se trabaja fuerte en la Clase 04. Pero sí importa ver cómo estas ideas empiezan a aparecer en MegaSuper.

---

### 2) Arquitectura por capas: por qué no alcanza con "que funcione"

#### Problema

Podemos escribir una API completa en un solo archivo. De hecho, el repo de esta clase lo hace para que sea fácil seguir el flujo.

El problema aparece cuando el sistema crece: si en el mismo lugar recibís HTTP, validás datos, aplicás reglas de negocio y guardás información, cualquier cambio toca todo.

#### Concepto

La teoría propone separar responsabilidades en capas:

| Capa | Responsabilidad | Ejemplo típico |
|---|---|---|
| Presentación / Controller | Recibir requests HTTP, leer params/body/query, devolver responses | `ProductoController` |
| Dominio / Service | Resolver reglas de negocio y orquestar casos de uso | `ProductoService` |
| Persistencia / Repository | Guardar o consultar datos en una fuente externa | `ProductoRepository` |

Modelo mental:

```txt
request HTTP
  -> controller
  -> service
  -> repository / cliente externo
  -> service
  -> controller
  -> response HTTP
```

#### Ejemplo real del repo

En `index.js` todavía está todo junto:

```txt
Express + rutas + validaciones + reglas + array en memoria
```

Eso está bien para una clase introductoria: permite ver toda la API sin saltar entre archivos. Pero también deja preparado el problema que se corrige en la clase siguiente: separar la API en capas.

Fuente:
- `./_tmp_ddso_api-megasuper-2026/index.js`
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js

#### Error típico

Creer que "arquitectura por capas" significa crear carpetas porque sí. No. Una capa suma valor si protege una responsabilidad. Si solo mueve código de lugar pero sigue todo acoplado, no mejoraste el diseño: solo lo repartiste.

#### Para examen

> Separar en capas permite que el controller maneje HTTP, el service concentre negocio y el repository resuelva acceso a datos. La ventaja es menor acoplamiento, mejor testeo y cambios más localizados.

---

### 3) Express: de programa JS a servidor HTTP

#### Problema

Node.js por sí solo permite ejecutar JavaScript, pero necesitamos una forma cómoda de declarar endpoints HTTP.

#### Concepto

Express es un **framework web minimalista para Node.js** que permite declarar rutas HTTP, usar middlewares y asociar cada endpoint a funciones que reciben `req` y `res`.

En el repo se ve el armado mínimo:

```js
import express from "express"

const app = express()
app.use(express.json())

app.listen(3000, () => {
  console.log("Servidor inicializado")
})
```

Qué hace cada parte:
- `express()` crea la aplicación web.
- `app.use(express.json())` habilita lectura de JSON en el body.
- `app.listen(...)` levanta el servidor.

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L1-L7
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L155-L158

#### Error típico

Olvidarte de `express.json()`. Resultado: el backend recibe la request, pero `req.body` no queda parseado como esperás. Es una pavada chiquita, pero te rompe todos los `POST` y `PUT`.

---

### 4) Recurso REST: productos

REST se organiza alrededor de **recursos**. En esta API el recurso principal es:

```txt
/v1/productos
```

La constante del repo lo deja explícito:

```js
const PATH_PRODUCTOS_V1 = "/v1/productos"
```

Por qué `/v1` importa:
- versiona la API;
- permite cambiar el contrato en el futuro sin romper clientes viejos;
- hace explícito que una URL es parte de un contrato público.

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L4

Regla práctica:
- Recurso en plural: `/productos`.
- Versión delante: `/v1/productos`.
- Método HTTP para expresar la operación: `GET`, `POST`, `PUT`, `DELETE`.

---

### 5) Healthcheck: endpoint técnico

Un healthcheck responde si el servidor está vivo.

En el repo:

```js
app.get("/v1/healthcheck", (req, res) => {
  res.json({ status: "ok" })
})
```

Concepto:
- No es una regla de negocio de MegaSuper.
- Es un endpoint técnico para monitoreo o pruebas rápidas.

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L46-L50

Gotcha real:
- En la colección Postman aparece `localhost:3000/healthcheck`, pero el código expone `/v1/healthcheck`.
- Si no coincide ruta-documentación-código, alguien pierde tiempo probando mal.

Fuente Postman:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/docs/megasuper.postman_collection.json

---

### 6) GET collection: listar productos

Endpoint:

```http
GET /v1/productos
```

En el repo devuelve el array `productos`.

Ejemplo conceptual:

```js
app.get("/v1/productos", (req, res) => {
  res.json(productos)
})
```

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L52-L69

Concepto REST:
- `GET` lee recursos.
- No debería modificar estado.
- Devuelve `200 OK` por defecto si usás `res.json(...)` sin setear otro status.

---

### 7) Query params: filtros sin cambiar el recurso

La API permite filtrar productos por:
- `precio_lt`
- `categoria`

Ejemplos:

```http
GET /v1/productosíprecio_lt=3000
GET /v1/productosícategoria=Bebidas
GET /v1/productosíprecio_lt=3000&categoria=Bebidas
```

Código equivalente:

```js
const precioMenorQue = req.query.precio_lt
const categoria = req.query.categoria

let resultado = productos

if (precioMenorQue) {
  resultado = resultado.filter(p => p.precioBase < precioMenorQue)
}

if (categoria) {
  resultado = resultado.filter(p => p.categoria === categoria)
}
```

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L52-L68

Concepto:
- Query params sirven para búsquedas, filtros, orden o paginación.
- No identifican un recurso puntual; ajustan la representación devuelta.

Gotcha técnico:
- `req.query.precio_lt` llega como string.
- JavaScript puede hacer coerción en `<`, pero para una API prolija conviene convertir explícitamente:

```js
const precio = Number(req.query.precio_lt)
```

---

### 8) Route params: identificar un recurso puntual

Endpoint:

```http
GET /v1/productos/:id
```

Ejemplo:

```http
GET /v1/productos/0
```

Código conceptual:

```js
const id = req.params.id
const producto = productos[id]

if (!producto) {
  return res.status(404).json({ error: "PRODUCTO_NO_ENCONTRADO" })
}

return res.json(producto)
```

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L71-L79

Concepto:
- `params` vienen de la ruta.
- `query` viene después de `?`.

Comparación rápida:

```txt
/v1/productos/0              -> params.id = "0"
/v1/productosícategoria=...  -> query.categoria = "..."
```

Gotcha real del repo:
- El código hace `res.status(404); return;`.
- Eso setea el status, pero no envía la respuesta. En Express conviene cerrar con `json`, `send` o `end`.

Mejor:

```js
return res.status(404).json({ error: "PRODUCTO_NO_ENCONTRADO" })
```

---

### 9) Body JSON y validación con Zod

Para crear o reemplazar productos, el cliente manda JSON en el body.

El repo define el contrato del producto con Zod:

```js
const productSchema = z.object({
  nombre: z.string().min(3).max(10),
  descripcion: z.string(),
  precioBase: z.number().nonnegative(),
  categoria: z.enum(["Bebidas", "Alimentos"]),
})
```

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L9-L14

Concepto:
- El cliente no manda "lo que quiere".
- La API define un contrato.
- Validar en backend es obligatorio, aunque el frontend también valide.

Ejemplo válido:

```json
{
  "nombre": "Pepsi",
  "precioBase": 2500,
  "descripcion": "1,5lt",
  "categoria": "Bebidas"
}
```

Ejemplo inválido:

```json
{
  "nombre": "P",
  "precioBase": -10,
  "descripcion": "x",
  "categoria": "Limpieza"
}
```

Esto debería terminar en `400 Bad Request`.

---

### 10) POST: crear producto

Endpoint:

```http
POST /v1/productos
```

Intención:
- Crear un nuevo recurso dentro de la colección.

Flujo correcto:

1. Leer `req.body`.
2. Validar schema.
3. Verificar conflicto de negocio.
4. Insertar.
5. Responder `201 Created`.

En el repo se ve:
- validación con `safeParse`;
- `400` si body inválido;
- `409` si ya existe producto con mismo nombre + categoría;
- `201` si se crea.

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L81-L107

Versión pedagógica prolija:

```js
app.post(PATH_PRODUCTOS_V1, (req, res) => {
  const result = productSchema.safeParse(req.body)

  if (!result.success) {
    return res.status(400).json(result.error.issues)
  }

  const nuevoProducto = result.data
  const existe = productos.some(p =>
    p.nombre === nuevoProducto.nombre &&
    p.categoria === nuevoProducto.categoria
  )

  if (existe) {
    return res.status(409).json({ error: "PRODUCTO_EXISTENTE" })
  }

  productos.push(nuevoProducto)
  return res.status(201).json(nuevoProducto)
})
```

Gotcha real del repo:
- En `POST`, después de responder `400` o `409`, falta cortar el flujo con `return`.
- Si no cortás, el handler puede seguir ejecutando e intentar usar datos inválidos o mandar otra respuesta.
- Este es un bug clásico de Express: responder no significa automáticamente "terminar la función".

---

### 11) PUT: reemplazar recurso completo

Endpoint:

```http
PUT /v1/productos/:id
```

Intención:
- Reemplazar el producto completo identificado por `id`.

En el repo:
- valida body con Zod;
- si el producto no existe responde `404`;
- si hay conflicto de nombre/categoría responde `409`;
- si todo va bien responde `200`.

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L109-L146

Concepto fuerte:
- `PUT` no es "actualizar cualquier campito".
- Para eso suele usarse `PATCH`.
- `PUT` representa reemplazo completo.

Ejemplo conceptual:

```http
PUT /v1/productos/0
Content-Type: application/json

{
  "nombre": "Sprite",
  "precioBase": 2700,
  "descripcion": "2lt",
  "categoria": "Bebidas"
}
```

---

### 12) DELETE: eliminar recurso

Endpoint:

```http
DELETE /v1/productos/:id
```

En el repo:

```js
productos.splice(id, 1)
res.status(204)
res.send()
```

Fuente:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/index.js#L148-L153

Concepto:
- `204 No Content` significa: salió bien, pero no hay body.

Mejora recomendada:

```js
if (!productos[id]) {
  return res.status(404).json({ error: "PRODUCTO_NO_ENCONTRADO" })
}

productos.splice(id, 1)
return res.status(204).send()
```

Por qué:
- si borrás un id inexistente, el cliente debería enterarse;
- si no, la API responde éxito aunque no haya borrado nada;
- además conviene validar que `id` sea un número aceptable antes de usarlo como índice.

---

### 13) Manejo de errores en REST: criterio mínimo

La teoría deja el manejo de errores como tema a profundizar después, pero ya aparece una regla clave:

```txt
error por datos del request -> familia 4XX
error inesperado del servidor -> familia 5XX
```

En esta API aparecen varios casos:

| Caso | Status | Motivo |
|---|---:|---|
| Body inválido | 400 | El cliente mandó datos que no cumplen el contrato |
| Producto inexistente | 404 | El recurso pedido no existe |
| Producto duplicado | 409 | Hay conflicto con una regla de negocio |
| Creación exitosa | 201 | Se creó un nuevo recurso |
| Eliminación exitosa sin body | 204 | La operación salió bien y no devuelve contenido |

Regla sana:
- No devolver stack traces al cliente.
- Tipificar errores esperables.
- Dar información suficiente para que el consumidor pueda corregir o mostrar un mensaje útil.
- Loguear errores críticos del lado servidor.

#### Para examen

> En una API REST, los errores también son parte del contrato. No alcanza con "falló": hay que responder un status correcto y un body entendible cuando corresponde.

---

### 14) Promesas y asincronismo: conexión con APIs

La teoría de Promesas refuerza algo importante para backend y frontend: muchas operaciones no terminan inmediatamente.

Ejemplos:
- llamar a una API externa;
- consultar una base de datos;
- leer un archivo;
- esperar una respuesta de red.

Una promesa representa el resultado futuro de una tarea asincrónica. Puede estar en tres estados:

| Estado | Significado |
|---|---|
| `pending` | todavía no terminó |
| `fulfilled` | terminó bien |
| `rejected` | terminó con error |

Modelo mental del Event Loop:

```txt
1. Código sincrónico
2. Microtasks resueltas, como callbacks de Promises
3. Macrotasks, como setTimeout
4. Re-render / siguiente vuelta del loop
```

Ejemplo mínimo:

```js
console.log("inicio")

Promise.resolve().then(() => {
  console.log("microtask")
})

setTimeout(() => {
  console.log("macrotask")
}, 0)

console.log("fin")
```

Salida esperada:

```txt
inicio
fin
microtask
macrotask
```

Relación con MegaSuper:
- En esta clase el array `productos` está en memoria, entonces las operaciones son sincrónicas.
- Cuando eso pase a base de datos o a otra API, las rutas van a necesitar `async/await` o manejo de promesas.

Fuente teórica:
- `_cache_pdf_text/Clase 3 - Promesas.txt`

---

### 15) Postman collection: contrato ejecutable de prueba manual

El repo trae una colección:
- https://github.com/ddso-utn/api-megasuper-2026/blob/main/docs/megasuper.postman_collection.json

Concepto:
- Postman no es la API.
- Es una herramienta para probar requests.
- Si la colección y el código no coinciden, gana el código, pero queda deuda de documentación.

Ejemplos en la colección:
- GET productos
- GET producto por id
- POST producto
- PUT producto
- DELETE producto

---

### 16) Gotchas reales de Clase 03

1. **Ruta de healthcheck inconsistente**
   Postman muestra `/healthcheck`, pero el código expone `/v1/healthcheck`.

2. **`res.status(...)` no alcanza si no enviás respuesta**
   Para cerrar una response usá `json`, `send` o `end`.

3. **Responder no corta la función**
   En Express, si querés frenar el handler, usá `return res.status(...).json(...)`.

4. **`req.params` y `req.query` llegan como strings**
   Si tratás un id o precio como número, convertí y validá.

5. **Un archivo único sirve para aprender, pero no escala bien**
   La clase práctica lo deja todo junto para ver el flujo. La teoría ya muestra por qué después conviene separar en capas.

---

### 17) Resumen mental de Clase 03

MegaSuper muestra REST en miniatura:

| Operación | Método | Ruta | Status esperado |
|---|---|---|---|
| healthcheck | GET | `/v1/healthcheck` | 200 |
| listar productos | GET | `/v1/productos` | 200 |
| filtrar productos | GET | `/v1/productosícategoria=Bebidas` | 200 |
| ver producto | GET | `/v1/productos/:id` | 200 / 404 |
| crear producto | POST | `/v1/productos` | 201 / 400 / 409 |
| reemplazar producto | PUT | `/v1/productos/:id` | 200 / 400 / 404 / 409 |
| borrar producto | DELETE | `/v1/productos/:id` | 204 / 404 recomendado |

Si te preguntan "¿qué aporta esta clase?", contestá:

> La clase muestra cómo HTTP y REST se implementan en una API Express real: rutas, recursos, params, query params, body JSON, validación con Zod y status codes. Además introduce el criterio de capas: hoy está todo en un archivo para aprender, pero el diseño correcto separa controller, service y repository para reducir acoplamiento y facilitar testeo.

Checklist para examen:
- explicar qué es un recurso REST;
- distinguir route params de query params;
- justificar `POST`, `PUT`, `DELETE` y sus status codes;
- explicar por qué validar el body en backend;
- detectar por qué `return res.status(...).json(...)` evita bugs;
- resumir controller/service/repository sin entrar todavía en implementación completa;
- conectar Promises con futuras llamadas a DB o APIs externas.

---


## Clase 04 - Arquitectura por capas y orquestación de casos de uso

Fuente práctica:
- PDF local: `Clases_Practica/Clase Práctica - 04 - Capas.pdf`
- Cache textual: `_cache_pdf_text/Clase Práctica - 04 - Capas.txt`

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase4-ApiSeparadaEnCapas/server
- Carpeta local de consulta: `./_tmp_ddso_ejercicio-megasuper-2026/server`
- Rama revisada: `origin/clase4-ApiSeparadaEnCapas`

Idea central:
> Esta clase toma la API que venía creciendo y la ordena por responsabilidades: controller para HTTP, service para orquestar casos de uso, repository para persistencia y domain para reglas del negocio.

Por qué importa:
Separar en capas no es “acomodar carpetas”. Es decidir **quién hace qué, en qué orden y con qué dependencias**. Esa decisión baja acoplamiento, sube cohesión y hace que el sistema sea más fácil de probar, cambiar y explicar.

---

### 1) Orquestación de casos de uso

#### Problema

El PDF arranca corrigiendo una confusión muy común: poner lógica de casos de uso directamente en clases del dominio, o repartirla entre controllers, entidades y utilidades sin un criterio claro.

El foco no debería ser “qué clase del mundo real hace esto”, sino:

```txt
qué operación quiere resolver el sistema
  -> qué pasos requiere
  -> qué objetos participan
  -> quién coordina el flujo
```

#### Concepto

La idea correcta es separar:

- **Dominio**: sabe las reglas del negocio.
- **Service**: sabe en qué orden ejecutar pasos para resolver un caso de uso.
- **Controller**: recibe request, traduce entrada HTTP y delega.
- **Repository**: encapsula el acceso a los datos.

En criollo:

- el dominio sabe **cómo se comporta** un producto;
- el service sabe **cuándo y en qué secuencia** crear, validar, buscar o eliminar;
- el controller sabe **cómo hablar HTTP**;
- el repository sabe **cómo guardar y recuperar datos**.

#### Ejemplo real del repo

En la rama de clase 4 se ve repartido así:

- `ProductoController`: recibe request/response.
- `ProductoService`: orquesta validaciones y flujo del caso de uso.
- `ProductoRepository`: accede al almacenamiento en memoria.
- `Producto`: modela la entidad y su comportamiento.

Fuentes:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/controllers/ProductoController.js
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/services/ProductoService.js
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/repositories/ProductoRepository.js
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/domain/Producto.js

#### Para examen

> Orquestar un caso de uso significa coordinar los pasos necesarios para resolver una operación del sistema sin mezclar HTTP, persistencia y reglas de dominio en el mismo lugar.

---

### 2) Capa de Controllers

#### Problema

Si el controller hace todo, termina siendo un “mega archivo” que parsea requests, decide reglas de negocio, consulta datos y arma respuestas. Eso funciona al principio, pero después se vuelve difícil de cambiar.

#### Concepto

Según el PDF, el controller:

- recibe pedidos externos;
- traduce inputs al lenguaje de la aplicación;
- delega en services;
- devuelve la respuesta;
- maneja validaciones superficiales y códigos HTTP;
- **no debería tener lógica de negocio real**.

#### Ejemplo real del repo

```js
findById = async (req, res) => {
  try {
    const id = this.parsearId(req.params.id)
    const producto = this.productoService.obtenerPorId(id)

    return res.status(200).json({ status: "success", data: producto })
  } catch (error) {
    return this.manejarError(res, error)
  }
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/controllers/ProductoController.js

Qué hace bien este controller:

- parsea el `id` desde HTTP;
- llama al service;
- transforma el resultado en respuesta HTTP;
- centraliza errores en `manejarError`.

Otro ejemplo importante: validación superficial del body.

```js
extraerYValidarBodyProducto(body) {
  if (!body || typeof body !== "object" || Array.isArray(body)) {
    throw new BadRequestError("El cuerpo de la request es inválido")
  }

  const camposPermitidos = ["nombre", "precio", "cantidad", "categoria"]
  // ... valida faltantes y campos no permitidos
}
```

Esto está bien ubicado acá porque valida la **forma de entrada HTTP**. Todavía no está decidiendo reglas profundas del negocio.

#### Error típico

Meter cálculos, descuentos, reglas de stock o unicidad en el controller. Eso rompe la separación de capas porque HTTP empieza a conocer negocio.

---

### 3) Capa de Services

#### Problema

El dominio no debería saber si una operación llegó por HTTP, por consola o por un job. Y el controller no debería conocer el detalle de cada regla de negocio. Falta una capa que coordine el caso de uso.

#### Concepto

El PDF define la capa de services como la que:

- orquesta la ejecución de una operación de negocio;
- llama a dominio, repositorios y utilidades;
- separa el “cómo se hace” del “cuándo y en qué orden”.

En el repo, `ProductoService` hace exactamente eso.

#### Ejemplo real: crear producto

```js
crear(datosProducto) {
  this.validarDatosProducto(datosProducto)
  this.validarNombreDisponible(datosProducto.nombre)

  const producto = new Producto(
    datosProducto.nombre,
    datosProducto.precio,
    datosProducto.cantidad,
    datosProducto.categoria
  )

  return this.productoRepository.guardar(producto)
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/services/ProductoService.js

Acá hay una lección importante:

- el service no persiste directamente;
- el service no sabe HTTP;
- el service no renderiza JSON;
- el service decide el flujo del caso de uso.

#### Ejemplo real: paginación + filtros

```js
obtenerTodos({ numeroPagina = 1, limitePorPagina = 10, filtros = {} } = {}) {
  this.validarPaginacion(numeroPagina, limitePorPagina)
  this.validarFiltros(filtros)

  const { productos, totalProductos } = this.productoRepository.obtenerPaginados(
    numeroPagina,
    limitePorPagina,
    filtros
  )

  const totalPaginas = totalProductos === 0 ? 0 : Math.ceil(totalProductos / limitePorPagina)

  return {
    productos,
    numeroPagina,
    limitePorPagina,
    totalPaginas,
    totalProductos
  }
}
```

Eso es orquestación pura:

1. valida entrada del caso de uso;
2. pide datos al repo;
3. calcula metadata de paginación;
4. devuelve una estructura lista para que el controller la traduzca a HTTP.

---

### 4) Capa de Repositories

#### Problema

Si el controller o el service conocen detalles concretos de almacenamiento, cambiar de memoria a base de datos se vuelve doloroso. El resto del sistema queda pegado a “cómo guardamos”.

#### Concepto

Según el PDF, el repository:

- encapsula acceso a persistencia;
- puede hablar con memoria, archivos, DB u otros sistemas;
- traduce entre dominio y almacenamiento;
- expone operaciones como agregar, modificar, eliminar, buscar y buscar todos.

En el repo actual, la persistencia es en memoria:

```js
constructor() {
  this.productos = {}
  this.nextId = 1
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/repositories/ProductoRepository.js

Operaciones clave:

- `guardar(producto)`
- `guardarTodos(productos)`
- `obtenerPorId(id)`
- `obtenerPorNombre(nombre)`
- `obtenerPaginados(...)`
- `eliminar(id)`

#### Ejemplo real de paginación en repository

```js
const inicio = (numeroPagina - 1) * limitePorPagina
const fin = inicio + limitePorPagina

return {
  productos: productos.slice(inicio, fin),
  totalProductos: productos.length
}
```

Esto está bien ubicado acá porque:

- el repository ya tiene la colección completa;
- sabe cómo aplicar filtros y slicing sobre su fuente de datos;
- no obliga al controller a conocer detalles de almacenamiento.

#### Error típico

Hacer que el controller filtre arrays directamente. Eso acopla HTTP con persistencia y vuelve más difícil cambiar la fuente de datos.

---

### 5) Capa de Domain

#### Problema

Si los objetos de negocio son solo bolsas de atributos, las reglas terminan repartidas por controllers, services y helpers. Ahí el sistema queda frágil: cualquier camino alternativo puede saltearse reglas.

#### Concepto

El PDF dice que el dominio es el corazón del sistema:

- reglas;
- validaciones;
- entidades;
- objetos de valor;
- independencia de infraestructura.

En el repo, la entidad principal es `Producto`.

#### Ejemplo real

```js
export class Producto {
  constructor(nombre, precio, cantidad, categoria) {
    this.validarNombre(nombre)
    this.validarPrecio(precio)
    this.validarCantidad(cantidad)
    this.validarCategoria(categoria)

    this.nombre = nombre.trim()
    this.precio = precio
    this.cantidad = cantidad
    this.categoria = categoria.trim()
    this.eliminado = false
    this.descuentos = []
  }
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/domain/Producto.js

Lo importante es el concepto:

- el producto se valida a sí mismo;
- no depende de Express;
- no depende del repository;
- no depende de `req` ni `res`.

También aparece comportamiento de dominio, no solo datos:

```js
precioFinal() {
  const precioBaseTotal = this.precio * this.cantidad

  const precioFinal = this.descuentos.reduce((precioAnterior, descuento) => {
    const valorDescuento = descuento.valorDescontado(this)
    return precioAnterior - valorDescuento
  }, precioBaseTotal)

  return Math.max(0, precioFinal)
}
```

Acá se ve una entidad rica: `Producto` no solo “tiene datos”, también sabe calcular su precio final con descuentos.

#### Para examen

> El dominio debería concentrar reglas e invariantes del negocio y mantenerse independiente de frameworks, HTTP y persistencia.

---

### 6) Relación entre capas: flujo completo

Caso de uso: crear producto.

Flujo real del repo:

```txt
POST /productos
  -> routes/productoRoutes.js
  -> ProductoController.create
  -> ProductoController.extraerYValidarBodyProducto
  -> ProductoService.crear
  -> new Producto(...)
  -> ProductoRepository.guardar
  -> response 201
```

#### Vista visual del flujo

```mermaid
flowchart TD
  A["Request HTTP: POST /productos"] --> B["Router: productoRoutes.js"]
  B --> C["Controller: ProductoController.create"]
  C --> D["Service: ProductoService.crear"]
  D --> E["Domain: new Producto(...)"]
  D --> F["Repository: ProductoRepository.guardar"]
  F --> G["Controller: arma response 201"]
```

Este diagrama ayuda a fijar la idea central: el request entra por HTTP, pero la responsabilidad se va delegando capa por capa.

Eso se ve repartido en:

- `routes/productoRoutes.js`
- `controllers/ProductoController.js`
- `services/ProductoService.js`
- `repositories/ProductoRepository.js`
- `domain/Producto.js`

Lección clave:

> Una capa superior puede usar servicios de capas inferiores, pero no al revés; y no conviene saltear niveles sin una razón de diseño clara.

---

### 7) Router: donde viven las rutas

En clase 3 veíamos todo junto. Acá ya se separa.

Router principal:

```js
router.use('/productos', productoRouter)
```

Router específico:

```js
router.route('/')
  .get((req, res) => productoController.findAll(req, res))
  .post((req, res) => productoController.create(req, res))

router.route('/:id')
  .get((req, res) => productoController.findById(req, res))
  .put((req, res) => productoController.update(req, res))
  .delete((req, res) => productoController.delete(req, res))
```

Fuentes:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/routes/router.js
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/routes/productoRoutes.js

Esto mejora porque:

- agrupa endpoints por recurso;
- evita un `index.js` monstruoso;
- permite que la API crezca sin mezclar rutas de distintos dominios.

---

### 8) Paginación

#### Problema

Si una API tiene miles de registros, devolver todo en una sola respuesta es lento, caro e incómodo.

#### Concepto

La paginación divide una colección grande en porciones más chicas.

- `page`: número de página.
- `limit`: cantidad de resultados por página.
- `offset = (page - 1) * limit`.

Ejemplo de request:

```http
GET /productos?page=2&limit=5
```

Extracción desde controller:

```js
extraerPaginacion(query) {
  const numeroPagina = query?.page === undefined ? 1 : Number(query.page)
  const limitePorPagina = query?.limit === undefined ? 10 : Number(query.limit)

  this.validarEnteroPositivo(numeroPagina, "page")
  this.validarEnteroPositivo(limitePorPagina, "limit")

  return { numeroPagina, limitePorPagina }
}
```

Corte real en repository:

```js
const inicio = (numeroPagina - 1) * limitePorPagina
const fin = inicio + limitePorPagina

productos.slice(inicio, fin)
```

Y la respuesta agrega metadata:

```js
return res.status(200).json({
  status: "success",
  data: resultado.productos,
  paginacion: {
    numeroPagina: resultado.numeroPagina,
    limitePorPagina: resultado.limitePorPagina,
    totalPaginas: resultado.totalPaginas,
    totalProductos: resultado.totalProductos
  }
})
```

Esto está bien porque el cliente no recibe solo datos: recibe contexto para navegar.

---

### 9) Filtros

El repo combina paginación con filtros:

- `precioMin`
- `precioMax`
- `categoria`

Controller extrae query params:

```js
extraerFiltros(query) {
  const filtros = {}

  if (query.precioMin !== undefined) {
    const precioMin = Number(query.precioMin)
    if (!Number.isFinite(precioMin)) {
      throw new BadRequestError("precioMin debe ser un número válido")
    }
    filtros.precioMin = precioMin
  }

  if (query.categoria !== undefined) {
    filtros.categoria = query.categoria
  }

  return filtros
}
```

Repository aplica el filtro:

```js
if (filtros.categoria !== undefined) {
  const categoriaNormalizada = filtros.categoria.trim().toLowerCase()
  productos = productos.filter((p) => p.categoria.trim().toLowerCase() === categoriaNormalizada)
}
```

Lectura de diseño:

```txt
controller -> parsea query params
service    -> valida reglas del filtro
repository -> aplica filtro sobre la fuente de datos
```

Eso es separación de responsabilidades en serio.

---

### 10) Manejo de errores en la versión de Clase 04

La clase 4 todavía no tiene middleware global de errores; eso aparece mejor trabajado en la Clase 05. En esta versión, el controller captura errores y los traduce con `manejarError`.

```js
manejarError(res, error) {
  const message = error?.message || "Error interno"
  const timestamp = error?.timestamp || new Date().toISOString()

  if (error instanceof NotFoundError) {
    return res.status(404).json({ status: "fail", message, timestamp })
  }

  if (error instanceof ConflictError) {
    return res.status(409).json({ status: "fail", message, timestamp })
  }

  return res.status(500).json({ status: "error", message: "Error interno del servidor", timestamp })
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/controllers/ProductoController.js

Esto es mejor que tirar strings random por todos lados, pero todavía deja una responsabilidad pesada en el controller. Justamente por eso la Clase 05 da el paso siguiente: `next(error)` + middlewares globales.

---

### 11) Cualidades de diseño que mejora la arquitectura por capas

El PDF cierra con cualidades importantes para examen.

#### Bajo acoplamiento

Cada capa depende de pocas cosas y de manera predecible.

Ejemplo:
- `Producto` no conoce Express.
- `ProductoRepository` no conoce `req` ni `res`.

#### Alta cohesión

Cada capa tiene un propósito claro.

Ejemplo:
- Controller: HTTP.
- Service: flujo de casos de uso.
- Repository: persistencia.
- Domain: reglas.

#### Simplicidad

La separación evita duplicación, magia rara y sobreingeniería.

#### Robustez

Las reglas del dominio quedan protegidas y no dependen de quién las llama.

#### Flexibilidad

Podés cambiar:

- UI;
- base de datos;
- forma de exponer API;

sin reventar todo el núcleo.

---

### 12) Gotchas reales del repo

No todo ejemplo de clase está “perfecto perfecto”, y eso también enseña.

1. **Imports innecesarios en `productoRoutes.js`**
   - Se importan `ProductoService` y `ProductoRepository`, pero no se usan.
   - Eso sobra y puede confundir sobre dónde se construyen las dependencias.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/routes/productoRoutes.js

2. **Handlers `async` con service sincrónico**
   - No rompe.
   - Pero conceptualmente todavía no hacía falta `async` porque el repository trabaja en memoria.
   - Esto probablemente anticipa persistencia futura o llamadas asincrónicas.

3. **Bug en `DescuentoPorCantidad`**
   - El método usa `cantidad` sin definir en vez de `producto.cantidad`.
   - Eso parece un bug real del ejemplo.
   - Sirve para recordar que el dominio también necesita tests.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/domain/Descuento.js

4. **Typo en `agregarDecuento`**
   - En `Producto` aparece un método con typo que delega a `agregarDescuento`.
   - No rompe si nadie lo usa, pero ensucia la API pública del objeto.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase4-ApiSeparadaEnCapas/server/domain/Producto.js

---

### 13) Resumen mental de Clase 04

Si te preguntan “¿para qué sirve separar en capasí”, la respuesta buena no es “porque queda más prolijo”.

La respuesta fuerte es:

> Separar en capas permite ubicar cada responsabilidad en el lugar correcto: controller para HTTP, service para orquestación, repository para persistencia y domain para reglas del negocio. Eso reduce acoplamiento, aumenta cohesión, facilita testeo y hace que el sistema pueda evolucionar sin romper todo el núcleo.

Checklist para examen:

- explicar qué problema resuelve la arquitectura por capas;
- distinguir controller, service, repository y domain;
- explicar qué significa orquestar un caso de uso;
- ubicar paginación y filtros en el flujo correcto;
- justificar bajo acoplamiento y alta cohesión;
- detectar por qué no conviene poner negocio en controllers;
- mencionar un gotcha real del repo.

---


## Clase 05 - Manejo de errores y middlewares en Express

Fuente práctica:
- PDF local: `Clases_Practica/Clase Práctica - 05- Manejo de errores.pdf`
- Cache textual: `_cache_pdf_text/Clase_Practica_05_Manejo_de_errores.txt`

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase5-error-handling
- Carpeta local de consulta: `./_tmp_ddso_ejercicio-megasuper-2026/server`
- Rama revisada: `origin/clase5-error-handling`

Idea central:
> Los errores no se manejan “como salga” en cada endpoint. Se modelan, se propagan con `next(error)` y se traducen a HTTP en middlewares centralizados.

Por qué importa:
La Clase 04 ordenó responsabilidades por capas. La Clase 05 completa esa idea para errores: la capa que detecta el problema lanza un error significativo, el controller lo delega y un middleware global decide cómo loguearlo y responderlo. Así la API gana consistencia y el controller deja de repetir lógica de error.


#### Clase 04 vs Clase 05

| Tema | Clase 04 | Clase 05 |
|---|---|---|
| Objetivo principal | Separar responsabilidades por capas | Centralizar propagación, logging y respuesta de errores |
| Controller | Recibe HTTP, delega y todavía traduce errores con `manejarError` | Recibe HTTP, delega y pasa errores con `next(error)` |
| Error handling | Está concentrado en el controller | Está en middlewares globales al final del pipeline |
| Ventaja nueva | Ordena dominio, casos de uso y persistencia | Hace consistente el contrato de errores de toda la API |
| Idea de examen | `controller -> service -> repository/domain` | `throw AppError -> next(error) -> errorLogger -> errorHandler` |

Esta comparación es clave: la Clase 05 no reemplaza a la Clase 04, la completa. Primero ordenamos responsabilidades; después ordenamos cómo viajan y se responden los errores.


---

### 1) ¿Por qué importa manejar bien los erroresí

El PDF marca que los errores bien manejados permiten:

- separar responsabilidades entre capas;
- mejorar debugging;
- dar respuestas útiles al usuario o API client;
- loguear problemas reales.

#### Problema

Si cada endpoint responde errores a mano, terminás con esto:

```js
if (!producto) {
  return res.status(404).json({ error: "No existe" })
}

if (nombreRepetido) {
  return res.status(409).json({ mensaje: "Duplicado" })
}

if (algoRaro) {
  return res.status(500).send("fallo")
}
```

El problema no es solo estético: cada controller inventa su propio contrato. Eso rompe consistencia y vuelve más difícil consumir la API.

#### Solución

Centralizar el manejo:

```txt
Error del sistema
  -> next(error)
  -> errorLogger
  -> errorHandler
  -> respuesta HTTP uniforme
```

Ejemplo real del repo:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/app.js
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/middlewares/errorHandler.js

---

### 2) Middleware normal vs middleware de error

#### Concepto

Un **middleware** es una función que recibe una request, puede procesarla y decide si:

1. responde la request; o
2. pasa al siguiente middleware con `next()`.

Middleware normal:

```js
function middlewareNormal(req, res, next) {
  // hago algo con la request
  next()
}
```

Middleware de error:

```js
function middlewareDeError(err, req, res, next) {
  // manejo el error
}
```

La diferencia no es estética. Express identifica el error handler por la firma con **cuatro parámetros**: `err, req, res, next`.

#### Ejemplo real del repo

En `server/app.js` se ve el pipeline:

```js
app.use(express.json())
app.use(cors())
app.use(router)

app.use(notFoundHandler)
app.use(errorLogger)
app.use(errorHandler)
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/app.js

Lectura:

1. `express.json()` parsea JSON.
2. `cors()` configura CORS.
3. `router` intenta resolver la ruta.
4. `notFoundHandler` captura rutas inexistentes.
5. `errorLogger` registra el error.
6. `errorHandler` arma la respuesta final.

#### Regla de examen

> El orden de registro es el orden de ejecución. Los middlewares de error van al final, después de las rutas.

Si ponés el `errorHandler` antes del router, no va a capturar errores producidos por esas rutas.

---

### 3) `next()` vs `next(error)`

#### `next()`

Sigue el flujo normal:

```js
app.use((req, res, next) => {
  console.log("Llegó request")
  next()
})
```

#### `next(error)`

Corta el flujo normal y salta al pipeline de errores:

```js
next(new Error("Algo salió mal"))
```

El PDF lo dice de forma directa: cuando se llama a `next(err)` con un argumento distinto de `undefined`, Express salta los middlewares de tres parámetros y busca el primer error handler.

#### Ejemplo real del repo

En `ProductoController`, los handlers capturan errores y los delegan:

```js
findById = async (req, res, next) => {
  try {
    const id = this.parsearId(req.params.id)
    const producto = this.productoService.obtenerPorId(id)

    return res.status(200).json({ status: "success", data: producto })
  } catch (error) {
    return next(error)
  }
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/controllers/ProductoController.js

#### ¿Por qué está bueno?

Porque el controller no necesita saber si el error va a terminar siendo:

- `400 Bad Request`;
- `404 Not Found`;
- `409 Conflict`;
- `422 Unprocessable Entity`;
- `500 Internal Server Error`.

El controller hace lo suyo: traduce HTTP a caso de uso y delega errores.

---

### 4) Errores personalizados: `AppError`

#### Problema

Un `Error` común trae mensaje y stack. Para una API necesitás también información HTTP:

- status code;
- tipo de estado (`fail` o `error`);
- timestamp;
- mensaje seguro para el cliente.

#### Solución del repo

`AppError` extiende `Error` y agrega datos útiles para la respuesta HTTP:

```js
export class AppError extends Error {
  constructor(message, statusCode) {
    super(message)
    this.name = this.constructor.name
    this.statusCode = statusCode
    this.status = statusCode >= 500 ? "error" : "fail"
    this.timestamp = new Date().toISOString()
  }
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/errors/AppError.js

Después se declaran errores concretos:

```js
export class BadRequestError extends AppError {
  constructor(message) {
    super(message, 400)
  }
}

export class NotFoundError extends AppError {
  constructor(message) {
    super(message, 404)
  }
}

export class ConflictError extends AppError {
  constructor(message) {
    super(message, 409)
  }
}

export class UnprocessableEntityError extends AppError {
  constructor(message) {
    super(message, 422)
  }
}
```

#### Para memorizar

| Error custom | HTTP | Cuándo usarlo |
|---|---:|---|
| `BadRequestError` | 400 | request mal formada, params inválidos, body incompleto |
| `NotFoundError` | 404 | recurso o ruta inexistente |
| `ConflictError` | 409 | conflicto con el estado actual, ej. nombre duplicado |
| `UnprocessableEntityError` | 422 | el JSON se entiende, pero viola reglas semánticas/de negocio |
| Error desconocido | 500 | bug, excepción inesperada, problema no controlado |

Ojo: `400` y `422` se parecen, pero no son lo mismo.

- `400`: no puedo interpretar bien lo que me mandaste.
- `422`: entiendo lo que me mandaste, pero no cumple reglas válidas del negocio.

---

### 5) Error handler centralizado

#### Concepto

Un error handler global es el lugar donde la aplicación traduce:

```txt
Error interno de JS / dominio / aplicación -> respuesta HTTP
```

Esto se parece a `@ControllerAdvice` en Spring Boot: un punto central para transformar excepciones en respuestas.

#### Ejemplo real del repo

```js
import { AppError } from "../errors/AppError.js"

export function errorHandler(err, req, res, next) {
  if (res.headersSent) {
    return next(err)
  }

  if (err instanceof AppError) {
    return res.status(err.statusCode).json({
      status: err.status,
      message: err.message,
      timestamp: err.timestamp,
    })
  }

  return res.status(500).json({
    status: "error",
    message: "Error interno del servidor",
    timestamp: new Date().toISOString(),
  })
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/middlewares/errorHandler.js

#### Lo importante

1. Si ya se enviaron headers, delega con `next(err)`.
2. Si el error es `AppError`, usa su `statusCode`.
3. Si el error es desconocido, responde `500` genérico.
4. No expone el `stack` al cliente.

Esto último es fundamental: el stack sirve para debugging interno, no para regalarle información al consumidor de la API.

---

### 6) Error logger: observar sin responder

#### Problema

Loguear y responder son responsabilidades distintas. Si las mezclás, mañana no podés cambiar cómo logueás sin tocar cómo respondés.

#### Concepto

- `errorLogger`: registra el problema.
- `errorHandler`: responde al cliente.

#### Ejemplo real del repo

```js
export function errorLogger(err, req, res, next) {
  console.error({
    timestamp: new Date().toISOString(),
    method: req.method,
    path: req.originalUrl,
    error: {
      name: err.name,
      message: err.message,
      stack: err.stack,
    },
  })

  next(err)
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/middlewares/errorLogger.js

#### Error típico

Olvidarte de `next(err)` al final.

Si el logger no llama a `next(err)`, el flujo queda colgado y el cliente no recibe respuesta. El logger observa; no reemplaza al handler final.

---

### 7) `notFoundHandler`: rutas inexistentes también son errores

#### Concepto

Si ninguna ruta matchea, conviene capturar ese caso al final de las rutas para responder con el mismo formato que el resto de errores.

#### Ejemplo real del repo

```js
import { NotFoundError } from "../errors/AppError.js"

export function notFoundHandler(req, res, next) {
  next(new NotFoundError(`Ruta ${req.originalUrl} no encontrada`))
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/middlewares/notFoundHandler.js

Flujo:

```txt
GET /sarasa
  -> no matchea ninguna ruta
  -> notFoundHandler
  -> next(new NotFoundError(...))
  -> errorLogger
  -> errorHandler
  -> 404 JSON
```

#### Diferencia importante

No confundas:

| Caso | Ejemplo | Dónde se detecta | Error |
|---|---|---|---|
| Ruta inexistente | `GET /sarasa` | `notFoundHandler` | `NotFoundError` |
| Recurso inexistente | `GET /productos/999` | `ProductoService.obtenerPorId` | `NotFoundError` |

Ambos son 404, pero conceptualmente no nacen en el mismo lugar.

---

### 8) Errores por capa: quién debe hacer qué

La Clase 05 conecta perfecto con la Clase 04: si separaste capas, también separás el manejo de errores.

#### Controller

Responsabilidad:

- parsear `req.params`, `req.query`, `req.body`;
- validar formato HTTP básico;
- responder éxito;
- delegar errores con `next(error)`.

Ejemplo real:

```js
parsearId(idParam) {
  const id = Number(idParam)

  this.validarEnteroPositivo(id, "id")

  return id
}
```

Si `id` no es entero positivo, termina lanzando `BadRequestError`.

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/controllers/ProductoController.js

#### Service

Responsabilidad:

- aplicar reglas de negocio;
- decidir errores de negocio;
- coordinar repositorios/dominio.

Ejemplo real:

```js
obtenerPorId(id) {
  this.validarEnteroPositivo(id, "Id")

  const producto = this.productoRepository.obtenerPorId(id)

  if (!producto) {
    throw new NotFoundError("Producto no encontrado")
  }

  return producto
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/services/ProductoService.js

#### Repository

Responsabilidad:

- acceso a datos;
- detalles de persistencia;
- validaciones propias del acceso al almacenamiento.

Ejemplo real:

```js
obtenerPorId(id, { incluirEliminados = false } = {}) {
  this.validarId(id)

  const producto = this.productos[id] ?? null

  if (!producto) {
    return null
  }

  if (!incluirEliminados && producto.eliminado) {
    return null
  }

  return producto
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/repositories/ProductoRepository.js

#### Middleware de error

Responsabilidad:

- transformar errores a HTTP;
- responder con formato uniforme;
- evitar filtrar detalles internos.

---

### 9) Casos prácticos para examen

#### Caso A: parámetro inválido

Request:

```http
GET /productos/abc
```

Flujo:

```txt
ProductoController.parsearId("abc")
  -> Number("abc") = NaN
  -> validarEnteroPositivo falla
  -> BadRequestError
  -> next(error)
  -> errorHandler
  -> 400
```

Respuesta esperada conceptual:

```json
{
  "status": "fail",
  "message": "El parámetro id debe ser un entero positivo",
  "timestamp": "..."
}
```

#### Caso B: producto inexistente

Request:

```http
GET /productos/999
```

Flujo:

```txt
Controller parsea id OK
  -> Service busca producto
  -> Repository devuelve null
  -> Service lanza NotFoundError
  -> 404
```

#### Caso C: producto duplicado

Request:

```http
POST /productos
Content-Type: application/json

{
  "nombre": "Coca-Cola 1.5L",
  "precio": 2500,
  "cantidad": 50,
  "categoria": "Bebidas"
}
```

Si ya existe un producto con ese nombre:

```txt
ProductoService.validarNombreDisponible
  -> ConflictError
  -> 409
```

#### Caso D: body entendido pero inválido

```http
POST /productos
Content-Type: application/json

{
  "nombre": "Co",
  "precio": 2500,
  "cantidad": 50,
  "categoria": "Bebidas"
}
```

El JSON está bien formado, pero `nombre` no cumple la regla mínima.

```txt
UnprocessableEntityError
  -> 422
```

#### Caso E: ruta inexistente

```http
GET /no-existe
```

```txt
router no matchea
  -> notFoundHandler
  -> NotFoundError
  -> 404
```

---

### 10) Flujo integrador completo

```txt
Request HTTP
  -> express.json / cors
  -> router
  -> ProductoController
  -> ProductoService
  -> ProductoRepository / Domain
  -> throw new AppError(...)
  -> catch (error) { next(error) }
  -> errorLogger
  -> errorHandler
  -> Response HTTP uniforme
```

En una API prolija, el error viaja hacia arriba como una señal, y solo al final se transforma en HTTP.

---

### 11) Gotchas reales del repo

1. **Imports innecesarios en `productoRoutes.js`**
   - Se importan `ProductoService` y `ProductoRepository`, pero no se usan.
   - Alternativa simple: borrar imports.
   - Alternativa arquitectónica: armar un composition root donde se cree `repository -> service -> controller`.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/routes/productoRoutes.js

2. **Conviven dos ideas de delete**
   - `ProductoService.eliminar` hace **soft delete** (`producto.eliminado = true`).
   - `ProductoRepository.eliminar` hace **hard delete** (`delete this.productos[id]`).
   - No necesariamente rompe, pero conceptualmente hay una decisión de diseño mezclada: ¿dónde debería decidirse? En el caso de uso/service.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/services/ProductoService.js
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/repositories/ProductoRepository.js

3. **Validaciones en service y domain**
   - Puede parecer duplicación.
   - Bien explicado tiene sentido: el service valida el caso de uso/API; el domain protege invariantes internas.
   - La clave es que no haya reglas contradictorias.

4. **Bug didáctico en `DescuentoPorCantidad`**
   - Usa `cantidad` sin definir en vez de `producto.cantidad`.
   - Esto muestra por qué los errores también necesitan tests.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase5-error-handling/server/domain/Descuento.js

5. **Handlers `async` con lógica sincrónica**
   - Como el repository está en memoria, hoy no hay awaits reales.
   - No rompe, pero anticipa una futura persistencia asincrónica.

---

### 12) Resumen mental de Clase 05

Si te preguntan “¿cómo se manejan errores en Expressí”, contestá:

> En Express, los errores se propagan con `next(error)`. Cuando Express recibe un error, salta los middlewares normales y busca un middleware de error con firma `(err, req, res, next)`. En una arquitectura por capas, las capas lanzan errores significativos (`AppError`, `NotFoundError`, etc.) y un error handler global los traduce a respuestas HTTP uniformes. Esto mejora consistencia, debugging, logging y separación de responsabilidades.

Checklist para examen:

- middleware normal: `(req, res, next)`;
- middleware de error: `(err, req, res, next)`;
- `next()` sigue flujo normal;
- `next(error)` salta al flujo de error;
- los middlewares de error se registran al final;
- `AppError` permite mapear errores del sistema a HTTP;
- `errorLogger` registra y delega;
- `errorHandler` responde;
- 400, 404, 409, 422 y 500 no significan lo mismo.

---


## Clase 06 - Testing con Jest, Supertest y documentación con OpenAPI

Fuente teórica:
- PDF local: `Clases_Teoria/1C2026 - DDSW - MN - Clase 6 - Resumen.pdf`
- Cache textual: `_cache_pdf_text/1C2026 - DDSW - MN - Clase 6 - Resumen.txt`

Fuente práctica:
- PDF local: `Clases_Practica/Clase Práctica - 06 - testing y documentacion.pdf`
- Cache textual: `_cache_pdf_text/Clase Practica - 06 - testing y documentacion.txt`

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase6-testing
- Local: `_tmp_ddso_ejercicio-megasuper-2026` (rama `origin/clase6-testing`)

Idea central:
> Esta clase baja testing a una API real: pruebas unitarias para dominio, pruebas de integración para el flujo HTTP/capas y documentación OpenAPI como contrato visible de la API.

Por qué importa:
Venimos de separar capas y ordenar errores. Testing permite verificar que esas decisiones sigan funcionando cuando el código cambia, y OpenAPI ayuda a que el contrato HTTP no quede solo “en la cabeza” del backend.

### 1) Por qué testeamos (y que estamos buscando)

El testing **no busca demostrar que el sistema funciona**: busca encontrar fallas. Cuatro objetivos en tensión:

- Encontrar fallas **rápido y barato** (eficiencia).
- Encontrar la **mayor cantidad** de fallas posibles.
- Evitar **falsos positivos** (lo que parece falla y no lo es).
- Priorizar las fallas **más importantes** (no todas valen lo mismo).

Idea clave: si un test no puede fallar nunca, no está probando nada. Si todos tus tests pasan siempre, capaz que sirven de poco.

#### Qué suma la teoría de testing

La teoría no cambia lo que se hizo en la práctica, pero agrega un mapa más completo para ubicar cada herramienta.

Beneficios principales:

- **Reducción de costos**: corregir temprano suele ser más barato que corregir en producción.
- **Mejora de calidad**: ayuda a sostener estándares y expectativas.
- **Reducción de riesgos**: baja la probabilidad de fallos costosos.
- **Confianza para cambiar**: si refactorizás y los tests siguen pasando, tenés una señal de que no rompiste comportamiento esperado.

TDD y BDD, muy resumido:

| Enfoque | Idea | Cuándo sirve más |
|---|---|---|
| TDD | escribir tests antes del código funcional | diseño de código, bugs y reglas bien acotadas |
| BDD | describir comportamiento esperado en lenguaje de negocio | nuevas funcionalidades y comunicación con negocio/usuarios |

Tipos de tests mencionados en teoría:

| Tipo | Qué valida | Ejemplo mental |
|---|---|---|
| Unitario | una unidad aislada | `Producto.precioFinal()` |
| Funcional | que una funcionalidad cumpla el requerimiento | crear producto con datos válidos |
| Integración | colaboración entre componentes | HTTP -> controller -> service -> repo mockeado |
| E2E | flujo completo como usuario real | frontend + backend + DB + servicios |
| Regresión | que algo que ya funcionaba no se rompa | correr suite después de un cambio |
| Rendimiento/carga/stress | velocidad y límites bajo carga | muchas requests simultáneas |
| UAT | aceptación del usuario/negocio | cliente valida que sirve para salir a producción |

Pirámide mental:

```
        /\        E2E         (caros, lentos, frágiles)
       /  \       Postman / cypress
      /----\
     / int. \     Integración  (Supertest: HTTP -> capas)
    /--------\
   /  unitar.  \  Unitarios    (Jest: dominio aislado, baratos)
  /------------\
```

> Cuanto más alta la prueba en la pirámide, más confianza da pero más cuesta. **Baja en la pirámide cuando podés**: si una regla la podés probar a nivel dominio, no la pruebes a nivel HTTP.

### 2) Jest: instalación y scripts

Instalación:

```bash
npm install --save-dev jest
```

El PDF muestra:

```json
{
  "scripts": {
    "test": "NODE_OPTIONS=--experimental-vm-modules jest"
  }
}
```

**Decisión del repo `clase6-testing`** (`package.json`): usa una variante más portable porque `NODE_OPTIONS=...` no funciona igual en Windows:

```json
{
  "type": "module",
  "scripts": {
    "test": "node --experimental-vm-modules node_modules/jest/bin/jest.js",
    "test:watch": "node --experimental-vm-modules node_modules/jest/bin/jest.js --watch"
  },
  "jest": { "testEnvironment": "node" }
}
```

Por qué la flag `--experimental-vm-modules`: el proyecto es ESM (`"type": "module"`) y Jest historicamente fue CommonJS. La flag habilita el loader experimental para que Jest entienda `import`/`export` sin Babel.

Aserciones que vas a usar siempre:

| Categoría | Aserciones |
| --------- | ---------- |
| Generales | `toBe` (igualdad exacta), `toEqual` (equivalencia, objetos), `toBeNull`, `toBeUndefined`, `toBeDefined`, `toBeTruthy`, `toBeFalsy` |
| Numéricas | `toBeGreaterThan`, `toBeGreaterThanOrEqual`, `toBeLessThan`, `toBeLessThanOrEqual`, `toBeCloseTo` (decimales) |
| Errores | `toThrow(ClaseError)` |
| Mocks | `toHaveBeenCalled`, `toHaveBeenCalledWith(args)`, `toHaveBeenCalledTimes(n)` |

Diferencia clave que confunden todos: `toBe` usa `===` (mismo objeto en memoria); `toEqual` compara recursivamente las props. Para objetos plano siempre `toEqual`.

### 3) Tests unitarios: el patron Condicion - Ejecución - Resultado

Un test unitario aisla **una unidad** (clase/función) y verifica un comportamiento. La estructura es siempre la misma:

1. **Condiciones / Arrange**: armás el escenario.
2. **Ejecución / Act**: corres lo que quieres probar.
3. **Resultado / Assert**: comparas obtenido vs esperado.

Ejemplo del PDF:

```js
describe("Descuento porcentual", () => {
  test("El valor descontado de un descuento porcentual", () => {
    const descuentoPorcentual = new DescuentoPorcentual(20)        // Arrange
    const valorDescontado = descuentoPorcentual.valorDescontado(100, 2) // Act
    expect(valorDescontado).toBe(40)                                // Assert
  })
})
```

**Ejemplo real del repo** - `tests/unitarios/Descuento.test.js`:

```js
import { describe, expect, test } from "@jest/globals"
import { DescuentoFijo, DescuentoPorcentual } from "../../server/domain/Descuento.js"
import { Producto } from "../../server/domain/Producto.js"

describe("DescuentoPorcentual", () => {
  describe("valorDescontado", () => {
    test("debe retornar el porcentaje del precio total (precio * cantidad)", () => {
      const descuento = new DescuentoPorcentual(10)
      const producto = new Producto("Arroz", 1000, 5, "Alimentos")

      expect(descuento.valorDescontado(producto)).toBe(500)
    })

    test("debe retornar el precio total completo con descuento del 100%", () => {
      const descuento = new DescuentoPorcentual(100)
      const producto = new Producto("Coca-Cola", 2500, 2, "Bebidas")

      expect(descuento.valorDescontado(producto)).toBe(5000)
    })
  })
})
```

**Decisiones de diseño del repo** que vale la pena destacar:

- **`describe` anidado por método**: cada clase tiene un describe externo y un describe interno por cada método publico (`constructor`, `precioFinal`, `agregarDescuento`). Asi el output del runner se lee como un arbol de comportamientos, no como una lista plana.
- **Casos felices + casos de borde + casos de error**: en `Producto.test.js` no solo hay tests del happy path, hay tests que verifican que el constructor lanza `UnprocessableEntityError` cuando el precio es cero, negativo, no-numero, o cuando la cantidad es decimal. Si tu test suite solo prueba lo que anda, no está haciendo testing.
- **Verificar el tipo de error, no solo que tire**: `expect(() => new Producto(...)).toThrow(UnprocessableEntityError)`. No alcanza con "lanzo algo": tiene que ser el error correcto.
- **`beforeEach` para SUT (System Under Test) compartido**: en `Producto.test.js` el describe de `agregarDescuento` arma un producto fresco en cada test para que no se contaminen entre si.

Mira como queda el patron en `Producto.test.js`:

```js
describe("Producto", () => {
  describe("constructor", () => {
    test("debe lanzar error si el precio es negativo", () => {
      expect(() => new Producto("Leche", -100, 5, "Lácteos"))
        .toThrow(UnprocessableEntityError)
    })
  })

  describe("precioFinal", () => {
    test("no debe retornar precio negativo aunque los descuentos superen el total", () => {
      const producto = new Producto("Pan", 100, 1, "Panadería")
      producto.agregarDescuento(new DescuentoFijo(9999))
      expect(producto.precioFinal()).toBe(0)
    })
  })

  describe("agregarDescuento", () => {
    let producto
    beforeEach(() => {
      producto = new Producto("Leche", 800, 2, "Lácteos")
    })
    test("debe lanzar error si el descuento no tiene el método valorDescontado", () => {
      expect(() => producto.agregarDescuento({ valor: 100 }))
        .toThrow(UnprocessableEntityError)
    })
  })
})
```

Errores típicos:
- Tests que dependen del orden de ejecución (estado compartido entre tests sin `beforeEach`).
- Asserts gigantes que prueban diez cosas a la vez. **Un test, un comportamiento**.
- No probar el caso de borde "limite superior 0 / negativo / vacio".

### 4) Mocking: que es y cuando lo necesitas

Mock = **doble de prueba**. Reemplazas una dependencia real (BD, servicio externo, repo) por una version controlada para:

- Aislar la unidad bajo prueba (no dependes de la red ni de un archivo).
- Determinismo (siempre devuelve lo mismo).
- Velocidad (no hay I/O real).
- Testear casos dificiles (un timeout, un 500, un dato corrupto).

#### Stub, mock y spy

La teoría distingue tres dobles de prueba que suelen mezclarse:

| Doble | Para qué sirve | Qué te interesa observar |
|---|---|---|
| Stub | devolver datos prefijados | que el SUT pueda avanzar sin dependencia real |
| Mock | simular una dependencia y verificar interacción | si fue llamado, con qué argumentos y cuántas veces |
| Spy | envolver un método real y observarlo | qué pasó sin reemplazar del todo la implementación |

En la práctica con Jest, muchas veces `jest.fn()` alcanza para implementar stubs o mocks simples. La diferencia importante no es la sintaxis: es **qué intención tiene el test**.

Jest da dos primitivas:

- `jest.fn()` -> crea una función mock. Por defecto retorna `undefined`.
- `jest.fn().mockReturnValue(x)` -> para funciones sincrónicas.
- `jest.fn().mockResolvedValue(x)` -> para async/promises (devuelve `Promise.resolve(x)`).
- `jest.fn().mockRejectedValue(err)` -> para simular errores async.

**Mock funcional (PDF)**:

```js
function fetchUserData(getUserFromDatabase, userId) {
  return getUserFromDatabase(userId)
}

test('should fetch user data', () => {
  const mockGetUserFromDatabase = jest.fn().mockResolvedValue({ id: 1, name: 'John Doe' })
  const userData = fetchUserData(mockGetUserFromDatabase, 1)
  expect(mockGetUserFromDatabase).toHaveBeenCalledWith(1)
})
```

**Mock de objeto (PDF)**: cuando el SUT recibe un objeto via constructor (DI), le pasas un mock con la misma forma:

```js
const mockDatabaseService = {
  query: jest.fn().mockResolvedValue({ id: 1, name: 'John Doe' })
}
const userService = new UserService(mockDatabaseService)
expect(mockDatabaseService.query).toHaveBeenCalledWith('SELECT * FROM users WHERE id = 1')
```

Esto **es exactamente** lo que el repo hace en los tests de integración para mockear el repository (ver siguiente sección).

> Pregunta de examen: **¿por qué mockeamos el repository y no la base de datosí** Porque la abstracción `repository` es nuestra frontera de capa: si mockeamos al repo, probamos service + controller juntos sin acoplarnos a un motor de persistencia. Esto es coherente con la arquitectura por capas de la Clase 04.

### 5) Tests de integración con Supertest

`supertest` te deja hacer requests HTTP a tu app de Express **sin levantar un servidor real**. Pasa por el stack completo (router -> middlewares -> controller -> service) pero el repository es un mock.

Instalación:

```bash
npm install --save-dev supertest
```

**Decision clave del repo**: `tests/integracion/utils/buildApp.js` arma una app **especifica para tests**, sin Swagger ni `cors`, con el repo inyectado como mock. Asi cada test elige que devuelve el repo:

```js
// tests/integracion/utils/buildApp.js
export function buildTestApp(productoRepository) {
  const productoService = new ProductoService({ productoRepository })
  const productoController = new ProductoController({ productoService })

  const app = express()
  app.use(express.json())

  const router = express.Router()
  router.route("/")
    .get((req, res, next) => productoController.findAll(req, res, next))
    .post((req, res, next) => productoController.create(req, res, next))
  router.route("/:id")
    .get((req, res, next) => productoController.findById(req, res, next))
    .put((req, res, next) => productoController.update(req, res, next))
    .delete((req, res, next) => productoController.delete(req, res, next))

  app.use("/productos", router)
  app.use(notFoundHandler)
  app.use(errorHandler)
  return app
}
```

Por qué está separado de `server/app.js`:

- En tests no quieres dotenv ni swagger ni cors -> menos ruido, menos efectos colaterales.
- Cada test crea su propio `productoRepository` mock con `jest.fn()` -> aislamiento total.
- **No hay `errorLogger`**: en tests no nos interesa loguear errores, solo verificar la respuesta.

Y el test usandolo (`tests/integracion/productos.test.js`):

```js
import request from "supertest"
import { describe, expect, jest, test, beforeEach } from "@jest/globals"
import { buildTestApp } from "./utils/buildApp.js"
import { Producto } from "../../server/domain/Producto.js"

describe("Productos API - Integración", () => {
  let app
  let productoRepository

  beforeEach(() => {
    productoRepository = {
      obtenerPaginados: jest.fn(),
      obtenerPorId: jest.fn(),
      obtenerPorNombre: jest.fn(),
      guardar: jest.fn(),
    }
    app = buildTestApp(productoRepository)
  })

  test("debe retornar 200 con lista paginada de productos", async () => {
    const productosMock = [new Producto("Leche", 800, 10, "Lácteos")]
    productosMock[0].id = 1
    productoRepository.obtenerPaginados.mockReturnValue({
      productos: productosMock,
      totalProductos: 1,
    })

    const response = await request(app).get("/productos")

    expect(response.status).toBe(200)
    expect(response.body.status).toBe("success")
    expect(response.body.paginacion.numeroPagina).toBe(1)
  })
})
```

Cosas para observar en el test suite del repo:

- **400 vs 422**: `POST /productos` con `precio: "mil pesos"` -> `422` (regla de dominio: el constructor de `Producto` tira `UnprocessableEntityError`). Pero `POST /productos` con campo extra `campoExtra` -> `400` (validacion de schema en el controller, antes del dominio). **El status code te dice donde fallo**: 400 = error del cliente al armar la request; 422 = la request está bien formada pero rompe una regla de negocio. Esto coincide con lo de Clase 05.
- **404 vs 409**: `PUT` a id inexistente -> `404`. `POST` con nombre duplicado -> `409` (conflicto de estado). Si confundis estos dos, tu API miente.
- **Verificar que NO se llamo al repo**: cuando una request es invalida, el test verifica `expect(productoRepository.guardar).not.toHaveBeenCalled()`. Esto valida que el cortocircuito de errores funciona y no llegamos a la capa de persistencia.
- **`mockImplementation` para simular efecto secundario**: `productoRepository.guardar.mockImplementation((p) => { p.id = 1; return p })` simula que el repo asigna un id al guardar.

> Si te llaman al parcial: un test de integración **prueba la colaboracion entre capas**. Si solo prueba el dominio aislado, es unitario. Si solo prueba que la ruta existe, es smoke test.

### 6) Tests externos con Postman

Postman tambien sirve como integración, pero **a otro nivel**: vos corres tu app real, Postman le pega por HTTP desde afuera. Tradeoffs:

| | Supertest | Postman |
| - | --------- | ------- |
| Velocidad | Rapido (mismo proceso) | Mas lento (red + servidor real) |
| Control de dependencias | Total (mocks) | Bajo (BD/servicios reales) |
| Reproducibilidad | Alta | Depende del ambiente |
| Cuando usar | CI / TDD / cada commit | Smoke tests post-deploy / QA manual |

El repo trae `postman/Producto-CRUD.postman_collection.json` para ejercicios manuales de Clases 03/04, pero el testing automatizado vive en Jest + Supertest.

### 7) Documentación con OpenAPI / Swagger

OpenAPI es un **estándar para describir APIs REST** (antes se llamaba Swagger; hoy Swagger es la suite de herramientas). Es un YAML/JSON con la forma de tu API: paths, parámetros, schemas, status codes, ejemplos.

Por qué importa:

- Es **contrato**: frontend/mobile/integradores consumen la doc, no el código.
- Permite generar clientes y servidores automáticamente.
- Es **inspeccionable**: con `swagger-ui-express` tenés una UI lista para tu equipo.

Instalación:

```bash
npm install swagger-ui-express
```

**Version del PDF** (carga el JSON con `readFile` async):

```js
import express from "express"
import swaggerUiExpress from "swagger-ui-express"
import { readFile } from "fs/promises"

const swaggerDocument = JSON.parse(
  await readFile(new URL("../docs/api-docs.json", import.meta.url))
)

export function swaggerRoutes() {
  const router = express.Router()
  router.use("/api-docs", swaggerUiExpress.serve)
  router.get("/api-docs", swaggerUiExpress.setup(swaggerDocument))
  return router
}
```

**Decisión del repo** (`server/app.js`): usa `createRequire` para cargar el JSON de forma sincronica desde un modulo ESM. Es más corto y evita el `await` top-level:

```js
import express from "express"
import swaggerUi from "swagger-ui-express"
import { createRequire } from "module"

const require = createRequire(import.meta.url)
const swaggerSpec = require("./docs/swaggerSpec.json")

const app = express()
app.use(express.json())
app.use(cors())
app.use("/api-docs", swaggerUi.serve, swaggerUi.setup(swaggerSpec))
app.use(router)
```

> Por qué `createRequire`: en ESM no podés hacer `import x from "./x.json"` sin assertion (`with { type: "json" }`), que tiene soporte irregular. `createRequire` te abre la puerta CJS para JSON sin tener que reescribir nada.

Estructura del `swaggerSpec.yaml` (resumida):

```yaml
openapi: "3.0.3"
info:
  title: MegaSuper
  version: "1.0.0"
paths:
  /productos:
    get:
      tags: [Productos]
      summary: Listar productos
      parameters:
        - name: page
          in: query
          schema: { type: integer, minimum: 1, default: 1 }
        - name: precioMin
          in: query
          schema: { type: number, minimum: 0 }
      responses:
        200:
          description: Lista de productos obtenida correctamente
          content:
            application/json:
              schema:
                type: object
                properties:
                  status: { type: string, example: success }
                  data:
                    type: array
                    items: { $ref: "#/components/schemas/Producto" }
                  paginacion:
                    $ref: "#/components/schemas/Paginacion"
        400:
          $ref: "#/components/responses/BadRequest"
```

Lo importante de la doc no es la sintaxis, son las **decisiones de diseño** que ya quedan documentadas:

- Cada parametro tiene tipo y restricciones (`minimum: 1`, `default: 10`) -> es la mismásima validacion del controller.
- Cada response apunta a un `$ref` reutilizable -> DRY en la doc.
- Los status codes son exactamente los que el controller responde.

> Si la doc dice una cosa y el código otra, **mentiste**. Por eso está version vive en el repo y se actualiza con el PR.

Una vez levantada la app, la UI está en `http://localhost:PORT/api-docs`.

### 8) Errores típicos y gotchas detectados en el repo

- **`agregarDecuento` (typo)**: en `server/domain/Producto.js` existe un método `agregarDecuento` (sin la "s") como alias del bueno. Es deuda técnica visible. No está cubierto por tests.
- **Tests no cubren `DescuentoPorCantidad`**: la clase existe en `Descuento.js` pero no hay tests. Y como ya vimos en Clase 04, su calculo tiene un olor a bug. Justamente lo que el testing deberia atrapar.
- **`buildTestApp` duplica wiring**: si manana cambias rutas en `productoRoutes.js`, te olvidas de tocar `buildTestApp.js` y los tests siguen verdes contra rutas obsoletas. Tradeoff: aislamiento vs duplicacion.
- **Falta test de `notFoundHandler` con error real**: solo hay un test de "ruta inexistente", no uno que verifique que un `AppError` lanzado en el service termina como JSON con el `status` correcto.

### 9) Comandos útiles

```bash
# Correr todos los tests
npm test

# Solo unitarios
npm test -- tests/unitarios

# Solo integración
npm test -- tests/integracion

# Modo watch
npm run test:watch

# Un test puntual por nombre
npm test -- -t "debe retornar 404"

# Coverage (sin instalar nada extra: jest lo trae)
npm test -- --coverage
```

### 10) Herramientas del ecosistema

La clase no se queda solo en "Jest + Supertest". Hay un conjunto de herramientas alrededor que el profe nombra y que conviene saber para que sirven, aunque no entremos a fondo.

#### 10.1 Jest

- Sitio: https://jestjs.io/
- Es **framework + test runner + libreria de aserciones + libreria de mocks**, todo en uno. Por eso es tan popular en el ecosistema Node.
- Lo que tenés que recordar para examen: `describe / test / expect`, `beforeEach / afterEach`, `jest.fn()`, `mockReturnValue`, `mockResolvedValue`, `toThrow`, modo `--watch`, `--coverage`.

#### 10.2 Supertest

- Sitio: https://www.npmjs.com/package/supertest
- Cliente HTTP **embebido** que envia requests contra una instancia de Express **sin abrir un puerto real**. No es un browser ni un curl: es una abstracción sobre la app de Express en memoria.
- Por eso `buildTestApp(productoRepository)` devuelve una `app` y Supertest le hace `request(app).get(...)`. Mas rápido, más reproducible, sin colisiones de puertos en CI.

#### 10.3 ESLint (bonus)

- Sitio: https://eslint.org/
- Es un **linter**: analiza el código **sin ejecutarlo** y marca problemás (variables sin usar, imports rotos, estilos inconsistentes, posibles bugs).
- En el repo `clase6-testing` aparece como dependencia:

```json
{
  "scripts": { "lint": "eslint ." },
  "devDependencies": { "eslint": "^10.2.1" }
}
```
##### configuración basica de ESLint
```js
export default [
    {
        ignores: ["node_modules/**", "index.js", "funciones.js"]
    },
    {
        languageOptions: {
            ecmaVersion: 2022,
            sourceType: "module",
            globals: {
                console: "readonly",
                process: "readonly",
            }
        },
        rules: {
            "no-unused-vars": ["warn", { argsIgnorePattern: "^_" }],
            "no-console": "off",
            "no-undef": "error",
        }
    }
]
```


> Diferencia conceptual importante: **tests** verifican que el código se **comporta** bien; **lint** verifica que el código **está bien escrito**. Son complementarios, no sustitutos. Un test passing no te dice si tenés un import muerto; un lint passing no te dice si la logica está rota.

#### 10.4 Postman: tests automatizados con scripts

- Doc oficial: https://learning.postman.com/docs/tests-and-scripts/write-scripts/test-examples/
- Postman no es solo "click y mira la respuesta". Cada request puede tener un **bloque de tests en JavaScript** que corre despues de recibir la respuesta. Es la version Postman de un test de integración externo.

Ejemplo típico - validar status y forma de la respuesta:

```js
pm.test("Status code is 200", function () {
  pm.response.to.have.status(200)
})

pm.test("Response has products array", function () {
  const json = pm.response.json()
  pm.expect(json.data).to.be.an("array")
  pm.expect(json.paginacion.numeroPagina).to.eql(1)
})

pm.test("Response time is acceptable", function () {
  pm.expect(pm.response.responseTime).to.be.below(500)
})
```

Cuando exportas la coleccion como `.postman_collection.json`, esos tests viajan adentro. Despues podés correrla en CI con **Newman** (el CLI de Postman). Util para humo (smoke tests) post-deploy.

> Comparado con Supertest: Supertest corre **en proceso** contra tu app, Postman corre **en red** contra una instancia desplegada. Cada uno cubre un nivel distinto.

#### 10.5 Editores de OpenAPI / Swagger

Editar un YAML/JSON de OpenAPI a mano es proclive a errores (indentación, refs rotas). Por eso hay editores específicos:

- **Swagger Editor (oficial)**: https://editor-next.swagger.io/
  - Editor online, gratis, sin instalación.
  - Panel izquierdo: YAML/JSON. Panel derecho: preview renderizado en vivo.
  - Valida el spec mientras escribís y te marca errores.
- **Apicurito**: https://www.apicur.io/apicurito/pwa/
  - Editor más visual (formularios, no solo YAML).
  - Bueno si no querías tocar YAML directamente o si trabajas con gente no-técnica.

Flujo de trabajo típico:

1. Diseñar el contrato en Swagger Editor o Apicurito.
2. Exportar como `swaggerSpec.yaml` o `swaggerSpec.json`.
3. Servir en la API con `swagger-ui-express` (ver punto 7).
4. **Actualizar la doc en el mismo PR que cambia el endpoint** - si no, mentís.

> Convención sana: tratar al spec de OpenAPI como **código fuente**, no como documentación. Vive en el repo, se revisa en code review, se actualiza con el cambio. Es el contrato de tu API.

---

### 11) Resumen mental de Clase 06

Si te preguntan "¿cómo se testea una API en Node?":

> Tests unitarios con Jest para el dominio (clases puras, sin I/O), tests de integración con Supertest que arman una app de Express con el repository mockeado para verificar el flujo HTTP -> controller -> service -> repository, y la API se documenta con OpenAPI servida vía `swagger-ui-express`. Los unitarios cubren reglas de dominio; los de integración cubren contrato HTTP, status codes y validaciones de borde.

Checklist para examen:

- Patrón AAA / Condición-Ejecución-Resultado.
- TDD escribe tests antes del código; BDD expresa comportamiento esperado desde negocio.
- Unitario, funcional, integración, E2E, regresión, rendimiento/carga/stress y UAT no prueban lo mismo.
- `describe` anidado por clase y método.
- `toBe` (===) vs `toEqual` (deep equality).
- `jest.fn()`, `mockReturnValue`, `mockResolvedValue`, `toHaveBeenCalledWith`.
- Stub devuelve datos; mock verifica interacción; spy observa un método real.
- Mocks para aislar dependencias y testear errores controlados.
- Supertest hace requests sin servidor real al mismo `app` de Express.
- `buildTestApp` separa la app de producción de la app de testing.
- Status codes en integración coherentes con Clase 05 (400 schema, 404 not found, 409 conflict, 422 dominio).
- OpenAPI / Swagger = contrato de la API (YAML/JSON), expuesto vía `swagger-ui-express` en `/api-docs`.

---


## Clase 07 - Persistencia y ODM con Mongoose

Fuentes usadas:
- Teoría: `Clases_Teoria/1C2026 - DDSW - MN - Clase 7 - Resumen.pdf`
- Cache teoría: `_cache_pdf_text/1C2026 - DDSW - MN - Clase 7 - Resumen.txt`
- Práctica: `Clases_Practica/Clase Práctica -  07 - ODM.pdf`
- Cache práctica: `_cache_pdf_text/Clase Practica - 07 - ODM.txt`
- Toma propia: `Clases_Practica/Clase 07 -apuntes de clase.md`

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase7-presistencia-odm-alojamientos
- Local: `_tmp_ddso_ejercicio-megasuper-2026` (branch `clase7-presistencia-odm-alojamientos`)
- Estructura del ejemplo: el branch contiene **otro proyecto** dentro de `practica-persistencia-odm/`, una API REST de alojamientos (no de productos como en clases 4-6). Cambia el dominio para empujarte a pensar conceptos, no a copiar código.

### Idea central de la clase

Hasta acá veníamos construyendo APIs que podían ordenar responsabilidades, validar, manejar errores y testear; pero todavía faltaba una pieza clave: que los datos **sobrevivan al proceso**.

Esta clase conecta la arquitectura por capas con una base real: MongoDB como base documental y Mongoose como ODM. La idea no es aprender comandos sueltos de Mongo, sino entender **dónde vive cada responsabilidad** cuando aparece persistencia: schema, model, repository, service, controller y DTO.

### 1) Persistencia: qué es y dónde

La **persistencia** es la propiedad de que el estado del sistema **sobreviva** más allá del proceso. Si apagás el servidor y al prenderlo perdiste los datos, no estás persistiendo: estás usando memoria.

Estrategias posibles:

| Estrategia | Dónde vive el dato | Cuándo se usa |
| ---------- | ------------------ | ------------- |
| Memoria | RAM del proceso | Cache, sesiones efímeras, tests, ejercicios |
| Archivos | Disco local (JSON, CSV) | Datos chicos, configuración, prototipos |
| Base de datos | Servicio separado | Casi todo lo serio: BD relacional, NoSQL u orientada a objetos |

Lo que cambia es el **costo de cada operación** y la **garantía que te da**. La memoria es rapidísima pero volátil; los archivos son persistentes pero te peleás con la concurrencia; la BD te resuelve persistencia, concurrencia, consistencia, índices y muchas otras cosas a cambio de **un proceso aparte que mantener**.

La teoría también menciona sistemas distribuidos y almacenamiento en la nube. No cambian la definición de persistencia, pero sí cambian quién opera la infraestructura, cómo se replica la información y qué tradeoffs aparecen entre disponibilidad, latencia y consistencia.

### 2) Clasificación de bases de datos

Tres familias grandes:

| Familia | Modelo de datos | Ejemplos |
| ------- | --------------- | -------- |
| **Relacional (SQL)** | Tablas + esquemas rígidos + relaciones vía FK | MySQL, PostgreSQL, SQL Server |
| **NoSQL** | Muchos sub-modelos. Más flexibles, pensadas para escalar | MongoDB, Redis, Cassandra, Neo4j |
| **Orientada a objetos** | Persiste objetos tal como existen en el código | db4o, ObjectDB (poco comunes) |

Dentro de NoSQL hay 4 sub-familias importantes:

- **Documentales** (MongoDB, CouchDB): cada registro es un **documento JSON-like**. Flexible.
- **Clave-valor** (Redis, DynamoDB): solo `clave -> valor`. Rapidísimas. Cache, sesiones, contadores.
- **Columnares** (Cassandra, HBase): optimizadas para lectura masiva y analítica.
- **Grafos** (Neo4j, ArangoDB): cuando lo importante son las **relaciones** entre nodos (redes sociales, recomendación).

> Pregunta de examen: "¿cuándo elegís NoSQL sobre SQL?". Respuesta corta: cuando **no hacés joins complejos** entre entidades, cuando priorizás **flexibilidad de esquema** o **escalabilidad horizontal**, y cuando tus datos son naturalmente **semiestructurados** (documentos anidados, listas, propiedades opcionales). NoSQL no es "mejor", es **distinto**.

#### 2.1 Mapeos: cómo pasás del modelo de objetos al almacenamiento

Cuando trabajás en capas, tu código piensa en **objetos** y la base guarda datos con otra forma. El "mapping" es el puente entre esos dos mundos.

| Mapeo | Base asociada | Qué resuelve |
| ----- | ------------- | ------------- |
| **ORM** (*Object Relational Mapping*) | SQL / relacional | Mapea objetos a tablas, filas y relaciones. |
| **ODM / Document Mapping** | Documental, como MongoDB | Mapea objetos a documentos JSON-like. |
| **Key-Value Mapping** | Clave-valor | Mapea una clave a un valor completo. |
| **Column-Family Mapping** | Columnares | Organiza datos por familias de columnas para lecturas masivas. |

El **Document Mapping** encaja bien cuando querés recuperar un agregado completo en una consulta: por ejemplo, un alojamiento con datos simples embebidos. Su costo aparece cuando necesitás muchas relaciones cruzadas, joins frecuentes o documentos que crecen sin control.

#### 2.2 ACID y CAP: dos límites que ordenan la discusión

No hace falta convertir esta clase en teoría de bases de datos, pero sí conviene ubicar dos ideas:

- **ACID** describe garantías de una transacción: atomicidad, consistencia, aislamiento y durabilidad. Es el lenguaje clásico de las bases relacionales cuando importa que una operación compleja se confirme completa o no se confirme.
- **CAP** aparece en sistemas distribuidos: ante particiones de red, no podés maximizar al mismo tiempo consistencia, disponibilidad y tolerancia a particiones. Elegir tecnología también es elegir qué tradeoff aceptás.

MongoDB no elimina estas discusiones: las mueve al diseño del documento, a la forma de consultar y al nivel de consistencia que necesita el caso de uso.

### 3) MongoDB: terminología y características

MongoDB es la BD documental más popular. Datos clave:

| MongoDB | Equivalente SQL |
| ------- | --------------- |
| Database | Database |
| Collection | Table |
| Document | Row |
| Field | Column |
| Embedded document | (no hay directo) |
| `_id` | Primary key |

Características de los documentos:

- **Flexible**: dos documentos de la misma colección pueden tener **estructura distinta**. Es la idea de "schema-less".
- **Anidado**: un documento puede contener otros documentos (sub-documentos) y arrays.
- **Autoidentificado**: cada documento tiene `_id` como identificador único.
- **Autónomo**: tiene **toda la información** para representar la entidad (no necesitas hacer 5 joins).

Ejemplo de documento:

```json
{
  "_id": "507f1f77bcf86cd799439011",
  "nombre": "Juan",
  "edad": 25,
  "hobbies": ["futbol", "lectura"],
  "direccion": {
    "calle": "Av. Medrano",
    "numero": 951
  }
}
```

#### 3.1 ObjectId

El `_id` por defecto es un **ObjectId**: 12 bytes de tipo BSON especial.

```
4 bytes - timestamp (cuando se creo)
5 bytes - identificador unico del host/proceso
3 bytes - contador aleatorio
```

> Detalle útil: como los primeros 4 bytes son timestamp, **un ObjectId te dice cuándo se creó el documento sin tener que guardar un campo aparte**. Útil para ordenar por antigüedad sin agregar `createdAt`.

ObjectId **no** es UUID, pero cumple un rol similar: es único prácticamente con probabilidad 1. es decir, no hay colisiones en la práctica.

### 4) CRUD básico en MongoDB

Comandos del **mongo shell** (los vas a tipear en Compass o en `mongosh`):

```js
// Insertar
db.usuarios.insertOne({ nombre: "Carlos", edad: 28 })
db.usuarios.insertMany([{ nombre: "Ana" }, { nombre: "Luis" }])

// Buscar
db.usuarios.findOne({ _id: ObjectId("507f1f77bcf86cd799439011") })
db.usuarios.find()                            // todos
db.usuarios.find({ edad: { $gte: 25 } })      // mayores o iguales a 25
db.usuarios.find({ edad: { $gte: 18 }, pais: "AR" })          // AND implicito
db.usuarios.find({ $or: [ { edad: { $lt: 18 } }, { pais: "AR" } ] })
db.usuarios.find().sort({ edad: -1 }).limit(5) // top 5 mas grandes

// Actualizar
db.usuarios.updateOne({ nombre: "Carlos" }, { $set: { edad: 29 } })

// Borrar
db.usuarios.deleteOne({ nombre: "Carlos" })
```

Operadores de comparación más usados:

| Operador | Uso |
| -------- | --- |
| `$eq` / `$ne` | Igual / distinto |
| `$gt` / `$gte` / `$lt` / `$lte` | Mayor, menor, etc. |
| `$in` / `$nin` | En lista / fuera de lista |
| `$exists` | El campo existe o no |
| `$type` | Filtrar por tipo BSON |
| `$regex` | Coincidencia con regex |

> Notación mental: `{ campo: { $operador: valor } }` es el patrón. Si lo internalizas, todas las queries de Mongo te van a salir derechas.

### 5) Embebidos vs Referencias (decisión de modelado clave)

Cuando dos entidades están relacionadas, en Mongo tenés **dos formas de modelarlas** y cada una tiene tradeoffs.

#### 5.1 Documentos embebidos

Meter un documento adentro de otro:

```json
{
  "_id": 1,
  "nombre": "Lucia",
  "direccion": {
    "calle": "Paunero",
    "numero": 123
  }
}
```

**Conviene cuando**:
- La relación es **uno a pocos** (`oneToAFew`).
- Los datos **siempre se consultan juntos**.
- El tamaño total no crece sin limite.
- La entidad contenida **no tiene sentido sin la contenedora** (ciclo de vida atado).

Ventajas: una sola consulta, atomicidad, datos juntos.

> Límite real: un documento de MongoDB no debería crecer sin control. Si un array embebido puede crecer indefinidamente, el modelado empieza a pedir **referencias**. Además, MongoDB tiene un límite técnico de 16 MB por documento.

#### 5.2 Referencias

Guardar solo el `ObjectId` del otro documento:

```json
// Coleccion personas
{ "_id": 1, "nombre": "Lucia", "direccion_id": ObjectId("X") }

// Coleccion direcciones
{ "_id": ObjectId("X"), "calle": "Paunero", "numero": 123 }
```

**Conviene cuando**:
- Relacion **muchos a muchos** o **uno a muchos grandes**.
- Las entidades tienen **ciclo de vida independiente**.
- Se consultan **por separado** la mayor parte del tiempo.
- Querés **flexibilidad** para evolucionar cada colección.

Ventajas: independencia, evitás duplicación, podés escalar cada colección por separado.

#### 5.3 Cómo elegir

| Pregunta | Embebido | Referencia |
| -------- | -------- | ---------- |
| ¿Los datos se consultan juntos casi siempre? | Sí | No |
| ¿La entidad contenida puede existir sola? | No | Sí |
| ¿La relación es 1 a muchos grandes (cientos+)? | No | Sí |
| ¿Necesitás actualizar la entidad contenida desde afuera? | No | Sí |
| ¿Es una relación `many-to-many`? | Casi nunca | Sí |

> En el repo de clase 7 las **reservas** referencian al **alojamiento** (`ref: 'Alojamiento'`), no lo embeben. Tiene sentido: un alojamiento tiene muchas reservas, una reserva pertenece a un alojamiento, y ambos tienen ciclo de vida propio.

### 6) ODM y Mongoose

#### 6.1 Qué es un ODM

**ODM = Object Document Mapper**. Es a Mongo lo que un ORM (Object Relational Mapper) es a SQL.

Te permite:
- Mapear **objetos JavaScript a documentos Mongo** (y al revés).
- Definir **esquemas** y validaciones de forma declarativa.
- Trabajar con una **interfaz OO**: en vez de escribir `db.usuarios.findOne({...})`, escribís `UsuarioModel.findOne({...})`.
- Agregar middlewares, virtuals, métodos custom.

Sin ODM: escribís queries crudas, validás todo a mano, mapeás a clase de dominio a mano. Funciona, pero es repetitivo y proclive a errores.

#### 6.2 Mongoose

[Mongoose](https://mongoosejs.com/) es el ODM por excelencia para Node.js. Lo instalás con:

```bash
npm install mongoose --save
```

Para correr el ejemplo localmente también necesitás tener MongoDB instalado o disponible como servicio, y opcionalmente MongoDB Compass para inspeccionar colecciones visualmente. `dotenv` entra en juego para leer `.env` sin hardcodear credenciales ni nombres de base.


Tres conceptos a internalizar:

| Concepto | Qué es | Ejemplo |
| -------- | ------ | ------- |
| **Schema** | Definición de la forma del documento (campos, tipos, validaciones, opciones) | `new mongoose.Schema({...})` |
| **Model** | Clase compilada a partir del schema. Es con la que interactuás | `mongoose.model("Alojamiento", schema)` |
| **Document** | Instancia del model, representa un registro real | `new AlojamientoModel({...})` |

> Un schema describe **cómo debe verse** un documento; un model es **la herramienta** para crear / leer / modificar documentos de esa forma.

### 7) La nueva capa: `schemas/`

Con Mongoose aparece una capa nueva que no estaba en clases anteriores: **`schemas/`**. Convive con `domain/` (las clases de dominio puras) y con `repositories/`.

En el repo de clase 7 la estructura queda así:

```
practica-persistencia-odm/
├── config/database.js          ← conexion a Mongo
├── models/
│   ├── entities/               ← dominio puro (Alojamiento, Reserva)
│   └── repositories/           ← acceso a datos
├── schemas/                    ← schemas de Mongoose (NUEVA CAPA)
│   ├── alojamientoSchema.js
│   └── reservaSchema.js
├── services/
├── controllers/
└── routes/
```

Qué hace cada una:

| Capa | Responsabilidad |
| ---- | --------------- |
| `entities/` | Clase de **dominio puro**: reglas y comportamiento, sin Mongo |
| `schemas/` | **Schema de Mongoose** + opciones de persistencia + middlewares |
| `repositories/` | Operaciones de persistencia, usan el `Model` exportado por el schema |
| `services/` | Casos de uso, validaciones de negocio |
| `controllers/` | HTTP, parseo de request, traducción a respuesta |

#### 7.1 Schema básico de Mongoose

Ejemplo real del repo (`schemas/alojamientoSchema.js`):

```js
import mongoose from 'mongoose'
import { Alojamiento } from '../models/entities/alojamiento.js'

const alojamientoSchema = new mongoose.Schema({
  nombre: {
    type: String,
    required: true,
    trim: true
  },
  precioPorNoche: {
    type: Number,
    required: true,
    min: 0
  },
  // Para soft delete
  eliminado: {
    type: Boolean,
    default: false
  }
}, {
  timestamps: true,             // agrega createdAt y updatedAt automaticos
  collection: 'alojamientos'    // nombre EXACTO de la coleccion en Mongo
})

// Carga los metodos de la clase de dominio sobre el schema
alojamientoSchema.loadClass(Alojamiento)

// Exporta el Model
export const AlojamientoModel = mongoose.model('Alojamiento', alojamientoSchema)
```

Cosas para observar:

- **Tipos**: `String`, `Number`, `Boolean`, `Date`, `mongoose.Schema.Types.ObjectId`, arrays, sub-schemas. Mongoose **valida tipos** antes de guardar.
- **Restricciones declarativas**: `required`, `min`, `max`, `trim`, `lowercase`, `enum`, `default`. Validación gratis.
- **`timestamps: true`**: te agrega `createdAt` y `updatedAt` automáticamente. **Usalo siempre**. Te salva la vida en debugging.
- **`collection: 'alojamientos'`**: por defecto Mongoose pluraliza el nombre del modelo (`Alojamiento -> alojamientos`), pero a veces conviene ser explícito para evitar sorpresas.
- **`loadClass(Alojamiento)`**: une la clase de dominio al schema. Así los métodos definidos en `Alojamiento` (como `getDescripcion()`, `tieneConflictoConFechas()`) **viajan con cada documento** que sale de Mongo.

#### 7.2 La paradoja del schema en una BD "schema-less"

> **Pregunta del alumno (real, en clase)**: si Mongo es schema-less, ¿por qué estamos definiendo schemasí

Respuesta del profe (perfecta): **Mongo es schema-less, Mongoose no lo es**.

- Mongo, motor crudo, **acepta cualquier estructura** dentro de una colección. Podés insertar `{nombre: "x"}` y al lado `{titulo: 123, items: [...]}`. Mongo no se queja.
- Mongoose, **arriba** de Mongo, **te impone disciplina**. El schema le dice: "para esta entidad voy a persistir estos campos con estas validaciones". Eso no quita que Mongo siga siendo flexible: si mañana querés agregar un campo, lo agregás al schema y listo, no hay `ALTER TABLE`.

> En criollo: Mongo te deja hacer cualquier cosa; Mongoose te ayuda a **no hacerla**. Si igual querías hacer cualquier cosa, podés ir directo al driver de Mongo sin el ODM. Pero a la tercera bug por falta de validación, te volvés al ODM corriendo.

#### 7.3 Schema con referencia + middleware de populate

Ejemplo real del repo (`schemas/reservaSchema.js`):

```js
const ReservaSchema = new mongoose.Schema({
  diaInicio:    { type: Date, required: true },
  diaFin:       { type: Date, required: true },
  nombreHuesped: {
    type: String,
    required: true,
    trim: true,
    validate: {
      validator: function(v) { return v && v.length >= 3 },
      message: 'El nombre del huesped debe tener al menos 3 caracteres.'
    }
  },
  alojamiento: {
    type: mongoose.Schema.Types.ObjectId,
    ref: 'Alojamiento',                   // referencia al model Alojamiento
    required: false
  }
}, { timestamps: true })

// Middleware: cada vez que se haga cualquier find, popular el alojamiento
ReservaSchema.pre(/^find/, function(next) {
  this.populate('alojamiento', '')
  next()
})

ReservaSchema.loadClass(Reserva)

export const ReservaModel = mongoose.model('Reserva', ReservaSchema)
```

Tres cosas para destacar:

1. **`ref: 'Alojamiento'`**: declara que `alojamiento` es una referencia a un documento de la colección `alojamientos`. En la BD se guarda solo el ObjectId; Mongoose sabe a dónde apuntar.

2. **`validate`** custom: validación de negocio adentro del schema. Útil para reglas simples; para reglas complejas, mejor en service/domain.

3. **Middleware `pre(/^find/, ...)`**: hook que se ejecuta **antes** de cualquier método cuyo nombre empiece con `find` (`find`, `findOne`, `findById`, etc.). En este caso hace **populate automático** del campo `alojamiento`: cuando traés una reserva, en vez de un `ObjectId` aparece el documento completo del alojamiento.

#### 7.4 Populate manual (sin middleware)

Si no querés autopopular, podés hacerlo on demand:

```js
const reservas = await ReservaModel.find().populate('alojamiento')
```
llamado desde el repository o el service. Esto te da **control total** sobre cuándo y qué popular.
Diferencia: con middleware **siempre** populás (puede ser overhead); manual te da control.

> **Gotcha importante**: si usás **soft delete** + populate automático, el populate **te trae el documento eliminado igual** porque el filtro `eliminado: false` no se propaga al populate. Si te importa que solo aparezcan los activos, tenés dos opciones:
>
> - Filtrar después: `if (reserva.alojamiento?.eliminado) { ... }`.
> - Configurar el populate con un match: `.populate({ path: 'alojamiento', match: { eliminado: false } })`.

### 8) Repository con Mongoose (operaciones reales)

El repository ahora **usa el Model** de Mongoose para las operaciones de persistencia. Todas son `async` porque hablan con la BD.

Ejemplo real (`models/repositories/alojamientoRepository.js`):

```js
import { AlojamientoModel } from '../../schemas/alojamientoSchema.js'

export class AlojamientoRepository {
  constructor() {
    this.model = AlojamientoModel
  }

  async findAll() {
    return await this.model.find({ eliminado: false })
  }

  async findById(id) {
    return await this.model.findById(id)
  }

  async save(alojamiento) {
    const nuevo = new this.model(alojamiento)
    return await nuevo.save()
  }

  async update(id, data) {
    return await this.model.findByIdAndUpdate(id, data, { new: true })
  }

  async delete(id) {
    return await this.model.findByIdAndDelete(id)
  }

  async count() {
    return this.model.countDocuments()
  }
}
```

Operaciones que vale memorizar:

| Operacion | Metodo del Model |
| --------- | ---------------- |
| Insertar | `new Model(data).save()` o `Model.create(data)` |
| Buscar todos | `Model.find(filtro)` |
| Buscar uno | `Model.findOne(filtro)` |
| Buscar por id | `Model.findById(id)` |
| Actualizar (devuelve el actualizado) | `Model.findByIdAndUpdate(id, data, { new: true })` |
| Borrar fisico | `Model.findByIdAndDelete(id)` |
| Contar | `Model.countDocuments(filtro)` |

> Detalle importante: `findByIdAndUpdate(...)` por defecto devuelve el **documento viejo**, antes del update. Casi nunca querés eso. La opción `{ new: true }` te devuelve el documento **ya actualizado**.

### 9) Paginación en el repository

> Decisión pedagógica clara del profe: la **paginación se hace en el repository**, no en el service ni en el controller.

Por qué: si paginás en service o controller, tenés que traer **todos** los documentos a memoria y después hacer `slice`. Eso anula la ventaja de tener BD. Si paginás en el **repository**, le pedís a Mongo **solo los que necesitás**.

```js
async findAllPaginated(page = 1, limit = 5) {
  const skip = (page - 1) * limit

  const alojamientos = await this.model
    .find()
    .skip(skip)
    .limit(limit)

  const total = await this.model.countDocuments()

  return {
    alojamientos,
    total,
    page,
    totalPages: Math.ceil(total / limit)
  }
}
```

Cosas para observar:

- `.skip(n)` salta los primeros `n` documentos.
- `.limit(n)` corta a `n` resultados.
- `countDocuments()` corre **aparte** de la query principal para saber el total real.
- Devolvemos un **objeto con metadata**: `total`, `page`, `totalPages`. El cliente sabe cuánto le falta.
- Si combinás paginación con soft delete, el filtro `eliminado: false` tiene que aplicarse tanto al `find()` como al `countDocuments()`. Si no, mostrás una página con activos pero calculás totales incluyendo borrados.

> Trampa de performance: `skip` en colecciones MUY grandes se vuelve caro (Mongo igual recorre lo que descarta). Para casos extremos se usa **paginación por cursor** (`{ _id: { $gt: ultimoId } }`). Para este nivel, skip+limit es perfecto.

### 10) Soft delete

**Soft delete = borrado lógico**: en vez de borrar físicamente el documento, le marcamos un flag `eliminado: true`. Las consultas filtran por `eliminado: false`.

Por qué: en sistemas reales **casi nunca querés perder datos**. Si alguien borró por error, querés poder revivirlo; si auditoría pregunta "¿qué pasó con la reserva 17?", querés poder contestar.

Implementación en el repo:

```js
// schema
eliminado: { type: Boolean, default: false }

// repository
async softDelete(id) {
  return await this.model.findByIdAndUpdate(
    id,
    { eliminado: true },
    { new: true }
  )
}

async findAll() {
  return await this.model.find({ eliminado: false })  // filtra los borrados
}
```

Decisiones a tomar cuando hay soft delete:

- ¿Todas las queries por defecto filtran `eliminado: false`? (Recomendado.)
- ¿Existe un endpoint para "ver eliminados" (admin)?
- ¿Existe "restaurar"? (Solo es cambiar el flag.)
- ¿Hay un proceso periódico que limpia eliminados viejosí (Garbage collection.)

> Si combinas soft delete con populate automático, **acordate del gotcha** del punto 7.4: el populate por defecto NO filtra borrados.

### 11) Agregación (aggregation pipeline)

La **agregación** es la herramienta más potente de Mongo. Te deja procesar documentos en una **secuencia de etapas** (pipeline) donde cada etapa transforma el resultado de la anterior.

Comparado con SQL:

| Mongo | SQL |
| ----- | --- |
| `$match` | `WHERE` |
| `$group` | `GROUP BY` |
| `$sort` | `ORDER BY` |
| `$limit` / `$skip` | `LIMIT / OFFSET` |
| `$lookup` | `JOIN` |
| `$project` | `SELECT` |
| `$unwind` | (no hay directo, "explota" un array en filas) |

Ejemplo real del repo: contar cuántas reservas tiene cada alojamiento y mostrar nombre + total.

```js
// capa de repository:
async reservasPorAlojamiento() {
  return await this.model.aggregate([
    // 1. Agrupar reservas por alojamiento y contar
    {
      $group: {
        _id: "$alojamiento",          // agrupa por el ObjectId del alojamiento
        totalReservas: { $sum: 1 }    // cuenta 1 por cada documento del grupo
      }
    },
    // 2. JOIN con la coleccion de alojamientos
    {
      $lookup: {
        from: "alojamientos",         // nombre REAL de la coleccion (no del Model)
        localField: "_id",            // _id actual = ObjectId del alojamiento
        foreignField: "_id",          // alojamientos._id
        as: "alojamiento"             // se guarda como array
      }
    },
    // 3. Desarmar el array (lookup siempre devuelve array, aunque haya 1 solo match)
    { $unwind: "$alojamiento" },
    // 4. Elegir que campos mostrar y como
    {
      $project: {
        _id: 0,
        alojamiento: "$alojamiento.nombre",
        totalReservas: 1
      }
    }
  ])
}
```

Lo importante:

- Cada **etapa** es un objeto en el array.
- **El orden importa**: cada etapa ve la salida de la anterior.
- **`$group._id`** define **por qué agrupás**, no es el id del documento original.
- **`$lookup`** siempre devuelve un **array** (de matches). Por eso casi siempre va seguido de `$unwind`.
- **`$project`** elige y renombra campos. `_id: 0` lo oculta; `campo: 1` lo incluye; `nuevo: "$viejo"` lo renombra.

> `$lookup` existe, pero no significa que convenga diseñar MongoDB como si fuera SQL con joins por todos lados. Si necesitás hacer `$lookup` constantemente en endpoints calientes, revisá si el documento está bien modelado, si conviene desnormalizar o si la relación debería resolverse de otra manera.

> Dónde vive la agregación: **en el repository**. Es una consulta a la BD, no lógica de negocio. El service la consume y eventualmente la transforma a DTO.

### 12) Conexión a Mongo (`config/database.js`)

Configuración centralizada de la conexión:

```js
import mongoose from 'mongoose'

export class MongoDBClient {
  static async connect() {
    try {
      const conn = await mongoose.connect(
        `${process.env.MONGODB_URI}/${process.env.MONGODB_DB_NAME}?authSource=admin`
      )
      console.log(`MongoDB is connected: ${conn.connection.host}`)
    } catch (error) {
      console.error(`Error: ${error.message}`)
      process.exit(1)
    }
  }
}
```

Cosas para observar:

- **Lee de `process.env`**: usa `dotenv` para cargar variables sensibles.
- **`process.exit(1)` si falla**: si no podés conectar a la BD, **no levantes el servidor**. Es mejor fallar rápido que servir un endpoint roto.
- **`authSource=admin`**: parámetro típico cuando MongoDB tiene autenticación habilitada.

`.env` del repo:

```
PORT=3000
MONGODB_DB_NAME=mi_base_de_datos
MONGODB_URI=mongodb://localhost:27017/mi_base_de_datos
```

> El `.env` **nunca se commitea** (`.gitignore`). Lo que se commitea es `.env.example` con las variables sin valores reales. Quien clone el repo sabe que tiene que llenar.

### 13) Async/await en cada capa

Con Mongo todas las operaciones son **async**. Eso obliga a llevar `async/await` por todas las capas:

```
Controller (async) -> Service (async) -> Repository (async) -> Mongoose
```

Ejemplo del flujo de un GET:

```js
// Controller
async findById(req, res, next) {
  try {
    const alojamiento = await this.alojamientoService.findById(req.params.id)
    res.json(alojamiento)
  } catch (error) {
    next(error)
  }
}

// Service
async findById(id) {
  const alojamiento = await this.alojamientoRepository.findById(id)
  if (!alojamiento) {
    throw new NotFoundError("Alojamiento no encontrado")
  }
  return this.toDTO(alojamiento)
}

// Repository
async findById(id) {
  return await this.model.findById(id)
}
```

Errores típicos:

- Olvidarse el `await` -> recibis una **Promise** en lugar del documento. `console.log` muestra `Promise { <pending> }`.
- Olvidarse el `try/catch` -> el error se propaga como **unhandled rejection**. Solución: `try/catch` + `next(error)` en el controller, o un wrapper de errores.
- Mezclar `.then()` con `async/await` -> funciona pero queda incoherente. Elegí uno.

### 14) DTO: Data Transfer Object

> Término que aparece en el service del repo.

Un **DTO** es un objeto que viaja entre capas (o hacia el cliente) y que **solo expone lo que querés exponer**. No es la entidad de dominio, no es el documento de Mongo: es la **forma curada** del dato.

Por qué importa: tu documento de Mongo puede tener campos internos (`__v` de Mongoose, `eliminado`, timestamps, password hash). Si los mandas al frontend, **estás filtrando** info. El DTO actúa de filtro.

Ejemplo del repo:

```js
toDTO(alojamiento) {
  return {
    id: alojamiento.id || alojamiento._id,
    nombre: alojamiento.nombre
    // precioPorNoche queda **fuera** del DTO en este caso
  }
}

async findAll() {
  const alojamientos = await this.alojamientoRepository.findAll()
  return alojamientos.map(a => this.toDTO(a))
}
```

> Convención: la transformación a DTO suele vivir en el **service**, no en el controller. Así cualquier consumidor del service recibe DTOs limpios sin preocuparse de filtrar.

### 15) Gotchas detectados en el repo

- **Nombre del directorio mal escrito**: `practica-persistencia-odm` está dentro de la rama, no en la raíz del repo. Si seguís el README hay que entrar primero a esa subcarpeta.
- **`bcrypt`, `bcryptjs`, `jsonwebtoken` instalados pero sin uso visible** en esta rama. Probable resto de otra clase o material que se va a ver después.
- **`AlojamientoService` usa errores custom sin importarlos**: tira `ValidationError`, `ConflictError`, `NotFoundError`, pero esos nombres no están importados en el archivo. Bug latente: si caés en ese camino, te tira `ReferenceError`.
- **Paginación + soft delete incompletos**: en `findAllPaginated` el ejemplo deja comentado el filtro `eliminado: false`. Si se usa baja lógica, query y contador tienen que compartir el mismo filtro.
- **`getDescripcion()` en `Alojamiento`** usa `this.categoria` pero la entidad no tiene `categoria`. Bug latente del ejemplo.
- **Repository de Reserva: `save` con upsert**: el `findOneAndUpdate(..., { upsert: true })` crea si no existe. Útil, pero hay que entender que **mezcla create y update** en una sola operación. Más cómodo para el caller, menos explícito.

### 16) Resumen mental de Clase 07

Si te preguntan "¿cómo persistís datos con MongoDB en una arquitectura por capasí":

> Uso MongoDB como BD documental NoSQL y Mongoose como ODM para definir schemas de cada entidad con validaciones declarativas. Los schemas viven en una capa propia `schemas/`; los repositories usan el `Model` exportado por el schema para CRUD; los services orquestan casos de uso (incluyendo conversión a DTO); los controllers manejan HTTP. La conexión se inicializa al arrancar el servidor con `mongoose.connect(...)` leyendo de `.env`. Para relaciones uso referencias (`ref: 'X'`) con populate cuando son many-to-many u one-to-many grandes; embebo cuando los datos van siempre juntos y tienen ciclo de vida atado. La paginación vive en el repository (`skip` + `limit`) para no traer todo a memoria. Para consultas complejas uso el aggregation pipeline. Al elegir MongoDB también considero tradeoffs de consistencia, disponibilidad, tamaño del documento y costo de consultas como `$lookup`.

Checklist para examen:

- **Persistencia** = estado que sobrevive al proceso.
- **NoSQL documental**: documentos JSON-like, schema flexible, escalabilidad horizontal.
- **Mapeos**: ORM para relacional; ODM / Document Mapping para documentales; key-value y column-family para otros modelos NoSQL.
- **ACID**: garantías de transacción. **CAP**: tradeoffs de sistemas distribuidos.
- **MongoDB**: database -> collection -> document. `_id` es `ObjectId` (12 bytes con timestamp embebido).
- **CRUD básico**: `insertOne`, `find`, `updateOne`, `deleteOne` + operadores `$gt`, `$in`, `$exists`, etc.
- **Embebidos vs referencias**: embebido para 1-a-pocos siempre juntos; referencia para muchos-a-muchos, ciclo de vida independiente o crecimiento sin límite. Recordá el límite de 16 MB por documento.
- **ODM (Mongoose)**: schema (forma) + model (clase) + document (instancia). Validaciones declarativas, middlewares, populate.
- **Nueva capa `schemas/`**: separa la forma de persistencia de la entidad de dominio.
- **Populate**: trae documentos referenciados. Se puede hacer manual (`.populate('x')`) o via middleware `pre(/^find/, ...)`.
- **Soft delete**: flag `eliminado: true` + filtrar en todas las queries. Gotcha con populate.
- **Paginación**: en el repository con `.skip()` + `.limit()` + `countDocuments()`.
- **Aggregation pipeline**: etapas `$match`, `$group`, `$lookup`, `$unwind`, `$project`. Vive en el repository.
- **Conexión**: centralizada en `config/database.js`, lee de `.env`, falla rápido (`process.exit(1)`).
- **Async/await en TODAS las capas** (controller / service / repository).
- **DTO en el service**: filtra qué datos viajan al cliente.

---




## Clase 08 - Frontend inicial: HTML, CSS, accesibilidad y DOM

Fuentes usadas:
- Fuente única por pedido explícito: `borradores/teoria/clase-08-frontend-inicial.md`

Nota de fuente:
- El archivo fuente conserva internamente el título "Clase 6 (Teoría) - Introducción al Frontend", pero en este apunte se integra como **Clase 08** porque esa es la numeración actual del repositorio.
- No se usaron PDFs, repos de código, documentación externa ni links adicionales. Esta clase se nutre solamente de esa toma de apuntes.

### Idea central de la clase

Esta clase baja a tierra la base del frontend sin frameworks: qué corre en el navegador, qué responsabilidad tiene cada lenguaje y cómo se construye una página que no sea solo "algo que se ve", sino una interfaz usable, semántica, accesible y mantenible.

La idea importante es esta:

> El frontend vive en el navegador del usuario y se apoya en tres piezas nativas: **HTML** para estructura, **CSS** para presentación y **JavaScript** para comportamiento.

Antes de React, hooks, routers o librerías de UI, hay que entender esto. Si no entendés HTML, CSS, DOM y eventos, cualquier framework termina pareciendo magia. Y NO queremos magia: queremos saber qué está pasando.

### 1) Qué es el frontend

El **frontend** es la parte de una aplicación web con la que el usuario interactúa directamente desde el navegador. Es lo que se renderiza en pantalla y lo que reacciona a clicks, teclas, scroll, formularios y otros eventos.

Modelo mental:

```txt
+---------------------------------+
| Frontend  (browser usuario)     | HTML + CSS + JS
+---------------------------------+
| Backend   (servidor)            | Node/Express, Java, etc.
+---------------------------------+
| Persistencia (BD)               | MongoDB, Postgres, etc.
+---------------------------------+
```

Un punto clave: el frontend **no es confiable para reglas críticas**. El usuario puede abrir DevTools, modificar HTML, ejecutar JavaScript propio o cambiar requests. Por eso:

- el frontend puede validar para mejorar experiencia;
- el backend valida para garantizar reglas de negocio;
- la persistencia guarda el estado confiable del sistema.

Ejemplo: mostrar "el precio debe ser mayor a cero" en el formulario está buenísimo para UX. Pero si el backend acepta precio negativo, el sistema está mal igual.

El navegador entiende tres lenguajes nativos:

| Lenguaje | Responsabilidad | Pregunta que responde |
|---|---|---|
| HTML | estructura y contenido | qué cosas hay |
| CSS | presentación visual | cómo se ven |
| JavaScript | comportamiento | qué pasa cuando el usuario interactúa |

Separarlos bien no es capricho. Es una forma de mantener el código entendible.

### 2) UI vs UX

UI y UX estan relacionadas, pero no significan lo mismo.

| | UI (User Interface) | UX (User Experience) |
|---|---|---|
| Qué es | La parte visual y de interacción | La experiencia general del usuario |
| Pregunta central | Cómo se ve | Cómo se siente usarlo |
| Incluye | Botones, colores, tipografía, layout, íconos | Flujos, claridad, eficiencia, satisfacción |
| Se evalúa con | consistencia, contraste, jerarquía visual | tiempo para completar táreas, errores, frustracion |

Ejemplo simple:

- Una app puede tener una **UI hermosa** pero mala UX si para hacer login te hace pasar por cinco pantallas.
- Un cajero automático viejo puede tener una UI fea, pero buena UX si en pocos pasos te deja hacer lo que necesitás.

Resumen mental:

```txt
UI = cómo se ve.
UX = cómo se usa y cómo se siente.
```

Una buena UI puede mejorar la UX, pero no la garantiza. Una mala UX arruina incluso una UI visualmente linda.

### 3) HTML: estructura y significado

**HTML** significa *HyperText Markup Language*. Es un lenguaje de marcado: sirve para describir la estructura de una página.

No es un lenguaje de programación: no tiene variables, condicionales ni loops. Su trabajo es etiquetar contenido para que el navegador, los lectores de pantalla y los motores de búsqueda entiendan que representa cada cosa.

#### 3.1 Anatomía de un tag

Ejemplo:

```html
<a href="https://utn.edu.ar" target="_blank">Ir a UTN</a>
```

Partes:

| Parte | Ejemplo | Para qué sirve |
|---|---|---|
| Tag de apertura | `<a>` | inicia el elemento |
| Atributos | `href`, `target` | configuran comportamiento o metadata |
| Contenido | `Ir a UTN` | lo que aparece dentro del elemento |
| Tag de cierre | `</a>` | marca dónde termina |

Algunos tags son **void** o autocerrados: no tienen contenido ni cierre. Ejemplos:

```html
<img>
<br>
<input>
<hr>
<meta>
<link>
```

Estructura mínima de HTML5:

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi página</title>
  </head>
  <body>
    <h1>Hola mundo</h1>
  </body>
</html>
```

Puntos importantes:

- `<!DOCTYPE html>` indica que el documento usa HTML5.
- `<html lang="es">` define la raíz y el idioma del documento.
- `<head>` contiene metadata: título, charset, viewport, links a CSS.
- `<body>` contiene lo que se renderiza en pantalla.

#### 3.2 HTML semántico vs no semántico

HTML **no semántico** es usar tags genéricos para todo:

```html
<div class="cabecera">
  <div class="logo">Mi sitio</div>
  <div class="menu">
    <div class="item">Inicio</div>
    <div class="item">Productos</div>
  </div>
</div>
<div class="contenido">
  <div class="articulo">
    <div class="título">Mi post</div>
    <div class="texto">Lorem ipsum...</div>
  </div>
</div>
<div class="pie">2026 - UTN</div>
```

Visualmente puede funcionar, pero semánticamente dice muy poco.

HTML **semántico** usa tags que describen el rol del contenido:

```html
<header>
  <h1>Mi sitio</h1>
  <nav>
    <ul>
      <li><a href="/">Inicio</a></li>
      <li><a href="/productos">Productos</a></li>
    </ul>
  </nav>
</header>
<main>
  <article>
    <h2>Mi post</h2>
    <p>Lorem ipsum...</p>
  </article>
</main>
<footer>2026 - UTN</footer>
```

Esto no solo ayuda a humanos que leen el código. También ayuda al navegador, lectores de pantalla, buscadores y motores generativos.

Tags semánticos clave:

| Tag | Para qué sirve |
|---|---|
| `<header>` | Encabezado de la página o de una sección |
| `<nav>` | Bloque de navegación |
| `<main>` | Contenido principal único de la página |
| `<section>` | Seccion temática |
| `<article>` | Contenido autocontenido |
| `<asíde>` | Contenido secundario o relacionado |
| `<footer>` | Pie de página o de sección |
| `<h1>` ... `<h6>` | Jerarquia de títulos |
| `<figure>` / `<figcaption>` | Imagen y descripción |
| `<time>` | Fecha u hora con valor legible por máquina |

> Regla pragmatica: si existe un tag semántico para lo que estas haciendo, usalo. `<div>` y `<span>` son última opción, no primera opción.

#### 3.3 SEO y GEO

**SEO** (*Search Engine Optimization*) busca que una página aparezca mejor posicionada en buscadores tradicionales.

Buenas prácticas básicas:

- un solo `<h1>` por página;
- jerarquía coherente de títulos (`h1 -> h2 -> h3`);
- `<meta name="description">` con resumen del contenido;
- `<title>` descriptivo y único;
- URLs legibles;
- `alt` en imágenes;
- HTML semántico.

**GEO** (*Generative Engine Optimization*) apunta a motores generativos y LLMs. La idea es que el contenido este suficientemente claro, estructurado y verificable como para ser entendido y citado por sistemás generativos.

Diferencia mental:

| | SEO | GEO |
|---|---|---|
| Audiencia | buscadores tradicionales | LLMs / motores generativos |
| Optimiza | ranking | probabilidad de ser citado o entendido |
| Ayuda | keywords, backlinks, velocidad | claridad, estructura, datos concretos, fuentes |

No hace falta memorizar la sigla como si fuera una tecnología. Lo importante es entender que la estructura del contenido importa cada vez más.

#### 3.4 Errores típicos de HTML

- Usar `<div>` para todo.
- Saltarse niveles de heading: pasar de `<h1>` a `<h4>` sin estructura.
- Olvidarse el `alt` en imágenes.
- Usar `<br>` para generar espacio visual.
- Anidar mal elementos, por ejemplo `<p><div>...</div></p>`.

### 4) Accesibilidad: que la web pueda ser usada por más personas

**Accesibilidad** es hacer que los productos digitales sean utilizables por todas las personas, incluidas personas con discapacidades visuales, auditivas, motoras o cognitivas.

La abreviatura **a11y** aparece porque entre la `a` y la `y` de *accessibility* hay 11 letras.

#### 4.1 Por qué importa

La accesibilidad no es un adorno. Importa por varios motivos:

- hay usuarios reales con necesidades distintas;
- muchas mejoras accesibles benefician a todos;
- lectores de pantalla, crawlers y motores generativos interpretan mejor HTML semántico;
- evita interfaces que solo funcionan en condiciones ideales.

Ejemplos:

- Una persona con baja visión necesita buen contraste.
- Una persona con una lesión temporal puede depender del teclado.
- Alguien usando el celular bajo el sol también se beneficia de contraste y claridad.
- Un lector de pantalla necesita que el HTML tenga estructura real.

#### 4.2 WCAG

**WCAG** significa *Web Content Accessibility Guidelines*. Define niveles de accesibilidad:

- **A**: mínimo.
- **AA**: objetivo recomendado.
- **AAA**: maximo.

Se organiza en cuatro principios:

| Principio | Idea |
|---|---|
| Perceptible | la información debe poder percibirse |
| Operable | la interfaz debe poder operarse |
| Comprensible | contenido y operación deben ser entendibles |
| Robusto | debe funcionar con tecnologías asístivas presentes y futuras |

Ejemplos concretos:

- Perceptible: texto alternativo en imágenes.
- Operable: poder navegar con teclado.
- Comprensible: errores claros en formularios.
- Robusto: HTML válido y ARIA cuando corresponde.

#### 4.3 Tipos de barreras

| Tipo | Barreras posibles | Como ayuda el frontend |
|---|---|---|
| Visual | ceguera, baja visión, daltonismo | lectores de pantalla, contraste, no depender solo del color |
| Auditiva | sordera, hipoacusia | subtítulos, transcripciones |
| Motora | Parkinson, parálisis, lesiónes | navegación por teclado, áreas grandes de click |
| Cognitiva | dislexia, TDAH, dificultad de comprensión | lenguaje claro, layouts predecibles |

#### 4.4 Lectores de pantalla

Un lector de pantalla lee en voz alta lo que aparece en pantalla. Interpreta el HTML y anuncia estructura: encabezados, listas, botónes, regiónes y navegación.

Si usas HTML semántico, el lector tiene información para comunicar. Si todo es `<div>`, el lector pierde contexto.

Ejemplo mental:

```txt
<header> -> región de encabezado
<nav>    -> navegación
<main>   -> contenido principal
<h1>     -> encabezado nivel 1
<button> -> botón
```

Por eso la semántica no es estetica. Es comportamiento real para ciertas herramientas.

#### 4.5 ARIA

**ARIA** (*Accessible Rich Internet Applications*) agrega semántica de accesibilidad cuando HTML no alcanza.

Ejemplos:

| Atributo | Para qué sirve |
|---|---|
| `aria-label="..."` | etiqueta accesible cuando no hay texto visible |
| `aria-labelledby="id"` | usa otro elemento como label |
| `aria-describedby="id"` | agrega descripción adicional |
| `aria-hidden="true"` | oculta un elemento a lectores de pantalla |
| `aria-live="polite"` | anuncia cambios dinámicos |
| `role="..."` | define rol semántico |

Ejemplo: botón solo con ícono.

```html
<!-- Mal: el lector solo puede anunciar "botón" -->
<button>
  <svg>...</svg>
</button>

<!-- Mejor: el lector anuncia "botón, cerrar" -->
<button aria-label="Cerrar">
  <svg aria-hidden="true">...</svg>
</button>
```

Ejemplo de notificación dinámica:

```html
<div aria-live="polite" id="status"></div>

<script>
  document.getElementById("status").textContent = "Turno reservado correctamente"
</script>
```

> Primera regla de ARIA: si existe un tag HTML nativo que ya hace lo que necesitás, usa el tag nativo. ARIA no es para reemplazar HTML semántico: es para completar casos donde HTML no alcanza.

#### 4.6 Checklist mínima de accesibilidad

- Todas las imágenes con `alt` (`alt=""` si son decorativas).
- Contraste suficiente entre texto y fondo.
- Navegacion posible por teclado.
- Foco visible.
- Formularios con `<label>` asociado a cada `<input>`.
- No depender solo del color para transmitir información.
- Idioma declarado con `<html lang="es">`.

### 5) CSS: presentación, cascada y layout

**CSS** (*Cascading Style Sheets*) define cómo se ven los elementos HTML: colores, tamaños, espaciado, layout y animaciones.

#### 5.1 Anatomía de una regla CSS

```css
selector {
  propiedad: valor;
  propiedad: valor;
}
```

Ejemplo:

```css
button.primario {
  background-color: #2563eb;
  color: white;
  padding: 8px 16px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
}
```

Partes:

| Parte | Ejemplo | Significado |
|---|---|---|
| Selector | `button.primario` | que elementos afecta |
| Bloque | `{ ... }` | conjunto de declaraciones |
| Declaración | `color: white;` | propiedad + valor |

Tres formás de incluir CSS:

```html
<!-- Externa: la más usada y recomendada -->
<link rel="stylesheet" href="estilos.css">

<!-- Interna: dentro del head -->
<style>
  body { background: white; }
</style>

<!-- Inline: la menos recomendada -->
<p style="color: red;">Hola</p>
```

Regla práctica: preferí CSS externo. El inline style sirve para casos puntuales, pero si lo usas como costumbre destruís mantenibilidad.

#### 5.2 Selectores

| Selector | Sintaxis | Qué matchea |
|---|---|---|
| Universal | `*` | todos los elementos |
| De tipo | `p`, `h1`, `button` | todos los elementos de ese tag |
| De clase | `.btn`, `.card` | elementos con esa clase |
| De ID | `#header` | elemento con ese id |
| De atributo | `[type="text"]` | elementos por atributo |
| Pseudo-clase | `:hover`, `:focus` | estados del elemento |
| Pseudo-elemento | `::before`, `::after` | partes del elemento |

Combinadores:

| Combinador | Ejemplo | Qué matchea |
|---|---|---|
| Descendiente | `nav a` | cualquier `<a>` dentro de `<nav>` |
| Hijo directo | `nav > a` | `<a>` hijo directo de `<nav>` |
| Hermano adyacente | `h1 + p` | primer `<p>` después de un `<h1>` |
| Hermano general | `h1 ~ p` | todos los `<p>` después de un `<h1>` |

#### 5.3 Especificidad

La regla "ID gana a clase, clase gana a tag" sirve como intuición, pero es incompleta. CSS calcula especificidad con una tupla:

```txt
(a, b, c, d)
```

| Posición | Qué cuenta | Ejemplo |
|---|---|---|
| `a` | estilos inline | `style="color: red"` |
| `b` | cantidad de IDs | `#principal` |
| `c` | clases, atributos y pseudo-clases | `.btn:hover` |
| `d` | tipos y pseudo-elementos | `div p::before` |

Ejemplo:

```css
p { color: blue; }            /* (0,0,0,1) */
.texto { color: green; }      /* (0,0,1,0) */
#principal { color: red; }    /* (0,1,0,0) */
```

```html
<p id="principal" class="texto">Hola</p>
<!-- Color: rojo. ID gana. -->
```

Con inline style:

```html
<p id="principal" class="texto" style="color: orange">Hola</p>
<!-- Color: naranja. Inline gana. -->
```

Con `!important`:

```css
.texto { color: green !important; }
#principal { color: red; }
```

```html
<p id="principal" class="texto">Hola</p>
<!-- Color: verde. !important rompe la jerarquía normal. -->
```

> `!important` es un olor a código. Puede servir para overrides puntuales, pero si lo usas para ganarle a tu propio CSS, estas perdiendo control del diseño.

Si hay empate de especificidad, gana la regla que aparece después en el archivo. Esa es la "C" de *cascading*.

#### 5.4 Box model

Cada elemento HTML es una caja rectangular con capas:

```txt
+-----------------------------+
|          margin             |  espacio entre cajas
|  +-----------------------+  |
|  |       border          |  |  borde
|  |  +-----------------+  |  |
|  |  |     padding     |  |  |  espacio interno
|  |  |  +-----------+  |  |  |
|  |  |  |  content  |  |  |  |  contenido
|  |  |  +-----------+  |  |  |
|  |  +-----------------+  |  |
|  +-----------------------+  |
+-----------------------------+
```

Ejemplo:

```css
.caja {
  width: 200px;
  height: 100px;
  padding: 16px;
  border: 2px solid black;
  margin: 8px;
}
```

Trampa clásica: por defecto (`box-sizing: content-box`), el `width` mide solo el contenido.

```txt
ancho real = width + padding-left + padding-right + border-left + border-right
           = 200 + 16 + 16 + 2 + 2 = 236px
```

Buena práctica:

```css
*, *::before, *::after {
  box-sizing: border-box;
}
```

Con `border-box`, el ancho declarado incluye contenido, padding y borde. La matemática se vuelve mucho más intuitiva.

#### 5.5 Display y position

`display` define cómo se comporta una caja dentro del flujo del documento.

| Valor | Comportamiento |
|---|---|
| `block` | ocupa todo el ancho disponible y va en línea propia |
| `inline` | ocupa solo lo necesario y no rompe línea |
| `inline-block` | como inline, pero permite `width` y `height` |
| `none` | no se renderiza ni ocupa espacio |
| `flex` | activa Flexbox para los hijos |
| `grid` | activa Grid para los hijos |

`position` controla cómo se ubica un elemento respecto del flujo.

| Valor | Comportamiento |
|---|---|
| `static` | valor por defecto; sigue el flujo normal |
| `relative` | sigue el flujo, pero puede desplazarse |
| `absolute` | sale del flujo y se posiciona respecto a un ancestro posicionado |
| `fixed` | sale del flujo y se posiciona respecto a la viewport |
| `sticky` | se comporta como relative hasta cierto scroll y luego se pega |

Para esta altura no hace falta memorizar todo. Lo importante es entender:

- `block` vs `inline` explica muchos comportamientos raros iniciales;
- `flex` y `grid` se usan para layouts reales;
- `position: absolute` y `fixed` sacan elementos del flujo, así que hay que usarlos con criterio.

#### 5.6 Errores típicos de CSS

- Pelearse con `width` sin entender `box-sizing`.
- Abusar de `!important`.
- Crear selectores demásiado especificos.
- Usar IDs para estilos cuando una clase sería mejor.
- Meter estilos inline por costumbre.

### 6) JavaScript en el navegador y DOM

JavaScript agrega comportamiento a la página. En el navegador, su trabajo principal es manipular el DOM y reaccionar a eventos del usuario.

#### 6.1 Qué es el DOM

**DOM** significa *Document Object Model*. Es la representación en memoria del HTML que el navegador arma cuando carga la página.

HTML:

```html
<html>
  <body>
    <h1>Hola</h1>
    <p>Mundo</p>
  </body>
</html>
```

DOM mental:

```txt
document
  \-- html
      \-- body
          |-- h1 -> "Hola"
          \-- p  -> "Mundo"
```

Puntos clave:

- El DOM lo genera el navegador al parsear el HTML.
- JavaScript accede al DOM usando `document`.
- Modificar el DOM modifica lo que se ve en pantalla.
- Si el JS rompe el DOM o falla en eventos, la página puede quedar visualmente presente pero funcionalmente rota.

#### 6.2 Acceder a elementos

```js
// Por ID: devuelve un elemento o null
const título = document.getElementById("título")

// Por selector CSS: devuelve el primer match o null
const primerBoton = document.querySelector("button.primario")

// Por selector CSS: devuelve todos los matches
const todosLosBotones = document.querySelectorAll("button")

// Por clase: devuelve HTMLCollection viva
const elementosCard = document.getElementsByClassName("card")

// Por tag: devuelve HTMLCollection viva
const todosLosP = document.getElementsByTagName("p")
```

Diferencia importante:

- `querySelectorAll` devuelve una **NodeList estática**.
- `getElementsByClassName` devuelve una **HTMLCollection viva**, que se actualiza si el DOM cambia.

Para la mayoría de los casos iniciales, `querySelector` y `querySelectorAll` son lo más práctico.

#### 6.3 Modificar contenido, atributos y clases

```js
const título = document.querySelector("h1")

// Cambiar texto
título.textContent = "Hola UTN"        // texto plano
título.innerHTML = "<em>Hola UTN</em>" // interpreta HTML

// Cambiar atributos
título.setAttribute("data-id", "42")
título.id = "título-principal"

// Cambiar clases
título.classList.add("destacado")
título.classList.remove("oculto")
título.classList.toggle("activo")
título.classList.contains("destacado")

// Cambiar estilos inline
título.style.color = "red"
título.style.fontSize = "24px"
```

Gotcha de seguridad:

> No uses `innerHTML` con datos del usuario sin sanitizar. Es una puerta de entrada a XSS (*Cross-Site Scripting*). Para texto del usuario, preferí `textContent`.

#### 6.4 Crear y eliminar elementos

```js
// Crear
const nuevo = document.createElement("li")
nuevo.textContent = "Nuevo item"
nuevo.classList.add("item")

// Insertar
const lista = document.querySelector("ul")
lista.append(nuevo)
lista.prepend(nuevo)
lista.insertBefore(nuevo, lista.firstChild)

// Eliminar
nuevo.remove()
lista.removeChild(nuevo)
```

Acá aparece un patrón clave: el DOM no es solo lectura. JavaScript puede crear, insertar, mover y eliminar nodos.

#### 6.5 Eventos

Los eventos son el centro del frontend interactivo. Cada click, tecla, scroll, submit o carga dispara un evento que JavaScript puede escuchar.

```js
const botón = document.querySelector("#guardar")

botón.addEventListener("click", (event) => {
  console.log("Boton clickeado")
  console.log(event.target)
  event.preventDefault()
})
```

Eventos comunes:

| Evento | Cuando se dispara |
|---|---|
| `click` | click del mouse |
| `dblclick` | doble click |
| `mouseenter` / `mouseleave` | cuando el mouse entra o sale |
| `keydown` / `keyup` | tecla presionada o soltada |
| `input` | cambia el valor de un input |
| `change` | cambia el valor y se confirma al perder foco |
| `submit` | envío de un formulario |
| `load` | la página o recurso terminó de cargar |
| `DOMContentLoaded` | el HTML se parseó sin esperar imágenes/CSS |

Patron tipico de formulario:

```html
<form id="form-turno">
  <input type="text" name="paciente" required>
  <button type="submit">Reservar</button>
</form>
```

```js
const form = document.querySelector("#form-turno")

form.addEventListener("submit", (event) => {
  event.preventDefault()
  const formData = new FormData(form)
  const paciente = formData.get("paciente")
  console.log("Reservando turno para:", paciente)
})
```

`event.preventDefault()` es fundamental en formularios cuando no querés que el navegador haga el submit tradicional y recargue la página.

#### 6.6 Errores típicos de JavaScript en el navegador

- Buscar elementos antes de que exista el DOM.
- Poner scripts en `<head>` sin `defer` y esperar que el HTML ya exista.
- Olvidarse `event.preventDefault()` en formularios.
- Usar `innerHTML` con input del usuario.
- Usar `var` en vez de `const` / `let`.
- Comparar con `==` en vez de `===`.

### 7) Resumen mental de Clase 08

Si te preguntan "qué es el frontend":

> El frontend es la parte de la aplicación qué corre en el navegador del usuario. Se construye con HTML para estructura, CSS para presentación y JavaScript para comportamiento. HTML semántico y accesibilidad no son detalles decorativos: permiten que la página sea entendible para usuarios, lectores de pantalla, buscadores y motores generativos. CSS controla cómo se ve y se distribuye la interfaz; JavaScript manipula el DOM y responde a eventos para volver la página interactiva.

Checklist para examen:

- **Frontend**: corre en el navegador; no es confiable para reglas críticas.
- **HTML**: estructura del contenido; no es lenguaje de programación.
- **CSS**: presentación visual, layout, cascada y especificidad.
- **JavaScript**: comportamiento, DOM y eventos.
- **UI vs UX**: cómo se ve vs cómo se usa/se siente.
- **HTML semántico**: mejora accesibilidad, SEO, GEO y mantenibilidad.
- **SEO / GEO**: estructura clara para buscadores y motores generativos.
- **a11y**: accesibilidad; WCAG se organiza en perceptible, operable, comprensible y robusto.
- **ARIA**: usar solo cuando HTML nativo no alcanza.
- **CSS especificidad**: inline, IDs, clases/atributos/pseudo-clases, tipos/pseudo-elementos.
- **Box model**: content + padding + border + margin; preferír `box-sizing: border-box`.
- **DOM**: árbol en memoria generado por el navegador.
- **Eventos**: `addEventListener` conecta interacción del usuario con comportamiento JS.
- **Seguridad**: cuidado con `innerHTML`; para texto de usuario, usar `textContent`.

---


## Clase 09 - Fundamentos de React y Routing

Fuentes usadas:
- Práctica: `Clases_Practica/Clase Práctica - 09 - Fundamentos de React.pdf`
- Cache práctica: `_cache_pdf_text/Clase_Practica_09_Fundamentos_de_React.txt`
- Teoría frontend intermedio: `borradores/teoria/clase-09-frontend-intermedio.md`
- Teoría UI/cache: `_cache_pdf_text/clase-09-teoria-ui.md`

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase9-front-react-pt1
- Subproyecto: `client/`

Links recomendados por la cátedra:
- React Router DOM: https://reactrouter.com/home
- React Icons: https://react-icons.github.io/react-icons/

Nota de fuente:
- El cache `clase-09-teoria-ui.md` conserva internamente el título "Clase 10 - UI", pero se usa acá porque fue indicado como fuente teórica para esta mejora de Clase 09.

Idea central de la clase:
> React permite construir interfaces declarativas basadas en componentes. En una SPA(single page application), el browser carga una app JavaScript y React se encarga de renderizar y actualizar la UI en el cliente.

Esto es importante: **React no es "HTML con cosas raras"**. React es una forma de organizar UI como funciones, estado, props y composición. Si entendés eso, el código deja de parecer magia.

---

### 0) Cómo leer esta clase: del arranque a la interacción

La Clase 09 tenía muchos conceptos nuevos juntos. Es por eso que conviene leerla con este recorrido:

```txt
crear/arrancar app
  -> entender dónde React se monta
  -> entender componentes y JSX
  -> pasar datos con props
  -> cambiar UI con state
  -> renderizar listas/eventos
  -> navegar con React Router
```

Ese orden importa. Si arrancás por Router sin entender componentes, estás poniendo ventanas antes de levantar las paredes. Primero la estructura, después la navegación.

#### De cero a una React app con Create React App

El repo de la clase está armado con Create React App (`react-scripts`). Ojo profesional: **Create React App está deprecado para proyectos nuevos**, pero sirve para entender esta base porque el repo de la materia lo usa.

Paso a paso mínimo si arrancaras sin nada instalado:

1. Instalar **Node.js LTS** desde https://nodejs.org/.
2. Verificar que quedaron disponibles Node y npm:

```bash
node -v
npm -v
```

3. Crear la app:

```bash
npx create-react-app@latest megasuper-client
```

4. Entrar al proyecto:

```bash
cd megasuper-client
```

5. Levantar servidor de desarrollo:

```bash
npm start
```

CRA genera una estructura con `public/`, `src/`, `package.json`, scripts y configuración oculta de bundling. La idea didáctica es que puedas escribir React sin configurar Babel/Webpack a mano.

En esta materia NO confundas esto con arquitectura final de producción. Para aprender está bien; para proyectos nuevos hoy conviene evaluar alternativas modernas como Vite o frameworks recomendados por React.

---

### 1) SSR vs CSR: dónde se genera la vista

El PDF compara dos formas de construir la vista que ve el usuario.

#### SSR - Server Side Rendering

La vista se genera principalmente en el **servidor**.

```txt
Browser pide /productos
  -> servidor arma HTML
  -> browser recibe HTML ya renderizado
```

Características:

- stream principal: HTML;
- carga inicial rápida porque el HTML ya viene armado;
- más procesamiento del lado servidor;
- menor dependencia de JavaScript para ver algo inicial.

#### CSR - Client Side Rendering

La vista se genera principalmente en el **cliente**.

```txt
Browser pide la app
  -> servidor entrega HTML casí vacío + JS
  -> browser descarga JS
  -> React renderiza la UI en #root
```

Características:

- stream principal: JSON/datos + JavaScript;
- más procesamiento del lado cliente;
- interacciónes más fluidas una vez cargada la app;
- si el JS no carga, no hay UI real.

#### Ejemplo real del repo: Create React App como CSR

En `client/public/index.html`, la página trae un contenedor vacío:

```html
<div id="root"></div>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/public/index.html

Y en `client/src/index.js`, React monta la aplicación en ese `root`:

```js
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <BrowserRouter>
      <App />
    </BrowserRouter>
  </React.StrictMode>
);
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/index.js

Traducción conceptual:

```txt
index.html aporta el punto de montaje
index.js arranca React
App.jsx define que pantalla renderizar
```

#### Para examen

> En CSR, el servidor no entrega cada pantalla ya renderizada; entrega una app JavaScript que corre en el navegador. React monta esa app sobre un nodo del DOM, normalmente `#root`.

---

### 2) Patrones y arquitecturas de UI: por qué React piensa así

Las fuentes teóricas agregan una capa conceptual que conviene ubicar antes de entrar al DOM y al Virtual DOM: React no aparece de la nada. Aparece como respuesta a un problema clásico de UI: **mantener sincronizados datos, interacciones y vista sin que el código se vuelva una telaraña**.

#### Componentización y patrones

Componentizar significa partir una interfaz en piezas más chicas y reutilizables.

Ganamos:

- **reutilización**: el mismo componente puede aparecer en varias pantallas;
- **parametrización**: el componente cambia según props;
- **legibilidad**: cada archivo tiene una responsabilidad más clara.

Un patrón de UI no es código copiado. Es una guía reutilizable para resolver un problema frecuente: un login, un formulario, un carrito, una barra de navegación, una card de producto.

En el repo se ve así:

```txt
Home = ProductSearchBar + ProductCarousel
ProductCarousel = lista de CarouselItem
Layout = Header + Navbar + Outlet
```

Eso es componentización aplicada, no solo carpetas lindas.

#### MVC, MVVM y Flux: tres formas de ordenar UI

| Arquitectura | Idea | Problema que intenta ordenar |
|---|---|---|
| MVC | Model, View, Controller | separar datos, interfaz y coordinación |
| MVVM | Model, View, ViewModel | preparar datos para la vista mediante binding |
| Flux | Action -> Dispatcher -> Store -> View | flujo de datos unidireccional |

La idea importante para React es **Flux**: los datos no deberían moverse de cualquier manera por la app. Conviene que haya una dirección clara.

```txt
View -> Action -> Dispatcher/actualización -> Store/State -> View
```

No hace falta implementar Flux en esta clase, pero sí entender el espíritu: si el estado cambia, la vista se actualiza; no deberíamos tener diez lugares modificando el DOM a mano.

En React esto se traduce en una regla muy concreta:

> Los datos bajan por props; los eventos suben como callbacks; el cambio de state dispara re-render.

#### Reactividad y ciclo de vida

**Reactividad** significa que cuando cambian el `state` o las `props`, React vuelve a renderizar el componente para reflejar el nuevo estado de la UI.

Ciclo mental de un componente:

| Momento | Qué pasa |
|---|---|
| Mount | primer renderizado; el componente aparece en el DOM |
| Update | cambian state o props; React re-renderiza |
| Unmount | el componente se elimina del DOM |

En Clase 09 alcanza con entender el concepto. En Clase 10, esto se conecta fuerte con `useEffect` y otros hooks.

---

### 3) DOM: la página como árbol

El PDF define el DOM como una representación estructurada de un documento HTML/XML en forma de árbol.

Ejemplo mental:

```txt
html
`-- body
    `-- div#root
        `-- App
            `-- Layout
                |-- Header
                |-- Navbar
                `-- Home / ProductDetailPage
```

El navegador usa el DOM real para pintar y actualizar la pantalla.

#### ¿Dónde aparece en el repo?

El DOM real arranca con:

```html
<div id="root"></div>
```

Después React renderiza componentes adentro.

Ejemplo:

```jsx
function App() {
  return (
    <Routes>
      <Route path="/" element={<Layout />}>
        <Route index element={<Home />} />
        <Route path="/productos/:id" element={<ProductDetailPage />} />
      </Route>
    </Routes>
  );
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/App.jsx

#### Idea clave

React no elimina el DOM. React te da una capa declarativa para describir **cómo debería verse** la UI, y después sincroniza eso con el DOM real.

---

### 4) Virtual DOM y reconciliación

#### Concepto

El Virtual DOM es una representación liviana, en memoria, de la UI.

Cuando cambia algo en la aplicación:

1. React genera una nueva representación virtual de la UI.
2. Compara esa representación con la anterior (**diff/reconciliación**).
3. Aplica al DOM real solo los cambios necesarios.

```txt
Estado anterior -> render virtual anterior
Estado nuevo    -> render virtual nuevo
React compara   -> detecta diferencias
DOM real        -> actualiza lo necesario
```

#### Ejemplo real del repo: carrusel con estado

En `ProductCarousel.jsx`:

```js
const [index, setIndex] = useState(0);
```

Cuando el usuario toca avanzar:

```js
const avanzar = () => {
  if (puedeAvanzar) setIndex(index + 1);
};
```

Ese cambio de estado recalcula:

```js
const desplazamiento = `translateX(-${index * (100 / VISIBLES)}%)`;
```

Y se aplica en JSX:

```jsx
<div className="carousel-track" style={{ transform: desplazamiento }}>
  {productos.map((producto) => (
    <CarouselItem producto={producto} key={producto.id} />
  ))}
</div>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productCarousel/ProductCarousel.jsx

Lectura:

```txt
click -> setIndex -> re-render -> nuevo transform -> React actualiza el DOM
```

No estás manipulando manualmente el DOM con `document.querySelector(...).style.transform = ...`. Estás declarando que el `transform` depende del estado `index`. BIEN. Eso es React.

---

### 5) React: biblioteca declarativa y basada en componentes

El PDF dice que React es una biblioteca de JavaScript para construir interfaces de usuario declarativas y basadas en componentes.

#### Imperativo vs declarativo

Imperativo:

```js
const título = document.createElement('h1')
título.textContent = 'Megasuper'
document.body.appendChild(título)
```

Declarativo con React:

```jsx
const Titulo = () => <h1>Megasuper</h1>
```

En React describís **que querés ver**, no cada paso manual para construirlo.

#### Ejemplo real del repo

`Home.jsx` compone una pantalla con componentes:

```jsx
const Home = () => {
  return (
    <>
      <div className="home-body">
        <ProductSearchBar />
      </div>
      <div>
        <ProductCarousel />
      </div>
    </>
  );
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/features/home/Home.jsx

Traducción:

```txt
Home = SearchBar + ProductCarousel
```

Eso es composición. Como arquitectura: no construís una casa pegando todo en una sola pared; separás ambientes, instalaciones y estructura. Acá igual, pero con UI.

---

### 6) Componentes: unidad básica de UI

Un componente es una pieza de interfaz con su propia lógica y apariencia.

Puede ser chico:

```jsx
const Header = (props) => {
  return (
    <header className="header">
      Hola {props.username}, aprovecha 3 y 6 cuotas sin interes en toda tu compra!
    </header>
  );
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/headers/Header.jsx

O puede representar una pantalla:

```jsx
const ProductDetailPage = () => {
  // busca producto y renderiza detalle
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/features/products/ProductDetailPage.jsx

#### Organización del repo

El proyecto separa:

```txt
client/src/components/   -> piezas reutilizables de UI
client/src/features/     -> pantallas o funcionalidades completas
client/src/mockdata/     -> datos mockeados
```

Ejemplos:

- `components/headers/Header.jsx`
- `components/productCarousel/ProductCarousel.jsx`
- `features/home/Home.jsx`
- `features/products/ProductDetailPage.jsx`

#### Para examen

> Un componente en React es una función de JavaScript que devuelve JSX. Permite encapsular estructura, estilos y comportamiento de una parte de la interfaz, y después reutilizarla o componerla con otros componentes.

---

### 7) Técnicas de reutilización: composición, utils y HOC

La teoría UI menciona tres formas de reutilizar que conviene distinguir:

| Técnica | Qué reutiliza | Ejemplo mental |
|---|---|---|
| Utils | funciones puras JS, sin JSX | formatear precio, parsear datos, calcular totales |
| Composición/nesting | componentes dentro de otros componentes | `Home` usa `ProductSearchBar` y `ProductCarousel` |
| HOC | función que recibe un componente y devuelve otro mejorado | envolver una pantalla con un header común |

#### Utils

Una función utilitaria vive fuera de la UI. No devuelve JSX: transforma datos.

```js
function formatearPrecio(precio) {
  return precio.toLocaleString("es-AR")
}
```

#### Composición

Es lo que más aparece en el repo:

```jsx
const Home = () => {
  return (
    <>
      <ProductSearchBar />
      <ProductCarousel />
    </>
  )
}
```

La UI se arma encastrando componentes, no escribiendo una pantalla gigante.

#### HOC - Higher Order Component

Un HOC es una función que recibe un componente y devuelve otro componente con comportamiento o estructura agregada.

```jsx
function withHeader(Component) {
  return function ComponentWithHeader() {
    return (
      <>
        <header>Mi Tienda Online</header>
        <Component />
      </>
    )
  }
}
```

No es el foco práctico del repo, pero sirve para entender que React no solo reutiliza HTML: reutiliza **formas de construir UI**.

---

### 8) JSX: JavaScript + markup

JSX parece HTML, pero vive dentro de JavaScript.

Ejemplo real:

```jsx
<Link to={`/productos/${producto.id}`} className="ver-detalles-btn">
  Ver Detalles
</Link>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productItem/CarouselItem.jsx

Cosas importantes:

- Para clases CSS se usa `className`, no `class`.
- Para insertar valores JS se usan `{}`.
- Los componentes se escriben con mayúscula: `<ProductCarousel />`.
- Los tags deben cerrarse: `<ProductSearchBar />`.
- Los estilos inline reciben un objeto JS:

```jsx
<div style={{ transform: desplazamiento }}>
```

#### Error típico

Querer escribir esto:

```jsx
<div class="card"></div>
```

En React corresponde:

```jsx
<div className="card"></div>
```

---

### 9) Props: datos que bajan de padre a hijo

Las **props** son valores que un componente padre le pasa a un componente hijo.

#### Ejemplo real: `Layout` le pasa username a `Header`

```jsx
const Layout = () => {
  return (
    <>
      <Header username="Alumno/a de DDSO"></Header>
      <Navbar></Navbar>
      <Outlet />
    </>
  );
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/features/layout/Layout.jsx

`Header` lo recibe:

```jsx
const Header = (props) => {
  return (
    <header className="header">
      Hola {props.username}, aprovecha 3 y 6 cuotas sin interes en toda tu compra!
    </header>
  );
};
```

Otra forma equivalente, mas limpia:

```jsx
const Header = ({ username }) => {
  return <header>Hola {username}!</header>
}
```

#### Ejemplo real: producto hacia item

```jsx
{productos.map((producto) => (
  <CarouselItem producto={producto} key={producto.id} />
))}
```

Y `CarouselItem` recibe:

```jsx
const CarouselItem = ({ producto }) => {
  return <h3>{producto.nombre}</h3>
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productItem/CarouselItem.jsx

#### Para memorizar

> Props = datos de entrada del componente. Vienen desde afuera. El componente no debería mutarlas.

> Regla de flujo: props bajan desde el padre; si el hijo necesita provocar un cambio, recibe una funcion callback y la ejecuta. Esa unidireccionalidad mantiene la UI mas predecible.

---

### 10) State: memoria interna del componente

El **estado** representa datos internos que pueden cambiar con el tiempo y producir un re-render.

Ejemplo real:

```js
const [index, setIndex] = useState(0);
```

- `index`: valor actual.
- `setIndex`: función para actualizarlo.
- `0`: valor inicial.

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productCarousel/ProductCarousel.jsx

Uso:

```js
const puedeRetroceder = index > 0;
const puedeAvanzar = index < ultimoIndice;

const retroceder = () => {
  if (puedeRetroceder) setIndex(index - 1);
};

const avanzar = () => {
  if (puedeAvanzar) setIndex(index + 1);
};
```

Y en la UI:

```jsx
<button onClick={retroceder} disabled={!puedeRetroceder}> {'<'} </button>
<button onClick={avanzar} disabled={!puedeAvanzar}> {'>'} </button>
```

#### Concepto importante

No se cambia estado así:

```js
index = index + 1 // MAL
```

Se cambia con el setter:

```js
setIndex(index + 1) // BIEN
```

Porque React necesita enterarse del cambio para volver a renderizar.

#### Puente a hooks (se profundiza en Clase 10)

`useState` es un **hook**. Un hook es una función especial de React que permite usar capacidades como estado, efectos y ciclo de vida dentro de componentes funcionales.

Para esta clase alcanza con esta idea:

```txt
useState   -> estado interno
useEffect  -> ejecutar efectos después del render
useContext -> compartir datos sin pasar props manualmente por todos los niveles
```

La teoría también menciona otros hooks (`useReducer`, `useRef`, `useCallback`, `useMemo`) y los custom hooks. En Clase 09 no hace falta desarrollarlos; alcanza con entender que los hooks conectan componentes funcionales con estado, ciclo de vida, contexto y reutilización de lógica.

Antes, muchas de esas capacidades se asociaban a componentes de clase. Con hooks, los componentes funcionales pueden recordar datos y reaccionar a cambios sin transformarse en clases. No nos adelantamos demasiado: en Clase 10 se trabaja en serio `useState`, `useEffect` y las reglas de hooks.

---

### 11) Listas y `key`: renderizar colecciones

React permite renderizar listas usando `map`.

Ejemplo real: en `ProductCarousel.jsx`:

```jsx
{productos.map((producto) => (
  <CarouselItem producto={producto} key={producto.id} />
))}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productCarousel/ProductCarousel.jsx

La `key` ayuda a React a identificar que elemento cambio, se agrego o se elimino.

#### Error típico

Usar indice del array como `key` siempre:

```jsx
productos.map((producto, index) => <Item key={index} />)
```

Puede funcionar en listas estaticas, pero si reordenas/agregas/eliminas elementos, React puede asociar mal estado y DOM. Mejor usar un identificador estable:

```jsx
key={producto.id}
```

#### Puente a renderizado condicional (se profundiza en Clase 10)

Cuando renderizas una colección también suele aparecer una pregunta: **¿qué muestro si la lista está vacía?** Ahí entra el renderizado condicional.

Ejemplo simple:

```jsx
{productos.length === 0 ? (
  <p>No hay productos disponibles</p>
) : (
  productos.map((producto) => (
    <CarouselItem producto={producto} key={producto.id} />
  ))
)}
```

La idea es que el JSX puede depender de condiciones de JavaScript. En Clase 09 alcanza con reconocerlo; en Clase 10 se formaliza con `if`, ternarios y `&&`.

En el repo ya aparece una variante temprana dentro de `ProductCarousel.jsx`:

```jsx
if (!Array.isArray(productos) || productos.length === 0) {
  return <p className="carousel-empty">No hay productos disponibles</p>;
}
```

---

### 12) Eventos: interacción del usuario

Los eventos se pasan como props especiales.

Ejemplo:

```jsx
<button onClick={avanzar} disabled={!puedeAvanzar}>
  {'>'}
</button>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productCarousel/ProductCarousel.jsx

Flujo:

```txt
usuario hace click
  -> se ejecuta avanzar
  -> setIndex cambia estado
  -> React renderiza de nuevo
  -> cambia el desplazamiento del carrusel
```

Ojo con este detalle: en JSX se pasa la función, no su resultado.

```jsx
onClick={avanzar}    // bien
onClick={avanzar()}  // mal: ejecuta durante render
```

---

### 13) Routing en React: SPA con múltiples vistas

El PDF dice que React por sí solo no trae routing. Para eso se usa React Router.

En una SPA no hay una página HTML distinta para cada pantalla. Hay una aplicación que cambia que componentes muestra según la URL.

#### `BrowserRouter`: habilita routing en el cliente

```jsx
<BrowserRouter>
  <App />
</BrowserRouter>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/index.js

#### `Routes` y `Route`: declaran rutas

```jsx
<Routes>
  <Route path="/" element={<Layout />}> // Layout es el componente común a todas las rutas hijas
    <Route index element={<Home />} />
    <Route path="/productos/:id" element={<ProductDetailPage />} />
  </Route>
</Routes>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/App.jsx

Lectura:

| Ruta | Componente |
|---|---|
| `/` | `Layout` + `Home` |
| `/productos/:id` | `Layout` + `ProductDetailPage` |

#### `Outlet`: donde se renderiza la ruta hija

`Layout` contiene elementos comunes:

```jsx
<Header username="Alumno/a de DDSO" />
<Navbar />
<Outlet />
```

`Outlet` es el hueco dónde React Router mete la pantalla hija (`Home` o `ProductDetailPage`).

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/features/layout/Layout.jsx

---

### 14) `Link` vs `<a>`

En React Router se usa `Link` para navegar sin recargar toda la página.

Ejemplo real:

```jsx
<Link to={`/`} className="link-no-style">
  <h1 className="brand-text"> Megasuper.com </h1>
</Link>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/headers/Navbar.jsx

Y en cada producto:

```jsx
<Link to={`/productos/${producto.id}`} className="ver-detalles-btn">
  Ver Detalles
</Link>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productItem/CarouselItem.jsx

Diferencia:

| Navegacion | Qué pasa |
|---|---|
| `<a href="/productos/1">` | el navegador puede recargar documento completo |
| `<Link to="/productos/1">` | React Router cambia la vista dentro de la SPA |

---

### 15) Route params: leer datos desde la URL

La ruta:

```jsx
<Route path="/productos/:id" element={<ProductDetailPage />} />
```

Define un parámetro dinámico `id`.

En `ProductDetailPage.jsx` se lee con `useParams`:

```js
const { id } = useParams();
const producto = productos.find((p) => p.id === parseInt(id));
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/features/products/ProductDetailPage.jsx

Si el producto no existe, se renderiza una pantalla alternativa:

```jsx
if (!producto) {
  return (
    <div className="product-detail-container">
      <div className="product-header">
        <h1>Producto no encontrado</h1>
        <p>Lo sentimos, no pudimos encontrar el producto que buscas.</p>
      </div>
    </div>
  );
}
```

Concepto:

```txt
URL /productos/3
  -> useParams() devuelve { id: "3" }
  -> se busca producto id 3
  -> se renderiza detalle
```

---

### 16) Datos mock y separación con backend

En esta clase el frontend todavía usa datos mockeados.

`Productos.js` exporta un array:

```js
const productos = [
  { id: 1, nombre: "Coca-Cola 1.5L", precio: 2500, imagen: "/images/coca-cola-1lt.jpg" },
  // ...
];
```

Tambien hay funciones async preparadas:

```js
async function obtenerProductos() {
  return productos;
}

async function obtenerProductoPorId(id) {
  return productos.find((producto) => producto.id === id) ?? null;
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/mockdata/Productos.js

Pero los componentes usan el array directo:

```js
import { productos } from "../../mockdata/Productos";
```

Esto es normal para una primera clase de front: primero se arma UI y navegación; después se reemplaza mock por llamadas HTTP al backend.

#### Tradeoff

- Mock rápido: permite diseñar UI sin depender del backend.
- Mock demasiado tiempo: podes construir una UI que después no coincide con la API real.

CONCEPTOS > CODE: el mock es andamio, no edificio terminado.

---

### 17) Estilos: CSS por componente + variables globales

El proyecto usa CSS tradicional importado desde componentes.

Ejemplo:

```js
import "./ProductCarousel.css";
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productCarousel/ProductCarousel.jsx

En `index.css` se definen variables globales:

```css
:root {
  --primary-green: rgb(30, 126, 52);
  --secondary-green: rgb(72, 168, 90);
  --primary-white: rgb(250, 250, 250);
  --primary-orange: rgb(255, 140, 0);
  --primary-gray: rgb(36, 36, 36);
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/index.css

Y se consumen en otros CSS:

```css
.navbar-bg {
  background-color: var(--primary-green);
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/headers/Navbar.css

Idea:

- estilos globales: reset, fuentes, variables;
- estilos de componente: layout y apariencia propia de cada componente.

---

### 18) Scripts del proyecto CRA ya creado

Como el setup desde cero ya lo vimos al inicio, acá lo importante es leer que dejo CRA dentro del repo.

En `client/package.json` aparecen scripts típicos:

```json
{
  "scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject"
  }
}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/package.json

Lectura:

- `start`: levanta el servidor de desarrollo.
- `test`: ejecuta tests en modo interactivo.
- `build`: genera bundle de producción.
- `eject`: expone configuración interna de CRA; es irreversible y no hace falta para la clase.

Dependencias clave:

- `react` -> biblioteca principal para componentes.
- `react-dom` -> integra React con el DOM del browser.
- `react-router-dom` -> routing de la SPA. Docu recomendada: https://reactrouter.com/home
- `bootstrap` -> estilos/componentes base.
- `react-icons` -> iconos como componentes React. Docu recomendada: https://react-icons.github.io/react-icons/

---

### 19) Gotchas reales del repo (aprendizaje de verdad)

1. **La búsqueda todavía no busca**.
   - `ProductSearchBar` renderiza un input y un botón, pero no maneja estado ni evento `onChange`.
   - El README dice que filtra productos en tiempo real, pero el código actual no lo implementa.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/src/components/productSearchBar/ProductSearchBar.jsx

2. **Mock async preparado, pero no usado**.
   - `Productos.js` exporta `obtenerProductos()` y `obtenerProductoPorId()`, pero los componentes importan `productos` directamente.
   - Esto está bien como paso inicial, pero no confundirlo con integracion real a backend.

3. **README dice React 18+, package usa React 19.2.6**.
   - No rompe el apunte, pero es una inconsistencia de documentación.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase9-front-react-pt1/client/package.json

4. **`App.css` parece quedar de plantilla CRA**.
   - Tiene estilos del logo default, pero `App.jsx` no lo importa en esta rama.
   - Esto es deuda menor/ruido típico de scaffolding.

5. **`parseInt(id)` sin radix y sin validación explícita**.
   - Para una clase inicial está bien, pero en producción convendría validar `Number.isInteger` y manejar IDs inválidos con más claridad.

---

### 20) Resumen mental de Clase 09

Si te preguntan "¿qué es React y cómo se estructura esta app?", contestá:

> React es una biblioteca de JavaScript para construir interfaces declarativas basadas en componentes. En esta app CSR, `index.html` aporta un `div#root`, `index.js` monta React con `createRoot`, `App.jsx` declara las rutas con React Router, `Layout` contiene partes comunes como `Header` y `Navbar`, y las pantallas (`Home`, `ProductDetailPage`) se componen con componentes reutilizables. Los datos bajan por props, los eventos pueden subir como callbacks, el estado interno se maneja con `useState`, y los cambios de state o props disparan re-render. React compara la nueva UI virtual con la anterior y actualiza el DOM real de forma eficiente.

Checklist para examen:

- CRA crea una app React con estructura, scripts y bundling preconfigurado; hoy está deprecado para proyectos nuevos, pero explica el repo de la clase.
- **SSR**: servidor genera HTML. **CSR**: cliente genera UI con JS.
- React se monta en `#root` con `ReactDOM.createRoot`.
- Componentización = reutilización + parametrización + legibilidad.
- MVC/MVVM/Flux son formas de ordenar datos, vista e interacciones; para React importa especialmente el flujo unidireccional.
- Reactividad = cambios de state/props disparan re-render.
- React es declarativo: describís la UI, no cada manipulación DOM.
- Componente = función JS que devuelve JSX.
- JSX usa `className`, `{}` para expresiones y componentes en mayúscula.
- Props = datos que bajan del padre al hijo; no se mutan desde el hijo.
- State = datos internos que cambian y disparan re-render.
- `useState` devuelve `[valor, setter]` y es el primer hook que aparece en el repo.
- Hooks permiten usar estado, efectos, contexto, ciclo de vida y reutilización de lógica en componentes funcionales; se profundizan en Clase 10.
- Listas con `map`; usar `key` estable.
- Renderizado condicional = mostrar JSX distinto según una condición; se profundiza en Clase 10.
- Eventos como `onClick={handler}`, no `onClick={handler()}`.
- React Router permite SPA con rutas del lado cliente.
- `BrowserRouter` envuelve la app; `Routes/Route` declaran pantallas.
- `Outlet` renderiza rutas hijas dentro de un layout.
- `Link` navega sin recargar toda la app.
- `useParams` lee parámetros dinámicos como `/productos/:id`.
- Mock data sirve para construir UI antes de integrar backend, pero no reemplaza la API real.
- Utils, composición y HOC son técnicas distintas de reutilización; en este repo predomina composición.

---
## Clase 10 - React Hooks, estado y carrito

Fuente práctica:
- PDF local: `Clases_Practica/Clase Práctica - 10 - React_ Hooks.pdf`
- Cache textual: `_cache_pdf_text/Clase_Practica_10_React_Hooks.txt`
- Toma propia: `Clases_Practica/clase 10 - toma de apuntes.md`

Fuente teórica relacionada:
- Cache textual: `_cache_pdf_text/clase-11-teoria-sesiones.md`
- Aclaración: no pertenece estrictamente a esta clase, pero sirve como puente para conectar estado, hooks, `Context`, `localStorage`, JWT y rutas protegidas.

Fuente de código:
- Repo/rama: https://github.com/ddso-utn/ejercicio-megasuper-2026/tree/clase10-front-react-pt2
- Subproyecto: `client/`

Links recomendados por la cátedra:
- Material UI: https://mui.com/
- React Bootstrap: https://react-bootstrap.netlify.app/
- Ant Design: https://ant.design/
- Hooks guide: https://hooks-guide.netlify.app/
- W3Schools React Hooks: https://www.w3schools.com/react/react_hooks.asp
- React docs - Managing State: https://react.dev/learn/managing-state

Idea central de la clase:
> En la Clase 09 armamos la base de React: componentes, JSX, props, listas, eventos y routing. En la Clase 10 esa UI empieza a tener memoria y comportamiento real: estado local, efectos, carga asincrónica, formularios controlados y carrito compartido.

La continuidad es importante: la Clase 09 te enseñó **cómo se compone** una interfaz; esta clase te muestra **cómo reacciona** esa interfaz cuando el usuario escribe, navega, carga datos o agrega productos al carrito.

Acá hay una idea que tenés que tener CLARA: **el estado no es una variable común**. Si cambiás una variable común, React no se entera. Si cambiás estado con su setter, React agenda un nuevo render. Esa diferencia es la base de toda interfaz interactiva.

---

### 1) Árbol de renderizado: cómo React organiza la UI

#### Problema

En React no pensamos una pantalla como un HTML gigante escrito de una vez. Pensamos la interfaz como una composición de componentes:

```txt
una pantalla
  -> se arma con componentes
  -> esos componentes renderizan otros componentes
  -> algunos hijos aparecen o desaparecen según la ruta, el estado o las props
```

Si no entendés ese árbol, después se vuelve difícil explicar por qué un cambio de estado actualiza una parte de la UI, por qué `Outlet` muestra una pantalla hija o por qué un componente no debería saber responsabilidades que pertenecen a su padre.

#### Concepto

Cuando anidamos componentes, React arma un **árbol de renderizado**: una estructura de componentes padre e hijo que representa qué se está renderizando en un pase concreto.

Importante: no es exactamente lo mismo que:

- el árbol de carpetas del proyecto;
- el DOM final del navegador;
- todas las rutas posibles de la aplicación al mismo tiempo.

Es el árbol de componentes que React evalúa para describir la UI actual.

#### Modelo mental de MegaSuper

```txt
App
`-- ThemeProvider
    `-- Routes
        `-- Layout
            |-- Header
            |-- Navbar
            `-- Outlet
                |-- Home
                |   |-- ProductSearchBar
                |   `-- ProductCarousel
                |       `-- CarouselItem[]
                |-- ProductDetailPage
                `-- Checkout
```

Lectura:

```txt
App define estructura general
ThemeProvider provee tema visual
Routes decide qué ruta corresponde
Layout muestra partes comunes
Outlet renderiza la pantalla hija de la ruta actual
Home / ProductDetailPage / Checkout son alternativas según la URL
```

Ese árbol representa **un pase de renderizado**. Si cambia el estado, cambian las props o cambia la ruta, React vuelve a evaluar los componentes afectados y genera una nueva descripción de la UI.

#### Ejemplo real del repo

En `App.jsx` la aplicación declara las rutas y pasa componentes a cada pantalla:

```jsx
<Route path="/" element={<Layout carrito={carrito} />}>
  <Route index element={<Home />} />
  <Route
    path="/productos/:id"
    element={
      <ProductDetailPage
        carrito={carrito}
        actualizarCarrito={actualizarCarrito}
      />
    }
  />
  <Route
    path="/checkout"
    element={
      <Checkout
        carrito={carrito}
        limpiarCarrito={limpiarCarrito}
      />
    }
  />
</Route>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/App.jsx

Qué muestra este ejemplo:

- `App` es el ancestro común donde vive el carrito.
- `Layout` contiene UI compartida entre rutas.
- `Outlet` marca el lugar donde React Router inserta la pantalla correspondiente.
- `Home`, `ProductDetailPage` y `Checkout` no se muestran todos juntos: dependen de la URL.
- El carrito baja por props hacia quienes lo necesitan.

#### Error típico

Pensar que "si está declarado en `Routes`, entonces está renderizado". No. Una ruta declarada es una posibilidad. React Router renderiza la rama que coincide con la URL actual.

Otro error típico: confundir árbol de renderizado con estructura de archivos. Que un componente esté en una carpeta no significa que esté montado en pantalla.

#### Para examen

Si te preguntan qué es el árbol de renderizado, podés responder:

> Es la estructura padre-hijo de componentes que React está renderizando en un momento dado. Cambia según rutas, props, estado y renderizado condicional. En MegaSuper, `App` define rutas, `Layout` mantiene partes comunes y `Outlet` muestra la pantalla hija actual.

---

### 2) Renderizado condicional

Renderizado condicional significa que un componente puede devolver JSX distinto según una condición.

React no inventa una sintaxis mágica para esto: usamos JavaScript.

#### Con `if`

```jsx
if (!producto) {
  return <h1>Producto no encontrado</h1>;
}
```

Sirve cuando querés cortar temprano el render.

#### Con operador ternario

```jsx
{carrito.length === 0 ? (
  <p>El carrito esta vacio</p>
) : (
  carrito.map((producto, index) => (
    <div key={index}>{producto.nombre}</div>
  ))
)}
```

Sirve cuando una zona de JSX tiene dos alternativas.

#### Con `&&`

```jsx
{name} {isPacked && 'OK'}
```

Sirve cuando querés mostrar algo solo si la condición es verdadera.

#### Ejemplo real: spinner mientras cargan productos

En `Home.jsx`:

```jsx
{!productos.length ? (
  <div className="spinner">
    <Spinner />
  </div>
) : (
  <div>
    <ProductCarousel productos={productosFiltrados} />
  </div>
)}
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/features/home/Home.jsx

Lectura:

```txt
productos vacio -> muestro loading
productos cargados -> muestro carrusel
```

Bien ahi: esto mejora UX. El usuario no queda mirando una pantalla muerta mientras se simula la carga.

---

### 3) Estado: datos que cambian y disparan render

El estado representa datos dinámicos de un componente. Ejemplos:

- texto escrito en un input;
- productos cargados;
- productos filtrados;
- unidades seleccionadas;
- carrito;
- campos de un formulario.

Cuando el estado cambia con su setter, React vuelve a renderizar.

```txt
evento del usuario
  -> setter de estado
  -> nuevo render
  -> UI actualizada
```

NO confundas esto con una variable local. Una variable local se pierde entre renders y no le avisa nada a React.

Este es el salto conceptual desde la Clase 09: antes nos alcanzaba con pasar datos por props; ahora necesitamos que la UI recuerde decisiones del usuario y cambie con ellas.

---

### 4) Hooks: funciones especiales de React

Un hook es una función que permite usar capacidades de React dentro de componentes funcionales.

Reglas importantes:

1. Se llaman dentro de componentes funcionales o custom hooks.
2. Se llaman en el nivel superior del componente.
3. No se llaman dentro de `if`, loops ni funciones anidadas.

¿Por qué tanta regla? Porque React necesita que los hooks se ejecuten siempre en el mismo orden entre renders. Si los llamás condicionalmente, rompés la correspondencia interna.

#### Tipos vistos

- **Estado**: `useState`, `useReducer`.
- **Efectos**: `useEffect`.
- **Referencias**: `useRef`.
- **Contexto**: `useContext`.
- **Performance**: `useMemo`, `useCallback`.

En esta clase el foco real estuvo en `useState` y `useEffect`.

Los demás aparecen como mapa mental para no perder el norte:

```txt
useState/useReducer -> memoria del componente
useEffect           -> sincronizar con algo externo al render
useRef              -> guardar una referencia que no dispara render
useContext          -> leer estado compartido sin pasarlo por cada prop
useMemo/useCallback -> evitar trabajo o referencias innecesarias en ciertos casos
```

Y cuando una lógica con estado se repite, se puede encapsular en un **custom hook**. Por ejemplo, más adelante `useSession()` puede envolver `useContext(SessionContext)` para que cualquier componente lea la sesión sin conocer los detalles internos del proveedor.

---

### 5) `useState`: recordar información entre renders

Sintaxis base:

```jsx
const [valor, setValor] = useState(valorInicial);
```

Ejemplo del PDF:

```jsx
const [contador, setContador] = useState(0);
```

Lectura:

```txt
contador    -> valor actual
setContador -> función para pedir un cambio de estado
0           -> valor inicial
```

#### Ejemplo real: búsqueda controlada

En `ProductSearchBar.jsx`:

```jsx
const [searchText, setSearchText] = useState('');
```

Y el input queda controlado por React:

```jsx
<TextField
  value={searchText}
  onChange={(e) => setSearchText(e.target.value)}
  fullWidth
  variant="standard"
  placeholder="¿Qué buscásí"
/>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/components/productSearchBar/ProductSearchBar.jsx

Eso se llama **componente controlado**:

```txt
usuario escribe
  -> onChange
  -> setSearchText
  -> React renderiza el input con el nuevo value
```

La UI y el estado quedan sincronizados. Eso es muchísimo más sano que leer el DOM a mano con `document.querySelector`.

---

### 6) Props + callback `filtrarProductos`: el hijo le avisa al padre

`ProductSearchBar` no filtra por su cuenta. Captura el texto y se lo devuelve al padre mediante una callback.

El callback concreto de esta clase es **`filtrarProductos`**:

```txt
Home define filtrarProductos
  -> se lo pasa como prop a ProductSearchBar
  -> ProductSearchBar lo ejecuta cuando el usuario toca Buscar
  -> Home actualiza productosFiltrados
```

Esta separación es importante: el hijo sabe **cuándo ocurrió el evento**, pero el padre decide **qué hacer con ese evento**.

```jsx
const ProductSearchBar = ({ filtrarProductos }) => {
  const [searchText, setSearchText] = useState('');

  return (
    <Button variant="outlined" onClick={() => filtrarProductos(searchText)}>
      Buscar
    </Button>
  );
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/components/productSearchBar/ProductSearchBar.jsx

En `Home.jsx`, el padre define la lógica:

```jsx
const filtrarProductos = (searchText) => {
  if (searchText.trim() === '') {
    setProductosFiltrados(productos);
  } else {
    const texto = searchText.toLowerCase();
    const filtered = productos.filter(producto =>
      producto.nombre.toLowerCase().includes(texto) ||
      producto.categoria.toLowerCase().includes(texto)
    );
    setProductosFiltrados(filtered);
  }
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/features/home/Home.jsx

Traducción:

```txt
ProductSearchBar sabe capturar texto
Home sabe qué hacer con ese texto
```

Esto está bien diseñado para la clase: el hijo no debería conocer toda la lista de productos si su responsabilidad es solamente ser barra de búsqueda.

Conexión con Clase 09: ya habíamos visto que las props bajan datos. Ahora aparece la otra mitad del patrón: **los callbacks suben eventos o intenciones**.

---

### 7) `useEffect`: efectos después del render

`useEffect` permite ejecutar código después de que React renderiza.

Sintaxis base:

```jsx
useEffect(() => {
  // efecto
}, [dependencias]);
```

Idea clave:

```txt
React renderiza primero
React ejecuta efectos después
```

#### Variantes

Sin array:

```jsx
useEffect(() => {
  console.log('corre después de cada render');
});
```

Array vacío:

```jsx
useEffect(() => {
  console.log('corre al montar');
}, []);
```

Con dependencias:

```jsx
useEffect(() => {
  console.log('corre cuando cambia userId o filtro');
}, [userId, filtro]);
```

#### Ejemplo del PDF

```jsx
const Count = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  }, [count]);

  return (
    <button onClick={() => setCount(count + 1)}>
      Click me
    </button>
  );
};
```

Lectura:

```txt
click -> setCount -> render -> efecto actualiza document.title
```

Clave: el render debería ser lo más puro posible. Cargar datos, tocar `document.title`, escuchar eventos externos o manejar timers son efectos; por eso viven en `useEffect` y no mezclados en el cuerpo del JSX.

---

### 8) Carga async de productos con `useEffect`

En esta rama aparece un servicio que simula una API lenta:

```js
export const getProductsSlowly = () => new Promise((resolve) => {
  setTimeout(() => {
    resolve(productos);
  }, 3000);
});
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/service/productsService.js

El PDF muestra el mismo patrón con una función `obtenerProductos()` que podría ir al backend. En esta rama todavía no hay integración real: se simula latencia con `setTimeout` para poder practicar loading, efecto y render condicional sin depender de una API.

`Home.jsx` lo usa así:

```jsx
const [productos, setProductos] = useState([]);
const [productosFiltrados, setProductosFiltrados] = useState([]);

const cargarProductos = async () => {
  const productosCargados = await getProductsSlowly();
  setProductos(productosCargados);
  setProductosFiltrados(productosCargados);
};

useEffect(() => {
  cargarProductos();
}, []);
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/features/home/Home.jsx

Lectura paso a paso:

```txt
primer render:
  productos = []
  se muestra Spinner

después del render:
  useEffect ejecuta cargarProductos
  getProductsSlowly espera 3 segundos
  setProductos + setProductosFiltrados

nuevo render:
  productos tiene datos
  se muestra ProductCarousel
```

Esto anticipa el patrón real de integración con backend: al montar la pantalla, pedís datos; mientras tanto, mostrás estado de carga.

---

### 9) Resetear estado cuando cambian props

En `ProductCarousel.jsx`, el carrusel mantiene un índice interno:

```jsx
const [index, setIndex] = useState(0);
```

Pero si cambia la lista de productos, resetea el carrusel:

```jsx
useEffect(() => {
  setIndex(0);
}, [productos]);
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/components/productCarousel/ProductCarousel.jsx

¿Por qué importa? Si estabas en el ítem 5 y filtrás una lista de 2 productos, el índice anterior puede quedar fuera de rango. El efecto sincroniza el estado interno con la nueva entrada.

Esto es una buena lección: **el estado interno no vive aislado**. Si depende de props, hay que pensar cómo se mantiene consistente.

---

### 10) Librerías de componentes: MUI y React Bootstrap

La clase mostró librerías de UI preconstruidas:

- **Material UI / MUI**: componentes React listos para usar, con theming(personalización de colores y tipografía) y sistema visual basado en Material Design.
- **React Bootstrap**: componentes Bootstrap reconstruidos como componentes React.
- **Ant Design**: otra biblioteca fuerte para productos empresariales y dashboards.

En el repo se usan principalmente MUI y React Bootstrap.

#### Tema global con Material UI

En `App.jsx`:

```jsx
const theme = createTheme({
  palette: {
    primary: {
      main: '#ff8c00'
    }
  },
  typography: {
    fontFamily: "'Poppins', sans-serif"
  }
});
```

Y se aplica a toda la app:

```jsx
<ThemeProvider theme={theme}>
  <Routes>{/* rutas */}</Routes>
</ThemeProvider>
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/App.jsx

Idea:

```txt
un tema central -> componentes MUI leen ese tema -> UI más consistente
```

#### Componentes MUI usados

- `TextField` para inputs.
- `Button` para botones.
- `ButtonGroup` para selector de unidades.
- `Card` para contenedor del checkout.

#### React Bootstrap usado

En `Home.jsx`:

```jsx
import { Spinner } from 'react-bootstrap';
```

Se usa para mostrar carga mientras `getProductsSlowly()` todavía no resolvió.

#### Tradeoff real

Usar librerías está bien, pero ojo: NO son reemplazo de entender HTML, CSS, estado y composición. Una librería acelera, no piensa por vos.

```txt
usar componentes preconstruidos -> más velocidad y consistencia
hacer todo custom -> más control, más tiempo, más mantenimiento
```

El criterio profesional es equilibrar ambas cosas.

---

### 11) Estado compartido: carrito levantado a `App`

El carrito se declara en `App.jsx`:

```jsx
const [carrito, setCarrito] = useState([]);
```

Y `App` define callbacks para modificarlo:

```jsx
const actualizarCarrito = (producto) => {
  setCarrito([...carrito, producto]);
};

const limpiarCarrito = () => {
  setCarrito([]);
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/App.jsx

¿Por qué el carrito está en `App` y no en `ProductDetailPage`? Porque lo necesitan varias partes:

- `ProductDetailPage` agrega productos.
- `Navbar` muestra la cantidad.
- `Checkout` muestra el resumen y limpia el carrito.

Entonces el estado se levanta al ancestro común.

```txt
App
|-- Layout -> Navbar necesita carrito
|-- ProductDetailPage necesita actualizar carrito
`-- Checkout necesita leer y limpiar carrito
```

Esta es la idea de **lifting state up**: cuando varios componentes necesitan coordinarse, el estado sube al padre común.

La clase aclara algo importante: para practicar, se pasó por props. Más adelante, con muchos niveles, conviene evaluar Context.

#### Diagrama del flujo de datos

```txt
ProductDetailPage
  unidades local + producto
  click "Agregar al carrito"
        |
        v
actualizarCarrito(productoConUnidades)
        |
        v
App actualiza carrito con setCarrito
        |
        +--> Layout -> Navbar recibe carrito y muestra cantidad
        |
        +--> Checkout recibe carrito y muestra resumen
        |
        `--> ProductDetailPage puede resetear unidades si cambia carrito
```

La lectura correcta es: **el detalle no es dueño del carrito**. El detalle solo informa una intención: "agregar este producto con estas unidades". El dueño del estado compartido es `App`.

Este punto conecta directamente con lo que viene después: si levantar estado a `App` empieza a obligarte a pasar props por demasiados componentes intermedios, aparece `Context` como herramienta para compartir estado de aplicación sin prop drilling.

---

### 12) Flujo del carrito

#### En detalle de producto

`ProductDetailPage` maneja las unidades localmente:

```jsx
const [unidades, setUnidades] = useState(0);
```

Incrementa/decrementa:

```jsx
const incrementarUnidades = () => {
  setUnidades(unidades + 1);
};

const decrementarUnidades = () => {
  if (unidades > 0) {
    setUnidades(unidades - 1);
  }
};
```

Agrega al carrito y navega:

```jsx
const agregarAlCarrito = () => {
  actualizarCarrito(conUnidades(unidades, producto));
  navigate('/');
};
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/features/products/ProductDetailPage.jsx

También resetea unidades si cambia el producto o el carrito:

```jsx
useEffect(() => {
  setUnidades(0);
}, [id, carrito]);
```

#### En navbar

`Navbar` calcula unidades totales del carrito:

```jsx
const cantUnidadesEnCarrito = () => {
  let suma = 0;
  for (const producto of carrito) {
    suma += producto.unidades;
  }
  return suma;
};
```

Y sincroniza su estado cuando cambia `carrito`:

```jsx
useEffect(() => {
  setCantUnidades(cantUnidadesEnCarrito());
}, [carrito]);
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/components/headers/Navbar.jsx

#### Estado propio vs estado derivado

Acá hay una distinción fina, pero MUY importante:

- `carrito` en `App` es **estado propio/fuente de verdad**: alguien tiene que guardarlo.
- `unidades` en `ProductDetailPage` es **estado propio local**: representa una decisión temporal del usuario en esa pantalla.
- `cantUnidades` en `Navbar` es **estado derivado**: se calcula a partir de `carrito`.

Eso último es debatible. En esta rama se guarda `cantUnidades` en estado y se sincroniza con `useEffect`, que sirve para practicar efectos. Pero conceptualmente también podría calcularse directo:

```jsx
const cantUnidades = carrito.reduce((acc, producto) => acc + producto.unidades, 0);
```

Tradeoff:

```txt
guardarlo en estado + useEffect -> practica efectos, pero duplica información
calcularlo en render           -> menos estado, menos riesgo de desincronización
```

Regla profesional: **no guardes en estado lo que puedas derivar claramente de otro estado**, salvo que haya un motivo concreto de performance, UX o sincronización externa. Si no, estás duplicando la verdad, y duplicar verdad es pedir bugs.

Lectura completa:

```txt
click en +
  -> setUnidades
click Agregar
  -> actualizarCarrito en App
  -> App cambia carrito
  -> Layout/Navbar reciben carrito nuevo
  -> Navbar actualiza contador
```

---

### 13) Problemas abiertos: del carrito local al estado de aplicación

La Clase 10 no intenta resolver todo el estado de una app real. Hace algo más importante: deja planteados los problemas que justifican la Clase 11 y 12.

En esta rama, el carrito vive en `App`:

```txt
App tiene carrito en useState
App pasa carrito y callbacks por props
Navbar / ProductDetailPage / Checkout usan esas props
```

Eso está perfecto para aprender **lifting state up**, props y callbacks. Pero también muestra los límites del enfoque.

#### Problema 1: prop drilling

Si más componentes necesitan el carrito, podemos terminar pasando props por componentes que no las usan directamente.

```txt
App
  -> Layout recibe carrito solo para pasarlo
    -> Navbar realmente usa carrito
```

Ese problema prepara el terreno para `Context` y un custom hook como `useCarrito()`, que se desarrollan en Clase 11/12.

#### Problema 2: estado no persistido

El carrito está en memoria de React:

```txt
recargás la página
  -> React monta de nuevo
  -> carrito vuelve a []
```

Eso no está mal para la clase. Simplemente significa que todavía no decidimos persistencia. Más adelante se puede discutir si conviene `localStorage`, backend, sesión o una combinación.

#### Problema 3: identidad y seguridad

El carrito representa estado de UI/aplicación. Una sesión representa otra cosa: identidad del usuario, token, roles y permisos.

```txt
carrito -> qué quiere comprar el usuario en esta UI
sesión  -> quién es el usuario y qué puede hacer
```

Por eso no conviene mezclar conceptos. Clase 10 deja claro el problema del estado compartido; Clase 11/12 desarrolla integración con backend, CORS, sesiones, JWT, `Context`, `ProtectedRoute` y validación real del lado servidor.

La idea importante es esta:

> No saltamos a Context ni a sesión para evitar aprender props. Primero entendemos props, callbacks y estado levantado. Recién después tiene sentido usar herramientas más globales.

---

### 14) Checkout: formulario controlado

`Checkout.jsx` maneja varios campos con un solo objeto de estado.

Inicialización:

```jsx
const inicializarCampo = (requerido = true) => ({ valor: '', requerido });

const inicializarCampos = () => ({
  nombre: inicializarCampo(),
  segundoNombre: inicializarCampo(false),
  apellido: inicializarCampo(),
  email: inicializarCampo(),
  repetirEmail: inicializarCampo()
});
```

Estado:

```jsx
const [campos, setCampos] = useState(inicializarCampos());
```

Fuente:
- https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/features/checkout/Checkout.jsx

Para leer un valor:

```jsx
const valorDe = (nombreCampo) => campos[nombreCampo].valor;
```

Para actualizarlo, usa una función que devuelve otra función:

```jsx
const setValorDe = (nombreCampo) => (e) => {
  const nuevoValor = e.target.value;
  setCampos({
    ...campos,
    [nombreCampo]: {
      ...campos[nombreCampo],
      valor: nuevoValor
    }
  });
};
```

Esto es importante: al actualizar objetos en estado, se copia el objeto anterior con spread. No se muta directo.

```txt
NO: campos.nombre.valor = 'Martin'
SI: setCampos({ ...campos, nombre: { ...campos.nombre, valor: 'Martin' } })
```

#### Validación mínima

```jsx
const camposCompletos = Object.values(campos).every(campo =>
  !campo.requerido || campo.valor.length
);
```

Y el botón se deshabilita si faltan campos o el carrito está vacío:

```jsx
<Button
  disabled={!camposCompletos || carrito.length === 0}
  variant="contained"
  onClick={handleGuardar}
>
  Guardar
</Button>
```

Lectura:

```txt
campos requeridos completos + carrito con items -> se puede guardar
si no -> botón deshabilitado
```

Ojo profesional: `repetirEmail` se pide, pero en esta rama solo se valida que esté completo; no se valida que sea igual a `email`. Para clase está bien, pero en una app real faltaría esa regla.

---

### 15) `useNavigate`: navegar desde código

`useNavigate` permite cambiar de ruta desde un handler.

En `ProductDetailPage.jsx`:

```jsx
const navigate = useNavigate();
```

Después de agregar al carrito:

```jsx
navigate('/');
```

En `Checkout.jsx`, cancelar vuelve al home:

```jsx
const handleCancelar = () => {
  navigate('/');
};
```

Y guardar también vuelve al home luego de limpiar el carrito.

Esto no reemplaza a `Link`. Regla práctica:

```txt
Link -> navegación declarativa visible en la UI
useNavigate -> navegación imperativa después de una acción
```

---

### 16) Componentes de clase: bonus histórico

El PDF muestra componentes de clase como antecedente:

```jsx
class Saludo extends Component {
  constructor(props) {
    super(props);
  this.state = { nombre: 'Valentín' };
  }

  render() {
    return <h1>Hola, {this.state.nombre}!</h1>;
  }
}
```

Antes de hooks, para tener estado y ciclo de vida era común usar clases. Con hooks, los componentes funcionales pueden manejar estado y efectos sin clase.

No hace falta demonizar clases: son parte de la historia de React. Pero para código moderno de esta materia, el foco es componentes funcionales + hooks.

---

### 17) Estado del repo al cierre de Clase 10

1. **Búsqueda ya implementada, pero no en tiempo real**.
   - `ProductSearchBar` actualiza `searchText` en cada cambio, pero filtra cuando el usuario toca `Buscar`.
   - El README dice búsqueda en tiempo real; esta rama funciona por botón.
   - Fuente: https://github.com/ddso-utn/ejercicio-megasuper-2026/blob/clase10-front-react-pt2/client/src/components/productSearchBar/ProductSearchBar.jsx

2. **Carga async simulada**.
   - `getProductsSlowly()` usa `setTimeout` y mock data.
   - Sirve para practicar `useEffect`, estado de carga y spinner.
   - No es todavía integración real con backend.

3. **Carrito compartido por props**.
   - `App` mantiene el carrito y pasa datos/callbacks hacia abajo.
   - Para esta clase está perfecto porque obliga a entender props y callbacks.
   - Si la app crece, Context puede evitar prop drilling.

4. **Estado derivado en Navbar**.
   - `Navbar` guarda `cantUnidades` calculado desde `carrito`.
   - Funciona, pero conceptualmente también podría calcularse directo durante el render.
   - Es una buena conversación para entender diferencia entre estado propio y dato derivado.

5. **Validación de checkout incompleta**.
   - Se valida que campos requeridos tengan texto.
   - No se valida formato fuerte ni igualdad entre `email` y `repetirEmail`.

6. **El carrito no persiste al recargar**.
   - Vive en `useState` dentro de `App`.
   - Si el usuario refresca la página, el carrito vuelve a vacío.
   - Esto está bien para la clase; si se quisiera persistir, habría que decidir entre backend, `localStorage` u otra estrategia.

7. **README desactualizado respecto del código**.
   - El README dice que la búsqueda filtra en tiempo real, pero el código filtra con botón.
   - También enumera rutas iniciales y no refleja todo el flujo de checkout de esta rama.
   - Para estudiar esta clase, priorizá el código de la rama y el apunte.

8. **No ejecutamos build**.
   - Regla del proyecto: no buildear después de cambios.

---

### 18) Resumen mental de Clase 10

Si te preguntan "¿qué agregó la clase 10 a React?", contestá:

> La clase 10 continúa la Clase 09: partimos de componentes, props y routing, y ahora entendemos cómo React actualiza la UI cuando cambian los datos. Vimos árbol de renderizado, renderizado condicional, hooks y especialmente `useState` y `useEffect`. En el repo, `Home` carga productos de forma asincrónica simulada y muestra un spinner; `ProductSearchBar` usa un input controlado y le avisa a `Home` mediante el callback `filtrarProductos`; `ProductCarousel` resetea su índice cuando cambia la lista; `App` levanta el estado del carrito para compartirlo con `Navbar`, `ProductDetailPage` y `Checkout`; y el checkout maneja un formulario controlado con estado compuesto. Como cierre, la clase deja planteados los límites de este diseño: prop drilling, estado no persistido y la necesidad futura de integración con backend, Context y sesión.

Checklist para examen:

- Árbol de renderizado = cómo React organiza componentes padre/hijo en un pase de render.
- Renderizado condicional = JSX distinto según condiciones (`if`, ternario, `&&`).
- Estado = datos dinámicos que, al cambiar con setter, disparan render.
- Hook = función especial para usar capacidades de React en componentes funcionales.
- Reglas de hooks: top-level, no condicionales, dentro de componente/custom hook.
- `useState` devuelve `[valor, setter]`.
- Input controlado = `value` viene del estado y `onChange` actualiza estado.
- Props bajan datos; callbacks suben eventos/intenciones. En esta clase, `filtrarProductos` baja como prop y `ProductSearchBar` lo ejecuta al buscar.
- `useEffect` corre después del render.
- `[]` en `useEffect` = efecto al montar.
- `[deps]` = efecto cuando cambian dependencias.
- Para cargar datos: estado vacío inicial + efecto async + spinner + setState.
- Si varios componentes necesitan el mismo estado, se levanta al padre común.
- Carrito en `App` porque lo usan detalle, navbar y checkout.
- MUI/React Bootstrap aceleran UI, pero no reemplazan entender React.
- `useNavigate` sirve para navegar desde handlers.
- El carrito levantado a `App` funciona para la clase, pero deja abierto el problema de prop drilling.
- El carrito en `useState` no persiste al recargar; esa decisión queda para integración/backend o persistencia futura.
- Context, sesión, JWT y `ProtectedRoute` se desarrollan en Clase 11/12; acá solo quedan motivados.

---

## Clase 11 y 12 - Desarrollo en React avanzado (parte III) + integración con backend

Fuentes usadas:
- Teoría frontend avanzado: `borradores/teoria/clase-11-frontend-avanzado.md`
- Práctica integración front-back: `borradores/practica/clase-11-integracion-front-back.md`
- PDF práctica 11: `Clases_Practica/Clase Práctica - 11 - Integracion Front y Backend.pdf`
- Cache práctica 11: `_cache_pdf_text/clase-11-practica-integracion-front-back.md`
- Repo usado como referencia de integración: https://github.com/ddso-utn/clase-cirbnb/tree/evolutivo-8-integracion
- Teoría sesiones: `_cache_pdf_text/clase-11-teoria-sesiones.md`
- Práctica React avanzado / estado global: `borradores/practica/clase-12-react-manejo-estado.md`
- PDF práctica 12: `Clases_Practica/Clase Práctica - 12 (2025) - React_ Manejo del Estado Global y React Avanzado.pdf`
- Cache práctica 12: `_cache_pdf_text/clase-12-practica-react-estado-global-avanzado.md`
- PR carrito con Context: https://github.com/ddso-utn/ejercicio-megasuper-2026/pull/4
- PR refactor CSS-in-JS: https://github.com/ddso-utn/ejercicio-megasuper-2026/pull/6
- Presentación CSS-in-JS / Context / Custom Hooks: https://docs.google.com/presentation/d/1GqP44ro-spWTtHlY5MPH0qOensN2ElJBj5xj2io9f98/edit?usp=sharing
- Herramientas mencionadas: OpenSpec (https://github.com/Fission-AI/OpenSpec/), GitHub Spec Kit (https://github.com/github/spec-kit) y OpenCode (https://opencode.ai/)

Nota de criterio:
- La práctica de integración front-back se vio con `clase-cirbnb`, pero en este apunte los ejemplos se adaptan pedagógicamente a **MegaSuper** para mantener la historia de la cursada.
- Cuando el código es una adaptación pedagógica a MegaSuper, no se cita como fuente de repo porque **no existe necesariamente en una rama real**.
- Cuando el código viene de los PRs de MegaSuper, se aclara como ejemplo real de PR.

Idea central:
> En las Clases 09 y 10 aprendimos a construir una SPA con componentes, props, rutas, estado local, efectos y carrito. En las Clases 11 y 12 damos el salto a una app más real: integrar frontend con backend, manejar CORS, sesión, JWT, estado global, custom hooks, CSS-in-JS y una forma más ordenada de evolucionar código con SDD.

La pregunta de fondo cambia:

```txt
Clase 09 -> ¿cómo compongo la UI?
Clase 10 -> ¿cómo reacciona la UI ante estado y eventos?
Clase 11/12 -> ¿cómo hago que esa UI conviva con backend, sesión, estado global y evolución del proyecto?
```

Esto es clave: React no vive aislado. Una app real no solo renderiza tarjetas lindas; pide datos, muestra carga, maneja errores, autentica usuarios, evita prop drilling y toma decisiones de arquitectura frontend.

---

### 1) De mock data a backend: el salto conceptual

Hasta la Clase 10, MegaSuper todavía podía funcionar con datos mock o servicios simulados:

```txt
Home monta
  -> getProductsSlowly()
  -> setProductos(...)
  -> spinner mientras espera
```

Eso sirve para aprender `useEffect`, loading y renderizado condicional. Pero en una app real los productos no viven en el bundle del frontend: vienen de una API.

El salto es este:

```txt
antes:
componente -> mock data local

ahora:
componente -> service/api frontend -> HTTP -> backend -> service/repository -> base de datos
```

#### Problema

Si mezclás llamadas HTTP directamente dentro de todos los componentes, el frontend se vuelve difícil de mantener:

```txt
Home sabe de axios
Checkout sabe URLs
Navbar sabe headers
ProductDetail sabe cómo parsear errores HTTP
```

Eso acopla la UI a detalles de infraestructura.

#### Solución

Separar una capa de API o services del lado frontend:

```txt
componentes React
  -> services/api frontend
  -> axios/fetch
  -> backend
```

El componente expresa intención:

```txt
"quiero productos"
"quiero crear compra"
"quiero buscar promoción"
```

El service sabe cómo hablar HTTP:

```txt
GET /productos
POST /compras
GET /notificaciones/promocion
```

---

### 2) Axios y capa de API en MegaSuper

`axios` es una librería para hacer requests HTTP desde JavaScript. Se puede usar con promesas o con `async/await`.

Ventajas prácticas:

- permite crear un cliente con `baseURL`;
- maneja JSON cómodamente;
- permite interceptores;
- centraliza headers;
- facilita manejo de errores HTTP.

#### Ejemplo pedagógico adaptado a MegaSuper

```js
// src/api/apiClient.js
import axios from 'axios';

export const apiClient = axios.create({
  baseURL: process.env.REACT_APP_API_URL,
  timeout: 10000,
  headers: {
    'Content-Type': 'application/json'
  }
});
```

Lectura:

```txt
apiClient concentra configuración HTTP
REACT_APP_API_URL evita hardcodear localhost
los services usan apiClient, no axios suelto
```

Ahora un service para productos:

```js
// src/services/productosService.js
import { apiClient } from '../api/apiClient';

export async function obtenerProductos({ page = 1, texto = '' } = {}) {
  const response = await apiClient.get('/productos', {
    params: { page, texto }
  });

  return response.data;
}

export async function obtenerProductoPorId(id) {
  const response = await apiClient.get(`/productos/${id}`);
  return response.data;
}

export async function crearCompra(payload) {
  const response = await apiClient.post('/compras', payload);
  return response.data;
}
```

Ojo: este código está adaptado a MegaSuper para estudiar el patrón. La idea viene de la integración vista en `clase-cirbnb`, pero no es una rama real de MegaSuper.

#### Dónde llamar al backend

Eventos típicos que disparan llamadas:

```txt
montaje de pantalla      -> cargar productos
cambio de página         -> pedir página siguiente
submit de formulario     -> crear compra/login/reserva
click de usuario         -> buscar, confirmar, cancelar
polling/timer            -> consultar novedades cada X segundos
```

Regla sana:

```txt
handler/useEffect del componente -> llama a service -> service llama al backend
```

No pongas toda la URL y el parseo HTTP en el JSX. El JSX debería contar la UI, no esconder infraestructura.

---

### 3) UX de integración: loading, error y éxito

Integrar con backend no es solo hacer `await axios.get(...)`.

Una pantalla conectada a una API tiene estados:

```txt
idle/loading/error/success
```

Ejemplo pedagógico de `Home` en MegaSuper:

```jsx
import { useEffect, useState } from 'react';
import { obtenerProductos } from '../services/productosService';

export function Home() {
  const [productos, setProductos] = useState([]);
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);
  const [pagina, setPagina] = useState(1);
  const [totalPaginas, setTotalPaginas] = useState(1);

  const cargarProductos = async (page = 1) => {
    setLoading(true);
    setError(null);

    try {
      const resultado = await obtenerProductos({ page });
      setProductos(resultado.data);
      setPagina(resultado.pagina);
      setTotalPaginas(resultado.totalPaginas);
    } catch (err) {
      setError('No pudimos cargar los productos. Intentá nuevamente.');
    } finally {
      setLoading(false);
    }
  };

  useEffect(() => {
    cargarProductos(1);
  }, []);

  if (loading) return <p>Cargando productos...</p>;
  if (error) return <p>{error}</p>;

  return (
    <>
      <ProductCarousel productos={productos} />
      <Paginacion
        currentPage={pagina}
        totalPaginas={totalPaginas}
        onPageChange={cargarProductos}
      />
    </>
  );
}
```

Lectura:

```txt
pantalla monta
  -> loading true
  -> service pide productos
  -> éxito: setProductos + totalPaginas
  -> error: mensaje visible
  -> finally: loading false
```

Esto mejora mucho la calidad de la UI. Sin loading, el usuario no sabe si la app está rota o esperando. Sin error, fallar es quedar en blanco.

---

### 4) Paginación: estado de UI + consulta al backend

En la integración vista con `clase-cirbnb`, el backend devuelve datos paginados y el frontend permite cambiar de página. En MegaSuper se puede pensar igual para el catálogo de productos.

Modelo mental:

```txt
click página 2
  -> cargarProductos(2)
  -> GET /productos?page=2
  -> backend responde { pagina, totalPaginas, data }
  -> React renderiza nueva página
```

Componente de paginación adaptado:

```jsx
export function Paginacion({ currentPage, totalPaginas, onPageChange }) {
  return (
    <div className="paginacion">
      {Array.from({ length: totalPaginas }, (_, i) => i + 1).map((num) => (
        <button
          key={num}
          onClick={() => onPageChange(num)}
          className={num === currentPage ? 'active' : ''}
        >
          {num}
        </button>
      ))}
    </div>
  );
}
```

Conceptualmente hay tres estados:

- `productos`: datos de la página actual;
- `pagina`: página seleccionada;
- `totalPaginas`: metadata devuelta por backend.

Gotcha: si filtrás productos en frontend sobre una sola página, no estás filtrando todo el catálogo. Para búsquedas reales, el filtro debería viajar al backend como query param:

```txt
GET /productos?page=1&texto=arroz
```

---

### 5) Polling: consultar al backend cada cierto tiempo

También se vio la idea de polling para mostrar una promoción o notificación.

Polling significa:

```txt
cada X segundos
  -> preguntar al backend si hay algo nuevo
  -> actualizar UI si corresponde
```

Ejemplo MegaSuper:

```jsx
useEffect(() => {
  const verificarPromocion = async () => {
    const promo = await obtenerPromocionActiva();
    setPromocion(promo?.mensaje ?? null);
  };

  verificarPromocion();
  const intervalo = setInterval(verificarPromocion, 30000);

  return () => clearInterval(intervalo);
}, []);
```

Lo más importante está al final:

```txt
return () => clearInterval(intervalo)
```

Ese cleanup evita que el timer siga corriendo cuando el componente ya no existe. Si te olvidás de limpiarlo, podés generar bugs, requests innecesarios y comportamiento duplicado.

---

### 6) CORS: por qué aparece el error

CORS significa **Cross-Origin Resource Sharing**.

El problema aparece porque frontend y backend pueden estar en orígenes distintos:

```txt
frontend React: http://localhost:3000
backend API:    http://localhost:3001
```

Para el navegador, esos son orígenes distintos porque cambia el puerto.

Importante: **CORS es una política del navegador**, no de React. Postman puede pegarle al backend sin problema y el browser puede bloquear igual.

#### Qué protege

CORS evita que cualquier sitio pueda hacer requests desde el navegador del usuario a otro dominio sin permiso explícito.

#### Cómo se configura en Express

Ejemplo pedagógico:

```js
import cors from 'cors';
import express from 'express';

const app = express();

app.use(cors({
  origin: 'http://localhost:3000',
  methods: ['GET', 'POST', 'PUT', 'DELETE'],
  credentials: true
}));

app.use(express.json());
```

Lectura:

```txt
backend dice: acepto requests desde este origin
browser revisa esa respuesta
si coincide, deja que React lea la respuesta
```

Gotcha importante: CORS no es autenticación. Que un origin está permitido no significa que cualquier request sea válido. Para seguridad necesitás sesión, token, roles y validación del lado backend.

---

### 7) Sesiones: HTTP no recuerda quién sos

HTTP es stateless: cada request es independiente.

```txt
POST /login -> OK, sos Ana
GET /compras -> ¿quién sos?
```

Para darle continuidad a esa conversación, usamos sesión. En esta materia se trabaja la idea de JWT guardado en `localStorage` para React puro.

Flujo mental:

```txt
usuario completa login
  -> React hace POST /login
  -> backend valida credenciales
  -> backend genera JWT
  -> React guarda token en localStorage
  -> requests siguientes mandan Authorization: Bearer <token>
  -> backend verifica firma y rol
```

#### Tipos de autorización vistos

**Bearer JWT**

```txt
Authorization: Bearer eyJhbGciOiJIUzI1NiIs...
```

- El backend firma el token.
- El cliente lo manda en cada request protegido.
- El servidor no necesita persistir el JWT para validarlo si tiene el secret.
- El payload puede leerse porque está codificado, no encriptado. Por eso no guardes datos sensibles ahí.

**Basic**

```txt
Authorization: Basic base64(usuario:password)
```

- Manda usuario/password codificados en cada request.
- Requiere HTTPS sí o sí.
- No es lo más recomendable para este caso.

**API Token**

```txt
Authorization: ApiToken abc123
```

- Suele persistirse en servidor/base.
- Puede revocarse desde backend.
- Es útil para integraciones sistema-sistema, no tanto para login de usuario final simple.

---

### 8) SessionContext + `localStorage`

La teoría de sesiones muestra una estructura muy alineada con lo que venimos construyendo: un `Context` para compartir el usuario autenticado.

Ejemplo adaptado a MegaSuper:

```jsx
import { createContext, useContext, useState } from 'react';
import { jwtDecode } from 'jwt-decode';

const SessionContext = createContext(null);

export function SessionProvider({ children }) {
  const [user, setUser] = useState(() => {
    const token = localStorage.getItem('token');
    if (!token) return null;

    try {
      const payload = jwtDecode(token);
      return payload.exp * 1000 < Date.now() ? null : payload;
    } catch {
      return null;
    }
  });

  const login = (token) => {
    localStorage.setItem('token', token);
    setUser(jwtDecode(token));
  };

  const logout = () => {
    localStorage.removeItem('token');
    setUser(null);
  };

  return (
    <SessionContext.Provider value={{ user, login, logout }}>
      {children}
    </SessionContext.Provider>
  );
}

export const useSession = () => useContext(SessionContext);
```

Puntos importantes:

- `useState(() => {...})` usa inicialización perezosa: lee `localStorage` una sola vez al montar.
- `login(token)` guarda token y actualiza estado React.
- `logout()` borra token y limpia usuario.
- `useSession()` es un custom hook para no exponer detalles del contexto.

#### Carrito vs sesión

```txt
carrito Clase 10 -> estado de UI, se pierde al refrescar
sesión Clase 11 -> estado de identidad, se reconstruye desde localStorage
```

No todo estado global merece persistencia. Persistir sin criterio también trae bugs: datos vencidos, inconsistencias y problemas de seguridad.

---

### 9) Interceptors y middleware: frontend y backend trabajando juntos

Una vez que existe token, no querés acordarte manualmente de agregarlo en cada request. Para eso sirven los interceptores de axios.

```js
apiClient.interceptors.request.use((config) => {
  const token = localStorage.getItem('token');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

apiClient.interceptors.response.use(null, (error) => {
  if (error.response?.status === 401) {
    localStorage.removeItem('token');
    window.location.href = '/login';
  }
  return Promise.reject(error);
});
```

Lectura:

```txt
antes de salir el request -> agrego token
si vuelve 401             -> token inválido/vencido, limpio sesión
```

Pero esto no alcanza. El backend también tiene que verificar:

```js
export function verificarToken(req, res, next) {
  const auth = req.headers.authorization;

  if (!auth?.startsWith('Bearer ')) {
    return res.status(401).json({ error: 'Token requerido' });
  }

  try {
    const token = auth.split(' ')[1];
    req.user = jwt.verify(token, process.env.JWT_SECRET);
    next();
  } catch {
    res.status(401).json({ error: 'Token inválido' });
  }
}
```

Esta es una de las ideas más importantes de toda la clase:

> El frontend mejora la experiencia; el backend garantiza la seguridad.

Si solo ocultás botones o rutas en React, no protegiste nada. Cualquiera puede llamar a la API directamente.

---

### 10) Rutas protegidas

`ProtectedRoute` es un componente que decide si una pantalla se renderiza o redirige.

```jsx
import { Navigate } from 'react-router-dom';
import { useSession } from '../contexts/SessionContext';

export function ProtectedRoute({ children, rolRequerido }) {
  const { user } = useSession();

  if (!user) {
    return <Navigate to="/login" replace />;
  }

  if (rolRequerido && user.rol !== rolRequerido) {
    return <Navigate to="/unauthorized" replace />;
  }

  return children;
}
```

Ejemplo MegaSuper:

```jsx
<Route
  path="/admin/productos"
  element={
    <ProtectedRoute rolRequerido="admin">
      <AdministrarProductos />
    </ProtectedRoute>
  }
/>
```

Esto sirve para UX: evita mostrar pantallas que el usuario no debería usar. Pero la API `/admin/productos` igual tiene que validar token y rol.

---

### 11) Context API: resolver prop drilling

En Clase 10 el carrito estaba levantado a `App` y bajaba por props:

```txt
App
  -> Layout
    -> Navbar recibe carrito
  -> ProductDetailPage recibe actualizarCarrito
  -> Checkout recibe carrito + limpiarCarrito
```

Eso fue correcto para aprender fundamentos. Primero se entiende props; después se justifica Context.

El problema aparece cuando el dato lo necesitan muchos componentes o está muy lejos en el árbol. Ahí aparece el **prop drilling**: pasar props por componentes intermedios que no las usan.

Context permite esto:

```txt
CarritoProvider
  -> cualquier descendiente llama useCarrito()
```

#### Tres pasos de Context

```txt
1. crear contexto
2. proveer contexto
3. consumir contexto con useContext
```

Ejemplo real del PR #4 de MegaSuper:

```jsx
import { createContext, useContext, useState } from 'react';

const CarritoContext = createContext(null);

export const CarritoProvider = ({ children }) => {
  const [carrito, setCarrito] = useState([]);

  const actualizarCarrito = (producto) => {
    setCarrito((prev) => [...prev, producto]);
  };

  const limpiarCarrito = () => {
    setCarrito([]);
  };

  return (
    <CarritoContext.Provider value={{ carrito, actualizarCarrito, limpiarCarrito }}>
      {children}
    </CarritoContext.Provider>
  );
};

export const useCarrito = () => useContext(CarritoContext);
```

Qué mejora:

```txt
antes: App pasa carrito por props
ahora: CarritoProvider expone carrito y operaciones
```

En `App.jsx`, el provider envuelve las rutas:

```jsx
<ThemeProvider theme={theme}>
  <CarritoProvider>
    <Routes>
      <Route path="/" element={<Layout />}>
        <Route index element={<Home />} />
        <Route path="/productos/:id" element={<ProductDetailPage />} />
        <Route path="/checkout" element={<Checkout />} />
      </Route>
    </Routes>
  </CarritoProvider>
</ThemeProvider>
```

Y los consumidores dejan de recibir props:

```jsx
const { carrito, actualizarCarrito } = useCarrito();
```

#### Criterio profesional

Context no reemplaza props. Context resuelve un problema concreto: compartir datos a través de muchos niveles o entre componentes alejados.

```txt
props   -> relación directa y explícita
context -> dato transversal del árbol
```

Si usás Context para todo, escondés dependencias y hacés más difícil seguir el flujo. No cambiemos un problema por otro.

---

### 12) Custom hooks: intención en vez de implementación

Un custom hook es una función que usa hooks de React y encapsula lógica reutilizable.

Ejemplos:

```txt
useCarrito()
useSession()
useOnlineStatus()
useProductos()
```

La ventaja no es solo "reutilizar código". La ventaja fuerte es que el componente pasa a expresar intención.

```jsx
const { carrito, limpiarCarrito } = useCarrito();
```

Eso se lee mejor que:

```jsx
const carritoContext = useContext(CarritoContext);
```

#### Ojo conceptual

El PDF remarca algo importante:

> Los custom hooks permiten compartir lógica con estado, no necesariamente compartir el mismo estado.

Ejemplo:

```jsx
function useOnlineStatus() {
  const [isOnline, setIsOnline] = useState(true);

  useEffect(() => {
    const handleOnline = () => setIsOnline(true);
    const handleOffline = () => setIsOnline(false);

    window.addEventListener('online', handleOnline);
    window.addEventListener('offline', handleOffline);

    return () => {
      window.removeEventListener('online', handleOnline);
      window.removeEventListener('offline', handleOffline);
    };
  }, []);

  return isOnline;
}
```

Si dos componentes llaman `useOnlineStatus()`, ambos reutilizan la lógica, pero cada llamada tiene su propio ciclo de hooks.

En cambio, `useCarrito()` parece compartir estado porque lee un Context común provisto por `CarritoProvider`.

```txt
custom hook solo -> comparte lógica
custom hook + context -> accede a estado compartido
```

---

### 13) CSS-in-JS: estilos como parte del componente

CSS-in-JS es un patrón donde los estilos se definen usando JavaScript en vez de archivos `.css` separados.

No es parte de React. React no te obliga a usarlo.

Bibliotecas vistas:

- `@emotion/react` / `@emotion/styled`;
- `styled-components`.

#### Qué problema intenta resolver

Con CSS tradicional, en una app grande puede pasar:

```txt
Navbar.jsx
Navbar.css
variables en index.css
clases globales
posibles nombres repetidos
```

CSS-in-JS busca acercar estructura y estilo:

```txt
componente + estilos que usa ese componente
```

Ejemplo real del PR #6 de MegaSuper:

```jsx
import styled from '@emotion/styled';
import { theme } from '../../theme.js';

const CartButton = styled.button`
  display: flex;
  align-items: center;
  color: ${theme.colors.primaryWhite};
  font-size: 1.25rem;
  background-color: transparent;
  border: none;
  padding: 0;
  cursor: pointer;
`;
```

Y después se usa como componente:

```jsx
<CartButton onClick={irACheckout}>
  <FaShoppingCart color="white" />
  <CartCount>{cantUnidades}</CartCount>
</CartButton>
```

También aparece un `theme.js`:

```js
export const theme = {
  colors: {
    primaryGreen: 'rgb(30, 126, 52)',
    secondaryGreen: 'rgb(72, 168, 90)',
    primaryOrange: 'rgb(255, 140, 0)',
    primaryWhite: 'rgb(250, 250, 250)',
    primaryGray: 'rgb(36, 36, 36)',
  },
  fonts: {
    primary: "'Poppins', sans-serif",
  },
};
```

Esto evita repetir colores sueltos por toda la app.

#### Tradeoff real

```txt
CSS separado
  + simple, estándar, fácil de aprender
  - puede crecer en globales y nombres repetidos

CSS-in-JS
  + estilos cerca del componente, props dinámicas, scoping más claro
  - más dependencia, más JS, posible ruido si el archivo crece demasiado
```

Criterio sano: si el equipo todavía está aprendiendo React, CSS separado está perfecto. CSS-in-JS suma cuando hay una necesidad real de encapsulamiento, theming o estilos dinámicos.

---

### 14) SDD en vivo: especificar antes de tocar

En la clase se mencionaron herramientas de SDD:

- **OpenSpec**: herramienta para trabajar especificaciones en proyectos ya empezados, especialmente útil en brownfield.
- **GitHub Spec Kit**: propuesta similar orientada a especificación y desarrollo guiado.
- **OpenCode**: agente de desarrollo asistido; se nombró como herramienta comparable a Claude/Copilot en ciertos flujos.

La idea de SDD no es "que la IA codee sola". La idea sana es:

```txt
entender problema
  -> escribir intención
  -> definir alcance
  -> listar tareas
  -> implementar
  -> verificar contra la especificación
```

Ejemplo real del PR #4 de MegaSuper: se escribió una especificación para resolver prop drilling con `CarritoContext`.

Problema declarado:

```txt
El carrito vive en App y se pasa manualmente por props.
Agregar nuevos componentes que usen carrito obliga a tocar cadenas intermedias.
```

Cambio propuesto:

```txt
crear CarritoContext
crear CarritoProvider
exportar useCarrito()
actualizar Navbar, ProductDetailPage y Checkout
```

Ese es el valor: antes de tocar archivos, queda claro qué se busca y qué NO se busca.

No objetivos del diseño:

- persistir carrito en `localStorage`;
- sincronizar carrito con backend;
- migrar a Redux/Zustand;
- cambiar reglas funcionales del carrito.

Eso es muy importante. Un buen cambio también dice qué deja afuera.

---

### 15) Gotchas reales de estas clases

1. **CORS no se arregla desde React**.
   - Si el navegador bloquea por CORS, el permiso lo tiene que dar el backend.
   - React puede cambiar URL o headers, pero no puede autorizarse a sí mismo.

2. **`localStorage` persiste, pero no es una caja fuerte**.
   - Sirve para prácticas y apps simples.
   - No guardes datos sensibles.
   - En producción, cookies `httpOnly` pueden ser más seguras, pero requieren más configuración.

3. **JWT no está encriptado**.
   - Header y payload se pueden decodificar.
   - La firma permite verificar que no fue modificado.
   - No pongas información sensible en el payload.

4. **Frontend no es seguridad**.
   - `ProtectedRoute` mejora UX.
   - El backend valida token y rol.

5. **Context no reemplaza todas las props**.
   - Props para relaciones directas.
   - Context para datos transversales.

6. **Custom hook no siempre significa estado compartido**.
   - Comparte lógica.
   - Comparte estado solo si internamente consume una fuente común, como Context.

7. **Polling necesita cleanup**.
   - Si usás `setInterval`, devolvé `clearInterval` desde `useEffect`.

8. **CSS-in-JS no es obligatorio**.
   - Es una herramienta más.
   - Si el componente queda enorme por mezclar JSX, lógica y estilos, también puede empeorar la legibilidad.

9. **SDD no reemplaza criterio técnico**.
   - Ayuda a ordenar intención, alcance y tareas.
   - El humano sigue definiendo qué vale la pena hacer y qué queda afuera.

---

### 16) Resumen mental de Clase 11 y 12

Si te preguntan "¿qué agregaron las clases 11 y 12 al bloque de React?", contestá:

> Agregaron el salto de una SPA con estado local a una app frontend más real. Vimos cómo integrar React con backend usando una capa de services y axios, cómo manejar loading/error/success, paginación y polling, por qué aparece CORS y cómo se configura desde Express. También vimos sesiones con JWT, `localStorage`, interceptores, middleware backend y rutas protegidas. Después profundizamos estado global con Context API, refactorizando el carrito de MegaSuper con `CarritoProvider` y `useCarrito`, vimos custom hooks para encapsular lógica, CSS-in-JS con Emotion para estilos encapsulados y SDD como forma de ordenar cambios en proyectos ya empezados.

Checklist para examen:

- Integración front-back = componentes llaman services, services llaman API.
- Axios permite centralizar `baseURL`, requests, errores e interceptores.
- Una pantalla integrada debe manejar loading, error y éxito.
- Paginación combina estado de UI + metadata del backend.
- Polling consulta periódicamente y necesita cleanup.
- CORS es política del navegador; se habilita desde backend.
- HTTP es stateless: sesión/JWT dan continuidad entre requests.
- JWT se firma; payload/header son decodificables, no secretos.
- `Authorization: Bearer <token>` manda credencial al backend.
- `localStorage` persiste entre recargas, pero no es almacenamiento seguro para datos sensibles.
- Interceptor de request agrega token; interceptor de response puede manejar 401.
- `ProtectedRoute` protege navegación de UI; backend protege datos reales.
- Context evita prop drilling cuando el dato es transversal.
- `useCarrito()` es custom hook sobre Context: mejora intención y encapsula detalles.
- Custom hooks comparten lógica; no siempre comparten estado.
- CSS-in-JS acerca estilos al componente, pero trae tradeoffs.
- SDD ayuda a definir problema, alcance, tareas y no-objetivos antes de tocar código.

---

## Clase 13 - Despliegue, CI/CD, contenedores y release

Fuentes usadas:
- PDF teoría: `Clases_Teoria/1C2026 - DDSW - MN - Clase 13 - Resumen escrito.pdf`
- Cache teoría escrito: `_cache_pdf_text/clase-13-teoria-resumen-escrito.md`
- Cache teoría presentación: `_cache_pdf_text/clase-13-teoria-resumen-ppt.md`

Nota de alcance:
- Esta clase integra **solo la parte teórica** de Clase 13.
- La parte práctica/UX de Clase 13 queda fuera del apunte por ahora, por pedido explícito.

Idea central:
> Hasta ahora construimos software: backend, persistencia, frontend, estado, integración y sesión. Clase 13 cierra el circuito preguntando algo distinto: ¿cómo hacemos para que una versión llegue a usuarios reales de forma controlada, repetible y con bajo riesgo?

El foco ya no está solamente en escribir código, sino en **ponerlo en producción** con criterio.

```txt
código
  -> tests / validaciones
  -> build / artefacto
  -> release
  -> deploy
  -> monitoreo / rollback si algo falla
```

Esta clase conecta directamente con temas que ya vimos:

- SemVer y releases de Clase 01.
- Git, ramas y PRs de Clase 02.
- Testing de Clase 06.
- Backend/frontend integrados de Clases 11 y 12.

---

### 1) Release: una versión disponible para usuarios

#### Problema

No alcanza con que el código esté mergeado o que funcione en la máquina del equipo.

Una cosa es tener código en el repositorio y otra muy distinta es tener una versión disponible para usuarios finales.

#### Concepto

Un **release** es el momento en que una versión del software se pone a disposición de los usuarios.

Puede ser:

- **completo**: se libera toda la aplicación;
- **parcial**: se libera solo para ciertas instancias, entornos, regiones o porcentajes de usuarios.

Cada release suele asociarse a una **versión**.

Ejemplo con versionado semántico:

```txt
MAJOR.MINOR.PATCH

2.1.0
│ │ └─ patch: corrección de bugs
│ └─── minor: nueva funcionalidad compatible
└───── major: cambio incompatible
```

#### Release vs deploy

No son exactamente lo mismo:

| Concepto | Pregunta que responde |
|---|---|
| Release | ¿Qué versión queda disponible para usuarios? |
| Deploy | ¿Cómo llevo esa versión a un entorno de ejecución? |
| Versión | ¿Cómo identifico ese estado del software? |

Podés deployar algo a un entorno de testing sin que sea un release productivo. Y podés tener un release gradual donde el deploy primero impacta a pocos usuarios.

#### Para examen

> Un release es la publicación de una versión del software para usuarios. El deploy es el proceso técnico de llevar esa versión a un entorno donde pueda ejecutarse.

---

### 2) CI/CD: automatizar confianza

#### Problema

Si cada integración depende de que alguien recuerde correr tests, revisar seguridad, empaquetar y desplegar manualmente, el proceso es frágil.

Cuanto más crece el equipo, más riesgo hay de:

- integrar código roto;
- desplegar una versión incorrecta;
- olvidarse pasos;
- detectar errores tarde;
- hacer rollback con presión y poca información.

#### Concepto

**CI/CD** agrupa prácticas para automatizar integración, validación, entrega y despliegue.

| Sigla | Nombre | Qué automatiza |
|---|---|---|
| CI | Continuous Integration | Validaciones al integrar código: tests, seguridad, convenciones. |
| CD | Continuous Delivery | Dejar una versión lista para desplegar en un entorno. |
| CD | Continuous Deployment | Desplegar automáticamente hasta producción si todo pasa. |

La diferencia importante:

```txt
Continuous Delivery    -> queda listo para desplegar, normalmente con aprobación humana
Continuous Deployment  -> si pasa el pipeline, llega automáticamente a producción
```

#### Pipeline mental

```txt
nueva rama
  -> commits
  -> push
  -> corre CI
      -> tests
      -> seguridad
      -> convenciones
  -> pull request
  -> review
  -> merge si está todo verde
  -> build artifact
  -> deploy a test o producción
```

El merge siempre existe. Lo que cambia según la estrategia es **a qué rama se mergea** y **qué dispara el deploy**.

| Estrategia | Idea |
|---|---|
| GitFlow | merge a `develop` para test; luego merge/tag hacia `main` para producción. |
| GitHub Flow | cambios chicos, PR a `main`, y `main` dispara deploy. |

#### Ventajas

- Menor riesgo: cambios chicos y validados continuamente.
- Feedback rápido: los errores aparecen cerca del cambio que los generó.
- Mayor velocidad: menos trabajo manual para llegar a producción.
- Calidad constante: las mismas validaciones corren siempre.
- Rollback más simple: si los cambios son chicos, volver atrás es menos traumático.

#### Para examen

> CI/CD no es “un script de deploy”. Es una forma de reducir riesgo automatizando validaciones, empaquetado y despliegue dentro del flujo de desarrollo.

---

### 3) Artefacto: no se despliega “mi carpeta”

#### Problema

Un error típico es pensar que desplegar es copiar archivos “como están en mi máquina”.

Eso es débil porque cada máquina puede tener versiones distintas de Node, dependencias, variables, sistema operativo o configuración.

#### Concepto

Un pipeline serio suele construir un **artefacto**: una unidad versionada y reproducible que representa lo que se va a desplegar.

Ejemplos:

- un build del frontend (`dist/`, `build/`);
- un paquete del backend;
- una imagen Docker;
- un archivo comprimido versionado;
- un release tag asociado a un commit.

Modelo mental:

```txt
código fuente + dependencias + configuración de build
  -> pipeline
  -> artefacto versionado
  -> deploy
```

La gracia es que el entorno de producción no “adivina” cómo correr la app: recibe algo construido y controlado.

---

### 4) Deployment: llevar la versión a un entorno

#### Concepto

El **deployment** es el proceso mediante el cual el código o artefacto desarrollado se traslada a un entorno de ejecución.

Ese entorno puede ser:

- desarrollo;
- testing;
- staging;
- producción.

En producción importan fuerte estas preguntas:

- ¿hay downtime?
- ¿cómo vuelvo atrás si falla?
- ¿puedo probar con pocos usuarios?
- ¿cuánta infraestructura necesito?
- ¿pueden convivir dos versiones al mismo tiempo?

---

### 5) Estrategias de deploy

No hay una estrategia “mejor” universal. Hay tradeoffs.

| Estrategia | Cómo funciona | Downtime | Rollback | Costo/Complejidad | Útil cuando... |
|---|---|---:|---|---|---|
| Recreate | Baja la versión vieja y sube la nueva. | Sí | Difícil | Bajo | Entornos de prueba o baja criticidad. |
| Rolling | Actualiza instancias de a poco. | Mínimo | Medio | Medio | Microservicios o varias instancias. |
| Blue-Green | Mantiene dos entornos: activo y nuevo. Cambia el tráfico cuando el nuevo está listo. | No | Muy fácil | Alto | Se necesita alta disponibilidad. |
| Canary | Envía poco tráfico a la versión nueva y escala si va bien. | No | Fácil | Medio/Alto | Servicios críticos con tráfico real. |

#### Recreate

```txt
V1 activa
  -> apagar V1
  -> levantar V2
```

Es simple, pero tiene downtime. Si falla, hay que volver a desplegar V1.

#### Rolling

```txt
V1 V1 V1
V2 V1 V1
V2 V2 V1
V2 V2 V2
```

Actualiza instancia por instancia. El sistema no cae entero, pero durante un tiempo conviven dos versiones.

Gotcha: si V1 y V2 no son compatibles entre sí, podés tener errores raros durante la transición.

#### Blue-Green

```txt
Blue  -> V1 activa
Green -> V2 lista

switch del load balancer:
Blue -> Green
```

Ventaja: rollback inmediato, porque Blue queda disponible.

Costo: duplicás infraestructura temporalmente.

#### Canary

```txt
90% tráfico -> V1
10% tráfico -> V2

si V2 funciona:
50% -> V2
100% -> V2
```

Sirve para validar con tráfico real sin exponer a todos los usuarios.

Si falla, el rollback puede ser tan simple como redirigir el tráfico nuevamente a V1.

---

### 6) Load balancer y health-check

En estrategias como Canary o Blue-Green aparece una pieza clave: el **load balancer**.

Su trabajo es repartir tráfico entre instancias y decidir a cuál enviar requests.

Para eso suele usar un endpoint de salud:

```txt
GET /health-check
```

Ese endpoint permite saber si una instancia está lista para recibir tráfico.

Modelo mental:

```txt
usuario
  -> load balancer
      -> instancia sana V1
      -> instancia sana V2
      -> no enviar tráfico a instancia caída
```

Esto conecta con algo que ya vimos en backend: un endpoint de healthcheck no está “de adorno”. En despliegue real puede decidir si una instancia entra o no al tráfico productivo.

---

### 7) Infraestructura: dónde vive el software

#### Concepto

La **infraestructura** es el conjunto de recursos físicos y virtuales que permiten ejecutar, alojar, escalar y mantener una aplicación.

Incluye cosas como:

- servidores;
- redes;
- balanceadores;
- bases de datos;
- almacenamiento;
- monitoreo;
- secretos y configuración;
- entornos de ejecución.

#### On-Premise vs Cloud

| Característica | On-Premise | Cloud |
|---|---|---|
| Costos iniciales | Altos: compra/alquiler de hardware. | Bajos: pago por uso. |
| Escalabilidad | Limitada y lenta. | Rápida y elástica. |
| Mantenimiento | Manual, en sitio. | Más automatizable. |
| Provisión | Días o semanas. | Minutos. |
| Ejemplos | Datacenter propio. | AWS, Azure, GCP. |

Cloud no significa “gratis” ni “mágico”. Significa que consumís infraestructura como servicio, con más elasticidad, pero también con nuevas responsabilidades: costos, seguridad, configuración y observabilidad.

---

### 8) Contenedores: empaquetar app + dependencias

#### Problema

La frase clásica:

> “En mi máquina anda.”

Ese problema aparece cuando desarrollo, testing y producción no tienen el mismo entorno.

#### Concepto

Un **contenedor** es una unidad estándar de software que empaqueta:

- la aplicación;
- dependencias;
- librerías;
- configuración necesaria;
- variables/entorno esperado.

Pero ojo: un contenedor **no incluye un sistema operativo completo**. Usa el kernel del host y aísla procesos.

Por eso suele ser más liviano que una máquina virtual.

Modelo mental:

```txt
contenedor
  -> app
  -> dependencias
  -> configuración
  -> proceso aislado
  -> comparte kernel del host
```

#### Ventajas

- Portabilidad: corre igual donde haya motor de contenedores compatible.
- Ligereza: no trae un SO completo por aplicación.
- Velocidad: arranque muy rápido.
- Aislamiento: los cambios de un contenedor no deberían afectar a otros.
- Escalabilidad: encaja bien con microservicios y pipelines CI/CD.

---

### 9) Docker: herramienta para construir y correr contenedores

#### Concepto

**Docker** es una plataforma para desarrollar, enviar y ejecutar aplicaciones dentro de contenedores.

Componentes principales:

| Componente | Qué es |
|---|---|
| Dockerfile | Archivo con instrucciones para construir una imagen. |
| Imagen | Plantilla inmutable a partir de la cual se crean contenedores. |
| Contenedor | Instancia en ejecución de una imagen. |
| Docker Hub / registry | Repositorio para publicar y descargar imágenes. |

Flujo mental:

```txt
Dockerfile
  -> docker build
  -> imagen
  -> docker run
  -> contenedor ejecutándose
  -> docker push
  -> registry
```

#### Imagen vs contenedor

Esta diferencia es MUY preguntable:

```txt
Imagen     = plantilla, receta, snapshot inmutable.
Contenedor = proceso corriendo creado desde esa imagen.
```

Podés tener muchos contenedores corriendo desde la misma imagen.

---

### 10) Contenedores vs máquinas virtuales

| Característica | Contenedores | Máquinas virtuales |
|---|---|---|
| Aislamiento | A nivel proceso / sistema operativo. | A nivel hardware virtualizado. |
| Sistema operativo | Comparten kernel del host. | Cada VM tiene su SO invitado. |
| Tamaño | Livianos, normalmente MB. | Más pesadas, normalmente GB. |
| Arranque | Muy rápido. | Más lento. |
| Uso típico | Microservicios, CI/CD, DevOps. | Apps legadas, aislamiento fuerte. |

No es que contenedores “reemplazan siempre” a VMs. Resuelven problemas distintos.

- Si necesitás mucha portabilidad y arranque rápido: contenedores.
- Si necesitás aislamiento fuerte a nivel sistema completo: VM.

---

### 11) Cómo se vería esto en MegaSuper

Si MegaSuper fuera a producción, el flujo razonable sería:

```txt
feature branch
  -> PR
  -> CI corre tests backend/frontend
  -> merge
  -> build frontend
  -> build backend o imagen Docker
  -> publicar artefacto/imagen
  -> deploy a staging
  -> validación
  -> release productivo
```

Y habría decisiones concretas:

- ¿El backend expone `/health-check` para el load balancer?
- ¿Dónde viven las variables de entorno de la API y la base de datos?
- ¿El frontend se sirve como archivos estáticos o dentro de un contenedor?
- ¿El backend y la base de datos están en la misma red privada?
- ¿La estrategia de deploy permite rollback rápido?
- ¿Los cambios de base de datos son compatibles con versiones anteriores?

Este es el punto importante: deploy no es “subir archivos”. Deploy es coordinar código, configuración, infraestructura, datos y riesgo.

---

### 12) Gotchas de examen y de proyecto real

1. **Confundir release con deploy**.
   - Release: versión disponible para usuarios.
   - Deploy: proceso técnico de llevarla a un entorno.

2. **Creer que CI/CD elimina la revisión humana**.
   - No. Automatiza validaciones, pero el criterio de diseño y negocio sigue siendo humano.

3. **Pensar que Docker es una VM liviana**.
   - No exactamente. El contenedor comparte kernel del host; una VM trae SO invitado completo.

4. **No pensar rollback antes de desplegar**.
   - Si no sabés cómo volver atrás, todavía no tenés una estrategia de despliegue madura.

5. **Romper compatibilidad entre versiones durante Rolling/Canary**.
   - Si V1 y V2 conviven, APIs y base de datos deben tolerar esa convivencia.

6. **Meter secretos dentro de la imagen**.
   - Una imagen debería ser portable; secretos/configuración sensible se inyectan por entorno.

---

### Resumen mental de la clase

Si te preguntan “¿qué aporta Clase 13?”, contestá:

> Clase 13 cierra el ciclo del desarrollo: después de construir y probar software, hay que liberarlo. Para eso aparecen release, versionado, CI/CD, artefactos, estrategias de deploy, infraestructura, contenedores y Docker. El objetivo no es solo llegar a producción, sino hacerlo de forma repetible, automatizada y con bajo riesgo.

Modelo mental completo:

```txt
desarrollo
  -> commit / PR
  -> CI valida
  -> merge
  -> build artifact / imagen
  -> CD prepara o ejecuta deploy
  -> estrategia de despliegue
  -> monitoreo
  -> rollback si falla
```

### Checklist de examen

Tenés que poder explicar:

- qué es un release;
- diferencia entre release, versión y deploy;
- qué automatiza CI;
- diferencia entre Continuous Delivery y Continuous Deployment;
- flujo típico de un pipeline CI/CD;
- qué es un artefacto;
- diferencias entre Recreate, Rolling, Blue-Green y Canary;
- qué rol cumple un load balancer;
- para qué sirve un health-check;
- qué es infraestructura;
- diferencias entre on-premise y cloud;
- qué es un contenedor;
- qué es Docker;
- diferencia entre Dockerfile, imagen, contenedor y registry;
- diferencias entre contenedores y VMs;
- por qué el rollback se piensa antes del deploy.

---


## Resumen para examen (si te queres salvar)

- Proceso: feature vs bug vs deuda tecnica + tickets.
- Arquitectura: estilos + capas y responsabilidades.
- HTTP/REST: protocolo, APIs, recursos, verbos, headers, body, cookies, status codes y restricciones REST.
- Errores: no es lo mismo 400 vs 404 vs 409 vs 422 vs 500.
- Middlewares: `(req, res, next)` para flujo normal; `(err, req, res, next)` para errores.
- `next(error)`: puente entre controller/service y error handler centralizado.
- Async: event loop, callbacks, promises, async/await, microtasks/macrotasks, `Promise.all` e I/O real.
- Git: ramas, merge, squash, rebase, GitFlow/GitHub Flow, PRs, tags y releases con criterio.
- Testing: unitarios (Jest) para dominio, integración (Supertest) para HTTP, mocks para aislar capas.
- Documentación: OpenAPI/Swagger como contrato vivo, servido con `swagger-ui-express`.
- Persistencia: MongoDB (NoSQL documental) + Mongoose como ODM. Schemas con validaciones declarativas, populate para referencias, soft delete, paginación en repository, aggregation pipeline para consultas complejas.
- Front inicial: HTML semántico, CSS, accesibilidad, DOM, eventos y separación entre estructura, presentación y comportamiento.
- React: CSR, componentes, JSX, props, state con `useState`, efectos con `useEffect`, renderizado condicional, formularios controlados, estado local/compartido/derivado, carrito levantado a `App`, integración front-back con services/axios, CORS, sesiones con `Context`, `localStorage`, JWT, interceptores y `ProtectedRoute`, Context API con `useCarrito`, custom hooks, CSS-in-JS, React Router (`BrowserRouter`, `Routes`, `Route`, `Outlet`, `Link`, `useParams`, `useNavigate`) y UI libraries como MUI/React Bootstrap.
- Despliegue: release/versionado, CI/CD, build artifact, estrategias de deploy (Recreate, Rolling, Blue-Green, Canary), infraestructura, health-check, contenedores, Docker e imagen vs contenedor.
