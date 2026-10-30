# MicoPay Factoring

Propuesta para desarrollar infraestructura de factoraje digital en México combinando verificación de CFDI, evaluación de riesgo fuera de cadena, originación de crédito sobre XRP Ledger y liquidación en MXN mediante la infraestructura de MicoPay.

> Estado: investigación y diseño conceptual. Este repositorio todavía no contiene una implementación funcional, un producto financiero disponible ni una oferta de inversión.

## Problema

Muchas PyMEs mexicanas venden a crédito y reciben el pago de sus facturas después de 60, 90 o más días. El factoraje permite anticipar una parte del valor de esas cuentas por cobrar para financiar la operación diaria.

México ofrece una base interesante para automatizar este proceso porque el CFDI permite validar datos fiscales y comerciales de una factura. Sin embargo, un CFDI no demuestra por sí mismo que el derecho de cobro sea válido, que la mercancía haya sido entregada, que el deudor acepte la obligación o que la factura no haya sido financiada previamente.

## Propuesta

```text
CFDI y documentos comerciales
            │
            ▼
Validación fiscal y verificación del derecho de cobro
            │
            ▼
Underwriting de emisor, deudor y operación
            │
            ▼
Cesión jurídica y prevención de doble financiamiento
            │
            ▼
Originación y liquidez en XRPL
            │
            ▼
Dispersión, cobranza y liquidación en MXN mediante MicoPay
```

La investigación inicial propone utilizar:

- **CFDI y SAT:** validación fiscal de las facturas.
- **XRP Ledger:** representación del activo, bóvedas de liquidez y originación del financiamiento.
- **XLS-65:** bóvedas de un solo activo para agrupar liquidez.
- **XLS-66:** préstamos de plazo fijo con evaluación crediticia fuera de cadena.
- **MicoPay y Stellar:** identidad, wallets, contabilidad, conciliación y entrada o salida de valor en MXN.

El estado actual de XLS-65 y XLS-66 debe verificarse nuevamente antes de iniciar una implementación. El reporte incluido refleja la información disponible en julio de 2026.

## Flujo propuesto

1. La PyME presenta el CFDI y la evidencia comercial asociada.
2. La plataforma valida el comprobante y comprueba que no esté cancelado.
3. El sistema verifica al emisor, al deudor, la entrega y el derecho de cobro.
4. El motor de riesgo calcula monto financiable, descuento, plazo y reservas de pérdida.
5. Las partes formalizan la cesión del derecho de cobro.
6. El financiamiento se origina y se entrega a la PyME.
7. El pago del deudor se concilia contra la obligación correspondiente.
8. El sistema distribuye principal, rendimiento, comisiones y pérdidas conforme a las reglas acordadas.

## Componentes que faltan

- ingesta y validación de CFDI;
- validación jurídica de la cesión del derecho de cobro;
- registro contra doble financiamiento;
- motor de underwriting y límites de concentración;
- modelo de riesgo del deudor y del proveedor;
- LoanBroker y lógica de originación;
- integración con bóvedas de liquidez;
- cobranza y conciliación bancaria;
- contabilidad de doble partida;
- manejo de mora, disputas, fraude y recuperación;
- KYC, KYB, prevención de lavado y controles regulatorios;
- panel para PyMEs, financiadores, operadores y auditores.

## Relación con MicoPay Issuer OS

El factoraje debe funcionar como un producto construido sobre la infraestructura financiera común de MicoPay:

- **Factoring:** valida las cuentas por cobrar, calcula el riesgo y administra el crédito.
- **MicoPay Issuer OS:** registra operaciones, lleva la contabilidad, concilia activos y obligaciones y conecta proveedores financieros.
- **MicoPay APK:** aporta identidad, wallet y autorización del usuario.
- **MicoPay Protocol:** aporta los flujos transaccionales que se decida reutilizar.

La lógica de crédito no debe mezclarse con el núcleo de emisión o con el escrow de efectivo. Cada componente conserva responsabilidades y riesgos diferentes.

## Riesgos principales

- fraude documental o CFDI sin operación comercial real;
- doble financiamiento de la misma cuenta por cobrar;
- disputa sobre entrega, calidad o aceptación del servicio;
- concentración en uno o pocos deudores;
- incumplimiento del deudor;
- diferencias entre la representación en cadena y los derechos legales reales;
- exposición de información fiscal o comercial sensible;
- promesas de liquidez incompatibles con la cobranza efectiva;
- tratamiento regulatorio del crédito, la inversión y la intermediación.

La blockchain puede registrar y ejecutar reglas, pero no sustituye la evaluación crediticia, la cesión legal, la cobranza ni la resolución de disputas del mundo real.

## Modelo de ingresos considerado

La investigación plantea tres fuentes posibles:

- comisión de originación;
- comisión de administración;
- participación en el margen financiero o rendimiento.

La estructura definitiva dependerá de las responsabilidades legales, el origen de la liquidez y quién asuma las primeras pérdidas.

## Documentación

- [Reporte: Factoring XRPL para el mercado mexicano](./docs/Reporte_Factoring_XRPL_Mexico_2026.pdf)

## Próxima revisión recomendada

Antes de escribir código:

1. verificar el estado vigente de XLS-65 y XLS-66;
2. definir la estructura jurídica mexicana de la cesión y cobranza;
3. elegir un sector y un deudor piloto;
4. diseñar el modelo de underwriting y First-Loss Capital;
5. decidir qué entidad origina el crédito y custodia la liquidez;
6. definir el vínculo técnico con MicoPay Issuer OS;
7. construir un prototipo con facturas y fondos de prueba.

## Aviso

Este repositorio es experimental y educativo. No constituye asesoría legal, fiscal o financiera. Tampoco representa una solicitud de inversión, una promesa de rendimiento o la disponibilidad de un servicio de factoraje.

## Licencia

MIT. Consulta [LICENSE](./LICENSE).
