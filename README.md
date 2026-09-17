# Franklin Lorenzo Gutiérrez Cantor

**Full Stack Developer** · .NET · Angular · Flutter

Bogotá, Colombia · flgutierrezkantor@gmail.com · [github.com/Frankkantor348](https://github.com/Frankkantor348)

<!-- LinkedIn: if you have a profile, add the link above separated by · / si tienes perfil, añade el enlace arriba separado por · -->

Full stack developer with 2+ years building web and mobile applications, focused on microservices
architecture, continuous integration and automation. I currently build and maintain an institutional
system at the National Police of Colombia (Bogotá).

---

## Featured project · JobsHunterBot

A job-hunting bot that runs unattended on GitHub Actions —no server, no machine left switched on—
and pings me on Telegram whenever a posting matches my profile.

**What it does, with numbers measured on real runs**

| Metric | Value |
| --- | --- |
| Job sources integrated | 10 public APIs (Get on Board, Adzuna, Jobicy, Himalayas, Working Nomads, RemoteOK, Arbeitnow, Trudvsem…) |
| Offers analysed per run | ~1,600 |
| Matches for my stack | ~220 after filtering freshness, technologies and location |
| Stale postings discarded | 364 per run (7-day freshness window) |
| Alerts delivered | 10 per run, twice a day |
| Delivery failures | 0 |
| Run duration | ~90 seconds |

**Engineering decisions behind it**

- **Idempotency without a database**: the history of what has already been sent lives in a JSON file
  preserved between runs by the GitHub Actions cache, so the same posting never reaches me twice.
- **Normalising 10 different schemas** into one model: epoch dates (seconds and milliseconds), ISO
  dates and date-only values; heterogeneous location fields; dirty HTML descriptions; Cyrillic
  titles.
- **Priority engine**: every posting is classified by country bucket and geography, with per-bucket
  quotas and a guaranteed alert for each country I care about.
- **Resilience**: each source is isolated, so when one fails or blocks the runner's IP the bot keeps
  going. It retries with backoff on 429/503 and trips a circuit breaker when the AI quota runs out.
  The alert goes out anyway: graceful degradation, never a lost run.
- **AI layer over the Gemini REST API (no SDK)**: automatic discovery of the available model, a
  prompt with strict rules —no inventing experience; respect the real levels declared in my CV— and
  tolerant parsing of malformed answers.
- **Careful delivery**: HTML-escaped messages and explicit handling of Telegram's 4,096-character
  limit, trimming by priority so the link to the posting is never lost.
- **Security and judgement**: credentials stored as Actions secrets, `.env` kept out of version
  control, API keys always in headers and never in URLs, and no application is ever sent without a
  human reviewing it.

*The repository is private because it contains my personal data; I am happy to walk through it or
grant access during a hiring process.*

---

## Stack

- **Backend**: C# / .NET Core, ASP.NET Core, CQRS, REST APIs, Entity Framework
- **Frontend**: Angular, TypeScript, JavaScript, Razor
- **Mobile**: Flutter / Dart (iOS and Android)
- **Databases**: SQL Server (data modelling and query tuning), PostgreSQL, Firebase, SQLite
- **Architecture and messaging**: microservices, Clean Architecture, RabbitMQ, Kafka
- **DevOps**: GitHub Actions, GitLab CI, Azure DevOps, Azure, Render, Docker and Docker Compose (intermediate)
- **Security**: JWT, RBAC, vulnerability analysis (personal training)
- **Tooling**: Git, Swagger/OpenAPI, Postman, Visual Studio, VS Code

## Experience

**Full Stack Developer / Microservices Architect** — National Police of Colombia, Bogotá · *present*

- Designed and implemented a microservices architecture for an institutional system, improving
  scalability by **40 %**.
- Built the Angular front end and the .NET back end using the CQRS pattern, deploying the services in
  Docker containers.
- Tuned high-performance SQL Server queries.
- Implemented JWT authentication and role-based access control (RBAC).
- Coordinated continuous integration with GitHub Actions and documented the APIs with Swagger.

**Mobile Developer — Flutter** — personal projects · *present*

- Cross-platform application (iOS/Android) built with Dart and Flutter for the local retail sector.
- Integrated with a microservices back end over REST and WebSockets.
- Local storage with SQLite and synchronisation against a remote database.

## Projects

- **EduTech Platform** — course and grading management platform for educational institutions.
  Angular, .NET, SQL Server, JWT.
- **VecinoApp** — mobile app connecting small local shops with neighbours through geolocation and
  reviews. Flutter, .NET 8, SQL Server, microservices.
- **Authentication service** — centralised authentication and authorisation for several enterprise
  applications. JWT, Docker.

## Education and languages

- **Software Development Technology** — SENA, 2024
- **Software Engineering** — Universidad Iberoamericana, in progress
- Spanish (native) · **English A2** (technical reading, actively improving) · **Russian B1**

## How I work

I automate the repetitive work before anyone asks, I write down every technical decision, and I
prefer a system that fails in a controlled way and tells me about it over one that looks perfect and
breaks silently. Everything I publish runs with continuous integration from the first commit.

---

## Español

**Full Stack Developer** · .NET · Angular · Flutter

Bogotá, Colombia · flgutierrezkantor@gmail.com · [github.com/Frankkantor348](https://github.com/Frankkantor348)

Desarrollador full stack con más de 2 años construyendo aplicaciones web y móviles, con foco en
arquitectura de microservicios, integración continua y automatización. Actualmente desarrollo y
mantengo un sistema institucional en la Policía Nacional (Bogotá).

### Proyecto destacado · JobsHunterBot

Bot de búsqueda de empleo que corre solo en GitHub Actions —sin servidor propio y sin tener el equipo
encendido— y me avisa por Telegram cuando aparece una oferta que encaja con mi perfil.

**Qué hace, con números medidos en ejecuciones reales**

| Dato | Valor |
| --- | --- |
| Fuentes integradas | 10 APIs públicas (Get on Board, Adzuna, Jobicy, Himalayas, Working Nomads, RemoteOK, Arbeitnow, Trudvsem…) |
| Ofertas analizadas por ejecución | ~1.600 |
| Coincidencias con mi stack | ~220 después de filtrar vigencia, tecnologías y ubicación |
| Descartadas por antigüedad | 364 por ejecución (ventana de 7 días) |
| Alertas entregadas | 10 por ejecución, dos veces al día |
| Fallos de entrega | 0 |
| Duración de una ejecución | ~90 segundos |

**Decisiones de ingeniería que resuelve**

- **Idempotencia sin base de datos**: el historial de lo ya enviado vive en un JSON que se conserva
  entre ejecuciones con la caché de GitHub Actions, así que nunca me llega la misma oferta dos veces.
- **Normalización de 10 esquemas distintos** a un modelo único: fechas en epoch (segundos y
  milisegundos), ISO y fechas sin hora; ubicaciones heterogéneas; descripciones en HTML sucio;
  títulos en cirílico.
- **Motor de prioridad**: cada oferta se clasifica por frente y país, con cupos por frente y una
  alerta garantizada por cada país que me interesa.
- **Resiliencia**: cada fuente está aislada, de modo que si una falla o bloquea la IP del runner el
  bot continúa con las demás. Incluye reintentos con espera creciente ante 429/503 y un
  cortacircuitos cuando se agota la cuota de la IA. La alerta se entrega igual: degradación elegante,
  ninguna ejecución perdida.
- **Capa de IA sobre la API REST de Gemini (sin SDK)**: descubrimiento automático del modelo
  disponible, prompt con reglas estrictas —prohibido inventar experiencia; respetar los niveles
  reales declarados en mi CV— y análisis tolerante a respuestas con formato roto.
- **Entrega cuidada**: mensajes en HTML escapado y control explícito del límite de 4.096 caracteres
  de Telegram, con recorte por prioridad para no perder nunca el enlace de la oferta.
- **Seguridad y criterio**: credenciales como *secrets* de Actions, `.env` fuera del control de
  versiones, claves siempre en cabeceras y nunca en la URL, y ninguna postulación se envía sin
  revisión humana.

*El repositorio es privado porque contiene mis datos personales; puedo mostrarlo o compartir acceso
durante un proceso de selección.*

### Stack

- **Backend**: C# / .NET Core, ASP.NET Core, CQRS, APIs REST, Entity Framework
- **Frontend**: Angular, TypeScript, JavaScript, Razor
- **Móvil**: Flutter / Dart (iOS y Android)
- **Bases de datos**: SQL Server (modelado y optimización de consultas), PostgreSQL, Firebase, SQLite
- **Arquitectura y mensajería**: microservicios, Clean Architecture, RabbitMQ, Kafka
- **DevOps**: GitHub Actions, GitLab CI, Azure DevOps, Azure, Render, Docker y Docker Compose (nivel intermedio)
- **Seguridad**: JWT, RBAC, análisis de vulnerabilidades (formación personal)
- **Herramientas**: Git, Swagger/OpenAPI, Postman, Visual Studio, VS Code

### Experiencia

**Desarrollador Full Stack / Arquitecto de Microservicios** — Policía Nacional, Bogotá · *actualidad*

- Diseñé e implementé una arquitectura de microservicios para un sistema institucional, mejorando la
  escalabilidad en un **40 %**.
- Desarrollé el frontend en Angular y el backend en .NET con patrón CQRS, desplegando los servicios en
  contenedores Docker.
- Optimicé consultas de alto rendimiento en SQL Server.
- Implementé autenticación con JWT y control de acceso basado en roles (RBAC).
- Coordiné la integración continua con GitHub Actions y documenté las APIs con Swagger.

**Desarrollador Mobile — Flutter** — proyectos personales · *actualidad*

- Aplicación multiplataforma (iOS/Android) con Dart y Flutter para el sector comercial local.
- Integración con un backend de microservicios mediante REST y WebSockets.
- Almacenamiento local con SQLite y sincronización con base de datos remota.

### Proyectos

- **EduTech Platform** — plataforma de gestión de cursos y calificaciones para instituciones
  educativas. Angular, .NET, SQL Server, JWT.
- **VecinoApp** — app móvil que conecta pequeños comercios con vecinos mediante geolocalización y
  reseñas. Flutter, .NET 8, SQL Server, microservicios.
- **Servicio de autenticación** — autenticación y autorización centralizada para varias aplicaciones
  empresariales. JWT, Docker.

### Educación e idiomas

- **Tecnología en Desarrollo de Software** — SENA, 2024
- **Ingeniería de Software** — Universidad Iberoamericana, en curso
- Español nativo · **Inglés A2** (lectura técnica, en mejora continua) · **Ruso B1**

### Cómo trabajo

Automatizo lo repetitivo antes de que me lo pidan, dejo por escrito cada decisión técnica y prefiero
un sistema que falle de forma controlada y avise a uno que parezca perfecto y se caiga en silencio.
Todo lo que publico corre con integración continua desde el primer commit.

---

## Русский

**Fullstack-разработчик** (.NET · Angular · Flutter) из Боготы, Колумбия. Более 2 лет опыта в веб- и
мобильной разработке: микросервисы, CI/CD и автоматизация. Сейчас развиваю и поддерживаю
внутреннюю систему в Национальной полиции Колумбии (Богота).

**Проект — JobsHunterBot**: бот поиска работы, который работает без сервера в GitHub Actions и
присылает подходящие вакансии в Telegram. Интегрирует **10 открытых API**, приводит 10 разных схем
к одной модели, анализирует ~1.600 вакансий за запуск, отбрасывает 364 устаревших объявления
(окно 7 дней) и отправляет 10 уведомлений два раза в день без сбоев примерно за 90 секунд.
Идемпотентность без базы данных, изоляция источников, повторные попытки при 429/503 и
предохранитель при исчерпании квоты ИИ: уведомление приходит всегда.

Стек: C#/.NET Core, Angular, Flutter/Dart, SQL Server, PostgreSQL, RabbitMQ, Kafka, Docker,
GitHub Actions, Azure. Языки: испанский (родной), английский (A2), русский (B1).
