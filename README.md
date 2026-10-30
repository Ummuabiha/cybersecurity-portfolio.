Kali Linux Virtual Machine Lab Setup

1. Project Overview

This project documents the installation, configuration, and basic setup of a Kali Linux virtual machine using Oracle VirtualBox.

The practical exercise involved setting up a virtualised Kali Linux environment, configuring its network connection, establishing communication between the Windows host and Kali Linux guest operating system, and creating a virtual machine snapshot.

The project was completed as part of the NetworkWalks Academy cybersecurity practical training.

2. Project Objectives

The objectives of this practical exercise were to:

- Set up Kali Linux as a virtual machine using Oracle VirtualBox.
- Create and configure a NAT Network.
- Configure the network adapter of the Kali Linux virtual machine.
- Attempt to assign a static IP address.
- Test internet connectivity and DNS resolution.
- Configure a shared folder between Windows and Kali Linux.
- Enable bidirectional shared clipboard.
- Enable bidirectional drag and drop.
- Create a virtual machine snapshot.
- Understand basic virtualisation and network configuration.

## 3. Lab Environment

The following environment and tools were used:

| Component | Configuration |
|---|---|
| Host Operating System | Windows |
| Virtualisation Software | Oracle VirtualBox |
| VirtualBox Version | 7.2.22 |
| Guest Operating System | Kali Linux |
| Kali Linux Version | 2026.3 (64-bit) |
| Network Attachment | NAT Network |
| NAT Network Name | NatNetwork |
| Network Subnet | 10.0.0.0/24 |
| Intended Static IP | 10.0.0.2 |
| Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |

4. Tools and Technologies

- Oracle VirtualBox: Used to create and manage the virtual machine.
- Kali Linux: The guest operating system used for the cybersecurity lab.
- **NAT Network:** Used to provide network connectivity to the virtual machine.
- **Windows:** The host operating system.
- **Linux Terminal:** Used to execute network verification commands.

## 5. Implementation and Configuration Steps

### Step 1: Creating the NAT Network

I opened Oracle VirtualBox and created a NAT Network named `NatNetwork`.

The network was configured with the following subnet:

- Network Address: `10.0.0.0/24`
- Intended Gateway: `10.0.0.1`

This network was created to provide network connectivity for the Kali Linux virtual machine.

### Step 2: Importing Kali Linux

I imported the Kali Linux virtual machine into Oracle VirtualBox.

After the import process, the virtual machine appeared in VirtualBox Manager and was ready for configuration.

### Step 3: Configuring the Network Adapter

I opened the virtual machine's settings and navigated to Network.

Initially, I selected NAT instead of NAT Network. This meant I could not select the previously created NAT Network.

I corrected this by changing the network attachment type to NAT Network and selecting:

`NatNetwork`

I also ensured that the network cable was connected.

### Step 4: Attempting Static IP Configuration

Inside Kali Linux, I opened the network settings and navigated to the IPv4 configuration.

I selected the Manual configuration method and entered the following values:

| Setting | Intended Value |
|---|---|
| IPv4 Method | Manual |
| IP Address | 10.0.0.2 |
| Netmask | 255.255.255.0 |
| Gateway | 10.0.0.1 |
| DNS | 8.8.8.8 |

I saved the configuration and reconnected the network.

However, after checking the network interface using the terminal, Kali Linux continued to display:

`10.0.0.3/24`

The address was marked as dynamic.

Therefore, the intended static IP address of `10.0.0.2` was not successfully verified. This remains an unresolved configuration issue.

### Step 5: Testing Network Connectivity

I used the Linux terminal to test internet connectivity and DNS resolution.

**Test 1: Testing connectivity using Google's public DNS IP**

Command:

```bash
ping -c 4 8.8.8.8
```

Result:

- 4 packets transmitted
- 4 packets received
- 0% packet loss

This confirmed that the virtual machine could communicate with the external IP address.

**Test 2: Testing DNS resolution**

Command:

```bash
ping -c 4 google.com
```

Result:

- The domain resolved to an IP address.
- 4 packets were received.
- 0% packet loss.

This confirmed that DNS resolution was working during the test.

### Step 6: Creating a Shared Folder

To make file sharing between Windows and Kali Linux easier, I created a folder on the Windows desktop named:

`Kali-Lab-Screenshots`

I then opened the virtual machine settings in VirtualBox and navigated to Shared Folders.

I added the Windows folder using the following settings:

| Setting | Configuration |
|---|---|
| Folder Name | Kali-Lab-Screenshots |
| Read-only | Disabled |
| Auto-mount | Enabled |
| Make Global | Enabled |

Initially, the OK button was disabled because the folder path had not been properly selected.

I resolved this by using the folder browser to locate and select the actual folder on the Windows desktop.

