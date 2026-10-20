# Historias de usuario: Gestión integral y automatizada de identidades y accesos (IAM)

Fuente: reporte *Gestión Integral y Automatizada de Identidades y Accesos Corporativos* (Segura Nolasco, M., 2026).

**Alcance:** piloto (PoC) de 8 semanas = 4 sprints de 2 semanas. Puntos en escala Fibonacci, **propuestos**; validar con planning poker. Prioridad MoSCoW.

## Resumen por sprint

| Sprint | Historias | Puntos |
|---|---|---|
| Sprint 1 | US-01 Disparo de eventos desde RR.HH., US-02 Conector con Entra ID y AD, US-03 Matriz de perfiles por rol y sector, US-04 LLM en infraestructura privada, US-23 Comité y arquitectura de detalle | 29 |
| Sprint 2 | US-05 Onboarding automático de colaboradores, US-08 Bloqueo inmediato en ceses, US-09 Evidencia de bajas para auditoría, US-19 Sanitización de payloads y tokens cortos, US-22 Registro centralizado y trazable | 29 |
| Sprint 3 | US-06 Integración con LabWare LIMS, US-10 Matriz de transición en movilidad interna, US-12 Revocación de accesos heredados, US-13 Alta temporal de contratistas, US-18 Revisión humana por umbral de confianza | 31 |
| Sprint 4 | US-07 Notificación de accesos listos, US-11 Aprobación de cambios por Teams o correo, US-14 Baja automática por fin de contrato, US-16 Resumen de riesgo para aprobadores, US-17 Detección de anomalías de acceso, US-21 Tablero de KPIs del piloto, US-24 Informe de cierre del piloto | 34 |
| Release 2 (post-piloto) | US-15 Solicitudes en lenguaje natural, US-20 Certificación trimestral de accesos | 13 |

**Releases:** R1 = piloto (sprints 1 a 4, incluye integración con AD/Entra ID y LabWare LIMS). R2 = escalamiento a las demás compañías y funciones IA avanzadas.

**KPIs objetivo del reporte:** onboarding de 48-72 h a menos de 15 min; 99,9% de revocación inmediata en ceses; -75% de tickets de credenciales; 0 accesos huérfanos tras movimientos.

## E1 Joiners: ingreso automatizado

### US-05 Onboarding automático de colaboradores (Must, 8 pts, Sprint 2)
Como **colaborador nuevo**, quiero recibir mis accesos iniciales automáticamente el día de mi ingreso, para comenzar a trabajar sin esperar 48 a 72 horas.

Criterios de aceptación:
- Dado un ingreso registrado en RR.HH., cuando se activa el flujo, entonces cuenta, correo y sistemas core quedan provisionados en menos de 15 minutos
- Dado el rol y sector, cuando se aprovisiona, entonces se aplican solo los perfiles de la matriz

### US-07 Notificación de accesos listos (Should, 3 pts, Sprint 4)
Como **jefe directo**, quiero recibir una notificación cuando los accesos de mi nuevo colaborador estén listos, para confirmar que puede operar desde el primer día.

Criterios de aceptación:
- Dado un onboarding completado, cuando termina, entonces la jefatura y el colaborador reciben notificación por correo o Teams

## E2 Movers: movilidad interna

### US-10 Matriz de transición en movilidad interna (Must, 8 pts, Sprint 3)
Como **responsable de RR.HH.**, quiero que un cambio de puesto calcule la matriz de transición de accesos, para retirar los permisos del puesto anterior y asignar los nuevos.

Criterios de aceptación:
- Dado un cambio de posición, cuando se registra, entonces se calculan los permisos a revocar y a otorgar
- Dado el resultado, cuando se revisa, entonces es consistente con la matriz de perfiles

### US-11 Aprobación de cambios por Teams o correo (Should, 5 pts, Sprint 4)
Como **jefe directo**, quiero aprobar o rechazar los cambios de acceso de mi equipo desde Teams o correo, para validar la movilidad interna de forma ágil.

Criterios de aceptación:
- Dado un cambio pendiente, cuando se envía la aprobación, entonces la jefatura puede aprobar o rechazar desde Teams o correo
- Dado una aprobación sin respuesta, cuando vence el plazo, entonces se recuerda y se escala

### US-12 Revocación de accesos heredados (Must, 5 pts, Sprint 3)
Como **responsable de Seguridad de la Información**, quiero revocar los accesos heredados tras un movimiento interno, para erradicar el privilege creep.

Criterios de aceptación:
- Dado un movimiento aprobado, cuando se ejecuta, entonces no quedan accesos huérfanos del puesto anterior
- Dado la ejecución, cuando termina, entonces queda trazabilidad de lo revocado

## E3 Leavers: ceses seguros

