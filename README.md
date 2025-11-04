# Sistema de Gestión de Pedidos con Microservicios

## 📋 Descripción del Proyecto

Sistema de gestión de pedidos implementado con arquitectura de microservicios utilizando Spring Boot y Spring Cloud Config.

**Tecnologías**: Spring Boot, Gradle, Spring Cloud Config

## 🏗️ Arquitectura de Microservicios

### Microservicios Implementados

#### ✅ **ms-config-server**
- **Tecnología**: Spring Boot + Gradle
- **Puerto**: 8888
- **Función**: Servidor de configuración centralizada
- **Perfiles**: dev, qa, prd
- **Estado**: Completado y funcional

#### ✅ **ms-productos**
- **Tecnología**: Spring Boot + Gradle + WebFlux + R2DBC
- **Puerto**: 8081
- **Función**: API REST completa de productos
- **Base de datos**: PostgreSQL con procedimientos almacenados
- **Estado**: Completado con API REST funcional
- **Endpoints**: CRUD completo + bajo stock + actualizar stock

#### ✅ **ms-pedidos**
- **Tecnología**: Spring Boot + Maven + WebFlux + R2DBC
- **Puerto**: 8082
- **Función**: API REST completa de pedidos con comunicación a ms-productos
- **Base de datos**: PostgreSQL con validación de stock
- **Estado**: Completado con integración entre microservicios

## 🛠️ Requisitos Previos

- **Java**: JDK 21 o superior
- **Git**: Para control de versiones
- **Gradle**: 8.0+

## ⚙️ Instalación y Configuración

### 1. Clonar el repositorio
```bash
git clone https://github.com/JoseVillacorta/sistema-gestion-pedidos.git
cd sistema-gestion-pedidos
```

### 2. Configurar variables de entorno
Crear variables de entorno del sistema:

```
GIT_REPO_URI=file://[ruta_a_tu_proyecto]/config-repo
GIT_USERNAME=[tu_usuario_github]
GIT_PASSWORD=[tu_personal_access_token]
CONFIG_USERNAME=
CONFIG_PASSWORD=
```

## 🚀 Cómo Ejecutar

### 1. Iniciar Config Server
```bash
cd ms-config-server
./gradlew.bat bootRun --args="--spring.profiles.active=local"
```

**Verificar**: http://localhost:8888

### 2. Iniciar ms-productos
```bash
cd ms-productos
./gradlew.bat bootRun --args="--spring.profiles.active=dev"
```

### 3. Verificar configuración
Abrir en navegador:
- Config server: http://localhost:8888
- Productos dev: http://localhost:8888/ms-productos/dev
- Health check: http://localhost:8081/actuator/health

## 🔧 Configuración de Perfiles

### Desarrollo (dev/local)
- **Config Server**: Puerto 8888
- **ms-productos**: Puerto 8081, BD: db_productos_dev
- **Logging**: INFO level
- **Seguridad**: Usuario admin/local123

### QA
- **Config Server**: Puerto 8888
- **ms-productos**: Puerto 8081, BD: db_productos_qa
- **Logging**: INFO level
- **Seguridad**: Usuario admin/qa456

### Producción (prd)
- **Config Server**: Puerto 8888
- **ms-productos**: Puerto 8081, BD: db_productos_prd
- **Logging**: WARN level
- **Seguridad**: Variables de entorno obligatorias

## 📋 APIs Disponibles

### ms-productos (Puerto 8081)
```
GET    /api/productos              - Listar productos
GET    /api/productos/{id}         - Obtener producto
POST   /api/productos              - Crear producto
PUT    /api/productos/{id}         - Actualizar producto
DELETE /api/productos/{id}         - Eliminar producto
PUT    /api/productos/{id}/stock   - Actualizar stock
GET    /api/productos/bajo-stock   - Productos con bajo stock
GET    /actuator/health            - Health check
```

