# Evaluacion-Parcial-1-Nivel-intermedio-Vc

📁 Estructura del proyecto

devops-wisdom/
├── .github/
│   └── workflows/
│       └── ci-cd.yml    → Pipeline de CI/CD (validación y despliegue)
├── index.html            → Estructura de la página
├── style.css             → Estética 
├── script.js             → Lógica
├── phrases.js            → Banco de datos de frases
└── README.md             → Documentación del proyecto

🌳 Estrategia de ramificación

Para este proyecto individual se adoptó **GitHub Flow con un entorno intermedio (lightweight GitFlow)**:
* **`main`**: Rama de producción. Contiene el código estable e invulnerable que se despliega automáticamente.
* **`develop`**: Rama de integración/staging. Refleja los cambios validados antes de ser promovidos a producción.
* **`feature/<nombre>` / `fix/<nombre>`**: Ramas efímeras para desarrollo de características o correcciones de errores.

**Justificación:** Dado que el trabajo es desarrollado por una solo integrante, mantener un GitFlow complejo generaría un costo administrativo innecesario. Esta estrategia ligera simplifica la trazabilidad, exige validar los cambios en `develop` antes de subirlos a `main` y simula un flujo profesional sin entorpecer el ritmo de trabajo.

📝 Convenciones de commits

Se adoptó el estándar **Conventional Commits** para mantener un historial limpio, legible y estructurado.

* **Formato:** `<tipo>(<alcance opcional>): <descripción corta en presente>`
* **Tipos permitidos:**
  * `feat`: Nueva funcionalidad (ej: `feat: agrega animación cursor titilante`)
  * `fix`: Corrección de un fallo (ej: `fix: corrige error de sintaxis en phrases.js`)
  * `docs`: Cambios en documentación (ej: `docs: actualiza estrategia de ramificación`)
  * `style`: Ajustes estéticos o formato sin cambiar lógica (ej: `style: ajusta tono verde fósforo`)
  * `ci`: Modificaciones en flujos de integración/despliegue continuo (ej: `ci: añade linter HTML`)

**Justificación:** Facilita la auditoría de cambios y permite integrar herramientas de automatización de releases o changelogs a futuro.

🔀 Convenciones de naming de ramas

Las ramas se nombran siguiendo una estructura jerárquica clara en minúsculas y separada por guiones:

* `feature/<descripción-corta>` → Ejemplo: `feature/boton-sonido`
* `fix/<descripción-corta>` → Ejemplo: `fix/animacion-tipeo`
* `ci/<descripción-corta>` → Ejemplo: `ci/pipeline-github-actions`
* `docs/<descripción-corta>` → Ejemplo: `docs/actualizar-readme`

🔍 Estrategia de revisión (Pull Requests)

A pesar de ser un proyecto individual, los cambios **nunca se suben directamente a `main` o `develop`**. Todo cambio pasa por un Pull Request (PR).

* **Criterios de aprobación de un PR:**
  1. Superar exitosamente los checks automáticos del Pipeline de CI (verificación de sintaxis HTML/JS).
  2. Auto-revisión de código (*Self-code-review*) verificando que no se rompa la estética offline/Vanilla JS.
  3. Ausencia de conflictos de merge.

⚙️ Automatización (CI/CD)

Se configuró un flujo de **GitHub Actions** (`.github/workflows/ci-cd.yml`) con dos etapas:

1. **Integración Continua (CI):** Se ejecuta en cada `push` o `Pull Request` hacia las ramas `develop` y `main`. Comprueba automáticamente que los archivos JS no tengan errores de sintaxis (`node -c`) y analiza el HTML con `htmlhint`.
2. **Despliegue Continuo (CD):** Al hacer merge o push directo en `main`, tras aprobar las pruebas, el sitio se despliega automáticamente en **GitHub Pages**.

> **Impacto en DevOps:** Asegura el principio de "fail fast" (fallar rápido) detectando errores de código básico antes de llevar el sitio a producción.

👥 Autores

* **Desarrollador:** Valentina Cortez/ Valentina-coder
