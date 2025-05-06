# Challenge App

Un microservicio sencillo en Spring Boot para realizar cálculos y registrar operaciones, respaldado por PostgreSQL, y empaquetado con Docker y Docker Compose.

---

## Tabla de Contenidos

* [Requisitos Previos](#requisitos-previos)
* [Configuración](#configuración)
* [Desarrollo Local](#desarrollo-local)
* [Generar imagen con Docker Compose](#generar-imagen-con-docker-compose)
* [Publicar imagen a DockerHub](#publicar-imagen-a-dockerhub)
* [Ejecución con Docker Compose](#ejecución-con-docker-compose)
* [Colección de Postman](#colección-de-postman)
* [Imagen en DockerHub](#imagen-en-dockerhub)
* [Endpoints de la API](#endpoints-de-la-api)
* [Credenciales de Base de Datos](#credenciales-de-base-de-datos)

---

## Requisitos Previos

* Docker y Docker Compose instalados
* Java 21 (para desarrollo local)
* Maven (para compilar localmente)
* Cliente de PostgreSQL (por ejemplo, DBeaver)

---

## Configuración

Las variables de entorno se definen en `docker-compose.yml` y se consumen en `application.yml`.

---

## Desarrollo Local

Si prefieres ejecutar la aplicación sin Docker:

1. Asegúrate de tener PostgreSQL instalado en tu máquina (puede usar puerto 5433 para evitar conflictos).
2. Ajusta las variables de entorno o edita `application.yml`:

   SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5433/challenge
   SPRING_DATASOURCE_USERNAME=postgres
   SPRING_DATASOURCE_PASSWORD=1234

3. Compila y ejecuta con Maven:

   mvn clean install
   mvn spring-boot:run

---

## Generar imagen con Docker Compose

1. Clona este repositorio.

   https://github.com/JeanPaucar/ChallengeTenpo

2. Comandos para generar imagen

   docker build -t <TU_USUARIO_DOCKERHUB>/challenge-app:1.0 .

3. Verificar que las imagenes estén creadas en Docker Desktop

---

## Publicar imagen a DockerHub

1. Se ejecuta los siguientes comandos.

   docker tag challenge-app:latest <TU_USUARIO_DOCKERHUB>/challenge-app:1.0

   docker push <TU_USUARIO_DOCKERHUB>/challenge-app:1.0

---

## Ejecución con Docker Compose

1. Descargar imagen del DockerHub:
   [jeanpier39/challenge-app en DockerHub](https://hub.docker.com/r/jeanpier39/challenge-app/tags)

2. Para descargarla:

    docker pull jeanpier39/challenge-app:1.0

3. Desde la raíz del proyecto, ejecuta:
   docker-compose up -d

4. Verifica los contenedores en ejecución:
   docker ps

5. La API estará disponible en `http://localhost:8080`.

---

## Colección de Postman

Importa la carpeta `postman` para probar los endpoints de la API.

* Nombre de la colección: **RETO TENPO**

---

## Imagen en DockerHub

La imagen está publicada en Docker Hub:

[jeanpier39/challenge-app en DockerHub](https://hub.docker.com/r/jeanpier39/challenge-app/tags)

Para descargarla:
docker pull jeanpier39/challenge-app:1.0

---

## Endpoints de la API

| Método | Ruta                          | Descripción                                      |
| ------ | ----------------------------- | ------------------------------------------------ |
| POST   | `/api/calculate`              | Calcula la suma de `num1 + num2` con porcentaje. |
| GET    | `/api/logs?page={p}&size={s}` | Obtiene logs paginados (página y tamaño).        |

**Ejemplo de payload**:

```json
{
  "num1": 10,
  "num2": 20
}
```

---

## Credenciales de Base de Datos

* **Base en Docker**

    * URL: `jdbc:postgresql://postgres:5432/challenge`
    * Usuario: `user`
    * Contraseña: `pass`

* **Base local**

    * URL: `jdbc:postgresql://localhost:5433/challenge`
    * Usuario: `postgres`
    * Contraseña: `1234`

