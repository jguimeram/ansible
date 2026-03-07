# Ansible - Gestión de Inventarios

En esta sección se exploran las dos formas principales de definir un inventario en Ansible: **INI** y **YAML**. El inventario es la fuente de verdad que indica a Ansible sobre qué servidores (hosts) debe actuar.

## Estructura de Archivos

*   `hosts`: Inventario en formato **INI**. Es el formato tradicional, simple y directo. Define grupos como `[debian]`, `[rocky]`, etc.
*   `hosts.yaml`: Inventario en formato **YAML**. Es el estándar moderno, más estructurado y jerárquico.
*   `ansible.cfg`: Configuración local que define parámetros como el inventario por defecto y la desactivación de la comprobación de claves SSH (`host_key_checking`).

## Comandos de Verificación

Puedes verificar la estructura de tus inventarios con los siguientes comandos:

```bash
# Ver inventario en formato gráfico (árbol)
ansible-inventory -i hosts.yaml --graph

# Listar todos los hosts
ansible-inventory -i hosts --list
```
