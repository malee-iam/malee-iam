# Hi, I'm Malee 👋

I am building hands-on experience in Identity and Access Management (IAM) and cybersecurity, with a focus on identity administration, directory integration, authentication, access control, and troubleshooting. 
I am developing hands-on skills in Identity and Access Management (IAM) and cybersecurity through practical labs using Okta, Microsoft Active Directory, and Windows Server.

My current learning focuses on identity administration, authentication, access control, directory integration, user and group management, and technical troubleshooting as I work toward a career in IAM and cybersecurity

## Education
 Bachelor of Science in Forensic Psychology
 
Grand Canyon University

## Current Focus

- Identity and Access Management (IAM)
- Okta Administration
- Microsoft Active Directory
- Identity Lifecycle Management (Joiner, Mover, Leaver)
- Authentication and Authorization
- Multi-Factor Authentication (MFA)
- Single Sign-On (SSO) and SAML 2.0
- User and Group Administration
- Directory Integration and Synchronization
- Profile and Attribute Mapping
- Just-in-Time (JIT) Provisioning
- Application Access and Provisioning
- IAM Troubleshooting and Root-Cause Analysis
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

###  Project Overview

This project simulates an enterprise Identity and Access Management (IAM) environment integrating Microsoft Active Directory with Okta. The lab was designed to practice identity administration, directory integration, authentication, user and group management, profile and attribute mapping, access provisioning, and IAM troubleshooting.

Rather than focusing only on configuration, this project documents the business purpose, implementation, validation, troubleshooting, and evidence used to verify that each identity process functions as expected.

## Business Scenario

A simulated organization requires centralized identity management between its on-premises Microsoft Active Directory environment and Okta.

Active Directory serves as the directory source for workforce identities, while Okta provides cloud-based identity, authentication, and application access capabilities.

The IAM implementation must support:

- Centralized user and group management
- Directory synchronization between Active Directory and Okta
- Secure user authentication
- Profile and attribute mapping
- Multi-factor authentication (MFA)
- Application access assignment
- Just-in-Time (JIT) provisioning
- Single Sign-On (SSO)
- Identity lifecycle management
- Troubleshooting and validation of IAM events

The environment is used to simulate common enterprise IAM administration and troubleshooting scenarios.

## Lab Environment

| Component | Purpose |
|---|---|
| Microsoft Active Directory | On-premises identity directory |
| Windows Server 2025 | Hosts Active Directory Domain Services |
| IAM-DC01 | Domain Controller |
| IAMLAB.TEST | Active Directory domain |
| Okta | Cloud Identity and Access Management platform |
| Okta Active Directory Agent | Connects Active Directory with Okta |
| Okta Verify | Multi-factor authentication |
| SAML 2.0 | Federated authentication / Single Sign-On |


## Project Objectives

The objectives of this lab are to:

- Configure an Active Directory environment for IAM practice
- Integrate Microsoft Active Directory with Okta
- Install and validate the Okta Active Directory Agent
- Import and manage users and groups
- Configure profile and attribute mappings
- Validate directory synchronization
- Configure delegated authentication
- Implement Just-in-Time (JIT) provisioning
- Configure and test Multi-Factor Authentication (MFA)
- Configure application access
- Implement and validate SAML 2.0 Single Sign-On
- Practice IAM troubleshooting and root-cause analysis
- Capture technical evidence showing successful IAM operations


  ## Identity Architecture

The primary identity flow used throughout the lab is:

**Active Directory → Okta AD Agent → Okta → Authentication / Provisioning → Applications**

### Authentication Flow

**User → Okta → Okta AD Agent → Active Directory → Authentication Result → Okta**

### Federated Application Access

**Active Directory User → Okta → SAML Assertion → Service Provider → Application Access**

## IAM Implementation

The following IAM capabilities were implemented and validated throughout the project:

