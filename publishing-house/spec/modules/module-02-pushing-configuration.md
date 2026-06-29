# Module 2: Pushing Configuration to the Fleet

## Brief Overview

Once edge devices are organized in AAP controller, the next challenge is ensuring consistent configuration across the entire fleet. Manually configuring individual devices leads to drift and errors at scale. In this module, learners will push standardized configurations to edge kiosks using AAP job templates and surveys, ensuring every device in the fleet meets the desired state.

The lab environment provides a pre-deployed AAP controller on OpenShift with two RHEL 9 VMs simulating retail edge kiosks at different locations ("Store-Portland" and "Store-Austin"). The devices are organized in the AAP inventory with groups and smart inventories. A sample kiosk application is pre-installed on each device.

## Audience and Time

- **Target personas:** Sysadmins and infrastructure engineers
- **Prerequisites:** Basic Ansible concepts (playbooks, inventory, roles), Linux system administration, RHEL fundamentals; familiarity with AAP inventory and device group concepts
- **Estimated duration:** ~20 min

## What You Will See, Learn, and Do

**See:**
- Job templates executing against the edge device fleet
- Survey prompts collecting input parameters before job execution
- Configuration changes applied consistently across both edge kiosks

**Learn:**
- How AAP job templates standardize configuration delivery to edge devices
- How surveys enable parameterized, reusable job templates without editing playbooks
- How to target configuration pushes to specific device groups or the full fleet

**Do:**
- Review a pre-loaded playbook that applies standardized configuration to edge kiosks
- Create a job template that targets edge devices in the inventory
- Add a survey to the job template to parameterize configuration values
- Launch the job template and push configuration to the fleet
- Verify the configuration was applied consistently on both edge devices

## Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1       | Reviewing the Configuration Playbook | ~5 min |
| 2       | Creating a Job Template with Survey | ~8 min |
| 3       | Pushing Configuration and Verifying | ~7 min |

## Detailed Steps

### Section 1: Reviewing the Configuration Playbook

1. Navigate to the Projects section in AAP controller and locate the pre-loaded edge management project
2. Review the playbook that applies standardized configuration to the kiosk devices — note the variables it expects
3. Identify which configuration parameters are suitable for survey input vs. hard-coded defaults
4. Observe how the playbook targets hosts using inventory groups

### Section 2: Creating a Job Template with Survey

5. Navigate to the Templates section and create a new job template
6. Configure the job template to use the edge management project and configuration playbook
7. Set the inventory to target the edge device group created in Module 1
8. Select the appropriate credentials for connecting to the edge devices
9. Add a survey to the job template that prompts for configurable parameters (e.g., configuration values that vary by deployment)
10. Set default values and validation rules for the survey fields
11. Save the job template and verify the survey preview

### Section 3: Pushing Configuration and Verifying

12. Launch the job template — fill in the survey prompts with the desired configuration values
13. Monitor the job execution in the AAP controller Jobs view — observe the playbook running against both edge devices
14. Review the job output to confirm successful execution on each host
15. Open a terminal and connect to one of the edge devices to verify the configuration was applied as expected
16. Verify the second edge device received the same configuration, confirming fleet-wide consistency

## Key Takeaways

- Job templates provide a repeatable, standardized method for pushing configuration to edge devices at scale
- Surveys make job templates flexible and reusable without requiring playbook modifications
- AAP controller tracks job execution history, providing an audit trail of every configuration change pushed to the fleet
- With organized inventories and job templates in place, the fleet is ready for application updates and automated remediation
