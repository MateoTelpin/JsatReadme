# Release 1.2.28

## Resumen de trazabilidad
- Commits totales: 169
- Commits con archivos: 169
- Archivos totales: 1320
- SIS primarios: 57
- SIS relacionados: 9
- REC: 43
- SIS con comentarios: 0

## Cambios detallados
### SIS-2125 - frontend RECURSO TECNICO

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Enzo Sives
- Descripcion: <p>Completar implementación de componente RecursoTecnicoProperties</p>

#### Commits asociados

- 3a33397a9c - 2026-05-14 12:36:25 - Marcos Rossi
  Mensaje: SIS-2125
  Stats: +67 | -4 | 71 cambios | 3 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/arenero/server/Application.java - modified | +22 | -0 | 22 cambios
- src/JSAT/project/web/arenero/container.jsp - modified | +17 | -4 | 21 cambios
- src/JSAT/project/web/arenero/styles/arenero.css - modified | +28 | -0 | 28 cambios

### SIS-2649 - Migración Sat / Bejerman

#### Jira
- Estado: En curso
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: COTIZAR
- REC: REC-798
- Descripcion: <p>RECLAMO: REC-798<br/> &#8212;<br/> Buenos dias.</p> <p>Queremos realizar la migración de Sat a Bejerman y necesitamos saber cómo proceder.</p> <p>Todavía no arrancamos con Bejerman, pero la decision ya esta tomada</p> <p>Nos podrías decir si tienen alguna guia de implementación o el listado de los archivos que se migran diariamente y cual seria el costo?</p> <p>Aguardo tus comentarios</p> <p>Desde ya muchas gracias<br/> &#8212;</p>

#### REC relacionados
- REC-798

#### Commits asociados

- 58188be7e1 - 2026-06-23 14:35:08 - cericci
  Mensaje: SIS-2649 Integracion de Jsat con Bejerman
  Stats: +46 | -2 | 48 cambios | 3 archivos
##### Archivos modificados
- BD/Datos/Dinamicos/DIN_BCO_CtaBan - BEJERMAN-VGG.sql - added | +27 | -0 | 27 cambios
- BD/Datos/Dinamicos/DIN_CONTAB_Cuentas - BEJERMAN-VGG.sql - added | +17 | -0 | 17 cambios
- BD/StoredProcedures/SP_GENERAL_CrearVistasBejerman.sql - modified | +2 | -2 | 4 cambios

### SIS-3662 - Error en transacción a JSC

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- REC: REC-1723
- Descripcion: <p>RECLAMO: REC-1723<br/> &#8212;<br/> Buenas tardes me notifican de un error sobre la línea IMOWI 2966279123 el cual en transacciones a JSC da el siguiente error: Error en lÃ­nea '1': detalles=java.io.FileNotFoundException: /var/jsat-files/docs/2025-04/rptLMovPNM174473247211049.pdf (No such file or directory)) (ADJUNTO IMAGEN)</p> <p>Generalmente se finaliza la tarea para volver a mandar el proceso de portabilidad, pero no aparece esta opción (ADJUNTO IMAGEN) y al seleccionar reiniciar de portabilidad da error.</p> <p>&#8212;<br/> Nacho, el servicio es 2966279123 (solo en produccion xq prueba no la estan restaurando)</p> <p>Yo no estoy viendo que en el WF haya una opcion Finalizar luego de esa etapa, vos los podras asesorar?</p> <p>gracias</p>

#### REC relacionados
- REC-1723

#### Commits asociados

- 83e1640601 - 2026-06-19 14:07:45 - MARIELA-CORAN
  Mensaje: SIS-3662 4.4- Obtener la fecha de turno del trámite en formato amigable para el cliente ( agregando ‘por la mañana ‘o por la tarde’) -Para ello agregue una nueva property fechaFinEsperadaStr en la clase Tramite.java , Operacion.hbm , TAB_Tramites_tramite.sql Ademas en la clase Tramite.java el metodo getFechaTurnoAmigable que dependiendo de la BP_granularidad que tiene la Agenda de ese turno ocupacion asignado al tramite arma el string: que dependiendo si la granularidad es D - Diaria, no muestra la hora, si es MyT, muestra la fecha concatenando el string “por la manana” o “por la tarde” dependiendo si la hora es 0 o 12 respectivamente. y cualquier otra granularidad devuelve la fechaHora completo. en el metodo Tramite.toWeb muestra la fechaFinEsperadaStr
  Stats: +63 | -4 | 67 cambios | 3 archivos
##### Archivos modificados
- BD/Tablas/TAB_TRAMITE_Tramite.sql - modified | +22 | -3 | 25 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/bo/Operacion.hbm.xml - modified | +4 | -0 | 4 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/bo/Tramite.java - modified | +37 | -1 | 38 cambios

### SIS-3862 - Notificacion y Gestion de Turnos por parte del cliente

#### Jira
- Estado: En curso
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Marcos Rossi
- SIS relacionados: SIS-3795
- REC: REC-1947
- Descripcion: <p>RECLAMO: REC-1947<br/> &#8212;<br/> Se desea poder automatizar y permitir que el cliente pueda autogestionarse los turnos de tramites del JSAT.</p> <p>También necesitamos automatizar la notificación vía WhatsApp de la proximidad de un turno ya pautado con el cliente</p> <p><b>1-Notificar al cliente de su proximo turno de tramite</b><br/> -Se podra enviar una notificación automática desde el JSAT ( via BotMaker) al numero asociado al tramite para informar al cliente de su proximo turno.<br/> -Los envios se programaran el dia anterior hábil a la fecha del turno a partir de las 9hs ( ej si el turno fuera un lunes , se debe notificar del mismo el dia viernes anterior)<br/> -Es posible que en la plantilla de notificación saliente se le permita al cliente indicar si esta de acuerdo con mantener ese turno o no:</p> <ul class="alternate" type="square"> <li><b>SI</b> mantiene el turno, se debería avisar al JSAT para que ese tramite este disponible para el despacho</li> <li><b>NO</b> mantiene el turno, se le podrá mostrar un link para que acceda a la pantalla de reprogramar el turno en la OV</li> <li><b>NO CONTESTA</b>, el tramite permanecera en la etapa de CITA para que sea contactado por personal de la empresa</li> </ul> <p>Si por alguna razón se reprograma un turno , se debe chequear y marcar como no pendiente la notificación del turno anterior y programar la notificación del nuevo turno.</p> <p><b>2-Dado un Tramite que tiene turno asignado,Permitir que el cliente pueda reprogramar su turno con otro turno disponible desde OV</b><br/> &#8212;</p>

#### REC relacionados
- REC-1947

#### Commits asociados

- 53c4b7fac2 - 2026-06-17 18:12:56 - MARIELA-CORAN
  Mensaje: SIS-3862 Gestion de dias feriados en AgendaOcupacion <h3> Turnos de la Agenda</h3> Es posible solo a efectos informativos, registrar si los turnos se estan dando en un dia Feriado o No Laborable a nivel administrativo. REC-1947
  Stats: +55 | -4 | 59 cambios | 7 archivos
##### Archivos modificados
- BD/Tablas/TAB_TRAMITE_AgendaTurnosOcupacion.sql - modified | +6 | -3 | 9 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/bo/AgendaTurnosOcupacion.hbm.xml - modified | +5 | -0 | 5 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/bo/AgendaTurnosOcupacion.java - modified | +15 | -0 | 15 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/uc/UCAgendaTurnosOcupacionAlta.java - modified | +16 | -0 | 16 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/view/gh/AgendaTurnosOcupacionGH.java - modified | +8 | -1 | 9 cambios
- src/JSAT/project/web/arenero/tramite/agendaTurnosOcupacionAlta.jsp - modified | +3 | -0 | 3 cambios
- src/JSAT/project/web/arenero/tramite/agendaTurnosOcupacionEdit.jsp - modified | +2 | -0 | 2 cambios

- a04eee2231 - 2026-06-19 14:55:07 - MARIELA-CORAN
  Mensaje: SIS-3862 4.2- Implementar un notificador por WhatsApp que permita registrar transacciones del conector a BotMaker Rulo habia implementado la clase ConectorBotmaker.java Modifique Conector.hbm para inlcuir la nueva clase con el discriminator ConectorBotmaker Inserto el nuevo Conector en la BD con Insert_Tecnica_ConectorBotmaker.sql Defini la clase NotificadorWhatsapp que llama al ConectorBotmaker para generar una transaccion cuando se usa para notificar Agregue en la clase UCNotificarACliente.java el nuevo notificador NotificadorWhatsapp que por defecto esta deshabilitado, hay un contructor UCNotificarAClientes que le cree para que solo use el notificadorwhatsapp con xNotificarSoloWhatsApp asi puedo enviar solo whatsapp , lo mismo desde el load de este UC para poder usarlo desde el UC programable Inserto un nuevo BP_TemaContacto que es WHATSAPP para que cada vez que se haga una notificacion x whatsapp quede registrado en los contactos con el ccliente con este tema. Insert BP_TemaContacto- Whatsapp.sql
  Stats: +450 | -6 | 456 cambios | 6 archivos
##### Archivos modificados
- BD/Datos/Datos/Insert BP_TemaContacto- WHATSAPP.sql - added | +20 | -0 | 20 cambios
- BD/Datos/Insert Tecnica_Conector BOTMAKER.sql - added | +59 | -0 | 59 cambios
- src/JSAT/project/src/com/telpin/jsat/notificador/NotificadorWhatsApp.java - added | +277 | -0 | 277 cambios
- src/JSAT/project/src/com/telpin/jsat/notificador/UCNotificarAClientes.java - modified | +85 | -0 | 85 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/Conector.hbm.xml - modified | +3 | -0 | 3 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/ConectorBotmaker.java - modified | +6 | -6 | 12 cambios

### SIS-4882 - Análisis de bajas reiteradas post temporada para definir oferta específica

#### Jira
- Estado: EN ESPERA
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-2986
- Descripcion: <p>RECLAMO: REC-2986<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenos días. En esta época del año, y hasta después de mayo, el churn de fibra crece considerablemente. Probablemente las bajas surgen porque las casas de temporada se cierran, y los titulares del servicio lo dan de baja, volviendo a pedirlos entre noviembre y diciembre, para luego volver a darlos de baja en marzo del año próximo. Necesitamos poder identificar los domicilios en los que año a año sucede lo mismo, altas y bajas, de manera de poder darles otro tratamiento al momento de la venta. <br/> Gracias!</p> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-2986

#### Commits asociados

- 1bbf7d838c - 2026-06-12 18:31:19 - CECILIA-RICCI
  Mensaje: SIS-4882
  Stats: +112 | -18 | 130 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado CLIBAJREIT - Clientes con Bajas de INTFO reiteradas.sql - modified | +112 | -18 | 130 cambios

- f0ba47a918 - 2026-06-17 17:49:58 - CECILIA-RICCI
  Mensaje: SIS-4882 Amplie el campo querySql. Agreguie en el listado Clientes con Bajas de INTFO reiteradas, si el cliente tiene servicios activos o no.
  Stats: +50 | -17 | 67 cambios | 2 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado CLIBAJREIT - Clientes con Bajas de INTFO reiteradas.sql - modified | +47 | -13 | 60 cambios
- BD/Tablas/TAB_BP_Listado.sql - modified | +3 | -4 | 7 cambios

### SIS-4888 - Reporte FIBRA

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-2869
- Descripcion: <p>RECLAMO: REC-2869<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenos dias, Iara nos pide un reporte con la siguiente informacion:</p> <blockquote><p><b>Iara Arcuri:</b> podemos saber en jsat, en los lugares que habilitamos con fibra, cuantos usuarios solicitaron el cambio de tecno? <br/> <b>Iara Arcuri:</b> y poder comparar total de usuarios de la zona vs cant de usuarios que gestionaron el cambio</p></blockquote> <p>En el caso de que ya exista la posibildad de sacar dicha informacion no podrian informar donde y como verla? sino dejo el pedido para su desarrollo.</p> <p>Gracias </p> <p>NICOLAI Patricia<br/> &#8212;<br/> <font color="#ff991f">Martu, no hay nada para ver esto que piden.</font></p> <p><font color="#ff991f">CR dice que hagamos un listado de servicios con cambio de tecnologia entre fechas, mostrando la direccion con la zona y que lo analicen a ver si les sirve.</font></p> <p><font color="#ff991f">Que te lo pase a vos y le vayas consultando, gracias!</font><br/> &#8212;</p>

#### REC relacionados
- REC-2869

#### Commits asociados

- 51730c5f6f - 2026-06-16 14:37:58 - CECILIA-RICCI
  Mensaje: SIS-4888 <h3>Servicios con Cambio de Tecnología entre fechas</h3> Dentro de Servicios\Listados se incorporó este listado para analizar los servicios con su ubicación que cambiaron de tecnologia en un rango de fechas. REC-2869
  Stats: +94 | -0 | 94 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado SVCAMBTEC - Servicios con Cambio de Tecnología entre fechas.sql - added | +94 | -0 | 94 cambios

### SIS-4904 - Simplificación para alta de clientes o producto

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: VERSION.1.2.28
- REC: REC-2948
- Descripcion: <p>RECLAMO: REC-2948<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola chicos!</p> <p>Vemos que hay algunas pantallas que podemos eliminar o mejorar para la carga de clientes o productos. </p> <p>Les dejo un documento con esta información, me dicen por favor si son todas posibles de realizar. </p> <p>¡Muchas gracias!</p> <p><a href="https://docs.google.com/document/d/1Azc6Nn3neF6olxH7BBzqoR-m61QqbGj1cJFLEj8CMhY/edit?usp=sharing" title="smart-link" class="external-link" rel="nofollow noreferrer">https://docs.google.com/document/d/1Azc6Nn3neF6olxH7BBzqoR-m61QqbGj1cJFLEj8CMhY/edit?usp=sharing</a> <br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-2948

#### Commits asociados

- b486d89a8c - 2026-06-04 11:37:36 - CECILIA-RICCI
  Mensaje: SIS-4904 <h3>Ingresos Brutos</h3> Como parte de la simplificación en el alta de nuevos clientes, si la condición de IVA es Consumidor Final, el sistema seteará automáticamente la condición de Ingresos Brutos como CF-No Alcanzado y se omitirá mostrar la pantalla. REC-2948
  Stats: +9 | -1 | 10 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/clientes/uc/UCDatoImpositivoIngresosBrutosAlta.java - modified | +9 | -1 | 10 cambios

### SIS-4916 - Nuevo método de pago

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: COTIZAR
- REC: REC-3023
- Descripcion: <p>RECLAMO: REC-3023<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenas, nos pasaron desde el BPN (Banco Provincia de Neuquén) un nuevo método de pago que permite que los clientes paguen con tarjeta de crédito o débito entre otros medios y en cuotas sin interés…</p> <p>Nos parece interesante desde ese punto de vista pero la implementación requiere un desarrollo porque se debe generar un JWT, generar un link de pago que redirigue a la página del BPN, una vez que el cliente paga dicha página redirige mediante un Web Hook hacia algún endpoint que debería tener la OVT para registrar el pago…</p> <p>La documentación del proceso está en </p> <p><a href="https://developers.bpnpagos.com.ar/" title="smart-link" class="external-link" rel="nofollow noreferrer">https://developers.bpnpagos.com.ar/</a> </p> <p>Necesitaríamos saber si pueden pasarnos una factibilidad para este desarrollo, un estimado de tiempo, teniendo en cuenta que hoy estamos con la API y no queremos descuidar ni demorar ese otro desarrollo …</p> <p>Gracias<br/> &#8212;<br/> <font color="#ff991f">Rulo, buenos dias. </font></p> <p><font color="#ff991f">Vos podras analizar esto? </font></p> <p><font color="#ff991f">Quizas es lo mismo que tenemos aca de Macro en la OV.</font></p> <p><font color="#ff991f"> Podrias decir si es posible implementar? Qué necesitas y cuánto tiempo puede requerir el desarrollo asi lo cotizamos? </font></p> <p><font color="#ff991f">Gracias!</font><br/> &#8212;</p>

