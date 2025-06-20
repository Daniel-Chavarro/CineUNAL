# Guía de Contribución - Proyecto CineUNAL

Este documento proporciona las directrices para contribuir al proyecto CineUNAL de manera efectiva y organizada. Por favor, lee esta guía antes de comenzar a trabajar en el proyecto.

## Tabla de Contenidos

1. [Organización del Equipo](#organización-del-equipo)
2. [Flujo de Trabajo Git](#flujo-de-trabajo-git)
3. [Normas de Codificación](#normas-de-codificación)
4. [Gestión de Issues](#gestión-de-issues)
5. [Revisión de Código](#revisión-de-código)
6. [Pruebas](#pruebas)
7. [Despliegue](#despliegue)

## Organización del Equipo


### Asignación de Tareas

- Las tareas se gestionan a través de **Issues de GitHub** en el repositorio.
- Cada miembro debe asignarse issues según su disponibilidad.
- Si vas a trabajar en una issue, asígnate a ti mismo y mueve la issue a "En progreso".
- Cuando termines, crea un Pull Request y mueve la issue a "En revisión".

## Flujo de Trabajo Git

### Estructura de Ramas

- **main**: Rama principal que contiene código estable y listo para producción.
- **develop**: Rama de desarrollo donde se integran todas las características.
- **feature/nombre-característica**: Ramas para desarrollar nuevas características.
- **bugfix/nombre-bug**: Ramas para corregir errores.
- **release/versión**: Ramas para preparar lanzamientos.

### Proceso de Contribución

1. **Crear una rama**: Desde `develop`, crea una nueva rama siguiendo la nomenclatura:
   ```
   git checkout develop
   git pull
   git checkout -b feature/nombre-caracteristica
   ```

2. **Realizar cambios**: Implementa tu funcionalidad o corrección en la rama.

3. **Commits frecuentes**: Realiza commits pequeños y frecuentes con mensajes claros:
   ```
   git add .
   git commit -m "Tipo: Breve descripción del cambio"
   ```
   Tipos de commit: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`.

4. **Push y Pull Request**: Sube tus cambios y crea un Pull Request a `develop`:
   ```
   git push origin feature/nombre-caracteristica
   ```
   Luego crea el PR en GitHub.

5. **Revisión de código**: Espera a que tu código sea revisado por al menos un miembro del equipo.

6. **Merge**: Una vez aprobado, se realizará el merge a `develop`.

### Resolución de Conflictos

Si encuentras conflictos al hacer merge:

1. Actualiza tu rama `develop`:
   ```
   git checkout develop
   git pull
   ```

2. Vuelve a tu rama y realiza un rebase:
   ```
   git checkout feature/nombre-caracteristica
   git rebase develop
   ```

3. Resuelve los conflictos manualmente, luego:
   ```
   git add .
   git rebase --continue
   ```

4. Finalmente, actualiza tu rama remota:
   ```
   git push origin feature/nombre-caracteristica --force
   ```
   (Usa `--force` con precaución y solo en ramas de características que nadie más esté utilizando)

## Normas de Codificación

### Estilo de Código

- **Nombres**: 
  - Clases: PascalCase (ej. `PeliculaController`)
  - Métodos y variables: camelCase (ej. `obtenerPelicula()`)
  - Constantes: SNAKE_CASE_MAYÚSCULA (ej. `MAX_ASIENTOS`)
- **Comentarios**: Documentar todas las clases y métodos públicos con JavaDoc.

### Estructura del Proyecto

Respetar la estructura de paquetes:
- `org.cineUNAL.model`: Clases de entidades y objetos de dominio
- `org.cineUNAL.controller`: Lógica de negocio y controladores
- `org.cineUNAL.view`: Interfaces gráficas y componentes visuales
- `org.cineUNAL.utils`: Utilidades y herramientas comunes
- `org.cineUNAL.dao`: Acceso a datos y persistencia

## Gestión de Issues

### Creación de Issues

- Usar plantillas proporcionadas para diferentes tipos de issues.
- Incluir descripción clara, criterios de aceptación y etiquetas relevantes.
- Asignar prioridad y estimación de tiempo.

### Etiquetas

- `bug`: Errores a corregir
- `feature`: Nuevas funcionalidades
- `enhancement`: Mejoras a funcionalidades existentes
- `documentation`: Cambios en la documentación
- `frontend`: Relacionado con la interfaz de usuario
- `backend`: Relacionado con la lógica del servidor
- `database`: Relacionado con la persistencia de datos
- `prioridad-alta/media/baja`: Nivel de prioridad

### Estados de Issues

- `Por hacer`: Issue pendiente de asignación
- `En progreso`: Issue asignada y en desarrollo
- `En revisión`: Desarrollo completado, esperando revisión
- `Completada`: Issue finalizada y verificada

## Revisión de Código

### Proceso de Pull Request

1. Crear PR con descripción detallada de los cambios.
2. Referenciar la issue que resuelve (ej. "Closes #123").
3. Asignar revisores relevantes.
4. Esperar aprobación antes de hacer merge.

### Criterios de Revisión

- El código cumple con las normas de estilo.
- Se han añadido pruebas adecuadas.
- El código es comprensible y está bien documentado.
- La funcionalidad cumple con los criterios de aceptación.
- No introduce deuda técnica innecesaria.

## Pruebas

### Tipos de Pruebas

- **Unitarias**: Para clases y métodos individuales.
- **Integración**: Para interacciones entre componentes.
- **Funcionales**: Para verificar que se cumplen los requisitos.

### Cobertura

- Se espera una cobertura mínima del 70% en el código del proyecto.
- Todas las clases del modelo y los controladores deben tener pruebas.

### Ejecución

- Ejecutar pruebas localmente antes de cada push:
  ```
  mvn test
  ```
- Recomiendo que utilices un IDE como IntelliJ IDEA o Eclipse para facilitar la ejecución de pruebas.
- Ademas es recomendable el uso de IA para generar pruebas unitarias y de integración.

## Despliegue

### Entornos

- **Desarrollo**: Para pruebas internas durante el desarrollo (develop).
- **Producción**: Versión estable para usuarios finales (main).

### Proceso de Release

1. Crear rama `release/vX.Y.Z` desde `develop`.
2. Realizar ajustes finales y pruebas.
3. Merge a `main` y etiquetar la versión.
4. Merge de vuelta a `develop`.

---

## Recordatorio

Recuerda que este proyecto es parte de un trabajo académico y debe cumplir con las normas de integridad académica de la Universidad Nacional de Colombia.

---

*Última actualización: 19 de junio de 2025*
