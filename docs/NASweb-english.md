# English

## 1. Introduction

**NASwebio** is a modern building security & automation controller with the embedded **NASweb** web application.  

It unifies functions typically provided by several separate devices: 

- access control unit  
- intrusion alarm (SSWiN) controller  
- automation module (e.g. HVAC)  
- event recorder with image linkage  
- notification and external integrations  

!!! question ""
    One device replaces many systems, simplifying installation and reducing costs.

---

## 2. System Synergy  1 + 1 = 3

The key advantage of NASwebio is **synergy** - combining functions yields more than the sum of parts.

### Example 1: Alarm + Access Control

**Separately**

- alarm protects the site, access control lets only authorized people in

**Together**

  - a card both opens the door and **arms/disarms a zone**  
  - card access can be **blocked** while a zone is armed  
  - automatic arming when the last user leaves a zone  

!!! success "Result"
    Fewer mistakes, higher security, less intervention.

### Example 2: HVAC & environmental control
- Temperature sensors drive relays in **three states**:  

    - **below range** - (e.g.) heating  
    - **within range** - (e.g.) ventilation  
    - **above range** - (e.g.) cooling  

!!! info "Relay outputs"
    For **each state**, you select **exactly one** relay output (it may be the same relay used in different states).   
    If you need to activate **multiple** outputs in the same state (e.g., ventilation and cooling at the same time), use a script or an external splitter/relay module.

!!! example "Example"
    In the *Warehouse* zone, the controller activates **ventilation** in 20–28 °C (the “within” state).   
    Once temperature exceeds 28 °C, control switches to the relay assigned to the “above” state (e.g. **cooling**).  

!!! success "Result"
    Stable conditions and energy efficiency.

### Example 3: Events + images

- Any event (e.g. card read, sensor trigger) can be linked with a camera snapshot  
- The admin sees: *John Doe opened the door at 10:05* + **the picture**  

!!! success "Result"
    Faster verification and response.

---

## 3. System Architecture

### 3.1. User Interface

- accessible from any modern browser (PC/tablet/phone)  
- roles:  

    - **operator** - logs in and manages the system  
    - **user** - uses cards/PINs at access points  

### 3.2. System Components

- 16 digital inputs  
- 6 relay outputs 2 A @ 12 VDC  
- 1-Wire sensors (temperature/humidity)  
- up to 4 RS-485 readers (OSDP)  
- up to 4 cameras (snapshot/ANPR)  
- GSM module (SMS control & alerts)  
- HTTP/HTTPS server (local & cloud)  
- TCP/IP broadcasting (real-time events)

---

## 4. Dashboard & NASweb app

<img width="1584" alt="Dashboard" src="https://github.com/user-attachments/assets/02bea178-1be1-4528-ada9-543a9612fea4" />  
📷 **Dashboard**

---

## 5. Access Control - Basics

### 5.1. Definition
Access control decides **who, when, where** may enter.  
Replacing keys with cards, PINs, biometrics, license plates.

### 5.2. How NASweb works

- a user is assigned **identifiers** (card, PIN, plate)  
- the operator builds **permission templates** – access points with schedules and conditions 
- a user may have multiple templates and additional **individual** rights

#### Inheritance, accumulation, and denial

- The system **accumulates rights (logical OR)** from templates and individual grants – the user gets **all** accesses granted by **any** source  
- **Denial (revocation)** acts like a “grant with the opposite sign”: it **removes** access even if granted elsewhere  

- **Conflict priorities:**  
    1) **Denial > grant** (denial wins)   
    2) **Individual > template** (individual rights are superior)    
    3) Schedule: access is active when **at least one** source is active (unless a denial is active at that time)

!!! example "Denial example" 
    The “Employees” group has Server Room access, but one user gets an **individual denial** on that door – result: **everyone has** access, **except that user**.

<img width="1180" alt="User edit" src="https://github.com/user-attachments/assets/cc01d60a-d9d2-4656-847d-c98ac232f87a" />  
📷 **User editing**

<img width="1479" alt="Template config" src="https://github.com/user-attachments/assets/3cfca29f-a443-4785-95c4-d3eb43f93ed0" />  
📷 **Permission template configuration**

---

## 6. Intrusion Alarm (SSWiN)

### 6.1. Definition
SSWiN monitors sensors (motion, door contacts).  
On violation - triggers alarm and notifies.

### 6.2. In NASweb
- inputs are assigned to **zones** (e.g. office, warehouse)  
- zones armed/disarmed by card  
- outputs drive sirens & automation 
- integrated with AC: entry via card can disarm the zone

<img width="1424" alt="Input config" src="https://github.com/user-attachments/assets/b95df204-3a53-49bc-9c1f-cd022b3c3b29" />  
📷 **Input configuration**

---

<img width="1345" alt="Zone config 1" src="https://github.com/user-attachments/assets/c10dadea-1bf7-447d-9484-ff077551bdb1" />  
📷 **Zone configuration**

<img width="1364" alt="Zone config 2" src="https://github.com/user-attachments/assets/375c8b04-1329-4aa5-970d-9492a88bc34d" />  
📷 **Zone configuration (detailed)**

---

## 7. Automation & HVAC