### US-08 Bloqueo inmediato en ceses (Must, 8 pts, Sprint 2)
Como **responsable de Seguridad de la Información**, quiero bloquear de inmediato cuentas, VPN y sesiones en la nube cuando RR.HH. registre un cese, para eliminar la ventana de exposición tras la salida de una persona.

Criterios de aceptación:
- Dado un cese registrado, cuando se activa el flujo, entonces se bloquea la cuenta en AD, se deshabilita la VPN y se revocan las sesiones activas
- Dado el proceso completado, cuando finaliza, entonces el tiempo total no supera el SLA definido

### US-09 Evidencia de bajas para auditoría (Must, 3 pts, Sprint 2)
Como **auditor interno**, quiero recibir evidencia automática de cada baja ejecutada, para verificar el cumplimiento de la revocación de accesos.

Criterios de aceptación:
- Dado un cese procesado, cuando termina, entonces se genera un registro con fecha, hora y sistemas revocados
- Dado una revocación fallida, cuando ocurre, entonces se escala como incidente

## E4 Accesos temporales de contratistas

### US-13 Alta temporal de contratistas (Must, 5 pts, Sprint 3)
Como **supervisor de operaciones mineras**, quiero registrar altas temporales de contratistas con vigencia y turno, para acotar sus accesos a la faena y al periodo contratado.

Criterios de aceptación:
- Dado un contratista, cuando se registra, entonces se asigna un perfil acotado con fecha de fin
- Dado un perfil de faena, cuando se asigna, entonces se limita a los turnos definidos

### US-14 Baja automática por fin de contrato (Must, 5 pts, Sprint 4)
Como **responsable de Seguridad de la Información**, quiero que los accesos de contratistas se deshabiliten al vencer el contrato, para evitar cuentas activas fuera de vigencia.

Criterios de aceptación:
- Dado un contrato vencido, cuando llega la fecha de fin, entonces la cuenta se deshabilita automáticamente
- Dado una renovación aprobada, cuando se registra antes del vencimiento, entonces se extiende la vigencia

## E5 Capa de IA Generativa

### US-04 LLM en infraestructura privada (Must, 8 pts, Sprint 1)
Como **responsable de Seguridad de la Información**, quiero desplegar el LLM en infraestructura privada con aislamiento de red (VPC), para procesar información sensible sin exponerla fuera del entorno controlado.

Criterios de aceptación:
- Dado el LLM desplegado, cuando se accede desde fuera de la VPC, entonces el acceso es denegado
- Dado un prompt, cuando se procesa, entonces no se envían datos a servicios públicos

### US-15 Solicitudes en lenguaje natural (Should, 8 pts, Release 2 (post-piloto))
Como **gerente de área**, quiero enviar una solicitud de excepción en lenguaje natural, para que se convierta en una solicitud de acceso estructurada y segura.

Criterios de aceptación:
- Dado un correo o ticket no estructurado, cuando la IA lo procesa, entonces genera una solicitud con sistema, perfil y justificación
- Dado una solicitud ambigua, cuando la IA no alcanza el umbral de confianza, entonces pide revisión humana

### US-16 Resumen de riesgo para aprobadores (Should, 5 pts, Sprint 4)
Como **aprobador corporativo**, quiero recibir un resumen de riesgo generado por IA en cada acceso privilegiado, para decidir con información suficiente.

Criterios de aceptación:
- Dado un acceso privilegiado, cuando se solicita aprobación, entonces se adjunta un resumen de riesgo
- Dado el resumen, cuando se revisa, entonces indica combinaciones de privilegios incompatibles

### US-17 Detección de anomalías de acceso (Should, 8 pts, Sprint 4)
Como **analista de seguridad**, quiero detectar anomalías de acceso (fuera de horario, privilegios incompatibles), para recibir alertas tempranas.

Criterios de aceptación:
- Dado un patrón inusual, cuando se detecta, entonces se genera una alerta con contexto
- Dado una alerta, cuando se analiza, entonces el analista puede marcarla como falso positivo

## E6 Seguridad y control de riesgos

### US-18 Revisión humana por umbral de confianza (Must, 5 pts, Sprint 3)
Como **responsable de Seguridad de la Información**, quiero umbrales de confianza estrictos y revisión humana (human-in-the-loop) en decisiones de la IA, para evitar bloqueos indebidos al personal operativo crítico.

Criterios de aceptación:
- Dado una decisión de la IA bajo el umbral, cuando se evalúa, entonces requiere aprobación humana
- Dado un bloqueo a personal crítico, cuando se detecta como falso positivo, entonces se revierte y se registra

### US-19 Sanitización de payloads y tokens cortos (Must, 5 pts, Sprint 2)
Como **responsable de Seguridad de la Información**, quiero sanitizar payloads y usar tokens cifrados de corto alcance en APIs y prompts, para prevenir inyección de comandos y exposición de credenciales.

