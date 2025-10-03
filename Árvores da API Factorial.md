# Factorial API Object Relationships

## 🏗️ **Complete API Architecture Overview**

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                              FACTORIAL API ECOSYSTEM                              │
│                              Version: 2025-07-01                                  │
└─────────────────────────────────────────────────────────────────────────────────────┘

                                    COMPANY (Root Entity)
                                           │
                                           │ company_id
                                           │
                    ┌──────────────────────┼──────────────────────┐
                    │                      │                      │
                    ▼                      ▼                      ▼
            ┌──────────────┐      ┌──────────────┐      ┌──────────────┐
            │   ATS        │      │  EMPLOYEES   │      │  ATTENDANCE  │
            │  SYSTEM      │      │  MANAGEMENT  │      │  MANAGEMENT  │
            └──────────────┘      └──────────────┘      └──────────────┘
                    │                      │                      │
                    │                      │                      │
        ┌───────────┼───────────┐         │         ┌─────────────┼─────────────┐
        │           │           │         │         │             │             │
        ▼           ▼           ▼         ▼         ▼             ▼             ▼
┌─────────────┐ ┌─────────┐ ┌─────────┐ │   ┌─────────────┐ ┌─────────┐ ┌─────────┐
│Job Postings │ │Candidates│ │Applications│ │   │   Employees  │ │ Shifts  │ │ Breaks  │
│             │ │         │ │           │ │   │             │ │         │ │         │
└─────────────┘ └─────────┘ └─────────┘ │   └─────────────┘ └─────────┘ └─────────┘
        │           │           │         │         │             │             │
        │           │           │         │         │             │             │
        └───────────┼───────────┘         │         └─────────────┼─────────────┘
                    │                     │                       │
                    │                     │                       │
            ┌───────┼───────┐             │               ┌───────┼───────┐
            │       │       │             │               │       │       │
            ▼       ▼       ▼             ▼               ▼       ▼       ▼
    ┌─────────┐ ┌─────┐ ┌─────┐   ┌─────────────┐ ┌─────────┐ ┌─────┐ ┌─────┐
    │Phases   │ │Conv.│ │Rej. │   │  Contracts  │ │Time Off │ │Overt│ │Holid│
    │         │ │     │ │Reas.│   │             │ │         │ │     │ │     │
    └─────────┘ └─────┘ └─────┘   └──────── ─────┘ └─────────┘ └─────┘ └─────┘

                    │                      │                      │
                    │                      │                      │
        ┌───────────┼───────────┐         │         ┌─────────────┼─────────────┐
        │           │           │         │         │             │             │
        ▼           ▼           ▼         ▼         ▼             ▼             ▼
┌─────────────┐ ┌─────────┐ ┌─────────┐ │   ┌─────────────┐ ┌─────────┐ ┌─────────┐
│PERFORMANCE  │ │ DOCUMENTS│ │ CUSTOM  │ │   │   PAYROLL   │ │ FINANCE │ │ TEAMS   │
│MANAGEMENT   │ │          │ │RESOURCES│ │   │             │ │         │ │         │
└─────────────┘ └─────────┘ └─────────┘ │   └─────────────┘ └─────────┘ └─────────┘
        │           │           │         │         │             │             │
        │           │           │         │         │             │             │
        └───────────┼───────────┘         │         └─────────────┼─────────────┘
                    │                     │                       │
                    │                     │                       │
            ┌───────┼───────┐             │               ┌───────┼───────┐
            │       │       │             │               │       │       │
            ▼       ▼       ▼             ▼               ▼       ▼       ▼
    ┌─────────┐ ┌─────┐ ┌─────┐   ┌─────────────┐ ┌─────────┐ ┌─────┐ ┌─────┐
    │Reviews  │ │Files│ │Schemas│ │  Cost Ctrs  │ │Supplem. │ │Bank │ │Proj.│
    │         │ │     │ │       │ │             │ │         │ │     │ │     │
    └─────────┘ └─────┘ └───────┘ └─────────────┘ └─────────┘ └─────┘ └─────┘
```

## 🔗 **Detailed Relationship Mappings**

### **1. ATS (Applicant Tracking System)**
```
Company
  └── ATS Job Postings (ats_job_posting_id)
      ├── ATS Applications (ats_application)
      │   ├── ATS Candidates (ats_candidate_id)
      │   ├── ATS Application Phases (ats_application_phase_id)
      │   ├── ATS Conversations (ats_conversation_id)
      │   ├── ATS Rejection Reasons (ats_rejection_reason_id)
      │   └── Sources (source_id)
      └── ATS Application Phases
          └── ATS Applications
