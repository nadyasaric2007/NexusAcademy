# Sistema de Gestión Académica "NEXUS"

Este proyecto es un sistema académico interactivo desarrollado en C++ que actúa como interfaz para una base de datos MySQL. Permite gestionar la información de alumnos, visualizar rankings y actualizar datos en tiempo real.

Características
- **Buscador Individual**: Consulta la ficha completa de un alumno por su ID, es decir: nombre, apellido, celular, nota final y su estado.
- **Cuadro de Honor**: Visualiza el Top 5 de los mejores promedios.
- **Filtro de Reprobados**: Lista a los alumnos con nota menor a 5.
- **Actualización**: 
  - Modifica notas y su estado automático (Aprobado/Reprobado).
  - Actualiza números de contacto.

## Requisitos Técnicos
- **Código**: C++
- **Compilador**: MinGW-w64 (g++)
- **Base de Datos**: MySQL Server 8.0
- **Conector**: MySQL Connector/C (libmysql)

## Configuración Local
Por razones de seguridad, los datos de acceso a la base de datos no fueron incluidos dentro de este repositorio. Para poder ejecutar correctamente el proyecto, es necesario crear un archivo denominado `db_config.h` en la carpeta principal del proyecto. Dicho archivo debe contener la configuración de conexión siguiendo el formato indicado a continuación:

```cpp
#ifndef DB_CONFIG_H
#define DB_CONFIG_H

#define DB_HOST "127.0.0.1"
#define DB_USER "tu_usuario"
#define DB_PASS "tu_password"
#define DB_NAME "sistema"

#endif
```

# Instalación y Compilación (Detalle Técnico)

Para que el sistema funcione, se debe seguir este proceso de integración:

### 1. Preparación del Entorno (Instalación)
- **Base de Datos**: Importar el archivo `NEXUS.sql` en MySQL Server para crear la estructura de tablas.
- **Dependencias**: Para el correcto funcionamiento del sistema, es indispensable que el archivo `libmysql.dll` se encuentre ubicado en la misma carpeta que el archivo ejecutable, ya que cumple la función de controlador de comunicación entre el programa y la base de datos MySQL.

- **Configuración**: Crear manualmente `db_config.h` con las credenciales locales de acceso.

### 2. Proceso de Compilación
Se utiliza vinculación dinámica con el compilador `g++`. El comando de compilación debe incluir los flags de inclusión (`-I`) y enlace (`-L`) apuntando a los directorios de instalación de MySQL:

```bash
g++ main.cpp -o main.exe -I"C:/Program Files/MySQL/MySQL Server 8.0/include" -L"C:/Program Files/MySQL/MySQL Server 8.0/lib" -lmysql
