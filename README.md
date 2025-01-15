## Tarea 10

***Puntos de la tarea***

  - Creación estructura docker-compose odoo
  - Creación estructura docker-compose postgresSQL
  - Creación estructura docker-compose PgAdmin
  - Verificación instalación odoo
  - Verificación instalación PgAdmin



1. ***Para instalar el servicio de odoo en el docker compose ponemos lo siguiente***
     ```
     web:
    image: odoo:17.0
    container_name: odooWebContainer
    restart: unless-stopped
    depends_on:
      - db
    ports:
      - "8069:8069"
    environment:
      HOST: db
      USER: odoo
      PASSWORD: myodoo
    volumes:
      - odoo-web-data:/var/lib/odoo
     ```

2. ***Despues para el postgres añadimos esto***
   ```
     db:
    image: postgres:15
    container_name: postgresSQLContainer
    restart: unless-stopped
    environment:
      POSTGRES_DB: postgres
      POSTGRES_PASSWORD: myodoo
      POSTGRES_USER: odoo
    volumes:
      - odoo-db-data:/var/lib/postgresql/data
    ports:
      - "5432:5432"
   ```


3. ***Para instalar el pgadmin necesitamos lo siguiente***
   ```
    pgadmin:
      restart: unless-stopped
      image: dpage/pgadmin4:latest
      container_name: PgAdminContainer
      depends_on:
        - db
      ports:
        - "5050:80"
      environment:
        PGADMIN_DEFAULT_EMAIL: jcaobaqueiro@gmail.com
        PGADMIN_DEFAULT_PASSWORD: PgAdminPassword
      volumes:
        - pgadmin-data:/var/lib/pgadmin
   ```

4. ***Ya con el docker compose hecho lo lanzamos como siempre***
![Captura de pantalla 2025-01-15 225259](https://github.com/user-attachments/assets/7415d358-5afc-4ab9-86f9-26f528dcb24f)

  ***Vamos a comprobarloa  un navegador***
  
  ***En el buscador ponemos nuestra ip y el puerto***
  
  ![Captura de pantalla 2025-01-15 225746](https://github.com/user-attachments/assets/04615418-dafc-4e20-8a69-e15f53283467)

  ***Iniciamos sesion***
  
  ![Captura de pantalla 2025-01-15 230111](https://github.com/user-attachments/assets/2781be95-a9f7-4c90-a707-5195927db600)

  ***Cuando ya estamos dentro nos sale esto***
![Captura de pantalla 2025-01-15 230237](https://github.com/user-attachments/assets/252d253d-74e6-4461-b3a1-c4c0e60f3f50)

  ***Comprobamos la versión***

  ![Captura de pantalla 2025-01-15 230447](https://github.com/user-attachments/assets/f6e05471-239b-4f90-b98c-2989810c01b3)


5. ***Ahora vamos a comprobar la base de datos***

***Lo mismo que antes, nuestra ip y el puerto de la base***
   
   ![Captura de pantalla 2025-01-15 230656](https://github.com/user-attachments/assets/82813804-d07d-4f27-a994-3e75016e564f)

***Una vez dentro nos saldria esto***

![Captura de pantalla 2025-01-15 231118](https://github.com/user-attachments/assets/aee3b21b-f321-4203-bc88-67f059fd3de3)

***Creamos el server y nos saldra esto***

![Captura de pantalla 2025-01-15 gf](https://github.com/user-attachments/assets/eec28826-1163-4ade-9a25-b44034a2a238)