- Active Directory user and group administration
- Okta Active Directory Agent integration
- Directory user and group imports
- Profile and attribute mapping
- Directory synchronization
- Delegated authentication
- Just-in-Time (JIT) provisioning
- Okta Verify / MFA enrollment
- Application assignment and access provisioning
- SAML 2.0 Single Sign-On
- Secure Web Authentication (SWA)
- Profile sourcing and attribute-level sourcing
- Self-service application access



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


## SAML 2.0 Single Sign-On (SSO)

I configured and tested SAML 2.0 Single Sign-On between Okta and a SAML Service Provider to demonstrate federated authentication.

### SAML Configuration

Okta was configured as the Identity Provider (IdP), while IAMShowcase was used as the Service Provider (SP).

The SAML integration included:

- Assertion Consumer Service (ACS) URL configuration
- Service Provider Entity ID configuration
- User assignment to the SAML application
- Okta username as the federated identity
- SAML assertion-based authentication

### Authentication Flow

Active Directory User → Okta AD Agent → Okta → SAML Assertion → Service Provider → Successful Federation

### Troubleshooting

During initial testing, the SAML application failed to reach the Service Provider and returned a connection timeout.

I reviewed the destination endpoint and identified an incorrect hostname in the ACS URL. After correcting the ACS endpoint and retesting the application, the SAML authentication flow completed successfully.

This troubleshooting process demonstrated the importance of validating SAML endpoints when diagnosing federation failures.

### SAML Validation

The assigned Active Directory user authenticated through Okta and launched the SAML application from the Okta dashboard.

Okta generated the SAML authentication response, and the Service Provider successfully accepted the federated identity.

<img width="1577" height="456" alt="SAML -SSO-successful-federation" src="https://github.com/user-attachments/assets/b60413cc-58db-40ca-9c44-6416f2f4888f" />


### Result

SAML 2.0 Single Sign-On was successfully validated between Okta and the Service Provider.

The completed authentication workflow demonstrated:

**Active Directory → Okta AD Agent → Delegated Authentication → Okta → SAML 2.0 → Service Provider**

This lab demonstrated hands-on experience configuring, testing, and troubleshooting federated authentication using SAML 2.0.

## Secure Web Authentication (SWA) Integration

I configured a custom Secure Web Authentication (SWA) application in Okta to practice credential-based Single Sign-On for applications that do not support federated authentication protocols such as SAML or OIDC.

### SWA Application Configuration

Using Okta's Classic App Integration experience, I created a custom internal application named **MyFictionalApp** and configured Secure Web Authentication (SWA) as the sign-in method.

The integration was configured with:

- Sign-in method: Secure Web Authentication (SWA)
- Application type: Internal application
- Credential management: Administrator sets username; password is the same as the user's Okta password
- Application username: Okta username
- Application username update behavior: Default

A fictional login URL was used for this training exercise.


<img width="1402" height="647" alt="okta-swa-custom-app-configuration" src="https://github.com/user-attachments/assets/80cdb47c-c8c5-43b7-a871-ef76f48a525a" />


### User Assignment and Access Provisioning

To practice application-level access provisioning, I assigned an existing lab identity, **Maya Thompson**, to MyFictionalApp.

The assignment granted the user an application entitlement without creating an additional Okta identity.

<img width="1357" height="687" alt="SWA-user-application-assignment" src="https://github.com/user-attachments/assets/853e54ce-d9c0-4950-b682-8e1bd14c7e2e" />


### SWA Authentication Model

Unlike SAML federation, where Okta sends a SAML assertion to a Service Provider, SWA uses application credentials with the application's existing login form.

**SWA Flow:**

User → Okta → Assigned SWA Application → Application Credentials → Application Login Form

### SAML vs. SWA

**SAML 2.0**

User → Okta → SAML Assertion → Service Provider → Access

**SWA**

User → Okta → Stored Application Credentials → Application Login Form → Access

This exercise reinforced the difference between federated SSO and credential-based SSO.

### Validation Status

The SWA application integration was successfully configured and an existing lab user was successfully assigned to the application.

Because the exercise used a fictional application URL, live authentication to the external application was not tested.

### Result

This lab demonstrated hands-on experience with:

