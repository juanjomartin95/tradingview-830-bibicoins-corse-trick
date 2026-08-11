# Vela 8:30 → TP ±100 pts + Asia/SL

Indicador para TradingView (Pine Script v6) que trabaja sobre la vela de las **8:30** en un gráfico de **5 minutos** y, al cerrarse esa vela (a las 8:35), calcula la operación completa:

- **Dirección**: la marca el cierre de la vela (alcista si cierra ≥ apertura).
- **Entrada**: el cierre de la vela de 8:30.
- **TP**: cierre **+ X puntos** si es alcista, cierre **− X puntos** si es bajista.
- **SL**: el extremo opuesto del **rango de la sesión asiática** → si la vela es **alcista**, el SL va al **mínimo** de Asia; si es **bajista**, al **máximo**.

Además sombrea la sesión asiática con una caja acotada a su máximo y su mínimo (no ocupa todo el eje Y), marca visualmente la vela de 8:30, muestra una tabla de resumen y lanza un aviso (`alert`) en cuanto la vela cierra.

![Ejemplo de la tabla y las líneas de TP](assets/tabla-tp.png)

## Qué dibuja en el gráfico

| Elemento | Aspecto |
|---|---|
| Caja de la sesión asiática | Rectángulo azul semitransparente, ajustado al máximo/mínimo de la sesión. Se estira en vivo mientras Asia sigue abierta y se congela al cerrar. |
| Vela de 8:30 | Recuadro naranja alrededor de la vela + flecha debajo (opcionalmente, coloreado de la propia vela). |
| Entrada | Línea gris punteada con etiqueta. |
| TP | Línea verde continua con etiqueta y flecha de dirección. |
| SL | Línea roja discontinua con etiqueta. Si no hay datos de Asia, no se dibuja. |
| Tabla de resumen | Esquina superior derecha: fecha, dirección, entrada, TP y SL. |

## Configuración en TradingView

1. Abre el editor Pine (**Pine Editor**, parte inferior de TradingView) ![icono Pine Editor](assets/pine-editor-icon.png).
2. Pega el contenido de [`vela-830-tp.pine`](vela-830-tp.pine) y pulsa **Add to chart** / **Guardar**.
3. **Pon el gráfico en temporalidad de 5 minutos.** Si no está en 5 min, el propio indicador muestra un aviso en pantalla (⚠ *Pon el gráfico en 5 min*).
4. Ajusta la **zona horaria** para que "8:30" corresponda a la hora que realmente quieres (por defecto `Europe/Madrid`). La sesión asiática y la vela de 8:30 usan **la misma** zona horaria, así que este ajuste afecta a las dos.
5. Revisa el resto de parámetros (ver más abajo).
6. Para recibir notificaciones, crea una **alerta** de TradingView sobre este indicador (clic derecho en el gráfico → **Añadir alerta**, o el icono de reloj). El mensaje ya incluye la dirección, la entrada, el TP y el SL calculados.

## Parámetros

### Vela de referencia (8:30)

| Parámetro | Descripción | Por defecto |
|---|---|---|
| Hora de la vela | Hora objetivo (0-23) | 8 |
| Minuto de la vela | Minuto objetivo (0-59) | 30 |
| Zona horaria | Zona con la que se calculan hora/minuto y la sesión asiática | Europe/Madrid |
| Puntos para el TP | Distancia en puntos del TP respecto al cierre | 100 |

### Sesión asiática

| Parámetro | Descripción | Por defecto |
|---|---|---|
| Sombrear sesión asiática | Muestra/oculta la caja del rango asiático | Activado |
| Asia · hora inicio | Hora de inicio de la sesión | 2 |
| Asia · hora fin | Hora de fin de la sesión | 8 |
| Color fondo Asia | Color base de la caja | Azul |
| Transparencia fondo | 0 = sólido, 100 = invisible | 90 |
| Transparencia del borde | Igual, aplicado al borde de la caja | 50 |

> El rango de la sesión asiática es lo que define el SL, así que estas horas afectan al nivel de stop aunque desactives el sombreado.

### Marcar la vela 8:30

| Parámetro | Descripción | Por defecto |
|---|---|---|
| Recuadro alrededor de la vela | Caja naranja que rodea la vela objetivo | Activado |
| Flecha señalando la vela | Triángulo debajo de la vela | Activado |
| Colorear la propia vela | Pinta la vela con el color del marcador | Desactivado |
| Color del marcador | Color del recuadro, la flecha y el coloreado | Naranja |
| Margen del recuadro (ticks) | Holgura entre la vela y el recuadro | 2 |

### Visual

| Parámetro | Descripción | Por defecto |
|---|---|---|
| Horas que se extienden las líneas | Cuánto se alargan entrada/TP/SL hacia la derecha | 13 |
| Mostrar línea de entrada | Muestra/oculta la línea del cierre de la vela | Activado |
| Mostrar días anteriores (historial) | Conserva líneas y etiquetas de días anteriores en vez de borrarlas | Desactivado |
| Mostrar tabla de resumen | Muestra/oculta la tabla superior derecha | Activado |
| Separar la tabla del borde derecho (% ancho) | Margen entre la tabla y el borde del gráfico | 7 |
| Color TP (verde) | Color de la línea y la etiqueta de TP | Verde |
| Color SL (rojo) | Color de la línea y la etiqueta de SL | Rojo |

> El historial solo afecta a las líneas de entrada/TP/SL. Las cajas de la sesión asiática se dibujan siempre en todos los días visibles.

## Historial de cambios

Las mejoras, cambios y correcciones de cada versión están en [`CHANGELOG.md`](CHANGELOG.md).
