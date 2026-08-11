# Changelog

Todos los cambios relevantes del indicador se anotan aquí.

El formato sigue [Keep a Changelog](https://keepachangelog.com/es-ES/1.1.0/)
y el versionado sigue [Semantic Versioning](https://semver.org/lang/es/).

Tipos de cambio que usamos: **Añadido**, **Cambiado**, **Corregido**, **Eliminado**.

## [Sin publicar]

## [1.1.0] - 2026-08-11

### Añadido

- **Sesión asiática**: caja sombreada acotada al máximo y al mínimo de la sesión (no ocupa todo el eje Y). Se dibuja en todas las sesiones del histórico y se va estirando en vivo mientras Asia sigue abierta. Configurable desde el grupo *Sesión asiática* (horas de inicio/fin, color, transparencia de fondo y de borde).
- **Stop loss automático** a partir del rango asiático: si la vela de 8:30 es alcista el SL va al **mínimo** de Asia; si es bajista, al **máximo**. Se pinta como línea roja discontinua con su etiqueta y aparece en la tabla. Si no hay datos de Asia, el SL se omite (`s/d`).
- **Marcador de la vela de 8:30** (grupo *Marcar la vela 8:30*): recuadro alrededor de la vela, flecha señalándola y opción de colorear la propia vela. Se dibuja en cuanto abre la vela y se ajusta en vivo hasta que cierra.
- **Fecha** de la vela de referencia en la tabla de resumen.
- Ajuste **"Separar la tabla del borde derecho (% ancho)"** (7% por defecto) para despegar la tabla del borde. Pine no admite desplazamientos en píxeles, así que se implementa con una columna vacía que hace de margen.

### Cambiado

- La alerta al cierre de la vela ahora incluye también el **SL**, y el cierre pasa a llamarse *Entrada*.
- Los colores de las líneas dejan de depender de la dirección: **TP siempre verde** y **SL siempre rojo**. Los ajustes *Color alcista / Color bajista* pasan a ser *Color TP / Color SL*.
- El fondo y el marco de la tabla se aplican **celda a celda** en lugar de a la tabla entera, necesario para que la columna de margen quede transparente. Como efecto secundario desaparecen el marco exterior y las líneas de separación entre celdas.
- Nombre del indicador: `Vela 8:30 → TP ±100 pts + Asia/SL` (antes `Vela 8:30 → TP ±100 pts`).
- El grupo de ajustes *Configuración* pasa a llamarse *Vela de referencia (8:30)*.

## [1.0.0] - 2026-08-10

### Añadido

- Versión inicial del indicador: detecta la vela de las 8:30 en gráfico de 5 minutos y calcula el TP a ±X puntos de su cierre según la dirección de la vela.
- Línea y etiqueta de TP, línea de entrada opcional (cierre de la vela) y opción de conservar los días anteriores.
- Tabla de resumen en la esquina superior derecha con dirección, entrada y TP.
- Alerta (`alert`) al cerrar la vela con la dirección, el cierre y el TP.
- Aviso en pantalla si el gráfico no está en temporalidad de 5 minutos.
- README con instrucciones de uso y de instalación en TradingView.