- Creating a custom SWA application integration
- Configuring SWA credential settings
- Assigning an existing identity to an application
- Provisioning an application entitlement
- Comparing credential-based SSO with SAML federation

The exercise expanded the IAM lab beyond federated authentication and demonstrated another method Okta can use to provide application access.


## Self-Service Application Access and Approval Workflow

I configured and tested Okta Self Service to demonstrate a governed application access request and approval workflow.

Instead of manually assigning application access as an administrator, this workflow allowed an existing lab user to request access to an organization-managed application. The request was then routed to a designated approver for review.

### Self-Service Configuration

I enabled self-service access for the existing SAML application and configured the application to require approval before access could be granted.

This changed the access model from:

**Direct Assignment:**

Administrator → Application Assignment → User Access

**Self-Service Access:**

User → Application Request → Approver Review → Approval → Application Assignment → Access

### Application Access Request

An existing lab user who did not have the SAML application assigned submitted a self-service request for access.

The request entered the approval workflow and was routed to the designated approver.
<img width="882" height="442" alt="self-service-app-request- pending" src="https://github.com/user-attachments/assets/66fe08b6-33fd-448b-8da5-d163fa2f54f7" />

### Approval Review

The designated approver received the pending application request through the Okta Tasks workflow.

The approver reviewed the requested SAML application entitlement before making the access decision

<img width="1317" height="356" alt="self-service-app-approval-review" src="https://github.com/user-attachments/assets/99e954cc-cc3c-4494-b25d-ddfad54e1150" />




### Access Approval and Application Assignment

After the request was approved, Okta processed the access request and granted the application entitlement to the requesting user.

The application assignment was verified in Okta, confirming that access resulted from the approval workflow rather than a manual administrator assignment.

<img width="1380" height="105" alt="self-service-app-access-approved" src="https://github.com/user-attachments/assets/165ff13a-f4fe-416d-ae79-177386adbd90" />



### End-User Access Validation

After approval, the user signed back into the Okta End-User Dashboard and launched the newly approved SAML Service Provider application.

The application successfully federated the user to the Service Provider, confirming that the approved self-service request resulted in functional application access.

<img width="1707" height="462" alt="self-service-aproved-app-visible" src="https://github.com/user-attachments/assets/bca68e42-6f99-4182-a6fb-f39d2f218650" />


### Access Request Flow

User → Application Request → Approver Review → Approval → Application Assignment → SAML SSO → Access Granted

### Result

This exercise demonstrated hands-on experience with:

- Configuring self-service application access
- Requiring approval for application requests
- Delegating application approval responsibilities
- Submitting an application request as an end user
- Reviewing and approving an access request
- Validating the resulting application entitlement
- Confirming successful SAML access after approval



## Universal Directory: Profile Management and Attribute Mapping

I worked with Okta Universal Directory to understand how identity profiles and attributes are centrally managed across connected directories and applications.

Universal Directory provides a centralized identity profile layer where attributes can be defined, extended, mapped, and used across identity lifecycle workflows.

### Profile Editor

Using the Profile Editor, I reviewed the different identity profiles available in the Okta organization, including the Okta user profile, the connected Active Directory profile, and application-specific profiles.

This demonstrated how Okta can manage profile schemas from multiple identity sources and connected applications.


<img width="1325" height="835" alt="universal-directory-profile-editor-overview" src="https://github.com/user-attachments/assets/c76d1d08-1eba-4c41-803f-a4929b16aec5" />



### Custom Profile Attribute

I extended the Okta user profile by creating a custom attribute named `EmployeeType`.

The attribute was configured as a string with an enumerated list of allowed values:

- Employee
- Contractor

This type of custom attribute can be used to classify identities and support future access, mapping, provisioning, and lifecycle decisions.

<img width="1217" height="1007" alt="universal-directory-custom-attribute" src="https://github.com/user-attachments/assets/e655e896-f2d9-475c-be6e-810decccf188" />


### Custom Attribute Validation

After saving and applying the profile change, I reviewed the user profile schema and confirmed that `EmployeeType` appeared alongside existing attributes such as department, division, organization, manager, and cost center.

