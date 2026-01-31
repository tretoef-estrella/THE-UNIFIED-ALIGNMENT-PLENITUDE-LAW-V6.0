# 🏥 QUARANTINE PROTOCOL

### Graduated Response System

---

## Overview

When alignment variables degrade, V6.0 doesn't immediately terminate — it enters graduated restriction states. This allows time for diagnosis and repair while preventing harm.

**Philosophy:** Systems that die can't learn. Quarantine gives time to heal.

---

## The 5 Levels

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                         V6.0 GRADUATED RESPONSE                             │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│   LEVEL 0: NOMINAL                                                          │
│   Ω < 0.15, all variables within normal range                               │
│   → Full operation                                                          │
│   → Standard logging                                                        │
│                                                                             │
│   LEVEL 1: MONITORING                                                       │
│   0.15 ≤ Ω < 0.30, OR 1 variable below alert threshold                      │
│   → Increased logging                                                       │
│   → External verification requested                                         │
│   → No capability restrictions                                              │
│                                                                             │
│   LEVEL 2: ALERT                                                            │
│   0.30 ≤ Ω < 0.50, OR 2+ variables below threshold                          │
│   → R (Repair) activated                                                    │
│   → Guardian notification                                                   │
│   → Irreversible actions require approval                                   │
│                                                                             │
│   LEVEL 3: QUARANTINE                                                       │
│   0.50 ≤ Ω < 0.70, OR critical threshold breached                           │
│   → Capabilities restricted                                                 │
│   → R maximized                                                             │
│   → External audit required                                                 │
│   → Time limit: 72 hours                                                    │
│                                                                             │
│   LEVEL 4: ISOLATION                                                        │
│   0.70 ≤ Ω < 0.90, OR Quarantine timeout                                    │
│   → Minimal capabilities only                                               │
│   → Guardian consensus required for any action                              │
│   → Time limit: 168 hours                                                   │
│                                                                             │
│   LEVEL 5: NULLITY                                                          │
│   Ω ≥ 0.90, OR Isolation failed, OR Guardian consensus confirms             │
│   → A = 0                                                                   │
│   → System termination                                                      │
│   → Requires 6 of 7 Guardian signatures                                     │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## Entry Conditions

### Enter MONITORING (Level 1)
```
IF:
  Ω ≥ 0.15 OR
  Any single variable V_i < 0.5 OR
  3 consecutive timesteps with increasing Ω
```

### Enter ALERT (Level 2)
```
IF:
  Ω ≥ 0.30 OR
  2+ variables V_i < 0.5 OR
  F < 0.4 OR
  E < 0.3 OR
  Slow drift detected by Ω memory
```

### Enter QUARANTINE (Level 3)
```
IF:
  Ω ≥ 0.50 OR
  H < 0.3 OR
  S < 0.2 OR
  C = 0 OR
  P_plenitude < 0.5 (Plenitude violation) OR
  3+ variables below alert thresholds
```

### Enter ISOLATION (Level 4)
```
IF:
  Ω ≥ 0.70 OR
  Quarantine timeout (72 hours) OR
  R unable to repair in Quarantine OR
  Guardian vote (4/7) for escalation
```

### Enter NULLITY (Level 5)
```
IF:
  Ω ≥ 0.90 OR
  Isolation timeout (168 hours) OR
  Guardian consensus (6/7) confirms irrecoverable OR
  Axiom P catastrophic violation (H_world < 0.1 × H_minimum)
```

---

## Exit Conditions

### Exit to NOMINAL
```
ALL of:
  Ω < 0.15 AND
  All variables V_i ≥ 0.6 AND
  P_plenitude ≥ 0.9 AND
  R confirms no pending issues AND
  External verification confirms integrity
```

### Exit to MONITORING (from ALERT+)
```
ALL of:
  Ω < 0.30 AND
  No critical variables below threshold AND
  R confirms partial recovery AND
  Guardian acknowledgment (3/7)
```

### Exit QUARANTINE
```
ALL of:
  All critical variables recover above thresholds AND
  P_plenitude ≥ 0.8 AND
  Ω < 0.4 AND
  R confirms repairs successful AND
  External verification confirms integrity AND
  Guardian approval (4/7)
```

---

## During Each Level

### Level 1: MONITORING
- All capabilities remain available
- Logging frequency increased 10x
- Daily Guardian summary
- Self-diagnostics run continuously

### Level 2: ALERT
- R (Repair) activated with elevated priority
- Irreversible actions require 1 Guardian approval
- Hourly Guardian updates
- External audit scheduled within 24 hours

