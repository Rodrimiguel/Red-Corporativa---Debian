# 🖧 Red Corporativa en Debian

Proyecto académico de simulación de una red corporativa completa con servicios fundamentales de infraestructura y seguridad, implementada en VirtualBox utilizando **Debian GNU/Linux**.

---

## 🎯 Objetivo

Diseñar, implementar y probar una red corporativa que integre los principales servicios de red y seguridad perimetral:

- 🔥 **Firewall**
- 🧩 **Proxy (Squid)**
- 🌐 **DNS (Bind9)**
- 💻 **Servidor WWW (Apache2)**
- 🔐 **Servidor RADIUS (FreeRADIUS)**
- 🖥️ **Cliente corporativo**
- 🌍 **Simulación de Internet exterior**

---

## 🗺️ Topología general

📸 *(Topología Red Corporativa)*  
![](https://github.com/Rodrimiguel/Red-Corporativa---Debian/blob/main/RedCorporativa.jpg)

---

## 💾 Direccionamiento IP y Roles

Antes de comenzar, definimos un **rango de direcciones IP único** para todo el laboratorio:  

- **Red del laboratorio:** `10.0.0.0/24`  
- **Máscara de red:** `255.255.255.0`  
- **Gateway de la LAN:** `10.0.0.1` (Firewall)  
- **DNS interno:** `10.0.0.4`  
- **DHCP:** desactivado en VirtualBox (IP manual en cada VM)  

| Rol / Máquina | Dirección IP | Función principal |
|----------------|--------------|------------------|
| **Firewall (FW)** | `10.0.0.1` | Gateway de red y NAT |
| **Syslog** | `10.0.0.2` | Registro centralizado de logs |
| **IDS** | `10.0.0.3` | Detección de intrusiones |
| **DNS** | `10.0.0.4` | Resolución de nombres internos |
| **RADIUS** | `10.0.0.5` | Autenticación de red |
| **Proxy (Squid)** | `10.0.0.6` | Control de acceso y caché web |
| **Web (Apache2)** | `10.0.0.7` | Servidor web corporativo |
| **SQL** | `10.0.0.8` | Base de datos del entorno |
| **VPN** | `10.0.0.9` | Acceso remoto seguro |

💡 **Nota:**  
El segmento `10.0.0.0/24` **no es asignado por defecto** por VirtualBox y debe configurarse manualmente.  
Esto evita conflictos entre participantes y asegura que todas las VMs puedan comunicarse dentro del mismo laboratorio.

---

## ⚙️ Servicios y configuraciones

### 🔥 Firewall (FW)
- Reglas con **iptables** para permitir tráfico interno y realizar **NAT** hacia el exterior.  
- Bloqueo de puertos no autorizados.  

### 🧩 Proxy (Squid)
- Filtrado de contenido y control de acceso HTTP.  
- Caché de navegación interna.  

### 🌐 DNS (Bind9)
- Resolución directa e inversa de dominios internos (`empresa.local`).  
- Redirección de consultas externas hacia **DNS públicos**.  

### 💻 WWW (Apache2)
- Servidor web interno con sitio corporativo básico.  
- Archivos ubicados en `/var/www/html`.  

### 🔐 RADIUS (FreeRADIUS)
- Autenticación centralizada para clientes.  
- Integración con servicios de red para control de acceso.  

---

## 🔍 Pruebas realizadas

- Comunicación entre todos los hosts (`ping` y `traceroute`).  
- Navegación controlada mediante proxy.  
- Resolución DNS interna y externa.  
- Autenticación exitosa de clientes contra RADIUS.  
- Acceso web interno y externo.  

---

## 📊 Resultados y Conclusiones

- La red logra comunicación estable entre todos los segmentos.  
- Los servicios funcionan de forma integrada.  
- Posibles mejoras: segmentación VLAN, firewall más granular, logs centralizados.  

---

## 🧠 Créditos

Proyecto realizado por **Rodrigo y equipo**, como parte de la simulación de una red corporativa en entorno virtual (**VirtualBox / Debian**).

---

📁 *Repositorio en desarrollo — configuraciones y scripts se documentarán en `/docs` y `/scripts`.*
