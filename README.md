# AWS IAM Access Control Project

## Minor Project – 2

**AWS Identity and Access Management (IAM)**  
**Implementation, Access Control and Permission Validation**

**Student:** Dalia Mahata  
**Project:** AWS IAM  
**Platform:** Amazon Web Services  
**Submission Date:** 04 September 2026

## 1. Introduction

AWS Identity and Access Management (IAM) is used to manage authentication and authorization for AWS resources.

In this project, different IAM users were assigned policies according to their responsibilities. Selected permissions were then tested using the IAM Policy Simulator.

## 2. Objectives

- Create and configure IAM users and groups.
- Assign customer-managed and AWS-managed policies.
- Implement role-based access control.
- Test selected AWS actions using the Policy Simulator.
- Document successful, denied and resource-dependent validation results.

## 3. Project Configuration

| User | Policy / Configuration |
|---|---|
| developer1 | Developers-S3-Policy; attached directly and through Developers group |
| developer2 | Developers-S3-Policy + IAMUserChangePassword |
| devops1 | DevOps-EC2-Operations-Policy through DevOps group |
| auditor1 | ReadOnlyAccess |

## 4. IAM Implementation

The project was implemented using the AWS IAM console.

The configured IAM users, groups and permissions were verified through the AWS console.

## 5. Permission Simulator Results

The following tests were performed using the IAM Policy Simulator.

| User | Action | Result |
|---|---|---|
| developer1 | S3: PutObject | Denied — implicit deny in captured test |
| developer1 | S3: DeleteBucket | Denied — implicit deny |
| devops1 | EC2: TerminateInstances | Allowed — explicit allow |
| auditor1 | EC2: RunInstances | Result blank; 5 resource types required |

## 6. Simulator Limitations

Some IAM actions require resource-specific values before the simulator can return a final decision.

In the captured tests, S3 PutObject and EC2 RunInstances did not produce the intended final validation state. These outputs are recorded as simulator/resource-validation limitations and are not presented as proof that the underlying IAM configuration is incorrect.

## 7. Conclusion

The project demonstrates practical AWS IAM access control using users, groups and policies.

Developers were given S3-related permissions, the auditor was configured with read-only access, and the DevOps user received EC2 operational permissions.

The simulator successfully confirmed the explicit allow for devops1 to perform EC2 TerminateInstances and also showed denied actions for developer1.

The collected screenshots provide implementation and validation evidence.

## 8. Project Report

The complete project report is available here:

**[Minor Project 2 – AWS IAM PDF](./Minor_Project_2_AWS_IAM.pdf)**

## 9. References

- Amazon Web Services — IAM Console
- AWS Identity and Access Management documentation
- AWS IAM Policy Simulator
