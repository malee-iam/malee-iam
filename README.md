# Hi, I'm Malee 👋

I am building hands-on experience in Identity and Access Management (IAM) and cybersecurity, with a focus on identity administration, directory integration, authentication, access control, and troubleshooting. 
I am developing hands-on skills in Identity and Access Management (IAM) and cybersecurity through practical labs using Okta, Microsoft Active Directory, and Windows Server.

My current learning focuses on identity administration, authentication, access control, directory integration, user and group management, and technical troubleshooting as I work toward a career in IAM and cybersecurity

## Education
 Bachelor of Science in Forensic Psychology
 
Grand Canyon University

##  Current Focus

- Identity and Access Management (IAM)
- Okta Administration
- Microsoft Active Directory
- User and Group Management
- Directory Integration
- Profile and Attribute Mapping
- Identity Synchronization
- Cybersecurity Fundamentals

##  Hands-On Lab Experience

### Okta + Active Directory IAM Lab
I built and documented a hands-on IAM lab integrating Okta with Microsoft Active Directory.

The project includes:
- Active Directory integration with Okta
- Okta AD Agent configuration
- User and group imports
- Profile and attribute mapping
- Directory synchronization
- Troubleshooting agent connectivity and time synchronization issues
- Verification of operational agent connectivity

➡️ [View the Okta + Active Directory IAM Lab](https://github.com/malee-iam/okta-active-directory-iam-lab)
### Windows Server + Active Directory Lab
I built and documented a Windows Server and Active Directory lab environment to develop hands-on experience with domain controller configuration, organizational units, users, groups, directory administration, and troubleshooting.

➡️ [View the Windows Server + Active Directory Lab](https://github.com/malee-iam/windows-server-active-directory-lab)
## Just-in-Time (JIT) Provisioning

After successfully configuring delegated authentication between Okta and Active Directory, I enabled **Just-in-Time (JIT) provisioning** to automate user creation during a user's first login.

### Configuration

JIT provisioning was configured in the Active Directory integration by enabling **Create and update users on login**.

This allows an eligible Active Directory user to be automatically created in Okta after successfully authenticating through the Okta AD Agent.

### JIT Provisioning Test

To validate the configuration, I created a new test user, **Maya Thompson**, directly in Active Directory on `IAM-DC01`.

The user was intentionally **not manually imported into Okta** before testing.

I then:

1. Attempted the user's first Okta login using the Active Directory credentials.
2. Okta sent the authentication request through the Okta AD Agent.
3. Active Directory successfully validated the credentials.
4. JIT provisioning automatically created the user's Okta account.
5. The user enrolled in Okta Verify for MFA.
6. The user successfully accessed the Okta end-user dashboard.
7. The newly provisioned account was verified as **Active** in Okta.

### Validation

The successful test demonstrated the following identity flow:

**Active Directory → Okta AD Agent → Delegated Authentication → JIT Provisioning → Okta Verify → Okta Dashboard**

No manual Active Directory import was required to create the user's Okta identity.

### Screenshots

**JIT provisioning enabled**

<!-- Drag jit-provisioning-enabled.png directly below this line -->


**JIT-provisioned user successfully created and Active in Okta**

<!-- Drag jit-provisioning-user-active.png directly below this line --><img width="1770" height="181" alt="jit-provisioning-enabled" src="https://github.com/user-attachments/assets/c0b3a30a-a020-4845-a099-09a7a80f8de2" />



<img width="1762" height="90" alt="jit-provisioning-user-active" src="https://github.com/user-attachments/assets/f75b54c3-4e95-4b72-8d8d-5b63763848a3" />




##  Currently Learning

- Okta Identity and Access Management
- Identity lifecycle management
- Authentication and access control
- Security+ concepts
- Cybersecurity fundamentals

##  Career Goal

I am developing practical IAM and cybersecurity skills with the goal of pursuing opportunities in Identity and Access Management and cybersecurity.

##  Portfolio Development

This GitHub profile documents my hands-on labs, troubleshooting experience, and continued development in IAM and cybersecurity.
