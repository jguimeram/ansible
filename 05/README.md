# Ansible - Gestión de Archivos y Recursos

En esta sección se exploran las capacidades de Ansible para trabajar con archivos locales y remotos utilizando el módulo `copy`.

## Estructura del Playbook (`playbook.yaml`)

El playbook en esta sección añade una tarea crítica: la copia de un recurso local (`index.html`) a un servidor remoto administrado.

### Módulo Clave Utilizado: `copy`

Se utiliza `ansible.builtin.copy` para transferir un archivo desde la máquina de control local (`./resources/index.html`) al servidor remoto administrado (`/var/www/html`).

### Atributos Clave

-   **src**: Ruta relativa o absoluta del archivo fuente en la máquina de control.
-   **dest**: Ruta absoluta de destino en el servidor remoto administrado.
-   **owner**: Usuario al que pertenecerá el archivo copiado.
-   **group**: Grupo al que pertenecerá el archivo copiado.
-   **mode**: Permisos en formato octal (`'0664'`) del archivo en el servidor remoto.

### Cómo ejecutar

```bash
# Ejecutar el playbook y verificar la copia del archivo index.html
ansible-playbook -i hosts.yaml playbook.yaml
```