- 1-Wire temperature sensor  
- **three states** with exactly **one** relay per state:  

    - below range - (e.g.) heating  
    - within range - (e.g.) ventilation  
    - above range - (e.g.) cooling  

!!! warning "Relays"
    The **same relay** may be used across different states if desired.  
    If you need **multiple relays** simultaneously for one state, use **scripts** or an external coupler.

!!! example "Example"
    *Warehouse* zone - ventilation in 20–28 °C; above 28 °C, control switches to the “above” state relay (cooling).  

<img width="1178" alt="HVAC config" src="https://github.com/user-attachments/assets/9cc6816a-d7f5-4848-abed-ca9bfba9cb13" />  
📷 **HVAC configuration**

---

## 8. Video & recording

<img width="1238" alt="Cameras / Campics" src="https://github.com/user-attachments/assets/5cba6870-c2ca-4372-b5fe-0f38b9b68e50" />  
📷 **Cameras / Campics**

- events linked to snapshots (*Campics*)  
- **ANPR** support  
- filtering and quick verification

---

## 9. Notifications - key events

Top 15 for homes/offices:  

1. Authorized entry  
2. Authorized exit  
3. Unauthorized attempt  
4. Door open too long  
5. Exit button pressed  
6. Alarm in zone  
7. Zone disarmed  
8. Reader tamper  
9. Input tamper  
10. Detector fault  
11. Sensor violation  
12. AC power fail  
13. Battery fail  
14. No server response  
15. Wrong PIN  

<img width="1266" alt="Notification config 1" src="https://github.com/user-attachments/assets/2d6e72f0-260c-4197-93dd-5eb922a2cfca" />  
📷 **Notification configuration**

<img width="1634" alt="Notification config 2" src="https://github.com/user-attachments/assets/4e862005-9564-4208-9bea-6dcca9b6818e" />  
📷 **Notification configuration (details)**

---

## 10. Integration

- LDAP sync  
- haos.app  
- TCP/IP event export  
- Home Assistant

---

## 11. Scripts & logic

Script engine (`JavaScript-like`):  

- custom reactions to events (sensor → outputs)  
- mantrap logic (door A opens only if B is closed)  
- time-based rules (e.g. after 22:00 PIN required)  
- inter-module links (card use → automation output)  
- **HVAC extensions** (drive multiple relays for one state)  
- custom project scenarios without external programming

---

## 12. Project applications

- entry/exit checkpoint with **ANPR**  
- load photo records 
- time-limited transport permissions  

<img width="1382" alt="Checkpoint" src="https://github.com/user-attachments/assets/db768285-0aa8-4442-bb9e-d924617de6f9" />  
📷 **Checkpoint application**

---

## 13. Admin panel
- networking  
- updates  
- diagnostics

---

## 14. Technical specs

| Parameter        | Value                                         |
|------------------|-----------------------------------------------|
| CPU              | ARM Quad-Core                                |
| RAM              | 4 GB                                          |
| Storage          | 32 GB eMMC                                   |
| Display          | 1.4’’                                         |
| Buttons          | 4                                             |
| Network          | 1× uplink FE (PoE+), 2× downlink FE          |
| Power            | 12 VDC + PoE+ (redundant, parallel)          |
| Enclosure        | DIN rail, 10 modules                         |
| Terminals        | Detachable                                   |
| USB              | storage/peripherals                          |
| Relay outputs    | 6× (2A @ 12VDC)                              |
| Digital inputs   | 16×                                           |
| Readers          | up to 4 (RS-485 OSDP)                        |
| Cameras          | up to 4 (snapshot/ANPR)                      |
| Power output     | relay for reset                              |
| OS               | Embedded Linux                               |
| Cloud            | VPN to haos.app                              |
| Home Assistant   | zones, inputs, outputs, thermostat           |
| Extra apps       | checkpoint/ANPR                              |
| OEM/ODM          | customization for volume                     |
| Variants         | versions with different I/O & housings       |

!!! info "Redundant power"
    Two independent sources (PoE+ and 12 VDC) can be connected simultaneously - disconnecting one **does not interrupt operation**.  
    Benefit over single-supply: higher reliability without extra UPS/adapters in small sites.

---

## 15. Summary

!!! quote ""
    **NASwebio + NASweb** = security + automation + monitoring  

!!! success ""
    Lower cost, higher safety, unified control.

---

## 16. haos.app Variant – eco optimization

NASwebio also available as **haos.app**:  

- full security controller  
- Home Assistant host  
- built-in switch  
- redundant supply  
- SOHO automation host 

### Advantages

- **all-in-one DIN device**  
- **space saving** - one instead of 3-4  
- **lower energy & heat**  
- **lower cost**  
- **eco-friendly** - fewer materials, lower footprint  

<img width="1500" alt="HAOS 1" src="https://github.com/user-attachments/assets/c1a6d8ba-f9d2-4d24-92b4-20bf02450188" />  
📷 **NASwebio with HAOS**

<img width="1245" alt="HAOS 2" src="https://github.com/user-attachments/assets/3e15c1bb-6942-46fc-b46c-b39cc66199e9" />  
📷 **haos.app variant**

---

## 17. Final notes

- Also available in a Tuya-supporting version  
- Logos (Tuya, Home Assistant) belong to their creators and are shown for information only
