# 🍽️ Sistema de Gestión de Restaurantes (SGR) | Proyecto en Java

<div align="center">
  
  <img src="https://github.com/user-attachments/assets/367f5203-b59c-4773-bc67-7dacd7cb48fa" alt="Logo de CSS" width="400"/>
  
  <p>Una solución integral en Java para optimizar las operaciones del restaurante CSS.</p>
  
  <br>

  ---
  
</div>

## ✨ Visión General del Proyecto

El **Sistema de Gestión de Restaurantes (SGR)**, desarrollado en **Java**, es una plataforma robusta diseñada a medida para el restaurante **CSS**.  
Su objetivo es optimizar y automatizar la gestión diaria del establecimiento, abarcando desde la **toma de pedidos** y el **control de cocina** hasta la **facturación detallada** y la **generación de informes**.

> **⚠️ Restricción de Uso:** Este sistema ha sido desarrollado exclusivamente para el restaurante CSS y su uso está limitado a este establecimiento.

El SGR combina diseño modular, persistencia en base de datos y una interfaz gráfica intuitiva, demostrando la aplicación práctica de los principios de la **Ingeniería de Software** y la **Programación Orientada a Objetos**.

---

## 🚀 Características Principales

Módulos clave implementados para asegurar un flujo de trabajo eficiente:

| Característica | Descripción |
| :--- | :--- |
| **Mesas y Meseros** | Asignación, seguimiento del estado de las mesas y administración del personal de servicio. |
| **Punto de Venta (POS)** | Interfaz rápida e intuitiva para la selección de productos y gestión de pedidos en curso. |
| **Control de Cocina** | Visualización en tiempo real de los pedidos pendientes, listos para ser preparados. |
| **Facturación Detallada** | Generación y manejo eficiente de facturas, incluyendo cierres de mesa. |
| **Informes y Resúmenes** | Acceso a datos clave del negocio (pedidos, ventas, rendimiento) para la toma de decisiones. |

---

## 🗂️ Organización de Carpetas

La estructura del proyecto sigue el **patrón multicapa (DAO – Lógica – Presentación)**, lo que garantiza un código más limpio, mantenible y escalable.

<p align="center">
<img width="403" height="686" alt="image" src="https://github.com/user-attachments/assets/f373ca8c-80b2-427b-b169-e5f80f9950d2" />
<br>
</p>

### 1. Capa de Datos y Persistencia
* **DAO (Data Access Objects):** abstraen y centralizan toda la lógica de comunicación con la base de datos.  
  Permiten cambiar la tecnología de persistencia (por ejemplo, de MySQL a PostgreSQL) sin afectar la lógica principal.

### 2. Abstracciones y Estructuras (POO)
* **Clases Abstractas:** definen estructuras comunes y métodos generales que deben seguir las entidades (p. ej. `Producto`).
* **Clases Concretas:** implementan estas plantillas para crear objetos funcionales (p. ej. `Mesa`, `Bebida`).
* **Interfaces:** establecen contratos de funcionalidad que garantizan organización y cohesión en el código (p. ej. `MesaService`).

### 3. Manejo de Errores
* **Excepciones Personalizadas:** gestionan situaciones anómalas (p. ej. `StockInsuficienteException`), evitando fallos inesperados y mejorando la estabilidad del sistema.

### 4. Interfaz de Usuario (Capa de Presentación)
* **Formularios (Forms):** cada ventana representa un módulo funcional (p. ej. Carta, Cocina, Acerca).
* **Ventana Principal:** actúa como **dashboard central**, coordinando la navegación hacia todas las funcionalidades del sistema.

---

## ⚙️ Requisitos del Sistema

### 💻 Entorno de Ejecución