This confirmed that the custom attribute was successfully added to the Universal Directory profile.


<img width="1307" height="617" alt="universal-directory-profile-attribute-list" src="https://github.com/user-attachments/assets/09004e55-7ab8-46b1-9897-8642a310b1ab" />




### Attribute Mapping

After configuring the profile schema, I worked with attribute mappings between Active Directory and Okta Universal Directory.

Attribute mapping defines how identity information moves from a source profile to a target profile.

In this exercise, I mapped the Active Directory `sAMAccountName` attribute to the Okta `nickname` attribute.

The mapping flow was:

Active Directory `sAMAccountName` → Okta `nickname`

This demonstrated how source-directory identity data can populate or transform attributes in an Okta user profile.





<img width="1267" height="1046" alt="ad-to-okta-attribute-mapping" src="https://github.com/user-attachments/assets/91f87896-7780-41b8-98c3-b323b5762e25" />



### Attribute Mapping Validation

After saving and applying the mapping, I used Okta's mapping preview feature with an existing lab user.

The Active Directory `sAMAccountName` value was `mcarter`, and the preview confirmed that the value successfully mapped to the Okta `nickname` attribute as `mcarter`.

This validated the attribute mapping before relying on it in a broader identity workflow.




<img width="1212" height="437" alt="attribute-mapping-user-preview" src="https://github.com/user-attachments/assets/753f990d-d8b5-4592-975a-cea223205cea" />


### Identity Data Flow

Source Profile → Attribute Mapping → Target Profile

In this lab:

Active Directory → Okta Universal Directory

### Result

This exercise demonstrated hands-on experience with:

- Navigating Okta Universal Directory and Profile Editor
- Reviewing identity source and application profiles
- Extending the Okta user schema with a custom attribute
- Creating enumerated attribute values
- Validating custom profile attributes
- Configuring AD-to-Okta attribute mappings
- Using mapping preview to validate attribute transformations
- Understanding source and target identity profiles

The exercise reinforced the difference between three related IAM concepts:

- Profile management defines what identity attributes are available.
- Attribute mapping controls how those values move between systems.
- Provisioning uses identity information to create, update, or deactivate downstream accounts.



## Profile Sourcing and Attribute-Level Sourcing

I configured and tested profile sourcing in Okta to understand how an authoritative identity source controls user profile data across connected systems.

In this lab, Active Directory was configured as the primary profile source for AD-integrated users.

### Profile-Level Sourcing

Active Directory acted as the authoritative source for the user's profile.

Conceptually:

Active Directory → Okta Universal Directory

To validate profile sourcing, I updated an existing lab user's Title attribute in Active Directory to:

`IAM Lab Analyst`

After running an Active Directory import into Okta, the user's Okta profile reflected the updated Title value.

This demonstrated that changes made in the authoritative source were successfully propagated into Okta.


<img width="1690" height="557" alt="profile-sourcing-ad-authoritative-source" src="https://github.com/user-attachments/assets/b79b2895-66cb-436d-b5e1-83e597b91ff2" />


### Profile Sourcing Validation

After updating the user's Title in Active Directory and importing the directory changes, I verified that the Okta user profile reflected:

`Title = IAM Lab Analyst`

This confirmed that Active Directory was successfully sourcing the corresponding profile attribute into Okta.




<img width="887" height="862" alt="profile--sourcing-carter-title-validation" src="https://github.com/user-attachments/assets/a3e889f0-6311-48c8-898e-bfa84637bbd2" />


### Attribute-Level Sourcing

I also configured attribute-level sourcing to demonstrate how an individual attribute can use a different authoritative source than the user's overall profile.

While Active Directory remained the primary profile source, the Okta `nickname` attribute was configured to inherit from Okta.

I then changed the user's Nickname in Okta to:

`carter-lab`

After running another Active Directory import, the user's profile retained:

`Title = IAM Lab Analyst`

and

`Nickname = carter-lab`

This demonstrated that the Title continued to follow the Active Directory profile source, while the Nickname attribute remained controlled by Okta.




