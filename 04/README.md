# Ansible - Playbooks con Múltiples Plays

En esta sección se explora la capacidad de un Playbook para ejecutar diferentes conjuntos de tareas contra diferentes grupos de servidores en una única ejecución.

## Estructura del Playbook (`playbook.yaml`)

El playbook en esta sección contiene dos **Plays**:

-   **Play 1 (Test play)**: Se dirige al grupo `app_servers` para realizar una prueba de `ping` y crear un archivo temporal con el módulo `shell`.
-   **Play 2 (Install nginx)**: Se dirige al grupo `debian` para realizar tareas de administración de sistemas más complejas.

### Módulos Clave Utilizados

-   **ansible.builtin.service**: Para la gestión de servicios (detener `apache2` e iniciar `nginx`).
-   **ansible.builtin.apt**: Para la gestión de paquetes en sistemas basados en Debian/Ubuntu (`apt install nginx`).
-   **state: latest**: Asegura que el paquete esté actualizado a la última versión disponible.

### Cómo ejecutar

```bash
# Ejecutar todo el playbook para instalar nginx
ansible-playbook -i hosts.yaml playbook.yaml
```
