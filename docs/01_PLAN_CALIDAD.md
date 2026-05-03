# 📋 Plan de Calidad y Testing - IEEE 829
## Tienda Online - Proyecto Integrador

**Versión:** 1.0  
**Fecha:** 2026-05-03  
**Responsable:** HERMAR55611  
**Estado:** En Ejecución

---

## 1. INTRODUCCIÓN

### 1.1 Propósito
Este documento define el plan integral de testing para el proyecto "Tienda Online", aplicando estándares IEEE 829, ISO 9001 e ISO/IEC 25010 para asegurar la calidad del software.

### 1.2 Alcance
- **Aplicación:** Sistema de Tienda Online (Carrito de Compras, Checkout, Pagos)
- **Componentes:** Backend (Spring Boot), Base de Datos, Servicios REST
- **Niveles de Prueba:** Unitarias, Integración, Sistema, E2E, Rendimiento
- **Período:** 8 semanas de ejecución

---

## 2. ESTRATEGIA DE TESTING

### 2.1 Niveles de Prueba

| Nivel | Herramienta | Cobertura Meta | Casos |
|-------|-------------|----------------|-------|
| **Unitarias** | JUnit 5 + Mockito | 80% líneas | 15-20 |
| **Integración** | Spring Test + TestContainers | 70% APIs | 10-15 |
| **Sistema** | REST Assured | 90% endpoints | 15-20 |
| **E2E** | Selenium WebDriver | 100% flujos críticos | 8-10 |
| **Rendimiento** | JMeter | Baselines | 5-10 |

### 2.2 Tipos de Prueba

1. **Pruebas Funcionales** → Validar requisitos de negocio
2. **Pruebas No Funcionales** → Rendimiento, seguridad, escalabilidad
3. **Pruebas de Regresión** → Cambios no afecten funcionalidad
4. **Pruebas de Humo** → Verificación rápida pre-deployment

### 2.3 Enfoque TDD (Test-Driven Development)

```
Red → Green → Refactor
1. Escribir test FALLA
2. Implementar código MÍNIMO para que PASE
3. Refactorizar código sin perder tests
```

---

## 3. ESTÁNDARES APLICADOS

### 3.1 IEEE 829 - Documentación de Testing
- Plan de Pruebas (este documento)
- Especificación de Casos de Prueba
- Reportes de Ejecución
- Reportes de Defectos

### 3.2 ISO 9001:2015 - Gestión de Calidad
- Gestión de Requisitos
- Control de Cambios
- Gestión de Defectos
- Mejora Continua

### 3.3 ISO/IEC 25010 - Características de Calidad
- **Adecuación Funcional:** Exactitud, Completitud, Apropiabilidad
- **Confiabilidad:** Madurez, Disponibilidad, Tolerancia a Fallos
- **Usabilidad:** Comprensibilidad, Aprendibilidad, Operabilidad
- **Eficiencia de Desempeño:** Tiempo de respuesta, Utilización de recursos
- **Compatibilidad:** Coexistencia, Interoperabilidad
- **Seguridad:** Confidencialidad, Integridad, No-repudio
- **Mantenibilidad:** Modularidad, Reutilizabilidad, Analizabilidad
- **Portabilidad:** Adaptabilidad, Instalabilidad

---

## 4. MÉTRICAS DE CALIDAD

### 4.1 Cobertura de Código
- **Meta:** 80% cobertura líneas de código
- **Herramienta:** JaCoCo
- **Quality Gate:** Falla si cae por debajo del 75%

### 4.2 Densidad de Defectos
- **Meta:** < 3 defectos por 1000 líneas de código
- **Seguimiento:** Registro en Issues de GitHub

### 4.3 Tasa de Éxito de Pruebas
- **Meta:** ≥ 95% tests pasando
- **Reportes:** GitHub Actions

### 4.4 Tiempo de Detección de Defectos
- **Meta:** Detectar defectos antes de UAT
- **Método:** Pirámide de Testing

---

## 5. REQUISITOS Y TRAZABILIDAD

### 5.1 Requisitos Funcionales Clave

