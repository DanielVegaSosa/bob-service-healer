# Infrastructure Service Persistence & Self-Healing Agent

An automated utility built with the assistance of **IBM Bob** as an AI SDLC partner to audit, repair, and guarantee the cold-start availability of critical web tier daemons (`httpd` / `apache2`) across enterprise application server environments.

---

## 📋 1. Problem Statement and Solution

### Problem Statement
Following scheduled operating system reboots or unplanned server maintenance restarts, critical web tier daemons (such as Apache HTTP Server / `httpd`) fail to initialize automatically. This lack of service persistence introduces extended system downtime, severely breaks operational SLAs, and forces infrastructure and middleware teams to execute manual operational interventions (`systemctl start`) to restore application-layer availability across enterprise environments.

### Solution
We utilized **IBM Bob** as our AI SDLC partner to rapidly design, develop, and deploy an automated **Infrastructure Service Persistence & Self-Healing Agent**. Leveraging Bob's advanced structural scaffolding and multi-line code generation capabilities, we built a secure Python utility that automatically inspects target `systemd` unit files, corrects missing boot-time configurations (`systemctl enable`), and monitors post-reboot process environments. If a web service fails to bind due to transient, boot-time dependencies (such as delayed network interface initialization), the agent triggers an intelligent, exponential back-off retry loop to guarantee web server recovery without human intervention.

---

## 🛠️ 2. Production Code Core (`service_healer.py`)

The repository includes a decoupled administrative pipeline engineered to run as an independent validation engine. It encapsulates the following design paradigms:
* **Safe Subprocess Execution:** Avoids raw shell parsing vectors to eliminate shell-injection risks.
* **Resilient Retry Mechanics:** Incorporates a state-machine verification structure using localized delays.
* **Enterprise Logging Hierarchy:** Implements comprehensive logging states for infrastructure monitoring tool integration.

---

## 🚀 3. Prompt and Bob Usage Documentation

### Step 1: Framework Scaffolding ('Create files and projects')
* **What we did:** We used Bob to establish a clean, modular project layout optimized for secure system interactions.
* **Prompt used in Bob:** `"Bob, scaffold a clean Python administrative script designed to safely interface with Linux systemd units. Include configurations for monitoring specific service strings like 'httpd' and 'apache2'."`
* **Bob Usage Impact:** Bob immediately generated the operational skeleton, pre-configuring array-based subprocess bindings and structural logging layouts, removing initial setup overhead.

### Step 2: Core Remediation Logic ('Generate code')
* **What we did:** We leveraged Bob's multi-line code generation to compose the `systemctl` lookup and configuration recovery blocks.
* **Prompt used in Bob:** `"Bob, write a high-performance function that uses systemctl to verify if a unit is enabled on startup. If it returns disabled, trigger the enablement sequence and capture any missing privileges or exception blocks cleanly."`
* **Bob Usage Impact:** Bob engineered pristine, validation-heavy logic utilizing safe, programmatic bindings, drastically reducing standard coding cycles.

### Step 3: Edge Case Resiliency ('Refactor and debug')
* **What we did:** We utilized Bob's refactoring assistant to address the transient initialization issue where services crash during early boot sequences.
* **Prompt used in Bob:** `"Bob, refactor this execution check to build an exponential back-off loop. If a service fails to stay active initially due to socket delays, retry up to 3 times before scaling to a critical infrastructure alert."`
* **Bob Usage Impact:** Bob quickly transformed a linear check script into a rugged, enterprise-ready recovery agent, successfully minimizing complexity markers tracked in **Bobalytics**.

---

## 💬 4. Feedback on Usage of the Prompt

* **Feedback Lead Architect:**
> "IBM Bob served as an outstanding SDLC velocity accelerator. Turning complex infrastructure persistence behaviors into structured, safe automation scripts took us minutes instead of a full day of scripting. Reviewing our metric trends via Bobalytics confirmed that leveraging Bob drastically minimizes initial prototyping and troubleshooting latency."

* **Feedback Systems Engineer:**
> "The IDE integration for multi-line autocompletions allowed me to map OS-level subprocess interactions smoothly without stumbling over syntax errors. Bob's automated debugging engine caught an unhandled unit-missing exception on the first run, allowing us to hit this urgent delivery deadline with zero technical debt."