Criterios de aceptación:
- Dado un payload con contenido malicioso, cuando llega, entonces se sanitiza o se rechaza
- Dado un token de API, cuando se emite, entonces es de corto alcance y expira

### US-20 Certificación trimestral de accesos (Could, 5 pts, Release 2 (post-piloto))
Como **dueño de proceso**, quiero certificar trimestralmente los accesos de mi área con apoyo de IA, para controlar el sobre-privilegio.

Criterios de aceptación:
- Dado el cierre de trimestre, cuando se ejecuta la auditoría, entonces se genera la lista de accesos a certificar
- Dado un acceso no certificado, cuando vence el plazo, entonces se revoca o se escala

## E7 Auditoría y KPIs

### US-21 Tablero de KPIs del piloto (Must, 5 pts, Sprint 4)
Como **Gerente Corporativo de TI**, quiero un tablero con los KPIs de éxito del piloto, para medir SLA de onboarding, cumplimiento de revocación, reducción de tickets y accesos huérfanos.

Criterios de aceptación:
- Dado el flujo operando, cuando se consulta el tablero, entonces muestra SLA de onboarding, % de revocación inmediata, tickets de credenciales y accesos huérfanos
- Dado una meta, cuando no se cumple, entonces se resalta

### US-22 Registro centralizado y trazable (Must, 5 pts, Sprint 2)
Como **auditor interno**, quiero un registro centralizado y trazable de cada acción de aprovisionamiento, para auditar de forma unificada a las compañías del grupo.

Criterios de aceptación:
- Dado una acción de alta, baja o cambio, cuando se ejecuta, entonces queda registrada con actor, fecha y resultado
- Dado el registro, cuando se consulta, entonces no puede ser modificado

## E8 Plataforma e integraciones

### US-01 Disparo de eventos desde RR.HH. (Must, 5 pts, Sprint 1)
Como **analista de TI**, quiero que un evento de contratación, cambio o baja en el ERP/RR.HH. dispare un webhook al motor de orquestación, para iniciar el ciclo JML sin intervención manual.

Criterios de aceptación:
- Dado un evento de RR.HH., cuando se registra, entonces el orquestador recibe el payload en menos de 1 minuto
- Dado un payload inválido, cuando llega, entonces se rechaza y se registra el error

### US-02 Conector con Entra ID y AD (Must, 8 pts, Sprint 1)
Como **analista de TI**, quiero un conector con Entra ID / Active Directory federado, para crear, modificar y deshabilitar cuentas desde el flujo automatizado.

Criterios de aceptación:
- Dado un perfil aprobado, cuando se ejecuta, entonces la cuenta se crea o modifica en AD/Entra ID
- Dado un fallo del conector, cuando ocurre, entonces se reintenta y se alerta

### US-03 Matriz de perfiles por rol y sector (Must, 5 pts, Sprint 1)
Como **responsable de Seguridad de la Información**, quiero una matriz de perfiles de acceso por rol y sector (minería, laboratorio, corporativo), para asignar solo los privilegios necesarios a cada puesto.

Criterios de aceptación:
- Dado un rol y sector, cuando se consulta la matriz, entonces devuelve los perfiles aplicables
- Dado un cambio en la matriz, cuando se publica, entonces queda versionado y aprobado

### US-06 Integración con LabWare LIMS (Must, 8 pts, Sprint 3)
Como **analista de TI**, quiero integrar RR.HH. con LabWare LIMS para una unidad de negocio piloto, para provisionar accesos de laboratorio de forma automática.

Criterios de aceptación:
- Dado un alta en la unidad piloto, cuando se ejecuta el flujo, entonces se crea el usuario en LabWare con su perfil
- Dado una baja, cuando se ejecuta, entonces el usuario se deshabilita en LabWare

## E9 Gobierno del piloto (PoC)

### US-23 Comité y arquitectura de detalle (Must, 3 pts, Sprint 1)
Como **Gerente Corporativo de TI**, quiero conformar el comité (Seguridad, Infraestructura TI, RR.HH.) y validar la arquitectura de detalle, para aprobar y gobernar el piloto de 8 semanas.

Criterios de aceptación:
- Dado el inicio del piloto, cuando se conforma el comité, entonces están asignados representantes de las tres áreas
- Dado la arquitectura de detalle, cuando se revisa, entonces queda aprobada

### US-24 Informe de cierre del piloto (Must, 3 pts, Sprint 4)
Como **Gerente Corporativo de TI**, quiero un informe de cierre del piloto con resultados contra los KPIs, para decidir el escalamiento al resto de compañías (AG, CP, CMH, SUNEC).

Criterios de aceptación:
- Dado el fin del piloto, cuando se emite el informe, entonces compara resultados con los KPIs objetivo
- Dado el informe, cuando se presenta, entonces incluye recomendación y presupuesto de escalamiento
