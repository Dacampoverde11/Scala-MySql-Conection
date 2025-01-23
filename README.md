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

**Principales librerías**

### Slick
Slick es un ORM (Object-Relational Mapping) funcional que proporciona una API altamente tipada para realizar consultas SQL de manera declarativa y funcional.

**Ventajas:**

Ofrece abstracción funcional y consultas tipadas que ayudan a prevenir errores en tiempo de compilación.
Compatible con varias bases de datos populares, como PostgreSQL, MySQL y SQLite.

**Desventajas:**
Tiene una curva de aprendizaje moderada, especialmente para desarrolladores nuevos en Scala o programación funcional.

### Doobie

Doobie es una biblioteca funcional construida sobre Cats, que permite trabajar directamente con JDBC, proporcionando un control más explícito sobre las consultas SQL.

**Ventajas:**
Permite un control detallado y directo sobre las consultas SQL, haciéndolo ideal para casos en los que se requiere optimización manual.
Es completamente modular y está diseñado para integrarse con ecosistemas funcionales en Scala.

**Desventajas:**
Al ser más explícito y técnico, requiere conocimientos sólidos de programación funcional, lo que lo hace menos accesible para principiantes.

### Comparación entre Slick y Doobie

| Aspecto             | Slick                                           | Doobie                                                 |
|---------------------|------------------------------------------------|-------------------------------------------------------|
| **Paradigma**       | Abstracción funcional para consultas SQL.       | Trabajo directo con JDBC desde un enfoque funcional.  |
| **Nivel de abstracción** | Alto (similar a un ORM).                       | Medio (gestión manual de consultas SQL).              |
| **Curva de aprendizaje** | Moderada, ideal para quienes tienen experiencia con Java y ORM. | Más pronunciada, adecuada para desarrolladores con experiencia en programación funcional. |
| **Soporte funcional** | Opcional.                                     | Obligatorio, basado en Cats.                          |






## Información adicional sobre JDBC y herramientas en Scala
### Integración con otras herramientas:

JDBC se puede combinar con frameworks como Spring para manejar transacciones, inyecciones de dependencias y configuraciones avanzadas.

### Aspectos de rendimiento:

Usar PreparedStatement no solo mejora la seguridad al evitar inyección SQL, sino que también optimiza el rendimiento al permitir la reutilización de consultas precompiladas.

### Otros frameworks de bases de datos en Scala:

Quill: Una biblioteca funcional que facilita la generación de consultas SQL basadas en modelos tipados, similar a Slick pero con un enfoque más declarativo.
JDBC Direct: Permite trabajar directamente con JDBC sin abstracciones adicionales, adecuado para proyectos pequeños.


## Establecer Conexion con una Base de Datos en Scala

## 1. Crear una base de datos en MySQL

Ejecute el siguiente script SQL en su entorno MySQL:

```sql
CREATE DATABASE music_library;

USE music_library;

CREATE TABLE songs (
    id INT AUTO_INCREMENT PRIMARY KEY,          -- Identificador único
    title VARCHAR(255) NOT NULL,                -- Título de la canción
    artist VARCHAR(255) NOT NULL,               -- Artista
    album VARCHAR(255) NOT NULL,                -- Álbum
    duration TIME NOT NULL                      -- Duración de la canción (hh:mm:ss)
);

-- Insertar datos de las canciones
INSERT INTO songs (title, artist, album, duration) VALUES
('Tanto Ganas Tanto Pierdes', 'Verde 70', 'La Edad de la Zebra', '00:04:13'),
('You Shook Me All Night Long', 'AC/DC', 'Who Made Who', '00:03:31'),
('De Música Ligera - Remasterizado', 'Soda Stereo', 'Canción Animal', '00:03:33'),
('La chispa adecuada', 'Héroes del Silencio', 'Avalancha', '00:05:27'),
('La chispa adecuada - Live', 'Héroes del Silencio', 'Tour 2007', '00:05:25'),
('Billie Jean', 'Michael Jackson', 'Thriller 25 Super Deluxe Edition', '00:04:54'),
('Creep', 'Radiohead', 'Pablo Honey', '00:03:59'),
('Your Love', 'The Outfield', 'Play Deep', '00:03:36'),
('Chico tienes que cuidarte', 'Hombres G', '30 años y un día', '00:04:10'),
('Nothing\'s Gonna Stop Us Now', 'Starship', 'No Protection', '00:04:30'),
('Soñé', 'Zoé', 'MTV Unplugged', '00:03:47'),
('Knockin\' On Heaven\'s Door', 'Guns N\' Roses', 'Use Your Illusion II', '00:05:36'),
('Sweet Child O\' Mine', 'Guns N\' Roses', 'Appetite For Destruction', '00:05:55'),
('I Was Made For Lovin\' You', 'KISS', 'Dynasty', '00:04:31'),
('Marta Tiene un Marcapasos', 'Hombres G, Los Enanitos Verdes', 'Huevos Revueltos', '00:04:11'),
('More Than Words', 'Extreme', 'Extreme II - Pornograffitti', '00:05:34'),
('The Way You Make Me Feel - 2012 Remaster', 'Michael Jackson', 'Bad 25th Anniversary', '00:04:58'),
('Oye Mi Amor', 'Maná', '¿Dónde Jugarán los Niños?', '00:04:23'),
('Bohemian Rhapsody - Remasterizado', 'Queen', 'A Night At The Opera', '00:05:54'),
('Si No Te Tengo a Ti (En Vivo)', 'Hombres G', 'Huevos Revueltos', '00:05:27'),
('Hey Jude - Remastered 2015', 'The Beatles', '1 (Remastered)', '00:07:06');
```

