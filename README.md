

API Banco

Este proyecto es una API RESTful construida con **ASP.NET Core** y **SQLite**. Permite gestionar información relacionada con clientes, cuentas bancarias y transacciones.

Estructura del Proyecto

1. Banco.Controllers: Controladores para manejar las solicitudes HTTP.
2. Banco.Models: Modelos que representan las entidades de la base de datos (Client, Account, Transactions).
3. Banco.Data: Configuración de la base de datos y contexto de Entity Framework (AppDbContext).
4. Banco.Migrations: Migraciones de la base de datos para la creación y actualización del esquema.

Endpoints de la API

La API proporciona los siguientes endpoints:

Clientes

1. Crear Cliente

* Método: `POST`
* Ruta: `/api/clientes`
* Descripción: Crea un nuevo cliente en la base de datos.
* Request Body:

  ```json
  {
    "name": "Carlos Pérez",
    "dateOfBirth": "1985-10-15T00:00:00",
    "sex": "Masculino",
    "income": 35000.50
  }
  ```
2. Obtener Todos los Clientes

* Método: `GET`
* Ruta: `/api/clientes`
* Descripción: Obtiene todos los clientes registrados en la base de datos.

3. Obtener Cliente por ID

* Método: `GET`
* Ruta: `/api/clientes/{id}`
* Descripción: Obtiene un cliente específico por su ID.

4. Eliminar Cliente

* Método: `DELETE`
* Ruta: `/api/clientes/{id}`
* Descripción: Elimina un cliente específico por su ID.

---

Cuentas

1. Crear Cuenta

* Método: `POST`
* Ruta: `/api/cuentas`
* Descripción: Crea una nueva cuenta para un cliente.
* Request Body:

  ```json
  {
    "number": "1234567890",
    "saldo": 1000.00,
    "clienteId": 1
  }
  ```

2. Obtener Todas las Cuentas

* Método: `GET`
* Ruta: `/api/cuentas`
* Descripción: Obtiene todas las cuentas bancarias registradas.

---
Transacciones

1. Registrar Transacción

* Método: `POST`
* Ruta: `/api/transacciones/{NumberAccount}`
* Descripción: Registra una transacción de depósito o retiro para una cuenta.
* Request Body:

  ```json
  {
    "type": "Depósito",
    "amount": 200.00
  }
  ```

2. Consultar Historial de Transacciones

* Método: `GET`
* Ruta: `/api/transacciones/{NumberAccount}/historial`
* Descripción: Obtiene el historial de transacciones para una cuenta específica.

---
Configuración de la Base de Datos

La base de datos utiliza SQLite. Se configura a través de un archivo `appsettings.json`, y se utiliza `Entity Framework Core` para las migraciones.

Cadena de Conexión

Asegúrate de que la cadena de conexión a la base de datos esté configurada en el archivo `appsettings.json`:

```json
{
  "ConnectionStrings": {
    "BancoDb": "Data Source=BancoDb.db"
  }
}
```

---

Instrucciones para Correr la Aplicación

1. Clonar el Repositorio

Clona el repositorio en tu máquina local:

```bash
git clone <URL_DEL_REPOSITORIO>
cd <nombre_del_directorio>
```

2. Restaurar Dependencias

Ejecuta el siguiente comando para restaurar las dependencias del proyecto:

```bash
dotnet restore
```

3. Ejecutar las Migraciones

Si no se han ejecutado las migraciones aún, ejecuta los siguientes comandos para crear la base de datos:

```bash
dotnet ef migrations add Init
dotnet ef database update
```

4. Iniciar la Aplicación

Ejecuta la aplicación utilizando el siguiente comando:

```bash
dotnet run
```

La API estará disponible en `http://localhost:5231`.

---

Acceder a la API con Swagger

La aplicación está configurada para generar documentación de la API utilizando **Swagger**. Accede a la interfaz de Swagger en:

```
http://localhost:5231/swagger
```

Desde aquí podrás interactuar con la API directamente.

---

Pruebas con Postman

Si prefieres usar Postman, puedes hacer las siguientes solicitudes:

1. **POST** `/api/clientes` para crear un nuevo cliente.
2. **GET** `/api/clientes` para obtener todos los clientes.
3. **GET** `/api/clientes/{id}` para obtener un cliente por su ID.
4. **DELETE** `/api/clientes/{id}` para eliminar un cliente por su ID.

---

Tecnologías Utilizadas

* ASP.NET Core 6
* Entity Framework Core
* SQLite
* Swagger para documentación