#### REC relacionados
- REC-3023

#### Commits asociados

- ebf76d76b4 - 2026-06-08 17:08:54 - ignacio.hahn
  Mensaje: SIS-4916 COTESMA - Entidad de cobranza BPN
  Stats: +161 | -0 | 161 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/EE-Cobranzas/Insert Cobranza - CCECCC Cobranzas Banco Provincia Neuquen - COTESMA.sql - added | +161 | -0 | 161 cambios

### SIS-4947 - Envio automatico de mails al finalizar  determinados tramites.

#### Jira
- Estado: En curso
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: VERSION.1.2.27
- REC: REC-3056
- Descripcion: <p>RECLAMO: REC-3056<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Queremos implementar el envío automático de encuestas en dos momentos clave del servicio:</p> <ul> <li>Al finalizar una instalación</li> </ul> <div class='table-wrap'> <table class='confluenceTable'><tbody> <tr> <td class='confluenceTd'>1553</td> <td class='confluenceTd'>AINTFO</td> <td class='confluenceTd'>Instalacion de Internet Fibra Optica</td> </tr> <tr> <td class='confluenceTd'>1555</td> <td class='confluenceTd'>OT-SIPI</td> <td class='confluenceTd'>Instalar Linea SIP</td> </tr> </tbody></table> </div> <ul> <li>Al cerrar un reclamo</li> </ul> <div class='table-wrap'> <table class='confluenceTable'><tbody> <tr> <td class='confluenceTd'>112</td> <td class='confluenceTd'>SER-18</td> <td class='confluenceTd'>Reclamo telefonia</td> </tr> <tr> <td class='confluenceTd'>1161</td> <td class='confluenceTd'>SER-18-2</td> <td class='confluenceTd'>Reclamo telefonia</td> </tr> <tr> <td class='confluenceTd'>1162</td> <td class='confluenceTd'>RECLAINT-2</td> <td class='confluenceTd'>Reclamo internet</td> </tr> <tr> <td class='confluenceTd'>2673</td> <td class='confluenceTd'>OT-PLAEXT</td> <td class='confluenceTd'>Reclamo Planta Externa</td> </tr> <tr> <td class='confluenceTd'>1422</td> <td class='confluenceTd'>IPTVRECLA</td> <td class='confluenceTd'>Reclamo Television</td> </tr> <tr> <td class='confluenceTd'>1526</td> <td class='confluenceTd'>SER-TELIP</td> <td class='confluenceTd'>Reclamo Telefonia</td> </tr> </tbody></table> </div> <p>Que deberíamos hacer en JSAT para que se dispare automáticamente un mail q...

#### REC relacionados
- REC-3056

#### Commits asociados

- 4280f30adb - 2026-06-10 18:42:14 - ignacio.hahn
  Mensaje: SIS-4947 COTORTEL: State de notificacion al cliente en worflows UCBandaAnchaInstalar y UCTelefoniaTELSIPIInstalar
  Stats: +67 | -1 | 68 cambios | 2 archivos
##### Archivos modificados
- src/JSAT/project/src/processDefinitions/cotortel/UCBandaAnchaInstalar.xml - modified | +5 | -1 | 6 cambios
- src/JSAT/project/src/processDefinitions/cotortel/UCTelefoniaTELSIPIInstalar.xml - added | +62 | -0 | 62 cambios

### SIS-4953 - Primeras pruebas de endpoints (parte 1/2)

#### Jira
- Estado: EN ESPERA
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Mateo Soto
- Etiquetas: VERSION.1.2.28
- SIS relacionados: SIS-4889
- REC: REC-2994
- Descripcion: <p>RECLAMO: REC-2994<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-4889" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-4889" class="jira-issue-macro-key issue-link" title="Primeras pruebas de endpoints" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-4889 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Buenas, estuve haciendo las primeras pruebas de los endpoints en el servidor de prueba y pude detectar lo siguiente:</p> <p>1 - Session login → Prueba OK (se pudo loguear con mi usuario 369 y se obtiene un sid)</p> <p>2 - GET Persona → Se consulta mediante un DNI existente y un tipo de documento existente y devuelve los datos OK. En otros casos responde no encontrado. Prueba OK</p> <p>3 - POST crear persona física → Se utiliza Postman para probar un POST a este endpoint. Se usa el body de ejemplo (tal cual) de Swagger para probar antes de personalizarlo con datos propios. Se agrega un Header con el sid obtenido del endpoint Session Login (logueandome con el usuario 369)</p> <p>El endpoint devuelve el mensaje de error:.</p> <div class="preformatted panel" style="border-width: 1px;"><div class="preformattedContent panelContent"> <pre>{ "status": "ERROR", "statusMessage": "java.lang.IllegalStateException: Expected BEGIN_ARRAY but was STRING", "result": null }</pre> </div></div> <p>El body de la request es:</p> <div class="...

#### REC relacionados
- REC-2994

#### Commits asociados

- 21bf6487f0 - 2026-06-03 17:34:12 - mateo-soto
  Mensaje: SIS-4953 Correcciones en API Se agregaron varios endpoints, como la edicion de datos de la persona, finalizar etapa y cambiar identificador
  Stats: +1753 | -504 | 2257 cambios | 61 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/clientes/api/CrearPersonaCommand.java - removed | +0 | -265 | 265 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/CrearPersonaFisicaCommand.java - modified | +3 | -4 | 7 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/CrearPersonaJuridicaCommand.java - modified | +3 | -3 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosContactoCommand.java - modified | +2 | -3 | 5 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosImpositivosCommand.java - modified | +7 | -14 | 21 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosPersonalesCommand.java - modified | +59 | -27 | 86 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/GetPersonaCommand.java - modified | +99 | -9 | 108 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/GetRegionDireccionFacturacionCommand.java - modified | +13 | -4 | 17 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/ProcesarDatosPersona.java - added | +346 | -0 | 346 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/dto/DatoImpositivoDTO.java - modified | +10 | -1 | 11 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/dto/DatosContactoDTO.java - modified | +5 | -10 | 15 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/dto/MedioContactoDTO.java - added | +38 | -0 | 38 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/dto/PersonaGetDTO.java - modified | +18 | -2 | 20 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/CambiarIndentificadorCommand.java - added | +76 | -0 | 76 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/GetParametrosVentaCommand.java - modified | +6 | -6 | 12 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/dto/ServicioDTO.java - modified | +1 | -0 | 1 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/dto/DireccionFacturacionDTO.java - modified | +3 | -0 | 3 cambios
- src/JSAT/project/src/com/telpin/jsat/mobile/api/FinalizarTareaCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/api/FinalizarEtapaCommand.java - added | +111 | -0 | 111 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/api/GetEtapaPendienteCommand.java - added | +65 | -0 | 65 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/dto/FinalizarEtapaDTO.java - added | +10 | -0 | 10 cambios
- tools/bruno/api-telpin/testing/comercial/cambiar-identificador/cambiar-identificador-INTFO-ok.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/comercial/cambiar-identificador/cambiar-identificador-IPTV-ok.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/comercial/cambiar-identificador/cambiar-identificador-TELSIPI-ok.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/comercial/cambiar-identificador/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/crear-persona-fisica.bru - removed | +0 | -59 | 59 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/crear-persona-juridica.bru - removed | +0 | -54 | 54 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/crear/crear-persona-fisica.bru - added | +74 | -0 | 74 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/crear/crear-persona-juridica.bru - added | +69 | -0 | 69 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/crear/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar-datos-contacto.bru - removed | +0 | -35 | 35 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/editar-datos-contacto-completo.bru - added | +53 | -0 | 53 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/editar-datos-contacto-direccion-facturacion.bru - added | +36 | -0 | 36 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/editar-datos-contacto-email.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/editar-datos-contacto-telefono.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/editar-datos-contacto-whatsapp.bru - added | +31 | -0 | 31 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/datos-contacto/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/impositivos/editar-datos-impositivos-completo.bru - renamed | +3 | -3 | 6 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/impositivos/editar-datos-impositivos-ib.bru - added | +29 | -0 | 29 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/impositivos/editar-datos-impositivos-iva.bru - added | +29 | -0 | 29 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/impositivos/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-apellido.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-completo.bru - renamed | +2 | -2 | 4 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-cuil.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-fecha-nacimiento.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-nacionalidad.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-nombre.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-numero-documento.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-sexo.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/editar-datos-personales-fisica-tipo-documento.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/fisica/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/juridica/editar-datos-personales-juridica-completo.bru - renamed | +2 | -2 | 4 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/juridica/editar-datos-personales-juridica-nombre-fantasia.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/juridica/editar-datos-personales-juridica-razon-social.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/juridica/editar-datos-personales-juridica-tipo-sociedad.bru - added | +25 | -0 | 25 cambios
- tools/bruno/api-telpin/testing/personas/casos-ok/editar/personales/juridica/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/tramites/buscar-etapa-pendiente.bru - added | +21 | -0 | 21 cambios
- tools/bruno/api-telpin/testing/tramites/finalizar-etapa.bru - added | +26 | -0 | 26 cambios
- tools/bruno/api-telpin/testing/tramites/folder.bru - added | +8 | -0 | 8 cambios

### SIS-4953 - Primeras pruebas de endpoints (parte 2/2)

#### Jira

#### Commits asociados

- 9fc14b394a - 2026-06-16 18:30:38 - mateo-soto
  Mensaje: SIS-4953 Correcciones en documentación de API
  Stats: +121 | -64 | 185 cambios | 29 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/arenero/api/APIMngr.java - modified | +7 | -0 | 7 cambios
- src/JSAT/project/src/com/telpin/arenero/api/LoginAPICommand.java - modified | +20 | -3 | 23 cambios
- src/JSAT/project/src/com/telpin/arenero/api/annotations/APIDocAN.java - modified | +3 | -0 | 3 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/CrearAvisoDePagoCommand.java - modified | +5 | -5 | 10 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosContactoCommand.java - modified | +3 | -3 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosImpositivosCommand.java - modified | +5 | -5 | 10 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDatosPersonalesCommand.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EditarDireccionFacturacionCommand.java - modified | +5 | -5 | 10 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EliminarApoderadoCommand.java - modified | +5 | -5 | 10 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/EliminarCotitularCommand.java - modified | +5 | -5 | 10 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/GetClienteCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/GetPersonaCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/GetRegionDireccionFacturacionCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/dto/RegionDireccionFacturacionGetDTO.java - modified | +7 | -0 | 7 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/CambiarIndentificadorCommand.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/GetDatosAgendaTurnoCommand.java - modified | +1 | -0 | 1 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/GetProductoClienteCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/GetServicioCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/VincularServiciosCommand.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/dto/DatosTramiteDTO.java - modified | +3 | -3 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/dto/ServicioDTO.java - modified | +12 | -3 | 15 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/BajaDebitoAutomaticoCommand.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/CrearDebitoAutomaticoCommand.java - modified | +3 | -3 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/GetAcuerdoFacturacionCommand.java - modified | +4 | -3 | 7 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/GetCuentaCobroCommand.java - modified | +1 | -2 | 3 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/GetDebitoAutomaticoCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/dto/CuentaCobroGetDTO.java - modified | +11 | -0 | 11 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/api/FinalizarEtapaCommand.java - modified | +2 | -1 | 3 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/api/GetEtapaPendienteCommand.java - modified | +5 | -4 | 9 cambios

### SIS-4967 - Automatizacion Deb automat Master

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: RENDICION_COMISION
- REC: REC-3076
- Descripcion: <p>RECLAMO: REC-3076<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenos dias!!!</p> <p>Se abre Req para seguir con la automatizacion de las cobranzas, En este caso es por el Deb Automatico de Master, que es uno de los pendientes y luego quedara Visa, ya que Amex esta automatizado y Fava finalizo hace pocos dias. Luego recordar que quedara lo de Payway y Fiser para automatizar. Hoy la carga es manual. </p> <p>En este caso, Deb Automat Master esta ingresando a nuestra cuenta del Banco Nacion y ahi lo conciliamos. Actualmente la liquidacion se carga manualmente junto con la comision y demas conceptos de impuestos, quedando el Neto acreditado en el extr Banco Nacion.</p> <p>Adjunto ultima liq de Master de Deb automatico como ej. Estas liquidaciones nos llegan entre 4 o 5 mensualmente para la carga.</p> <p>Cualquier duda nos consultan. Gracias!!!<br/> &#8212;<br/> <span class="nobr"><a href="/rest/api/3/attachment/content/29021" title="LiquidacionDiaria-289995-3865275-MastercardCr_dito-20260319.pdf 19-03-2026.pdf attached to SIS-4967" data-attachment-type="file" data-attachment-name="LiquidacionDiaria-289995-3865275-MastercardCr_dito-20260319.pdf 19-03-2026.pdf" data-media-services-type="file" data-media-services-id="638a94d6-cba2-4d00-9545-db875decb7fd" rel="noreferrer">LiquidacionDiaria-289995-3865275-MastercardCr_dito-20260319.pdf 19-03-2026.pdf<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span><br/> &#8212;</p>

#### REC relacionados
- REC-3076

#### Commits asociados

- eb6c7f2f32 - 2026-06-24 18:03:55 - cericci
  Mensaje: SIS-4967 Hice un cambio para que levante bien los importes.
  Stats: +11 | -11 | 22 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ComisionDebAutMastercard.sql - modified | +11 | -11 | 22 cambios

### SIS-4994 - Cambios en Clientes - Listados - Datos de contacto Whatsapp para clientes activos

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- REC: REC-3045
- Descripcion: <p>RECLAMO: REC-3045<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola!<br/> Necesitamos algunos cambios en el listado de Clientes - Listados - Datos de contacto Whatsapp para clientes activos</p> <ol> <li>Agregar columna Etiqueta del Cliente en el listado y que contenga el código de etiqueta. Esto nos va a permitir hacer un análisis más profundo de la base, como por ejemplo sacar clientes con etiquetas empleado o por determinada cantidad de servicios.</li> </ol> <ol> <li>En la columna Contacto aparece el número de WhatsApp pero solo si el mismo está en Medios de contacto del cliente tildado como Contacto para notificación o Particular o Para Instalación. Muchos contactos, sobre todos cuando comenzamos a tener el contacto WhatsApp, están tildados sin ninguna de esas tres opciones, por lo que necesitamos que esta columna traiga siempre el contacto marcado como WhatsApp, tenga tildada una opción de tipo de contacto o no.</li> </ol> <ol> <li>En algunas ocasiones queremos saber la antigüedad del servicio que estamos listando, de esta manera podemos aplicar promociones según fidelidad. Lo que necesitamos es que si por ejemplo listamos servicios INTFO, nos traiga la fecha de activación del servicio, es decir cuando se cumplió la orden de trabajo o dicho de otra manera, la primera vez que el servicio estuvo en estado Habilitado. ¿Es posible traer la fecha original de activación del servicio?</li> </ol> <ol> <li>En la columna Servicio se encuentra el identificador del servicio que elegimos listar (INTFO, TELM, OTTTV, etc), lo que necesitamos es que en otra columna al lado...

#### REC relacionados
- REC-3045

#### Commits asociados

- 0da66d37ce - 2026-05-26 12:38:27 - Martina
  Mensaje: SIS-4994 - Actualizacion SP listado ClientesActivosPorTipoContacto Se actualiz贸 el archivo SP_LST_CLI_ClientesActivosPorTipoContacto ya que estaba mal el nombre al crear el store procedure. Adem谩s se copiaron nuevamente todas las modificaciones hechas a este listado y qued贸 como se solicit贸 en el REC-3045.
  Stats: +251 | -199 | 450 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_CLI_ClientesActivosPorTipoContacto.sql - modified | +251 | -199 | 450 cambios

