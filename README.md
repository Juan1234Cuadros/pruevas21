# Proyecto: CreaciÃ³n y gestiÃ³n de contenedores de bases de datos con Docker
## Autor: Juan David Cuadros Molina

---

## 1. Objetivo de la prÃ¡ctica

El objetivo de esta actividad es **crear, configurar y gestionar contenedores de bases de datos utilizando Docker desde la lÃ­nea de comandos (CMD)**, verificando su funcionamiento mediante diferentes clientes SQL de escritorio.

---

## 2. Entorno de trabajo

| Herramienta | DescripciÃ³n | VersiÃ³n |
|--------------|-------------|----------|
| Docker Engine | Plataforma para crear y ejecutar contenedores | 27.1.1 |
| CMD / Terminal | Consola de Windows para ejecutar comandos Docker | Windows 11 |
| DBeaver | Cliente SQL grÃ¡fico multiplataforma | 24.1.0 |
| HeidiSQL | Cliente SQL para MariaDB/MySQL | 12.0 |
| Beekeeper Studio | Cliente SQL para PostgreSQL | 4.0 |

---

## 3. CreaciÃ³n de contenedores

Se levantaron tres contenedores independientes desde CMD, sin utilizar Docker Desktop ni Docker Compose.

| Contenedor | Imagen Docker | Puerto | Usuario | ContraseÃ±a |
|-------------|----------------|---------|-----------|-------------|
| MySQL | mysql:latest | 3306 | root | root |
| MariaDB | mariadb:latest | 3307 | root | root |
| PostgreSQL | postgres:latest | 5432 | postgres | root |

### Comandos utilizados

**MySQL**
```bash
docker run -d --name mysql_container -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 mysql:latest
```

**MariaDB**
```bash
docker run -d --name mariadb_container -e MARIADB_ROOT_PASSWORD=root -p 3307:3306 mariadb:latest
```

**PostgreSQL**
```bash
docker run -d --name postgres_container -e POSTGRES_PASSWORD=root -p 5432:5432 postgres:latest
```

### VerificaciÃ³n de contenedores activos
```bash
docker ps
```

**Evidencia:**  
![cmd_contenedores](evidencias/cmd_contenedores.png)

---

## 4. ConexiÃ³n desde clientes SQL

Cada base de datos fue conectada desde un cliente SQL diferente.

| Cliente | Base de datos | Host | Puerto | Usuario | ContraseÃ±a | Estado |
|----------|----------------|-------|---------|-----------|-------------|---------|
| DBeaver | MySQL | localhost | 3306 | root | root | Conectado |
| HeidiSQL | MariaDB | localhost | 3307 | root | root | Conectado |
| Beekeeper Studio | PostgreSQL | localhost | 5432 | postgres | root | Conectado |

**Evidencias:**  
![dbeaver_conexion](evidencias/dbeaver_conexion.png)  
![heidisql_conexion](evidencias/heidisql_conexion.png)  
![beekeeper_conexion](evidencias/beekeeper_conexion.png)

---

## 5. CreaciÃ³n de bases de datos

En cada contenedor se crearon tres bases de datos, una desde cada cliente SQL.

| Cliente | Contenedor | Base de datos creada | Resultado |
|----------|-------------|----------------------|------------|
| DBeaver | MySQL | db_dbeaver | Creada |
| HeidiSQL | MariaDB | db_heidisql | Creada |
| Beekeeper Studio | PostgreSQL | db_beekeeper | Creada |

**Evidencia:**  
![db_creadas](evidencias/db_creadas.png)

---

## 6. Estructura del proyecto

```
Proyecto_Docker_BasesDatos/
â”œâ”€â”€ README.md
â””â”€â”€ evidencias/
    â”œâ”€â”€ cmd_contenedores.png
    â”œâ”€â”€ dbeaver_conexion.png
    â”œâ”€â”€ heidisql_conexion.png
    â”œâ”€â”€ beekeeper_conexion.png
    â””â”€â”€ db_creadas.png
```

---

## 7. Observaciones

- Docker permite ejecutar mÃºltiples bases de datos en contenedores aislados, evitando conflictos de puertos o dependencias.
- Los clientes grÃ¡ficos SQL facilitan la gestiÃ³n visual y comprobaciÃ³n de conexiones.
- Se comprobÃ³ la interoperabilidad entre contenedores Docker y herramientas externas de administraciÃ³n.
- Esta prÃ¡ctica refuerza el dominio de comandos Docker para gestiÃ³n de servicios de base de datos.

---

## 8. Conclusiones

- Docker es una herramienta poderosa para ambientes de desarrollo y pruebas con bases de datos.  
- Se logrÃ³ crear, ejecutar y conectar tres contenedores distintos sin interferencias.  
- Los resultados demuestran la eficiencia de Docker al simular entornos productivos locales.  
- El proceso completo puede ser replicado fÃ¡cilmente en otros equipos y sistemas operativos.