| ID | Requisito | Tipo | Prioridad | Test IDs |
|----|-----------|------|-----------|----------|
| REQ-001 | Listar productos | Funcional | Alta | TC-001, TC-002 |
| REQ-002 | Agregar producto a carrito | Funcional | Alta | TC-003, TC-004, TC-005 |
| REQ-003 | Modificar cantidad en carrito | Funcional | Alta | TC-006, TC-007 |
| REQ-004 | Eliminar producto del carrito | Funcional | Alta | TC-008, TC-009 |
| REQ-005 | Calcular total con impuestos | Funcional | Alta | TC-010, TC-011 |
| REQ-006 | Procesar pago | Funcional | Crítica | TC-012, TC-013, TC-014 |
| REQ-007 | Crear orden | Funcional | Alta | TC-015, TC-016 |
| REQ-008 | Enviar confirmación por email | Funcional | Media | TC-017, TC-018 |

---

## 6. ESTIMACIÓN DE ESFUERZO

### 6.1 Desglose de Actividades

| Actividad | Estimación | Esfuerzo (horas) |
|-----------|-----------|-----------------|
| Planificación y Setup | 1 semana | 15 |
| Desarrollo Backend | 2 semanas | 40 |
| Pruebas Unitarias | 1.5 semanas | 25 |
| Pruebas Integración | 1.5 semanas | 25 |
| Pruebas E2E/Rendimiento | 1 semana | 20 |
| Documentación | 0.5 semanas | 10 |
| **TOTAL** | **8 semanas** | **135 horas** |

### 6.2 Recursos
- 1 Desarrollador/QA
- 1 Máquina de desarrollo
- Herramientas: Spring Boot, JUnit, Selenium, JMeter, Maven

---

## 7. CRONOGRAMA

```
Semana 1: Planificación, Setup, Estructura
Semana 2-3: Backend + Pruebas Unitarias (TDD)
Semana 4: Pruebas de Integración
Semana 5: Pruebas E2E (Selenium)
Semana 6: Pruebas de Rendimiento (JMeter)
Semana 7: Refactoring, Optimización
Semana 8: Documentación Final, Presentación
```

---

## 8. RIESGOS Y MITIGACIÓN

| Riesgo | Impacto | Probabilidad | Mitigación |
|--------|---------|--------------|-----------|
| Cambios en requisitos | Alto | Media | Documentar bien, control de cambios |
| Complejidad en pagos | Alto | Media | Usar mock de gateway, tests exhaustivos |
| Cobertura insuficiente | Medio | Media | Automatizar, revisar regularmente |
| Ambiente de test inestable | Medio | Baja | Usar TestContainers, ambiente aislado |

---

## 9. CRITERIOS DE ACEPTACIÓN

✅ **Se aprueba si:**
- Cobertura de código ≥ 80%
- 100% casos de prueba documentados y ejecutados
- 0 defectos críticos sin resolver
- Todos los tests pasando en CI/CD
- Documentación completa según IEEE 829
- Tiempo de respuesta < 200ms (95 percentil)

❌ **Se rechaza si:**
- Cobertura < 70%
- Más de 2 defectos críticos sin resolver
- Tests fallando en CI/CD
- Documentación incompleta

---

## 10. HERRAMIENTAS UTILIZADAS

| Herramienta | Propósito | Versión |
|-------------|----------|---------|
| JUnit 5 | Tests unitarios | 5.9.2 |
| Mockito | Mocking de dependencias | 5.5.0 |
| Spring Test | Tests de integración | 3.2.0 |
| TestContainers | BD aislada para tests | 1.19.3 |
| REST Assured | Tests de APIs | 5.3.2 |
| Selenium WebDriver | Tests E2E | 4.15.0 |
| JMeter | Tests de rendimiento | 5.6 |
| JaCoCo | Cobertura de código | 0.8.10 |
| GitHub Actions | CI/CD | Latest |
| Maven | Build & Test runner | 3.9.x |

---

## 11. REPORTES Y COMUNICACIÓN

### 11.1 Reportes Generados
- ✅ Cobertura JaCoCo (HTML)
- ✅ Surefire Report (JUnit)
- ✅ JMeter Report (Rendimiento)
- ✅ Defectos (Issues GitHub)

### 11.2 Frecuencia
- **Diaria:** Ejecución automática en cada commit
- **Semanal:** Resumen de métricas
- **Al final:** Reporte ejecutivo

---

## 12. APROBACIONES

| Rol | Nombre | Firma | Fecha |
|-----|--------|-------|-------|
| Autor | HERMAR55611 | ✓ | 2026-05-03 |
| Revisor | Profesor | - | - |

---

**Última actualización:** 2026-05-03
