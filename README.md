# PrácticoBD

Proyecto práctico de **Base de Datos** orientado al análisis y gestión de información de ventas de videojuegos.

## Nombre del proyecto

**PrácticoBD – Base de datos de ventas de videojuegos**

## Descripción

El dataset utilizado contiene información de videojuegos, plataformas, géneros, editores y ventas por región, incluyendo las ventas globales. A partir de estos datos se normalizó la información y se diseñó una estructura relacional que permite realizar consultas, generar vistas e incorporar índices para mejorar el acceso a la información.

## Fuente de los datos

Los datos utilizados provienen de un dataset basado en información del sitio Web Kaggle.

- Fuente original: https://www.kaggle.com/datasets/gregorut/videogamesales

## Estructura de la base de datos

La base de datos está organizada mediante tablas relacionadas que permiten separar la información y evitar duplicación de datos.

### Tablas principales

- **plataforma:** almacena las plataformas de videojuegos.
- **genero:** almacena los géneros de los videojuegos.
- **editor:** almacena los editores o empresas responsables de los videojuegos.
- **videojuegos:** contiene la información principal de cada videojuego, incluyendo nombre, año de lanzamiento y referencias a género, editor y plataforma.
- **ventas:** almacena la información de ventas por región y las ventas globales asociadas a los videojuegos.

Las relaciones entre las tablas se implementan mediante claves primarias y claves foráneas.

## Diagrama

![Diagrama](docs/diagrama.png)

## Requisitos

- MySQL 8.0 o superior / MariaDB
- HeidiSQL, MySQL Workbench u otro cliente compatible
- Git
- Archivo CSV del dataset
- Permisos para crear bases de datos, tablas, índices y vistas

## Instalación

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/geroovisconti13/PracticoBD.git
   ```

2. Ingresar al directorio del proyecto:

   ```bash
   cd PracticoBD
   ```

3. Crear la base de datos en MySQL/MariaDB.

4. Ejecutar los scripts SQL incluidos en el proyecto respetando el orden indicado.

5. Importar los datos del CSV en la tabla correspondiente.

6. Ejecutar las sentencias de creación de índices y vistas.

## Creación de tablas

La estructura de la base de datos se crea mediante scripts SQL.

Los scripts contemplan:

- Creación de la base de datos.
- Creación de tablas.
- Definición de claves primarias.
- Definición de claves foráneas.
- Restricciones necesarias.
- Relaciones entre las entidades.

El modelo busca separar los datos de plataformas, géneros y editores de la información propia de los videojuegos y sus ventas.

## Importación de datos

Los datos originales se encuentran en formato **CSV**.

El procedimiento general de importación es:

1. Crear previamente la estructura de las tablas.
2. Verificar que los tipos de datos de las columnas sean compatibles con el CSV.
3. Importar el archivo CSV utilizando HeidiSQL, MySQL Workbench o una herramienta equivalente.
4. Controlar valores nulos o datos especiales del dataset, como años sin información.
5. Verificar la cantidad de registros importados.
6. Ejecutar consultas de control para comprobar la integridad de los datos.

## Índices

Se crean índices sobre columnas utilizadas frecuentemente en búsquedas, filtros y relaciones.

Los índices tienen como objetivo mejorar el rendimiento de las consultas, especialmente sobre:

- Claves foráneas.
- Plataformas.
- Géneros.
- Editores.
- Datos utilizados para filtrar y ordenar las ventas.

Los índices se encuentran definidos mediante sentencias `CREATE INDEX` o mediante las restricciones correspondientes.

## Vistas

El proyecto incluye **4 o más vistas** destinadas a facilitar consultas frecuentes y mostrar información resumida.

Entre las vistas desarrolladas se encuentran:

- **n64:** permite consultar información relacionada con videojuegos de la plataforma Nintendo 64.
- **misc:** reúne información seleccionada para realizar consultas y análisis específicos.
- **ventas_globales_plataforma:** permite analizar las ventas globales agrupadas por plataforma.
- **top_20_juegos:** muestra los 20 videojuegos destacados según sus ventas globales.

Las vistas permiten reutilizar consultas SQL sin necesidad de escribir nuevamente toda la lógica de consulta.

## Backup

Para realizar un backup de la base de datos se puede utilizar `mysqldump`.

Ejemplo:

```bash
mysqldump -u USUARIO -p practicodb > backup_practicodb.sql
```

Para restaurar el backup:

```bash
mysql -u USUARIO -p practicodb < backup_practicodb.sql
```

También se puede realizar el backup y la restauración utilizando las herramientas disponibles en HeidiSQL.

## Consultas SQL

El proyecto contiene consultas SQL destinadas a:

- Buscar videojuegos por plataforma.
- Filtrar videojuegos por género.
- Consultar información de editores.
- Analizar ventas globales.
- Obtener las plataformas con mayores ventas.
- Obtener los videojuegos con mayores ventas.
- Consultar información específica de una plataforma, como Nintendo 64.
- Utilizar las vistas creadas para obtener información resumida.

Ejemplo:

```sql
SELECT *
FROM top_20_juegos;
```

Otro ejemplo para consultar las ventas globales por plataforma:

```sql
SELECT *
FROM ventas_globales_plataforma;
```

## Autores

- **Geronimo Visconti**
- **Martin Fogar**
