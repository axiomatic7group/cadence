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

# Axiomatic Lab 

Early-stage startups don't just need fractional C-suite advice, they need a reliable operational backbone that can scale fast. 

Most companies hit a chaotic friction point when they hit hyper-scale growth and outgrow their founding team and begin to hire in-house experienced executives.

Tribal knowledge is lost, systems break, and, worst of all, growth stalls.

At Axiom AI, we solve this by blending expert fractional leadership with custom AI software curation. We don’t just give you a strategic roadmap for fast growth; We embed the AI tools, prompts, and automations into your daily workflows from day one.

As you scale, our software acts as the institutional memory of your company, making the eventual hand-off to your full-time, in-house hires seamless, documented, and hyper-efficient.

### How we support early-stage founders:

 * **Fractional C-Suite:** Hands-on strategy across Finance (CFO), Go-To-Market (CMO), and Operations/Execution (COO/Chief of Staff).

 * **AI Operational Roadmaps:** Designing the exact tech stack you need to stay lean while growing rapidly.

 * **The Software Hand-Off:** Curating and configuring AI systems during our tenure so your future in-house hires inherit an optimized, automated machine.


If you are an early-stage founder looking to build a high-growth, AI-leveraged organization without the overhead of immediate full-time executive hires, let’s talk.

## **Contact Us**
[Axiomatic Lab Website](https://axiomaticlab.com)
[YouTube Channel](https://www.youtube.com/channel/UCltGi4Su305oln_ldu-b94Q)
[LinkedIn](https://www.linkedin.com/company/axiomatic-lab/)