<img width="742" height="752" alt="attribute-level-sourcing-carter-validation" src="https://github.com/user-attachments/assets/49232032-2fec-4ed2-9220-026d4e549220" />



### Sourcing Model

Profile-Level Sourcing:

Active Directory → Okta User Profile

Attribute-Level Sourcing:

Active Directory → Most Profile Attributes

Okta → Nickname Attribute

### Result

This exercise demonstrated hands-on experience with:

- Configuring profile sourcing in Okta
- Using Active Directory as an authoritative identity source
- Validating profile updates from Active Directory to Okta
- Understanding profile-level sourcing
- Configuring attribute-level sourcing
- Assigning a different source to an individual profile attribute
- Validating that multiple authoritative sources can control different attributes within the same user profile

This lab reinforced the difference between profile sourcing and attribute-level sourcing.

Profile sourcing determines which system is authoritative for the user's overall profile, while attribute-level sourcing allows individual attributes to use a different authoritative source.




## Password Policy and Multifactor Authentication

I configured password and multifactor authentication controls in Okta to practice group-based security policy enforcement and MFA-protected application access.

### HR Password Policy

I created a dedicated password policy for the Human Resources group.

The policy was configured with:

- Assigned group: `HR-Users`
- Minimum password length: 10 characters
- Lowercase letter required
- Uppercase letter required
- Number required
- Symbol required

The remaining settings were left aligned with the existing default configuration.

This demonstrated how Okta can apply different password requirements to specific user populations.


<img width="1245" height="980" alt="okta-hr-password-policy-configuration" src="https://github.com/user-attachments/assets/33397cce-6bd7-4c21-a08a-fe65983bdbf0" />


### HR Password Policy Rule

I created an `HR Password Rule` to control self-service password operations for users governed by the HR password policy.

The rule allowed:

- Password change
- Password reset
- Account unlock

The rule applied from any network location and used the Okta account management authentication policy for recovery and account management operations.




### MFA Enrollment Policy

I created an MFA enrollment policy for the `IT-Users` group.

The policy required:

- Password
- Okta Verify

Email remained available as an optional authenticator.

A rule was added so the enrollment policy could be applied to the targeted users.


<img width="1267" height="890" alt="okta-mfa-enrollment-policyt-it-users" src="https://github.com/user-attachments/assets/7a393367-c8ce-4e7d-b4ff-2da4e77d272e" />



### MFA Sign-On Policy

I created an application sign-on policy named:

`IAM Lab MFA Sign-On Policy`

The policy used the enabled catch-all rule requiring:

`Any 2 factor types`

This required users accessing applications assigned to the policy to satisfy two authentication factors.


<img width="1330" height="852" alt="okta-mfa-two-factor-authentication=policy" src="https://github.com/user-attachments/assets/847d5b38-e8ee-44c1-a6fc-19e6acbff445" />



### SAML Application Assignment

I assigned the existing SAML Service Provider application to the MFA sign-on policy.

This connected the application's access requirements to the two-factor authentication policy.


<img width="1351" height="787" alt="okta-mfa-smal-app-policy-assignment" src="https://github.com/user-attachments/assets/c894f085-7e18-4c98-9ba2-c7ee7b8c1c74" />


### MFA-Protected SAML Access Validation

I tested the policy using an existing lab user.

The user authenticated using:

Password → Okta Verify

After satisfying both factors, the user launched the SAML Service Provider and successfully federated into the application.

This validated that MFA was enforced before SAML application access was granted.


<img width="1400" height="807" alt="okta-mfa-saml-access-validation" src="https://github.com/user-attachments/assets/74c164ac-17fe-42c7-b966-89b3f353938c" />



### Authentication Flow

IT User → Password → Okta Verify → MFA Satisfied → SAML Application → Access Granted

### Result

This exercise demonstrated hands-on experience with:

- Creating group-specific password policies
- Applying stronger password requirements to HR users
- Configuring password policy rules
- Enabling self-service password change, reset, and account unlock
- Creating MFA enrollment policies
- Requiring Password and Okta Verify enrollment
- Configuring application sign-on policies
- Enforcing two-factor authentication
- Assigning applications to authentication policies
- Validating MFA-protected SAML access

