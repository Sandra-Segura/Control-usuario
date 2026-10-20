# US-04 LLM en infraestructura privada

| Campo | Valor |
|---|---|
| Jira | [CDU202610-13](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-13) |
| Épica | E5 Capa de IA Generativa ([CDU202610-5](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-5)) |
| Prioridad (MoSCoW) | Must |
| Puntos | 8 |
| Sprint | Sprint 1 |
| Release | R1 (piloto) |

## Historia

Como **responsable de Seguridad de la Información**, quiero desplegar el LLM en infraestructura privada con aislamiento de red (VPC), para procesar información sensible sin exponerla fuera del entorno controlado.

## Criterios de aceptación

- [ ] Dado el LLM desplegado, cuando se accede desde fuera de la VPC, entonces el acceso es denegado
- [ ] Dado un prompt, cuando se procesa, entonces no se envían datos a servicios públicos
