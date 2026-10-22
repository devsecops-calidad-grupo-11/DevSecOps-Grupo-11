# DevSecOps y Calidad – Equipo 8

[![Playwright Tests CI](https://github.com/devsecops-calidad-grupo-8/DevSecOps-Grupo-8/actions/workflows/ci.yml/badge.svg)](https://github.com/devsecops-calidad-grupo-8/DevSecOps-Grupo-8/actions/workflows/ci.yml)

Trabajo práctico de la **Actividad 8** de Gestión de Desarrollo de Software
(UTN FRA): calidad de código, deuda técnica y seguridad (DevSecOps) integradas
al pipeline de CI.

---

## 1. Proyecto base

La aplicación (SPA de gestión de usuarios), la suite de tests con Playwright y
el workflow de GitHub Actions provienen de la **Actividad 6 del Grupo 6**:
https://github.com/gdsGrupo6GitActions/GithubActions-Grupo-6

Sobre esa base, el Equipo 8 agregó las herramientas de calidad y seguridad
descritas a continuación.

---

## 2. Qué se agregó en la Actividad 8

- [ X ] **SonarCloud**: análisis estático (SAST) integrado al workflow de GitHub Actions.
- [ ] **Quality Gate**: el pipeline falla si hay Bugs o Vulnerabilidades nuevos, o si la cobertura de tests es menor al 80%.
- [ ] **Tests unitarios con reporte de cobertura**, que complementan los tests E2E de Playwright.
- [ ] **Dependabot**: alertas y Pull Requests automáticos ante dependencias vulnerables.
- [ ] **Branch Protection Rules** en `main`: el merge exige que los checks del pipeline pasen.

---

## 3. Cómo funciona el pipeline

El workflow `.github/workflows/ci.yml` se ejecuta en cada Pull Request hacia
`main` y realiza, en orden:

1. Descarga del código.
2. Instalación de Node.js y de las dependencias (con caché de npm).
3. Instalación de los navegadores de Playwright.
4. Ejecución de los tests automatizados.
5. Publicación del reporte HTML como artifact.
6. Análisis con SonarCloud y evaluación del Quality Gate.

Si algún paso falla, GitHub bloquea el botón de Merge del Pull Request.

---

## 4. Tecnologías

- HTML, CSS y JavaScript (aplicación)
- Node.js
- Playwright y Playwright Test (tests E2E)
- GitHub Actions (CI)
- SonarCloud (análisis estático y Quality Gate)
- Dependabot (auditoría de dependencias)

---

## 5. Cómo ejecutar el proyecto

Requisitos: Node.js (versión LTS) y npm.

```bash
npm ci
npx playwright install --with-deps
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
├── app/                       # SPA bajo prueba
├── pages/                     # Page Object Model
├── fixtures/                  # Fixtures de Playwright
├── tests/                     # Tests E2E
├── docs/                      # Documentación de la actividad base
├── package.json
└── playwright.config.js
```

---

## 7. Integrantes

- Graneros Johann
- Godoy Aron
- Garcez Gonzalo
- Suarez Juan