# 🚀 Cadence - The Open Source Project Management Engine

![Cadence](https://img.shields.io/badge/Cadence-Project%20Management-blue)
![License](https://img.shields.io/badge/License-MIT-green)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Django](https://img.shields.io/badge/Django-4.2%2B-green)

**Cadence is the Open Source project management engine that powers Axiom’s proprietary solutions.** Built on **Django**, it provides a **scalable, secure, and resilient** framework for managing projects, tasks, and team collaboration.


![Cadence is the Open Source project management engine that powers Axiom’s proprietary solutions.](https://github.com/axiomatic7group/cadence/raw/main/assets/cadence_img_hero.jpeg)

---

## **Key Features**

### **1. Role-Based Access Control (RBAC)**
- **Staff**, **Stakeholders**, and **General Users** with granular permissions.
- **Fail-to-Human** security ensures AI agents never overstep their authority.

### **2. Dynamic Task Management**
- **Recurring tasks** (weekly, monthly) with automated status updates.
- **Exclusive task relationships** (tasks belong to either a project or deliverable, not both).
- **Task dependencies** (e.g., `finish-to-start`, `start-to-start`).

### **3. Real-Time Scheduling**
- **APScheduler** integration for automated task status updates.
- **No manual intervention** needed for deadline tracking.

### **4. Secure Collaboration**
- **User-level attribution** ensures AI agents operate with the same security clearance as their human counterparts.
- **Audit logs** track every action for transparency and compliance.

### **5. Open Source & Extensible**
- **Fully customizable** to fit your team’s workflow.
- **API-ready** for third-party integrations.

---

## 🛠 **Tech Stack**
| **Component**       | **Technology**               | **Purpose**                                                                 |
|----------------------|------------------------------|-----------------------------------------------------------------------------|
| **Backend**          | Django (Python)              | Core framework for ORM, authentication, and business logic.                |
| **Database**         | PostgreSQL/SQLite            | Stores all models (users, projects, tasks, etc.).                           |
| **Task Scheduling**  | APScheduler                  | Handles recurring tasks and status updates.                                 |
| **Authentication**   | Django Auth                  | Built-in user authentication with role-based extensions.                    |

---

## 🚀 **Quick Start**

### **1. Clone the Repository**
```bash
git clone https://github.com/axiomatic7group/cadence.git
cd cadence
```

### **2. Install Dependencies**
```bash
pip install -r requirements.txt
```

### **3. Run Migrations**
```bash
python manage.py migrate
```

### **4. Start the Development Server**
```bash
python manage.py runserver
```

### **5. Access the Admin Panel**
```bash
python manage.py createsuperuser
```
Visit `http://127.0.0.1:8000/admin` to manage users, projects, and tasks.

---

## **Why Choose Cadence?**
✅ **Open Source** – Free to use and modify.
✅ **Secure** – User-level attribution ensures no "God Mode" for AI.
✅ **Resilient** – Non-linear process recovery (fix tasks mid-stream).
✅ **Scalable** – Built for teams of all sizes.

---

## **Explore Axiom’s Proprietary Solutions**
Cadence is part of **Axiom**, our **proprietary suite of AI-driven automation tools** designed to bring **common sense back to automation**.

### **Axiom’s Key Layers**
🔹 **Synapse (Governance & Semantic Layer)** – Secure data access and business logic understanding.
🔹 **Cadence (Action Layer)** – Task orchestration with **Surgical Correction**.
🔹 **Daemon (Reasoning Layer)** – A secure AI assistant that doubles as a "second brain."

### **Why Axiom?**
**Deterministic Task Onboarding** – Turn documented processes into autonomous workflows.

**Hierarchical Permissioning** – AI agents operate with the same security clearance as their human counterparts.

**Non-Linear Process Resilience** – Fix tasks mid-stream without restarting the entire workflow.

**[Learn More About Axiom](https://axiomaticlab.com)**

---

## **Join the Community**
**Star this repo** if you find Cadence useful!

**Report bugs** or suggest features via [GitHub Issues](https://github.com/axiomatic7group/cadence/issues).

**Contribute** – Fork, improve, and submit pull requests!

---

## **License**
This project is licensed under the **MIT License** – see [LICENSE](LICENSE) for details.

---

------------------------------

# Axiomatic Lab

Mission: On-boarding AI that eliminates Operational Debt.

### 1. The Challenge: The "Black Box" Risk
Modern enterprises struggle with automation that is either too rigid or dangerously opaque. Standard AI implementations often lack granular security controls, creating a "clearance gap" where automated systems have more access than the employees they assist. Furthermore, when complex automated sequences fail, most systems require a total restart, leading to significant operational downtime.

### 2. The Solution: Task-Based AI Onboarding
Axiomatic Lab treats AI agents like professional hires rather than just software. We automate your business by **"onboarding"** your organizations tasks, notes, and Ai chats, one at a time, alongside your staff all in one platform. Ensuring every automated action, note, and company information is collected, organized, and maintained to ensure your business operates efficiently and strategically.

**Background Knowledge Agents:** Automated background agents that will continously review all provided data from user workflows, notes, and AI chats, to relevant connected databases to create, maintain, and organize your companies operations. Automatically generating and updating Processes and Procedures, Company Guidelines, Client Notes, and much more.

**Security-Level Attribution:** Unlike generic AI, every task within our system is assigned a specific user-security level. This ensures that the AI only interacts with data and systems it is explicitly authorized to access, mimicking your internal organizational hierarchy.

**Dynamic Task Orchestration:** Our modular architecture allows for real-time auditability. Because we build processes task-by-task, our system is uniquely resilient:
-**Surgical Correction:** If an error occurs in step 5 of a 10-step process, you can correct just that specific task or adjust the subsequent steps.
-**Zero Restart Waste:** There is no need to restart the entire workflow from step 1. You save time, compute costs, and manual effort by fixing only what is broken.

### 3. Business Impact & Value
By choosing Axiomatic Lab, your organization gains:
-**Rapid Strategic Growth:** A suistainable platform that ensures your organization remains efficient and operationally sound as you scale Fast!
-**Total Oversight:** A transparent, auditable trail for every automated action.
-**Risk Mitigation:** Granular permissions that eliminate unauthorized data access.
-**Operational Agility:** The ability to modify and "hot-fix" live automations without process disruption.

### 4. Next Steps
We recommend a Phase 1 Pilot to identify your **"obvious" automation wins.**

**Discovery Call:** Review your most repetitive, high-margin tasks.

**Prototype:** Deploy a secure task-based agent within 90 days.

---

### **Join the Waitlist today: [axiomaticlab.com](https://axiomaticlab.com/)**

## **Contact Us**
[Axiomatic Lab Website](https://axiomaticlab.com)
[YouTube Channel](https://www.youtube.com/channel/UCltGi4Su305oln_ldu-b94Q)
[LinkedIn](https://www.linkedin.com/company/axiomatic-lab/)
