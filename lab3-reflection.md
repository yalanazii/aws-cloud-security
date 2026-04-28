# Lab 03 – AWS Cloud Security Fundamentals Reflection

## IAM

In this part of the lab, I focused on Identity and Access Management, which is used to control who can access AWS resources and what actions they are allowed to perform. I first checked the root account and verified whether MFA was enabled, which is important because the root account has full access to everything. Using the root account is risky because if it gets compromised, the attacker would have full control over the entire environment.

I then created a restricted IAM user and added it to a group with limited permissions. Instead of giving full administrator access, I used a more restricted policy, which follows the principle of least privilege. This means that the user only has the permissions needed to perform specific tasks and nothing more. This reduces the risk of misuse or damage if the account is compromised.

---

## S3

In this part, I created an S3 bucket and made sure that “Block all public access” was enabled. S3 is used to store data, and if it is not properly configured, it can become publicly accessible, which can lead to data leaks.

By enabling block public access, I made sure that no one from the internet can access the data inside the bucket. This is an important security control because it prevents accidental exposure of sensitive data. Even though I did not upload any data, this configuration is still important because it ensures that the bucket is secure by default.

---

## EC2

In this part, I launched a basic EC2 instance and focused on securing it using a security group. I created a security group that only allows SSH access from my own IP address instead of allowing access from anywhere. This is important because opening access to 0.0.0.0/0 would allow anyone on the internet to attempt to connect to the instance.

I also checked the instance metadata service, which can be used to retrieve credentials from the instance. If not properly secured, attackers can exploit this using SSRF attacks to gain access to sensitive information. Restricting access and using secure configurations helps reduce this risk.

---

## Monitoring, Logging, and Billing

In this part, I reviewed the billing dashboard and services like CloudTrail. The billing dashboard helps track costs and can also be used to detect unusual activity, such as unexpected charges that may indicate a compromise.

CloudTrail is used to log API activity, which allows you to see who is doing what in the AWS account. This is important because it provides visibility into actions taken in the environment. Without logging and monitoring, it would be difficult to detect attacks or suspicious behavior.

---

## Capital One Connection

These configurations are directly related to the Capital One breach. In that case, attackers were able to exploit a vulnerability and gain access to credentials because of misconfigurations and lack of proper controls.

For example, using least privilege in IAM limits what an attacker can do if credentials are compromised. Blocking public access in S3 prevents large amounts of sensitive data from being exposed. Restricting EC2 access and properly configuring instance metadata helps prevent SSRF attacks, which were part of the breach. Logging with CloudTrail also helps detect suspicious activity faster, reducing the time attackers can stay undetected.

---

## Critical Analysis

Overall, some parts of this lab were straightforward, such as creating an S3 bucket and enabling block public access, while other parts like configuring IAM and security groups required more attention to detail. It is easy to make mistakes in these areas, especially with permissions and network rules, which can lead to serious security risks.

This lab also shows that security is not just about having the right tools, but also about how they are configured and managed. Even though AWS provides many security features, they can still be misconfigured if not used properly. This highlights the importance of good security practices and organizational awareness to ensure that these controls are implemented correctly.
