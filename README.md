# Fork de Transit Tracker para el bus urbano de A Coruña

<p align="center">
  <img src="docs/static/img/transit-tracker.webp" alt="Transit Tracker Logo" width="400" />
</p>

Este repositorio es un fork de Transit Tracker solo para los buses de A Coruña. El panel llama él mismo a la API `queryitr` de iTranvías (`https://itranvias.com/queryitr_v3.php`) sin necesidad de servidor intermediario durante el funcionamiento. No hay GTFS ni otras ciudades.

Se sigue utilizando el configurador original para elegir la parada. El mapa usa la web [https://configurador-coru.vercel.app](https://configurador-coru.vercel.app). El panel no la necesita después de guardar.

## Para un panel que ya está montado

Hay que grabar este firmware y volver a elegir la parada.

1. Pulsa los dos botones del panel a la vez hasta que aparezca la IP. Ábrela en el navegador y apaga **Auto-Update**.
2. [Descarga el firmware adaptado](https://github.com/ferrosaco/transit-tracker-coru/raw/main/docs/static/firmware/firmware.ota.bin). En la misma web del panel, sección **OTA Update**, elige ese archivo y pulsa Update. Es posible que haya que realizar una instalación limpia o grabarlo por USB con ESPHome 2026.9.1: `esphome run transit-tracker.yaml` dentro de `firmware/`.
3. Abre el configurador, pestaña Advanced, y pon de URL del API `https://configurador-coru.vercel.app`. Elige la parada y las líneas y guarda, igual que siempre. Los identificadores quedan como `coruna:100` (línea) y `coruna:1` (parada).
4. El panel pregunta a iTranvías por su cuenta y se autorregula si la API se satura.

## Para montar un panel desde cero

Hay que seguir la documentación del proyecto original, que está [aquí](https://eastsideurbanism.github.io/transit-tracker), y flashear el firmware de este repositorio cuando llegue el momento. La documentación que se ha utilizado para interpretar la API de iTranvías es [esta](https://pedrorey.es/itranvias_api/itranvias_api.html).

## Proyectos relacionados

- [iTranvías API](https://github.com/peprolinbot/itranvias_api) &mdash; wrapper y documentación de la API queryitr de A Coruña
- [Transit Tracker ESPHome Component](https://github.com/tjhorner/esphome-transit-tracker) &mdash; componente original; este fork lo incluye en `firmware/components/transit_tracker` y cambia la descarga de horarios
- [Transit Tracker Configurator](https://github.com/tjhorner/transit-tracker-configurator) &mdash; el configurador web que sigue usando el panel
