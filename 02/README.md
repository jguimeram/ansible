# Ansible - Ejecución de Playbooks Básicos

En esta sección se introduce el concepto de **Playbook** como la forma de automatizar tareas complejas en Ansible. En lugar de ejecutar comandos ad-hoc, el playbook permite definir el estado deseado en un archivo YAML reproducible.

## Estructura del Playbook (`ping.yaml`)

El playbook utiliza el módulo `ansible.builtin.ping` para verificar la conectividad con los nodos administrados. A diferencia de un `ping` de red ICMP ordinario, este módulo verifica que la conexión SSH esté activa y que el entorno de ejecución de Python esté disponible en el nodo remoto.

### Cómo ejecutar un Playbook

Para ejecutar el playbook utilizando el inventario YAML proporcionado:

```bash
# Ejecutar el playbook contra todos los hosts
ansible-playbook -i hosts.yaml ping.yaml

# Ejecutar el playbook contra un subconjunto (ej. app_servers)
ansible-playbook -i hosts.yaml ping.yaml --limit app_servers
```
