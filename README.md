Proyecto Red Local: GIMNASIO

Este repositorio contiene la propuesta integral de diseño y configuración de red local para una empresa de servicios deportivos de alta tecnología. El proyecto ha sido desarrollado para el módulo de **Redes Locales** dentro del Proyecto Intermodular.

## Descripción del Proyecto
El objetivo es diseñar una infraestructura de red corporativa que integre de forma segura los servicios administrativos de un gimnasio, un ecosistema domótico avanzado para una gestión "inteligente" (IoT), y una conectividad pública transparente y segura para los clientes.

## 1. Diagrama de Topología de Red
Se ha optado por una topología en estrella segmentada lógicamente para garantizar la seguridad y el rendimiento.

---
#### Mapa Visual de la Infraestructura
<img width="2324" height="1020" alt="image" src="https://github.com/user-attachments/assets/8eb57aec-5b24-476d-ab47-f229a23478ac" />

---

## 2. Arquitectura y Tecnologías
La simulación se ha realizado con **Cisco Packet Tracer**. Los componentes clave son:

* **Capa de Core/Distribución:** Router Cisco 4331 (gestionando subinterfaces y ACLs) y Switch Cisco 2960-24TT (segmentación de VLANs).
* **Capa de Acceso:** Una mezcla densa de dispositivos finales, incluyendo PCs, laptops y dispositivos IoT.
* **Movilidad:** Despliegue de múltiples Puntos de Acceso (AP) para una cobertura inalámbrica total.

## 3. Plan de Direccionamiento IP (/24)
La red se ha segmentado en tres VLANs lógicas para aislar el tráfico y aplicar políticas de seguridad.

| VLAN | Nombre | Subred (Red: 192.10.x.0) | Gateway (Router) | Propósito de la Red |
| :--- | :--- | :--- | :--- | :--- |
| **10** | GESTIÓN | `192.10.10.0 /24` | `192.10.10.1` | PCs Administrativos (Recepción, Gerencia) y Tornos de acceso. |
| **20** | IOT | `192.10.20.0 /24` | `192.10.20.1` | Domótica avanzada (Webcams, Sensores, Altavoces, Ventiladores). |
| **30** | CLIENTES | `192.10.30.0 /24` | `192.10.30.1` | WiFi público para Smartphones y Tablets de los socios. |

## 4. Servicios y Seguridad (ACL)
Para garantizar la integridad de los datos de la empresa, se han implementado los siguientes servicios:

* **DHCP Dinámico:** Asignación automática de IPs para facilitar la conexión de clientes inalámbricos.
* **Enrutamiento Inter-VLAN:** El Router actúa como Gateway permitiendo la comunicación privada entre Gestión e IoT.
* **Aislamiento de Clientes (Seguridad):** Se ha configurado una Lista de Control de Acceso (ACL Extendida) en el Router. Esta política permite a los clientes de la VLAN 30 acceder a Internet, pero bloquea estrictamente cualquier intento de comunicación con las redes privadas (VLAN 10 y 20).

## 5. Pruebas de Funcionamiento (Testing)

A continuación, se demuestran los flujos de comunicación y las restricciones de seguridad mediante pruebas de conectividad (ping).

### Flujo 1: Conectividad Interna (Gestión a IoT)
Prueba exitosa que demuestra que los servicios privados (ej: PC de recepción) pueden monitorizar los equipos domóticos (ej: una Webcam).

---
<img width="891" height="688" alt="image" src="https://github.com/user-attachments/assets/14eea0ef-4143-4489-9ce4-648e3fd4ee02" />

---

### Flujo 2: Bloqueo de Seguridad (Clientes a Red Privada)
Prueba que demuestra el aislamiento de seguridad. Un Smartphone de un cliente intenta conectarse a un PC de la administración y el Router bloquea el paquete.

---
<img width="886" height="688" alt="image" src="https://github.com/user-attachments/assets/e2461671-9877-469f-bac3-b80610b6b0e8" />

---
