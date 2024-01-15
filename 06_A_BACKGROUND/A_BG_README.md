# INFORMATIONEN ZUM ANIMIERTEN HINTERGRUND

Hier zeige ich meinen selbst erstellten Template Sensor für die Steuerung eines animierten Hintergrunds in Home Assistant.
Der Sensor basiert auf verschiedenen Parametern, darunter die Position der Sonne über und unter dem Horizont sowie aktuelle Wetterdaten. 
Die Hauptintention hinter diesem Sensor besteht darin, sicherzustellen, dass während der Nacht, also wenn die Sonne unter dem Horizont liegt, keine Bilder mit Sonnenlicht im Hintergrund angezeigt werden.


![ABACKGRAOUND](/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/a_backgound_tag_nacht.gif)

<details>

<summary>HIER GIBTS DAS TEMPLATE</summary>

### Animated Background Tag Nacht Sensor

Dieses Template ist für den Sensor Folder (eine Ausgelagerte Datei) erstellt worden.
Beim Einfügen in die `configuration.yaml` müssen Formatierungen vorgenommen werden.

```yaml
#########################################################################################
#---------------------------------------------------------------------------------------#
##--------------- TAG NACHT Änderung für den animierten Hintergrund -------------------##
#---------------------------------------------------------------------------------------#
#########################################################################################

sensor:

#-----------------------------------------------------------
# Tag/Nacht Änderung
#-----------------------------------------------------------
- name: A-Background Tag Nacht
  unique_id: a_background_tag_nacht
  icon: theme-light-dark
  state: >
    {%- set SUN = states['sun.sun'].state %}
    {%- set WEATHER = states['sensor.openweathermap_condition'].state %}
    {%- set DAY = "above_horizon" %}
    {%- set NIGHT = "below_horizon" %}
    {%- if SUN == DAY %}
    {{ WEATHER }}
    {%- elif SUN == NIGHT %}
    night_{{ WEATHER }}
    {%- else %}
    Default
    {%- endif %}
```
</details>

# MEINE VIDEOS FÜR DEN ANIMATED BACKGROUND UND SCREENSAVER


| **ADVENT** | **BERGSEE** |
| :---: | :---: |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Advent.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Advent.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Bergsee.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Bergsee.png" width="400"></a> |
| **FEUERSTELLE** | **FEUERWERK** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Feuerstelle.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Feuerstelle.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Feuerwerk.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Feuerwerk.png" width="400"></a> |
| **KAMINFEUER** | **NORDLICHT** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Kaminfeuer.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Kaminfeuer.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Nordlicht.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Nordlicht.png" width="400"></a> |
| **WALDSEE-2** | **WALDSEE-3** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Waldsee-2.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Waldsee-2.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Waldsee-3.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Waldsee-3.png" width="400"></a> |
| **WALDSEE** | **WASSERFALL-FLUSS-2** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Waldsee.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Waldsee.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Wasserfall-Fluss-2.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Wasserfall-Fluss-2.png" width="400"></a> |
| **WASSERFALL-FLUSS** | **WASSERFALL-WALD-2** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Wasserfall-Fluss.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Wasserfall-Fluss.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Wasserfall-Wald-2.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Wasserfall-Wald-2.png" width="400"></a> |
| **WASSERFALL-WALD** | **WEIHNACHTEN** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Wasserfall-Wald.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Wasserfall-Wald.png" width="400"></a> | <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Weihnachten.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Weihnachten.png" width="400"></a> |
| **WINTERLANDSCHAFT** | **LEER** |
| <a href="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Winterlandschaft.mp4" target="_blank">  <img src="/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/Winterlandschaft.png" width="400"></a> |  |
