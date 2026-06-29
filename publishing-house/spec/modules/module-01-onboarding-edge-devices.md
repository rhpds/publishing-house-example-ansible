# Module 1: Onboarding Edge Devices at Scale

## Brief Overview

Infrastructure engineers managing distributed edge devices need a centralized way to organize and manage their fleet. Manually tracking devices across locations leads to configuration drift and operational blind spots. In this module, learners will use AAP controller to organize a fleet of remote edge kiosks using smart inventories and device groups, establishing the foundation for all subsequent fleet management tasks.

The lab environment provides a pre-deployed AAP controller on OpenShift with two RHEL 9 VMs simulating retail edge kiosks at different locations ("Store-Portland" and "Store-Austin"), already registered in the AAP inventory with a sample kiosk application pre-installed.

## Audience and Time

- **Target personas:** Sysadmins and infrastructure engineers
- **Prerequisites:** Basic Ansible concepts (playbooks, inventory, roles), Linux system administration, RHEL fundamentals
- **Estimated duration:** ~20 min

## What You Will See, Learn, and Do

**See:**
- The AAP controller dashboard showing registered edge devices
- Smart inventory dynamically grouping devices by location and attributes
- Device group membership and host variables in the AAP UI

**Learn:**
- How AAP controller organizes and manages a fleet of remote edge devices
- How smart inventories automatically categorize devices based on attributes
- How device groups enable targeted operations across subsets of the fleet

**Do:**
- Explore the pre-populated AAP inventory containing the edge devices
- Create device groups to organize kiosks by location
- Build a smart inventory that dynamically filters edge devices based on host attributes
- Verify device connectivity and group membership from the AAP controller

## Lab Structure

| Section | Title | Duration |
|---------|-------|----------|
| 1       | Exploring the AAP Controller and Inventory | ~5 min |
| 2       | Organizing Devices with Groups | ~8 min |
| 3       | Building Smart Inventories | ~7 min |

## Detailed Steps

### Section 1: Exploring the AAP Controller and Inventory

1. Log in to the AAP controller web UI using the provided credentials
2. Navigate to the Inventories section and open the pre-populated edge device inventory
3. Review the two registered hosts ("Store-Portland" and "Store-Austin") and their host variables
4. Observe the existing inventory structure — note how the devices are listed but not yet organized into operational groups
5. Verify connectivity to both edge devices by running an ad-hoc ping command from the AAP controller

### Section 2: Organizing Devices with Groups

6. Create a new group within the inventory for organizing devices by location (e.g., "west-coast", "south-central")
7. Assign "Store-Portland" to the appropriate location group
8. Assign "Store-Austin" to its location group
9. Add host variables to each device that identify device attributes (e.g., region, device type, application version)
10. Verify the group membership displays correctly in the inventory view

### Section 3: Building Smart Inventories

11. Navigate to the Smart Inventories section in AAP controller
12. Create a new smart inventory with a filter that dynamically selects devices based on the host attributes set in the previous section
13. Verify the smart inventory automatically includes the correct devices based on the filter criteria
14. Modify a host attribute on one device and observe how the smart inventory membership updates
15. Review the AAP controller dashboard to confirm fleet status and device organization

## Key Takeaways

- AAP controller provides centralized visibility and organization for distributed edge device fleets
- Smart inventories enable dynamic, attribute-based grouping that automatically adapts as the fleet changes
- Properly organized inventories and device groups are the foundation for pushing configurations, deploying updates, and automating remediation in subsequent modules

## Infrastructure Notes

- Both RHEL 9 edge kiosk VMs must be pre-registered in the AAP inventory with network connectivity established
- Host variables identifying location and device attributes should be partially pre-populated to reduce setup time
