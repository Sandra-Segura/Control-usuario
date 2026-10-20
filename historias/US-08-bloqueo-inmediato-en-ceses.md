# US-08 Bloqueo inmediato en ceses

| Campo | Valor |
|---|---|
| Jira | [CDU202610-17](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-17) |
| Épica | E3 Leavers: ceses seguros ([CDU202610-3](https://cmh-team-gemu7bu9.atlassian.net/browse/CDU202610-3)) |
| Prioridad (MoSCoW) | Must |
| Puntos | 8 |
| Sprint | Sprint 2 |
| Release | R1 (piloto) |

## Historia

Como **responsable de Seguridad de la Información**, quiero bloquear de inmediato cuentas, VPN y sesiones en la nube cuando RR.HH. registre un cese, para eliminar la ventana de exposición tras la salida de una persona.

## Criterios de aceptación

- [ ] Dado un cese registrado, cuando se activa el flujo, entonces se bloquea la cuenta en AD, se deshabilita la VPN y se revocan las sesiones activas
- [ ] Dado el proceso completado, cuando finaliza, entonces el tiempo total no supera el SLA definido
