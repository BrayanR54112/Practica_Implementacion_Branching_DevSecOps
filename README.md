# Practica_Implementacion_Branching_DevSecOps
# Proyecto Final Integrador - Implementación DevSecOps

[cite_start]Este repositorio contiene la implementación de una estrategia de branching y un pipeline de CI/CD con controles de seguridad automatizados, siguiendo los lineamientos de la práctica de "Implementación de Estrategia de Branching & DevSecOps"[cite: 4].

## Estrategia de Branching

[cite_start]Para este proyecto, el equipo ha seleccionado la estrategia **GitHub Flow**[cite: 13]. 

### Justificación de la elección
[cite_start]Nuestra decisión se fundamenta en los siguientes criterios técnicos[cite: 18]:

* [cite_start]**Tamaño del equipo:** Al ser un equipo de 3 integrantes, GitHub Flow elimina la sobrecarga administrativa de gestionar múltiples ramas de larga duración (como develop o release), permitiendo una colaboración directa y ágil a través de Pull Requests[cite: 6, 20].
* **Frecuencia de despliegue esperada:** El proyecto busca una entrega continua donde cada funcionalidad terminada se integre inmediatamente a la rama `main`. [cite_start]Esta estrategia facilita despliegues rápidos y constantes sin las interrupciones de ciclos de estabilización prolongados[cite: 19].
* [cite_start]**Madurez del pipeline CI/CD:** La implementación de un pipeline automatizado con **Gitleaks** y **Linters** asegura que cualquier código que intente entrar a `main` sea validado automáticamente, garantizando la integridad de la rama principal sin necesidad de ramas intermedias[cite: 21, 37].

### Flujo de Trabajo
[cite_start]Siguiendo esta estrategia, el repositorio se organiza de la siguiente manera[cite: 34, 81]:
1.  **main:** Rama principal, siempre en estado desplegable y protegida.
2.  **feature/*:** Ramas temporales de corta duración creadas para el desarrollo de nuevas funcionalidades o correcciones.
3.  **Pull Requests:** Todo cambio debe ser revisado y aprobado antes de integrarse a `main`.

---

## Configuración DevSecOps
[cite_start]El pipeline configurado en `.github/workflows/devsecops.yml` ejecuta los siguientes controles en cada push y pull request[cite: 39, 40]:
* [cite_start]**Secret Scanning:** Uso de Gitleaks para detectar credenciales expuestas[cite: 49].
* **Linting:** Verificación de calidad y formato de código según el stack tecnológico[cite: 52].
* [cite_start]**Branch Protection:** Reglas activas para requerir PRs, verificaciones de estado (status checks) y prohibición de Force Push[cite: 73, 74, 75].
