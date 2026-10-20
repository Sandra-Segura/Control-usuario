# US-18 Revisión humana por umbral de confianza

| Campo | Valor |
|---|---|
| Jira | [CDU202610-27](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-27) |
| Épica | E6 Seguridad y control de riesgos ([CDU202610-6](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-6)) |
| Prioridad (MoSCoW) | Must |
| Puntos | 5 |
| Sprint | Sprint 3 |
| Release | R1 (piloto) |

## Historia

Como **responsable de Seguridad de la Información**, quiero umbrales de confianza estrictos y revisión humana (human-in-the-loop) en decisiones de la IA, para evitar bloqueos indebidos al personal operativo crítico.

## Criterios de aceptación

- [ ] Dado una decisión de la IA bajo el umbral, cuando se evalúa, entonces requiere aprobación humana
- [ ] Dado un bloqueo a personal crítico, cuando se detecta como falso positivo, entonces se revierte y se registra
