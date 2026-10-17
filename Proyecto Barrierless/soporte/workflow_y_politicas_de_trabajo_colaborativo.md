# Estrategias de trabajo colaborativo con Git

## 1. Flujos de trabajo

### Flujo de trabajo con ramas

El uso de ramas es fundamental para el trabajo en equipo, ya que permite a cada desarrollador trabajar en características o correcciones específicas sin afectar el código principal.

- Cada integrante crea su propia rama y trabaja sobre ella, sin tocar `main`.
- Para integrar los cambios, el integrante abre un **Pull Request (PR)**.
- El líder revisa los cambios propuestos para no afectar `main`.
- Una vez revisados, se hace **squash and merge** directamente en `main`.

> Es un proceso altamente burocrático, pero muy necesario para evitar errores fatales.

### Flujo basado en ramas permanentes

La idea principal es tener ramas que duran para siempre y que representan distintos estados o etapas del proyecto, por ejemplo:

- La versión que usa el usuario final (producción).
- La versión en la que se trabaja actualmente (desarrollo).

### Flujo basado en bifurcaciones (forks)

En lugar de compartir un único repositorio central con permisos de escritura para todos, cada colaborador crea una copia completa (*fork*) del proyecto en su propia cuenta de GitHub.

- Los cambios se trabajan de forma local.
- Se proponen al repositorio original mediante un PR.

---

## 2. Integración de cambios

| Método | Qué hace | Resultado en el historial |
|---|---|---|
| **Merge commit** | Toma todos los commits de una rama secundaria y crea un commit de fusión especial en la rama principal que conecta la historia de ambas. | Se conservan todos los commits tal cual, más el commit de fusión. |
| **Squash and merge** | Toma todos los commits individuales de la rama secundaria, los condensa ("aplasta") en un único commit nuevo y lo coloca en la rama principal. | Un solo commit por rama; historial limpio. |
| **Rebase** | "Despega" los commits de la rama y los vuelve a "pegar" uno a uno sobre el último commit de `main`, como si el desarrollo hubiera iniciado sobre la versión más reciente. | Historial lineal, reescrito para que aparezca más reciente. |

---

## 3. Decisión: ¿cuál encaja mejor con nuestro proyecto?

**Elegimos el flujo de trabajo con ramas.**

**Justificación:** cada integrante realiza su propio trabajo en su propia rama y en sus propios archivos. De esta forma se evita que todos trabajen de forma asíncrona sobre un único archivo, lo que reduce los conflictos al hacer merge.

---

## 4. Políticas concretas

### Nombres de ramas

```text
feature/[#]-[acción]-[nombre]
```

### Mensajes de commit

| Prefijo | Uso |
|---|---|
| `docs` | Cambios en documentación |
| `feat` | Cambios en acciones o nuevas funcionalidades |
| `fix` | Cuando se arregla algo dentro del repositorio |

### Requisitos para integrar un PR

- Alguien del equipo debe revisarlo.
- El robot realiza la verificación automática.
- El revisor redacta una descripción de los cambios realizados.

### Método de integración

Mediante PR. Se revisa y, si todo está bien, se hace **squash and merge**.

### Ramas protegidas y reglas

- Ramas protegidas: `main` y `docs` (documentación).
- Los cambios en ellas se hacen **únicamente mediante PR**.

### Qué revisaría un robot

Revisaría los PR (verificación automática antes de la revisión humana).

### Resolución de conflictos y deshacer errores

- Los conflictos se resuelven en equipo.
- Se revisa qué causó el error.
- Se corrige lo que sea necesario.