# CIT2008 - Template Base para Proyecto Semestral

Este es el template base para el proyecto web de la asignatura CIT2008. Proporciona una estructura completa de aplicación web full-stack con Node.js, Express, y un frontend en HTML/CSS/JS vanilla.

## Tabla de Contenidos

-   [Características](#características)
-   [Estructura del Proyecto](#estructura-del-proyecto)
-   [Pre-requisitos](#pre-requisitos)
-   [Instalación](#instalación)
-   [Scripts Disponibles](#scripts-disponibles)
-   [Gestión del servidor](#gestión-del-servidor)
-   [Herramientas de Calidad de Código](#herramientas-de-calidad-de-código)
-   [Comentarios finales](#comentarios-finales)

## Características

-   **Backend**: Servidor Express.js con estructura modular de rutas
-   **Frontend**: Aplicación web vanilla (HTML, CSS, JavaScript)
-   **API REST**: Endpoint de ejemplo con heartbeat
-   **Gestión de Procesos**: Configuración PM2 para producción
-   **Proxy Reverso**: Configuración Nginx incluida
-   **SSL**: Configuración automática con Let's Encrypt
-   **Calidad de Código**: ESLint, Stylelint, y HTMLHint configurados
-   **Despliegue Automatizado**: Script de setup completo para servidores Ubuntu

## Estructura del Proyecto

```
├── backend/                  # Servidor Express.js
│   ├── routes/               # Rutas de la API
│   │   ├── index.js          # Archivo principal de rutas
│   │   ├── heartbeat.js      # Endpoint de prueba
│   │   └── ...               # Archivos de desarrollo del backend
│   └── server.js             # Servidor principal
├── frontend/                 # Aplicación web frontend
│   ├── heartbeat/            # Página de prueba
│   │   ├── index.html        # HTML principal
│   │   ├── index.css         # Estilos
│   │   └── index.js          # JavaScript del cliente
│   └── ...                   # Archivos del desarrollo del front end
├── commons/                  # Configuraciones compartidas
│   ├── configs/              # Archivos de configuración
│   │   ├── site.config.js    # Configuración del sitio
│   │   ├── pm2.config.js     # Configuración PM2
│   │   └── nginx.template    # Template de Nginx
│   └── scripts/              # Scripts de automatización
│       └── setup.sh          # Script de configuración automática
├── package.json              # Dependencias y scripts
├── eslint.config.js          # Configuración ESLint
├── stylelint.config.mjs      # Configuración Stylelint
├── .htmlhintrc               # Configuración HTMLHint
└── .gitignore                # Archivos ignorados por Git
```

## Pre-requisitos

Usted debe tener su máquina en AWS preparada, esto significa:

-   La máquina está funcionando
-   Tiene una dirección IP fija asignada mediante ElasticIP
-   La dirección ip está vinculada al dominio exampledomain.cloud mediante la herramienta de registros de DNS indicada en clases
-   Ha configurado un usuario que pertenece al grupo de sudoers con acceso mediante contraseña
-   Ha configurado sus credenciales para acceder a GitHub

## Instalación

1. **Clona el repositorio**:

    ```bash
    git clone <url-del-repositorio> ~/www-group
    ```

2. **Ejecuta el script de setup**

    ```bash
    cd ~/www-group/commons/scripts
    ./setup.sh
    ```

3. **Comprobar funcionamiento correcto**

-   Ir a https://SXXGXX.www.exampledomain.cloud/heatbeat/index.html
-   Comprobar que la página abre
-   Comprobar que el api endpoint heartbeat funciona

## Scripts Disponibles

```bash
# Gestión del servidor (producción)
npm start          # Inicia con PM2
npm run restart    # Reinicia el proceso PM2
npm run stop       # Detiene el proceso PM2
npm run logs       # Muestra logs del servidor

# Herramientas de desarrollo
npm run lint       # Ejecuta todos los linters
npm run lint:html  # Valida archivos HTML
npm run lint:css   # Valida archivos CSS
npm run lint:js    # Valida archivos JavaScript
```

### Gestión del servidor

Si bien se ha disponibilizado múltiples comandos para gestionar el estado del servidor, **pm2** ha sido configurado de modo que ante un cambio en sus archivos dentro de la carpeta `backend` se realiza automáticamente un restart del servidor para disponibilizar inmediatamente sus cambios.

### Herramientas de Calidad de Código

Se ha disponibilizado 4 comandos para realizar la validación de calidad del código:

#### HTMLHint (HTML)

-   **Comando**: `npm run lint:html`
-   **Configuración**: `.htmlhintrc`

#### Stylelint (CSS)

-   **Comando**: `npm run lint:css`
-   **Configuración**: `stylelint.config.mjs`

#### ESLint (JavaScript)

-   **Comando**: `npm run lint:js`
-   **Configuración**: `eslint.config.js`

#### Revisión completa

-   **Comando**: `npm run lint`
-   Ejecuta secuencialmente los 3 linters de HTML, CSS, JS

## Comentarios finales

Este template está diseñado para ser utilizado como template en GitHub Classroom y ser extendido por los estudiantes. Se recomienda:

1. Mantener la estructura
2. Seguir atentamente las instrucciones de las entregas
3. Agregar nuevas funcionalidades (en especial respecto de la API) de forma modular
4. Seguir las convenciones de código establecidas
5. Documentar cambios significativos
