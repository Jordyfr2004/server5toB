#  Práctica 4 – API REST con NestJS

## 📘 Descripción del proyecto
En esta práctica se implementó una **API REST** utilizando el framework **NestJS**, organizada por módulos para manejar las principales entidades del sistema:  
equipos, servicios de mantenimiento, órdenes de reparación, repuestos y usuarios.

Cada módulo incluye sus propios **controladores**, **servicios**, **DTOs** y **entidades**, lo que permite crear, actualizar y consultar los datos de forma estructurada.  
Esta práctica refuerza los conceptos de arquitectura modular, inyección de dependencias y el uso de DTOs en NestJS.

---

## 🧱 Estructura del proyecto

```
Practica4/
│
├── package.json               # Dependencias del proyecto
├── nest-cli.json              # Configuración del CLI de NestJS
├── tsconfig.json              # Configuración de TypeScript
├── src/
│   ├── main.ts                # Punto de inicio del servidor
│   ├── app.module.ts          # Módulo raíz
│   │
│   ├── equipments/            # Módulo de equipos
│   ├── maintenance-services/  # Módulo de servicios de mantenimiento
│   ├── repair-orders/         # Módulo de órdenes de reparación
│   ├── spare-parts/           # Módulo de repuestos
│   └── users/                 # Módulo de usuarios y técnicos
│
└── README.md
```

---

##  Instalación y ejecución

1. **Instalar dependencias**
   ```bash
   npm install
   ```

2. **Ejecutar el servidor**
   ```bash
   npm run start:dev
   ```

3. **Abrir en el navegador o Postman**
   ```
   http://localhost:3000
   ```

---

## 🧩 Estructura de los módulos principales

- `equipments/` → Manejo de equipos registrados  
- `maintenance-services/` → Gestión de servicios de mantenimiento  
- `repair-orders/` → Registro de órdenes, notificaciones y reseñas  
- `spare-parts/` → Gestión de repuestos disponibles  
- `users/` → Administración de usuarios y técnicos  

Cada módulo tiene:
- `controller.ts` → Define las rutas HTTP (GET, POST, PUT, DELETE)  
- `service.ts` → Contiene la lógica del negocio  
- `dto/` → Estructuras para validar los datos enviados  
- `entities/` → Modelos de las tablas o colecciones  

---

## Ejemplos de métodos POST

Puedes hacer las pruebas en **Postman**, **Thunder Client** o **cURL**.

###  1. Registrar un equipo
**Ruta:**  
`POST http://localhost:3000/equipments`

**Cuerpo (JSON):**
```json
{
  "userId": "3fbd8c54-b9f3-4e22-94e4-905a8bb12c99",
  "name": "Laptop HP Pavilion",
  "type": "LAPTOP",
  "brand": "HP",
  "model": "Pavilion 15",
  "serialNumber": "SN12345HP2025",
  "observations": "Laptop with overheating issues"
}
```

---

###  2. Crear un usuario
**Ruta:**  
`POST http://localhost:3000/users`

**Cuerpo (JSON):**
```json
{
  "name": "Pedro",
  "lastName": "Alay",
  "email": "pedrocrackc@gmail.com",
  "phone": "+593987654321",
  "address": "Quito, Ecuador"
}
```

---

###  3. Crear un tecnico
**Ruta:**  
`POST http://localhost:3000/users/technician`

**Cuerpo (JSON):**
```json
{
  "name": "Pedro",
  "lastName": "Alay",
  "email": "pedrocrackc@gmail.com",
  "phone": "+593987654321",
  "address": "Quito, Ecuador",
  "specialty": "Laptop and hardware repair",
  "experienceYears": 5,
  "active": true
}
```

---

###  4. Registrar un servicio de mantenimiento
**Ruta:**  
`POST http://localhost:3000/services`

**Cuerpo (JSON):**
```json
{
  "serviceName": "Screen changes",
  "description": "screen changes for all types of devices",
  "basePrice": 45.5,
  "estimatedTimeMinutes": 60,
  "requiresParts": true,
  "type": "REPAIR",
  "imageUrls": [
    "https://example.com/image1.jpg",
    "https://example.com/image2.jpg"
  ],
  "notes": "string"
}
```

---

###  5. Crear una orden de reparación
**Ruta:**  
`POST http://localhost:3000/repair-orders`

**Cuerpo (JSON):**
```json
{
  "equipmentId": "a4b8b632-1df3-4c12-84e8-29ab8c1a22a1",
  "problemDescription": "Laptop does not power on.",
  "diagnosis": "Power circuit issue.",
  "estimatedCost": 150.5,
  "details": [
    {
      "repairOrderId": "c0cbe78e-8a26-4b91-a8f7-44baf820aa12",
      "serviceId": "ff98e41b-3e01-4a99-bd90-c2cc8513e213",
      "technicianId": "bda2b7d1-c8d9-47a5-b6f1-47f5a98f52d7",
      "unitPrice": 100,
      "discount": 10,
      "notes": "Performed full diagnostic on motherboard."
    }
  ],
  "parts": [
    {
      "repairOrderId": "c0cbe78e-8a26-4b91-a8f7-44baf820aa12",
      "partId": "c0cbe78e-8a26-4b91-a8f7-44baf820aa12",
      "quantity": 2,
      "imgUrl": "https://example.com/parts/img123.jpg"
    }
  ]
}
```

---

###  6. Agregar un repuesto
**Ruta:**  
`POST http://localhost:3000/spare-parts`

**Cuerpo (JSON):**
```json
{
  "name": "SSD 500GB Kingston",
  "description": "Solid State Drive compatible with laptops and desktops.",
  "stock": 25,
  "unitPrice": 65.99
}
```

---

##  Conclusión

Con esta práctica se logró crear una **API REST completa** en NestJS, aplicando conceptos como controladores, servicios, DTOs y entidades.  
Además, se comprendió cómo estructurar un proyecto modular y cómo realizar **peticiones POST** para crear registros dentro del sistema.
