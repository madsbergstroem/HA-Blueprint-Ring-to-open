# Ring Intercom – Ring-to-Open (Gate-based, Emergency-aware)

A Home Assistant blueprint implementing **Nuki-like Ring-to-Open behaviour**
for Ring Intercoms using a **strict gate model**.

The door is unlocked **only** when a dedicated helper (`input_boolean`)
explicitly allows it.

---

## Core Concept

**One gate. One decision. No side effects.**

> The door may only be unlocked when  
> `ring_to_open = ON`.

All triggers only **enable or disable the gate**.  
The Ding (doorbell) never opens the door by itself.

---

## Required Helper

You must create the following helper manually:

- `input_boolean`
  - Example name: `input_boolean.ring_to_open`
  - Purpose: **single gatekeeper for unlocking**

---

## Supported Scenarios

### 1. Arrival Window (Default)

**Purpose:** Convenience when coming home.

**Enable**
- At least one authorised person arrives home

**Disable**
- After a configurable arrival timeout

**Notes**
- Time-based
- Safe by design
- Does not affect Emergency Mode

---

### 2. Emergency Mode (Battery Critical)

**Purpose:** Ensure access when devices are critically low on battery.

**Enable**
- Emergency Mode enabled
- ANY configured battery sensor below threshold
- Nobody is home

**Disable (configurable, multi-select)**
- All batteries are OK again
- An authorised person arrives home
- Optional global emergency timeout

**Notes**
- State-based by default
- Timeout is optional
- Designed to avoid lock-outs

---

### 3. Manual Enable

**Purpose:** Explicit user override.

**Enable**
- User manually switches `ring_to_open` ON

**Disable**
- Optional auto-reset after first Ding
- Optional emergency timeout
- Arrival logic if configured

---

### 4. Ding (Doorbell)

**Unlock happens ONLY if**
- Ding is pressed
- `ring_to_open = ON`
- At least one authorised person is home

**Optional**
- Auto-reset gate after first successful unlock

---

## Emergency Mode Configuration

You can configure **multiple batteries** and **multiple disable conditions**.

### Emergency Disable Options
- Batteries recovered
- Person arrives home
- Global emergency timeout

All options are **independent and combinable**.

---

## Debug Logging

The blueprint logs all relevant decisions to the Home Assistant Logbook:

- Why Ring-to-Open was enabled
- Why it was disabled
- Why the door was unlocked

This makes every unlock **fully explainable and auditable**.

---

## Safety Guarantees

- No unlock without explicit gate
- No silent state changes
- No emergency lock-out by default
- No global timeout forcing unsafe behaviour

---

## Design Philosophy

- Deterministic
- Explainable
- Emergency-safe
- Minimal assumptions
- Production-ready

---

## License

MIT
