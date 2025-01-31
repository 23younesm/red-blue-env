# CCSO OpenStack Environment

## Deployment Guide

This guide provides step-by-step instructions for deploying an environment on CCSO OpenStack using a Heat template. Follow these instructions carefully to ensure a successful deployment.

---

### Prerequisites

1. **Access to Horizon OpenStack Dashboard**:

   - Navigate to the Horizon OpenStack URL provided by your Tech Director.
   - Log in using your credentials. If you do not have credentials, contact the Tech Director.

2. **Project Selection**:

   - After logging in, ensure you have selected the correct project from the project dropdown menu.

---

### Deployment Steps

#### Step 1: Launch the Stack

1. Navigate to **Orchestration > Stacks** in the Horizon dashboard.
2. Click **Launch Stack**.
3. In the **Template Source** dropdown, select **Direct Input**.
4. Copy the contents of the Heat template file (`docs/heat/templates/main_template.yaml`) from this repository and paste it into the template input field.
5. Click **Next**.

---

#### Step 2: Configure Stack Parameters

1. **Stack Name**:
   - Provide a unique name for your stack.

2. **Images**:
   - For each image parameter (e.g., CentOS 7 Image, Ubuntu 20.04 Image), select the corresponding image from the dropdown menu.

3. **SSH Key**:
   - Select a predefined SSH key from the dropdown. If no key is available, contact the Technical Director to create one.

4. **Master Node Volume Size**:
   - Specify the volume size for the master node. The default is **40 GB**.

5. Click **Launch** to start the stack deployment.

---

#### Step 3: Monitor Deployment

1. Navigate to **Compute > Instances** to monitor the status of the virtual machines.
2. Wait until all instances are in the **Active** state. This indicates that the deployment is complete.

---

#### Step 4: Assign a Floating IP to the Master Node

To access the master node via SSH, you need to assign a public (floating) IP address:

1. Navigate to **Network > Floating IPs**.
2. Click **Allocate IP to Project**.
3. In the popup window, click **Allocate**.
4. Once the floating IP is allocated, click **Associate**.
5. In the **Port to be Associated** dropdown, select the port corresponding to the master node.
6. Click **Associate** to complete the process.

---

#### Step 5: Connect to the Master Node

1. Connect to the **CCSO Cloudflare WARP VPN**.
2. Use the SSH key specified during the stack setup to connect to the master node:

   ```bash
   ssh -i <path-to-ssh-key> ubuntu@<floating-ip>
   ```

3. You should now have access to the master node.

---

### Conclusion

You have successfully deployed an environment on CCSO OpenStack using a Heat template. If you encounter any issues during the process, contact the Technical Director for assistance.

---

### Troubleshooting

- **Stack Deployment Errors**: Check the stack events in **Orchestration > Stacks** for detailed error messages.
- **SSH Connection Issues**: Ensure the SSH key is correct and the floating IP is properly associated with the master node.
- **Instance Not Active**: Verify that the images and resources specified in the Heat template are available in your project.

For further assistance, refer to the OpenStack documentation or contact the Tech Director.