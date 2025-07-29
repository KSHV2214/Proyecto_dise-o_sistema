# ServicePro - Sistema de Gestión para Papelería Cybersis

Sistema web completo desarrollado en Python Flask con PostgreSQL para la gestión de servicios de impresión, fotocopiado y encuadernación. Incluye facturación electrónica, sistema de promociones con códigos QR y eliminación automática de servicios.

## 🚀 Características Principales

- **Gestión de Servicios**: CRUD completo para servicios de impresión, fotocopiado y encuadernación
- **Facturación Electrónica**: Generación de facturas en PDF con cálculo automático de IVA (15%)
- **Eliminación Automática**: Los servicios se eliminan automáticamente después de ser facturados
- **Promociones QR**: Creación y validación de códigos QR para descuentos especiales
- **Sistema de Verificación**: Monitor en tiempo real del estado del sistema y base de datos
- **Dashboard Interactivo**: Estadísticas y gráficos en tiempo real
- **Respaldos Automáticos**: Sistema automatizado de backup de base de datos
- **Sistema de Usuarios**: Autenticación con roles (administrador/empleado)
- **Respaldos Automáticos**: Backup semanal de la base de datos

## 📋 Requisitos Previos

- Docker
- Docker Compose

## 🛠️ Instalación y Ejecución

### 1. Clonar el proyecto
```bash
git clone [repositorio]
cd servicepro
```

### 2. Ejecutar con Docker
```bash
docker-compose up --build
```

### 3. Acceder al sistema
- **URL**: http://localhost:5000
- **Usuario Administrador**: admin / admin123
- **Usuario Empleado**: empleado / emp123

## 🐳 Comandos Docker Útiles

```bash
# Ejecutar en segundo plano
docker-compose up -d

# Ver logs de la aplicación
docker-compose logs web

# Ver logs de la base de datos
docker-compose logs db

# Acceso directo a PostgreSQL
docker-compose exec db psql -U servicepro_user -d servicepro_db

# Detener todos los servicios
docker-compose down

# Reiniciar servicios
docker-compose restart

# Ver contenedores en ejecución
docker-compose ps
```

## 📊 Funcionalidades del Sistema

### 1. Gestión de Servicios
- Registro de nuevos servicios (impresión, fotocopiado, encuadernación)
- Seguimiento de estados (pendiente, proceso, completado)
- Cálculo automático de precios
- Filtros por tipo y estado

### 2. Gestión de Clientes
- Registro de clientes con información completa
- Historial de servicios por cliente
- Validación de cédula ecuatoriana

### 3. Facturación
- Generación automática de números de factura
- Cálculo de IVA al 15%
- Aplicación de descuentos por promociones QR
- Exportación a PDF para impresión

### 4. Promociones QR
- Creación de códigos QR únicos
- Configuración de descuentos y vigencia
- Asignación a instituciones específicas
- Validación en tiempo real

### 5. Reportes y Estadísticas
- Dashboard con KPIs principales
- Gráficos de ingresos mensuales
- Efectividad de promociones QR
- Servicios más solicitados

## 🗄️ Estructura de la Base de Datos

- **usuarios**: Sistema de autenticación
- **clientes**: Información de clientes
- **servicios**: Servicios ofrecidos
- **facturas**: Facturación y pagos
- **promociones_qr**: Códigos QR y descuentos
- **instituciones**: Entidades para promociones específicas

## 🔧 Configuración

### Variables de Entorno
```bash
DATABASE_URL=postgresql://servicepro_user:servicepro_pass@db:5432/servicepro_db
SECRET_KEY=servicepro-secret-key-2024
FLASK_ENV=development
```

### Volúmenes Docker
- `./volumes/postgres_data`: Datos persistentes de PostgreSQL
- `./volumes/backups`: Respaldos automáticos de la base de datos
- `./static/qr_codes`: Códigos QR generados
- `./static/facturas`: Facturas PDF generadas

## 📈 Datos de Prueba

El sistema incluye datos de demostración:
- 2 usuarios (admin/empleado)
- 10 clientes ficticios
- 15 servicios de diferentes tipos
- 5 facturas generadas
- 3 promociones QR activas
- 2 instituciones educativas

## 🔒 Seguridad

- Autenticación de usuarios requerida
- Protección CSRF en formularios
- Validación de datos de entrada
- Roles de usuario diferenciados

## 🚨 Solución de Problemas

### Si PostgreSQL no inicia:
```bash
docker-compose down
docker volume rm servicepro_postgres_data
docker-compose up --build
```

### Si hay problemas de permisos:
```bash
chmod +x wait-for-it.sh
chmod +x backup_script.sh
```

### Para reiniciar datos de prueba:
```bash
docker-compose down
docker volume rm servicepro_postgres_data
docker-compose up --build
```

## 📞 Soporte

Para problemas técnicos o preguntas sobre el sistema, revisar los logs:
```bash
docker-compose logs web
```

---

**Desarrollado para Papelería Cybersis** - Sistema académico de gestión integral
