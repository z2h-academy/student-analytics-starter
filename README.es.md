[English](README.md) | **Español**

# Analytics Starter — Espacio de trabajo del estudiante

Este es tu espacio de trabajo para el proyecto **Analytics Starter**: tu primer
data warehouse de punta a punta.

- **Ruta de trabajo:** `/workspaces/student-analytics-starter` (Codespaces o VM)
- **Página del proyecto:** https://z2h-academy.com/es/roadmap/analytics-starter
- **Contenido de referencia:** privado. TUTOR lo lee y te guía; no necesitas
  clonarlo.

## Qué es este repo

Este repo entrega el **dataset sintético** del proyecto y el espacio de
trabajo donde construyes el pipeline:

- `data/`: las fuentes de Melodix (160 archivos JSON de canciones y 30 archivos
  de log diarios).
- Todo lo demás se construye durante el proyecto con la guía de TUTOR: el
  esquema en estrella de PostgreSQL (`songplays` + cuatro dimensiones), el ETL
  idempotente en Python y el notebook de verificación.

La implementación de referencia no se distribuye aquí: TUTOR la lee y te ayuda
a construir tu propia versión, paso a paso.

### El dataset

| Fuente | Ruta | Archivos | Grano |
|---|---|---|---|
| Catálogo de canciones | `data/song_data/<A>/<B>/<C>/<song_id>.json` | 160 | una canción por archivo |
| Actividad de la app | `data/log_data/2025/01/2025-01-01-events.json` | 30 | un evento por línea (JSONL) |

El dataset es totalmente sintético (CC0), construido en UTC a partir de una
semilla fija y versionado: forma parte del repositorio, así que no lo generas.
No lo edites. Todos los conteos del proyecto (8.248 eventos, 7.061 `NextSong`,
4.544 emparejados) provienen exactamente de estos archivos.

## Cómo empezar

```bash
cd /workspaces/student-analytics-starter
opencode
```

Pide a TUTOR que inicie el proyecto **Analytics Starter**. La primera respuesta
es la base teórica (Melodix, esquema en estrella, grano, claves), seguida de un
checkpoint. Después del checkpoint, TUTOR presenta el plan del proyecto y
pregunta si quieres ejecutarlo de forma automática o manual.

> No clones ni copies el contenido de referencia: es privado y se accede solo a
> través del harness.

## Requisitos

| Requisito | Cómo verificar |
|---|---|
| Python 3.9+ (3.11+ para pandas 3.x) | `python3 --version` |
| PostgreSQL 12+ (validado en 16) | `psql --version` o `pg_isready` |
| Git | `git --version` |
| Docker (opcional, para correr PostgreSQL en local) | `docker --version` |

## Qué vas a aprender

- Modelar un esquema en estrella y elegir el grano de la tabla de hechos.
- Usar claves naturales y una clave subrogada de identidad sin romper la
  idempotencia.
- Construir un ETL que se pueda reejecutar con seguridad.
- Verificar una carga con conteos, cobertura de emparejamiento e integridad
  referencial.
- Defender cada decisión de modelado con evidencia.

## Reglas del repo

- Nunca comitees `.env` ni `.venv`.
- `data/` está versionado: mantenlo sin modificar, para que `git status` quede
  limpio.
- El espacio de trabajo es tuyo: construye los scripts durante las sesiones.
- Mantén el proyecto en `/workspaces/student-analytics-starter`.
