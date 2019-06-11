# AWS-VGW-PANOS
Configure IKE/IPSec + BGP for PAN-OS and connect to AWS Virtual Private Gateway

## Brief Description
This skillet will configure IKE/IPSec parameters and BGP in order to connect PAN-OS to AWS VPN Gateway.

## Skillet Details
- Authoring Group: Public Cloud, Networking, IPSec.
- Documentation: AWS VGW IPSec PANOS.pdf
- Github Location: https://github.com/cestebanez91/AWS-VGW-PANOS
- PAN-OS Supported: 8.1.0 minimum
- Cloud Provider(s) Supported:  AWS only dedicated
- Type of Skillet: PAN-OS, multiple xml.
- Purpose: Config

## Detail Description
This skillet will be used to connect your Palo Alto Network device (physical or VM-series) to any AWS Virtual Private Gateway to establish an IPSec connection.
Based on parameters given by AWS (AWS VGW public IP addresses, BGP peer...).
It will create two new IKE gateways and two new Ipsec tunnels, whatever this is already existing, iteration is possible up to four IKE gateways and four IPSec tunnels.
IKE and IPSec profile are compliant to AWS VGW expectations.

This skillet will configure PAN-OS with following features:
-	IKE crypto profile compliant with AWS VGW
-	IPSec crypto profile compliant with AWS VGW
-	IKE gateways to connect to AWS VGW
-	IPSec tunnels
-	Tunnel interfaces,and Zone "VPN"
-	Routing and BGP configuration with distribution profile activated for connected routes

## Content is the following:
-	ikecrypto.xml will configure IKE crypto profile
-	ipseccrypto.xml will configure IPSec crypto profile
-	ikeprofile.xml will configure IKE gateways with iteration
-	ipsecprofile.xml will configure IPSec tunnels with iteration
-	interface.xml will configure tunnels interfaces
-	zone.xml will configure zone
-	routing.xml will configure BGP parameters to exchange routes



# Prerequisite
In order to run this skillet, you need a running default configuration for PAN-OS and AWS.
## PAN-OS
- VM-Series or physical device running PAN-OS 8.1 running
- untrust and trust interfaces configured
- Default route configured for untrust subnet gateway
- untrust interface is binded to a Public ip address
- Security Policies to allow outbound traffic

## AWS
- VPC and Virtual Private Gateway deployed and attached to a VPC
- AWS Customer Gateway configured
- AWS VPN Site-to-Site VPN connection configured with configuration file downloaded for PAN-OS



# Support Policy
The code and templates in the repo are released under an as-is, best effort, support policy. These scripts should be seen as community supported and Palo Alto Networks will contribute our expertise as and when possible. We do not provide technical support or help in using or troubleshooting the components of the project through our normal support options such as Palo Alto Networks support teams, or ASC (Authorized Support Centers) partners and backline support options. The underlying product used (the VM-Series firewall) by the scripts or templates are still supported, but the support is only for the product functionality and not for help in deploying or using the template or script itself. Unless explicitly tagged, all projects or work posted in our GitHub repository (at https://github.com/PaloAltoNetworks) or sites other than our official Downloads page on https://support.paloaltonetworks.com are provided under the best effort policy.
