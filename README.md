# Proyecto E-commerce .NET Core

## Descripción

Este proyecto implementa una aplicación completa de comercio electrónico desarrollada con .NET Core siguiendo los principios de arquitectura N-Capas, Domain-Driven Design (DDD) y patrones de diseño modernos.

## Estructura del Proyecto

La solución está organizada en 4 capas principales:

- **EcommerceApp.Web**: Interfaz de usuario MVC y punto de entrada de la aplicación
- **Ecommerce.Application**: Servicios de aplicación e implementación de lógica de negocio
- **Ecommerce.Domain**: Entidades de dominio y reglas de negocio core
- **Ecommerce.Infrastructure**: Implementación de persistencia y servicios externos

## Características Principales

- Catálogo de productos con búsqueda y filtrado
- Carrito de compras
- Proceso de checkout
- Sistema de pago seguro
- Gestión de usuarios y autenticación
- Gestión de pedidos
- Descuentos y promociones

## Requisitos

- .NET 7.0 o superior
- SQL Server (o base de datos compatible con EF Core)
- Visual Studio 2022 / VS Code / Rider

## Instalación

1. Clonar el repositorio
   ```bash
   git clone https://github.com/yourusername/ecommerce-project.git
   cd ecommerce-project
   ```

2. Restaurar paquetes NuGet
   ```bash
   dotnet restore
   ```

3. Configurar la cadena de conexión en `appsettings.json` en el proyecto EcommerceApp.Web
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=EcommerceDb;Trusted_Connection=True;MultipleActiveResultSets=true"
   }
   ```

4. Aplicar migraciones para crear la base de datos
   ```bash
   cd EcommerceApp.Web
   dotnet ef database update
   ```

5. Ejecutar la aplicación
   ```bash
   dotnet run
   ```

## Distribución por Módulos

| Equipo | Módulo | Componentes |
|--------|--------|------------|
| MarsDiv | Checkout | Proceso de finalización de compra, envío |
| Compila2 | Sistema de pago | Integración con pasarelas, procesamiento seguro |
| Los DevOps | Gestión de pedidos | Estados, notificaciones, seguimiento |
| Mentes Maestras | Catálogo y búsqueda | Filtros, categorías, inventario |
| #504 | Carrito de compras | Gestión de productos, cantidades, cálculos |
| Binomio Perfecto | Registro y autenticación | Login, registro, seguridad |

## Arquitectura

### Capa de Dominio (Ecommerce.Domain)

Contiene las entidades principales:
- User
- Product
- Category
- Cart / CartItem
- Order / OrderItem
- Payment
- Address
- Discount

### Capa de Aplicación (Ecommerce.Application)

Implementa servicios que coordinan la lógica de negocio:
- UserService
- ProductService
- CartService
- OrderService
- PaymentService

### Capa de Infraestructura (Ecommerce.Infrastructure)

Proporciona implementaciones concretas para acceso a datos:
- ApplicationDbContext
- Repositorios
- Servicios externos
- UnitOfWork

### Capa de Presentación (EcommerceApp.Web)

Gestiona la interfaz de usuario y la interacción:
- Controllers
- Views
- ViewModels
- Filtros y validación

## Patrones Implementados

- **Repository Pattern**: Para abstraer el acceso a datos
- **Unit of Work**: Para mantener la consistencia en transacciones
- **Dependency Injection**: Para desacoplar componentes
- **DTO Pattern**: Para transferencia de datos entre capas
- **Factory Pattern**: Para creación de objetos complejos

## Convenciones de Código

Este proyecto sigue las convenciones estándar de C# y .NET:
- PascalCase para nombres de clases, propiedades y métodos
- camelCase para variables locales y parámetros
- Prefijo "I" para interfaces
- Sufijo "Service", "Repository", "Controller" según corresponda

## Testing

Para ejecutar las pruebas unitarias:
```bash
dotnet test
```

## Configuración de CI/CD

El proyecto incluye configuración para:
- GitHub Actions
- Azure DevOps Pipelines

## Licencia

Este proyecto está licenciado bajo [MIT License](LICENSE).
