# MediQueue SL

**Triage and Queue Management System for Community Health Centres in Sierra Leone**

PROG101: Principles of Programming Logic and Design | Assignment 1
Limkokwing University of Creative Technology, Sierra Leone
Department of Information and Communication Technology | Semester 01 (September 2026 to January 2027)

| | |
|---|---|
| **Student** | Mohamed Turay |
| **Student ID** | 905006574 |
| **Examiner** | Elijah Fullah |
| **Tool** | Flowgorithm (flowchart and pseudocode) |

> This assignment is a logical design. No source code is written, as required by the brief.

---

## 1. The Problem

Community Health Centres (CHCs) and government hospitals in Sierra Leone often receive more patients than the available nurses can see at once. Patients are commonly attended to in order of arrival, so a pregnant woman with a danger sign, a child under five with a high fever, or a patient showing signs of cholera, Lassa fever or Ebola can wait behind people with mild complaints.

**Who is affected:** patients (especially mothers, children under five and the elderly), nurses and clinic staff, and the wider community when infectious cases are not identified early.

**Why it exists:** limited staff, high patient numbers, paper registers, no standard triage tool, unreliable power and internet, and limited budgets for commercial software.

## 2. The Solution

MediQueue SL is a menu-driven system that applies fixed, transparent triage rules to every patient. It places each patient in a colour-coded queue, issues a ticket with an estimated waiting time, alerts staff to suspected infectious cases, and produces a daily summary.

### Menu

| Option | Function |
|---|---|
| 1 | Register patient |
| 2 | Call next patient |
| 3 | Show queue status |
| 4 | Daily summary |
| 5 | Exit |

### Triage rules

| Priority | Colour | Conditions |
|---|---|---|
| 1 Emergency | RED | Unconscious or convulsing, OR severe bleeding, OR difficulty breathing, OR pregnant with a danger sign, OR age under 5 with temperature of 39.5 C or more |
| 2 Urgent | YELLOW | Temperature of 38.0 C or more, OR pregnant, OR age under 5, OR age 65 or over, OR ill for 3 days or more |
| 3 Routine | GREEN | Everyone else |

### Queue rules

- RED patients are always called first.
- Within each colour, patients are called first come, first served.
- **Fairness limit:** after 4 consecutive YELLOW calls, one GREEN patient is called if any is waiting.
- Maximum queue size is 200 per colour. If a queue is full, the patient is referred to the nearest CHC.
- Estimated wait = patients ahead x 10 minutes (average consultation time).
- Patients with signs of cholera, Lassa fever or Ebola trigger an isolation alert.

## 3. Programming Logic Demonstrated

- **Computational thinking:** decomposition, pattern recognition, abstraction and algorithm design
- **Variables, constants and data types:** Integer, Real, String and Boolean, plus arrays
- **Decision structures:** nested If/Else for the menu, priority and queue selection
- **Repetition structures:** While loop (main menu), Do...Loop (input validation), For loops (initialising, shifting and printing queues)
- **Boolean logic:** AND, OR and NOT in priority and fairness rules
- **Functions and modular design:** 13 modules

| Module | Purpose |
|---|---|
| `Main` | Sets constants and arrays, runs the menu loop |
| `DisplayMenu` | Prints the menu |
| `GetValidatedInteger` / `GetValidatedReal` / `GetYesNo` | Validated input |
| `RegisterPatient` | Collects data, assigns priority, queues the patient, prints ticket |
| `AssignPriority` | Returns 1, 2 or 3 using Boolean rules |
| `AddToQueue` | Adds a patient to the correct queue |
| `CallNextPatient` | Applies RED first and the fairness rule |
| `EstimateWaitTime` | Calculates estimated wait |
| `ColourName` | Converts priority number to RED, YELLOW or GREEN |
| `ShowQueueStatus` | Lists the three queues |
| `GenerateDailySummary` | Totals and percentages |

## 4. Sample Scenario

