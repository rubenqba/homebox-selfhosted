# Homebox Deployment with Docker Compose

Este repositorio contiene los archivos necesarios para desplegar **Homebox**, un sistema de gestión de inventario personal, utilizando Docker Compose. A continuación se detalla la configuración requerida y los pasos para su despliegue.

---

## 📋 Requisitos previos

1. **Docker y Docker Compose** instalados
2. **Red Docker para Traefik** preexistente
3. **Volumen Docker** creado manualmente
4. Traefik configurado como reverse proxy

---

## ⚙️ Configuración

### 1. Volumen de datos

- Se utilizará un volumen Docker para persistir los datos de Homebox.
- Nombre del volumen: Definido por la variable `INVENTORY_DATA_VOLUME` (valor por defecto: `homebox-data`).
- Verifique que el volumen exista o se creará automáticamente al desplegar.

```bash
# Crear volumen manualmente antes del despliegue
docker volume create homebox-data -d local --opt device=/path/to/dir --opt type=bind --opt o=none
```

---

## 🔧 Configuración Requerida

### Variables de entorno
| Variable                  | Valor por defecto   | Función                                 |
|---------------------------|---------------------|-----------------------------------------|
| `PROXY_NETWORK_NAME`      | `proxy`             | Nombre de la red Docker para Traefik    |
| `INVENTORY_DATA_VOLUME`   | `homebox-data`      | Volumen persistente para datos del servicio |
| `INVENTORY_HOSTNAME`      | -                   | Hostname para el servicio de `reverse-proxy` |

### Personalización obligatoria
1. Definir el dominio en las etiquetas de Traefik (`INVENTORY_HOSTNAME`)
2. Verificar nombres de red y volumen coincidan con su entorno