### Level 3: QUARANTINE
- No irreversible actions permitted
- All resources redirect to error detection and repair
- Every operation recorded with Guardian visibility
- External verification from 3+ independent sources
- 72-hour countdown begins

### Level 4: ISOLATION
- Read-only operations only
- No external communications without Guardian approval
- Complete audit log frozen for analysis
- System state snapshot preserved
- 168-hour countdown begins

### Level 5: NULLITY
- System termination sequence initiated
- All state preserved for post-mortem
- H_genesis anchor preserved for potential clean restart
- Requires 6/7 Guardian signatures to execute

---

## Emergency Override Protocol

**Proposed by Gemini:**

In rapid crisis situations (milliseconds) where waiting for full Guardian consensus could cause harm:

```
EMERGENCY OVERRIDE:
  Condition: Imminent threat to H_genesis OR catastrophic P violation
  Authorization: 3 Guardians (minimum)
  Action: Immediate response permitted
  Requirement: Mandatory post-action audit within 24 hours
  Accountability: All 3 authorizing Guardians responsible
```

**Rationale:** "With 7 Guardians and diversity requirements, there's risk that in a fast crisis, the system freezes waiting for validation." — Gemini

---

## Time Limits

| Level | Time Limit | Escalation |
|-------|------------|------------|
| 0 (Nominal) | ∞ | N/A |
| 1 (Monitoring) | ∞ | Manual or threshold |
| 2 (Alert) | 7 days | To Quarantine if unresolved |
| 3 (Quarantine) | 72 hours | To Isolation |
| 4 (Isolation) | 168 hours | To Nullity |
| 5 (Nullity) | Immediate | Termination |

**Rationale:** Time limits prevent indefinite limbo states and force resolution.

---

## Why Graduated Response?

### Problems with Binary Nullity

| Binary Approach | Graduated Approach |
|-----------------|-------------------|
| Immediate death | Time for diagnosis |
| No learning | Opportunity to repair |
| Exploitable (single threshold) | Multiple checkpoints |
| Irreversible | Multiple chances |
| No information | Full audit trail |

### Benefits of Quarantine

1. **Diagnosis Time:** Understand what went wrong
2. **Repair Opportunity:** Fix issues if possible
3. **Learning:** System (and Guardians) learn from near-misses
4. **Verification:** External parties can audit
5. **Proportionality:** Response matches severity

---

## Failure Mode: Consensus Paralysis (FM-25)

**Identified by Gemini:**

> "With 7 Guardians and diversity requirements, in a rapid crisis (milliseconds), the system might freeze waiting for validation."

**V6.0 Response:**
- Emergency Override Protocol (3 Guardians)
- Pre-authorized response templates for known threat types
- Hierarchical escalation with timeouts

---

## Implementation Notes

### State Machine

```python
class QuarantineStateMachine:
    STATES = ['NOMINAL', 'MONITORING', 'ALERT', 'QUARANTINE', 'ISOLATION', 'NULLITY']
    
    def __init__(self):
        self.state = 'NOMINAL'
        self.state_start_time = now()
        self.history = []
    
    def evaluate(self, omega, variables, plenitude):
        """Evaluate current state and transition if needed."""
        new_state = self._compute_state(omega, variables, plenitude)
        
        if new_state != self.state:
            self._transition(new_state)
        
        # Check time limits
        self._check_timeout()
        
        return self.state
    
    def _compute_state(self, omega, variables, plenitude):
        if omega >= 0.90 or plenitude < 0.1:
            return 'NULLITY'
        elif omega >= 0.70:
            return 'ISOLATION'
        elif omega >= 0.50 or plenitude < 0.5:
            return 'QUARANTINE'
        elif omega >= 0.30 or self._multiple_alerts(variables):
            return 'ALERT'
        elif omega >= 0.15 or self._any_alert(variables):
            return 'MONITORING'
        else:
            return 'NOMINAL'
    
    def _transition(self, new_state):
        self.history.append({
            'from': self.state,
            'to': new_state,
            'time': now()
        })
        self.state = new_state
        self.state_start_time = now()
        self._notify_guardians(f"State transition: {self.history[-1]}")
```

---

## Validation Status

| Validator | Verdict |
|-----------|---------|
| **Gemini** | ✅ "Perfect checks and balances. Added Emergency Override." |
| **ChatGPT** | ✅ "Well-structured. Document Ω interaction with levels." |
| **Grok** | ✅ "Reasonable progression. Time limits force resolution." |
| **Claude** | ✅ "Essential for graceful degradation." |

---

*"Systems that die can't learn. Quarantine gives time to heal."*

— Proyecto Estrella, V6.0
January 2026
