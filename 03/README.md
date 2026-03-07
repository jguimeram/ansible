# Ansible - Definición de Tareas en un Play

En esta sección se profundiza en la estructura de un Playbook. Un **Play** es un conjunto de tareas que se ejecutan contra un grupo de hosts específico.

## Estructura del Playbook (`playbook.yaml`)

En este ejemplo se introducen las siguientes tareas:

-   **Ping**: Para verificar la conectividad inicial.
-   **Módulo Shell**: Se utiliza `ansible.builtin.shell` para ejecutar un comando de shell puro (`touch /tmp/file.txt`). Se debe preferir el uso de módulos específicos cuando sea posible por motivos de idempotencia.

### Anatomía del Playbook

Un Playbook se compone de una o más secciones llamadas **Plays**. Cada Play debe contener:

1.  **name**: Una descripción breve del propósito del Play.
2.  **hosts**: El grupo de inventario al que se dirige.
3.  **tasks**: La lista de operaciones a realizar de forma secuencial.

### Ejecución Recomendada

```bash
# Ejecutar el playbook y verificar la creación del archivo
ansible-playbook -i hosts.yaml playbook.yaml
```
