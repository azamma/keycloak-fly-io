# Keycloak Fly Deploy

Este repositorio automatiza el despliegue de un servidor Keycloak en Fly.io, conectado a una base de datos PostgreSQL.

## Pasos para desplegar

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/keycloak-fly-deploy.git
   cd keycloak-fly-deploy
   ```

2. Iniciar sesión en Fly.io:
   ```bash
   fly auth login
   ```

3. Crear y desplegar la aplicación:
   ```bash
   fly launch --no-deploy
   ```

4. Crear y conectar la base de datos PostgreSQL:
   ```bash
   fly postgres create
   fly postgres attach -a keycloak-fly-conexa keycloak-conexa-db
   ```

5. Configurar las variables de entorno:
   ```bash
   fly secrets set -a keycloak-fly-conexa KC_DB=postgres KEYCLOAK_ADMIN=admin KEYCLOAK_ADMIN_PASSWORD=admin KC_DB_URL="jdbc:postgresql://keycloak-conexa-db.flycast:5432/keycloak_fly_conexa?sslmode=disable" KC_DB_USERNAME=postgres KC_DB_PASSWORD=zamma KC_PROXY=edge
   ```

6. Desplegar la aplicación con memoria aumentada:
   ```bash
   fly deploy --vm-memory=2048
   ```
# keycloak-fly-io