| Ticket | Patient | Priority | Est. wait |
|---|---|---|---|
| 1 | Aminata Kamara, F, 28, pregnant with danger sign | RED | 0 min |
| 2 | Ibrahim Sesay, M, 4, 38.6 C | YELLOW | 10 min |
| 3 | Fatmata Bangura, F, 35, 36.8 C | GREEN | 20 min |
| 4 | Musa Conteh, M, 41, 39.0 C, infectious signs | YELLOW (isolation alert) | 30 min |

Calling four patients gives the order: Aminata (RED), Ibrahim (YELLOW), Musa (YELLOW), Fatmata (GREEN). The daily summary shows 4 registered, 4 served, Emergency 1 (25%), Urgent 2 (50%), Routine 1 (25%), and 1 suspected infectious case.

## 5. How to View and Run

1. Download and install [Flowgorithm](http://www.flowgorithm.org) (free, Windows).
2. Open `MediQueue_SL.fprg` in Flowgorithm.
3. Click **Run** to use the menu in the console, or view the flowcharts for each function.
4. The flowchart image and the pseudocode can be read without installing anything.

## 6. Repository Contents

```
PROG101_Assignment1_MohamedTuray_905006574/
|-- README.md                          Project overview (this file)
|-- Report/
|   `-- MediQueue_SL_Report.pdf        Full assignment report
|-- Flowcharts/
|   |-- MediQueue_SL.fprg              Flowgorithm program (all 13 functions)
|   `-- MediQueue_SL_Main.png          Main flowchart
`-- Pseudocode/
    `-- MediQueue_SL_Pseudocode.txt    Complete pseudocode
```

## 7. Sustainable Development Goals

- **SDG 3: Good Health and Well-being (primary).** Faster care for emergencies, mothers and children, and early flagging of infectious disease risks.
- **SDG 10: Reduced Inequalities.** A rule-based queue serves patients by need, not status or connections.
- **SDG 9: Industry, Innovation and Infrastructure.** A low-cost, offline-capable digital tool for public services.

## 8. Open Source and Digital Public Good

MediQueue SL is shared openly so that clinicians can check and improve the triage rules, local developers can adapt it, and any facility can use it at no cost.

**Ways to contribute**
- Review and refine the triage thresholds (clinicians and nurses)
- Translate prompts into Krio, Mende and Temne
- Add secure storage, a touch-screen interface or SMS tickets
- Report problems through GitHub Issues

It aims to meet the [Digital Public Goods Standard](https://www.digitalpublicgoods.net/standard/) through an open licence, clear documentation, relevance to the SDGs, no permanent storage of personal data in the prototype, and platform independence. It is a prototype design and has not been registered as a Digital Public Good.

## 9. Limitations

- Data is held in memory only and is lost when the program closes.
- The triage thresholds are design values for learning and must be reviewed by qualified health professionals before any real use.
- The system supports nurses' decisions and does not replace clinical judgement.

## 10. Sustainability

The system needs no internet or special hardware. Queue size, fairness limit and average consultation time are single values that staff can change, and the open design lets the community maintain and extend it.

## 11. Licence

Released under the MIT Licence 
## 12. References

- Digital Public Goods Alliance (n.d.) *The Digital Public Goods Standard*. Available at: https://www.digitalpublicgoods.net/standard/
- Mackway-Jones, K., Marsden, J. and Windle, J. (eds.) (2014) *Emergency triage: Manchester Triage Group*. 3rd edn. Chichester: Wiley Blackwell.
- United Nations (2015) *Transforming our world: the 2030 Agenda for Sustainable Development*. Available at: https://sdgs.un.org/2030agenda
- Wing, J.M. (2006) 'Computational thinking', *Communications of the ACM*, 49(3), pp. 33-35.
- World Health Organization (2016) *Updated guideline: paediatric emergency triage, assessment and treatment*. Geneva: WHO.

---

*Author: Mohamed Turay (905006574) | PROG101 Assignment 1 | Limkokwing University of Creative Technology, Sierra Leone*
