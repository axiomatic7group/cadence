# **Project Documentation: Django Task & Project Management System**

---

## **1. Overview**
This **Django-based Task and Project Management System** is designed to streamline project planning, task delegation, and team collaboration. Built with **Django’s ORM**, **ModelForms**, and **APScheduler**, the system provides a robust framework for managing projects, deliverables, tasks, and user interactions. It includes features for **real-time task scheduling**, **role-based access control**, and **automated status updates**, making it ideal for teams requiring structured workflow management.

---

## **2. Core Features**

### **2.1 User Management**
- **User Roles**:
  - `staff` (Project Managers)
  - `stakeholder` (Clients/Investors)
  - `other` (General Users)
- **Authentication**:
  - Django’s built-in `User` model extension via `user_info` (OneToOneField).
  - Custom validation to restrict roles (e.g., only `staff` can manage projects).
- **User-Specific Dashboards**:
  - Staff users see project overviews.
  - Stakeholders receive deliverable updates.

**Reference**:
- [Django Custom User Models](https://docs.djangoproject.com/en/4.2/topics/auth/customizing/#extending-the-existing-user-model)

---

### **2.2 Project & Deliverable Management**
- **Projects**:
  - Defined by `project_name` (primary key) and `project_description`.
  - Assigned to a **Project Manager (`pm_owner`)**.
  - Grouped via `project_group` for categorization.
- **Deliverables**:
  - Linked to projects (`deliverable_project`).
  - Grouped via `deliverable_group`.
  - Stakeholders can be assigned to deliverables (`deliverable_stakeholder`).

**Unique Feature**:
- **Dynamic Project Filtering**: Non-superusers can only delete their own projects (enforced in `delete_project_f` form).

**Reference**:
- [Django ForeignKey](https://docs.djangoproject.com/en/4.2/ref/models/fields/#django.db.models.ForeignKey)

---

### **2.3 Task Management**
- **Task Creation**:
  - Tasks can belong to either a **project** or a **deliverable** (exclusive relationship enforced via `CheckConstraint`).
  - Fields:
    - `task_name`, `task_description`
    - `start_date`, `soft_due_date`, `hard_due_date`
    - `task_status` (e.g., `completed`, `in_progress`)
    - `task_schedule` (e.g., `one_time`, `repeat_wkly`)
- **Task Dependencies**:
  - Defined via `task_prerequisite` with relationship types (e.g., `start-to-start`).
- **Task Assignments**:
  - Staff users assigned via `task_staff`.
  - Stakeholders can view but not modify tasks.

**Unique Feature**:
- **Recurring Tasks**: Supported via `task_schedule` (e.g., weekly reports).

**Reference**:
- [Django Model Constraints](https://docs.djangoproject.com/en/4.2/ref/models/constraints/)

---

### **2.4 Real-Time Scheduling & Status Updates**
- **APScheduler Integration**:
  - Automatically checks task statuses (`new_task_add_to_scheduler`).
  - Updates statuses based on dates (e.g., `late`, `completed`).
- **Notifications**:
  - System messages (`user_messages`) for urgent updates (e.g., `SOS`, `urgent`).

**Unique Feature**:
- **Automated Status Tracking**: No manual intervention needed for deadline-based status changes.

**Reference**:
- [APScheduler Documentation](https://apscheduler.readthedocs.io/)

---

### **2.5 Communication & Collaboration**
- **Task Comments**:
  - Stored via `task_comments` with metadata (e.g., `User`, `API`, `Other`).
- **File Attachments**:
  - Supports task-related files (`task_attachement`).
- **Messaging System**:
  - `user_messages` for system-wide or role-specific communications.

**Unique Feature**:
- **Comment Types**: Differentiates between user comments and system-generated messages.

---

### **2.6 Role-Based Access Control (RBAC)**
- **Permissions**:
  - **Staff Users**: Can create/edit projects, tasks, and assign staff.
  - **Stakeholders**: Can view deliverables and tasks but cannot modify them.
  - **Superusers**: Full access (e.g., `delete_project_f` for all projects).

**Reference**:
- [Django Permissions](https://docs.djangoproject.com/en/4.2/topics/auth/default/#permissions-and-authorization)

---

## **3. Technical Specifications**

### **3.1 Tech Stack**
| **Component**       | **Technology**               | **Purpose**                                                                 |
|----------------------|------------------------------|-----------------------------------------------------------------------------|
| **Backend**          | Django (Python)              | Core framework for ORM, authentication, and business logic.                |
| **Frontend**         | Django Templates             | Renders forms and data (assumed, no React/Next.js in context).              |
| **Database**         | PostgreSQL (or SQLite)       | Stores all models (users, projects, tasks, etc.).                           |
| **Task Scheduling**  | APScheduler                  | Handles recurring tasks and status updates.                                 |
| **File Storage**     | Django `FileField`/`ImageField** | Manages task attachments and user uploads.                              |
| **Authentication**   | Django Auth                  | Built-in user authentication with role-based extensions.                    |
| **Admin Interface**  | Django Admin                 | Default admin panel for data management (assumed, not customized).          |

**Unique Technical Choices**:
1. **Exclusive Task Relationships**:
   - Tasks **cannot** belong to both a project and a deliverable simultaneously (enforced via `CheckConstraint`).
2. **Dynamic Form Querysets**:
   - Forms like `delete_project_f` filter options based on the logged-in user (e.g., non-superusers only see their own projects).
3. **Beta Features**:
   - Superuser-specific forms (e.g., `add_task_comments_super`) suggest phased rollouts.

---

### **3.2 Database Schema**
Key models and relationships:
1. **`user_info`** → Extends Django’s `User` model (OneToOneField).
2. **`project`** → Owned by a `user_info` (Project Manager).
3. **`deliverable`** → Linked to a `project` and can have stakeholders.
4. **`task`** → Belongs to either a `project` or `deliverable` (exclusive).
5. **`task_staff`** → Assigns staff to tasks (validates `user_type='staff'`).
6. **`task_prerequisite`** → Defines task dependencies (e.g., `finish-to-start`).

**Schema Visualization**:
```
User_info (staff/stakeholder)
   │
   ├── Project (pm_owner)
   │    │
   │    ├── Deliverable (deliverable_project)
   │    │    │
   │    │    └── Task (task_deliverable)
   │    │
   │    └── Task (task_project)
   │
   └── Task (task_project or task_deliverable)
        │
        ├── Task_Staff (staff assignments)
        ├── Task_Comments (user/system comments)
        └── Task_Attachement (files)
```

**Reference**:
- [Django Model Relationships](https://docs.djangoproject.com/en/4.2/topics/db/models/#relationships)

---

### **3.3 Key Django Features Used**
| **Feature**               | **Usage**                                                                 |
|---------------------------|---------------------------------------------------------------------------|
| **ModelForms**            | Simplifies CRUD operations (e.g., `create_new_tasks`, `add_new_users`).  |
| **ForeignKey**            | Links models (e.g., `task_project` → `project`).                          |
| **CheckConstraint**       | Enforces business rules (e.g., tasks cannot belong to both project and deliverable). |
| **OneToOneField**         | Extends Django’s `User` model (`user_info`).                              |
| **APScheduler**           | Automates task scheduling and status updates.                            |
| **Django Admin**          | Default interface for data management (assumed, not customized).         |

---

### **3.4 Performance Optimizations**
1. **Database Indexing**:
   - Assumed for frequently queried fields (e.g., `project_name`, `task_status`).
2. **Efficient Queries**:
   - Django ORM’s `select_related`/`prefetch_related` likely used in views (e.g., fetching tasks with their assignments).


**Reference**:
- [Django Database Optimization](https://docs.djangoproject.com/en/4.2/topics/db/optimization/)

---

## **4. Project Structure**
```
project_root/
│
├── manage.py                  # Django management script
├── requirements.txt           # Python dependencies
│
├── main/                      # Main Django app
│   ├── models.py              # Database schema (user_info, project, task, etc.)
│   ├── forms.py               # ModelForms for CRUD operations
│   ├── views.py               # Handles HTTP requests/responses
│   ├── urls.py                # URL routing
│   └── admin.py               # Admin panel customization (assumed)
│
├── templates/                 # Frontend templates (assumed)
│   ├── base.html              # Base template
│   ├── pm/                    # Project Manager views
│   └── stakeholder/           # Stakeholder views
│
└── static/                    # CSS/JS files (assumed)
```

---

## **5. Workflow Examples**

### **5.1 Creating a Project**
1. **User Action**: Staff user submits `create_new_projects` form.
2. **Validation**: Form checks if `pm_owner` is a staff user.
3. **Database**: New `project` record created.
4. **Response**: Redirect to project dashboard.

### **5.2 Assigning a Task**
1. **User Action**: Staff user submits `add_staff_to_task` form.
2. **Validation**: Form checks if `user_type='staff'`.
3. **Database**: New `task_staff` record created.
4. **Response**: Task dashboard updated with assignment.

### **5.3 Real-Time Status Update**
1. **Trigger**: APScheduler runs `check_task_status` every hour.
2. **Logic**:
   - If `hard_due_date` < today → status = `late`.
   - If `task_status='completed'` → mark as `done`.
3. **Notification**: System sends `user_messages` to stakeholders.


---

## **6. Future Enhancements**
1. **API Endpoints**:
   - Add REST/GraphQL APIs for third-party integrations.
2. **Webhooks**:
   - Notify external systems (e.g., Slack) on task status changes.
3. **Advanced Analytics**:
   - Track project completion rates, task bottlenecks.
4. **Mobile App**:
   - Django REST Framework + React Native for cross-platform access.
5. **AI-Powered Suggestions**:
   - Recommend task priorities based on deadlines and dependencies.

---

## **9. Known Limitations**
1. **Limited Frontend**:
   - No React/Next.js integration (assumed Django templates only).
2. **No Caching**:
   - Dashboard data could benefit from Redis caching.
3. **Hardcoded User Roles**:
   - Adding new roles requires code changes (consider a `Role` model).

---

## **9. References & Resources**
- [Django Official Documentation](https://docs.djangoproject.com/en/4.2/)
- [APScheduler Documentation](https://apscheduler.readthedocs.io/)
- [Django ModelForms](https://docs.djangoproject.com/en/4.2/topics/forms/modelforms/)
- [Django Model Constraints](https://docs.djangoproject.com/en/4.2/ref/models/constraints/)

---

## **10. Appendix: Sample Code Snippets**
### **10.1 Model Definition (tasks)**
```python
# models.py
from django.db import models
from django.core.validators import MinValueValidator

class task(models.Model):
    task_name = models.CharField(max_length=200)
    task_description = models.TextField(blank=True)
    start_date = models.DateField()
    soft_due_date = models.DateField(null=True, blank=True)
    hard_due_date = models.DateField()
    task_status = models.CharField(
        max_length=20,
        choices=[
            ('not_started', 'Not Started'),
            ('in_progress', 'In Progress'),
            ('completed', 'Completed'),
            ('late', 'Late'),
        ],
        default='not_started'
    )
    task_schedule = models.CharField(
        max_length=20,
        choices=[
            ('one_time', 'One Time'),
            ('repeat_wkly', 'Repeat Weekly'),
            ('repeat_mnthly', 'Repeat Monthly'),
        ],
        default='one_time'
    )
    task_project = models.ForeignKey(
        'project',
        on_delete=models.CASCADE,
        null=True,
        blank=True,
        related_name='tasks'
    )
    task_deliverable = models.ForeignKey(
        'deliverable',
        on_delete=models.CASCADE,
        null=True,
        blank=True,
        related_name='tasks'
    )

    class Meta:
        constraints = [
            models.CheckConstraint(
                check=(
                    models.Q(task_project__isnull=True) |
                    models.Q(task_deliverable__isnull=True)
                ),
                name="task_exclusive_relationship"
            )
        ]
```

### **10.2 Form Definition (create tasks)**
```python
# forms.py
from django import forms
from .models import task, project, deliverable

class create_new_tasks(forms.ModelForm):
    class Meta:
        model = task
        fields = ['task_name', 'task_description', 'start_date',
                  'soft_due_date', 'hard_due_date', 'task_status', 'task_schedule']
        widgets = {
            'start_date': forms.DateInput(attrs={'type': 'date'}),
            'soft_due_date': forms.DateInput(attrs={'type': 'date'}),
            'hard_due_date': forms.DateInput(attrs={'type': 'date'}),
        }

    def clean(self):
        cleaned_data = super().clean()
        task_project = cleaned_data.get('task_project')
        task_deliverable = cleaned_data.get('task_deliverable')
        if task_project and task_deliverable:
            raise forms.ValidationError("A task can belong to either a project or a deliverable, not both.")
        return cleaned_data
```

### **10.3 View Definition (create tasks)**
```python
# views.py
from django.shortcuts import render, redirect
from .forms import create_new_tasks
from .models import task

def create_tasks(request):
    if request.method == 'POST':
        form = create_new_tasks(request.POST)
        if form.is_valid():
            task_obj = form.save(commit=False)
            task_obj.save()
            return redirect('task_dashboard')
    else:
        form = create_new_tasks()
    return render(request, 'pm/create_tasks.html', {'form': form})
```

---

## **11. Conclusion**
This **Django Task and Project Management System** is a **scalable, role-based platform** for organizing projects, tasks, and team collaboration. Its **unique features**—such as **exclusive task relationships**, **APScheduler integration**, and **dynamic form validation**—set it apart from generic project management tools. With **minimal frontend assumptions** (Django templates) and a **focus on backend logic**, it’s ideal for teams prioritizing **structure and automation**.

**Next Steps**:
1. Deploy a staging environment.
2. Gather user feedback.
3. Iterate on features (e.g., API endpoints, mobile support).

---
**Document Control**:
| **Version** | **Date**       | **Author**  | **Changes**                          |
|-------------|----------------|-------------|--------------------------------------|
| 0.0         | May 2026 | Axiomatic Lab | Initial documentation.               |