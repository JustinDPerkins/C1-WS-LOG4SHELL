# C1-WS-LOG4SHELL
This is a learning application. Thank you [christophetd](https://github.com/christophetd/log4shell-vulnerable-app) for providing the vulnerable Spring Boot web application.

# Cloud One - Workload Security
This repo contains a quick deployment template to showcase CVE-2021-44228 LOG4SHELL exploit and Workload Security Intrusion Prevention

## Deploy CloudFormation Template

Parameters to Define:
- KeyPair: name of a current Key Pair

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)]()

## After CloudFormation Template Deployment

1. SSH into EC2 instance(Shell A)
    ```bash
    sudo su
    <Deploy Workload Security Agent deployment script with Linux Policy attached.>
    ```

2. In CLoud One-WS: Assign IPS rule for CVE-2021-44228 to linux machine
    - ips rule number: 1011242
    - assign rule and change to Detect Onle for now.
    - accept any rule dependencies.

3. Start docker app

```bash
cd log4shell-vulnerable-app
docker run -p 8080:8080 --name vulnerable-app vulnerable-app
```

4. Open Second SSH session(Shell B) and run command to create LDAP server
* [JNDIExploit](https://github.com/feihong-cs/JNDIExploit/releases/tag/v1.2) provided by feihong-cs before it was removed from GitHub.
```bash
java -jar JNDIExploit-1.2-SNAPSHOT.jar -i your-private-ip -p 8888
```
