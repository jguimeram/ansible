# Ansible - Modularización con `include_tasks`

En esta sección se explora la capacidad de Ansible para dividir playbooks complejos en partes más manejables y reutilizables mediante la inclusión de archivos de tareas.

## Estructura del Playbook (`playbook.yaml`)

El playbook en esta sección utiliza el comando `include_tasks: add_task.yaml`.

### Beneficios de la Modularización

1.  **Reutilización**: Se pueden reutilizar conjuntos de tareas en diferentes playbooks.
2.  **Mantenibilidad**: Se simplifica la gestión de archivos largos de playbook.
3.  **Organización**: Se facilita la colaboración en equipo al separar responsabilidades.

### Cómo ejecutar

```bash
# Ejecutar el playbook y verificar que las tareas incluidas se ejecutan correctamente
ansible-playbook -i hosts.yaml playbook.yaml
```

### Contenido de `add_task.yaml`

Este archivo contiene tareas específicas que se incluirán en el flujo principal del Playbook, como la gestión de servicios o la configuración de red.
