# INFORMATIONEN ZUM ANIMIERTEN HINTERGRUND

Hier zeige ich meinen selbst erstellten Template Sensor für die Steuerung eines animierten Hintergrunds in Home Assistant.
Der Sensor basiert auf verschiedenen Parametern, darunter die Position der Sonne über und unter dem Horizont sowie aktuelle Wetterdaten. 
Die Hauptintention hinter diesem Sensor besteht darin, sicherzustellen, dass während der Nacht, also wenn die Sonne unter dem Horizont liegt, keine Bilder mit Sonnenlicht im Hintergrund angezeigt werden.


![ABACKGRAOUND](/../main/06_A_BACKGROUND/Bildschirmschoner_Hintergrund/Vorschaubilder/a_backgound_tag_nacht.gif)


<details>

<summary>## HIER GIBTS DAS TEMPLATE</summary>

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


Natürlich musste auch der Code für den `RAW Konfigurationseditor` am Dashboard angepasst werden.
Dieser enthällt nun zusätzliche Bilder und den neuen Template Sensor `sensor.a_background_tag_nacht` als Entität.


<details>

<summary>## HIER GIBTS DEN EINTRAG FÜR DAS DASHBOARD</summary>

### Code für den RAW Konfigurationseditor

```yaml
animated_background:
  groups:
    - name: weather
      config:
        default_url: https://cdn.flixel.com/flixel/ypy8bw9fgw1zv2b4htp2.hd.mp4
        entity: sensor.a_background_tag_nacht
        state_url:
          sunny:
            - https://cdn.flixel.com/flixel/hlhff0h8md4ev0kju5be.hd.mp4
            - https://cdn.flixel.com/flixel/zjqsoc6ecqhntpl5vacs.hd.mp4
            - https://cdn.flixel.com/flixel/jvw1avupguhfbo11betq.hd.mp4
            - https://cdn.flixel.com/flixel/8cmeusxf3pkanai43djs.hd.mp4
            - https://cdn.flixel.com/flixel/guwb10mfddctfvwioaex.hd.mp4
            - https://cdn.flixel.com/flixel/wk1xpz8kv5jylcyro8bl.hd.mp4
          partlycloudy:
            - https://cdn.flixel.com/flixel/13e0s6coh6ayapvdyqnv.hd.mp4
            - https://cdn.flixel.com/flixel/aorl3skmssy7udwopk22.hd.mp4
            - https://cdn.flixel.com/flixel/qed6wvf2igukiioykg3r.hd.mp4
            - https://cdn.flixel.com/flixel/3rd72eezaj6d23ahlo7y.hd.mp4
            - https://cdn.flixel.com/flixel/9m11gd43m6qn3y93ntzp.hd.mp4
            - https://cdn.flixel.com/flixel/hrkw2m8eofib9sk7t1v2.hd.mp4
          cloudy:
            - https://cdn.flixel.com/flixel/13e0s6coh6ayapvdyqnv.hd.mp4
            - https://cdn.flixel.com/flixel/aorl3skmssy7udwopk22.hd.mp4
            - https://cdn.flixel.com/flixel/qed6wvf2igukiioykg3r.hd.mp4
            - https://cdn.flixel.com/flixel/3rd72eezaj6d23ahlo7y.hd.mp4
            - https://cdn.flixel.com/flixel/9m11gd43m6qn3y93ntzp.hd.mp4
            - https://cdn.flixel.com/flixel/hrkw2m8eofib9sk7t1v2.hd.mp4
          mostlycloudy:
            - https://cdn.flixel.com/flixel/e95h5cqyvhnrk4ytqt4q.hd.mp4
            - https://cdn.flixel.com/flixel/l2bjw34wnusyf5q2qq3p.hd.mp4
            - https://cdn.flixel.com/flixel/rrgta099ulami3zb9fd2.hd.mp4
          clear-night:
            - https://cdn.flixel.com/flixel/x9dr8caygivq5secll7i.hd.mp4
            - https://cdn.flixel.com/flixel/v26zyfd6yf0r33s46vpe.hd.mp4
            - https://cdn.flixel.com/flixel/rosz2gi676xhkiw1ut6i.hd.mp4
          fog:
            - https://cdn.flixel.com/flixel/vwqzlk4turo2449be9uf.hd.mp4
            - https://cdn.flixel.com/flixel/5363uhabodwwrzgnq6vx.hd.mp4
          rainy:
            - https://cdn.flixel.com/flixel/qti3s5st0srowd9krhcw.hd.mp4
            - https://cdn.flixel.com/flixel/f0w23bd0enxur5ff0bxz.hd.mp4
          pouring:
            - https://cdn.flixel.com/flixel/qti3s5st0srowd9krhcw.hd.mp4
            - https://cdn.flixel.com/flixel/f0w23bd0enxur5ff0bxz.hd.mp4
          lightning-rainy:
            - https://cdn.flixel.com/flixel/sbk5sc03j7vay52r3e4o.hd.mp4
            - https://cdn.flixel.com/flixel/chrgj6raf5q3s6y2so7z.hd.mp4
          snowy:
            - https://cdn.flixel.com/flixel/on3ysblo5hzdmrhv1kwh.hd.mp4
            - https://cdn.flixel.com/flixel/psi1hhbsshcus8eumtr7.hd.mp4
            - https://cdn.flixel.com/flixel/ndza6yswd0k6vlboxyhk.hd.mp4
            - https://cdn.flixel.com/flixel/bbqzgcm54sbewywlcl1d.hd.mp4
          snowy-rainy:
            - https://cdn.flixel.com/flixel/on3ysblo5hzdmrhv1kwh.hd.mp4
            - https://cdn.flixel.com/flixel/psi1hhbsshcus8eumtr7.hd.mp4
            - https://cdn.flixel.com/flixel/ndza6yswd0k6vlboxyhk.hd.mp4
            - https://cdn.flixel.com/flixel/bbqzgcm54sbewywlcl1d.hd.mp4
          night_partlycloudy:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_cloudy:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_mostlycloudy:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_clear-night:
            - https://cdn.flixel.com/flixel/x9dr8caygivq5secll7i.hd.mp4
            - https://cdn.flixel.com/flixel/v26zyfd6yf0r33s46vpe.hd.mp4
            - https://cdn.flixel.com/flixel/rosz2gi676xhkiw1ut6i.hd.mp4
          night_fog:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_rainy:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_pouring:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_lightning-rainy:
            - https://cdn.flixel.com/flixel/lcjcf0kq236tlnxzdyog.hd.mp4
          night_snowy:
            - https://cdn.flixel.com/flixel/65hxqr4u4o62idb86e36.hd.mp4
          night_snowy-rainy:
            - https://cdn.flixel.com/flixel/65hxqr4u4o62idb86e36.hd.mp4
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
