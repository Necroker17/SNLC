# Programa de Embajadores — Comisiones

> Mantenido por `/product`. Fuente de verdad de la estructura de comisiones para embajadores/afiliados que venden el Scanner. Depende de `pricing_strategy.md` (planes y precios) — cualquier cambio de precio ahí impacta el cálculo de comisión aquí.

**Decisión oficial (2026-07-06):** comisión escalonada por cliente referido, no un 50% recurrente plano de por vida.

---

## 1. Estructura de comisión

| Evento | Comisión |
|---|---|
| Primera venta de un cliente referido (STANDARD, PRO o PREMIUM) | **50%** del valor pagado por el cliente |
| Segunda re-compra del mismo cliente en adelante (renovaciones/re-consumos posteriores) | **25%** del valor pagado, en cada re-consumo, sin límite de tiempo mientras el cliente siga activo bajo ese embajador |

**Por qué esta estructura y no 50% recurrente plano:** el 50% recompensa lo más caro de reemplazar — la adquisición de un cliente nuevo. El 25% en adelante sigue premiando la retención sin comprometer el margen indefinidamente al mismo nivel que la venta inicial. Un embajador que trae un cliente que se queda años sigue ganando, pero la casa recupera más margen a partir del segundo ciclo.

---

## 2. Supuesto pendiente de confirmar con el usuario

- **Qué cuenta como "re-consumo":** se asume que es cualquier nueva compra del mismo cliente después de la primera (renovación del mismo plan o upgrade a un plan superior). Si el negocio quiere tratar un *upgrade* de plan de forma distinta a una *renovación* del mismo plan, hay que definirlo aquí antes de comunicarlo a los embajadores.
- **Segunda compra vs. "en adelante":** se interpreta que el 25% aplica desde la segunda compra **y todas las siguientes** (no solo la segunda). Confirmar si es la lectura correcta.

---

## 3. Riesgo abierto — margen no calculado

El usuario confirmó (2026-07-06) que **el margen neto por plan aún no está calculado** (precio menos costos de infraestructura, soporte, bono del broker, etc.). Esta estructura de comisión (50% / 25%) se definió sin ese dato — es razonable como punto de partida frente a un 50% recurrente plano, pero **no está validada contra margen real**.

Antes de lanzar el programa a embajadores externos:
1. Calcular el costo real de servir un cliente por plan (no solo el bono del broker — también soporte, infraestructura de señales, etc.).
2. Verificar que precio − costo − comisión del embajador siga dejando margen positivo saludable, especialmente en el escenario "peor caso" (cliente PREMIUM que renueva varias veces con un embajador ganando 25% cada vez).
3. Si el margen no alcanza, ajustar aquí antes de comunicar cifras a nadie — nunca al revés.

---

## 4. Reglas resueltas (2026-07-09) y pendientes

**Resuelto:**
- **Cierre directo del fundador (Juan) = venta directa**, sin comisión de embajador — Synapse retiene todo salvo la `cuota_socio` (ver `financial_model.md` §1.3).
- **Atribución en canal fusionado (varios embajadores en un mismo WhatsApp):** cada cliente se atribuye a **un** embajador vía palabra clave o link único por embajador; si existe registro de la comunidad de origen previa a la fusión, esa es la atribución por defecto. Detalle operativo en `lanzamiento_1_secuencia.md` §5.
- **Coexistencia con la `cuota_socio`:** la comisión del embajador y el 15%/25% del socio se calculan ambos sobre el precio facturado pero salen de bolsillos distintos — el embajador cobra su tramo, el socio cobra del lado de Synapse. No se restan entre sí; ambos reducen el margen retenido por Synapse (ver tabla en `financial_model.md` §2.1).

**Pendiente:**
- Ventana de pago de comisión (¿al confirmarse el pago del cliente, o con algún período de gracia por reembolsos/chargebacks?).
- Qué pasa si el cliente cancela o no renueva — ¿el embajador pierde el derecho a comisión futura de ese cliente automáticamente?
- Implementación técnica del tracking (código/link único por embajador) para operar la atribución a escala más allá del primer lote.
