# Ansible Edge Automation Lab

## Problem Statement

Infrastructure engineers managing fleets of remote edge devices — retail kiosks, industrial gateways, branch office systems — struggle to maintain consistency, push updates, and remediate security findings at scale. Individual SSH access doesn't work when you have dozens or hundreds of devices across distributed locations. This workshop demonstrates how Ansible Automation Platform provides a centralized, scalable approach to the full edge device lifecycle.

## Target Audience

- **Role:** Sysadmins and infrastructure engineers
- **Experience level:** Intermediate
- **What they already know:** Basic Ansible concepts (playbooks, inventory, roles), Linux system administration, RHEL fundamentals
- **What they don't know:** AAP controller workflows for edge fleet management, Event-Driven Ansible for automated remediation, fleet-scale configuration and update patterns
- **Prerequisites:** Familiarity with Ansible playbooks and inventory; basic Linux CLI experience

## Learning Objectives

1. Configure AAP controller to organize and manage a fleet of remote edge devices using smart inventories and device groups
2. Push standardized configurations to edge devices using AAP job templates and surveys
3. Deploy application updates across edge devices with rolling update strategies
4. Implement automated security remediation using Event-Driven Ansible rulebooks
5. Monitor edge device fleet status and compliance from the AAP controller dashboard

## Content Type

Workshop (hands-on)

## Products & Technologies

- Red Hat Ansible Automation Platform 2.6
- Event-Driven Ansible
- Red Hat Enterprise Linux 9 (edge devices)
- Red Hat OpenShift (AAP deployment platform)

## Module Map

| Module | Title | Duration |
|--------|-------|----------|
| 1 | Onboarding Edge Devices at Scale | ~20 min |
| 2 | Pushing Configuration to the Fleet | ~20 min |
| 3 | Deploying Application Updates | ~25 min |
| 4 | Remediating a Security Finding | ~25 min |
| — | **Total hands-on** | **~90 min** |

## Difficulty Level

Intermediate

## Environment

**Learner view:** Pre-deployed AAP controller on OpenShift, accessible via browser. Two RHEL 9 VMs simulating edge kiosks at different retail locations (e.g., "Store-Portland" and "Store-Austin"), already registered in the AAP inventory. A sample kiosk application is pre-installed on each device. Event-Driven Ansible controller is pre-installed and accessible. The learner interacts primarily through the AAP web UI and a terminal for verification.

**Automation needed:** Yes

Automation must provision:
- AAP controller on OpenShift (controller, EDA controller, credentials, base inventory)
- Two RHEL 9 VMs configured as edge kiosks with a sample application
- Network connectivity between AAP and edge devices
- Pre-populated inventory with edge devices grouped by location
- Sample playbooks, job templates, and EDA rulebooks loaded into AAP

## Infrastructure Requirements

- **Base infrastructure:** ocp4-cluster with CNV (TBD — validate CNV performance for RHEL 9 VMs during automation phase)
- **Sizing:** OCP cluster with sufficient workers to host AAP + 2 KubeVirt RHEL 9 VMs (~4 CPU, 8GB RAM per VM). Exact cluster sizing TBD.
- **Cloud provider:** CNV (default)
- **Automation approach:** Ansible (AgnosticD roles for OCP + AAP deployment, custom roles for edge VM provisioning and app setup)
- **Existing workloads to reuse:** AAP deployment roles from AgnosticD (if available), RHEL 9 VM provisioning patterns
- **New workloads needed:** Edge kiosk application setup, EDA rulebook configuration, sample security finding injection for module 4

## Differentiation

This workshop fills a specific gap in the RHDP catalog identified during vetting:

- **vs. Red Hat Edge Manager labs** — Those labs cover fleet management using Edge Manager (flightctl) with desired-state OS management and GitOps workflows. This workshop uses AAP controller and Event-Driven Ansible as the management layer, focusing on application-level lifecycle operations (configuration, updates, remediation) rather than OS-level image management.
- **vs. AI-Driven AAP lab** — That lab covers EDA in an AIOps context with AI inference, Splunk integration, and Granite LLM. This workshop keeps EDA grounded in a straightforward edge operations scenario without AI dependencies, making it accessible to sysadmins who want practical EDA skills.
- **vs. Advanced Features of AAP lab** — That lab covers AAP controller features broadly (CaC, workflows, RBAC). This workshop applies those features to a concrete edge use case with a cohesive scenario, showing how inventories, job templates, and EDA work together for fleet management.

**Unique content gaps this workshop fills:**
- AAP credential management patterns for edge device authentication
- Inventory organization strategies (groups + smart inventories) for edge fleets
- Fleet-scale rolling update orchestration via AAP
- Event-Driven Ansible for automated security remediation of edge devices
