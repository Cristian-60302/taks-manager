# Sistema de Gestión de Tareas - Java

Sistema completo de gestión de tareas con interfaz gráfica, programación funcional, y APIs REST.

## 🚀 Características

- ✅ **Interfaz Gráfica (Swing)**: Login, registro, y gestión completa de tareas
- ✅ **Programación Funcional**: Implementación de Monad y Functor
- ✅ **Manejo de Excepciones**: Excepciones personalizadas para diferentes errores
- ✅ **Concurrencia**: Uso de threads, SwingWorker, y locks para operaciones paralelas
- ✅ **Autenticación**: Sistema de login con usuarios y contraseñas hasheadas
- ✅ **APIs REST**: Dos servidores API (Tareas y Autenticación)
- ✅ **CRUD Completo**: Crear, buscar, modificar, eliminar tareas
- ✅ **Ordenamiento**: Tareas ordenadas por prioridad y fecha
- ✅ **Código Limpio**: Arquitectura en capas, sin código espagueti

## 📁 Estructura del Proyecto

\`\`\`
src/main/java/com/taskmanager/
├── Main.java                          # Punto de entrada
├── api/                               # APIs REST
│   ├── TaskApiServer.java            # API de tareas (puerto 8080)
│   └── AuthApiServer.java            # API de autenticación (puerto 8081)
├── exceptions/                        # Excepciones personalizadas
│   ├── TaskException.java
│   ├── TaskNotFoundException.java
│   ├── AuthenticationException.java
│   └── ValidationException.java
├── functional/                        # Programación funcional
│   ├── Functor.java                  # Interfaz Functor
│   ├── Monad.java                    # Interfaz Monad
│   └── Result.java                   # Implementación de Monad
├── model/                            # Modelos de datos
│   ├── Task.java
│   ├── TaskPriority.java
│   ├── TaskStatus.java
│   └── User.java
├── service/                          # Lógica de negocio
│   ├── TaskService.java              # Servicio de tareas (thread-safe)
│   └── AuthService.java              # Servicio de autenticación
└── ui/                               # Interfaz gráfica
    ├── LoginFrame.java               # Ventana de login
    ├── RegisterDialog.java           # Diálogo de registro
    ├── MainFrame.java                # Ventana principal
    └── TaskDialog.java               # Diálogo de tareas
\`\`\`

## 🛠️ Requisitos

- Java 17 o superior
- Maven 3.6+
- Visual Studio Code con Extension Pack for Java

## 📦 Instalación y Ejecución

### Opción 1: Usando Maven

\`\`\`bash
# Compilar el proyecto
mvn clean compile

# Ejecutar la aplicación
mvn exec:java -Dexec.mainClass="com.taskmanager.Main"

# O crear un JAR ejecutable
mvn clean package
java -jar target/task-manager-1.0.0.jar
\`\`\`

### Opción 2: Desde Visual Studio Code

1. Abre el proyecto en VS Code
2. Asegúrate de tener instalado "Extension Pack for Java"
3. Abre `Main.java`
4. Presiona F5 o haz clic en "Run" → "Run Without Debugging"

## 👤 Usuarios de Prueba

El sistema incluye dos usuarios predefinidos:

- **Usuario**: `admin` | **Contraseña**: `admin123`
- **Usuario**: `user` | **Contraseña**: `user123`

## 🔧 APIs REST

### API de Tareas (Puerto 8080)

**GET** `/api/tasks?userId=admin`
\`\`\`json
{
  "tasks": [...],
  "count": 5
}
\`\`\`

**POST** `/api/tasks`
\`\`\`json
{
  "title": "Nueva tarea",
  "description": "Descripción",
  "priority": "HIGH",
  "userId": "admin"
}
\`\`\`

**GET** `/api/tasks/search?q=buscar&userId=admin`

### API de Autenticación (Puerto 8081)

**POST** `/api/auth/login`
\`\`\`json
{
  "username": "admin",
  "password": "admin123"
}
\`\`\`

**POST** `/api/auth/register`
\`\`\`json
{
  "username": "nuevo",
  "password": "password123",
  "fullName": "Nuevo Usuario"
}
\`\`\`

## 🎯 Funcionalidades Principales

### Gestión de Tareas
- ✅ Crear tareas con título, descripción y prioridad
- ✅ Buscar tareas por título
- ✅ Filtrar por estado (Pendiente, En Progreso, Completada, Cancelada)
- ✅ Filtrar por prioridad (Baja, Media, Alta, Urgente)
- ✅ Editar tareas existentes
- ✅ Eliminar tareas
- ✅ Ordenamiento automático por prioridad y fecha

### Programación Funcional
- **Monad Result**: Manejo elegante de errores sin try-catch
- **Functor**: Transformación de valores con `map()`
- **Composición**: Encadenamiento de operaciones con `flatMap()`

Ejemplo:
\`\`\`java
taskService.createTask(title, description, priority, userId)
    .onSuccess(task -> System.out.println("Tarea creada: " + task))
    .onFailure(error -> System.err.println("Error: " + error.getMessage()));
\`\`\`

### Concurrencia y Paralelismo
- **SwingWorker**: Operaciones en background sin bloquear la UI
- **ReadWriteLock**: Acceso concurrente seguro a las tareas
- **ConcurrentHashMap**: Almacenamiento thread-safe
- **Daemon Threads**: Servidores API en threads separados

## 🏗️ Arquitectura

El proyecto sigue una arquitectura en capas:

1. **Capa de Presentación (UI)**: Swing components
2. **Capa de Servicio**: Lógica de negocio
3. **Capa de Modelo**: Entidades de dominio
4. **Capa de API**: Endpoints REST
5. **Capa Funcional**: Abstracciones funcionales (Monad, Functor)

## 🔒 Seguridad

- Contraseñas hasheadas con SHA-256
- Validación de entrada en todos los formularios
- Manejo robusto de excepciones
- Thread-safety en operaciones concurrentes

## 📝 Notas de Desarrollo

- El código está completamente documentado con Javadoc
- Sigue principios SOLID y clean code
- Sin código espagueti: cada clase tiene una responsabilidad única
- Uso extensivo de programación funcional
- Manejo de errores con Result Monad en lugar de excepciones checked

## 🚀 Próximas Mejoras

- Persistencia en base de datos (actualmente en memoria)
- Autenticación JWT para las APIs
- WebSocket para actualizaciones en tiempo real
- Tests unitarios y de integración
- Exportar/importar tareas (JSON, CSV)

---

**Desarrollado con ❤️ usando Java 17, Swing, y programación funcional**
