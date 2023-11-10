# critical_alert_card_in_homassistant
Карточка критических уведомлений в интерфейсе Lovelace хаба умного дома Home Assistant

https://www.youtube.com/shorts/MU8A0x3SVp0

```yaml
type: custom:mushroom-template-card
primary: |-
  {% if is_state('binary_sensor.we_have_troubles', 'on') %}
    Есть проблемы
  {% else  %}
    Проблем нет
  {% endif  %}
icon: |-
  {% if is_state('binary_sensor.we_have_troubles', 'on') %}
    mdi:radioactive
  {% else  %}
    mdi:check
  {% endif  %}
icon_color: |-
  {% if is_state('binary_sensor.we_have_troubles', 'on') %}
    red
  {% endif  %}
fill_container: true
multiline_secondary: true
layout: vertical
tap_action:
  action: navigate
  navigation_path: /dashboard-/troubles
hold_action:
  action: none
double_tap_action:
  action: none
card_mod:
  style: |
    {% if is_state('binary_sensor.we_have_troubles', 'on') %}
    ha-card {
      animation: borderPulse 1s ease-out infinite;
    }
    @keyframes borderPulse {
      50% {
        box-shadow: 0 0 150px red;
      }
    }
    {% endif  %}
```
