# Active-Directory-Lab

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Building a Complete Active Directory Lab with VirtualBox</title>
</head>
<body>

<h1>Building a Complete Active Directory Lab with VirtualBox</h1>

<p>In this project, I'll walk you through creating a comprehensive Active Directory lab environment on your personal computer. This setup will help you gain hands-on experience with Active Directory (AD) and Windows networking, which can be incredibly useful in cybersecurity, system administration, or IT support roles.</p>

<h2>Project Overview</h2>
<p>The primary goal is to create a local Active Directory network with a domain controller and a client machine. This lab will include:</p>
<ul>
    <li>Configuring VirtualBox for virtual machines</li>
    <li>Setting up a Windows Server as the domain controller</li>
    <li>Configuring Active Directory, DHCP, and DNS</li>
    <li>Adding a Windows 10 client to the domain</li>
    <li>Using PowerShell to create multiple AD user accounts automatically</li>
</ul>

<h2>Steps to Set Up the Lab</h2>

<h3>1. Download and Install VirtualBox</h3>
<p>Start by downloading and installing <a href="https://www.virtualbox.org/" target="_blank">Oracle VirtualBox</a>. Ensure that you also install the extension pack to support additional features like shared clipboard and file transfer between host and VM.</p>
<img src="https://imgur.com/zzn6p3f.png" alt="Download and Install VirtualBox">

<h3>2. Download Windows 10 and Windows Server ISOs</h3>
<p>Download the Windows 10 and Server 2019 ISO files. Microsoft offers trial versions for testing and educational purposes. These will be used to create virtual machines (VMs) for the domain controller and client machine.</p>
<img src="https://imgur.com/6OTGijX.png" alt="Download Windows ISOs">

<h3>3. Create the Domain Controller VM</h3>
<p>Open VirtualBox and create a new VM named “DC” (Domain Controller) with a 2GB RAM allocation. Install Windows Server on this VM using the downloaded ISO.</p>
<img src="https://imgur.com/qLZk3ZB.png" alt="Create Domain Controller VM">

<h3>4. Configure Network Adapters</h3>
<p>Assign two network adapters to the domain controller VM:</p>
<ul>
    <li><b>Adapter 1</b> (NAT): For internet access, connected to your home network.</li>
    <li><b>Adapter 2</b> (Internal Network): A private network where the domain controller and clients communicate.</li>
</ul>
<img src="https://imgur.com/UW9TUiQ.png" alt="Configure Network Adapters">
<img src="https://imgur.com/8t2cUHC.png" alt="Configure Network Adapters">

<h3>5. Set Up IP Addresses</h3>
<p><b>Internal Adapter:</b> Assign a static IP (e.g., 172.16.0.1) and subnet mask (255.255.255.0) to the internal network adapter. Configure DNS to point to the domain controller’s IP or the loopback address <code>127.0.0.1</code>.</p>
<img src="https://imgur.com/xK6jTtd.png" alt="Set Up IP Addresses">

<h3>6. Rename and Restart the Domain Controller</h3>
<p>Rename the server to “DC” and restart it to apply network settings.</p>
<img src="https://imgur.com/6Cn76Kn.png" alt="Rename and Restart the Domain Controller">

<h3>7. Install Active Directory Domain Services (AD DS)</h3>
<p>In the Server Manager, add the “Active Directory Domain Services” role. Create a new forest and domain (e.g., <code>mydomain.com</code>). Configure DNS as part of the AD installation.</p>
<img src="https://imgur.com/acodU6Q.png" alt="Install Active Directory Domain Services">
<img src="https://imgur.com/240cmfi.png" alt="Install Active Directory Domain Services">

<h3>8. Create an Administrator Account in Active Directory</h3>
<p>In Active Directory, create a new organizational unit (OU) for admin accounts and add a dedicated domain admin account. This account will be used to manage the domain instead of the default Administrator account.</p>
<img src="https://imgur.com/IvgH7tU.png" alt="Create Administrator Account in AD">
<img src="https://imgur.com/qmP4ULH.png" alt="Create Administrator Account in AD">

<h3>9. Configure DHCP and Routing</h3>
<p>Set up DHCP on the domain controller to assign IP addresses automatically to the client machines on the internal network. This configuration will simulate a typical network environment where clients can connect to the domain and reach the internet.</p>
<img src="image_link_for_DHCP_configuration.png" alt="Configure DHCP and Routing">

<h3>10. Automate User Creation with PowerShell</h3>
<p>Download a PowerShell script to create multiple user accounts in Active Directory. The script pulls names from a text file and programmatically creates each user, assigning a default password. You can add yourself as the first user in the list to test logins later.</p>
<img src="image_link_for_PowerShell_script.png" alt="Automate User Creation with PowerShell">

<h3>11. Create the Windows 10 Client VM</h3>
<p>Set up a second VM for the client machine with the Windows 10 ISO. Assign it only one network adapter connected to the internal network. Once the Windows 10 setup is complete, add the client to the domain and use the credentials created in the PowerShell script to log in.</p>
<img src="image_link_for_client_VM_creation.png" alt="Create Windows 10 Client VM">

<h3>12. Verify Network Connectivity</h3>
<p>On the client machine, verify that it can reach the domain controller and the internet. Check IP configurations with <code>ipconfig</code> and ping internal addresses (like <code>mydomain.com</code>) to confirm everything is working.</p>
<img src="image_link_for_network_connectivity_test.png" alt="Verify Network Connectivity">

<h2>Key Takeaways</h2>
<p>This project is an excellent way to understand the fundamentals of Active Directory and Windows networking. It simulates a basic network environment where you can learn how user authentication, IP allocation, and domain management work. Here are some skills and insights you’ll gain from this lab:</p>
<ul>
    <li><b>Network Configuration:</b> Working with NAT, internal networks, and static IP assignments.</li>
    <li><b>Active Directory Management:</b> Creating OUs, users, and managing AD roles and permissions.</li>
    <li><b>PowerShell Automation:</b> Using scripts to automate administrative tasks in AD.</li>
</ul>

<h2>Final Thoughts</h2>
<p>Building this lab environment gives you practical experience that translates well to enterprise environments. It's a great addition to your resume, demonstrating a working knowledge of Active Directory and network setup. This lab setup can also serve as a foundation for learning more about group policies, security monitoring, and penetration testing in a controlled environment.</p>

<p>Give this a try and see how much you learn! For future projects, you can expand this lab by adding more clients or testing different configurations.</p>

</body>
</html>
