# Modelo Relacional de Bases de Datos 1



## Descripción



Este documento detalla el esquema y la estructura del modelo relacional de bases de datos correspondiente al ejercicio de la unidad, enfocado en la gestión de una biblioteca (autores, libros, editoriales, ejemplares, usuarios y préstamos).

---

## Estructura de Tablas y Atributos



### 1. Autor



* **PK (Clave Primaria):** `id_Autor`


* **Atributos:**
* `Nombre`


* `Apellido`


* `fecha_nacimiento`


* `Nacionalidad`





### 2. Autor-Libro



* **PK (Clave Primaria):** `id_Autor-Libro`


* **FK (Claves Foráneas):**
* `ISBN` (asociado a la tabla Libro)


* `id_Autor` (asociado a la tabla Autor)





### 3. Libro



* **PK (Clave Primaria):** `ISBN`


* **Atributos:**
* `titulo`


* `autor`


* `qr`


* `Año_de_edicion`





### 4. Editorial



* **PK (Clave Primaria):** `id_editorial`


* **Atributos:**
* `nombre`


* `pais`


* `ciudad`


* `telefono`





### 5. Ejemplar



* **PK (Clave Primaria):** `Código_inventario`


* **Atributos:**
* `estado_disponibilidad`


* `ubicacion`


* `estado_conservación`




* **FK (Claves Foráneas):**
* `ISBN` (asociado a la tabla Libro)





### 6. Usuario



* **PK (Clave Primaria):** `Legajo`


* **Atributos:**
* `Nombre`


* `Teléfono`


* `tipo_usuario`


* `email`





### 7. Prestamo



* **PK (Clave Primaria):** `id_prestamo`


* **Atributos:**
* `fecha_de_prestamo`


* `costo`


* `fecha_prevista_devolucion`


* `fecha_real_devolucion`




* **FK (Claves Foráneas):**
* `Legajo` (asociado a la tabla Usuario)





### 8. Detalle_Prestamo



* **PK (Clave Primaria):** `id_detalle_prestamo`


* **FK (Claves Foráneas):**
* `id_prestamo` (asociado a la tabla Prestamo)


* `Código_inventario` (asociado a la tabla Ejemplar)





---

## Relaciones Principales



* **Autor y Libro:** Se relacionan mediante la tabla intermedia `Autor-Libro` utilizando las claves foráneas `id_Autor` e `ISBN`.


* **Libro y Ejemplar:** Un libro se vincula con sus copias físicas en la tabla `Ejemplar` a través del campo `ISBN`.


* **Usuario y Prestamo:** Los préstamos son realizados por usuarios identificados de forma única por su `Legajo`.


* **Prestamo y Ejemplar:** La relación de muchos a muchos entre préstamos y ejemplares se gestiona a través de la tabla `Detalle_Prestamo` utilizando `id_prestamo` y `Código_inventario`.
