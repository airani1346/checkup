<b>About</b></br>
Create Management Server, Security Gateway and Honey Pot over AWX.</br>
all parameter has to be defined in AWX Workflow Survey</br>

<b>Overview</b></br>
This repository contains all ansible scripts to .</br>
zerops.ps1</br>

<b>Requirements</b></br>
AWX Server</br>


<b>Usage</b></br>
create a AWX Workflow </br></br>

define survey Variables in your Workflow</br>

cp_version , Type text, Default R81</br>
vpc_title, Type text, Default CloudCheckup</br>
vpc_name, Type text, Default CloudCheckupVPC</br>
igw_name, Type text, Default CloudCheckupIGW</br>
route_name, Type text, Default CloudCheckupRouteName</br>
subnet_name1, Type text, Default CloudCheckupExternalSubnet</br>
subnet_name2, Type text, Default CloudCheckupInternalSubnet</br>
subnet_name3, Typetext, Default CloudCheckupHoneyPotSubnet</br>
acl_name, Type text, Default CloudCheckupACL</br>
security_group_name, Type text, Default CloudCheckupSecurity Group</br>
route_table_name, Type text, Default CloudCheckuproute table</br>
vpc_cidr, Type text, Default 10.5.0.0/16</br>
subnet_cidr1, Type text, Default 10.5.1.0/24</br>
subnet_cidr2, Type text, Default 10.5.2.0/24</br>
subnet_cidr3, Type text, Default 10.5.3.0/24</br>
port22CidrBlock, Type text, Default 0.0.0.0/0</br>
destinationCidrBlock, Type text, Default 0.0.0.0/0</br>
mgmt_hw, Type text, Default m5.xlarge</br>
mgmt_net1_ip, Type text, Default 10.5.1.11</br>
mgmt_passwd, Type text, Default <put your password></br>
mgmt_server_name, Type text, Defaul tmgmt1</br>
mgmt_sic_key, Type text,  Default vpn123</br>
gateway_hw, Type text, Default c5.large</br>
gateway_net1_ip, Type text, Default 10.5.1.10</br>
gateway_net2_ip, Type text, Default 10.5.2.10</br>
gateway_passwd, Type text, Default <put yout password></br>
gateway_Name, Type text, Default vsecgwr80</br>
gateway_sic_key, Type text, Default vpn123</br>
hp_hw, Type text, Default t2.medium</br>
hp_net3_ip, Type text, Default 10.5.3.33</br>
state, Type text, Default present</br>
region, Type text, Default eu-central-1</br>
keypairName, Type text, Default aws-key</br>

and put the git yaml files in flowing order in your workflow</br>

- createVPC.yml -(on-success)-> createIGWandNetworks.yml -(on-success)-> createSecurityGroups.yml -(on-success)-> (parallel start launchManagement.yml, launchHoneyPot.yml, launchGateway.yml)