- 100c991ba8 - 2026-05-26 14:03:51 - Martina
  Mensaje: SIS-4994 - Actualizaciones parametros de Listado Se actualizaron los parametros del listado Datos de contacto Whatsapp para clientes activos respectivos para la nueva actualizacion del SP. Segun lo solicitado en el REC-3045
  Stats: +85 | -21 | 106 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado LSTCLIDTC - Datos de contacto Whatsapp para clientes activos.sql - modified | +85 | -21 | 106 cambios

- e8f69b33d7 - 2026-05-27 12:49:09 - Martina
  Mensaje: SIS-4994 - Actualizacion nombres SP Se actualizó el nombre del SP LST_CLI_ClientesActivosPorTipoContactoque habia quedado mal y no permitia ejecutar el scritp.
  Stats: +5 | -5 | 10 cambios | 2 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado LSTCLIDTC - Datos de contacto Whatsapp para clientes activos.sql - modified | +1 | -1 | 2 cambios
- BD/StoredProcedures/SP_LST_CLI_ClientesActivosPorTipoContacto.sql - modified | +4 | -4 | 8 cambios

### SIS-5047 - Implementar Tramite Tarea Preventiva Masiva

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Mariela Coran
- Etiquetas: VERSION.1.2.28
- SIS relacionados: SIS-4269
- REC: REC-2375
- Descripcion: <p>RECLAMO: REC-2375<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-4269" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-4269" class="jira-issue-macro-key issue-link" title="Implementar Tramite Tarea Preventiva Masiva" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-4269 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Se desea implementar un nuevo tipo de tramite Tarea Preventiva Masiva ( similar al Incidente Masivo) pero que permita gestionar tareas preventivas que se realizan sobre la red o los servicios.</p> <p>La idea es que el tramite se registre y se indique el/los RT tecnicos afectados y su workflow contenga al menos una etapa donde se envia notificacion masiva a los servicios afectados ( usando una plantilla ) y que el tramite se suspenda hasta que exista una etapa de “Inicio de Tarea Preventiva”donde el jsat etiquetara los servicios afectados en ese momento. </p> <p>Una vez que la Tarea Preventiva es finalizada deberia avanzar en el WF para que desetiquete a todos los servicios y se les notifique que se finalizó <img class="emoticon" src="/images/icons/emoticons/help_16.png" height="16" width="16" align="absmiddle" alt="" border="0"/></p> <p>Vamos avanzando con la definicion de este WF.</p> <p>&#8212;<br/> Hola chicos! <br/> Ya estuvimos trabajando sobre el trámite <br/> INCIDPREV - Incidente Masivo Preventivo...

#### REC relacionados
- REC-2375

#### Commits asociados

- dbbe773e08 - 2026-06-08 16:49:34 - MARIELA-CORAN
  Mensaje: SIS-5047 <h3> Notificacion a Clientes desde Servicios</h3> Se incorporan nuevos paramatros para utilizar para el envio de Notificaciones a los clientes con plantillas desde Servicios @@identificadorServicio @@aliasServicio @@domicilioInstalacion REC-2375
  Stats: +10 | -0 | 10 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/notificador/UCNotificarAClientesMasivo.java - modified | +10 | -0 | 10 cambios

### SIS-5061 - Agregar Link de pago CETEVENTOS a cobranzas automaticas

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: CONSULTA_DIRECTA
- SIS relacionados: SIS-4820
- REC: REC-2926
- Descripcion: <p>RECLAMO: <span class="error">&#91;REC-2926&#93;</span><br/> —<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-4820" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-4820" class="jira-issue-macro-key issue-link" title="Agregar Link de pago CETEVENTOS a cobranzas automaticas" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-4820 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>—<br/> Hola Colo, agregue un link de pago CETEVENTOS como el de fichaje para el CET para que ahi puedan ingresar cobranzas de eventos, y le vamos modificando el monto. Seria como el del Fichaje que creamos.</p> <p>Te paso el link y codigo, vos podes hacer que eso se procese?</p> <p><tt><a href="https://mpago.la/1gqB9qu" class="external-link" rel="nofollow noreferrer">https://mpago.la/1gqB9qu</a></tt></p> <p>CETEVENTOS</p> <p>Gracias</p> <p>—</p> <ul> <li><font color="#ff991f">Xime solicitó incorporar otro link de pago, BONOCOLAB, que se procese de la misma manera que se procesa el y que los recibos vayan a la misma cuenta 1519/04 Consumidor final. </font></li> <li><font color="#ff991f">Gracias</font></li> <li>BONOCOLAB<br/> El link de pago es: <br/> <a href="https://mpago.la/2Jcbn8R" title="smart-link" class="external-link" rel="nofollow noreferrer">https://mpago.la/2Jcbn8R</a> <br/> —</li> </ul>

#### REC relacionados
- REC-2926

#### Commits asociados

- 2b09f2a293 - 2026-05-14 15:52:46 - MARIELA-CORAN
  Mensaje: SIS-5061 CET- Incorporacion nuevos links de pago MICRO
  Stats: +33 | -15 | 48 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ImportarMercadoPagoCET_FIJO.sql - modified | +33 | -15 | 48 cambios

- 3a643b608a - 2026-05-27 17:32:25 - ignacio.hahn
  Mensaje: SIS-5061
  Stats: +5 | -8 | 13 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ImportarMercadoPagoCET_FIJO.sql - modified | +5 | -8 | 13 cambios

- 2e74fd18bd - 2026-05-28 12:20:14 - ignacio.hahn
  Mensaje: SIS-5061 fix: el crear lote diario de cobranzas fallaba si el lote a cerrar no tenia comprobantes
  Stats: +1 | -1 | 2 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_COMPROBANTES_LoteCobranzaAlta_CreaLoteDiario.sql - modified | +1 | -1 | 2 cambios

### SIS-5094 - Modificar Listado RTXTSER

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3168
- Descripcion: <p>RECLAMO: REC-3168<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola, buen día.</p> <p>En Menú Técnica → Listados esta el siguiente: <b>RTXTSER Recursos técnicos por tipo de servicio (completo)</b></p> <p>Se solicita que agreguen/reemplacen por nuestro recursos técnicos</p> <ol> <li>Tarjeta/decodificador (de los casados)</li> </ol> <ol> <li>Mininodo</li> </ol> <ol> <li>DPC (drop preconectorizado)</li> </ol> <ol> <li>modulo de telefonia</li> </ol> <ol> <li>AP Mesh</li> </ol> <p>Los pueden reemplazar por cualquier de estas columnas</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30423" alt="imagen-20260429-130235.png" height="70" width="297" style="border: 0px solid black" /></span></p> <p>Desde ya muchas gracias.<br/> Saludos.<br/> MUCH, Pablo.<br/> &#8212;<br/> Podes ver este listado y cambiarlo solo para CPE ?</p> <p>Quizás podemos poner una condición que si existe el tipo de RT Mininodo, va a mostrar unas columnas diferentes a las que esta mostrando actualmente.</p> <p>Después asignamelo a mi para ejecutarlo en producción.</p> <p>Cecilia<br/> &#8212;</p>

#### REC relacionados
- REC-3168

#### Commits asociados

- 3775a64235 - 2026-05-14 17:50:17 - mateo-soto
  Mensaje: SIS-5094 Correcciones en LST_TEC_RT_SERVICIOS
  Stats: +129 | -442 | 571 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_TEC_RT_SERVICIOS.sql - modified | +129 | -442 | 571 cambios

- 3d4c00a128 - 2026-06-01 13:56:36 - mateo-soto
  Mensaje: SIS-5094 Modificar Listado RTXTSER Se modific贸 el listado T茅cnica -> Listado -> RTXTSER para que ahora muestre todos los recursos t茅cnicos relacionados al servicio padre. REC-3168
  Stats: +90 | -67 | 157 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_AFIP_RetRG2126_CargaInicial.sql - modified | +90 | -67 | 157 cambios

### SIS-5104 - Imowi prepago

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: COTIZAR, IMOWI, PREPAGO
- REC: REC-3207
- Descripcion: <p>RECLAMO: REC-3207<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Mariela buenos días.</p> <p>Tal lo conversado con Rene abrimos el ticket.</p> <p>Entonces el me dice que quedaron en definir dos entidades externas de cobranza (Pago Fácil y Rapipago) para procesar los archivos de rendición. Estos deben impactar en la cuenta de cobro de un cliente genérico, permitiendo así la posterior emisión de una factura manual innominada.</p> <p>aguardamos cotización y desde ya muchas gracias<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3207

#### Commits asociados

- a5f1d0e677 - 2026-06-09 15:27:03 - mateo-soto
  Mensaje: SIS-5104 VGG Se agregaron dos nuevas entidades de cobranza: RPPREPAGO y PFPREPAGO. Estas pueden visualizarse en Entidades Externas → Cobranza y se utilizarán para procesar los archivos recibidos. REC-3207
  Stats: +445 | -0 | 445 cambios | 3 archivos
##### Archivos modificados
- BD/Datos/Insert Cobranza - PFPREPAGO - Pago Facil PrePago - VGG.sql - added | +202 | -0 | 202 cambios
- BD/Datos/Insert cobranza - RPPREPAGO - Rapi Pago PrePago - VGG.sql - added | +202 | -0 | 202 cambios
- BD/StoredProcedures/SP_EE_PagoFacilPrePagoPOS.sql - added | +41 | -0 | 41 cambios

- 2ff5983088 - 2026-06-09 18:11:06 - mateo-soto
  Mensaje: SIS-5104 Correcciones -> campos con logitud fija
  Stats: +5 | -6 | 11 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/Insert cobranza - RPPREPAGO - Rapi Pago PrePago - VGG.sql - modified | +5 | -6 | 11 cambios

### SIS-5108 - Solicitar desarrollo para automatizacion de pagos de clientes Banelco-pago mis cuentas.

#### Jira
- Estado: EN ESPERA
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Mariela Coran
- Etiquetas: VERSION.1.2.28
- REC: REC-3211
- Descripcion: <p>RECLAMO: REC-3211<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Estimados, buen dia.</p> <p>Desde contaduria estan interesados en integrar los avisos de pagos de la entidad <b>Banelco-Pago mis cuentas</b> para que impacten automaticamente como lo hace mercado pago hoy en dia.</p> <p>Luego de una reunion con el area tecnica de Prisma, nos brindaron el manual de la API el cual adjunto debajo.</p> <p>En caso de ser factible dicha integracion, esperamos la cotizacion de su desarrollo.</p> <p>Gracias, Saludos. </p> <p>&#8212;<br/> <span class="nobr"><a href="/rest/api/3/attachment/content/30633" title="Manual - API REST - AVISO DE PAGO V 2.3.pdf attached to SIS-5108" data-attachment-type="file" data-attachment-name="Manual - API REST - AVISO DE PAGO V 2.3.pdf" data-media-services-type="file" data-media-services-id="7c24c364-9c82-4dce-9588-36a4eac326b4" rel="noreferrer">Manual - API REST - AVISO DE PAGO V 2.3.pdf<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span><br/> &#8212;</p>

#### REC relacionados
- REC-3211

#### Commits asociados

- 1b619d20a0 - 2026-05-19 13:08:52 - Marcos Rossi
  Mensaje: SIS-5108
  Stats: +82 | -0 | 82 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/ovt/api/pagos/NotificacionesPrismaAPICommand.java - added | +82 | -0 | 82 cambios

- 32ac98ba4c - 2026-05-20 11:46:15 - Marcos Rossi
  Mensaje: SIS-5108: Ajuste de ruta
  Stats: +1 | -1 | 2 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/ovt/api/pagos/NotificacionesPrismaAPICommand.java - modified | +1 | -1 | 2 cambios

### SIS-5112 - Veraz

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: VERAZ, VILLA_GOBERNADOR_GALVEZ-VGG
- REC: REC-3200
- Descripcion: <p>RECLAMO: REC-3200<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Estimados, buen día.</p> <p>Estamos analizando empezar a trabajar con veraz y necesitamos exportar todos los clientes fisicos/juridicos que se encuentren en condición Carta Documento.</p> <p>En la seccion de Entidades externas → Informacion encontramos un listado llamado VERAZ - COMUNICACION o INTIMACION, ambos listados devuelven 2 o 3 clientes. Favor de informarnos si este es el listado que debemos utilizar.</p> <p>En adjunto encontrarán un template con los datos que le debemos enviar a Veraz.</p> <p>Aguardamos sus comentarios.</p> <p>&#8212;<br/> <span class="image-wrap" style=""><a id="30705_thumb" href="/rest/api/3/attachment/content/30705" title="image (4).png" file-preview-type="image" file-preview-id="30705" file-preview-title="image (4).png"><jira-attachment-thumbnail url="https://telpinsistemas.atlassian.net/rest/api/3/attachment/thumbnail/30705?default=false" jira-url="https://telpinsistemas.atlassian.net/rest/api/3/attachment/thumbnail/30705" filename="image (4).png"><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/thumbnail/30705" data-attachment-name="image (4).png" data-attachment-type="thumbnail" data-media-services-id="516a1781-a1f2-4922-a2c7-79de7a3f8146" data-media-services-type="file" style="border: 0px solid black" /></jira-attachment-thumbnail></a></span></p> <p><span class="nobr"><a href="/rest/api/3/attachment/content/30706" title="template_carga_masiva.xlsx attached to SIS-5112" data-attachment-type="file" data-attachment-name="template_carga_masiva.xlsx" d...

#### REC relacionados
- REC-3200

#### Commits asociados

- 862294219f - 2026-05-15 14:52:43 - ignacio.hahn
  Mensaje: SIS-5112 fix: Archivo VERAZ VGG informan ahora como nosotros segun formato 2022
  Stats: +164 | -566 | 730 cambios | 4 archivos
##### Archivos modificados
- BD/Datos/EE-Otros/Insert BP_EspecificacionArchivo VERAZCOM - Comunicar - VGG.sql - modified | +41 | -138 | 179 cambios
- BD/Datos/EE-Otros/Insert BP_EspecificacionArchivo VERAZCOMPR - Comunicar Prueba - VGG.sql - modified | +41 | -142 | 183 cambios
- BD/Datos/EE-Otros/Insert BP_EspecificacionArchivo VERAZINT - Intimar - VGG.sql - modified | +41 | -146 | 187 cambios
- BD/Datos/EE-Otros/Insert BP_EspecificacionArchivo VERAZINTPR - Intimar Prueba - VGG.sql - modified | +41 | -140 | 181 cambios

### SIS-5118 - CPE - Asientos no registrados.

