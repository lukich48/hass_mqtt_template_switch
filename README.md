# Mqtt template switch

The component base on a standard mqtt switch and has 2 addition properties:

```yaml
payload_template_on
payload_template_off
```

# Example:

```yaml
switch:
  - platform: mqtt_template
    name: laundry-fan
    state_topic: "home/bathroom/switch/laundry-fan/state"
    command_topic: "home/bathroom/switch/laundry-fan"
    payload_template_on: '{"action":"hold","duration": {{(states.input_number.fan_duration.state
        | int)*1000}}}'
    payload_template_off: '{"action":"off"}'
    state_on: 1
    state_off: 0
```