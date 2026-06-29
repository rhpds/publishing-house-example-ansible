# Module 3: Deploying Application Updates

## Brief Overview

Edge devices running applications need regular updates, but pushing updates to an entire fleet simultaneously risks downtime if something goes wrong. Infrastructure engineers need a strategy that updates devices incrementally, validating each batch before proceeding. In this module, learners will deploy application updates across edge kiosks using rolling update strategies in AAP, minimizing risk while keeping the fleet current.

The lab environment provides a pre-deployed AAP controller on OpenShift with two RHEL 9 VMs simulating retail edge kiosks at different locations ("Store-Portland" and "Store-Austin"). A sample kiosk application is pre-installed on each device, and the devices are organized in the AAP inventory.

## Audience and Time

- **Target personas:** Sysadmins and infrastructure engineers
- **Prerequisites:** Basic Ansible concepts (playbooks, inventory, roles), Linux system administration, RHEL fundamentals; familiarity with AAP job templates and inventory concepts
- **Estimated duration:** ~25 min

## What You Will See, Learn, and Do

**See:**
- A rolling update executing across edge devices in controlled batches
- Application version changing on edge kiosks as the update progresses
- AAP controller tracking the progress and status of the rolling update

**Learn:**
- How to deploy application updates across edge devices with rolling update strategies
- How AAP manages batch size, failure tolerance, and update sequencing
- How to monitor and verify application deployments across a distributed fleet

**Do:**
- Review the application update playbook and rolling update configuration
- Configure a job template with rolling update strategy settings
- Launch the rolling update and monitor its progress across the edge fleet
- Verify the application was updated successfully on each edge device
- Observe how AAP handles the update sequence and reports results

## Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1       | Understanding the Update Playbook and Strategy | ~5 min |
| 2       | Configuring the Rolling Update Job Template | ~8 min |
| 3       | Executing and Monitoring the Rolling Update | ~7 min |
| 4       | Verifying the Application Update | ~5 min |

## Detailed Steps

### Section 1: Understanding the Update Playbook and Strategy

1. Navigate to the Projects section in AAP controller and review the application update playbook
2. Examine how the playbook handles the update process for the sample kiosk application — note the update steps and validation checks
3. Identify the rolling update parameters in the playbook (batch size, serial execution, failure thresholds)
4. Check the current application version running on the edge devices via the AAP controller or terminal

### Section 2: Configuring the Rolling Update Job Template

5. Create a new job template for the application update
6. Configure the job template to use the update playbook and target the edge device inventory
7. Set the rolling update strategy parameters — configure batch size and failure tolerance appropriate for the two-device fleet
8. Select the appropriate credentials and review the job template settings
9. Save the job template

### Section 3: Executing and Monitoring the Rolling Update

10. Launch the rolling update job template
11. Monitor the job execution in the AAP controller Jobs view — observe the update applying to devices in the configured batch sequence
12. Watch for each device progressing through the update stages (pre-update checks, application update, post-update validation)
13. Observe how AAP reports the status of each host as the rolling update proceeds
14. Note how the rolling strategy controls the update sequence rather than updating all devices simultaneously

### Section 4: Verifying the Application Update

15. Review the completed job output to confirm all hosts updated successfully
16. Connect to "Store-Portland" via terminal and verify the application is running the new version
17. Connect to "Store-Austin" and confirm the same updated version is running
18. Return to the AAP controller dashboard and review the fleet status after the update

## Key Takeaways

- Rolling update strategies reduce risk by updating edge devices in controlled batches rather than all at once — with 2 devices and `serial: 1`, the lab demonstrates the pattern; in production this scales to hundreds of devices
- AAP controller provides visibility into update progress across the fleet, showing per-host status throughout the process
- Failure thresholds prevent a bad update from propagating across the entire fleet
- In production, these same rolling update patterns scale to hundreds or thousands of edge devices across distributed locations
