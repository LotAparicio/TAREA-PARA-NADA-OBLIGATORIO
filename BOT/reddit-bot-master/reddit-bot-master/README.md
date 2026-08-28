# Reddit Bot Automation CLI 

## Descripción del Proyecto
Este proyecto es un bot modular automatizado para Reddit desarrollado en Python. Permite la ejecución de tareas automatizadas en la plataforma como creación de publicaciones, interacción con comentarios, envío de mensajes directos, gestión de votos y seguimiento de usuarios, utilizando persistencia de datos SQLite para evitar duplicidad de acciones y mantener un registro estructurado.

### Justificación de la Necesidad
Elegimos este proyecto porque responde a la necesidad real de automatizar tareas repetitivas de interacción y moderación dentro de comunidades de Reddit. Desde el punto de vista de la Ingeniería de Software, permite estructurar un sistema extensible de acciones de red, manejo seguro de credenciales y almacenamiento persistente local.

---

## Seleccion de Metodologia de Desarrollo

### Enfoque Seleccionado: Metodología Ágil (Kanban)

**Justificación:**
1. **Duración y Flexibilidad:** Dado el marco de tiempo reducido de la práctica, un enfoque ágil nos permite trabajar con entregas incrementales y priorizar los módulos del bot de forma independiente.
2. **Estructura Modular:** Al estar el proyecto dividido en acciones individuales (comentarios, posts, votos, mensajes), Kanban facilita asignar cada funcionalidad a un integrante del equipo mediante *Issues* en GitHub Projects.
3. **Adaptabilidad:** Permite ajustar los requisitos y resolver fallos detectados durante las pruebas unitarias sin romper la planificación general.

---

## Historias de Usuario (User Stories)

* **HU-01: Autenticación y Credenciales**
  * **Como** desarrollador del bot,
  * **Quiero** validar y cargar las credenciales de Reddit mediante variables/archivos de configuración,
  * **Para** garantizar conexiones seguras a los servicios de la plataforma.

* **HU-02: Gestión de Interacciones y Acciones**
  * **Como** usuario del bot,
  * **Quiero** ejecutar acciones automatizadas (comentar, votar, publicar, enviar DMs),
  * **Para** automatizar la presencia en comunidades específicas de Reddit.

* **HU-03: Persistencia y Registro de Datos**
  * **Como** administrador del bot,
  * **Quiero** guardar el historial de interacciones en una base de datos local (SQLite),
  * **Para** evitar duplicar interacciones y llevar un control de auditoría.

* **HU-04: Pruebas y Validación**
  * **Como** ingeniero de calidad,
  * **Quiero** contar con un conjunto de pruebas unitarias con Pytest,
  * **Para** verificar que la lógica de validación e entrada funcione sin errores.

---

## Arquitectura del Proyecto
reddit-bot-master/
├── bot/
│   ├── actions/      # Módulos de acciones (comment, post, vote, dm, follow)
│   ├── utils/        # Validadores, parser de entradas, credenciales
│   ├── database.py   # Control de base de datos SQLite
│   └── bot.py        # Motor principal del bot
├── tests/            # Pruebas unitarias automatizadas (pytest)
├── main.py           # Punto de entrada ejecutable CLI
├── config.example.yaml
└── requirements.txt

---

## Instrucciones de Ejecución

1. Clonar el repositorio:
   ```bash
   git clone <URL_DE_TU_REPOSITO>
   cd reddit-bot-master

pip install -r requirements.txt
pytest
python main.py

---

### 2. Tareas para tu Tablero en *GitHub Projects*
Para cumplir con la **Fase de Planeación**, entra a la pestaña **Projects** en tu repositorio de GitHub, crea un proyecto tipo **Board (Kanban)** y crea estas 4 tarjetas en la columna *To Do* / *Por Hacer* (asigna a los miembros de tu equipo en cada una):

1. **[HU-01] Configuración del Entorno y Credenciales** (Asignar a Integrante 1)
2. **[HU-02] Implementación de Módulos de Acciones (Bot Actions)** (Asignar a Integrante 2)
3. **[HU-03] Configuración de la Base de Datos SQLite** (Asignar a Integrante 3)
4. **[HU-04] Elaboración de Pruebas Unitarias y Documentación** (Asignar a Integrante 4)

---

### 3. Diagrama para la Fase de Modelado (Mermaid / Draw.io)
Para subir la imagen que pide la guía en la sección de **Modelado**:

1. Entra a [draw.io](https://app.diagrams.net/).
2. Da clic en **Arrange > Insert > Advanced > Mermaid**.
3. Pega este código para que te genere el diagrama automáticamente:

```mermaid
graph TD
    A[Usuario / CLI] -->|Ejecuta main.py| B[Parser & Validadores]
    B -->|Verifica Credenciales| C[Bot Core Engine]
    C -->|Consulta / Guarda Estado| D[(SQLite Database)]
    C -->|Ejecuta Acción| E{Acciones del Bot}
    E -->|Comment| F[Reddit API / Web]
    E -->|Post| F
    E -->|Vote| F
    E -->|DM| F
    C -->|Genera Reporte| G[Ghost Logger / Reportes
  
# Retrospectiva del Proyecto - Práctica 1 🔄

### 1. ¿Qué funcionó bien?
* La arquitectura modular en la carpeta `bot/actions/` facilitó la separación de responsabilidades y la integración de nuevas características.
* El uso de GitHub Projects nos ayudó a distribuir las tareas de manera transparente entre los integrantes del equipo.
* La inclusión de pruebas unitarias (`pytest`) permitió validar la robustez de los módulos antes de realizar commits principales.

### 2. ¿Qué no funcionó o generó retrasos?
* Las configuraciones iniciales de entorno y el manejo de credenciales generaron pequeñas inconsistencias entre los miembros del equipo.
* La resolución de conflictos menores de Git al momento de sincronizar los archivos compilados del paquete `__pycache__`.

### 3. ¿Qué mejoras implementaremos para el siguiente proyecto?
* Configurar adecuadamente el archivo `.gitignore` desde la primera sesión para evitar subir archivos caché innecesarios.
* Establecer convenciones de mensajes de commit más estandarizadas vinculadas directamente al número de Issue de GitHub.
