# DevSecOps y Calidad – Equipo 11

[![Playwright Tests CI](https://github.com/devsecops-calidad-grupo-11/DevSecOps-Grupo-11/actions/workflows/ci.yml/badge.svg)](https://github.com/devsecops-calidad-grupo-11/DevSecOps-Grupo-11/actions/workflows/ci.yml)

Trabajo práctico de la **Actividad 8** de Gestión de Desarrollo de Software
(UTN FRA): calidad de código, deuda técnica y seguridad (DevSecOps) integradas
al pipeline de CI.

**Estado del proyecto:** actividad implementada y verificada mediante Pull
Requests, pruebas automatizadas, análisis estático, auditoría de dependencias y
protección de la rama principal.

---

## 1. Proyecto base

La aplicación (SPA de gestión de usuarios), la suite de tests con Playwright y
el workflow de GitHub Actions provienen de la **Actividad 6 del Grupo 6**:
https://github.com/gdsGrupo6GitActions/GithubActions-Grupo-6

Sobre esa base, el Equipo 11 agregó las herramientas de calidad y seguridad
descritas a continuación.

---

## 2. Qué se agregó en la Actividad 8

- [x] **SonarQube Cloud**: análisis estático (SAST) integrado al workflow de GitHub Actions.
- [x] **Quality Gate**: controla bugs, vulnerabilidades, mantenibilidad, duplicación y una cobertura mínima del 80 % en código nuevo.
- [x] **Tests unitarios con Jest y reporte de cobertura LCOV**, que complementan los tests E2E de Playwright.
- [x] **Dependabot**: alertas y Pull Requests automáticos ante dependencias vulnerables.
- [x] **Ruleset de protección de `main`**: exige Pull Request y los checks de Playwright y SonarQube Cloud antes del merge.

---

## 3. Cómo funciona el pipeline

El workflow `.github/workflows/ci.yml` se ejecuta en cada Pull Request hacia
`main` y realiza, en orden:

1. Descarga del código.
2. Instalación de Node.js y de las dependencias (con caché de npm).
3. Ejecución de los tests unitarios con Jest y generación de `coverage/lcov.info`.
4. Ejecución de los tests funcionales con Playwright.
5. Análisis con SonarQube Cloud y evaluación del Quality Gate.
6. Publicación del reporte HTML de Playwright como artifact.

Si algún paso falla, GitHub bloquea el botón de Merge del Pull Request.

---

## 4. Tecnologías

- HTML, CSS y JavaScript (aplicación)
- Node.js
- Playwright y Playwright Test (tests E2E)
- GitHub Actions (CI)
- Jest (tests unitarios y cobertura LCOV)
- SonarQube Cloud (análisis estático y Quality Gate)
- Dependabot (auditoría de dependencias)

---

## 5. Cómo ejecutar el proyecto

Requisitos: Node.js (versión LTS) y npm.

```bash
npm ci
npx playwright install --with-deps
npm run test:unit
npm test
```

Otros comandos disponibles:

```bash
npm run test:headed   # tests con el navegador visible
npm run report        # abrir el reporte HTML
```

---

## 6. Estructura del repositorio

```text
.
├── .github/workflows/ci.yml   # Pipeline de CI
├── .github/dependabot.yml     # Configuración de Dependabot
├── app/                       # SPA bajo prueba
├── pages/                     # Page Object Model
├── fixtures/                  # Fixtures de Playwright
├── tests-unit/                # Tests unitarios con Jest
├── tests/                     # Tests E2E
├── docs/                      # Documentación de la actividad base
├── jest.config.js             # Configuración de cobertura
├── sonar-project.properties   # Configuración de SonarQube Cloud
├── package.json
└── playwright.config.js
```

---

## 7. Evidencias y entrega

La entrega se encuentra centralizada en la siguiente carpeta de Google Drive:

[Abrir carpeta de entrega en Google Drive](https://drive.google.com/drive/folders/1RlWfc7NvXv5zvvQtRuWrXAHkHIqsQYfH)

La carpeta reúne los siguientes elementos solicitados:

- El archivo `.github/workflows/ci.yml` actualizado y comentado.
- Capturas del Quality Gate aprobado y fallido.
- El video final de la presentación.

Evidencias adicionales disponibles en GitHub:

- [Ejecuciones de GitHub Actions](https://github.com/devsecops-calidad-grupo-11/DevSecOps-Grupo-11/actions)
- [PR #10: integración de SonarQube Cloud](https://github.com/devsecops-calidad-grupo-11/DevSecOps-Grupo-11/pull/10)
- [PR #16: demostración del Quality Gate y bloqueo del merge](https://github.com/devsecops-calidad-grupo-11/DevSecOps-Grupo-11/pull/16)

---

## 8. Integrantes

- Graneros Johann
- Godoy Aron
- Garcez Gonzalo
- Suarez Juan
