# Home Assistant Blueprints

Reusable Home Assistant automation blueprints for state-aware alerts and action loops.

## Blueprints

### Auto Annoyer: Repeat any actions until a state is resolved

Any door left open. Any bad temp in a machine. Any package is detected.

Basically anything that needs to be addressed and is detectable by home assistant.

Example: Bug your kids with a google home announcement that increases in volume,
because they left the freezer open in the garage.

Example: Bug your kids to shut the damn door they left cracked open that's letting
all the A/C out.

Example: Bug yourself because your server is overheating.

Bug people with automation™

Once they resolve the issue, stop being annoying and play a happy noise and congratulate
them. Or something whatever idc

---

This blueprint starts from anything configurable in Home Assistant's normal trigger
editor, runs optional start actions once, repeats any user-configured action list
while a binary state remains active, and runs optional end actions once when the
state resolves. Repeating actions can use `{{ loop_index }}` or `{{ repeat.index }}`
in templates.

An optional **Resolution grace period** requires the monitored entity to remain in
its resolved state continuously before the loop ends. If the entity becomes active
again during the grace period, the loop continues.

An optional **Maximum loops** setting provides a hard safety cap for long-running
automations. Leave it at `0` for unlimited behavior. When the cap is reached,
the loop ends and the configured end actions run.

[View blueprint](blueprints/automation/repeat_actions_until_resolved.yaml)

Import URL:

```text
https://github.com/billy-the-ape/ha-blueprints/blob/main/blueprints/automation/repeat_actions_until_resolved.yaml
```

### Early Version Auto Annoyer: Repeating escalating spoken alert

Announces a configurable message while a binary state remains active, increasing
the media-player volume on each iteration up to a configured limit. It can play
an optional warning sound beginning on a selected iteration and restore the
original volume after the alert resolves.

[View blueprint](blueprints/automation/repeating_spoken_alert.yaml)

Import URL:

```text
https://github.com/billy-the-ape/ha-blueprints/blob/main/blueprints/automation/repeating_spoken_alert.yaml
```

## Installation

1. In Home Assistant, open **Settings → Automations & scenes → Blueprints**.
2. Select **Import Blueprint**.
3. Paste one of the GitHub URLs above and select **Preview**.
4. Import the blueprint, then select **Create automation**.

The generic action-loop blueprint requires Home Assistant 2024.10.0 or newer.
The spoken-alert blueprint requires Home Assistant 2024.6.0 or newer.

## Updating

After this repository publishes an update, open the blueprint's three-dot menu
in Home Assistant and select **Re-import blueprint**.

## License

Licensed under the [BSD Zero Clause License](LICENSE).
