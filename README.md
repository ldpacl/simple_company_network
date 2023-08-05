<h1>Simple Company Network using Cisco Packet Tracer</h1>
<h2>Problem Statement</h2>
<p>XYZ company is a fast-growing comapany in Bangalore with more than 2 million customers globally. The company deals with selling and buying food items, which are basically operated from the headquarters. The company is intending to open a branch near the local village. Thus, the company requires young IT graduates to design the network for the branch. The network is intended to operate separately from the HQ network.</p>
<p>Being a small network, the company has the following requirements during implementation</p>
<ol>
  <li>One router and one switch to be used(all CISCO products).</li>
  <li>3 departments(Admin/IT, Finance/HR and Customer service/Reception).</li>
  <li>Each department is required to be in different VLANS.</li>
  <li>Each department is required to have wireless network for the users.</li>
  <li>Host devices in the network are required to obtain IPv4 address automatically.</li>
  <li>Devices in all the departments are required to communicate with each other.</li>
</ol>
<p>Assume the ISP gave out a base network of 192.168.1.0, design and implement a network considering the above requirements</p>
<h2>Solution:</h2>
<p>
  <pre>
    Network address: 192.168.1.0        Subnet mask: 255.255.255.192
    Number of Subnets = 3
    2^n=3    Therefore n=2(number of borrowed bits)
  </pre>
  <p>New subnet mask: 255.255.255.192</p>
  <p>Block size = 64</p>

  <h4>1st Subnet</h4>
  <table>
    <tr>
      <td>Network ID</td>
      <td>192.168.1.0</td>
    </tr>
    <tr>
      <td>Broadcast ID</td>
      <td>192.168.1.63</td>
    </tr>
    <tr>
      <td>Host range</td>
      <td>192.168.1.1 - 192.168.1.62</td>
    </tr>
  </table>
  <h4>2nd Subnet</h4>
  <table>
    <tr>
      <td>Network ID</td>
      <td>192.168.1.64</td>
    </tr>
    <tr>
      <td>Broadcast ID</td>
      <td>192.168.1.127</td>
    </tr>
    <tr>
      <td>Host range</td>
      <td>192.168.1.65 - 192.168.1.126</td>
    </tr>
  </table>
  <h4>3rd Subnet</h4>
  <table>
    <tr>
      <td>Network ID</td>
      <td>192.168.1.128</td>
    </tr>
    <tr>
      <td>Broadcast ID</td>
      <td>192.168.1.191</td>
    </tr>
    <tr>
      <td>Host range</td>
      <td>192.168.1.129 - 192.168.1.190</td>
    </tr>
  </table>
</p>
<h3>Configuring VLAN in switch</h3>
<p><pre>
  en
  conf t
  int range fa 0/2-4
  switchport access vlan 10
</pre></p>
<p>Repeat the above steps for all other VLANs</p>
<p><pre>
  do wr
  do show start
</pre></p>
<h3>Configuring Access Points</h3>
<p><pre>
  click on AP
  go to port 1
  type SSID of choice
  click WPA2-PSK
  type pass phrase of choice
</pre></p>
<p>Repeat the above steps for all other APs</p>
<h3>Trunking of VLAN</h3>
<p><pre>
  int fa 0/1
  switchport mode trunk
</pre></p>
<h3>Router Configuration</h3>
<p><pre>
  en
  int gig 0/0
  no shutdown
  do wr
</pre></p>
<h4>Configuring sub-interface for vlans</h4>
<p><pre>
  int gig 0/0.10
  encapsulation dot1Q 10
  ip address 192.168.1.1 255.255.255.192
  exit
</pre></p>
<p>Repeat the above steps for all other subinterfaces</p>
<h4>Configuring DHCP service</h4>
<p><pre>
  conf t
  service dhcp
  ip dhcp pool Admin-Pool
  network 192.168.1.0 255.255.255.192
  default-router 192.168.1.1
  dns server 192.168.1.1
  domain-name Admin.com
  exit
</pre></p>
<p>Repeat the above steps for all other subinterfaces</p>
<h3>Checking DHCP</h3>
<p><pre>
  go to host
  click in ip coonfiguration
  enable dhcp
  check if the host is getting it's ip address automatically
</pre></p>
<p>Check for all the hosts</p>
<h3>Connecting wirelessly to Acess Points</h3>
<h4>Laptop</h4>
<p><pre>
  poweroff
  remove module
  insert wifi module
  power on 
  go to desktop
  go to wireless
  select SSID
  type password
</pre></p>
<h4>Smartphone</h4>
<p><pre>
  go to config
  go to wireless0
  type SSID
  type password
</pre></p>
<h3>Checking connectivity between hosts</h3>
<p><pre>
  ping host-ipaddress
</pre></p>
