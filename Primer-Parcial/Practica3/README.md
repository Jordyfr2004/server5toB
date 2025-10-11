# 🧩 Práctica 3 – Aplicación con Repositorios y Base de Datos (TypeScript)

## 📘 Descripción del proyecto
En esta práctica se amplió la estructura anterior (Práctica 2) incorporando el uso de **una base de datos**, **repositorios reales** y **datos iniciales (seeds)**.  
El objetivo fue aplicar los principios de **arquitectura por capas (DDD)**, ahora con una capa de persistencia que permita manejar información realista de **usuarios, técnicos, equipos, servicios, tickets, reseñas y partes**.

Este proyecto demuestra cómo conectar la lógica del dominio con una base de datos simulada o real, y cómo inicializarla con datos de prueba para validar su funcionamiento.

---

##  Estructura del proyecto

```
Practica3/
│
├── package.json           # Dependencias del proyecto
├── tsconfig.json          # Configuración de TypeScript
├── app.ts                 # Punto de entrada principal
│
├── src/
│   ├── application/       # Servicios del negocio (lógica de aplicación)
│   │   └── services/
│   │       ├── EquipmentService.ts
│   │       ├── TechnicianService.ts
│   │       ├── TicketService.ts
│   │       ├── UserService.ts
│   │       └── etc...
│   │
│   ├── domain/            # Capa del dominio (entidades, enums, repositorios base)
│   │   ├── entities/
│   │   ├── enums/
│   │   └── repositories/
│   │
│   └── infrastructure/    # Implementaciones reales de los repositorios
│       ├── db/
│       │   ├── data-source.ts       # Configuración de conexión
│       │   └── seeds/seed.ts        # Datos iniciales
│       └── repositories/            # Repositorios conectados a la BD
│
└── README.md
```

---

##  Tecnologías usadas

- **Node.js** – entorno de ejecución  
- **TypeScript** – lenguaje principal  
- **TypeORM / In-Memory DB** – conexión a base de datos  
- **npm** – gestor de dependencias  

---

##  Instalación y ejecución

1. **Abrir el proyecto en VS Code**  
   Asegúrate de estar dentro de la carpeta principal (`Practica3/Practica3`).

2. **Instalar dependencias**
   ```bash
   npm install
   ```

3. **Compilar el proyecto**
   ```bash
   npx tsc
   ```

4. **Ejecutar el proyecto**
   ```bash
   npx ts-node src/app.ts
   ```
   o si ya está compilado:
   ```bash
   node dist/app.js
   ```

---

##  Explicación de las capas

- **Domain:**  
  Define las entidades (`User`, `Ticket`, `Technician`, `Service`, etc.), enums (roles, estados) y contratos de repositorios.  
  Representa el "corazón" del sistema.

- **Application:**  
  Contiene los **servicios** que implementan la lógica del negocio.  
  Por ejemplo: `UserService`, `TicketService`, `PartService`, etc.

- **Infrastructure:**  
  Contiene las implementaciones concretas de los repositorios y la conexión a la base de datos.  
  En `db/seed.ts` hay datos iniciales para hacer pruebas sin usar una BD real.

---

##  Conclusión

Con esta práctica comprendí cómo integrar **repositorios y base de datos** dentro de una arquitectura en capas.  
Fue posible crear entidades completas, inicializar datos (seeds) y organizar correctamente las responsabilidades del sistema.  
Esto facilita el desarrollo escalable y bien estructurado de aplicaciones reales en **TypeScript**.
