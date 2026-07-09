Here's the markdown version ready for your README.md:

```markdown
# Performance Task: Router Initial Configuration

**Course:** ITE 359 - Networking 2  
**Module:** Router Initial Configuration  
**Tool Required:** Cisco Packet Tracer

---

## Objective

In this performance task, you will apply the concepts from the "Router Initial Configuration" module. You will build a basic network topology, access a router via a console connection, and configure fundamental settings including the device hostname, administrative passwords, and interface IP addresses.

---

## Task 1: Build the Physical Topology

Your first step is to set up the equipment in your Packet Tracer workspace.

1. Open Cisco Packet Tracer on your computer.

2. **Add a Router:**
   - Go to the device category menu in the bottom-left corner.
   - Click on **Network Devices** (the router icon), then select **Routers**.
   - Click and drag the **1941 router** into the center of the white workspace.

3. **Add an Administrator PC:**
   - Click on **End Devices** (the PC/Monitor icon) in the bottom-left corner.
   - Click and drag a **PC** onto the workspace next to your router.

4. **Connect the Console Cable:**
   - Click the **Connections** icon (the orange lightning bolt).
   - Select the **Console cable** (the light blue, curved line).
   - Click on the **PC**, and select **RS 232** from the pop-up menu.
   - Click on the **Router**, and select **Console** from the pop-up menu.

---

## Task 2: Access the Router's CLI

In the real world, you cannot just click on a router to configure it. You must use a terminal emulator software on your PC.

1. Click on the **PC** in your workspace to open its configuration window.
2. Navigate to the **Desktop** tab at the top.
3. Click on the **Terminal** application.
4. Leave the default port configuration settings as they are (9600 baud rate) and click **OK**.
5. You will see the router's boot-up text. If it asks `Would you like to enter the initial configuration dialog? [yes/no]:`, type **no** and press **Enter**.
6. Press **Enter** once more to access the User EXEC mode prompt (`Router>`).

---

## Task 3: Apply the Initial Configuration

Now you will apply the three pillars of initial router configuration. Type the commands exactly as shown below.

### Step A: Enter Global Configuration Mode

First, you must elevate your privileges to make changes to the device.

```
Router> enable
Router# configure terminal
```

### Step B: Configure Management Identifiers (Hostname)

Assign a unique name to the router so it can be easily identified on the network.

```
Router(config)# hostname R1
```

> **Note:** The prompt immediately changes from `Router(config)#` to `R1(config)#`.

### Step C: Configure Device Security

Set an encrypted password to protect the Privileged EXEC mode (enable mode).

```
R1(config)# enable secret class
```

### Step D: Activate the Interface

A router's interfaces are turned off by default. You must assign an IP address and turn the interface on.

```
R1(config)# interface gigabitethernet0/0
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
```

> **Note:** You should see a message pop up stating that the interface changed state to "up".

---

## Task 4: Verify Your Configuration

A good network administrator always verifies their work. Let's check if your interface accepted the IP address and is currently active.

1. Exit out of configuration mode back to the Privileged EXEC prompt:

```
R1(config-if)# end
```

2. Run the following command to view a summary of your interfaces:

```
R1# show ip interface brief
```

3. **Check your output:** Look at the row for **GigabitEthernet0/0**.
   - Does it show the IP address **192.168.1.1**?
   - Does the **Status** column say **up**?
   - Does the **Protocol** column say **up**?

If yes, congratulations! You have successfully completed the initial configuration of a Cisco router.

---

## Reflection Questions

*Submit your answers to the following questions to your instructor.*

1. **Why is it important to use the `enable secret` command instead of leaving the router without a password?**

2. **What happened to the router's interface status immediately after you typed the `no shutdown` command?**
```

This markdown is properly formatted with headers, code blocks, blockquotes, and lists, making it clean and readable for your README.md file. Let me know if you need any adjustments!
