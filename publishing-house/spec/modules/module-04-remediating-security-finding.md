# Module 4: Remediating a Security Finding

## Brief Overview

Edge devices spread across remote locations are vulnerable to security issues that need rapid response. Waiting for manual intervention to remediate findings across a distributed fleet is too slow and error-prone. In this module, learners will implement automated security remediation using Event-Driven Ansible (EDA) rulebooks, enabling the system to detect a security finding on an edge device and automatically trigger a remediation playbook through AAP controller.

The lab environment provides a pre-deployed AAP controller on OpenShift with two RHEL 9 VMs simulating retail edge kiosks at different locations ("Store-Portland" and "Store-Austin"). Event-Driven Ansible controller is pre-installed and accessible. A sample kiosk application is pre-installed on each device.

## Audience and Time

- **Target personas:** Sysadmins and infrastructure engineers
- **Prerequisites:** Basic Ansible concepts (playbooks, inventory, roles), Linux system administration, RHEL fundamentals; familiarity with AAP job templates from previous modules
- **Estimated duration:** ~25 min

## What You Will See, Learn, and Do

**See:**
- Event-Driven Ansible detecting a security event from an edge device
- An EDA rulebook automatically triggering a remediation job template in AAP controller
- The remediation playbook executing on the affected device without manual intervention

**Learn:**
- How Event-Driven Ansible rulebooks define event sources, conditions, and automated actions
- How EDA integrates with AAP controller to trigger remediation workflows
- How automated remediation reduces response time for security findings across a distributed fleet

**Do:**
- Explore the Event-Driven Ansible controller interface
- Review a pre-loaded EDA rulebook that responds to security findings
- Review the remediation playbook that the rulebook triggers
- Simulate a security finding on one of the edge devices
- Observe EDA detecting the event and automatically launching the remediation job
- Verify the security finding was remediated on the affected device

## Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1       | Exploring Event-Driven Ansible | ~5 min |
| 2       | Reviewing the Rulebook and Remediation Playbook | ~7 min |
| 3       | Simulating and Remediating a Security Finding | ~8 min |
| 4       | Verifying Remediation and Fleet Compliance | ~5 min |

## Detailed Steps

### Section 1: Exploring Event-Driven Ansible

1. Log in to the Event-Driven Ansible controller web UI
2. Navigate to the overview and observe the EDA controller components — rulebook activations, event sources, and actions
3. Review how EDA controller connects to the AAP controller for triggering job templates
4. Familiarize yourself with the EDA interface layout and key sections

### Section 2: Reviewing the Rulebook and Remediation Playbook

5. Open the pre-loaded EDA rulebook and examine its structure — identify the event source, the condition that triggers the rule, and the action it takes
6. Note how the rulebook condition matches a specific security finding event
7. Trace the action to the AAP controller job template it triggers upon detection
8. Switch to the AAP controller and review the remediation playbook — understand what steps it takes to fix the security finding on an affected device
9. Verify the remediation job template is configured and ready to be triggered by EDA

### Section 3: Simulating and Remediating a Security Finding

10. Open a terminal connection to one of the edge devices (e.g., "Store-Portland")
11. Introduce a simulated security finding on the device using the provided simulation method
12. Return to the EDA controller and observe the event being detected by the rulebook activation
13. Watch the rulebook condition match and the action fire — the EDA controller triggers the remediation job template in AAP controller
14. Switch to the AAP controller Jobs view and monitor the remediation playbook executing against the affected edge device
15. Observe the job completing and reporting success

### Section 4: Verifying Remediation and Fleet Compliance

16. Connect to the affected edge device via terminal and verify the security finding has been remediated
17. Confirm the device is back to a compliant state
18. Review the AAP controller dashboard — check fleet status and compliance across both edge devices
19. Review the EDA controller to see the event history and action log for the remediation that occurred

## Key Takeaways

- Event-Driven Ansible enables automated, event-driven responses to security findings without manual intervention
- EDA rulebooks define the detection criteria and remediation actions, creating a closed-loop security response
- Integration between EDA controller and AAP controller allows rulebooks to trigger full remediation workflows using existing job templates and playbooks
- Automated remediation dramatically reduces response time for security findings across distributed edge fleets

## Infrastructure Notes

- A method for injecting a simulated security finding on the edge devices must be pre-configured in the environment
- The EDA controller must be pre-configured with connectivity to the AAP controller and the event source for the edge devices
- The EDA rulebook activation should be running and ready to detect events before the learner begins the simulation step