#### Jira
- Estado: EN ESPERA
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3225
- Descripcion: <p>RECLAMO: REC-3225<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola, buen día.<br/> Abro el siguiente requerimiento por un tema de ASIENTOS NO REGISTRADOS que estuvieron manejando Manuel Beneitez y Cecilia Ricci.<br/> Por lo que me comenta Gaston Jorge, <b><em>la cuestión se viene repitiendo en la no generación de asientos diarios pero ademas ayer se agregaron falta de asientos en las cajas.</em></b><br/> Cito chat de Mesa Chica de Telpin por Mariela Coran:</p> <p><em>Ahora, mirando más a detalle, vemos que tampoco se hicieron los siguientes asientos:</em></p> <p><em>P. REG. EGRES. Caja Nro: 22 MERCADO SILVANA</em><br/> <em>P. REG. INGRES. Caja Nro: 40 DE LA MANO NADIA</em><br/> <em>P. REG. EGRES. Caja Nro: 40 DE LA MANO NADIA</em><br/> <em>P. REG. EGRES. Caja Nro: 42 HEREDIA ANOTNELLA</em><br/> <em>P. REG. EGRES. Caja Nro: 58 MAÑAK PABLO</em><br/> <em>P. REG. INGRES. Caja Nro: 83 PEREYRA VICTORIA</em><br/> <em>P. REG. EGRES. Caja Nro: 83 PEREYRA VICTORIA</em><br/> <em>P. REG. EGRES. Caja Nro: 94 RAMOS JULIO</em><br/> <em>P. REG. INGRES. Caja Nro: 104 GUZMAN NICOLAS</em><br/> <em>P. REG. EGRES. Caja Nro: 104 GUZMAN NICOLAS</em><br/> <em>P. REG. EGRES. Caja Nro: 124 MODON EMILSE</em><br/> <em>P. REG. EGRES. Caja Nro: 126 ARRUE LORENA</em><br/> <em>P. REG. EGRES. Caja Nro: 134 ALVAREZ RODRIGO</em><br/> <em>P. REG. EGRES. Caja Nro: 135 RODRIGUEZ SUSANA</em><br/> <em>P. REG. EGRES. Caja Nro: 136 IRIARTE ROMINA</em></p> <p><em>COBRANZAS AUTONOMAS DE JSAT (MACROCLICK DE TELECOMUNICACIONES).</em></p> <p><em>Sin embargo, llama mucho la atención que SÍ se hicieron los as...

#### REC relacionados
- REC-3225

#### Commits asociados

- 54fae250f8 - 2026-05-14 13:21:42 - CECILIA-RICCI
  Mensaje: SIS-5118 <h3>CPE - Listado Asientos vs. Lotes</h3> Dentro de General \ Listados se incorporo este listado que dada una fecha lista los lotes con el estado actual, el o los asientos que genero Jsat y la fecha que se exporto a CPE. REC-3225
  Stats: +51 | -0 | 51 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado ASTLOT - Asientos vs. Lotes.sql - added | +51 | -0 | 51 cambios

- b30628b322 - 2026-05-14 17:49:29 - CECILIA-RICCI
  Mensaje: SIS-5118 Se utiliza en CPE. El SP GENERAL_ExportarAsientosCPE lista los asientos que no estan en GENERAL_BoExportado y los carga en GENERAL_BoExportado, y ellos los cargan en su sistema, pero si les faltan asientos y en jsat figuran exportados, ejecuta este SP que elimina el registro de GENERAL_BoExportado de los asientos del nro de lote que se pasa por parametro. REC-3225
  Stats: +25 | -0 | 25 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_GENERAL_EliminarLogExportado.sql - added | +25 | -0 | 25 cambios

- 2e24b4ba2f - 2026-05-14 17:50:42 - CECILIA-RICCI
  Mensaje: SIS-5118 Agregue que loguee en application log el inicio y fin de ejecucion y los asientos exportados. REC-3225
  Stats: +27 | -2 | 29 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_GENERAL_ExportarAsientosCPE.sql - modified | +27 | -2 | 29 cambios

- 098183ee38 - 2026-05-14 17:51:30 - CECILIA-RICCI
  Mensaje: SIS-5118 Le agregue la fecha de estado del lote para que puedan ven cuando se cerro la caja por ejemplo. REC-3225
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/BP_Listados/BP_Listado ASTLOT - Asientos vs. Lotes.sql - modified | +2 | -2 | 4 cambios

- 2f26640a6f - 2026-05-14 18:10:50 - CECILIA-RICCI
  Mensaje: SIS-5118 Parametrizo los usuarios adicionales a los cuales hay que notificar en caso de tener un comprobante provisorios. REC-3225
  Stats: +7 | -3 | 10 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_GENERAL_AlertaComprobantesProvisorios.sql - modified | +7 | -3 | 10 cambios

### SIS-5120 - Importador API Rest

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Mateo Soto
- Descripcion: <p>Implementar en Java un procesador de líneas llamado ProcesadorLineaAPI basándose en ProcesadorLineaIF.</p> <p>La idea es que cada linea este compuesta asi</p> <p>METODO;URL_RELATIVA;BODY</p> <ul> <li>MEDOTO puede ser GET/POST etc</li> <li>URL es algo del estilo /api/clientes/crear-cliente</li> <li>BODY es un string en formato JSON</li> </ul> <p>El procesador debe tomar los parámetros de sistema USER/PWD para hacer un login inicial y reutilizar en token/sid en cada invocación de API</p> <p>Hay que crear una bptipooperacion para que aparezca en algun menú (<a href="https://telpinsistemas.atlassian.net/secure/ViewProfile.jspa?accountId=60ec9094f749c40068e569e5" class="user-hover" rel="60ec9094f749c40068e569e5" data-account-id="60ec9094f749c40068e569e5" accountid="60ec9094f749c40068e569e5" rel="noreferrer">Matias Garofalo</a> sabe)</p>

#### Commits asociados

- 16e4acbfa4 - 2026-05-14 13:22:45 - mateo-soto
  Mensaje: SIS-5120 Procesador de lineaAPI
  Stats: +1176 | -323 | 1499 cambios | 30 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/arenero/api/GetFixtureAPIComand.java - modified | +40 | -11 | 51 cambios
- src/JSAT/project/src/com/telpin/jsat/clientes/api/CrearClienteCommand.java - modified | +43 | -37 | 80 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/CambioDomicilioCommand.java - modified | +26 | -26 | 52 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/CambioTecnologiaCommand.java - modified | +18 | -18 | 36 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/CargarDatosVender.java - modified | +42 | -37 | 79 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/ProcesarAltaUc.java - modified | +75 | -68 | 143 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/ProcesarUc.java - modified | +83 | -96 | 179 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/ValidarDatos.java - modified | +8 | -8 | 16 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/CrearCuentaCobroCommand.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/ctaCtes/api/dto/CuentaCobroCrearDTO.java - modified | +1 | -1 | 2 cambios
- src/JSAT/project/src/com/telpin/jsat/importador/ProcesadorLineaAPI.java - added | +259 | -0 | 259 cambios
- tools/bruno/api-telpin/automatico/crear-acuerdo-facturacion.bru - renamed | +5 | -8 | 13 cambios
- tools/bruno/api-telpin/automatico/crear-cliente-fisica.bru - added | +41 | -0 | 41 cambios
- tools/bruno/api-telpin/automatico/crear-cliente-juridica.bru - added | +41 | -0 | 41 cambios
- tools/bruno/api-telpin/automatico/crear-cuenta-cobro.bru - added | +41 | -0 | 41 cambios
- tools/bruno/api-telpin/automatico/crear-persona-fisica.bru - modified | +2 | -2 | 4 cambios
- tools/bruno/api-telpin/automatico/crear-persona-juridica.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/results.json - added | +336 | -0 | 336 cambios
- tools/bruno/api-telpin/testing/acuerdoFacturacion/casos-ok/crear-acuerdo-facturacion.bru - modified | +2 | -2 | 4 cambios
- tools/bruno/api-telpin/testing/comercial/baja-producto/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/buscar/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/cambio-domicilio/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/cambio-tecnologia/LINEATOTALFO.bru - added | +37 | -0 | 37 cambios
- tools/bruno/api-telpin/testing/comercial/cambio-tecnologia/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/vender-producto-plan-tasacion/folder.bru - added | +8 | -0 | 8 cambios
- tools/bruno/api-telpin/testing/comercial/vender-producto-plan-tasacion/plan13-ok.bru - added | +29 | -0 | 29 cambios
- tools/bruno/api-telpin/testing/comercial/vender-productos-articulo/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/vincular-servicios/folder.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/cuentaCobro/casos-ok/crear-cuenta-cobro.bru - modified | +1 | -1 | 2 cambios
- tools/bruno/run-tests.bat - added | +30 | -0 | 30 cambios

- bdd93f436e - 2026-05-14 19:08:23 - mateo-soto
  Mensaje: SIS-5120 Correcciones en el ProcesadorLineaAPI
  Stats: +18 | -99 | 117 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/importador/ProcesadorLineaAPI.java - modified | +18 | -99 | 117 cambios

### SIS-5124 - Reporte de error en Liquidacion Banelco

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: RENDICION_COMISION
- REC: REC-3230
- Descripcion: <p>RECLAMO: REC-3230<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Se abre Req debido a que recibimos un reporte de error por el proceso de la Liquidacion de Banelco. Abrimos el archivo y vemos que en esa Liq se agrega una Ret de IIBB que en anteriores liquidaciones no incluia, podria ser ese el motivo.</p> <p>Se adjunta el archivo y dejo citado lo que reporta el error.</p> <p>Gracias!!!</p> <p>Rendicion de CC-Banelco-PagoMisCuentas procesada con ERROR<br/> Archivo:\10.10.3.15\documentos-jsat\subidas\CC1\2026-05\LIQ2413.P.130526.html<br/> El total a liquidar no coincide con el total del lote - el total de deducciones.</p> <p><span class="nobr"><a href="/rest/api/3/attachment/content/30845" title="LIQ2413.P.130526.html attached to SIS-5124" data-attachment-type="file" data-attachment-name="LIQ2413.P.130526.html" data-media-services-type="file" data-media-services-id="efcdabb4-e19c-49e4-86d6-782abfe62a1a" rel="noreferrer">LIQ2413.P.130526.html<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span></p> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3230

#### Commits asociados

- 7d4b7d083b - 2026-05-14 18:40:14 - CECILIA-RICCI
  Mensaje: SIS-5124 Esta informando importe de percepcion de IIBB que no lo estabamos tomando.
  Stats: +36 | -3 | 39 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ComisionBanelco.sql - modified | +36 | -3 | 39 cambios

- 00416a04a1 - 2026-05-18 18:27:49 - CECILIA-RICCI
  Mensaje: SIS-5124 El importe de IIBB es retencion, no percepcion
  Stats: +5 | -5 | 10 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ComisionBanelco.sql - modified | +5 | -5 | 10 cambios

### SIS-5125 - Indicador novedades versión JSAT

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Matias Garofalo
- Descripcion: <p>Cuando sale una versión nueva de JSAT, queremos informar a los usuarios cuáles son la novedades de la misma.</p> <p>La idea es mostrar un indicador visual en la pantalla principal que “llame la atención” y que al hacer click abra la pantalla de ayuda en un topic específico (NOVEDADES_*)</p> <p>Es deseable que este indicador se muestre durante los primeros días de la versión y luego que desaparezca (de todas formas al hacer click en el número de versión, que siga abriendo la pantalla)</p> <p>Por otro lado, se debe generar el contenido para la pantalla de ayuda a partir de los commits recientes.</p>

#### Commits asociados

- 0b5c2d7643 - 2026-05-14 13:11:34 - matias.garofalo
  Mensaje: SIS-5125 SP_GENERAL_MostrarReadme retorna true o false si debe el indicador de version en función de la cantidad de días que se instalo la versión (no cuenta sábados y domingos) y lo mostrara por 3 dias. SP_HELP_CrearScripts.sql se modifico para que reciba como parámetro si debe generar el archivo o si debe retornar el SELECT para que otro proceso genere el archivo. El gestor-versiones.xml se modifico para que en lugar de llamar a la ayuda con osql lo haga con sqlcmd y llame al SP anterior para que muestre el select y se exporte con el comando de Ant
  Stats: +71 | -7 | 78 cambios | 3 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_GENERAL_MostrarReadme.sql - added | +47 | -0 | 47 cambios
- BD/StoredProcedures/SP_HELP_CrearScripts.sql - modified | +21 | -5 | 26 cambios
- versiones/gestor-versiones.xml - modified | +3 | -2 | 5 cambios

- 2cdc25e5ef - 2026-05-14 18:38:24 - Marcos Rossi
  Mensaje: SIS-5125
  Stats: +11 | -11 | 22 cambios | 2 archivos
##### Archivos modificados
- src/JSAT/project/web/arenero/container.jsp - modified | +1 | -1 | 2 cambios
- src/JSAT/project/web/arenero/styles/arenero.css - modified | +10 | -10 | 20 cambios

### SIS-5127 - Reclamos - Problemas en los Cambio de Etapas del WK del mismo nivel

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- SIS relacionados: SIS-4917
- REC: REC-3022
- Descripcion: <p>RECLAMO: REC-3022<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-4917" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-4917" class="jira-issue-macro-key issue-link" title="Reclamos - Problemas en los Cambio de Etapas del WK del mismo nivel" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-4917 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Hola, buen día.<br/> Luciano plantea lo siguiente:<br/> Al momento de que una cuadrilla de "reclamos propia" cambia de etapa un trabajo cuadrilla domicilio a Trabajo Plantel Exterior (ticket), JSAT en vez de mantener abierto el reclamo, lo finaliza y genera el trámite a Plantel Exterior (ticket). Esto hace que automáticamente le llegue al usuario una notificación de que su trámite (reclamo) a sido finalizado, y no es así, normalmente hasta que Plantel Exterior no realiza sus tareas de reparación (ticket) no queda normalizado el servicio del usuario; es más, en ocasiones la cuadrilla de reclamos tiene que volver al domicilio luego de que Plantel Exterior finaliza el ticket correspondiente. <br/> En definitiva ver la manera de que el reclamo siga abierto y la notificación de finalización y cierre del mismo (reclamo) no le llegue al usuario hasta tanto este se finalice completamente; o no generarse un nuevo reclamo al pasar a TRABAJO PLANTEL EXTERIOR.- <br/> Esto corre para todos los t...

#### REC relacionados
- REC-3022

#### Commits asociados

- 64212114e5 - 2026-05-18 17:51:39 - Martina
  Mensaje: SIS-5127 - Actualización en Tramites de Reclamos <H3> CPE - Cambios en Reclamos </h3> Se actualizaron los WF de Reclamos de Telefonía e Internet para que ahora los técnicos puedan pasar de la etapa Trabajo en Domicilio a Trabajo de Obra. Según lo solicitado en el REC-3022.
  Stats: +2 | -0 | 2 cambios | 2 archivos
##### Archivos modificados
- src/JSAT/project/src/processDefinitions/cpe/UCReclamosInternetCPE.xml - modified | +1 | -0 | 1 cambios
- src/JSAT/project/src/processDefinitions/cpe/UCReclamosTelefoniaCPE.xml - modified | +1 | -0 | 1 cambios

### SIS-5130 - Reunion 13/05

#### Jira
- Estado: En curso
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Matias Garofalo
- REC: REC-3243
- Descripcion: <p>RECLAMO: REC-3243<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Luego de la reunión del 13/05 surgieron algunas mejoras para incorporar a JSATElite</p> <p>Información del Servicio/Cliente</p> <ul> <li>Agregar DNI/CUIT</li> <li>Incorporar Alias del Servicio</li> <li>Incluir la IP de la ONT. Esta informacion hay que consultar con Rodrigo si puede incoporarla a cuando realiza la consultada de estado de la misma o del DHCP mediante una invocación. Esta ultima opción hoy se usa para las ONTs Raisecom antes de aprovisionarlas</li> <li>Medición de la ONT</li> <li>Estado de la ONT</li> </ul> <p>Búsquedas Adicionales</p> <ul> <li>Agregar por Cliente, de igual manera que se consulta en jsat</li> <li>Agregar por Tramite, de igual manera que se consulta en jsat</li> </ul> <p>Impresión</p> <ul> <li>Mejorar la calidad de la impresión porque se ve pixelada</li> <li>Luego de la impresión, ver como queda la interacción, porque luego de esta operación, pierdo lo seleccionado.</li> </ul> <p>Herramientas</p> <ul> <li>Unificar las herramientas de Navegación con la de Selección y que este marcado por defecto. Cuando elija un elemento del se comportara de igual que la Selección y si no es elemento nuestro como el de navegación.</li> <li>Si elijo de las herramientas, la opción de Medir y luego elijo otra sin medir, queda seteada para medir.</li> </ul> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3243

#### Commits asociados

