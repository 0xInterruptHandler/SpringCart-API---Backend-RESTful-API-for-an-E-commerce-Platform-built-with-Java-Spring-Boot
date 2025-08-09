# Esquema Base de datos
 

## Tabla: `Usuario`

| Columna                   | Tipo         | Restricciones    |
| ------------------------- | ------------ | ---------------- |
| UsuarioCodigo             | bigint       | PK               |
| FechaCreacion             | timestamp    | NOT NULL         |
| UsuarioCorreo             | varchar(255) | NOT NULL, UNIQUE |
| UsuarioPassword           | varchar(255) | NOT NULL         |
| UsuarioRol                | varchar(10)  | NOT NULL         |
| UsuarioFechaActualizacion | timestamp    | NOT NULL         |

---

## Tabla: `Direccion`

| Columna                     | Tipo         | Restricciones |
| --------------------------- | ------------ | ------------- |
| DireccionCodigo             | bigint       | PK            |
| DireccionLinea1             | varchar(100) | NOT NULL      |
| DireccionLinea2             | varchar(100) |               |
| DireccionCiudad             | varchar(50)  | NOT NULL      |
| DireccionPais               | varchar(50)  | NOT NULL      |
| DireccionFechaCreacion      | timestamp    | NOT NULL      |
| DireccionCodigoPostal       | integer      | NOT NULL      |
| DireccionFechaActualizacion | timestamp    | NOT NULL      |

---

## Tabla: `Cliente`

| Columna                   | Tipo         | Restricciones                                 |
| ------------------------- | ------------ | --------------------------------------------- |
| ClienteCodigo             | bigint       | PK                                            |
| ClienteFechaCreacion      | timestamp    | NOT NULL                                      |
| ClienteCorreo             | varchar(255) | NOT NULL, UNIQUE                              |
| ClienteNombre             | varchar(20)  | NOT NULL                                      |
| ClienteApellido           | varchar(20)  | NOT NULL                                      |
| ClienteNumeroTelefonico   | varchar(255) | NOT NULL                                      |
| ClienteFechaActualizacion | timestamp    | NOT NULL                                      |
| ClienteDireccionCodigo    | bigint       | FK → `address.address_id`                     |
| ClienteUsuarioCodigo      | bigint       | NOT NULL, UNIQUE, FK → Usuario.UsuarioCodigo` |

---

## Tabla: `Categoria`

| Columna                       | Tipo          | Restricciones                    |
| ----------------------------- | ------------- | -------------------------------- |
| CategoriaCodigo               | bigint        | PK                               |
| CategoriaEstado               | boolean       | NOT NULL                         |
| CategoriaFechaCreacion        | timestamp     | NOT NULL                         |
| CategoriaDescuento            | varchar(1000) |                                  |
| CategoriaImagen               | varchar(255)  | NOT NULL                         |
| CategoriaNombre               | varchar(20)   | NOT NULL                         |
| CategoriaFechaActualizacion   | timestamp     | NOT NULL                         |
| CategoriaSupraCategoriaCodigo | bigint        | FK → `Categoria.CategoriaCodigo` |

---

## Tabla: `product`

| Columna                    | Tipo             | Restricciones                              |
| -------------------------- | ---------------- | ------------------------------------------ |
| ProductoCodigo             | bigint           | PK                                         |
| ProductoFechaCreacion      | timestamp        | NOT NULL                                   |
| ProductoDescripcion        | varchar(1000)    |                                            |
| ProductoDescuento          | double precision | CHECK ≥ 0                                  |
| ProductoImagen             | varchar(255)     | NOT NULL                                   |
| ProductoNombre             | varchar(255)     | NOT NULL                                   |
| ProductoPrecio             | double precision | NOT NULL, CHECK ≥ 0                        |
| ProductoStock              | integer          | CHECK ≥ 0                                  |
| ProductoSKU                | varchar(255)     | NOT NULL, UNIQUE                           |
| ProductoFechaActualizacion | timestamp        |                                            |
| ProductoCategoriaCodigo    | bigint           | NOT NULL, FK → `Categoria.CategoriaCodigo` |


---

## Tabla: `Carrito`

| Columna                   | Tipo             | Restricciones                                  |
| ------------------------- | ---------------- | ---------------------------------------------- |
| CarritoCodigo             | bigint           | PK                                             |
| CarritoFechaCreacion      | timestamp        | NOT NULL                                       |
| CarritoDescuento          | double precision | CHECK ≥ 0                                      |
| CarritoTotal              | double precision | NOT NULL, CHECK ≥ 0                            |
| CarritoFechaActualizacion | timestamp        |                                                |
| CarritoClienteCodigo      | bigint           | NOT NULL, UNIQUE, FK → `Cliente.ClienteCodigo` |

---

## Tabla: `Carrito_Articulo`

| Columna                           | Tipo      | Restricciones                            |
| --------------------------------- | --------- | ---------------------------------------- |
| CarritoArticuloCodigo             | bigint    | PK                                       |
| CarritoArticuloFechaCreacion      | timestamp | NOT NULL                                 |
| CarritoArticuloCantidad           | bigint    | NOT NULL, CHECK ≥ 0                      |
| CarritoArticuloFechaActualizacion | timestamp |                                          |
| CarritoArticuloProductoCodigo     | bigint    | NOT NULL, FK → `Producto.ProductoCodigo` |
| CarritoArticuloCarritoCodigo      | bigint    | NOT NULL, FK → `Carrito.CarritoCodigo`   |

---

## Tabla: `Orden`  

| Columna                 | Tipo             | Restricciones                              |
| ----------------------- | ---------------- | ------------------------------------------ |
| OrdenCodigo             | bigint           | PK                                         |
| OrdenFechaCreacion      | timestamp        | NOT NULL                                   |
| OrdenEstado             | varchar(30)      | NOT NULL                                   |
| OrdenTotal              | double precision | NOT NULL, CHECK ≥ 0                        |
| OrdenFechaActualizacion | timestamp        |                                            |
| OrdenDireccionCodigo    | bigint           | NOT NULL, FK → `Direccion.DireccionCodigo` |
| OrdenClienteCodigo      | bigint           | NOT NULL, FK → `Cliente.ClienteCodigo`     |


---

## Tabla: `Orden_Articulo`

| Columna                         | Tipo      | Restricciones                        |
| ------------------------------- | --------- | ------------------------------------ |
| OrdenArticuloCodigo             | bigint    | PK                                   |
| OrdenArticuloFechaCreacion      | timestamp | NOT NULL                             |
| OrdenArticuloCantidad           | bigint    | NOT NULL, CHECK ≥ 0                  |
| OrdenArticuloFechaActualizacion | timestamp |                                      |
| OrdenArticuloOrdenCodigo        | bigint    | NOT NULL, FK → `"order".OrdenCodigo` |
| OrdenArticuloProductoCodigo     | bigint    | NOT NULL, FK → `product.product_id`  |

---