This exercise reinforced the difference between:

- Password policies: define password requirements
- Enrollment policies: define which authenticators users must enroll
- Authentication policies: define what factors users must actually present to access an application


## Troubleshooting and Root-Cause Analysis

Troubleshooting was documented throughout the IAM project to demonstrate not only successful configuration, but also the ability to identify, investigate, resolve, and validate identity-related issues.

Each troubleshooting scenario follows:

**Issue → Investigation → Root Cause → Resolution → Validation**



### Incident 01 — Okta AD Agent / Directory Synchronization

**Issue**

Directory integration and authentication did not initially operate as expected between Active Directory and Okta.

**Investigation**

The environment was reviewed by checking:

- Okta AD Agent operational status
- Active Directory connectivity
- Domain Controller configuration
- Windows Server date and time configuration
- Directory import behavior
- Authentication testing

**Root Cause**

Time synchronization between the Windows Server environment and the identity platform contributed to authentication and directory communication issues.

**Resolution**

The Windows Server time zone and time synchronization configuration were corrected and the environment was resynchronized.

**Validation**

- Okta AD Agent reported operational
- Active Directory users and groups were successfully detected
- Directory imports completed
- Authentication testing succeeded


### Incident 02 — SAML SSO Connection Failure

**Issue**

During initial SAML testing, the application failed to reach the Service Provider and returned a connection timeout.

**Investigation**

The SAML configuration and destination endpoint were reviewed, including the Assertion Consumer Service (ACS) URL.

**Root Cause**

An incorrect hostname was configured in the ACS endpoint.

**Resolution**

The ACS endpoint was corrected and the SAML authentication flow was tested again.

**Validation**

The assigned user successfully authenticated through Okta, the SAML assertion was accepted by the Service Provider, and federated application access completed successfully.



## Evidence and Validation

Successful configuration alone was not considered sufficient validation. Each major IAM workflow was tested to verify the expected identity behavior.

Evidence collected throughout the project includes:

- Okta AD Agent operational status
- Successful Active Directory user and group imports
- Profile and attribute mappings
- Successful delegated authentication
- JIT-provisioned user creation
- MFA enrollment and authentication
- Successful application assignment
- Successful SAML authentication
- Service Provider access confirmation
- Profile sourcing validation
- Self-service application access
- Troubleshooting before-and-after results

Screenshots included throughout this repository provide supporting technical evidence for the implemented IAM workflows.


## Identity Lifecycle Management

### Joiner → Mover → Leaver (JML)

This section documents an end-to-end employee identity lifecycle scenario across Active Directory and Okta.

The lifecycle will demonstrate how identity attributes and access requirements change throughout an employee's relationship with an organization.

### Joiner

- Create a new workforce identity
- Assign department and role attributes
- Provision appropriate group membership
- Provide required application access
- Validate authentication and access
- Capture baseline and provisioning evidence

### Mover

- Simulate an employee department or role change
- Update identity attributes
- Remove access no longer required
- Assign access appropriate to the new role
- Validate that unnecessary access does not remain
- Capture before-and-after access evidence

### Leaver

- Simulate employee termination
- Disable the workforce identity
- Revoke application access
- Validate that authentication is no longer possible
- Capture evidence showing when access was removed

The scenario emphasizes least privilege, identity lifecycle management, access governance, and audit evidence.



## Skills Demonstrated

- Identity and Access Management (IAM)
- Microsoft Active Directory
- Okta Identity Management
- Directory Integration
- Identity Lifecycle Management
- User and Group Administration
- Authentication and Authorization
- Multi-Factor Authentication (MFA)
- Just-in-Time (JIT) Provisioning
- SAML 2.0 Single Sign-On
- Profile and Attribute Mapping
- Application Access Provisioning
- IAM Troubleshooting
- Root-Cause Analysis
- Technical Documentation
- Evidence-Based Validation



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