- 7040b226fe - 2026-05-27 12:02:33 - matias.garofalo
  Mensaje: SIS-5130 Agrego a la respuesta de la API, el Alias y el DNI/CUIT
  Stats: +49 | -4 | 53 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/ServicioDTO.java - modified | +49 | -4 | 53 cambios

- acec60cbc2 - 2026-06-09 12:56:34 - matias.garofalo
  Mensaje: SIS-5130 Agrego soporte para mostrar informacion del estado de la ONT y de las conexiones a Radius para determinar la IP.
  Stats: +379 | -58 | 437 cambios | 8 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_INFO_TEC_Caja.sql - modified | +25 | -15 | 40 cambios
- BD/StoredProcedures/SP_JOB_CargarInfoONT.sql - modified | +59 | -9 | 68 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/InfoTecnicaServicioDTO.java - added | +74 | -0 | 74 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/PosicionDTO.java - modified | +11 | -0 | 11 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/ServicioDTO.java - modified | +148 | -0 | 148 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/ConectorInternet.java - modified | +55 | -34 | 89 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/ConectoresMngr.java - modified | +6 | -0 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/RecursoTecnicoDao.java - modified | +1 | -0 | 1 cambios

- d4b99dd406 - 2026-06-11 16:13:48 - matias.garofalo
  Mensaje: SIS-5130 Agrego el api command para la busqueda de clientes desde jsatelite
  Stats: +94 | -2 | 96 cambios | 3 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/api/ClientesAPICommand.java - added | +46 | -0 | 46 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/ClienteDTO.java - added | +46 | -0 | 46 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/ServicioDTO.java - modified | +2 | -2 | 4 cambios

