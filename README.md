# C1-WS-LOG4SHELL

# Cloud One - Workload Security
This repo contains a quick deployment template to showcase CVE-2021-44228 LOG4SHELL exploit and Workload Security Intrusion Prevention

## Deploy CloudFormation Template

Parameters to Define:
- EnvironmentName:
- KeyPair: name of a KeyPair
- PublicSubnet1CIDR: VpcCIDR


## After CloudFormation Template Deployment

1. SSH into EC2 instance and deploy Workload Security Agent with Linux Policy attached.
2. Start docker app
3. Run recommendation Scan or manually Assign IPS rule for CVE-2021-44228
4. Open Second SSH session and run command to create LDAP server
