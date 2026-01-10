# Ring2Open Blueprints (Ring Intercom + Home Assistant)

This repository contains Home Assistant Blueprints that implement a Nuki-like "Ring to Open" flow for a Ring Intercom setup.

## Blueprint: Ring-to-Open (helper-based)

Behaviour:
1. On arrival (authorised person becomes `home`), enable Ring-to-Open (`input_boolean`) for a configured time.
2. While Ring-to-Open is active, pressing the Ding (doorbell binary_sensor) unlocks the Intercom lock.
3. After the configured time, Ring-to-Open is disabled again.
4. Optional: a special trigger can enable Ring-to-Open (e.g. phone battery below a threshold while not at home).

### Import into Home Assistant

Use the raw GitHub URL:

`https://raw.githubusercontent.com/<YOUR_GITHUB_USER>/<YOUR_REPO>/main/automation/ring_intercom/ring_to_open.yaml`

Home Assistant:
Settings → Automations & Scenes → Blueprints → Import Blueprint

### Required entities

- Ding: `binary_sensor.*`
- Intercom: `lock.*`
- Authorised Person: `person.*`
- Ring-to-Open Active helper: `input_boolean.*`

### Helper to create

Settings → Devices & services → Helpers → Add Helper → Toggle

Example entity id:
- `input_boolean.ring_to_open`

## Notes

- This blueprint is intentionally helper-based so you can also toggle Ring-to-Open manually from the UI.
- If your phone battery sensor is not numeric (e.g. returns "50 %"), create a template sensor that outputs a number 0–100.