### SIS-5132 - TELPIN - Envío de mail desde pop up de información a múltiples casillas

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: VERSION.1.2.28
- SIS relacionados: SIS-5093
- Descripcion: <p>Hablando por un cambio de WF de Asistencias Comerciales con Florencia Vuk ( <span class="jira-issue-macro resolved" data-jira-key="SIS-5093" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5093" class="jira-issue-macro-key issue-link" title="cambio en COMAST - Asistencia Comercial " > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5093 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> ) me comenta que no le llegan los mails de notificación.<br/> En el caso particular de Telpin, Planisys no reconoce múltiples destinatarios en el TO de un mail y termina enviando el mail al primero que encuentra (lo marco en amarillo).<br/> Habría que tokenizar la lista de destinarios y hacer un envío para cada uno.</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30995" alt="image-20260518-145313.png" width="667" style="border: 0px solid black" /></span></p>

#### Commits asociados

- a34f683a3e - 2026-05-19 14:41:42 - ignacio.hahn
  Mensaje: SIS-5132
  Stats: +14 | -1 | 15 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/arenero/web/InfoUseCaseWH.java - modified | +14 | -1 | 15 cambios

### SIS-5141 - Extender el plazo de baja de debitos

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- REC: REC-3251
- Descripcion: <p>RECLAMO: REC-3251<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenos días. Quisieramos pedirles que el plazo de baja automatica de debitos tanto directo como automatico sea extendido a 6 rechazos consecutivos. Quedamos a la espera de su respuesta. Saludos.<br/> &#8212;<br/> <font color="#ff991f">Martu, Ceci me comentó que podias resolver esto y dice: </font></p> <p><font color="#ff991f"><b><em>Tenemos una regla definida en cada cooperativa que indica si se da de baja y evaluamos cuantos rechazos tuvo y si es mayor que uno lo damos de baja, asi que ellos puede ser que nunca lo den de baja o aumentar la cantidad de rechazos.</em></b> </font></p> <p><font color="#ff991f">Y me pasó esta info: </font><font color="#ff991f"><b><em>la regla con codigo DA Anular evalua el SP DIN_Regla_DebitoAutomaticoAnular</em></b></font><br/> &#8212;</p>

#### REC relacionados
- REC-3251

#### Commits asociados

- 0bb11f8ce6 - 2026-05-19 13:41:43 - Martina
  Mensaje: SIS-5141 - Anular debito automatico <H3> BATAN - Cambios en Anular Debito Automatico </h3> Se modificó la regla que anula los debitos automáticos para que lo haga a los 6 meses consecutivos de rechazo. Segun lo solicitado en el REC-3251.
  Stats: +30 | -0 | 30 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/Dinamicos/DIN_Regla_DebitoAutomaticoAnular - BATAN.sql - added | +30 | -0 | 30 cambios

### SIS-5150 - Extender el plazo de baja de debitos

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- SIS relacionados: SIS-5141
- REC: REC-3251
- Descripcion: <p>RECLAMO: REC-3251<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5141" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5141" class="jira-issue-macro-key issue-link" title="Extender el plazo de baja de debitos" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5141 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Buenos días. Quisieramos pedirles que el plazo de baja automatica de debitos tanto directo como automatico sea extendido a 6 rechazos consecutivos. Quedamos a la espera de su respuesta. Saludos.<br/> &#8212;<br/> <font color="#ff991f">Martu, esto dice Batan: </font></p> <p><font color="#ff991f"><em>Buen día. Consulta. En la respuesta dijeron 6 MESES, pero en el pedido son 6 VECES</em></font><br/> <font color="#ff991f"><em>porque nosotros hacemos 3 presentaciones por mes o sea, serían en meses 2 consecutivos de rechazos.¿Es asi? o ¿modificaron para que sean 6 meses?</em> </font><br/> &#8212;</p>

#### REC relacionados
- REC-3251

#### Commits asociados

- bd5b0783a9 - 2026-05-21 19:04:56 - Martina
  Mensaje: SIS-5150 - Extender el plazo de Baja de Debitos <H3> BATAN - Actualizacion Anular Debito Automatico </H3> Se actualizó la condicion para anular los debitos automaticos despues de 6 rechazos consecutivos. Según lo solicitado en el REC-3251
  Stats: +34 | -24 | 58 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/Dinamicos/DIN_Regla_DebitoAutomaticoAnular - BATAN.sql - modified | +34 | -24 | 58 cambios

### SIS-5155 - Diferencias entre Ver Deuda y Facturar deuda.

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3265, REC-3113
- Descripcion: <p>RECLAMO: REC-3265<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Este REC se empezó a gestionar sobre el <a href="https://telpinsistemas.atlassian.net/browse/REC-3113" title="smart-link" class="external-link" rel="nofollow noreferrer">https://telpinsistemas.atlassian.net/browse/REC-3113</a> </p> <p>el caso planteado inicialmente quedó resuelto y luego se planteó otro inconveniente que no tiene relacion, se gestionará aparte.</p> <ul> <li>Se generó una diferencia entre el monto de la 'liquidar deuda' y el monto de la factura emitida, debido a que la liquidación no consideró todos los tickets pendientes de facturación (correspondientes a decodificadores de TV).</li> <li>Se eliminó y se volvió a generar el comprobante, logrando finalmente su emisión correcta, pero con un importe superior al acordado inicialmente.</li> <li>Se solicita investigar por qué el proceso de 'liquidar deuda' no considera todos los tickets pendientes, generando inconsistencias.</li> <li>Se está intentando simular el proceso en una base de pruebas para identificar la causa de las diferencias, pero la base de datos presenta demoras.<br/> &#8212;</li> </ul> <p>&#8212;</p>

#### REC relacionados
- REC-3265
- REC-3113

#### Commits asociados

- 25d2829526 - 2026-05-22 11:33:26 - CECILIA-RICCI
  Mensaje: SIS-5155 Le puse union all para que muestre todos los tickets.
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_RPT_CTACTES_VerDeuda.sql - modified | +2 | -2 | 4 cambios

### SIS-5156 - CPE - Pago sobre Cuenta de Refinanciación (Saldo en Negativo)

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3253, REC-3118
- Descripcion: <p>RECLAMO: REC-3253<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola, buenas tardes.<br/> Gastón reporta lo siguiente como problema reiterado:<br/> <em>Pagaron sobre la cuenta de re financiación y ese saldo negativo no veo forma de pasarlo a la otra cuenta. Si pasas el saldo negativo arriba lo toma como débito en lugar de crédito. Esta la muestra en testing.</em> <br/> <em>De arriba pasar 2000 la cuenta de re financiación no te deja.</em><br/> <em>Y si das de baja la cuenta de re financiación tampoco sube el crédito.</em></p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31237" alt="imagen-20260519-163224.png" height="321" width="1833" style="border: 0px solid black" /></span></p> <p><em>Ver forma de solucionarlo.</em></p> <hr /> <p>Estuve leyendo lo propuesto en el Rec 3118 (creo que es un tema similar), pero por lo que leo lo terminaron solucionando ustedes. No termino de captar la idea de lo que hay que hacer en estos casos, por tanto abro este requerimiento para ver si efectivamente podemos hacerlo nosotros o tienen que hacerlo ustedes.<br/> Desde ya muchas gracias.<br/> Saludos.<br/> MUCH, Pablo.<br/> &#8212;<br/> Los movimientos de deuda los hacemos desde acá</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31236" alt="imagen-20260520-131225.png" height="299" width="1835" style="border: 0px solid black" /></span></p> <p>Eligiendo la opción transferir saldo<br/> &#8212;</p>

#### REC relacionados
- REC-3253
- REC-3118

#### Commits asociados

- d26e4dc4da - 2026-05-21 14:00:24 - CECILIA-RICCI
  Mensaje: SIS-5156 Va a cargar el valor del comporbante que se vence si es menor que el saldo total de la cuenta de cobro, sino toma el saldo de la cuenta de cobro.
  Stats: +2 | -1 | 3 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_COMPROBANTES_LoteComprobanteCuotasRefinGenerar.sql - modified | +2 | -1 | 3 cambios

### SIS-5164 - Corregir SQLProxyHelper

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- Descripcion: <p><a href="https://chatgpt.com/share/6a10b2a3-7cb0-83e9-b934-3efd979335e9" class="external-link" rel="nofollow noreferrer">https://chatgpt.com/share/6a10b2a3-7cb0-83e9-b934-3efd979335e9</a></p>

#### Commits asociados

- 8c29306301 - 2026-05-26 13:08:00 - Marcos Rossi
  Mensaje: SIS-5164
  Stats: +111 | -87 | 198 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/SQLProxyHelper.java - modified | +111 | -87 | 198 cambios

### SIS-5168 - CPE - App Técnicos - Visualización de trabajos

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- REC: REC-3271
- Descripcion: <p>RECLAMO: REC-3271<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buen día.</p> <p>Necesitaría que la siguiente cuadrilla visualice <b>un domicilio por vez</b>: </p> <ul> <li>CPampa 1 </li> </ul> <p>Gracias.</p> <p>MUCH, Pablo.<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3271

#### Commits asociados

- 5741a0c514 - 2026-05-26 18:16:36 - ignacio.hahn
  Mensaje: SIS-5168 CPE: Visualizacion en la APP solo un tramite a la vez para CPAMPA1
  Stats: +1 | -0 | 1 cambios | 1 archivos
##### Archivos modificados
- BD/Datos/Dinamicos/DIN_TRA_ObtenerIDEtapasTramitesParaUsuarioMobile - CPE.sql - modified | +1 | -0 | 1 cambios

### SIS-5178 - reporte totales de facturación - cantidad de facturas a imprimir

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- SIS relacionados: SIS-4724
- REC: REC-2830
- Descripcion: <p>RECLAMO: REC-2830<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-4724" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-4724" class="jira-issue-macro-key issue-link" title="reporte totales de facturación - cantidad de facturas a imprimir" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-4724 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> En cada proceso de facturación sacamos desde el lote a facturar , el reporte totales de facturación . </p> <p>En éste caso facturamos el 1/2/26 los lotes 72408 y 77169 , en la cantidad de comprobantes a imprimir , ahora tenemos 747 piezas más que el mes pasado.</p> <p>Ahora que ya está cerrado , puedo listar los comprobantes para oca y veo que en lote mensual tengo 67 comprobantes para imprimir y en el del área extendida … 124</p> <p>Podrán verificar por favor ?</p> <p>gracias</p> <p><span class="nobr"><a href="/rest/api/3/attachment/content/31459" title="totales facturacion 77169.xls attached to SIS-5178" data-attachment-type="file" data-attachment-name="totales facturacion 77169.xls" data-media-services-type="file" data-media-services-id="ef0a8ed1-cd9f-42ee-b89e-32b132a546d7" rel="noreferrer">totales facturacion 77169.xls<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span><br/> <span class="...

#### REC relacionados
- REC-2830

#### Commits asociados

- a6c9e4cdf8 - 2026-05-29 13:13:31 - ignacio.hahn
  Mensaje: SIS-5178 fix: total de comprobantes a imprimir
  Stats: +35 | -23 | 58 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_COMPROBANTES_TotalFacturacion.sql - modified | +35 | -23 | 58 cambios

### SIS-5187 - Listado de servicios telefonicos

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- REC: REC-3303
- Descripcion: <p>RECLAMO: REC-3303<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenas tardes. Queriamos pedirles si existe la posibilidad de obtener un listado de clientes que solo tengan servicios TELB o TELSIPI nada mas sin ningun servicio de internet. Muchas gracias.<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3303

#### Commits asociados

- 1a047514b3 - 2026-06-01 14:19:54 - Martina
  Mensaje: SIS-5187 - Correcciones listado LSTCLIDC Se corrigió el listado de clientes Datos de Clientes con Servicios Activos ya que los filtros no se aplicaban bien, haciendo que se incluyeran los servicios que se querían excluir. Según el pedido del REC-3303 se corrigió este listado para solucionarlo.
  Stats: +231 | -226 | 457 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_CLIENTES_ClientesDatosContactoSegunServicios.sql - modified | +231 | -226 | 457 cambios

### SIS-5190 - CPE - Acreditación automática de Macro Click Pagos.

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- REC: REC-3309
- Descripcion: <p>RECLAMO: REC-3309<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola buen día.<br/> Se me solicita que abra el siguiente requerimiento.<br/> Debido a la reunión mantenida en el día de hoy entre Mariela Coran, Manuel Beneitez, Iara Arcuri y Gaston Jorge; se solicita la acreditación automática de pagos Macro Click.<br/> Saludos. Muchas gracias.<br/> MUCH, Pablo.<br/> &#8212;<br/> Te paso Nacho, gracias.<br/> &#8212;</p>

#### REC relacionados
- REC-3309

#### Commits asociados

- cc4f46c709 - 2026-06-16 12:11:49 - ignacio.hahn
  Mensaje: SIS-5190 El finalizar aviso de pago ahora chequea contra IC
  Stats: +1 | -1 | 2 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_TRAMITE_AvisoPagoFinalizar.sql - modified | +1 | -1 | 2 cambios

### SIS-5191 - CPE - Descarga de Factura y asentar Avisos de Pagos por API

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Marcos Rossi
- REC: REC-3308
- Descripcion: <p>RECLAMO: REC-3308<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola buen día.<br/> Se me solicita que abra el siguiente requerimiento.<br/> Debido a la reunión mantenida en el día de hoy entre Mariela Coran, Manuel Beneitez, Iara Arcuri y Gaston Jorge; se solicita el acceso a la API para descargar la factura y asentar avisos de pago.<br/> Saludos. Muchas gracias.<br/> MUCH, Pablo.</p> <p>&#8212;<br/> Te lo paso para dejar mas detalles de lo que conversaron, gracias.<br/> &#8212;</p>

#### REC relacionados
- REC-3308

#### Commits asociados

- 469fc24284 - 2026-06-02 12:42:11 - Marcos Rossi
  Mensaje: SIS-5191
  Stats: +107 | -5 | 112 cambios | 4 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/ovt/api/AvisoPagoAPICommand.java - modified | +13 | -3 | 16 cambios
- src/JSAT/project/src/com/telpin/jsat/ovt/api/GetComprobantesParaCPEAPI.java - added | +72 | -0 | 72 cambios
- src/JSAT/project/src/com/telpin/jsat/ovt/api/GetComprobantesParaCuentaCobroAPICommand.java - modified | +12 | -2 | 14 cambios
- src/JSAT/project/src/com/telpin/jsat/ovt/api/dto/ComprobantesParaCPEDTO.java - added | +10 | -0 | 10 cambios

### SIS-5194 - Tramites Calculo Promedio Dias en Finalizar Semanal

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- REC: REC-3312
- Descripcion: <p>RECLAMO: REC-3312<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Necesitaría por favor saber en qué etapa se encuentran los trámites pendientes (podría agregarse cuando elijo la opción de información detallada).<br/> Gracias!<br/> &#8212;<br/> <font color="#ff991f">Martu, me avisa Ceci que te lo pase asi lo podes analizar, gracias.</font><br/> &#8212;</p>

#### REC relacionados
- REC-3312

#### Commits asociados

- af8fffc54b - 2026-06-10 14:19:57 - Martina
  Mensaje: SIS-5194 - Correcciones Listado Calculo Promedio Días Corregido el query en la condicion de buscar la etapa actual del tramite. Segun REC-3312
  Stats: +13 | -20 | 33 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_TEC_PromedioDiasFinalizarTramiteSemanal.sql - modified | +13 | -20 | 33 cambios

### SIS-5195 - Tramites Calculo Promedio Dias en Finalizar Semanal

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- SIS relacionados: SIS-5194
- REC: REC-3312
- Descripcion: <p>RECLAMO: REC-3312<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5194" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5194" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5194 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Necesitaría por favor saber en qué etapa se encuentran los trámites pendientes (podría agregarse cuando elijo la opción de información detallada).<br/> Gracias!<br/> &#8212;<br/> <font color="#ff991f">Martu, me avisa Ceci que te lo pase asi lo podes analizar, gracias.</font></p> <p>Existe un listado llamado:</p> <p>LSTCALPTFS - Tramites Calculo Promedio Dias en Finalizar Semanal</p> <p>Desde Tramites/Listados.</p> <p>Ahi quiere que se agregue en que etapa se encuentran.<br/> &#8212;</p>

#### REC relacionados
- REC-3312

#### Commits asociados

- 7178ebebbd - 2026-06-09 17:08:49 - Martina
  Mensaje: SIS-5195 - Listado Calculo Promedio Dias en Finalizar Semana <H3> Telpin - Etapa actual en Calculo Promedio D铆as </h3> Se actualiz贸 el listado LSTCALPTFS - Tramites Calculo Promedio Dias en Finalizar Semanal para agregar la columna de 'Etapa actual' de cada tramite. Segun lo solicitado en el REC-3312
  Stats: +50 | -42 | 92 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/LST_TEC_PromedioDiasFinalizarTramiteSemanal.sql - modified | +50 | -42 | 92 cambios

### SIS-5198 - Falla en almacenamiento donde se aloja la BD MASTER de JSAT y dificultad para recuperar los backups diferenciales para recuperar la informacion

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- SIS relacionados: SIS-5177
- REC: REC-3289
- Descripcion: <p>RECLAMO: REC-3289<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5177" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5177" class="jira-issue-macro-key issue-link" title="Falla en almacenamiento donde se aloja la BD MASTER de JSAT y dificultad para recuperar los backups diferenciales para recuperar la informacion" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5177 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Se detectó una falla en las unidades de disco correspondientes a las bases de datos históricas y archivos LOG del servidor JSAT BD MASTER.</p> <p>Actualmente, el servidor presenta un comportamiento inestable y no existen garantías operativas de funcionamiento normal sostenido. Por este motivo, y con asistencia de TELPIN, se decidió poner en servicio el servidor BD SLAVE utilizando los backups disponibles.</p> <p>TELPIN se encuentra analizando la posibilidad de restaurar los backups diferenciales para completar la actualización de la base de datos.</p> <p>En caso de no resultar viable la recuperación completa mediante diferenciales, se procederá a levantar el servicio utilizando únicamente el backup full disponible, lo que permitiría restablecer la operatividad de JSAT con información consistente hasta las 04:00 hs del día de hoy.</p> <p>Les pedimos por favor si nos pueden asistir en el análisis de alternativ...

#### REC relacionados
- REC-3289

#### Commits asociados

- 542f4ec494 - 2026-06-02 14:28:59 - CECILIA-RICCI
  Mensaje: SIS-5198 en Tortuguitas tienen 3 talonarios con el mismo numerador y al actualizar el numero verifica si hay un comprobante con el mismo numero y numerador y daba error. Lo cambie a que busque por mismo numero y talonario.
  Stats: +5 | -9 | 14 cambios | 1 archivos
##### Archivos modificados
- BD/Triggers/TRG_Comprobante_FormateaNro.sql - modified | +5 | -9 | 14 cambios

### SIS-5201 - Modificacion Agenda turno reclamos para que muestre disponibilidad en el dia

#### Jira
- Estado: En curso
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: VERSION.1.2.28
- REC: REC-3307
- Descripcion: <p>RECLAMO: REC-3307<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola chicos, estuve hablando con Ceci el viernes sobre un cambio que estamos necesitando en las agendas de turno. Especificamente sobre la de reclamos pinamar, queremos implementar ir en el dia a realizar reclamos (famoso proyecto AM/PM) pero hoy en dia entiendo que no se muestran los turnos del dia que estan libres y es una condición que no podemos editar desde la pantalla. El parametro que hoy existe es Dias demora asignacion Comercial y esta en 0 pero no muestra los turnos del mismo dia, con lo cual supongo que hay alguna otra regla interna.</p> <p>Lo que quisieramos es cambiar la granularidad de esa agenda RECLAMOS TEL, INT, IPTV a Mañana y tarde (esto lo podemos ya hacer desde JSAT) y que podamos elegir que hasta las 12am muestre turnos disponibles del dia que esten libres por la tarde. </p> <p>Me avisan y charlamos cualquier duda.</p> <p>Gracias</p> <p>&#8212;<br/> <font color="#ff991f">Cambiar la granularidad de esa agenda RECLAMOS TEL, INT, IPTV a Mañana y tarde</font><br/> &#8212;</p>

#### REC relacionados
- REC-3307

#### Commits asociados

- dca49a7d93 - 2026-06-23 12:04:57 - CECILIA-RICCI
  Mensaje: SIS-5201 Modifique que los turnos disponibles de una agenda se tomen desde el SP DIN_GetTurnosLibresAgenda. Esto permite que podamos poner condiciones segun lo requieran.
  Stats: +232 | -7 | 239 cambios | 2 archivos
##### Archivos modificados
- BD/Datos/Dinamicos/DIN_GetTurnosLibresAgenda-DEFAULT.sql - added | +47 | -0 | 47 cambios
- src/JSAT/project/src/com/telpin/arenero/tramite/bo/AgendaTurnosOcupacionDao.java - modified | +185 | -7 | 192 cambios

### SIS-5205 - Mal confección de la factura

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: REPORTES
- REC: REC-3278
- Descripcion: <p>RECLAMO: REC-3278<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenos dias, tenemos el reclamo de un usuario que pasó a responsable inscripto sin percepción.</p> <p>Con esta condición no discrimina entre el 21% y el 27%, si bien lo calcula bien lo agrupa todo en el de 21%. Y además aparece la leyenda "El importe de IVA discriminado en la presente factura no puede computarse como Crédito Fiscal" esa leyenda no va!!!.</p> <p>Adjunto la factura emitida</p> <p>saludos!</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31836" alt="lXxIeLcTSmLnU2Bl-20260526-140947.png" height="675" width="1263" style="border: 0px solid black" /></span></p> <p>NICOLAI Patricia<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3278

#### Commits asociados

- d56f8901a7 - 2026-06-03 16:15:19 - CECILIA-RICCI
  Mensaje: SIS-5205 En el caso de la condición de iva responsable inscripto sin percepción, no muestre la leyenda, 'El importe de I.V.A discriminado en la presente factura no puede computarse como Crédito Fiscal', al igual que lo hace en el caso de Inscriptos.
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_RPT_COMPROBANTES_Factura_MultiServicios.sql - modified | +2 | -2 | 4 cambios

### SIS-5213 - Verificar demora envio de mail Planysis

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Marcos Rossi
- Etiquetas: PROXIMA_VERSION
- REC: REC-3327
- Descripcion: <p>RECLAMO: REC-3327<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Verificar demora envio de mail Planysis<br/> &#8212;<br/> Creado por Majo a pedido de Mariela. Desarrolla Rossi.<br/> &#8212;</p>

#### REC relacionados
- REC-3327

#### Commits asociados

- 9ca2cf0d34 - 2026-06-04 14:15:06 - Marcos Rossi
  Mensaje: SIS-5213
  Stats: +279 | -31 | 310 cambios | 4 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/arenero/server/Application.java - modified | +1 | -0 | 1 cambios
- src/JSAT/project/src/com/telpin/arenero/utils/MailHelper.java - added | +207 | -0 | 207 cambios
- src/JSAT/project/src/com/telpin/jsat/general/uc/UCEnviarMails.java - modified | +43 | -26 | 69 cambios
- src/JSAT/project/src/com/telpin/jsat/general/uc/UCEnviarUnMail.java - modified | +28 | -5 | 33 cambios

### SIS-5220 - Mal confección de la factura

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: REPORTES
- SIS relacionados: SIS-5205
- REC: REC-3278
- Descripcion: <p>RECLAMO: REC-3278<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5205" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5205" class="jira-issue-macro-key issue-link" title="Mal confección de la factura" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5205 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Buenos dias, tenemos el reclamo de un usuario que pasó a responsable inscripto sin percepción.</p> <p>Con esta condición no discrimina entre el 21% y el 27%, si bien lo calcula bien lo agrupa todo en el de 21%. Y además aparece la leyenda "El importe de IVA discriminado en la presente factura no puede computarse como Crédito Fiscal" esa leyenda no va!!!.</p> <p>Adjunto la factura emitida</p> <p>saludos!</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31905" alt="lXxIeLcTSmLnU2Bl-20260526-140947.png" height="675" width="1263" style="border: 0px solid black" /></span></p> <p>NICOLAI Patricia<br/> &#8212;<br/> <font color="#ff991f">Ceci, Patricia dice no ver los cambios, y nos pasa la captura de la FC donde ya no se ve la leyenda que eliminaste. Asi que parece ser que se refiere a como esta mostrando los totales de iva. Queres verlo? gracias.</font><br/> &#8212;</p>

#### REC relacionados
- REC-3278

#### Commits asociados

- 7b7cd53752 - 2026-06-08 18:08:54 - CECILIA-RICCI
  Mensaje: SIS-5220 Mofique este SP para que las nuevas condiciones de iva, 'RSP', 'MS', 'MTI' funcionen igual que 'I', 'M', 'S'
  Stats: +4 | -4 | 8 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_RPT_COMPROBANTES_Comprobantes_TotalesFactura.sql - modified | +4 | -4 | 8 cambios

### SIS-5221 - Ajustar backend edición (sacar procesadores)

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- Descripcion: <p>Simplificar el alta del elementos sacando AddProcessosIF. Ahora el endpoint de alta, llama directamente al stored procedure.</p>

#### Commits asociados

- f9dd4960f7 - 2026-06-05 11:48:13 - Marcos Rossi
  Mensaje: SIS-5221
  Stats: +12 | -59 | 71 cambios | 5 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/GisMngr.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/AddElementAPICommand.java - modified | +7 | -19 | 26 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/add/AddProcessorIF.java - removed | +0 | -12 | 12 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/add/AddZonaInteresAP.java - removed | +0 | -25 | 25 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/dao/DaoDB.java - modified | +3 | -1 | 4 cambios

- e22b6b3e45 - 2026-06-09 17:35:57 - Marcos Rossi
  Mensaje: SIS-5221
  Stats: +3 | -1 | 4 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/api/PasarProyectoAMaestroAPICommand.java - modified | +3 | -1 | 4 cambios

### SIS-5222 - Implementar endpoints para 2 y 5

#### Jira
- Estado: En curso
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- Descripcion: <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31939" alt="1000156023.jpeg" width="539" style="border: 0px solid black" /></span></p> <p>Los pasos de alta de un elementos son:</p> <ol> <li>Apretar +</li> <li><b>Recuperar categorías aplicables, tipos y representaciones posibles (dado el elemento de partida, que puede ser null)</b></li> <li>Dibujar (punto, linea, poligono, etc)</li> <li>Abrir diálogo de edición según el tipo de elemento</li> <li><b>Obtener configuración para editor</b></li> <li>Realizar edición</li> <li>Parar la llamada al backend</li> <li>Dibujar lo que indica el backend</li> </ol>

#### Commits asociados

- 7a84c257c8 - 2026-06-05 14:33:52 - Marcos Rossi
  Mensaje: SIS-5222: Inicio de APIs
  Stats: +208 | -0 | 208 cambios | 7 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/api/GetConfiguracionEditorAPICommand.java - added | +36 | -0 | 36 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/GetOpcionesAltaAPICommand.java - added | +38 | -0 | 38 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/ConfiguracionEditorDTO.java - added | +6 | -0 | 6 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/OpcionCategoriaDTO.java - added | +41 | -0 | 41 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/OpcionTipoElementoDTO.java - added | +41 | -0 | 41 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/OpcionVarianteTipoElementoDTO.java - added | +28 | -0 | 28 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/OpcionesAltaDTO.java - added | +18 | -0 | 18 cambios

### SIS-5228 - Implementar endpoints de proyectos

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- Descripcion: <p>Implementar API commands para crear, actualizar, recuperar y pasar a maestro.</p>

#### Commits asociados

- 9b6dbfd02c - 2026-06-09 17:24:38 - Marcos Rossi
  Mensaje: SIS-5228
  Stats: +418 | -0 | 418 cambios | 8 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/GisMngr.java - modified | +21 | -0 | 21 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/AddProyectoAPICommand.java - added | +33 | -0 | 33 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/GetProyectosAPICommand.java - added | +37 | -0 | 37 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/PasarProyectoAMaestroAPICommand.java - added | +29 | -0 | 29 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/UpdateProyectoAPICommand.java - added | +37 | -0 | 37 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/bo/Proyecto.java - added | +54 | -0 | 54 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/bp/BPEstadoProyecto.java - added | +8 | -0 | 8 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/dao/DaoDB.java - modified | +199 | -0 | 199 cambios

- 57071d07f9 - 2026-06-09 17:29:31 - Marcos Rossi
  Mensaje: SIS-5228
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/gis/api/UpdateProyectoAPICommand.java - modified | +2 | -2 | 4 cambios

### SIS-5230 - anulacion de lotes de MP

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: BEJERMAN, FINANZAS
- SIS relacionados: SIS-5203
- REC: REC-3316
- Descripcion: <p>RECLAMO: REC-3316<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5203" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5203" class="jira-issue-macro-key issue-link" title="anulacion de lotes de MP" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5203 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Buen dia los dias 20/04 y 23/04 del corriente se anularon dos lotes de mercado pago que ingresados en la misma fecha. al generar los archivos para informarlo a bejerman, el archivo de asientos lo informo bien, pero en el archivo de finanzas en vez de generar un egreso genero otro ingreso. habria que ajustar ese parametro pero necesitamos nos indiquen como hacerlo, No recordamos si es algo que setean uds ya que no es algo que no sucede a menudo y luego del hackeo, es la primera anulacion de mercado pago que lo hacemos por ello es que no se detecto antes este tipo de eventos.</p> <p>quedamos a la espera<br/> &#8212;<br/> <font color="#ff991f">Reabierto luego del Meet con Cotecal. </font><br/> &#8212;</p>

#### REC relacionados
- REC-3316

#### Commits asociados

- b3aa22b94c - 2026-06-08 11:44:15 - ignacio.hahn
  Mensaje: SIS-5230 No se deben registrar movimientos negativos para evitar que se registren ID
  Stats: +11 | -0 | 11 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ImportarMercadoPagoPos_FIJO.sql - modified | +11 | -0 | 11 cambios

### SIS-5235 - Mapas Tematicos - Filtros 

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Matias Garofalo
- REC: REC-3335
- Descripcion: <p>RECLAMO: REC-3335<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> 1- El filtro de Etapa que sea un selector y no texto libre</p> <p>2- Analizar si se puede presetear la Localidad en base a la seleccionada en la capa <br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3335

#### Commits asociados

- 3d3326161a - 2026-06-09 17:07:39 - matias.garofalo
  Mensaje: SIS-5235 Se agrega un selector para filtrar por tipo de etapa en las instalaciones y reclamos pendientes desde jsatelite
  Stats: +29 | -5 | 34 cambios | 2 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_MAP_TramitesPendientes.sql - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/gis/api/dto/TematicoParametroDTO.java - modified | +27 | -3 | 30 cambios

### SIS-5249 - Modificar Listado RTXTSER

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- SIS relacionados: SIS-5094
- REC: REC-3168
- Descripcion: <p>RECLAMO: REC-3168<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5094" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5094" class="jira-issue-macro-key issue-link" title="Modificar Listado RTXTSER" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5094 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Hola, buen día.</p> <p>En Menú Técnica → Listados esta el siguiente: <b>RTXTSER Recursos técnicos por tipo de servicio (completo)</b></p> <p>Se solicita que agreguen/reemplacen por nuestro recursos técnicos</p> <ol> <li>Tarjeta/decodificador (de los casados)</li> </ol> <ol> <li>Mininodo</li> </ol> <ol> <li>DPC (drop preconectorizado)</li> </ol> <ol> <li>modulo de telefonia</li> </ol> <ol> <li>AP Mesh</li> </ol> <p>Los pueden reemplazar por cualquier de estas columnas</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32112" alt="imagen-20260429-130235.png" height="70" width="297" style="border: 0px solid black" /></span></p> <p>Desde ya muchas gracias.<br/> Saludos.<br/> MUCH, Pablo.<br/> &#8212;<br/> <font color="#ff991f"><b>MATE: REABIERTO POR EL CLIENTE (Si no ves bien las img me avisas) Majo.-</b> </font></p> <p>Respecto a este listado, ahora pareciera que los trae a los recursos pero no puedo esta seguro porque ahora no me trae la columna de los servici...

#### REC relacionados
- REC-3168

#### Commits asociados

- 08f014164b - 2026-06-10 18:27:30 - mateo-soto
  Mensaje: SIS-SIS-5249 Correcciones en el listado
  Stats: +64 | -48 | 112 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_TEC_RT_SERVICIOS.sql - modified | +64 | -48 | 112 cambios

### SIS-5250 - MIGRACION DE TELEFONIA

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Matias Garofalo
- REC: REC-3340
- Descripcion: <p>RECLAMO: REC-3340<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Segun lo hablado con Matias</p> <p>Cuando se migra una linea Telefonica en cobre a Sip, se genera el siguiente proceso:</p> <p> </p> <p>I- Con linea de cobre en la EWSD</p> <p> </p> <p>1.- Se genera una transaccion donde se crea el usuario sip y su contraseña en el jsat.<br/> 2.- Se envia esa transaccion al SSW.<br/> 3.- Cuando se Cierra la orden de instalacion, se genera una Nueva transaccion, donde se elimina la linea Telefonica de la central EWSD y se crean los puntos de codigo.<br/> 4.- Se envia esa transaccion, a la central EWSD.</p> <p> </p> <p> </p> <p>II- Con linea de cobre en el SSW</p> <p> </p> <p>1.- Se genera una transacción donde se crea el usuario sip y su contraseña en el jsat.<br/> 2.- Se envía esa transacción al SSW.<br/> 3.- Cuando se Cierra la orden de instalación, se genera una Nueva transacción, donde se elimina la línea Telefónica(cobre) de el SSW y se crean una línea sip con diferente contraseña en el SSW.<br/> 4.- Se envía esa transacción, al SSW.</p> <p>una línea que se instaló recientemente 4934295, </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32115" alt="image-20260608-160821.png" height="327" width="1283" style="border: 0px solid black" /></span></p> <p>Saludos.</p> <p>&#8212;<br/> otro ejemplo: 4934679 antes de cerrar la instalación: </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32117" alt="image-20260608-162351.png" width="50%...

#### REC relacionados
- REC-3340

#### Commits asociados

- c75b945b70 - 2026-06-11 15:01:32 - matias.garofalo
  Mensaje: SIS-5250 En el doTraducirAltaServicio no tendria que hacer xServicio.getPassword().getValue().startsWith(vIdentificador) al momento de determinar si debe reutilizar el pwd. Ademas le agregue que si esta cambiando de tegnologia no le ponga el password 6722 sino el identificador original.
  Stats: +9 | -1 | 10 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/ConectorSoftSwitchIntegratech.java - modified | +9 | -1 | 10 cambios

### SIS-5259 - Ajustes build de hotfix

#### Jira
- Estado: EN ESPERA
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- Etiquetas: PROXIMA_VERSION
- Descripcion: <p>Ajustar los WF de github actions para evitar que un push en el branch hotfix haga el build (reemplazando la versión de producción de las imágenes de docker de JSAT)</p> <p>Pretendemos que este reemplazo SOLO ocurra una vez FINALIZADO el hotfix explicitamente.</p>

#### Commits asociados

- e451b23286 - 2026-06-10 14:15:24 - Marcos Rossi
  Mensaje: SIS-5259
  Stats: +134 | -2 | 136 cambios | 3 archivos
##### Archivos modificados
- .github/workflows/on_close_pr_hotfix.yml - renamed | +1 | -1 | 2 cambios
- .github/workflows/on_open_pr_hotfix.yml - added | +132 | -0 | 132 cambios
- .github/workflows/on_push_hotfix.yml - modified | +1 | -1 | 2 cambios

### SIS-5275 - Tramites Calculo Promedio Dias en Finalizar Semanal

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: CONSULTA_DIRECTA
- SIS relacionados: SIS-5194, SIS-5195
- REC: REC-3312
- Descripcion: <p>RECLAMO: REC-3312<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5194" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5194" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5194 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> , <span class="jira-issue-macro resolved" data-jira-key="SIS-5195" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5195" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5195 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Necesitaría por favor saber en qué etapa se encuentran los trámites pendientes (podría agregarse cuando elijo la opción de información detallada).<br/> Gracias!<br/> &#8212;<br/> Hola! Sigo viendo diferencia entre la cantidad de trámites finalizados que figura cuando elijo la opción sin detalle, y la cantidad de cerrados cuando pongo con detalles. </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32336" alt="image-20260612-135949.png"...

#### REC relacionados
- REC-3312

#### Commits asociados

- 7ce245d9f9 - 2026-06-12 14:46:26 - Martina
  Mensaje: SIS-5275 - Correccion listado Calculo Promedio Dias Se corrigió el calculo de los Tramite Finalizados en la vista no detallada. Segun lo solicitado en el REC-3312
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_TEC_PromedioDiasFinalizarTramiteSemanal.sql - modified | +2 | -2 | 4 cambios

### SIS-5279 - Factura de Mayo con ticket facturado de Junio

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3385
- Descripcion: <p>RECLAMO: REC-3385<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Tenemos un caso raro de una clienta a la cual se le facturó, en la FC de Mayo, un ticket de Junio … es raro porque revisando los lotes tenemos las fechas delimitadas desde el 1/5 a las 00:00:00 hasta el 31/5 a las 23:59:59, no se cómo se puede haber colado ese ticket</p> <p>Como dato, a esa clienta se le reconectó el mismo 1/6 y ese dia tuvimmos que regenerar los lotes a las 15:00 aprox … es decir, se desarmó el lote en Generado para volver a generarlo todo desde el JOB</p> <p>Adjunto la FC</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32465" alt="image-20260616-152926.png" height="361" width="1886" style="border: 0px solid black" /></span></p> <p>&#8212;<br/> <a href="mailto:danasamu2014@hotmail.com" class="external-link" rel="nofollow noreferrer">danasamu2014@hotmail.com</a> <font color="#ff991f">es el identificador del caso que nos pasan.</font></p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32464" alt="image-20260616-160849 (1).png" width="665" style="border: 0px solid black" /></span><br/> &#8212;</p>

#### REC relacionados
- REC-3385

#### Commits asociados

- d8041779b8 - 2026-06-17 12:51:16 - CECILIA-RICCI
  Mensaje: SIS-5279 Paso que a un servicio, que estaba dado de baja al 31/5, lo habilitaron el 01/06 y al facturar le facturo los tickets del 01/06 que no corresponden. Hice un cambio para que tome el estado actual si es activo o alta, sino que tome el estado a la fecha hasta del lote.
  Stats: +8 | -4 | 12 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_COMPROBANTES_LoteGenerarTickets.sql - modified | +8 | -4 | 12 cambios

### SIS-5281 - Generar parámetros en specs de compra

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Mateo Soto
- Descripcion: <p>Ajustar el UC de specs de parámetros de compra para que incluya:</p> <p>PARÁMETROS dentro de su estructura con formato:</p> <p>*@</p> {NOMBRE_VARIABLE; Label; TIPO; CONFIG} <p>*</p> <p>Donde <b>TIPO</b> puede ser:</p> <ul> <li>STRING</li> <li>MONEDA</li> <li>NUMERO</li> <li>FECHA</li> <li>FECHA_HORA</li> <li>SELECTOR</li> </ul> <p>Y <b>CONFIG</b> puede incluir parámetros del estilo “opciones de un selector”</p> <p>Por ejemplo:</p> <p>@{<br/> FORMA_PAGO;<br/> Forma de pago;<br/> SELECTOR;<br/> [</p> {id: '1', 'Cambio de producto'} <p>, </p> {id: '2', 'Cambio de sas'} <p>]<br/> }</p> <p>Notar que en los parámetros de SELECTOR, se devuelve un array con objetos con id y descripcion.</p>

#### Commits asociados

- 9a4b95328e - 2026-06-17 18:06:17 - mateo-soto
  Mensaje: SIS-5281 generador de specs para OVT
  Stats: +518 | -3 | 521 cambios | 4 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/comercial/api/GetParametrosVentaCommand2.java - added | +495 | -0 | 495 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/dto/DatosTramiteDTO.java - modified | +2 | -2 | 4 cambios
- src/JSAT/project/src/com/telpin/jsat/comercial/api/dto/DireccionInstalacionDTO.java - modified | +1 | -1 | 2 cambios
- tools/bruno/api-telpin/testing/comercial/buscar/buscar-parametros-vender/buscar-parametros-vender-OVT.bru - added | +20 | -0 | 20 cambios

### SIS-5284 - Tramites Calculo Promedio Dias en Finalizar Semanal

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: CONSULTA_DIRECTA
- SIS relacionados: SIS-5194, SIS-5195, SIS-5275
- REC: REC-3312
- Descripcion: <p>RECLAMO: REC-3312<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5194" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5194" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5194 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> , <span class="jira-issue-macro resolved" data-jira-key="SIS-5195" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5195" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5195 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> , <span class="jira-issue-macro resolved" data-jira-key="SIS-5275" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5275" class="jira-issue-macro-key issue-link" title="Tramites Calculo Promedio Dias en Finalizar Semanal" > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5275 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Nec...

#### REC relacionados
- REC-3312

#### Commits asociados

- f7aafcec61 - 2026-06-17 13:46:42 - CECILIA-RICCI
  Mensaje: SIS-5284 Modifique para que la cantidad de pendientes solo tome los de fecha fin en null, para que den las cuentas de cantidad pendientes + cantidad finalizados es igual a la cantidad de tramites.
  Stats: +1 | -1 | 2 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_LST_TEC_PromedioDiasFinalizarTramiteSemanal.sql - modified | +1 | -1 | 2 cambios

### SIS-5287 - CPE - Acreditación automática de Macro Click Pagos.

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- SIS relacionados: SIS-5190
- REC: REC-3309
- Descripcion: <p>RECLAMO: REC-3309<br/> &#8212;<br/> SIS previos:</p> <p> <span class="jira-issue-macro resolved" data-jira-key="SIS-5190" > <a href="https://telpinsistemas.atlassian.net/browse/SIS-5190" class="jira-issue-macro-key issue-link" title="CPE - Acreditación automática de Macro Click Pagos." > <img class="icon" src="https://telpinsistemas.atlassian.net/rest/api/2/universal_avatar/view/type/issuetype/avatar/10304?size=medium" /> SIS-5190 </a> <span class="aui-lozenge aui-lozenge-subtle aui-lozenge-success jira-macro-single-issue-export-pdf">Done</span> </span> </p> <p>&#8212;<br/> Hola buen día.<br/> Se me solicita que abra el siguiente requerimiento.<br/> Debido a la reunión mantenida en el día de hoy entre Mariela Coran, Manuel Beneitez, Iara Arcuri y Gaston Jorge; se solicita la acreditación automática de pagos Macro Click.<br/> Saludos. Muchas gracias.<br/> MUCH, Pablo.<br/> &#8212;<br/> <span class="nobr"><a href="/rest/api/3/attachment/content/32500" title="Diferencias macro click (ad1cc11f-9617-4774-ae92-be4ab87a6119).xlsx attached to SIS-5287" data-attachment-type="file" data-attachment-name="Diferencias macro click (ad1cc11f-9617-4774-ae92-be4ab87a6119).xlsx" data-media-services-type="file" data-media-services-id="2eefc692-9761-4675-b09d-562c0ebdfbd8" rel="noreferrer">Diferencias macro click (ad1cc11f-9617-4774-ae92-be4ab87a6119).xlsx<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span></p> <p>&#8212;</p>

#### REC relacionados
- REC-3309

#### Commits asociados

- 35d3aafedc - 2026-06-18 14:31:39 - ignacio.hahn
  Mensaje: SIS-5287 Cambio interno, ahora la finalizacion de avisos de pago va a chequear los IC que se registran automaticamente luego de las notificaciones automaticas. Ej. Plus Pagos y Fiserv
  Stats: +2 | -2 | 4 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_TRAMITE_AvisoPagoFinalizar.sql - modified | +2 | -2 | 4 cambios

- 0905d1c1f8 - 2026-06-23 19:30:42 - ignacio.hahn
  Mensaje: SIS-5287 CPE - Importacion de archivos de cobranzas desde Macro Click Pagos <H3> CPE - Importacion de archivos de cobranzas desde Macro Click Pagos</h3> El proceso de importación de archivos de cobranzas verificará que los pagos informados por Macro Click no se encuentren previamente registrados de manera automática en la cuenta del cliente. Los pagos que ya hayan sido registrados serán descartados durante la importación. REC-3309
  Stats: +28 | -0 | 28 cambios | 1 archivos
##### Archivos modificados
- BD/StoredProcedures/SP_EE_ImportarDebitosPlusPagosPos_Fijo.sql - modified | +28 | -0 | 28 cambios

### SIS-5291 - Error al despachar Tramites

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Marcos Rossi
- REC: REC-3393
- Descripcion: <p>RECLAMO: REC-3393<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Claudio Teruggi nos reporta por chat que le da error al Despachar Tramites.</p> <p>org.hibernate.exception.SQLGrammarException: could not load an entity: <a href="#45723" rel="noreferrer">com.telpin.arenero.tramite.bo.AgendaTurnosOcupacion#45723</a></p> <p>Tb comenta que le pasa con otros tramites, no es solamente el caso que nos muestra.</p> <p>TRAMITE NRO 1205541</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32580" alt="image (66).png" width="673" style="border: 0px solid black" /></span></p> <p>(Reclamo cargado por JSAT desde el Soporte)<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3393

#### Commits asociados

- 2aea0258fc - 2026-06-18 13:18:05 - Marcos Rossi
  Mensaje: SIS-5291
  Stats: +2 | -0 | 2 cambios | 2 archivos
##### Archivos modificados
- .github/workflows/on_close_pr_hotfix.yml - modified | +1 | -0 | 1 cambios
- .github/workflows/on_open_pr_hotfix.yml - modified | +1 | -0 | 1 cambios

### SIS-5314 - Cambio de IPTV a SENSA

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: VERSION.1.2.28
- REC: REC-3417
- Descripcion: <p>RECLAMO: REC-3417<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hay problemas cuando realizan el cambio de producto desde Jsat de IPTV a Sensa Box, no esta impactando en la plataforma de Minerva Nube y a los abonados no les funciona en dispositivos mobiles.</p> <p>En los siguientes abonados este PACK faltante se les agrego a mano para poder brindar el servicio.</p> <p>105580</p> <p>104133</p> <p>&#8212;<br/> <font color="#ff991f">Ce, lo que pude ver de estos dos casos, es que tienen una Transaccion Rechazada.</font></p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/32783" alt="image-20260623-113529.png" width="665" style="border: 0px solid black" /></span><br/> &#8212;</p>

#### REC relacionados
- REC-3417

#### Commits asociados

- 53bbf5cb5c - 2026-06-23 18:45:50 - cericci
  Mensaje: SIS-5314 Con la ayuda de Mati, hice un cambio para que no dé de alta el servicio en la nube cuando se vende el subservicio Mobile, sino que solo da de alta el paquete. REC-3417
  Stats: +0 | -7 | 7 cambios | 1 archivos
##### Archivos modificados
- src/JSAT/project/src/com/telpin/jsat/tecnica/bo/ConectorPlataformaIPTVMinerva10.java - modified | +0 | -7 | 7 cambios

### SIS-3795 - Implementar API de callback de aceptación de turno en JSAT

#### Jira
- Estado: Finalizada
- Tipo: Tarea
- Prioridad: Medium
- Responsable: Marcos Rossi
- SIS relacionados: SIS-3862
- Descripcion: <p>Se debe implementar un API command que se encargue de “confirmar” el turno de un trámite</p> <p>La clase se debe llamar CallbackTramiteAPICommand y será invocada desde una acción de código? vía Botmaker.</p> <p>Básicamente tiene que hacer un “nextStep” del trámite especificado.</p>

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-4269 - Implementar Tramite Tarea Preventiva Masiva

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Mariela Coran
- Etiquetas: VERSION.1.2.26
- REC: REC-2375
- Descripcion: <p>RECLAMO: REC-2375<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Se desea implementar un nuevo tipo de tramite Tarea Preventiva Masiva ( similar al Incidente Masivo) pero que permita gestionar tareas preventivas que se realizan sobre la red o los servicios.</p> <p>La idea es que el tramite se registre y se indique el/los RT tecnicos afectados y su workflow contenga al menos una etapa donde se envia notificacion masiva a los servicios afectados ( usando una plantilla ) y que el tramite se suspenda hasta que exista una etapa de “Inicio de Tarea Preventiva”donde el jsat etiquetara los servicios afectados en ese momento. </p> <p>Una vez que la Tarea Preventiva es finalizada deberia avanzar en el WF para que desetiquete a todos los servicios y se les notifique que se finalizó <img class="emoticon" src="/images/icons/emoticons/help_16.png" height="16" width="16" align="absmiddle" alt="" border="0"/></p> <p>Vamos avanzando con la definicion de este WF.</p> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-2375

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-4724 - reporte totales de facturación - cantidad de facturas a imprimir

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- REC: REC-2830
- Descripcion: <p>RECLAMO: REC-2830<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> En cada proceso de facturación sacamos desde el lote a facturar , el reporte totales de facturación . </p> <p>En éste caso facturamos el 1/2/26 los lotes 72408 y 77169 , en la cantidad de comprobantes a imprimir , ahora tenemos 747 piezas más que el mes pasado.</p> <p>Ahora que ya está cerrado , puedo listar los comprobantes para oca y veo que en lote mensual tengo 67 comprobantes para imprimir y en el del área extendida … 124</p> <p>Podrán verificar por favor ?</p> <p>gracias</p> <p><span class="nobr"><a href="/rest/api/3/attachment/content/25254" title="totales facturacion 77169.xls attached to SIS-4724" data-attachment-type="file" data-attachment-name="totales facturacion 77169.xls" data-media-services-type="file" data-media-services-id="b7f10d53-cf08-4dc4-ba88-f34a47f6da37" rel="noreferrer">totales facturacion 77169.xls<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span><br/> <span class="nobr"><a href="/rest/api/3/attachment/content/25255" title="total facturación 72408.xls attached to SIS-4724" data-attachment-type="file" data-attachment-name="total facturación 72408.xls" data-media-services-type="file" data-media-services-id="677a244e-e448-4284-8535-cb926b11426c" rel="noreferrer">total facturación 72408.xls<sup><img class="rendericon" src="/images/icons/link_attachment_7.gif" height="7" width="7" align="absmiddle" alt="" border="0"/></sup></a></span></p> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-2830

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-4820 - Agregar Link de pago CETEVENTOS a cobranzas automaticas

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Mariela Coran
- REC: REC-2926
- Descripcion: <p>RECLAMO: REC-2926<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola Colo, agregue un link de pago CETEVENTOS como el de fichaje para el CET para que ahi puedan ingresar cobranzas de eventos, y le vamos modificando el monto. Seria como el del Fichaje que creamos.</p> <p>Te paso el link y codigo, vos podes hacer que eso se procese?</p> <p><tt><a href="https://mpago.la/1gqB9qu" class="external-link" rel="nofollow noreferrer">https://mpago.la/1gqB9qu</a></tt></p> <p>CETEVENTOS</p> <p>Gracias</p> <p>&#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-2926

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-4889 - Primeras pruebas de endpoints

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Marcos Rossi
- REC: REC-2994
- Descripcion: <p>RECLAMO: REC-2994<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buenas, estuve haciendo las primeras pruebas de los endpoints en el servidor de prueba y pude detectar lo siguiente:</p> <p>1 - Session login → Prueba OK (se pudo loguear con mi usuario 369 y se obtiene un sid)</p> <p>2 - GET Persona → Se consulta mediante un DNI existente y un tipo de documento existente y devuelve los datos OK. En otros casos responde no encontrado. Prueba OK</p> <p>3 - POST crear persona física → Se utiliza Postman para probar un POST a este endpoint. Se usa el body de ejemplo (tal cual) de Swagger para probar antes de personalizarlo con datos propios. Se agrega un Header con el sid obtenido del endpoint Session Login (logueandome con el usuario 369)</p> <p>El endpoint devuelve el mensaje de error:.</p> <div class="preformatted panel" style="border-width: 1px;"><div class="preformattedContent panelContent"> <pre>{ "status": "ERROR", "statusMessage": "java.lang.IllegalStateException: Expected BEGIN_ARRAY but was STRING", "result": null }</pre> </div></div> <p>El body de la request es:</p> <div class="preformatted panel" style="border-width: 1px;"><div class="preformattedContent panelContent"> <pre>{ "persona": { "nombre": "Juan", "apellido": "Pérez", "fechaNacimiento": "15/04/1985", "nacionalidad": "Argentina", "tipoDocumento": "D", "numeroDocumento": "12345678", "sexo": "M", "cuil": "20123456783" }, "datosContacto": { "email": "pepe@telpin.com.ar", "telefono": "2254484849", "whatsapp": "5492254626262", "calle": "Jason", "numero": "133", "codigoPostal": "7167", "edificio": "Edif. C...

#### REC relacionados
- REC-2994

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-4917 - Reclamos - Problemas en los Cambio de Etapas del WK del mismo nivel

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Martina Virgilli
- REC: REC-3022
- Descripcion: <p>RECLAMO: REC-3022<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola, buen día.<br/> Luciano plantea lo siguiente:<br/> Al momento de que una cuadrilla de "reclamos propia" cambia de etapa un trabajo cuadrilla domicilio a Trabajo Plantel Exterior (ticket), JSAT en vez de mantener abierto el reclamo, lo finaliza y genera el trámite a Plantel Exterior (ticket). Esto hace que automáticamente le llegue al usuario una notificación de que su trámite (reclamo) a sido finalizado, y no es así, normalmente hasta que Plantel Exterior no realiza sus tareas de reparación (ticket) no queda normalizado el servicio del usuario; es más, en ocasiones la cuadrilla de reclamos tiene que volver al domicilio luego de que Plantel Exterior finaliza el ticket correspondiente. <br/> En definitiva ver la manera de que el reclamo siga abierto y la notificación de finalización y cierre del mismo (reclamo) no le llegue al usuario hasta tanto este se finalice completamente; o no generarse un nuevo reclamo al pasar a TRABAJO PLANTEL EXTERIOR.- <br/> Esto corre para todos los tramites que implica trabajo domicilio cuadrilla ya sea reclamo o asistencia e independientemente del servicio (internet, telefonía, televisión) y siempre acotado a nuestras cuadrillas.-</p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/28382" alt="imagen-20260319-181820.png" height="413" width="502" style="border: 0px solid black" /></span></p> <p>Ejemplo de lo que sucede hay varios, cliente: 24544-LOPEZ, ENRIQUE ALBERTO.<br/> Reclamo: 62560, luego se cier...

#### REC relacionados
- REC-3022

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-5093 - cambio en COMAST - Asistencia Comercial	

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Ignacio Hahn
- Etiquetas: VERSION.1.2.27
- REC: REC-3148
- Descripcion: <p>RECLAMO: REC-3148<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Hola chicos! como va? </p> <p>Quiero pedirles un cambio en la asistencia comercial y ustedes me cuentan si es posible. </p> <p>Actualmente escribimos una asistencia comercial la finalizamos y vamos por fuera a “enviar constancia para el cliente” y se la mandamos por mail. </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30421" alt="image-20260423-145834.png" height="248" width="1503" style="border: 0px solid black" /></span></p> <p>Lo que me gustaría es poder enviarlo por mail desde la misma asistencia, para ahorra un paso. </p> <p>Las pantallas actuales son estas: </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30419" alt="image-20260423-145919.png" height="425" width="1002" style="border: 0px solid black" /></span></p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30420" alt="image-20260423-145938.png" height="559" width="1372" style="border: 0px solid black" /></span></p> <p>En este segundo paso, podemos agregar “finalizar y enviar constancia al cliente” ? </p> <p>Otra opción sería que nos de la opción por fuera, como lo hacen las ventas o gestiones de servicios, asi: </p> <p><span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/30422" alt="image-20260423-150135.png" height="360" width="644" style="border: 0px solid black" /></span></p>...

#### REC relacionados
- REC-3148

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-5177 - Falla en almacenamiento donde se aloja la BD MASTER de JSAT y dificultad para recuperar los backups diferenciales para recuperar la informacion

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- REC: REC-3289
- Descripcion: <p>RECLAMO: REC-3289<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Se detectó una falla en las unidades de disco correspondientes a las bases de datos históricas y archivos LOG del servidor JSAT BD MASTER.</p> <p>Actualmente, el servidor presenta un comportamiento inestable y no existen garantías operativas de funcionamiento normal sostenido. Por este motivo, y con asistencia de TELPIN, se decidió poner en servicio el servidor BD SLAVE utilizando los backups disponibles.</p> <p>TELPIN se encuentra analizando la posibilidad de restaurar los backups diferenciales para completar la actualización de la base de datos.</p> <p>En caso de no resultar viable la recuperación completa mediante diferenciales, se procederá a levantar el servicio utilizando únicamente el backup full disponible, lo que permitiría restablecer la operatividad de JSAT con información consistente hasta las 04:00 hs del día de hoy.</p> <p>Les pedimos por favor si nos pueden asistir en el análisis de alternativas para intentar recuperar la totalidad de la información generada durante el día de hoy.</p> <p>Quedamos atentos a cualquier requerimiento técnico o información adicional que necesiten para avanzar con las tareas de recuperación.<br/> &#8212;</p> <p>&#8212;</p>

#### REC relacionados
- REC-3289

#### Commits asociados

- Sin commits asociados en este segmento.

### SIS-5203 - anulacion de lotes de MP

#### Jira
- Estado: Finalizada
- Tipo: Requerimiento
- Prioridad: Medium
- Responsable: Cecilia Ricci
- Etiquetas: BEJERMAN, FINANZAS
- REC: REC-3316
- Descripcion: <p>RECLAMO: REC-3316<br/> &#8212;<br/> SIS previos:</p> <p>&#8212;<br/> Buen dia los dias 20/04 y 23/04 del corriente se anularon dos lotes de mercado pago que ingresados en la misma fecha. al generar los archivos para informarlo a bejerman, el archivo de asientos lo informo bien, pero en el archivo de finanzas en vez de generar un egreso genero otro ingreso. habria que ajustar ese parametro pero necesitamos nos indiquen como hacerlo, No recordamos si es algo que setean uds ya que no es algo que no sucede a menudo y luego del hackeo, es la primera anulacion de mercado pago que lo hacemos por ello es que no se detecto antes este tipo de eventos.</p> <p>quedamos a la espera<br/> &#8212;<br/> <span class="image-wrap" style=""><img src="https://telpinsistemas.atlassian.net/rest/api/3/attachment/content/31762" alt="image-20260602-131850.png" height="284" width="1011" style="border: 0px solid black" /></span></p> <p>&#8212;</p>

#### REC relacionados
- REC-3316

#### Commits asociados

- Sin commits asociados en este segmento.

## Commits sin SIS
- b91cc4140a: Le hice un cambio para que no de error cuandp no esta linkeado el server Bejerman.
- c13113c11f: Correcciones API
- 749a5da07f: Correcciones Importador API
- a85a0a9715: Actualizar el monto del lote de cobranzas al momento de cerrarlo
- 4a6081f482: Parametrizacion de codigo de entidad de cobranzas FISERV
- bced169a30: fix: SP detalle de especificacion de cobranzas
- 432d4cd7a8: Modifique para que se pueda tomar el resultado e informarlo en un mail desde el JOB BCKP - Restore JsatTesting que se ejecuta en expluto\jsat
- b2fd1753cf: fix: mejora en listado de status de envio de mails de un lote de facturacion descartamos los casos de usuarios de oficina virtual y medios de contacto creados posteriormente al envio masivo de facturas por mail.
- 7060a48dec: Pruebas de API JSC
- 75378358fd: hago un convert a nvarchar del icono porque la Ñ generaba errores en el api command
- cecbaccda5: Correxion permisos Grant y nombre archivo Se corrigió el nombre del SP LST_TEC_PromedioDiasFinalizarTramiteSemanal y los permisos GRANT Execute
- 56971954d9: Solicitan del jsatelite que ciertas etapas no esten incluidas en los tematicos
- 48686333fa: Me habia quedado del commit anterior que no necesitara session
- 74e74c7c7e: Ajuste conector botmaker
- e141dc669b: Estrategias para dispatcher ftth
- 43a68c1627: /
- c7dd8d9fa8: Ajustes JSAT Elite
- da6e123f21: Cambie para que asigne el permiso al usuario cpeM3 si es que existe el usuario
- 0e70f9d199: Estaba dando error al grabar los tramites que no tienen FechaFinEsperada al setear mFechaFinEsperadaStr
- facbaa830d: TEST 0148 - Validacion de grilla y notificacion de test sin casos para prueba
- 514eba1aa1: TEST 0149 - Validacion de grilla y notificacion de test sin casos para prueba
- e65eeb0760: TEST 0152 - Validacion de grilla y notificacion de test sin casos para prueba

## SIS sin REC
- SIS-2125
- SIS-5120
- SIS-5125
- SIS-5132
- SIS-5164
- SIS-5221
- SIS-5222
- SIS-5228
- SIS-5259
- SIS-5281
- SIS-3795