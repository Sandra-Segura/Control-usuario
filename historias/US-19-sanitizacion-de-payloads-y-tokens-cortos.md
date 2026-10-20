# US-19 Sanitización de payloads y tokens cortos

| Campo | Valor |
|---|---|
| Jira | [CDU202610-28](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-28) |
| Épica | E6 Seguridad y control de riesgos ([CDU202610-6](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-6)) |
| Prioridad (MoSCoW) | Must |
| Puntos | 5 |
| Sprint | Sprint 2 |
| Release | R1 (piloto) |

## Historia

Como **responsable de Seguridad de la Información**, quiero sanitizar payloads y usar tokens cifrados de corto alcance en APIs y prompts, para prevenir inyección de comandos y exposición de credenciales.

## Criterios de aceptación

- [ ] Dado un payload con contenido malicioso, cuando llega, entonces se sanitiza o se rechaza
- [ ] Dado un token de API, cuando se emite, entonces es de corto alcance y expira
