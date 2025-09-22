# 🚀 Infraestructura en Docker

Este repositorio contiene la **infraestructura base en Docker** para proyectos en **Python/Django**.  
Incluye **PostgreSQL 15** como motor de base de datos principal y **pgAdmin 4** para su administración vía navegador.

Está diseñado para funcionar tanto en **entornos locales de desarrollo** como en un **VPS en producción**, con volúmenes persistentes y buenas prácticas de seguridad, backups y logs.

---

## 📦 Servicios incluidos

- 🐘 **PostgreSQL 15** – Base de datos relacional.
- 🖥 **pgAdmin 4** – Cliente web para administrar Postgres (`http://localhost:5050`).
- 📂 **Volúmenes persistentes** – Para mantener los datos aunque se reinicien los contenedores.
- 📑 **Backups** – Carpeta dedicada para respaldos de bases de datos.
- 📝 **Logs** – Carpeta dedicada para registros de los servicios.
- 🔜 **Soporte futuro para SQL Server, Redis u otros servicios**.

---

## ⚙️ Requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

---

## 🚀 Cómo usar

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/gcboot/infraestructura.git
   cd infraestructura
   ```

2. Clonar el repositorio:
   ```bash
   cp .env.example .env
   ```
3. Configurar las variables en .env:

   ```env
   POSTGRES_USER=admin_user
   POSTGRES_PASSWORD=super_secret
   PGADMIN_DEFAULT_EMAIL=admin@local.com
   PGADMIN_DEFAULT_PASSWORD=pgadmin_pass

   ```

4. Levantar los servicios:
   ```bash
   docker compose up -d
   ```
5. Acceder a los servicios:

   - pgAdmin → http://localhost:5050

   - Postgres → localhost:5432
  
---

## Estructura del proyecto

    ```bash
        infraestructura/
        │── backups/        # Copias de seguridad de las bases de datos
        │── logs/           # Archivos de logs de los servicios
        │── .env            # Variables de entorno (no se sube a git)
        │── .env.example    # Plantilla de variables de entorno
        │── .gitignore      # Archivos a ignorar en Git
        │── docker-compose.yml  # Definición de servicios en Docker

    ```
---

## Buenas Prácticas

   - Nunca subir el archivo .env → contiene credenciales.
   - Usar backups/ para respaldos automáticos (pg_dump).
   - Revisar logs/ en caso de errores en los contenedores.
   - Mantener contraseñas seguras y diferentes en desarrollo/producción.
