#  Azure Policy Lab – Cloud Governance Gone Rogue

##  Course
**CST8919 – DevOps Security and Compliance**  
**Lab Title**: Enforcing Organizational Policies in the Cloud

##  Scenario
This lab shows how to enforce compliance rules within Azure to establish cloud governance using **Azure Policy**. I established unique policies, organized them into an initiative, and verified their functionality through several deployment tests while posing as a recently hired Cloud Security Engineer at **MapleTech Solutions**.

##  Summary of the Lab
In MapleTech Solutions, developers did not control resources, instead, they were deploying blindly, their resources lacked tags, they used public IP addresses and even deployed in more than one region. As the new-joining **Cloud Security engineer**, my responsibility included the construction of guardrails on **azure policy** to apply company standards.

The following policies have been developed and tried:
Keep all resource deployments to the center of Canada
Will also need a **ProjectName** tag on all resources
Deny public IP address creation

These were all put under a **Policy Initiative** called `MapleTech Secure Foundation` and put under a resource group with mode set to **Enforce (Deny)**.

---
## Policy Description

~Only-CanadaCentral` ### 1.  
- **Type**: Particular Policy  

**Aim**: Prevents the deployment of resources beyond of the {canadacentral` region. 
**Effect**: Deny.  
Data residency is guaranteed, and multi-region expansion is decreased.

### 2. `ProjectName-Tag-Require`  
**Effect**: Deny - 
**Type**: Custom Policy  

All resources must have a `ProjectName` tag in order to achieve the goal.  
**Justification**: Encourages identification for resource ownership and cost control.

### 3. `Deny-Public-IP`  
**Effect**: Deny - 
**Type**: Custom Policy  

The creation of all publicly accessible IP resources is blocked.  
**Justification**: Improves security posture and lowers external exposure.

##  Test Results Summary

| Test Action | Result |
|-------------|--------|
| Deploy VM in East US | ❌ Denied |
| Deploy Storage without tag | ❌ Denied |
| Create Public IP | ❌ Denied |
| Deploy VM in Canada Central with ProjectName tag | ✅ Allowed |

##  Video Demo
https://youtu.be/5MUAYOA5_JI


### The facing challenges
Obtaining the right JSON schema of custom policies.
Enforcement behavior-comprehending in the process of designating policy
Failures in testing that do not have to affect quota limits

Lessons Learned
Azure Policy is not only needed to detect non-compliant deployments but to prevent such non-compliances.
Having them grouped as policies under initiatives makes managing and control easier.
Custom policies allow business-aligned controls to be implemented.
The Tags are important in monitoring costs and characterizations of resources.


