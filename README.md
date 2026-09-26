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
