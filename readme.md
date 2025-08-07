
# Esquema Base de datos

 
## Tabla: `Usuario`

| Columna            | Tipo         | Restricciones    |
| ------------------ | ------------ | ---------------- |
| UsuarioCodigo      | bigint       | PK               |
| FechaCreacion      | timestamp    | NOT NULL         |
| UsuarioCorreo      | varchar(255) | NOT NULL, UNIQUE |
| password           | varchar(255) | NOT NULL         |
| rol                | varchar(10)  | NOT NULL         |
| FechaActualizacion | timestamp    | NOT NULL         |

---

## Tabla: `address`

| Columna            | Tipo         | Restricciones |
| ------------------ | ------------ | ------------- |
| DireccionCodigo    | bigint       | PK            |
| linea1             | varchar(100) | NOT NULL      |
| linea2             | varchar(100) |               |
| ciudad             | varchar(50)  | NOT NULL      |
| pais               | varchar(50)  | NOT NULL      |
| FechaCreacion      | timestamp    | NOT NULL      |
| codigoPostal       | integer      | NOT NULL      |
| FechaActualizacion | timestamp    | NOT NULL      |