```

### **2. Employee Management**
```
Company
  └── Employees (employee_id)
      ├── Contracts
      │   ├── Contract Changes
      │   └── Policy Timelines
      ├── Personal Information
      ├── Terminations
      └── New Hires
```

### **3. Attendance Management**
```
Company
  └── Employees (employee_id)
      ├── Shifts
      │   ├── Clock In/Out Events
      │   ├── Breaks
      │   └── Overtime
      ├── Work Schedules
      ├── Estimated Times
      └── Bank Holidays
```

### **4. Performance Management**
```
Company
  └── Employees (employee_id)
      ├── Review Processes
      │   ├── Employee Scores
      │   └── Score Scales
      └── Performance Agreements
```

### **5. Time Off Management**
```
Company
  ├── Leave Policies
  │   └── Employee Leaves (employee_id)
  ├── Blocked Periods
  └── Leave Requests
```

### **6. Document Management**
```
Company
  ├── Documents
  │   ├── Files
  │   ├── Folders
  │   └── Download URLs
  └── Document Events
```

### **7. Payroll & Finance**
```
Company
  ├── Cost Centers
  ├── Supplements
  ├── Banking Information
  └── Payroll Employees
```

### **8. Team Management**
```
Company
  ├── Teams
  │   ├── Team Members
  │   └── Team Projects
  └── Team Events
```

## 🔄 **Key Relationship Types**

### **One-to-Many Relationships:**
- **Company → Employees** (1 company has many employees)
- **Company → Job Postings** (1 company has many job postings)
- **Job Posting → Applications** (1 job posting has many applications)
- **Candidate → Applications** (1 candidate can have many applications)
- **Employee → Shifts** (1 employee has many shifts)
- **Employee → Contracts** (1 employee can have multiple contracts over time)

### **Many-to-Many Relationships:**
- **Applications ↔ Application Phases** (applications move through phases)
- **Employees ↔ Teams** (employees can belong to multiple teams)
- **Documents ↔ Employees** (documents can be associated with multiple employees)

### **Hierarchical Relationships:**
- **Company → Departments → Teams → Employees**
- **Company → Cost Centers → Employees**
- **Company → Leave Policies → Employee Leaves**

## 📊 **Data Flow Patterns**

### **ATS Pipeline:**
```
Job Posting Created → Candidate Applies → Application Created → 
Application Moved Through Phases → Hired (becomes Employee) OR Rejected
```

### **Employee Lifecycle:**
```
Candidate → Application → Hired → Contract → Performance Reviews → 
Time Off → Attendance Tracking → Termination (if applicable)
```

### **Document Workflow:**
```
Document Created → Associated with Employee/Team → 
Download URLs Generated → Document Events Tracked
```

## 🌐 **Webhook Integration Points**

### **Real-time Notifications:**
- **ATS Events**: Application create/update/delete, candidate create/update
- **Employee Events**: Hire, update, terminate, contract changes
- **Attendance Events**: Clock in/out, break start/end, shift changes
- **Performance Events**: Review process start/stop, score updates
- **Time Off Events**: Leave request create/approve/reject
- **Document Events**: File create/update, download URL generation

## 🔑 **Foreign Key Relationships**

### **Core IDs Used Across Resources:**
- `company_id` - Links everything to a company
- `employee_id` - Links employee-related resources
- `ats_job_posting_id` - Links ATS resources
- `ats_candidate_id` - Links candidate-related resources
- `ats_application_id` - Links application-related resources
- `ats_application_phase_id` - Links to application workflow stages

## 💡 **Integration Patterns**

### **1. Cross-Resource Queries:**
- Get all applications for a specific job posting
- Get all shifts for a specific employee in a date range
- Get all documents associated with a specific team

### **2. Workflow Tracking:**
- Track candidate from application to hire
- Monitor employee performance through review cycles
- Track time off requests through approval workflow

### **3. Reporting & Analytics:**
- Company-wide hiring metrics
- Employee attendance patterns
- Performance review statistics
- Time off utilization rates

This architecture provides a comprehensive HR management system where all components are interconnected through the company entity, enabling complex workflows and comprehensive reporting across all HR functions.
