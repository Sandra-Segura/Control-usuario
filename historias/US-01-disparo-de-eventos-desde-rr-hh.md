# US-01 Disparo de eventos desde RR.HH.

| Campo | Valor |
|---|---|
| Jira | [CDU202610-10](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-10) |
| Épica | E8 Plataforma e integraciones ([CDU202610-8](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-8)) |
| Prioridad (MoSCoW) | Must |
| Puntos | 5 |
| Sprint | Sprint 1 |
| Release | R1 (piloto) |

## Historia

Como **analista de TI**, quiero que un evento de contratación, cambio o baja en el ERP/RR.HH. dispare un webhook al motor de orquestación, para iniciar el ciclo JML sin intervención manual.

## Criterios de aceptación

- [ ] Dado un evento de RR.HH., cuando se registra, entonces el orquestador recibe el payload en menos de 1 minuto
- [ ] Dado un payload inválido, cuando llega, entonces se rechaza y se registra el error
