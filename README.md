# Conexión Base de Datos Relacional
## ¿Qué es JDBC y cuáles son sus componentes?
JDBC (Java Database Connectivity) es una API estándar proporcionada por Java que facilita la conexión y comunicación de aplicaciones con bases de datos relacionales utilizando SQL. Su objetivo principal es proporcionar una interfaz uniforme para interactuar con diferentes sistemas de bases de datos, independientemente del proveedor. JDBC permite a los desarrolladores realizar operaciones como establecer conexiones, ejecutar consultas SQL y procesar los resultados obtenidos.

### Componentes principales de JDBC:

   #### **Driver Manager**
   Es el encargado de gestionar los controladores JDBC, permitiendo a las aplicaciones encontrar y utilizar el driver adecuado para conectarse a una base de datos     específica.
  
   #### **Driver**
   Define las reglas para interactuar con una base de datos en particular. Cada sistema de bases de datos (por ejemplo, MySQL, PostgreSQL, Oracle) cuenta con su propio  driver JDBC, que actúa como intermediario entre la aplicación y la base de datos.
  
   #### **Connection**
   Representa una conexión activa con una base de datos. Es el punto de partida para ejecutar consultas SQL y realizar transacciones. Permite configuraciones específicas como niveles de aislamiento de transacciones y la activación o desactivación del modo de autocommit.
  
   #### **Statement**
   Proporciona herramientas para ejecutar consultas SQL. Hay tres tipos principales:
  
   -  Statement: Usado para consultas simples y estáticas.
   -  PreparedStatement: Utilizado para consultas precompiladas que aceptan parámetros, mejorando el rendimiento y reduciendo el riesgo de inyección SQL.
   -  CallableStatement: Diseñado para ejecutar procedimientos almacenados en la base de datos.
   -  ResultSet: Representa los datos devueltos por una consulta SQL. Permite recorrer filas y columnas, leer valores y realizar transformaciones sobre los resultados.
    
   #### **SQLException**
   Es la clase utilizada para manejar errores y excepciones que pueden ocurrir durante la interacción con la base de datos, como problemas de conexión, consultas mal formadas o restricciones violadas.

## Librerías en Scala para interactuar con bases de datos relacionales

Scala cuenta con varias librerías diseñadas para conectarse y trabajar con bases de datos relacionales. Entre las más populares están Slick y Doobie, que abordan la interacción con las bases de datos desde diferentes paradigmas y niveles de abstracción.

### **Principales librerías**

#### Slick
Slick es un ORM (Object-Relational Mapping) funcional que proporciona una API altamente tipada para realizar consultas SQL de manera declarativa y funcional.

**Ventajas:**

Ofrece abstracción funcional y consultas tipadas que ayudan a prevenir errores en tiempo de compilación.
Compatible con varias bases de datos populares, como PostgreSQL, MySQL y SQLite.

**Desventajas:**
Tiene una curva de aprendizaje moderada, especialmente para desarrolladores nuevos en Scala o programación funcional.
Doobie
Doobie es una biblioteca funcional construida sobre Cats, que permite trabajar directamente con JDBC, proporcionando un control más explícito sobre las consultas SQL.

**Ventajas:**
Permite un control detallado y directo sobre las consultas SQL, haciéndolo ideal para casos en los que se requiere optimización manual.
Es completamente modular y está diseñado para integrarse con ecosistemas funcionales en Scala.

**Desventajas:**
Al ser más explícito y técnico, requiere conocimientos sólidos de programación funcional, lo que lo hace menos accesible para principiantes.

### Comparación entre Slick y Doobie



