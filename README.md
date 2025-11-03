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

### 2. Verificar configuración
Abrir en navegador:
- Productos dev: http://localhost:8888/ms-productos/dev
- Pedidos dev: http://localhost:8888/ms-pedidos/dev

## 🔧 Configuración de Perfiles

### Desarrollo (dev/local)
- **Config Server**: Puerto 8888
- **Logging**: INFO level
- **Seguridad**: Usuario admin/local123

### QA
- **Config Server**: Puerto 8888
- **Logging**: INFO level
- **Seguridad**: Usuario admin/qa456

### Producción (prd)
- **Config Server**: Puerto 8888
- **Logging**: WARN level
- **Seguridad**: Variables de entorno obligatorias

