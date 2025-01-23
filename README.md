# Conexión Base de Datos Relacional
## ¿Qué es JDBC y cuáles son sus componentes?
JDBC (Java Database Connectivity) es una API estándar proporcionada por Java que facilita la conexión y comunicación de aplicaciones con bases de datos relacionales utilizando SQL. Su objetivo principal es proporcionar una interfaz uniforme para interactuar con diferentes sistemas de bases de datos, independientemente del proveedor. JDBC permite a los desarrolladores realizar operaciones como establecer conexiones, ejecutar consultas SQL y procesar los resultados obtenidos.

Componentes principales de JDBC:

   **Driver Manager**
   Es el encargado de gestionar los controladores JDBC, permitiendo a las aplicaciones encontrar y utilizar el driver adecuado para conectarse a una base de datos     específica.
  
   **Driver**
   Define las reglas para interactuar con una base de datos en particular. Cada sistema de bases de datos (por ejemplo, MySQL, PostgreSQL, Oracle) cuenta con su propio  driver JDBC, que actúa como intermediario entre la aplicación y la base de datos.
  
   **Connection**
   Representa una conexión activa con una base de datos. Es el punto de partida para ejecutar consultas SQL y realizar transacciones. Permite configuraciones específicas como niveles de aislamiento de transacciones y la activación o desactivación del modo de autocommit.
  
   **Statement**
   Proporciona herramientas para ejecutar consultas SQL. Hay tres tipos principales:
  
   -  Statement: Usado para consultas simples y estáticas.
   -  PreparedStatement: Utilizado para consultas precompiladas que aceptan parámetros, mejorando el rendimiento y reduciendo el riesgo de inyección SQL.
   -  CallableStatement: Diseñado para ejecutar procedimientos almacenados en la base de datos.
   -  ResultSet: Representa los datos devueltos por una consulta SQL. Permite recorrer filas y columnas, leer valores y realizar transformaciones sobre los resultados.
    
   **SQLException**
   Es la clase utilizada para manejar errores y excepciones que pueden ocurrir durante la interacción con la base de datos, como problemas de conexión, consultas mal formadas o restricciones violadas.