After saving the configuration and starting Kali Linux, the shared folder appeared on the Kali desktop.

### Step 7: Testing the Shared Folder

I opened the shared folder in Kali Linux and created a test folder named:

`Test-Shared-Folder`

I then checked the corresponding folder on the Windows desktop.

The test folder appeared successfully in Windows.

This confirmed that file sharing between the host and guest operating systems was working.

### Step 8: Enabling Shared Clipboard

I opened the Devices menu in the running VirtualBox window.

Under Shared Clipboard, I selected:

`Bidirectional`

I tested the feature by copying text from Windows and pasting it into Kali Linux.

The test was successful.

### Step 9: Enabling Drag and Drop

I opened the Devices menu again.

Under Drag and Drop, I selected:

`Bidirectional`

I tested the feature by transferring a small test file between Windows and Kali Linux.

The feature worked successfully.

### Step 10: Creating a Virtual Machine Snapshot

I opened Oracle VirtualBox Manager and selected the Snapshots section.

I created a snapshot named:

`My Fresh Kali Linux`

The snapshot was successfully created and appeared in the snapshot list.

The snapshot provides a recovery point for the virtual machine.

## 6. Challenges Encountered and Solutions

During the practical exercise, I encountered the following challenges:

### Challenge 1: Selecting the Wrong Network Attachment

**Problem:** I initially selected NAT instead of NAT Network. As a result, I could not select the previously created NAT Network.

**Solution:** I changed the network attachment type to NAT Network and selected `NatNetwork`.

### Challenge 2: Static IP Address Not Applying

**Problem:** Although I entered `10.0.0.2` in the manual IPv4 configuration, the terminal continued to display `10.0.0.3/24` as a dynamic address.

**Solution:** I checked the network interface and attempted to reconfigure the connection. The intended static IP was not successfully applied, so further troubleshooting is required.

### Challenge 3: Shared Folder OK Button Disabled

**Problem:** The Add Shared Folder window did not allow me to click OK.

**Solution:** I used the folder browser to select the actual Windows folder path. After selecting the correct folder, the OK button became available.

### Challenge 4: Network Connection Stuck Loading

**Problem:** After changing network settings, the network connection remained in a loading state.

**Solution:** I disconnected and reconnected Wired Connection 1, then waited for the connection to respond. I subsequently repeated the connectivity and DNS tests successfully.

## 7. Verification and Results

The following table summarises the results of the practical exercise.

| Configuration or Test | Result |
|---|---|
| Kali Linux imported into VirtualBox | Successful |
| NAT Network selected | Successful |
| Internet connectivity test | Successful |
| DNS resolution test | Successful |
| Intended static IP (10.0.0.2) | Not verified |
| Shared folder configuration | Successful |
| Shared folder file-sharing test | Successful |
| Bidirectional shared clipboard | Successful |
| Bidirectional drag and drop | Successful |
| Virtual machine snapshot | Successful |


## 8. Lessons Learned

This practical exercise helped me develop a better understanding of virtualisation and basic network configuration.

Some of the key lessons include:

- Understanding the difference between NAT and NAT Network.
- Learning how to configure a virtual machine's network adapter.
- Understanding the importance of verifying IP address assignments.
- Using terminal commands to test network connectivity and DNS resolution.
- Sharing files between a host and guest operating system.
- Configuring bidirectional clipboard and drag-and-drop functionality.
- Understanding how snapshots can preserve a virtual machine's state.
- Learning to troubleshoot configuration problems instead of assuming that settings have been applied successfully.

## 9. Conclusion

This practical exercise provided hands-on experience in setting up and configuring a Kali Linux virtual machine using Oracle VirtualBox.

I successfully imported Kali Linux, configured its network attachment, tested internet connectivity and DNS resolution, established file sharing between Windows and Kali Linux, enabled bidirectional clipboard and drag-and-drop functionality, and created a virtual machine snapshot.

Although the intended static IP address was not successfully applied, the issue helped me understand the importance of verifying network configurations through practical testing.

Overall, this exercise strengthened my foundational understanding of virtualisation, Linux networking, and virtual machine management as part of my cybersecurity learning journey.

## 11. References

- Student Lab Setup Repository: https://github.com/Victory-cyber-hub/virtualbox-kali-linux-lab-setup
- Instructor Sample Repository: https://github.com/waqaskarimccie/NETWORKWALKS-B082-WK1-PM1-CYBERSECURITY-LAB-SETUP-SAMPLE
- Kali Linux: https://www.kali.org/
- Oracle VirtualBox: https://www.virtualbox.org/

---

**Author:** Fatima Ibrahim Abdullahi

**Training:** NetworkWalks Academy

**Practical:** Week 1 – Practical 1 (WK1-PM1)

**Project:** Kali Linux Virtual Machine Lab Setup
