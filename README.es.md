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

### Opción A: GitHub Codespaces (recomendado)

GitHub Codespaces te da un entorno en la nube listo para usar, así que no
necesitas instalar Python, Git ni Docker en tu máquina.

Abre el repositorio en un codespace:

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/z2h-academy/student-analytics-starter)

O inicia uno desde la terminal, si tienes instalado GitHub CLI:

```bash
gh codespace create -r z2h-academy/student-analytics-starter
```

El primer arranque tarda unos minutos mientras GitHub construye el contenedor.
Cuando el editor se abra, espera a que aparezca el prompt de la terminal y
confirma que el repositorio está ahí:

```bash
pwd        # /workspaces/student-analytics-starter
ls data    # log_data  song_data
```

Después inicia el agente desde la raíz del repositorio:

```bash
opencode
```

> El repositorio no incluye una configuración `.devcontainer/`, así que el
> codespace usa la imagen por defecto. Si el detalle del entorno importa para
> tu sesión, ejecuta `devcontainer-info` en la terminal para ver qué imagen se
> está usando.

Para reutilizar el codespace más adelante, ábrelo de nuevo desde
<https://github.com/codespaces> o con `gh codespace code`. Las cuentas
gratuitas tienen una cuota mensual de horas de cómputo y almacenamiento;
detener el codespace cuando terminas evita que se consuma. Los codespaces se
eliminan automáticamente después de un período de retención (30 días por
defecto), y puedes borrar uno antes con `gh codespace delete`.

### Opción B: entorno local

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

> La preparación de la base de datos (PostgreSQL) no se cubre aquí: TUTOR te
> acompaña con ella desde los docs del proyecto cuando la sesión llega a ese
> paso.

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
