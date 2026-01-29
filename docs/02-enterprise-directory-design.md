# Phase 2 – Enterprise Directory Design

This phase focuses on transforming a basic Active Directory domain into an
enterprise-style directory structure that mirrors how real organizations
organize identities and devices.

## Goals

- Introduce a hierarchical OU design
- Separate users and machines by function and department
- Prepare the environment for Group Policy and delegated administration
- Validate end-to-end domain functionality from DC to client

## Architecture

OU structure implemented:

corp.local
└── Corp
├── IT
├── HR
├── Sales
└── Workstations


- Department OUs represent business units
- `Workstations` contains all domain-joined client machines
- Structure is designed to support targeted Group Policy and role-based control

## Implementation Steps

1. Created top-level `Corp` OU
2. Created departmental OUs: `IT`, `HR`, `Sales`
3. Created `Workstations` OU for client machines
4. Joined `WS01` to the domain and moved it into `Workstations`
5. Created test users in each department OU
6. Validated:
   - DNS resolution to DC
   - Domain authentication
   - AD object visibility from DC

## Lessons Learned

- Domain-joined machines are initially placed in the default `Computers` container  
- Organizational Units provide policy and delegation boundaries  
- AD protects certain containers by default (accidental deletion protection)  
- Domain Admin privileges differ from local Administrator accounts  

This phase establishes a foundation for:

- Group Policy enforcement by role
- Department-based security boundaries
- Realistic enterprise directory modeling
