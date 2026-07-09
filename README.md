Here's your performance task converted to well-structured markdown:

```markdown
# Performance Task: Router Initial Configuration

| **Course** | ITE 359 - Networking 2 |
|------------|------------------------|
| **Module** | Router Initial Configuration |
| **Tool Required** | Cisco Packet Tracer |

---

## Objective

In this performance task, you will apply the concepts from the **Router Initial Configuration** module. You will build a basic network topology, access a router via a console connection, and configure fundamental settings including the device hostname, administrative passwords, and interface IP addresses.

---

## Task 1: Build the Physical Topology

Your first step is to set up the equipment in your Packet Tracer workspace.

### Step 1: Open Cisco Packet Tracer
Launch Cisco Packet Tracer on your computer.

### Step 2: Add a Router
1. Go to the device category menu in the bottom-left corner.
2. Click on **Network Devices** (the router icon), then select **Routers**.
3. Click and drag the **1941 router** into the center of the white workspace.

### Step 3: Add an Administrator PC
1. Click on **End Devices** (the PC/Monitor icon) in the bottom-left corner.
2. Click and drag a **PC** onto the workspace next to your router.

### Step 4: Connect the Console Cable
1. Click the **Connections** icon (the orange lightning bolt).
2. Select the **Console cable** (the light blue, curved line).
3. Click on the **PC**, and select **RS 232** from the pop-up menu.
4. Click on the **Router**, and select **Console** from the pop-up menu.

> ✅ **Checkpoint:** Your physical topology should now have a 1941 router and a PC connected via a console cable.

---

## Task 2: Access the Router's CLI

In the real world, you cannot simply click on a router to configure it. You must use a terminal emulator software on your PC.

### Steps to Access the CLI

1. **Click on the PC** in your workspace to open its configuration window.
2. Navigate to the **Desktop** tab at the top.
3. Click on the **Terminal** application.
4. Leave the default port configuration settings as they are (**9600 baud rate**) and click **OK**.
5. You will see the router's boot-up text. If it asks:
   ```
   Would you like to enter the initial configuration dialog? [yes/no]:
   ```
   Type **`no`** and press **Enter**.
6. Press **Enter** once more to access the User EXEC mode prompt:
   ```
   Router>
   ```

> ✅ **Checkpoint:** You should now see the `Router>` prompt, indicating you are in User EXEC mode.

---

## Task 3: Apply the Initial Configuration

Now you will apply the **three pillars of initial router configuration**. Type the commands exactly as shown below.

### Step A: Enter Global Configuration Mode

First, you must elevate your privileges to make changes to the device.

```bash
Router> enable
Router# configure terminal
```

| Command | Description |
|---------|-------------|
| `enable` | Enters Privileged EXEC mode |
| `configure terminal` | Enters Global Configuration mode |

---

### Step B: Configure Management Identifiers (Hostname)

Assign a unique name to the router so it can be easily identified on the network.

```bash
Router(config)# hostname R1
```

> ℹ️ **Notice:** The prompt immediately changes from `Router(config)#` to `R1(config)#`

---

### Step C: Configure Device Security

Set an encrypted password to protect the Privileged EXEC mode (enable mode).

```bash
R1(config)# enable secret class
```

| Command | Description |
|---------|-------------|
| `enable secret class` | Sets an **encrypted** privileged EXEC password to "class" |

---

### Step D: Activate the Interface

A router's interfaces are **turned off by default**. You must assign an IP address and turn the interface on.

```bash
R1(config)# interface gigabitethernet0/0
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
```

| Command | Description |
|---------|-------------|
| `interface gigabitethernet0/0` | Enters interface configuration mode for GigabitEthernet0/0 |
| `ip address 192.168.1.1 255.255.255.0` | Assigns the IP address and subnet mask |
| `no shutdown` | Administratively brings the interface up |

> ℹ️ **Notice:** You should see a message pop up stating that the interface changed state to **"up"**.

---

## Task 4: Verify Your Configuration

A good network administrator always verifies their work. Let's check if your interface accepted the IP address and is currently active.

### Step 1: Exit Configuration Mode

Exit out of configuration mode back to the Privileged EXEC prompt:

```bash
R1(config-if)# end
```

### Step 2: Check Interface Status

Run the following command to view a summary of your interfaces:

```bash
R1# show ip interface brief
```

### Step 3: Verify the Output

Look at the row for **GigabitEthernet0/0** and check the following:

| Verification Item | Expected Value |
|-------------------|----------------|
| IP Address | `192.168.1.1` |
| Status | `up` |
| Protocol | `up` |

> 🎉 **If all three match, congratulations!** You have successfully completed the initial configuration of a Cisco router.

---

## Summary of Commands Used

| Command | Mode | Purpose |
|---------|------|---------|
| `enable` | User EXEC → Privileged EXEC | Elevate privileges |
| `configure terminal` | Privileged EXEC → Global Config | Enter configuration mode |
| `hostname R1` | Global Config | Set router name |
| `enable secret class` | Global Config | Set encrypted enable password |
| `interface gigabitethernet0/0` | Global Config → Interface Config | Enter interface configuration |
| `ip address 192.168.1.1 255.255.255.0` | Interface Config | Assign IP address |
| `no shutdown` | Interface Config | Enable interface |
| `end` | Any config mode → Privileged EXEC | Return to Privileged EXEC |
| `show ip interface brief` | Privileged EXEC | Verify interface status |

---

## Reflection Questions

*Submit your answers to the following questions to your instructor.*

### Question 1
**Why is it important to use the `enable secret` command instead of leaving the router without a password?**

> *Your answer here...*

### Question 2
**What happened to the router's interface status immediately after you typed the `no shutdown` command?**

> *Your answer here...*

---

*End of Performance Task*
```

---

The markdown version includes:
- **Tables** for organized information and command references
- **Code blocks** with syntax highlighting for all CLI commands
- **Callout boxes** (using blockquotes with emojis) for checkpoints and notices
- **Clear section hierarchy** with consistent heading levels
- **A summary command table** for quick reference
- **Answer spaces** for the reflection questions
