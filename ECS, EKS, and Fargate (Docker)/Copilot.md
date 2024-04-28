- tool to help build, release, and operate production-ready containerized applications
- provisions and helps you build the infrastructure so that you can focus on building applications.
- uses CloudFormation to provision the resources needed for your application

![[Pasted image 20240428104529.png]]



**Copilot commands**

**Initialize Copilot**
`copilot init`

![[Pasted image 20240428110626.png]]

**Creation of Copilot Environments**
`copilot env init --name prod --profile default --app copilot-guide`
![[Pasted image 20240428110831.png]]
![[Pasted image 20240428110022.png]]

**Deploy your Application to Copilot**
`copilot env deploy --name prod`

`copilot deploy`
![[Pasted image 20240428111218.png]]

**Copilot Clean Up**
`copilot app delete`