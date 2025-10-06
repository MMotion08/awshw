# awshw
<h1>Hi, I'm Kyle! <br/> Currently learning AWS CloudDevOps and beyond! </h1>

<h2> Below is the instructions about how to configure EC2's and teardown procedures </h2>


---

## EC2 Configuration Instructions

### Prerequisites
1. Sign into the AWS Console
2. Verify the region you are using
3. Navigate to the EC2 Dashboard

### Step 1: Security Group Creation
*Create a security group with only an HTTP rule*

1. **Navigate to Security Groups:**
   - Left pane → Network and Security → Security Groups
   
2. **Create Security Group:**
   - Click "Create Security Group"
   - Enter SG Name and Description
   - Verify VPC is set to default
   - Add inbound HTTP rule with "Anywhere IPv4" source (`0.0.0.0/0`)
   - **Don't modify outbound rules** - verify "All traffic" is allowed
   - *(Optional: Add tags)*
   - Click "Create Security Group"
   
3. **Verification:**
   - Verify SG is created and correctly configured

### Step 2: Obtain Startup Script
- Choose from the available scripts (mine, yours, or Theo's)
- Copy the script from GitHub

### Step 3: Launch EC2 Instance

1. **Navigate to Instances:**
   - Left pane → Instances → Instances
   - Click "Launch Instances"

2. **Configure Instance:**
   - **Name and Tags:** Enter instance name, add relevant tags
   - **AMI Selection:** Review AMI menu, ensure defaults are selected, collapse
   - **Instance Type:** Review instance type menu, ensure proper sizing, collapse
   - **Key Pair:** Select "Proceed without key pair", collapse
   
3. **Network Settings:**
   - **Don't click "Edit"**
   - Verify VPC selection
   - *Note: Subnet selection is not critical for this lab*
   - Ensure "Auto-assign public IP" is enabled
   - **Select your created Security Group** *(NOT "launch-wizard"!)*
   - Collapse section
   
4. **Storage Configuration:**
   - Review Configure Storage menu
   - *Brief discussion: What is EBS?*
   - Collapse section
   
5. **Advanced Settings:**
   - Open Advanced Settings
   - **Focus on User Data section only** - ignore everything else
   - Paste your chosen startup script
   
6. **Launch:**
   - Review configuration
   - Click "Launch Instance"

### Step 4: Test Your Web Server

1. Wait for the instance to pass status checks
2. Copy the instance's **public DNS address**
3. Open your web browser
4. Navigate to: `http://<public-DNS-address>`
   - **Important:** Use `http://` prefix, not `https://`


---


<h2> EC2 Teardown Instructions </h2>

## Teardown


1. **Terminate the EC2 Instance**
   - Navigate to EC2 → Instances
   - Select your instance
   - Instance State → Terminate Instance

2. **Delete Security Group** *(Optional)*
   - Navigate to EC2 → Security Groups
   - Select your created security group
   - Actions → Delete Security Group
   - *Note: Can only delete after instance termination*

---