* **Java:** [Java Development Kit (JDK) 24](https://www.oracle.com/java/technologies/javase/jdk24-downloads.html) o superior.

### 💾 Base de Datos

* **Motor:** MariaDB  
* **Gestión:** HeidiSQL  
* **Configuración:** el proyecto incluye un script SQL para crear la base de datos y sus tablas.  
  Asegúrese de que la instancia de MariaDB esté activa y accesible antes de ejecutar el programa.

---

## 🧩 Guía de Ejecución

Siga estos pasos para ejecutar el sistema correctamente:

1. **Instalar JDK 24** o superior.  
2. **Clonar o descargar** el proyecto desde GitHub.  
3. **Configurar la base de datos** en MariaDB ejecutando el script incluido.  
4. **Abrir el proyecto** en su IDE preferido (recomendado: NetBeans o IntelliJ IDEA).  
5. Localizar la clase principal: `BienvenidaMenuInicial.java`.  
6. **Ejecutar** el programa y comenzar a interactuar con el sistema.  

---

## 🧭 Flujo de Uso del Sistema

El siguiente esquema describe los pasos que seguiría un usuario (mesero, cajero o encargado) para utilizar el sistema de manera normal y eficiente en el día a día del restaurante.

---

### 1. 🍽️ Carta
- Permite **visualizar los productos actuales** del restaurante con la siguiente información:
  - **Nombre del producto**
  - **Precio**
  - **Stock disponible**
  - **Disponibilidad** (activo/inactivo)
  - **Categoría** (p. ej. bebida, plato principal, postre)
- Desde esta ventana también se pueden:
  - **Modificar productos existentes** (actualizar precio, stock, categoría, etc.).
  - **Crear nuevos productos** para ampliar la oferta gastronómica.
- Mantener la carta actualizada es fundamental para evitar errores al registrar pedidos en las mesas.

---

### 2. 🪑 Mesas
- Muestra las **12 mesas del restaurante**, cada una identificada visualmente según su estado:
  - 🟥 **Rojo:** Ocupada  
  - ⬜ **Blanco:** Disponible  
  - 🟨 **Amarillo:** Reservada  
  - 🟩 **Verde:** En limpieza  
- Al seleccionar una mesa disponible:
  1. Se **abre una cuenta** asociada a esa mesa.  
  2. Se **asigna el mesero** que la atenderá.  
  3. Se comienzan a **cargar los pedidos** solicitados por el cliente.  
- Una vez completados los pedidos, se presiona **“Enviar”** para que sean enviados al módulo **Cocina**.

---

### 3. 👨‍🍳 Cocina
- En este módulo se **reciben los pedidos enviados desde las mesas**.  
- Funciona como una **comanda digital**, mostrando los productos pendientes de preparación y su respectivo orden.  
- Cada pedido puede cambiar su **estado** a medida que avanza en el proceso:
  - **Pendiente → En preparación → Servido**
  - También puede marcarse como **Cancelado** si el pedido se anula antes de servirse.
- Este módulo permite que los cocineros gestionen la secuencia de trabajo y los meseros verifiquen el progreso de los pedidos.

---

### 4. 💰 Facturación
- Una vez que el cliente solicita pagar su cuenta:
  1. Ingresar al módulo **Facturas**.  
  2. **Seleccionar la mesa** correspondiente.  
  3. Elegir el **método de pago** (efectivo, tarjeta, etc.).  
  4. Aplicar un **descuento del 5%, 10% o 15%** si corresponde.  
  5. Generar el **comprobante de pago** para el cliente.  
- Al cerrar la cuenta, la mesa vuelve automáticamente al estado **disponible**.

---

### 5. 📊 Resumen
- Módulo destinado al **análisis y control general** del restaurante.  
- Permite:
  - Consultar los **pedidos realizados en el día**.  
  - Ver los **pedidos por cada mesa**.  
  - Identificar los **tres productos más vendidos** del día.  
- Es una herramienta clave para el encargado o administrador al cierre de la jornada.

---

### ✅ Flujo General Resumido

1. **Carta:** Configurar o actualizar productos.  
2. **Mesas:** Seleccionar mesa, abrir cuenta y asignar mesero.  
3. **Pedidos:** Registrar pedidos y enviarlos a cocina.  
4. **Cocina:** Preparar los pedidos y actualizar su estado.  
5. **Facturas:** Cobrar al cliente, aplicar descuentos y generar comprobante.  
6. **Resumen:** Revisar pedidos del día y estadísticas generales.

---

> Este flujo refleja el funcionamiento real de un restaurante profesional, garantizando una gestión ordenada, fluida y eficiente desde la toma del pedido hasta la facturación final.

---

## 🖥️ Módulos de la Interfaz (Screenshots)

Las siguientes capturas muestran las principales pantallas del sistema, desde la bienvenida hasta la gestión de pedidos y facturación.

<p align="center">
  <img src="https://github.com/user-attachments/assets/3feba958-3e64-4ecf-87c3-c7199cdbfe05" alt="Vista del menú principal del SGR" width="600" />
  <br>
  <i>Menú Principal del Sistema.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/716df9df-1f92-4152-b494-d9972b6de7a5" alt="Menú de bienvenida inicial" width="600" />
  <br>
  <i>Ventana de Bienvenida Inicial.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d1af79fa-f5a1-4d8f-83de-3d208e3d8520" alt="Interfaz de usuario del módulo de Carta/Menú" width="600" />
  <br>
  <i>Módulo de Carta / Menú.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/44e09d64-044e-4f0e-87c9-3a219cf771ff" alt="Interfaz de usuario del módulo de Cocina" width="600" />
  <br>
  <i>Módulo de Cocina.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/b2919abe-b62e-4adc-8454-af841dc1c884" alt="Interfaz de usuario del módulo de Facturación" width="600" />
  <br>
  <i>Módulo de Facturación.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/7cfe0c5b-5f73-4ed2-b965-65e84c4d725d" alt="Interfaz de usuario para la Selección de mesas" width="600" />
  <br>
  <i>Selección de Mesas.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/9c4a3910-c509-42c6-a8d8-1fbafdb30faa" alt="Interfaz de usuario para el Manejo de mesas" width="600" />
  <br>
  <i>Gestión de Mesas.</i>
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/92adf3c8-0588-4df6-938d-a37b50c94a24" alt="Interfaz de usuario del Resumen" width="600" />
  <br>
  <i>Resumen e Informes.</i>
</p>

---

## 📎 Recursos Externos

### 🔸 Diagrama UML
El diagrama UML por su tamaño se encuentra alojado en el siguiente enlace:

[**Acceder al diagrama UML**](https://drive.google.com/file/d/1ze_hoKHIy_gUFDDabduETDyWlQq7xwLY/view?usp=sharing)

### 🔸 Creación de la Base de Datos
La documentación completa de la base de datos está disponible en el siguiente enlace:

[**Acceder a la Base de Datos (SQL)**](https://docs.google.com/document/d/1CbDZiO3eitz26q_SBT3Nu6D-5uoRq0OSP_CJCVtZcW0/edit?usp=drive_link)

---

## 🤝 Contribución y Desarrollo

Este proyecto es el resultado del esfuerzo conjunto del equipo de desarrollo.

* **Reporte de Errores / Sugerencias:** Abra un **Issue** en este repositorio para reportar problemas o proponer mejoras.  
* **Aportes de Código:** Las contribuciones mediante **Pull Requests** son bienvenidas para corregir o ampliar funcionalidades.

---

## 👥 Equipo de Desarrollo

| Nombre | Usuario de GitHub |
| :--- | :--- |
| **Ezequiel Costa** | [@Costa200513](https://github.com/Costa200513) |
| **Thiago Sosa** | [@RetrOSys](https://github.com/RetrOSys) |

<p align="center">
  <img width="600" height="600" alt="Imagen del equipo" src="https://github.com/user-attachments/assets/f2b39efa-dca6-4503-99f5-c5b08e27d426" />
</p>

---

<p align="center">
  <i>© 2025 Sistema de Gestión de Restaurantes (SGR) - Proyecto académico del equipo CSS.</i>
</p>
