## URL

El gateway se encuentra desplegado en la siguiente URL: [https://sociounido-gateway.onrender.com](https://sociounido-gateway.onrender.com). Puedes acceder a esta URL para interactuar con los microservicios a través del gateway.

## Deploy

El gateway se despliega utilizando Docker. Para construir la imagen y ejecutar el contenedor, sigue estos pasos:

1. Asegúrate de tener Docker instalado en tu máquina.
2. Navega al directorio del gateway y ejecuta el siguiente comando para construir la imagen:
   ```bash
   docker build -t sociounido-gateway .
   ```
3. Una vez que la imagen esté construida, puedes ejecutar el contenedor con el siguiente comando:
   ```bash
    docker run -d -p 8080:8080 --env-file .env --name sociounido-gateway sociounido-gateway
    ```
    Esto iniciará el gateway en el puerto 8080, utilizando las variables de entorno definidas en el archivo `.env`.
4. Para detener el contenedor, puedes usar el siguiente comando:
5. ```bash
   docker stop sociounido-gateway
   ```
6. Para eliminar el contenedor, puedes usar el siguiente comando:
   ```bash
    docker rm sociounido-gateway
    ```
## Configuración

El gateway utiliza un archivo de configuración `krakend.json` para definir las rutas y la seguridad. Asegúrate de actualizar las variables de entorno en el archivo `.env` para que coincidan con tu configuración, especialmente `FIREBASE_PROJECT_ID` y `FRONTEND_URL`.

## CORS

El gateway está configurado para permitir solicitudes CORS desde el frontend definido en `FRONTEND_URL` y desde `http://localhost:3000` para desarrollo local. Asegúrate de actualizar esta configuración si tu frontend se despliega en una URL diferente.
