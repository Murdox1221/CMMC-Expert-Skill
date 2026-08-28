# SP 800-53 Rev 5 — Parent Controls for CUI Security Requirements

**What this is.** Verbatim control text (the *Control* statement and the *Discussion*) for every NIST SP 800-53 control and control enhancement that NIST SP 800-171 Rev 2 identifies as a source for one or more of the 110 CUI security requirements. This is the material to quote and reason from when the question is *what a requirement means* or *what it is trying to accomplish* — see `references/control-lineage.md` for the method and `references/sources/sp-800-171r2-to-800-53-mapping.md` for which control(s) sit behind each requirement.

**Source.** Extracted directly from NIST's official OSCAL catalog for **SP 800-53 Rev 5.2.0** (`usnistgov/oscal-content`, catalog last modified 2026-05-11), which is the machine-readable form of the published SP 800-53 Rev 5 and its Rev 5.1.1 patch release. Not paraphrased.

**Reading notes:**

- **`[assignment: organization-defined ...]` / `[selection: ...]`** — Rev 5 exposes organization-defined parameters (ODPs) explicitly. Where the OSCAL source carried an ODP placeholder, it is rendered here as `[assignment: organization-defined <parameter label>]`. SP 800-171 Rev 2 hard-coded or left vague many of these (e.g. "periodically"); Rev 3 surfaces them as ODPs. See `control-lineage.md`.
- **Revision mismatch.** SP 800-171 Rev 2 was tailored from **SP 800-53 Rev 4**; the text below is **Rev 5**. For the base controls used as CUI parents the control identifier, title, and intent are stable across Rev 4→Rev 5, but wording was made outcome-based and some enhancements were renumbered, withdrawn, or merged. Seven enhancements that SP 800-171 Rev 2 Appendix D cites are marked **WITHDRAWN in SP 800-53 Rev 5** below, with the control they were incorporated into. When precision matters, check the Rev 4 text on `csrc.nist.gov` and note which revision you used.
- **Assess against SP 800-171, not against these.** Use the parent control to interpret intent only. Never import an obligation SP 800-53 carries that SP 800-171 did not adopt; the graded artifact is the SP 800-171A / CMMC Assessment Guide objective.
- Control enhancements not adopted by SP 800-171 Rev 2 are omitted. This file is a subset of the catalog, not the whole of SP 800-53.

---

### AC-2 — Account Management

**Control**

  a. Define and document the types of accounts allowed and specifically prohibited for use within the system;  
  b. Assign account managers;  
  c. Require [assignment: organization-defined prerequisites and criteria] for group and role membership;  
  d. Specify:  
    1. Authorized users of the system;  
    2. Group and role membership; and  
    3. Access authorizations (i.e., privileges) and [assignment: organization-defined attributes (as required)] for each account;  
  e. Require approvals by [assignment: organization-defined personnel or roles] for requests to create accounts;  
  f. Create, enable, modify, disable, and remove accounts in accordance with [assignment: organization-defined policy, procedures, prerequisites, and criteria];  
  g. Monitor the use of accounts;  
  h. Notify account managers and [assignment: organization-defined personnel or roles] within:  
    1. [assignment: organization-defined time period] when accounts are no longer required;  
    2. [assignment: organization-defined time period] when users are terminated or transferred; and  
    3. [assignment: organization-defined time period] when system usage or need-to-know changes for an individual;  
  i. Authorize access to the system based on:  
    1. A valid access authorization;  
    2. Intended system usage; and  
    3. [assignment: organization-defined attributes (as required)];  
  j. Review accounts for compliance with account management requirements [assignment: organization-defined frequency];  
  k. Establish and implement a process for changing shared or group account authenticators (if deployed) when individuals are removed from the group; and  
  l. Align account management processes with personnel termination and transfer processes.

**Discussion**

Examples of system account types include individual, shared, group, system, guest, anonymous, emergency, developer, temporary, and service. Identification of authorized system users and the specification of access privileges reflect the requirements in other controls in the security plan. Users requiring administrative privileges on system accounts receive additional scrutiny by organizational personnel responsible for approving such accounts and privileged access, including system owner, mission or business owner, senior agency information security officer, or senior agency official for privacy. Types of accounts that organizations may wish to prohibit due to increased risk include shared, group, emergency, anonymous, temporary, and guest accounts.

Where access involves personally identifiable information, security programs collaborate with the senior agency official for privacy to establish the specific conditions for group and role membership; specify authorized users, group and role membership, and access authorizations for each account; and create, adjust, or remove system accounts in accordance with organizational policies. Policies can include such information as account expiration dates or other factors that trigger the disabling of accounts. Organizations may choose to define access privileges or other attributes by account, type of account, or a combination of the two. Examples of other attributes required for authorizing access include restrictions on time of day, day of week, and point of origin. In defining other system account attributes, organizations consider system-related requirements and mission/business requirements. Failure to consider these factors could affect system availability.

Temporary and emergency accounts are intended for short-term use. Organizations establish temporary accounts as part of normal account activation procedures when there is a need for short-term accounts without the demand for immediacy in account activation. Organizations establish emergency accounts in response to crisis situations and with the need for rapid account activation. Therefore, emergency account activation may bypass normal account authorization processes. Emergency and temporary accounts are not to be confused with infrequently used accounts, including local logon accounts used for special tasks or when network resources are unavailable (may also be known as accounts of last resort). Such accounts remain available and are not subject to automatic disabling or removal dates. Conditions for disabling or deactivating accounts include when shared/group, emergency, or temporary accounts are no longer required and when individuals are transferred or terminated. Changing shared/group authenticators when members leave the group is intended to ensure that former group members do not retain access to the shared or group account. Some types of system accounts may require specialized training.

---

### AC-3 — Access Enforcement

**Control**

Enforce approved authorizations for logical access to information and system resources in accordance with applicable access control policies.

**Discussion**

Access control policies control access between active entities or subjects (i.e., users or processes acting on behalf of users) and passive entities or objects (i.e., devices, files, records, domains) in organizational systems. In addition to enforcing authorized access at the system level and recognizing that systems can host many applications and services in support of mission and business functions, access enforcement mechanisms can also be employed at the application and service level to provide increased information security and privacy. In contrast to logical access controls that are implemented within the system, physical access controls are addressed by the controls in the Physical and Environmental Protection ( [PE] ) family.

---

### AC-4 — Information Flow Enforcement

**Control**

Enforce approved authorizations for controlling the flow of information within the system and between connected systems based on [assignment: organization-defined information flow control policies].

**Discussion**

Information flow control regulates where information can travel within a system and between systems (in contrast to who is allowed to access the information) and without regard to subsequent accesses to that information. Flow control restrictions include blocking external traffic that claims to be from within the organization, keeping export-controlled information from being transmitted in the clear to the Internet, restricting web requests that are not from the internal web proxy server, and limiting information transfers between organizations based on data structures and content. Transferring information between organizations may require an agreement specifying how the information flow is enforced (see [CA-3] ). Transferring information between systems in different security or privacy domains with different security or privacy policies introduces the risk that such transfers violate one or more domain security or privacy policies. In such situations, information owners/stewards provide guidance at designated policy enforcement points between connected systems. Organizations consider mandating specific architectural solutions to enforce specific security and privacy policies. Enforcement includes prohibiting information transfers between connected systems (i.e., allowing access only), verifying write permissions before accepting information from another security or privacy domain or connected system, employing hardware mechanisms to enforce one-way information flows, and implementing trustworthy regrading mechanisms to reassign security or privacy attributes and labels.

Organizations commonly employ information flow control policies and enforcement mechanisms to control the flow of information between designated sources and destinations within systems and between connected systems. Flow control is based on the characteristics of the information and/or the information path. Enforcement occurs, for example, in boundary protection devices that employ rule sets or establish configuration settings that restrict system services, provide a packet-filtering capability based on header information, or provide a message-filtering capability based on message content. Organizations also consider the trustworthiness of filtering and/or inspection mechanisms (i.e., hardware, firmware, and software components) that are critical to information flow enforcement. Control enhancements 3 through 32 primarily address cross-domain solution needs that focus on more advanced filtering techniques, in-depth analysis, and stronger flow enforcement mechanisms implemented in cross-domain products, such as high-assurance guards. Such capabilities are generally not available in commercial off-the-shelf products. Information flow enforcement also applies to control plane traffic (e.g., routing and DNS).

---

### AC-5 — Separation of Duties

**Control**

  a. Identify and document [assignment: organization-defined duties of individuals] ; and  
  b. Define system access authorizations to support separation of duties.

**Discussion**

Separation of duties addresses the potential for abuse of authorized privileges and helps to reduce the risk of malevolent activity without collusion. Separation of duties includes dividing mission or business functions and support functions among different individuals or roles, conducting system support functions with different individuals, and ensuring that security personnel who administer access control functions do not also administer audit functions. Because separation of duty violations can span systems and application domains, organizations consider the entirety of systems and system components when developing policy on separation of duties. Separation of duties is enforced through the account management activities in [AC-2] , access control mechanisms in [AC-3] , and identity management activities in [IA-2], [IA-4] , and [IA-12].

---

### AC-6 — Least Privilege

**Control**

Employ the principle of least privilege, allowing only authorized accesses for users (or processes acting on behalf of users) that are necessary to accomplish assigned organizational tasks.

**Discussion**

Organizations employ least privilege for specific duties and systems. The principle of least privilege is also applied to system processes, ensuring that the processes have access to systems and operate at privilege levels no higher than necessary to accomplish organizational missions or business functions. Organizations consider the creation of additional processes, roles, and accounts as necessary to achieve least privilege. Organizations apply least privilege to the development, implementation, and operation of organizational systems.

---

### AC-7 — Unsuccessful Logon Attempts

**Control**

  a. Enforce a limit of [assignment: organization-defined number] consecutive invalid logon attempts by a user during a [assignment: organization-defined time period] ; and  
  b. Automatically [selection (one-or-more): lock the account or node for [assignment: organization-defined time period] ; lock the account or node until released by an administrator; delay next logon prompt per [assignment: organization-defined delay algorithm] ; notify system administrator; take other [assignment: organization-defined action] ] when the maximum number of unsuccessful attempts is exceeded.

**Discussion**

The need to limit unsuccessful logon attempts and take subsequent action when the maximum number of attempts is exceeded applies regardless of whether the logon occurs via a local or network connection. Due to the potential for denial of service, automatic lockouts initiated by systems are usually temporary and automatically release after a predetermined, organization-defined time period. If a delay algorithm is selected, organizations may employ different algorithms for different components of the system based on the capabilities of those components. Responses to unsuccessful logon attempts may be implemented at the operating system and the application levels. Organization-defined actions that may be taken when the number of allowed consecutive invalid logon attempts is exceeded include prompting the user to answer a secret question in addition to the username and password, invoking a lockdown mode with limited user capabilities (instead of full lockout), allowing users to only logon from specified Internet Protocol (IP) addresses, requiring a CAPTCHA to prevent automated attacks, or applying user profiles such as location, time of day, IP address, device, or Media Access Control (MAC) address. If automatic system lockout or execution of a delay algorithm is not implemented in support of the availability objective, organizations consider a combination of other actions to help prevent brute force attacks. In addition to the above, organizations can prompt users to respond to a secret question before the number of allowed unsuccessful logon attempts is exceeded. Automatically unlocking an account after a specified period of time is generally not permitted. However, exceptions may be required based on operational mission or need.

---

### AC-8 — System Use Notification

**Control**

  a. Display [assignment: organization-defined system use notification] to users before granting access to the system that provides privacy and security notices consistent with applicable laws, executive orders, directives, regulations, policies, standards, and guidelines and state that:  
    1. Users are accessing a U.S. Government system;  
    2. System usage may be monitored, recorded, and subject to audit;  
    3. Unauthorized use of the system is prohibited and subject to criminal and civil penalties; and  
    4. Use of the system indicates consent to monitoring and recording;  
  b. Retain the notification message or banner on the screen until users acknowledge the usage conditions and take explicit actions to log on to or further access the system; and  
  c. For publicly accessible systems:  
    1. Display system use information [assignment: organization-defined conditions] , before granting further access to the publicly accessible system;  
    2. Display references, if any, to monitoring, recording, or auditing that are consistent with privacy accommodations for such systems that generally prohibit those activities; and  
    3. Include a description of the authorized uses of the system.

**Discussion**

System use notifications can be implemented using messages or warning banners displayed before individuals log in to systems. System use notifications are used only for access via logon interfaces with human users. Notifications are not required when human interfaces do not exist. Based on an assessment of risk, organizations consider whether or not a secondary system use notification is needed to access applications or other system resources after the initial network logon. Organizations consider system use notification messages or banners displayed in multiple languages based on organizational needs and the demographics of system users. Organizations consult with the privacy office for input regarding privacy messaging and the Office of the General Counsel or organizational equivalent for legal review and approval of warning banner content.

---

### AC-11 — Device Lock

**Control**

  a. Prevent further access to the system by [selection (one-or-more): initiating a device lock after [assignment: organization-defined time period] of inactivity; requiring the user to initiate a device lock before leaving the system unattended] ; and  
  b. Retain the device lock until the user reestablishes access using established identification and authentication procedures.

**Discussion**

Device locks are temporary actions taken to prevent logical access to organizational systems when users stop work and move away from the immediate vicinity of those systems but do not want to log out because of the temporary nature of their absences. Device locks can be implemented at the operating system level or at the application level. A proximity lock may be used to initiate the device lock (e.g., via a Bluetooth-enabled device or dongle). User-initiated device locking is behavior or policy-based and, as such, requires users to take physical action to initiate the device lock. Device locks are not an acceptable substitute for logging out of systems, such as when organizations require users to log out at the end of workdays.

---

### AC-12 — Session Termination

**Control**

Automatically terminate a user session after [assignment: organization-defined conditions or trigger events].

**Discussion**

Session termination addresses the termination of user-initiated logical sessions (in contrast to [SC-10] , which addresses the termination of network connections associated with communications sessions (i.e., network disconnect)). A logical session (for local, network, and remote access) is initiated whenever a user (or process acting on behalf of a user) accesses an organizational system. Such user sessions can be terminated without terminating network sessions. Session termination ends all processes associated with a user’s logical session except for those processes that are specifically created by the user (i.e., session owner) to continue after the session is terminated. Conditions or trigger events that require automatic termination of the session include organization-defined periods of user inactivity, targeted responses to certain types of incidents, or time-of-day restrictions on system use.

---

### AC-17 — Remote Access

**Control**

  a. Establish and document usage restrictions, configuration/connection requirements, and implementation guidance for each type of remote access allowed; and  
  b. Authorize each type of remote access to the system prior to allowing such connections.

**Discussion**

Remote access is access to organizational systems (or processes acting on behalf of users) that communicate through external networks such as the Internet. Types of remote access include dial-up, broadband, and wireless. Organizations use encrypted virtual private networks (VPNs) to enhance confidentiality and integrity for remote connections. The use of encrypted VPNs provides sufficient assurance to the organization that it can effectively treat such connections as internal networks if the cryptographic mechanisms used are implemented in accordance with applicable laws, executive orders, directives, regulations, policies, standards, and guidelines. Still, VPN connections traverse external networks, and the encrypted VPN does not enhance the availability of remote connections. VPNs with encrypted tunnels can also affect the ability to adequately monitor network communications traffic for malicious code. Remote access controls apply to systems other than public web servers or systems designed for public access. Authorization of each remote access type addresses authorization prior to allowing remote access without specifying the specific formats for such authorization. While organizations may use information exchange and system connection security agreements to manage remote access connections to other systems, such agreements are addressed as part of [CA-3] . Enforcing access restrictions for remote access is addressed via [AC-3].

---

### AC-18 — Wireless Access

**Control**

  a. Establish configuration requirements, connection requirements, and implementation guidance for each type of wireless access; and  
  b. Authorize each type of wireless access to the system prior to allowing such connections.

**Discussion**

Wireless technologies include microwave, packet radio (ultra-high frequency or very high frequency), 802.11x, and Bluetooth. Wireless networks use authentication protocols that provide authenticator protection and mutual authentication.

---

### AC-19 — Access Control for Mobile Devices

**Control**

  a. Establish configuration requirements, connection requirements, and implementation guidance for organization-controlled mobile devices, to include when such devices are outside of controlled areas; and  
  b. Authorize the connection of mobile devices to organizational systems.

**Discussion**

A mobile device is a computing device that has a small form factor such that it can easily be carried by a single individual; is designed to operate without a physical connection; possesses local, non-removable or removable data storage; and includes a self-contained power source. Mobile device functionality may also include voice communication capabilities, on-board sensors that allow the device to capture information, and/or built-in features for synchronizing local data with remote locations. Examples include smart phones and tablets. Mobile devices are typically associated with a single individual. The processing, storage, and transmission capability of the mobile device may be comparable to or merely a subset of notebook/desktop systems, depending on the nature and intended purpose of the device. Protection and control of mobile devices is behavior or policy-based and requires users to take physical action to protect and control such devices when outside of controlled areas. Controlled areas are spaces for which organizations provide physical or procedural controls to meet the requirements established for protecting information and systems.

Due to the large variety of mobile devices with different characteristics and capabilities, organizational restrictions may vary for the different classes or types of such devices. Usage restrictions and specific implementation guidance for mobile devices include configuration management, device identification and authentication, implementation of mandatory protective software, scanning devices for malicious code, updating virus protection software, scanning for critical software updates and patches, conducting primary operating system (and possibly other resident software) integrity checks, and disabling unnecessary hardware.

Usage restrictions and authorization to connect may vary among organizational systems. For example, the organization may authorize the connection of mobile devices to its network and impose a set of usage restrictions, while a system owner may withhold authorization for mobile device connection to specific applications or impose additional usage restrictions before allowing mobile device connections to a system. Adequate security for mobile devices goes beyond the requirements specified in [AC-19] . Many safeguards for mobile devices are reflected in other controls. [AC-20] addresses mobile devices that are not organization-controlled.

---

### AC-20 — Use of External Systems

**Control**

  a. [selection (one-or-more): establish [assignment: organization-defined terms and conditions] ; identify [assignment: organization-defined controls asserted] ] , consistent with the trust relationships established with other organizations owning, operating, and/or maintaining external systems, allowing authorized individuals to:  
    1. Access the system from external systems; and  
    2. Process, store, or transmit organization-controlled information using external systems; or  
  b. Prohibit the use of [assignment: organization-defined prohibited types of external systems].

**Discussion**

External systems are systems that are used by but not part of organizational systems, and for which the organization has no direct control over the implementation of required controls or the assessment of control effectiveness. External systems include personally owned systems, components, or devices; privately owned computing and communications devices in commercial or public facilities; systems owned or controlled by nonfederal organizations; systems managed by contractors; and federal information systems that are not owned by, operated by, or under the direct supervision or authority of the organization. External systems also include systems owned or operated by other components within the same organization and systems within the organization with different authorization boundaries. Organizations have the option to prohibit the use of any type of external system or prohibit the use of specified types of external systems, (e.g., prohibit the use of any external system that is not organizationally owned or prohibit the use of personally-owned systems).

For some external systems (i.e., systems operated by other organizations), the trust relationships that have been established between those organizations and the originating organization may be such that no explicit terms and conditions are required. Systems within these organizations may not be considered external. These situations occur when, for example, there are pre-existing information exchange agreements (either implicit or explicit) established between organizations or components or when such agreements are specified by applicable laws, executive orders, directives, regulations, policies, or standards. Authorized individuals include organizational personnel, contractors, or other individuals with authorized access to organizational systems and over which organizations have the authority to impose specific rules of behavior regarding system access. Restrictions that organizations impose on authorized individuals need not be uniform, as the restrictions may vary depending on trust relationships between organizations. Therefore, organizations may choose to impose different security restrictions on contractors than on state, local, or tribal governments.

External systems used to access public interfaces to organizational systems are outside the scope of [AC-20] . Organizations establish specific terms and conditions for the use of external systems in accordance with organizational security policies and procedures. At a minimum, terms and conditions address the specific types of applications that can be accessed on organizational systems from external systems and the highest security category of information that can be processed, stored, or transmitted on external systems. If the terms and conditions with the owners of the external systems cannot be established, organizations may impose restrictions on organizational personnel using those external systems.

---

### AC-22 — Publicly Accessible Content

**Control**

  a. Designate individuals authorized to make information publicly accessible;  
  b. Train authorized individuals to ensure that publicly accessible information does not contain nonpublic information;  
  c. Review the proposed content of information prior to posting onto the publicly accessible system to ensure that nonpublic information is not included; and  
  d. Review the content on the publicly accessible system for nonpublic information [assignment: organization-defined frequency] and remove such information, if discovered.

**Discussion**

In accordance with applicable laws, executive orders, directives, policies, regulations, standards, and guidelines, the public is not authorized to have access to nonpublic information, including information protected under the [PRIVACT] and proprietary information. Publicly accessible content addresses systems that are controlled by the organization and accessible to the public, typically without identification or authentication. Posting information on non-organizational systems (e.g., non-organizational public websites, forums, and social media) is covered by organizational policy. While organizations may have individuals who are responsible for developing and implementing policies about the information that can be made publicly accessible, publicly accessible content addresses the management of the individuals who make such information publicly accessible.

---

### AT-2 — Literacy Training and Awareness

**Control**

  a. Provide security and privacy literacy training to system users (including managers, senior executives, and contractors):  
    1. As part of initial training for new users and [assignment: organization-defined organization-defined frequency] thereafter; and  
    2. When required by system changes or following [assignment: organization-defined organization-defined events];  
  b. Employ the following techniques to increase the security and privacy awareness of system users [assignment: organization-defined awareness techniques];  
  c. Update literacy training and awareness content [assignment: organization-defined frequency] and following [assignment: organization-defined events] ; and  
  d. Incorporate lessons learned from internal or external security incidents or breaches into literacy training and awareness techniques.

**Discussion**

Organizations provide basic and advanced levels of literacy training to system users, including measures to test the knowledge level of users. Organizations determine the content of literacy training and awareness based on specific organizational requirements, the systems to which personnel have authorized access, and work environments (e.g., telework). The content includes an understanding of the need for security and privacy as well as actions by users to maintain security and personal privacy and to respond to suspected incidents. The content addresses the need for operations security and the handling of personally identifiable information.

Awareness techniques include displaying posters, offering supplies inscribed with security and privacy reminders, displaying logon screen messages, generating email advisories or notices from organizational officials, and conducting awareness events. Literacy training after the initial training described in [AT-2a.1] is conducted at a minimum frequency consistent with applicable laws, directives, regulations, and policies. Subsequent literacy training may be satisfied by one or more short ad hoc sessions and include topical information on recent attack schemes, changes to organizational security and privacy policies, revised security and privacy expectations, or a subset of topics from the initial training. Updating literacy training and awareness content on a regular basis helps to ensure that the content remains relevant. Events that may precipitate an update to literacy training and awareness content include, but are not limited to, assessment or audit findings, security incidents or breaches, or changes in applicable laws, executive orders, directives, regulations, policies, standards, and guidelines.

---

### AT-3 — Role-based Training

**Control**

  a. Provide role-based security and privacy training to personnel with the following roles and responsibilities: [assignment: organization-defined organization-defined roles and responsibilities]:  
    1. Before authorizing access to the system, information, or performing assigned duties, and [assignment: organization-defined frequency] thereafter; and  
    2. When required by system changes;  
  b. Update role-based training content [assignment: organization-defined frequency] and following [assignment: organization-defined events] ; and  
  c. Incorporate lessons learned from internal or external security incidents or breaches into role-based training.

**Discussion**

Organizations determine the content of training based on the assigned roles and responsibilities of individuals as well as the security and privacy requirements of organizations and the systems to which personnel have authorized access, including technical training specifically tailored for assigned duties. Roles that may require role-based training include senior leaders or management officials (e.g., head of agency/chief executive officer, chief information officer, senior accountable official for risk management, senior agency information security officer, senior agency official for privacy), system owners; authorizing officials; system security officers; privacy officers; acquisition and procurement officials; enterprise architects; systems engineers; software developers; systems security engineers; privacy engineers; system, network, and database administrators; auditors; personnel conducting configuration management activities; personnel performing verification and validation activities; personnel with access to system-level software; control assessors; personnel with contingency planning and incident response duties; personnel with privacy management responsibilities; and personnel with access to personally identifiable information.

Comprehensive role-based training addresses management, operational, and technical roles and responsibilities covering physical, personnel, and technical controls. Role-based training also includes policies, procedures, tools, methods, and artifacts for the security and privacy roles defined. Organizations provide the training necessary for individuals to fulfill their responsibilities related to operations and supply chain risk management within the context of organizational security and privacy programs. Role-based training also applies to contractors who provide services to federal agencies. Types of training include web-based and computer-based training, classroom-style training, and hands-on training (including micro-training). Updating role-based training on a regular basis helps to ensure that the content remains relevant and effective. Events that may precipitate an update to role-based training content include, but are not limited to, assessment or audit findings, security incidents or breaches, or changes in applicable laws, executive orders, directives, regulations, policies, standards, and guidelines.

---

### AU-2 — Event Logging

**Control**

  a. Identify the types of events that the system is capable of logging in support of the audit function: [assignment: organization-defined event types];  
  b. Coordinate the event logging function with other organizational entities requiring audit-related information to guide and inform the selection criteria for events to be logged;  
  c. Specify the following event types for logging within the system: [assignment: organization-defined organization-defined event types (subset of the event types defined in [AU-2a.]) along with the frequency of (or situation requiring) logging for each identified event type];  
  d. Provide a rationale for why the event types selected for logging are deemed to be adequate to support after-the-fact investigations of incidents; and  
  e. Review and update the event types selected for logging [assignment: organization-defined frequency].

**Discussion**

An event is an observable occurrence in a system. The types of events that require logging are those events that are significant and relevant to the security of systems and the privacy of individuals. Event logging also supports specific monitoring and auditing needs. Event types include password changes, failed logons or failed accesses related to systems, security or privacy attribute changes, administrative privilege usage, PIV credential usage, data action changes, query parameters, or external credential usage. In determining the set of event types that require logging, organizations consider the monitoring and auditing appropriate for each of the controls to be implemented. For completeness, event logging includes all protocols that are operational and supported by the system.

To balance monitoring and auditing requirements with other system needs, event logging requires identifying the subset of event types that are logged at a given point in time. For example, organizations may determine that systems need the capability to log every file access successful and unsuccessful, but not activate that capability except for specific circumstances due to the potential burden on system performance. The types of events that organizations desire to be logged may change. Reviewing and updating the set of logged events is necessary to help ensure that the events remain relevant and continue to support the needs of the organization. Organizations consider how the types of logging events can reveal information about individuals that may give rise to privacy risk and how best to mitigate such risks. For example, there is the potential to reveal personally identifiable information in the audit trail, especially if the logging event is based on patterns or time of usage.

Event logging requirements, including the need to log specific event types, may be referenced in other controls and control enhancements. These include [AC-2(4)], [AC-3(10)], [AC-6(9)], [AC-17(1)], [CM-3f], [CM-5(1)], [IA-3(3)(b)], [MA-4(1)], [MP-4(2)], [PE-3], [PM-21], [PT-7], [RA-8], [SC-7(9)], [SC-7(15)], [SI-3(8)], [SI-4(22)], [SI-7(8)] , and [SI-10(1)] . Organizations include event types that are required by applicable laws, executive orders, directives, policies, regulations, standards, and guidelines. Audit records can be generated at various levels, including at the packet level as information traverses the network. Selecting the appropriate level of event logging is an important part of a monitoring and auditing capability and can identify the root causes of problems. When defining event types, organizations consider the logging necessary to cover related event types, such as the steps in distributed, transaction-based processes and the actions that occur in service-oriented architectures.

---

### AU-3 — Content of Audit Records

**Control**

Ensure that audit records contain information that establishes the following:  
  a. What type of event occurred;  
  b. When the event occurred;  
  c. Where the event occurred;  
  d. Source of the event;  
  e. Outcome of the event; and  
  f. Identity of any individuals, subjects, or objects/entities associated with the event.

**Discussion**

Audit record content that may be necessary to support the auditing function includes event descriptions (item a), time stamps (item b), source and destination addresses (item c), user or process identifiers (items d and f), success or fail indications (item e), and filenames involved (items a, c, e, and f) . Event outcomes include indicators of event success or failure and event-specific results, such as the system security and privacy posture after the event occurred. Organizations consider how audit records can reveal information about individuals that may give rise to privacy risks and how best to mitigate such risks. For example, there is the potential to reveal personally identifiable information in the audit trail, especially if the trail records inputs or is based on patterns or time of usage.

---

### AU-5 — Response to Audit Logging Process Failures

**Control**

  a. Alert [assignment: organization-defined personnel or roles] within [assignment: organization-defined time period] in the event of an audit logging process failure; and  
  b. Take the following additional actions: [assignment: organization-defined additional actions].

**Discussion**

Audit logging process failures include software and hardware errors, failures in audit log capturing mechanisms, and reaching or exceeding audit log storage capacity. Organization-defined actions include overwriting oldest audit records, shutting down the system, and stopping the generation of audit records. Organizations may choose to define additional actions for audit logging process failures based on the type of failure, the location of the failure, the severity of the failure, or a combination of such factors. When the audit logging process failure is related to storage, the response is carried out for the audit log storage repository (i.e., the distinct system component where the audit logs are stored), the system on which the audit logs reside, the total audit log storage capacity of the organization (i.e., all audit log storage repositories combined), or all three. Organizations may decide to take no additional actions after alerting designated roles or personnel.

---

### AU-6 — Audit Record Review, Analysis, and Reporting

**Control**

  a. Review and analyze system audit records [assignment: organization-defined frequency] for indications of [assignment: organization-defined inappropriate or unusual activity] and the potential impact of the inappropriate or unusual activity;  
  b. Report findings to [assignment: organization-defined personnel or roles] ; and  
  c. Adjust the level of audit record review, analysis, and reporting within the system when there is a change in risk based on law enforcement information, intelligence information, or other credible sources of information.

**Discussion**

Audit record review, analysis, and reporting covers information security- and privacy-related logging performed by organizations, including logging that results from the monitoring of account usage, remote access, wireless connectivity, mobile device connection, configuration settings, system component inventory, use of maintenance tools and non-local maintenance, physical access, temperature and humidity, equipment delivery and removal, communications at system interfaces, and use of mobile code or Voice over Internet Protocol (VoIP). Findings can be reported to organizational entities that include the incident response team, help desk, and security or privacy offices. If organizations are prohibited from reviewing and analyzing audit records or unable to conduct such activities, the review or analysis may be carried out by other organizations granted such authority. The frequency, scope, and/or depth of the audit record review, analysis, and reporting may be adjusted to meet organizational needs based on new information received.

---

### AU-7 — Audit Record Reduction and Report Generation

**Control**

Provide and implement an audit record reduction and report generation capability that:  
  a. Supports on-demand audit record review, analysis, and reporting requirements and after-the-fact investigations of incidents; and  
  b. Does not alter the original content or time ordering of audit records.

**Discussion**

Audit record reduction is a process that manipulates collected audit log information and organizes it into a summary format that is more meaningful to analysts. Audit record reduction and report generation capabilities do not always emanate from the same system or from the same organizational entities that conduct audit logging activities. The audit record reduction capability includes modern data mining techniques with advanced data filters to identify anomalous behavior in audit records. The report generation capability provided by the system can generate customizable reports. Time ordering of audit records can be an issue if the granularity of the timestamp in the record is insufficient.

---

### AU-8 — Time Stamps

**Control**

  a. Use internal system clocks to generate time stamps for audit records; and  
  b. Record time stamps for audit records that meet [assignment: organization-defined granularity of time measurement] and that use Coordinated Universal Time, have a fixed local time offset from Coordinated Universal Time, or that include the local time offset as part of the time stamp.

**Discussion**

Time stamps generated by the system include date and time. Time is commonly expressed in Coordinated Universal Time (UTC), a modern continuation of Greenwich Mean Time (GMT), or local time with an offset from UTC. Granularity of time measurements refers to the degree of synchronization between system clocks and reference clocks (e.g., clocks synchronizing within hundreds of milliseconds or tens of milliseconds). Organizations may define different time granularities for different system components. Time service can be critical to other security capabilities such as access control and identification and authentication, depending on the nature of the mechanisms used to support those capabilities.

---

### AU-9 — Protection of Audit Information

**Control**

  a. Protect audit information and audit logging tools from unauthorized access, modification, and deletion; and  
  b. Alert [assignment: organization-defined personnel or roles] upon detection of unauthorized access, modification, or deletion of audit information.

**Discussion**

Audit information includes all information needed to successfully audit system activity, such as audit records, audit log settings, audit reports, and personally identifiable information. Audit logging tools are those programs and devices used to conduct system audit and logging activities. Protection of audit information focuses on technical protection and limits the ability to access and execute audit logging tools to authorized individuals. Physical protection of audit information is addressed by both media protection controls and physical and environmental protection controls.

---

### AU-11 — Audit Record Retention

**Control**

Retain audit records for [assignment: organization-defined time period] to provide support for after-the-fact investigations of incidents and to meet regulatory and organizational information retention requirements.

**Discussion**

Organizations retain audit records until it is determined that the records are no longer needed for administrative, legal, audit, or other operational purposes. This includes the retention and availability of audit records relative to Freedom of Information Act (FOIA) requests, subpoenas, and law enforcement actions. Organizations develop standard categories of audit records relative to such types of actions and standard response processes for each type of action. The National Archives and Records Administration (NARA) General Records Schedules provide federal policy on records retention.

---

### AU-12 — Audit Record Generation

**Control**

  a. Provide audit record generation capability for the event types the system is capable of auditing as defined in [AU-2a] on [assignment: organization-defined system components];  
  b. Allow [assignment: organization-defined personnel or roles] to select the event types that are to be logged by specific components of the system; and  
  c. Generate audit records for the event types defined in [AU-2c] that include the audit record content defined in [AU-3].

**Discussion**

Audit records can be generated from many different system components. The event types specified in [AU-2d] are the event types for which audit logs are to be generated and are a subset of all event types for which the system can generate audit records.

---

### CA-2 — Control Assessments

**Control**

  a. Select the appropriate assessor or assessment team for the type of assessment to be conducted;  
  b. Develop a control assessment plan that describes the scope of the assessment including:  
    1. Controls and control enhancements under assessment;  
    2. Assessment procedures to be used to determine control effectiveness; and  
    3. Assessment environment, assessment team, and assessment roles and responsibilities;  
  c. Ensure the control assessment plan is reviewed and approved by the authorizing official or designated representative prior to conducting the assessment;  
  d. Assess the controls in the system and its environment of operation [assignment: organization-defined assessment frequency] to determine the extent to which the controls are implemented correctly, operating as intended, and producing the desired outcome with respect to meeting established security and privacy requirements;  
  e. Produce a control assessment report that document the results of the assessment; and  
  f. Provide the results of the control assessment to [assignment: organization-defined individuals or roles].

**Discussion**

Organizations ensure that control assessors possess the required skills and technical expertise to develop effective assessment plans and to conduct assessments of system-specific, hybrid, common, and program management controls, as appropriate. The required skills include general knowledge of risk management concepts and approaches as well as comprehensive knowledge of and experience with the hardware, software, and firmware system components implemented.

Organizations assess controls in systems and the environments in which those systems operate as part of initial and ongoing authorizations, continuous monitoring, FISMA annual assessments, system design and development, systems security engineering, privacy engineering, and the system development life cycle. Assessments help to ensure that organizations meet information security and privacy requirements, identify weaknesses and deficiencies in the system design and development process, provide essential information needed to make risk-based decisions as part of authorization processes, and comply with vulnerability mitigation procedures. Organizations conduct assessments on the implemented controls as documented in security and privacy plans. Assessments can also be conducted throughout the system development life cycle as part of systems engineering and systems security engineering processes. The design for controls can be assessed as RFPs are developed, responses assessed, and design reviews conducted. If a design to implement controls and subsequent implementation in accordance with the design are assessed during development, the final control testing can be a simple confirmation utilizing previously completed control assessment and aggregating the outcomes.

Organizations may develop a single, consolidated security and privacy assessment plan for the system or maintain separate plans. A consolidated assessment plan clearly delineates the roles and responsibilities for control assessment. If multiple organizations participate in assessing a system, a coordinated approach can reduce redundancies and associated costs.

Organizations can use other types of assessment activities, such as vulnerability scanning and system monitoring, to maintain the security and privacy posture of systems during the system life cycle. Assessment reports document assessment results in sufficient detail, as deemed necessary by organizations, to determine the accuracy and completeness of the reports and whether the controls are implemented correctly, operating as intended, and producing the desired outcome with respect to meeting requirements. Assessment results are provided to the individuals or roles appropriate for the types of assessments being conducted. For example, assessments conducted in support of authorization decisions are provided to authorizing officials, senior agency officials for privacy, senior agency information security officers, and authorizing official designated representatives.

To satisfy annual assessment requirements, organizations can use assessment results from the following sources: initial or ongoing system authorizations, continuous monitoring, systems engineering processes, or system development life cycle activities. Organizations ensure that assessment results are current, relevant to the determination of control effectiveness, and obtained with the appropriate level of assessor independence. Existing control assessment results can be reused to the extent that the results are still valid and can also be supplemented with additional assessments as needed. After the initial authorizations, organizations assess controls during continuous monitoring. Organizations also establish the frequency for ongoing assessments in accordance with organizational continuous monitoring strategies. External audits, including audits by external entities such as regulatory agencies, are outside of the scope of [CA-2].

---

### CA-5 — Plan of Action and Milestones

**Control**

  a. Develop a plan of action and milestones for the system to document the planned remediation actions of the organization to correct weaknesses or deficiencies noted during the assessment of the controls and to reduce or eliminate known vulnerabilities in the system; and  
  b. Update existing plan of action and milestones [assignment: organization-defined frequency] based on the findings from control assessments, independent audits or reviews, and continuous monitoring activities.

**Discussion**

Plans of action and milestones are useful for any type of organization to track planned remedial actions. Plans of action and milestones are required in authorization packages and subject to federal reporting requirements established by OMB.

---

### CA-7 — Continuous Monitoring

**Control**

Develop a system-level continuous monitoring strategy and implement continuous monitoring in accordance with the organization-level continuous monitoring strategy that includes:  
  a. Establishing the following system-level metrics to be monitored: [assignment: organization-defined system-level metrics];  
  b. Establishing [assignment: organization-defined frequencies] for monitoring and [assignment: organization-defined frequencies] for assessment of control effectiveness;  
  c. Ongoing control assessments in accordance with the continuous monitoring strategy;  
  d. Ongoing monitoring of system and organization-defined metrics in accordance with the continuous monitoring strategy;  
  e. Correlation and analysis of information generated by control assessments and monitoring;  
  f. Response actions to address results of the analysis of control assessment and monitoring information; and  
  g. Reporting the security and privacy status of the system to [assignment: organization-defined organization-defined personnel or roles] [assignment: organization-defined organization-defined frequency].

**Discussion**

Continuous monitoring at the system level facilitates ongoing awareness of the system security and privacy posture to support organizational risk management decisions. The terms "continuous" and "ongoing" imply that organizations assess and monitor their controls and risks at a frequency sufficient to support risk-based decisions. Different types of controls may require different monitoring frequencies. The results of continuous monitoring generate risk response actions by organizations. When monitoring the effectiveness of multiple controls that have been grouped into capabilities, a root-cause analysis may be needed to determine the specific control that has failed. Continuous monitoring programs allow organizations to maintain the authorizations of systems and common controls in highly dynamic environments of operation with changing mission and business needs, threats, vulnerabilities, and technologies. Having access to security and privacy information on a continuing basis through reports and dashboards gives organizational officials the ability to make effective and timely risk management decisions, including ongoing authorization decisions.

Automation supports more frequent updates to hardware, software, and firmware inventories, authorization packages, and other system information. Effectiveness is further enhanced when continuous monitoring outputs are formatted to provide information that is specific, measurable, actionable, relevant, and timely. Continuous monitoring activities are scaled in accordance with the security categories of systems. Monitoring requirements, including the need for specific monitoring, may be referenced in other controls and control enhancements, such as [AC-2g], [AC-2(7)], [AC-2(12)(a)], [AC-2(7)(b)], [AC-2(7)(c)], [AC-17(1)], [AT-4a], [AU-13], [AU-13(1)], [AU-13(2)], [CM-3f], [CM-6d], [CM-11c], [IR-5], [MA-2b], [MA-3a], [MA-4a], [PE-3d], [PE-6], [PE-14b], [PE-16], [PE-20], [PM-6], [PM-23], [PM-31], [PS-7e], [SA-9c], [SR-4], [SC-5(3)(b)], [SC-7a], [SC-7(24)(b)], [SC-18b], [SC-43b] , and [SI-4].

---

### CM-2 — Baseline Configuration

**Control**

  a. Develop, document, and maintain under configuration control, a current baseline configuration of the system; and  
  b. Review and update the baseline configuration of the system:  
    1. [assignment: organization-defined frequency];  
    2. When required due to [assignment: organization-defined circumstances] ; and  
    3. When system components are installed or upgraded.

**Discussion**

Baseline configurations for systems and system components include connectivity, operational, and communications aspects of systems. Baseline configurations are documented, formally reviewed, and agreed-upon specifications for systems or configuration items within those systems. Baseline configurations serve as a basis for future builds, releases, or changes to systems and include security and privacy control implementations, operational procedures, information about system components, network topology, and logical placement of components in the system architecture. Maintaining baseline configurations requires creating new baselines as organizational systems change over time. Baseline configurations of systems reflect the current enterprise architecture.

---

### CM-3 — Configuration Change Control

**Control**

  a. Determine and document the types of changes to the system that are configuration-controlled;  
  b. Review proposed configuration-controlled changes to the system and approve or disapprove such changes with explicit consideration for security and privacy impact analyses;  
  c. Document configuration change decisions associated with the system;  
  d. Implement approved configuration-controlled changes to the system;  
  e. Retain records of configuration-controlled changes to the system for [assignment: organization-defined time period];  
  f. Monitor and review activities associated with configuration-controlled changes to the system; and  
  g. Coordinate and provide oversight for configuration change control activities through [assignment: organization-defined configuration change control element] that convenes [selection (one-or-more): [assignment: organization-defined frequency] ; when [assignment: organization-defined configuration change conditions] ].

**Discussion**

Configuration change control for organizational systems involves the systematic proposal, justification, implementation, testing, review, and disposition of system changes, including system upgrades and modifications. Configuration change control includes changes to baseline configurations, configuration items of systems, operational procedures, configuration settings for system components, remediate vulnerabilities, and unscheduled or unauthorized changes. Processes for managing configuration changes to systems include Configuration Control Boards or Change Advisory Boards that review and approve proposed changes. For changes that impact privacy risk, the senior agency official for privacy updates privacy impact assessments and system of records notices. For new systems or major upgrades, organizations consider including representatives from the development organizations on the Configuration Control Boards or Change Advisory Boards. Auditing of changes includes activities before and after changes are made to systems and the auditing activities required to implement such changes. See also [SA-10].

---

### CM-4 — Impact Analyses

**Control**

Analyze changes to the system to determine potential security and privacy impacts prior to change implementation.

**Discussion**

Organizational personnel with security or privacy responsibilities conduct impact analyses. Individuals conducting impact analyses possess the necessary skills and technical expertise to analyze the changes to systems as well as the security or privacy ramifications. Impact analyses include reviewing security and privacy plans, policies, and procedures to understand control requirements; reviewing system design documentation and operational procedures to understand control implementation and how specific system changes might affect the controls; reviewing the impact of changes on organizational supply chain partners with stakeholders; and determining how potential changes to a system create new risks to the privacy of individuals and the ability of implemented controls to mitigate those risks. Impact analyses also include risk assessments to understand the impact of the changes and determine if additional controls are required.

---

### CM-5 — Access Restrictions for Change

**Control**

Define, document, approve, and enforce physical and logical access restrictions associated with changes to the system.

**Discussion**

Changes to the hardware, software, or firmware components of systems or the operational procedures related to the system can potentially have significant effects on the security of the systems or individuals’ privacy. Therefore, organizations permit only qualified and authorized individuals to access systems for purposes of initiating changes. Access restrictions include physical and logical access controls (see [AC-3] and [PE-3] ), software libraries, workflow automation, media libraries, abstract layers (i.e., changes implemented into external interfaces rather than directly into systems), and change windows (i.e., changes occur only during specified times).

---

### CM-6 — Configuration Settings

**Control**

  a. Establish and document configuration settings for components employed within the system that reflect the most restrictive mode consistent with operational requirements using [assignment: organization-defined common secure configurations];  
  b. Implement the configuration settings;  
  c. Identify, document, and approve any deviations from established configuration settings for [assignment: organization-defined system components] based on [assignment: organization-defined operational requirements] ; and  
  d. Monitor and control changes to the configuration settings in accordance with organizational policies and procedures.

**Discussion**

Configuration settings are the parameters that can be changed in the hardware, software, or firmware components of the system that affect the security and privacy posture or functionality of the system. Information technology products for which configuration settings can be defined include mainframe computers, servers, workstations, operating systems, mobile devices, input/output devices, protocols, and applications. Parameters that impact the security posture of systems include registry settings; account, file, or directory permission settings; and settings for functions, protocols, ports, services, and remote connections. Privacy parameters are parameters impacting the privacy posture of systems, including the parameters required to satisfy other privacy controls. Privacy parameters include settings for access controls, data processing preferences, and processing and retention permissions. Organizations establish organization-wide configuration settings and subsequently derive specific configuration settings for systems. The established settings become part of the configuration baseline for the system.

Common secure configurations (also known as security configuration checklists, lockdown and hardening guides, and security reference guides) provide recognized, standardized, and established benchmarks that stipulate secure configuration settings for information technology products and platforms as well as instructions for configuring those products or platforms to meet operational requirements. Common secure configurations can be developed by a variety of organizations, including information technology product developers, manufacturers, vendors, federal agencies, consortia, academia, industry, and other organizations in the public and private sectors.

Implementation of a common secure configuration may be mandated at the organization level, mission and business process level, system level, or at a higher level, including by a regulatory agency. Common secure configurations include the United States Government Configuration Baseline [USGCB] and security technical implementation guides (STIGs), which affect the implementation of [CM-6] and other controls such as [AC-19] and [CM-7] . The Security Content Automation Protocol (SCAP) and the defined standards within the protocol provide an effective method to uniquely identify, track, and control configuration settings.

---

### CM-7 — Least Functionality

**Control**

  a. Configure the system to provide only [assignment: organization-defined mission-essential capabilities] ; and  
  b. Prohibit or restrict the use of the following functions, ports, protocols, software, and/or services: [assignment: organization-defined organization-defined prohibited or restricted functions, system ports, protocols, software, and/or services].

**Discussion**

Systems provide a wide variety of functions and services. Some of the functions and services routinely provided by default may not be necessary to support essential organizational missions, functions, or operations. Additionally, it is sometimes convenient to provide multiple services from a single system component, but doing so increases risk over limiting the services provided by that single component. Where feasible, organizations limit component functionality to a single function per component. Organizations consider removing unused or unnecessary software and disabling unused or unnecessary physical and logical ports and protocols to prevent unauthorized connection of components, transfer of information, and tunneling. Organizations employ network scanning tools, intrusion detection and prevention systems, and end-point protection technologies, such as firewalls and host-based intrusion detection systems, to identify and prevent the use of prohibited functions, protocols, ports, and services. Least functionality can also be achieved as part of the fundamental design and development of the system (see [SA-8], [SC-2] , and [SC-3]).

---

### CM-8 — System Component Inventory

**Control**

  a. Develop and document an inventory of system components that:  
    1. Accurately reflects the system;  
    2. Includes all components within the system;  
    3. Does not include duplicate accounting of components or components assigned to any other system;  
    4. Is at the level of granularity deemed necessary for tracking and reporting; and  
    5. Includes the following information to achieve system component accountability: [assignment: organization-defined information] ; and  
  b. Review and update the system component inventory [assignment: organization-defined frequency].

**Discussion**

System components are discrete, identifiable information technology assets that include hardware, software, and firmware. Organizations may choose to implement centralized system component inventories that include components from all organizational systems. In such situations, organizations ensure that the inventories include system-specific information required for component accountability. The information necessary for effective accountability of system components includes the system name, software owners, software version numbers, hardware inventory specifications, software license information, and for networked components, the machine names and network addresses across all implemented protocols (e.g., IPv4, IPv6). Inventory specifications include date of receipt, cost, model, serial number, manufacturer, supplier information, component type, and physical location.

Preventing duplicate accounting of system components addresses the lack of accountability that occurs when component ownership and system association is not known, especially in large or complex connected systems. Effective prevention of duplicate accounting of system components necessitates use of a unique identifier for each component. For software inventory, centrally managed software that is accessed via other systems is addressed as a component of the system on which it is installed and managed. Software installed on multiple organizational systems and managed at the system level is addressed for each individual system and may appear more than once in a centralized component inventory, necessitating a system association for each software instance in the centralized inventory to avoid duplicate accounting of components. Scanning systems implementing multiple network protocols (e.g., IPv4 and IPv6) can result in duplicate components being identified in different address spaces. The implementation of [CM-8(7)] can help to eliminate duplicate accounting of components.

---

### CM-11 — User-installed Software

**Control**

  a. Establish [assignment: organization-defined policies] governing the installation of software by users;  
  b. Enforce software installation policies through the following methods: [assignment: organization-defined methods] ; and  
  c. Monitor policy compliance [assignment: organization-defined frequency].

**Discussion**

If provided the necessary privileges, users can install software in organizational systems. To maintain control over the software installed, organizations identify permitted and prohibited actions regarding software installation. Permitted software installations include updates and security patches to existing software and downloading new applications from organization-approved "app stores." Prohibited software installations include software with unknown or suspect pedigrees or software that organizations consider potentially malicious. Policies selected for governing user-installed software are organization-developed or provided by some external entity. Policy enforcement methods can include procedural methods and automated methods.

---

### CP-9 — System Backup

**Control**

  a. Conduct backups of user-level information contained in [assignment: organization-defined system components] [assignment: organization-defined frequency];  
  b. Conduct backups of system-level information contained in the system [assignment: organization-defined frequency];  
  c. Conduct backups of system documentation, including security- and privacy-related documentation [assignment: organization-defined frequency] ; and  
  d. Protect the confidentiality, integrity, and availability of backup information.

**Discussion**

System-level information includes system state information, operating system software, middleware, application software, and licenses. User-level information includes information other than system-level information. Mechanisms employed to protect the integrity of system backups include digital signatures and cryptographic hashes. Protection of system backup information while in transit is addressed by [MP-5] and [SC-8] . System backups reflect the requirements in contingency plans as well as other organizational requirements for backing up information. Organizations may be subject to laws, executive orders, directives, regulations, or policies with requirements regarding specific categories of information (e.g., personal health information). Organizational personnel consult with the senior agency official for privacy and legal counsel regarding such requirements.

---

### IA-2 — Identification and Authentication (Organizational Users)

**Control**

Uniquely identify and authenticate organizational users and associate that unique identification with processes acting on behalf of those users.

**Discussion**

Organizations can satisfy the identification and authentication requirements by complying with the requirements in [HSPD 12] . Organizational users include employees or individuals who organizations consider to have an equivalent status to employees (e.g., contractors and guest researchers). Unique identification and authentication of users applies to all accesses other than those that are explicitly identified in [AC-14] and that occur through the authorized use of group authenticators without individual authentication. Since processes execute on behalf of groups and roles, organizations may require unique identification of individuals in group accounts or for detailed accountability of individual activity.

Organizations employ passwords, physical authenticators, or biometrics to authenticate user identities or, in the case of multi-factor authentication, some combination thereof. Access to organizational systems is defined as either local access or network access. Local access is any access to organizational systems by users or processes acting on behalf of users, where access is obtained through direct connections without the use of networks. Network access is access to organizational systems by users (or processes acting on behalf of users) where access is obtained through network connections (i.e., nonlocal accesses). Remote access is a type of network access that involves communication through external networks. Internal networks include local area networks and wide area networks.

The use of encrypted virtual private networks for network connections between organization-controlled endpoints and non-organization-controlled endpoints may be treated as internal networks with respect to protecting the confidentiality and integrity of information traversing the network. Identification and authentication requirements for non-organizational users are described in [IA-8].

---

### IA-3 — Device Identification and Authentication

**Control**

Uniquely identify and authenticate [assignment: organization-defined devices and/or types of devices] before establishing a [selection (one-or-more): local; remote; network] connection.

**Discussion**

Devices that require unique device-to-device identification and authentication are defined by type, device, or a combination of type and device. Organization-defined device types include devices that are not owned by the organization. Systems use shared known information (e.g., Media Access Control [MAC], Transmission Control Protocol/Internet Protocol [TCP/IP] addresses) for device identification or organizational authentication solutions (e.g., Institute of Electrical and Electronics Engineers (IEEE) 802.1x and Extensible Authentication Protocol [EAP], RADIUS server with EAP-Transport Layer Security [TLS] authentication, Kerberos) to identify and authenticate devices on local and wide area networks. Organizations determine the required strength of authentication mechanisms based on the security categories of systems and mission or business requirements. Because of the challenges of implementing device authentication on a large scale, organizations can restrict the application of the control to a limited number/type of devices based on mission or business needs.

---

### IA-4 — Identifier Management

**Control**

Manage system identifiers by:  
  a. Receiving authorization from [assignment: organization-defined personnel or roles] to assign an individual, group, role, service, or device identifier;  
  b. Selecting an identifier that identifies an individual, group, role, service, or device;  
  c. Assigning the identifier to the intended individual, group, role, service, or device; and  
  d. Preventing reuse of identifiers for [assignment: organization-defined time period].

**Discussion**

Common device identifiers include Media Access Control (MAC) addresses, Internet Protocol (IP) addresses, or device-unique token identifiers. The management of individual identifiers is not applicable to shared system accounts. Typically, individual identifiers are the usernames of the system accounts assigned to those individuals. In such instances, the account management activities of [AC-2] use account names provided by [IA-4] . Identifier management also addresses individual identifiers not necessarily associated with system accounts. Preventing the reuse of identifiers implies preventing the assignment of previously used individual, group, role, service, or device identifiers to different individuals, groups, roles, services, or devices.

---

### IA-5 — Authenticator Management

**Control**

Manage system authenticators by:  
  a. Verifying, as part of the initial authenticator distribution, the identity of the individual, group, role, service, or device receiving the authenticator;  
  b. Establishing initial authenticator content for any authenticators issued by the organization;  
  c. Ensuring that authenticators have sufficient strength of mechanism for their intended use;  
  d. Establishing and implementing administrative procedures for initial authenticator distribution, for lost or compromised or damaged authenticators, and for revoking authenticators;  
  e. Changing default authenticators prior to first use;  
  f. Changing or refreshing authenticators [assignment: organization-defined time period by authenticator type] or when [assignment: organization-defined events] occur;  
  g. Protecting authenticator content from unauthorized disclosure and modification;  
  h. Requiring individuals to take, and having devices implement, specific controls to protect authenticators; and  
  i. Changing authenticators for group or role accounts when membership to those accounts changes.

**Discussion**

Authenticators include passwords, cryptographic devices, biometrics, certificates, one-time password devices, and ID badges. Device authenticators include certificates and passwords. Initial authenticator content is the actual content of the authenticator (e.g., the initial password). In contrast, the requirements for authenticator content contain specific criteria or characteristics (e.g., minimum password length). Developers may deliver system components with factory default authentication credentials (i.e., passwords) to allow for initial installation and configuration. Default authentication credentials are often well known, easily discoverable, and present a significant risk. The requirement to protect individual authenticators may be implemented via control [PL-4] or [PS-6] for authenticators in the possession of individuals and by controls [AC-3], [AC-6] , and [SC-28] for authenticators stored in organizational systems, including passwords stored in hashed or encrypted formats or files containing encrypted or hashed passwords accessible with administrator privileges.

Systems support authenticator management by organization-defined settings and restrictions for various authenticator characteristics (e.g., minimum password length, validation time window for time synchronous one-time tokens, and number of allowed rejections during the verification stage of biometric authentication). Actions can be taken to safeguard individual authenticators, including maintaining possession of authenticators, not sharing authenticators with others, and immediately reporting lost, stolen, or compromised authenticators. Authenticator management includes issuing and revoking authenticators for temporary access when no longer needed.

---

### IA-6 — Authentication Feedback

**Control**

Obscure feedback of authentication information during the authentication process to protect the information from possible exploitation and use by unauthorized individuals.

**Discussion**

Authentication feedback from systems does not provide information that would allow unauthorized individuals to compromise authentication mechanisms. For some types of systems, such as desktops or notebooks with relatively large monitors, the threat (referred to as shoulder surfing) may be significant. For other types of systems, such as mobile devices with small displays, the threat may be less significant and is balanced against the increased likelihood of typographic input errors due to small keyboards. Thus, the means for obscuring authentication feedback is selected accordingly. Obscuring authentication feedback includes displaying asterisks when users type passwords into input devices or displaying feedback for a very limited time before obscuring it.

---

### IR-2 — Incident Response Training

**Control**

  a. Provide incident response training to system users consistent with assigned roles and responsibilities:  
    1. Within [assignment: organization-defined time period] of assuming an incident response role or responsibility or acquiring system access;  
    2. When required by system changes; and  
    3. [assignment: organization-defined frequency] thereafter; and  
  b. Review and update incident response training content [assignment: organization-defined frequency] and following [assignment: organization-defined events].

**Discussion**

Incident response training is associated with the assigned roles and responsibilities of organizational personnel to ensure that the appropriate content and level of detail are included in such training. For example, users may only need to know who to call or how to recognize an incident; system administrators may require additional training on how to handle incidents; and incident responders may receive more specific training on forensics, data collection techniques, reporting, system recovery, and system restoration. Incident response training includes user training in identifying and reporting suspicious activities from external and internal sources. Incident response training for users may be provided as part of [AT-2] or [AT-3] . Events that may precipitate an update to incident response training content include, but are not limited to, incident response plan testing or response to an actual incident (lessons learned), assessment or audit findings, or changes in applicable laws, executive orders, directives, regulations, policies, standards, and guidelines.

---

### IR-3 — Incident Response Testing

**Control**

Test the effectiveness of the incident response capability for the system [assignment: organization-defined frequency] using the following tests: [assignment: organization-defined tests].

**Discussion**

Organizations test incident response capabilities to determine their effectiveness and identify potential weaknesses or deficiencies. Incident response testing includes the use of checklists, walk-through or tabletop exercises, and simulations (parallel or full interrupt). Incident response testing can include a determination of the effects on organizational operations and assets and individuals due to incident response. The use of qualitative and quantitative data aids in determining the effectiveness of incident response processes.

---

### IR-4 — Incident Handling

**Control**

  a. Implement an incident handling capability for incidents that is consistent with the incident response plan and includes preparation, detection and analysis, containment, eradication, and recovery;  
  b. Coordinate incident handling activities with contingency planning activities;  
  c. Incorporate lessons learned from ongoing incident handling activities into incident response procedures, training, and testing, and implement the resulting changes accordingly; and  
  d. Ensure the rigor, intensity, scope, and results of incident handling activities are comparable and predictable across the organization.

**Discussion**

Organizations recognize that incident response capabilities are dependent on the capabilities of organizational systems and the mission and business processes being supported by those systems. Organizations consider incident response as part of the definition, design, and development of mission and business processes and systems. Incident-related information can be obtained from a variety of sources, including audit monitoring, physical access monitoring, and network monitoring; user or administrator reports; and reported supply chain events. An effective incident handling capability includes coordination among many organizational entities (e.g., mission or business owners, system owners, authorizing officials, human resources offices, physical security offices, personnel security offices, legal departments, risk executive [function], operations personnel, procurement offices). Suspected security incidents include the receipt of suspicious email communications that can contain malicious code. Suspected supply chain incidents include the insertion of counterfeit hardware or malicious code into organizational systems or system components. For federal agencies, an incident that involves personally identifiable information is considered a breach. A breach results in unauthorized disclosure, the loss of control, unauthorized acquisition, compromise, or a similar occurrence where a person other than an authorized user accesses or potentially accesses personally identifiable information or an authorized user accesses or potentially accesses such information for other than authorized purposes.

---

### IR-5 — Incident Monitoring

**Control**

Track and document incidents.

**Discussion**

Documenting incidents includes maintaining records about each incident, the status of the incident, and other pertinent information necessary for forensics as well as evaluating incident details, trends, and handling. Incident information can be obtained from a variety of sources, including network monitoring, incident reports, incident response teams, user complaints, supply chain partners, audit monitoring, physical access monitoring, and user and administrator reports. [IR-4] provides information on the types of incidents that are appropriate for monitoring.

---

### IR-6 — Incident Reporting

**Control**

  a. Require personnel to report suspected incidents to the organizational incident response capability within [assignment: organization-defined time period] ; and  
  b. Report incident information to [assignment: organization-defined authorities].

**Discussion**

The types of incidents reported, the content and timeliness of the reports, and the designated reporting authorities reflect applicable laws, executive orders, directives, regulations, policies, standards, and guidelines. Incident information can inform risk assessments, control effectiveness assessments, security requirements for acquisitions, and selection criteria for technology products.

---

### IR-7 — Incident Response Assistance

**Control**

Provide an incident response support resource, integral to the organizational incident response capability, that offers advice and assistance to users of the system for the handling and reporting of incidents.

**Discussion**

Incident response support resources provided by organizations include help desks, assistance groups, automated ticketing systems to open and track incident response tickets, and access to forensics services or consumer redress services, when required.

---

### MA-2 — Controlled Maintenance

**Control**

  a. Schedule, document, and review records of maintenance, repair, and replacement on system components in accordance with manufacturer or vendor specifications and/or organizational requirements;  
  b. Approve and monitor all maintenance activities, whether performed on site or remotely and whether the system or system components are serviced on site or removed to another location;  
  c. Require that [assignment: organization-defined personnel or roles] explicitly approve the removal of the system or system components from organizational facilities for off-site maintenance, repair, or replacement;  
  d. Sanitize equipment to remove the following information from associated media prior to removal from organizational facilities for off-site maintenance, repair, or replacement: [assignment: organization-defined information];  
  e. Check all potentially impacted controls to verify that the controls are still functioning properly following maintenance, repair, or replacement actions; and  
  f. Include the following information in organizational maintenance records: [assignment: organization-defined information].

**Discussion**

Controlling system maintenance addresses the information security aspects of the system maintenance program and applies to all types of maintenance to system components conducted by local or nonlocal entities. Maintenance includes peripherals such as scanners, copiers, and printers. Information necessary for creating effective maintenance records includes the date and time of maintenance, a description of the maintenance performed, names of the individuals or group performing the maintenance, name of the escort, and system components or equipment that are removed or replaced. Organizations consider supply chain-related risks associated with replacement components for systems.

---

### MA-3 — Maintenance Tools

**Control**

  a. Approve, control, and monitor the use of system maintenance tools; and  
  b. Review previously approved system maintenance tools [assignment: organization-defined frequency].

**Discussion**

Approving, controlling, monitoring, and reviewing maintenance tools address security-related issues associated with maintenance tools that are not within system authorization boundaries and are used specifically for diagnostic and repair actions on organizational systems. Organizations have flexibility in determining roles for the approval of maintenance tools and how that approval is documented. A periodic review of maintenance tools facilitates the withdrawal of approval for outdated, unsupported, irrelevant, or no-longer-used tools. Maintenance tools can include hardware, software, and firmware items and may be pre-installed, brought in with maintenance personnel on media, cloud-based, or downloaded from a website. Such tools can be vehicles for transporting malicious code, either intentionally or unintentionally, into a facility and subsequently into systems. Maintenance tools can include hardware and software diagnostic test equipment and packet sniffers. The hardware and software components that support maintenance and are a part of the system (including the software implementing utilities such as "ping," "ls," "ipconfig," or the hardware and software implementing the monitoring port of an Ethernet switch) are not addressed by maintenance tools.

---

### MA-4 — Nonlocal Maintenance

**Control**

  a. Approve and monitor nonlocal maintenance and diagnostic activities;  
  b. Allow the use of nonlocal maintenance and diagnostic tools only as consistent with organizational policy and documented in the security plan for the system;  
  c. Employ strong authentication in the establishment of nonlocal maintenance and diagnostic sessions;  
  d. Maintain records for nonlocal maintenance and diagnostic activities; and  
  e. Terminate session and network connections when nonlocal maintenance is completed.

**Discussion**

Nonlocal maintenance and diagnostic activities are conducted by individuals who communicate through either an external or internal network. Local maintenance and diagnostic activities are carried out by individuals who are physically present at the system location and not communicating across a network connection. Authentication techniques used to establish nonlocal maintenance and diagnostic sessions reflect the network access requirements in [IA-2] . Strong authentication requires authenticators that are resistant to replay attacks and employ multi-factor authentication. Strong authenticators include PKI where certificates are stored on a token protected by a password, passphrase, or biometric. Enforcing requirements in [MA-4] is accomplished, in part, by other controls. [SP 800-63B] provides additional guidance on strong authentication and authenticators.

---

### MA-5 — Maintenance Personnel

**Control**

  a. Establish a process for maintenance personnel authorization and maintain a list of authorized maintenance organizations or personnel;  
  b. Verify that non-escorted personnel performing maintenance on the system possess the required access authorizations; and  
  c. Designate organizational personnel with required access authorizations and technical competence to supervise the maintenance activities of personnel who do not possess the required access authorizations.

**Discussion**

Maintenance personnel refers to individuals who perform hardware or software maintenance on organizational systems, while [PE-2] addresses physical access for individuals whose maintenance duties place them within the physical protection perimeter of the systems. Technical competence of supervising individuals relates to the maintenance performed on the systems, while having required access authorizations refers to maintenance on and near the systems. Individuals not previously identified as authorized maintenance personnel—such as information technology manufacturers, vendors, systems integrators, and consultants—may require privileged access to organizational systems, such as when they are required to conduct maintenance activities with little or no notice. Based on organizational assessments of risk, organizations may issue temporary credentials to these individuals. Temporary credentials may be for one-time use or for very limited time periods.

---

### MP-2 — Media Access

**Control**

Restrict access to [assignment: organization-defined organization-defined types of digital and/or non-digital media] to [assignment: organization-defined organization-defined personnel or roles].

**Discussion**

System media includes digital and non-digital media. Digital media includes flash drives, diskettes, magnetic tapes, external or removable hard disk drives (e.g., solid state, magnetic), compact discs, and digital versatile discs. Non-digital media includes paper and microfilm. Denying access to patient medical records in a community hospital unless the individuals seeking access to such records are authorized healthcare providers is an example of restricting access to non-digital media. Limiting access to the design specifications stored on compact discs in the media library to individuals on the system development team is an example of restricting access to digital media.

---

### MP-3 — Media Marking

**Control**

  a. Mark system media indicating the distribution limitations, handling caveats, and applicable security markings (if any) of the information; and  
  b. Exempt [assignment: organization-defined types of media exempted from marking] from marking if the media remain within [assignment: organization-defined controlled areas].

**Discussion**

Security marking refers to the application or use of human-readable security attributes. Digital media includes diskettes, magnetic tapes, external or removable hard disk drives (e.g., solid state, magnetic), flash drives, compact discs, and digital versatile discs. Non-digital media includes paper and microfilm. Controlled unclassified information is defined by the National Archives and Records Administration along with the appropriate safeguarding and dissemination requirements for such information and is codified in [32 CFR 2002] . Security markings are generally not required for media that contains information determined by organizations to be in the public domain or to be publicly releasable. Some organizations may require markings for public information indicating that the information is publicly releasable. System media marking reflects applicable laws, executive orders, directives, policies, regulations, standards, and guidelines.

---

### MP-4 — Media Storage

**Control**

  a. Physically control and securely store [assignment: organization-defined organization-defined types of digital and/or non-digital media] within [assignment: organization-defined organization-defined controlled areas] ; and  
  b. Protect system media types defined in MP-4a until the media are destroyed or sanitized using approved equipment, techniques, and procedures.

**Discussion**

System media includes digital and non-digital media. Digital media includes flash drives, diskettes, magnetic tapes, external or removable hard disk drives (e.g., solid state, magnetic), compact discs, and digital versatile discs. Non-digital media includes paper and microfilm. Physically controlling stored media includes conducting inventories, ensuring procedures are in place to allow individuals to check out and return media to the library, and maintaining accountability for stored media. Secure storage includes a locked drawer, desk, or cabinet or a controlled media library. The type of media storage is commensurate with the security category or classification of the information on the media. Controlled areas are spaces that provide physical and procedural controls to meet the requirements established for protecting information and systems. Fewer controls may be needed for media that contains information determined to be in the public domain, publicly releasable, or have limited adverse impacts on organizations, operations, or individuals if accessed by other than authorized personnel. In these situations, physical access controls provide adequate protection.

---

### MP-5 — Media Transport

**Control**

  a. Protect and control [assignment: organization-defined types of system media] during transport outside of controlled areas using [assignment: organization-defined organization-defined controls];  
  b. Maintain accountability for system media during transport outside of controlled areas;  
  c. Document activities associated with the transport of system media; and  
  d. Restrict the activities associated with the transport of system media to authorized personnel.

**Discussion**

System media includes digital and non-digital media. Digital media includes flash drives, diskettes, magnetic tapes, external or removable hard disk drives (e.g., solid state and magnetic), compact discs, and digital versatile discs. Non-digital media includes microfilm and paper. Controlled areas are spaces for which organizations provide physical or procedural controls to meet requirements established for protecting information and systems. Controls to protect media during transport include cryptography and locked containers. Cryptographic mechanisms can provide confidentiality and integrity protections depending on the mechanisms implemented. Activities associated with media transport include releasing media for transport, ensuring that media enters the appropriate transport processes, and the actual transport. Authorized transport and courier personnel may include individuals external to the organization. Maintaining accountability of media during transport includes restricting transport activities to authorized personnel and tracking and/or obtaining records of transport activities as the media moves through the transportation system to prevent and detect loss, destruction, or tampering. Organizations establish documentation requirements for activities associated with the transport of system media in accordance with organizational assessments of risk. Organizations maintain the flexibility to define record-keeping methods for the different types of media transport as part of a system of transport-related records.

---

### MP-6 — Media Sanitization

**Control**

  a. Sanitize [assignment: organization-defined organization-defined system media] prior to disposal, release out of organizational control, or release for reuse using [assignment: organization-defined organization-defined sanitization techniques and procedures] ; and  
  b. Employ sanitization mechanisms with the strength and integrity commensurate with the security category or classification of the information.

**Discussion**

Media sanitization applies to all digital and non-digital system media subject to disposal or reuse, whether or not the media is considered removable. Examples include digital media in scanners, copiers, printers, notebook computers, workstations, network components, mobile devices, and non-digital media (e.g., paper and microfilm). The sanitization process removes information from system media such that the information cannot be retrieved or reconstructed. Sanitization techniques—including clearing, purging, cryptographic erase, de-identification of personally identifiable information, and destruction—prevent the disclosure of information to unauthorized individuals when such media is reused or released for disposal. Organizations determine the appropriate sanitization methods, recognizing that destruction is sometimes necessary when other methods cannot be applied to media requiring sanitization. Organizations use discretion on the employment of approved sanitization techniques and procedures for media that contains information deemed to be in the public domain or publicly releasable or information deemed to have no adverse impact on organizations or individuals if released for reuse or disposal. Sanitization of non-digital media includes destruction, removing a classified appendix from an otherwise unclassified document, or redacting selected sections or words from a document by obscuring the redacted sections or words in a manner equivalent in effectiveness to removing them from the document. NSA standards and policies control the sanitization process for media that contains classified information. NARA policies control the sanitization process for controlled unclassified information.

---

### MP-7 — Media Use

**Control**

  a. [selection (one): restrict; prohibit] the use of [assignment: organization-defined types of system media] on [assignment: organization-defined systems or system components] using [assignment: organization-defined controls] ; and  
  b. Prohibit the use of portable storage devices in organizational systems when such devices have no identifiable owner.

**Discussion**

System media includes both digital and non-digital media. Digital media includes diskettes, magnetic tapes, flash drives, compact discs, digital versatile discs, and removable hard disk drives. Non-digital media includes paper and microfilm. Media use protections also apply to mobile devices with information storage capabilities. In contrast to [MP-2] , which restricts user access to media, MP-7 restricts the use of certain types of media on systems, for example, restricting or prohibiting the use of flash drives or external hard disk drives. Organizations use technical and nontechnical controls to restrict the use of system media. Organizations may restrict the use of portable storage devices, for example, by using physical cages on workstations to prohibit access to certain external ports or disabling or removing the ability to insert, read, or write to such devices. Organizations may also limit the use of portable storage devices to only approved devices, including devices provided by the organization, devices provided by other approved organizations, and devices that are not personally owned. Finally, organizations may restrict the use of portable storage devices based on the type of device, such as by prohibiting the use of writeable, portable storage devices and implementing this restriction by disabling or removing the capability to write to such devices. Requiring identifiable owners for storage devices reduces the risk of using such devices by allowing organizations to assign responsibility for addressing known vulnerabilities in the devices.

---

### PE-2 — Physical Access Authorizations

**Control**

  a. Develop, approve, and maintain a list of individuals with authorized access to the facility where the system resides;  
  b. Issue authorization credentials for facility access;  
  c. Review the access list detailing authorized facility access by individuals [assignment: organization-defined frequency] ; and  
  d. Remove individuals from the facility access list when access is no longer required.

**Discussion**

Physical access authorizations apply to employees and visitors. Individuals with permanent physical access authorization credentials are not considered visitors. Authorization credentials include ID badges, identification cards, and smart cards. Organizations determine the strength of authorization credentials needed consistent with applicable laws, executive orders, directives, regulations, policies, standards, and guidelines. Physical access authorizations may not be necessary to access certain areas within facilities that are designated as publicly accessible.

---

### PE-3 — Physical Access Control

**Control**

  a. Enforce physical access authorizations at [assignment: organization-defined entry and exit points] by:  
    1. Verifying individual access authorizations before granting access to the facility; and  
    2. Controlling ingress and egress to the facility using [selection (one-or-more): [assignment: organization-defined systems or devices] ; guards];  
  b. Maintain physical access audit logs for [assignment: organization-defined entry or exit points];  
  c. Control access to areas within the facility designated as publicly accessible by implementing the following controls: [assignment: organization-defined physical access controls];  
  d. Escort visitors and control visitor activity [assignment: organization-defined circumstances];  
  e. Secure keys, combinations, and other physical access devices;  
  f. Inventory [assignment: organization-defined physical access devices] every [assignment: organization-defined frequency] ; and  
  g. Change combinations and keys [assignment: organization-defined organization-defined frequency] and/or when keys are lost, combinations are compromised, or when individuals possessing the keys or combinations are transferred or terminated.

**Discussion**

Physical access control applies to employees and visitors. Individuals with permanent physical access authorizations are not considered visitors. Physical access controls for publicly accessible areas may include physical access control logs/records, guards, or physical access devices and barriers to prevent movement from publicly accessible areas to non-public areas. Organizations determine the types of guards needed, including professional security staff, system users, or administrative staff. Physical access devices include keys, locks, combinations, biometric readers, and card readers. Physical access control systems comply with applicable laws, executive orders, directives, policies, regulations, standards, and guidelines. Organizations have flexibility in the types of audit logs employed. Audit logs can be procedural, automated, or some combination thereof. Physical access points can include facility access points, interior access points to systems that require supplemental access controls, or both. Components of systems may be in areas designated as publicly accessible with organizations controlling access to the components.

---

### PE-4 — Access Control for Transmission

**Control**

Control physical access to [assignment: organization-defined system distribution and transmission lines] within organizational facilities using [assignment: organization-defined security controls].

**Discussion**

Security controls applied to system distribution and transmission lines prevent accidental damage, disruption, and physical tampering. Such controls may also be necessary to prevent eavesdropping or modification of unencrypted transmissions. Security controls used to control physical access to system distribution and transmission lines include disconnected or locked spare jacks, locked wiring closets, protection of cabling by conduit or cable trays, and wiretapping sensors.

---

### PE-5 — Access Control for Output Devices

**Control**

Control physical access to output from [assignment: organization-defined output devices] to prevent unauthorized individuals from obtaining the output.

**Discussion**

Controlling physical access to output devices includes placing output devices in locked rooms or other secured areas with keypad or card reader access controls and allowing access to authorized individuals only, placing output devices in locations that can be monitored by personnel, installing monitor or screen filters, and using headphones. Examples of output devices include monitors, printers, scanners, audio devices, facsimile machines, and copiers.

---

### PE-6 — Monitoring Physical Access

**Control**

  a. Monitor physical access to the facility where the system resides to detect and respond to physical security incidents;  
  b. Review physical access logs [assignment: organization-defined frequency] and upon occurrence of [assignment: organization-defined events] ; and  
  c. Coordinate results of reviews and investigations with the organizational incident response capability.

**Discussion**

Physical access monitoring includes publicly accessible areas within organizational facilities. Examples of physical access monitoring include the employment of guards, video surveillance equipment (i.e., cameras), and sensor devices. Reviewing physical access logs can help identify suspicious activity, anomalous events, or potential threats. The reviews can be supported by audit logging controls, such as [AU-2] , if the access logs are part of an automated system. Organizational incident response capabilities include investigations of physical security incidents and responses to the incidents. Incidents include security violations or suspicious physical access activities. Suspicious physical access activities include accesses outside of normal work hours, repeated accesses to areas not normally accessed, accesses for unusual lengths of time, and out-of-sequence accesses.

---

### PE-17 — Alternate Work Site

**Control**

  a. Determine and document the [assignment: organization-defined alternate work sites] allowed for use by employees;  
  b. Employ the following controls at alternate work sites: [assignment: organization-defined controls];  
  c. Assess the effectiveness of controls at alternate work sites; and  
  d. Provide a means for employees to communicate with information security and privacy personnel in case of incidents.

**Discussion**

Alternate work sites include government facilities or the private residences of employees. While distinct from alternative processing sites, alternate work sites can provide readily available alternate locations during contingency operations. Organizations can define different sets of controls for specific alternate work sites or types of sites depending on the work-related activities conducted at the sites. Implementing and assessing the effectiveness of organization-defined controls and providing a means to communicate incidents at alternate work sites supports the contingency planning activities of organizations.

---

### PL-2 — System Security and Privacy Plans

**Control**

  a. Develop security and privacy plans for the system that:  
    1. Are consistent with the organization’s enterprise architecture;  
    2. Explicitly define the constituent system components;  
    3. Describe the operational context of the system in terms of mission and business processes;  
    4. Identify the individuals that fulfill system roles and responsibilities;  
    5. Identify the information types processed, stored, and transmitted by the system;  
    6. Provide the security categorization of the system, including supporting rationale;  
    7. Describe any specific threats to the system that are of concern to the organization;  
    8. Provide the results of a privacy risk assessment for systems processing personally identifiable information;  
    9. Describe the operational environment for the system and any dependencies on or connections to other systems or system components;  
    10. Provide an overview of the security and privacy requirements for the system;  
    11. Identify any relevant control baselines or overlays, if applicable;  
    12. Describe the controls in place or planned for meeting the security and privacy requirements, including a rationale for any tailoring decisions;  
    13. Include risk determinations for security and privacy architecture and design decisions;  
    14. Include security- and privacy-related activities affecting the system that require planning and coordination with [assignment: organization-defined individuals or groups] ; and  
    15. Are reviewed and approved by the authorizing official or designated representative prior to plan implementation.  
  b. Distribute copies of the plans and communicate subsequent changes to the plans to [assignment: organization-defined personnel or roles];  
  c. Review the plans [assignment: organization-defined frequency];  
  d. Update the plans to address changes to the system and environment of operation or problems identified during plan implementation or control assessments; and  
  e. Protect the plans from unauthorized disclosure and modification.

**Discussion**

System security and privacy plans are scoped to the system and system components within the defined authorization boundary and contain an overview of the security and privacy requirements for the system and the controls selected to satisfy the requirements. The plans describe the intended application of each selected control in the context of the system with a sufficient level of detail to correctly implement the control and to subsequently assess the effectiveness of the control. The control documentation describes how system-specific and hybrid controls are implemented and the plans and expectations regarding the functionality of the system. System security and privacy plans can also be used in the design and development of systems in support of life cycle-based security and privacy engineering processes. System security and privacy plans are living documents that are updated and adapted throughout the system development life cycle (e.g., during capability determination, analysis of alternatives, requests for proposal, and design reviews). [Section 2.1] describes the different types of requirements that are relevant to organizations during the system development life cycle and the relationship between requirements and controls.

Organizations may develop a single, integrated security and privacy plan or maintain separate plans. Security and privacy plans relate security and privacy requirements to a set of controls and control enhancements. The plans describe how the controls and control enhancements meet the security and privacy requirements but do not provide detailed, technical descriptions of the design or implementation of the controls and control enhancements. Security and privacy plans contain sufficient information (including specifications of control parameter values for selection and assignment operations explicitly or by reference) to enable a design and implementation that is unambiguously compliant with the intent of the plans and subsequent determinations of risk to organizational operations and assets, individuals, other organizations, and the Nation if the plan is implemented.

Security and privacy plans need not be single documents. The plans can be a collection of various documents, including documents that already exist. Effective security and privacy plans make extensive use of references to policies, procedures, and additional documents, including design and implementation specifications where more detailed information can be obtained. The use of references helps reduce the documentation associated with security and privacy programs and maintains the security- and privacy-related information in other established management and operational areas, including enterprise architecture, system development life cycle, systems engineering, and acquisition. Security and privacy plans need not contain detailed contingency plan or incident response plan information but can instead provide—explicitly or by reference—sufficient information to define what needs to be accomplished by those plans.

Security- and privacy-related activities that may require coordination and planning with other individuals or groups within the organization include assessments, audits, inspections, hardware and software maintenance, acquisition and supply chain risk management, patch management, and contingency plan testing. Planning and coordination include emergency and nonemergency (i.e., planned or non-urgent unplanned) situations. The process defined by organizations to plan and coordinate security- and privacy-related activities can also be included in other documents, as appropriate.

---

### PS-3 — Personnel Screening

**Control**

  a. Screen individuals prior to authorizing access to the system; and  
  b. Rescreen individuals in accordance with [assignment: organization-defined organization-defined conditions requiring rescreening and, where rescreening is so indicated, the frequency of rescreening].

**Discussion**

Personnel screening and rescreening activities reflect applicable laws, executive orders, directives, regulations, policies, standards, guidelines, and specific criteria established for the risk designations of assigned positions. Examples of personnel screening include background investigations and agency checks. Organizations may define different rescreening conditions and frequencies for personnel accessing systems based on types of information processed, stored, or transmitted by the systems.

---

### PS-4 — Personnel Termination

**Control**

Upon termination of individual employment:  
  a. Disable system access within [assignment: organization-defined time period];  
  b. Terminate or revoke any authenticators and credentials associated with the individual;  
  c. Conduct exit interviews that include a discussion of [assignment: organization-defined information security topics];  
  d. Retrieve all security-related organizational system-related property; and  
  e. Retain access to organizational information and systems formerly controlled by terminated individual.

**Discussion**

System property includes hardware authentication tokens, system administration technical manuals, keys, identification cards, and building passes. Exit interviews ensure that terminated individuals understand the security constraints imposed by being former employees and that proper accountability is achieved for system-related property. Security topics at exit interviews include reminding individuals of nondisclosure agreements and potential limitations on future employment. Exit interviews may not always be possible for some individuals, including in cases related to the unavailability of supervisors, illnesses, or job abandonment. Exit interviews are important for individuals with security clearances. The timely execution of termination actions is essential for individuals who have been terminated for cause. In certain situations, organizations consider disabling the system accounts of individuals who are being terminated prior to the individuals being notified.

---

### PS-5 — Personnel Transfer

**Control**

  a. Review and confirm ongoing operational need for current logical and physical access authorizations to systems and facilities when individuals are reassigned or transferred to other positions within the organization;  
  b. Initiate [assignment: organization-defined transfer or reassignment actions] within [assignment: organization-defined time period following the formal transfer action];  
  c. Modify access authorization as needed to correspond with any changes in operational need due to reassignment or transfer; and  
  d. Notify [assignment: organization-defined personnel or roles] within [assignment: organization-defined time period].

**Discussion**

Personnel transfer applies when reassignments or transfers of individuals are permanent or of such extended duration as to make the actions warranted. Organizations define actions appropriate for the types of reassignments or transfers, whether permanent or extended. Actions that may be required for personnel transfers or reassignments to other positions within organizations include returning old and issuing new keys, identification cards, and building passes; closing system accounts and establishing new accounts; changing system access authorizations (i.e., privileges); and providing for access to official records to which individuals had access at previous work locations and in previous system accounts.

---

### RA-3 — Risk Assessment

**Control**

  a. Conduct a risk assessment, including:  
    1. Identifying threats to and vulnerabilities in the system;  
    2. Determining the likelihood and magnitude of harm from unauthorized access, use, disclosure, disruption, modification, or destruction of the system, the information it processes, stores, or transmits, and any related information; and  
    3. Determining the likelihood and impact of adverse effects on individuals arising from the processing of personally identifiable information;  
  b. Integrate risk assessment results and risk management decisions from the organization and mission or business process perspectives with system-level risk assessments;  
  c. Document risk assessment results in [selection (one): security and privacy plans; risk assessment report; [assignment: organization-defined document] ];  
  d. Review risk assessment results [assignment: organization-defined frequency];  
  e. Disseminate risk assessment results to [assignment: organization-defined personnel or roles] ; and  
  f. Update the risk assessment [assignment: organization-defined frequency] or when there are significant changes to the system, its environment of operation, or other conditions that may impact the security or privacy state of the system.

**Discussion**

Risk assessments consider threats, vulnerabilities, likelihood, and impact to organizational operations and assets, individuals, other organizations, and the Nation. Risk assessments also consider risk from external parties, including contractors who operate systems on behalf of the organization, individuals who access organizational systems, service providers, and outsourcing entities.

Organizations can conduct risk assessments at all three levels in the risk management hierarchy (i.e., organization level, mission/business process level, or information system level) and at any stage in the system development life cycle. Risk assessments can also be conducted at various steps in the Risk Management Framework, including preparation, categorization, control selection, control implementation, control assessment, authorization, and control monitoring. Risk assessment is an ongoing activity carried out throughout the system development life cycle.

Risk assessments can also address information related to the system, including system design, the intended use of the system, testing results, and supply chain-related information or artifacts. Risk assessments can play an important role in control selection processes, particularly during the application of tailoring guidance and in the earliest phases of capability determination.

---

### RA-5 — Vulnerability Monitoring and Scanning

**Control**

  a. Monitor and scan for vulnerabilities in the system and hosted applications [assignment: organization-defined organization-defined frequency and/or randomly in accordance with organization-defined process] and when new vulnerabilities potentially affecting the system are identified and reported;  
  b. Employ vulnerability monitoring tools and techniques that facilitate interoperability among tools and automate parts of the vulnerability management process by using standards for:  
    1. Enumerating platforms, software flaws, and improper configurations;  
    2. Formatting checklists and test procedures; and  
    3. Measuring vulnerability impact;  
  c. Analyze vulnerability scan reports and results from vulnerability monitoring;  
  d. Remediate legitimate vulnerabilities [assignment: organization-defined response times] in accordance with an organizational assessment of risk;  
  e. Share information obtained from the vulnerability monitoring process and control assessments with [assignment: organization-defined personnel or roles] to help eliminate similar vulnerabilities in other systems; and  
  f. Employ vulnerability monitoring tools that include the capability to readily update the vulnerabilities to be scanned.

**Discussion**

Security categorization of information and systems guides the frequency and comprehensiveness of vulnerability monitoring (including scans). Organizations determine the required vulnerability monitoring for system components, ensuring that the potential sources of vulnerabilities—such as infrastructure components (e.g., switches, routers, guards, sensors), networked printers, scanners, and copiers—are not overlooked. The capability to readily update vulnerability monitoring tools as new vulnerabilities are discovered and announced and as new scanning methods are developed helps to ensure that new vulnerabilities are not missed by employed vulnerability monitoring tools. The vulnerability monitoring tool update process helps to ensure that potential vulnerabilities in the system are identified and addressed as quickly as possible. Vulnerability monitoring and analyses for custom software may require additional approaches, such as static analysis, dynamic analysis, binary analysis, or a hybrid of the three approaches. Organizations can use these analysis approaches in source code reviews and in a variety of tools, including web-based application scanners, static analysis tools, and binary analyzers.

Vulnerability monitoring includes scanning for patch levels; scanning for functions, ports, protocols, and services that should not be accessible to users or devices; and scanning for flow control mechanisms that are improperly configured or operating incorrectly. Vulnerability monitoring may also include continuous vulnerability monitoring tools that use instrumentation to continuously analyze components. Instrumentation-based tools may improve accuracy and may be run throughout an organization without scanning. Vulnerability monitoring tools that facilitate interoperability include tools that are Security Content Automated Protocol (SCAP)-validated. Thus, organizations consider using scanning tools that express vulnerabilities in the Common Vulnerabilities and Exposures (CVE) naming convention and that employ the Open Vulnerability Assessment Language (OVAL) to determine the presence of vulnerabilities. Sources for vulnerability information include the Common Weakness Enumeration (CWE) listing and the National Vulnerability Database (NVD). Control assessments, such as red team exercises, provide additional sources of potential vulnerabilities for which to scan. Organizations also consider using scanning tools that express vulnerability impact by the Common Vulnerability Scoring System (CVSS).

Vulnerability monitoring includes a channel and process for receiving reports of security vulnerabilities from the public at-large. Vulnerability disclosure programs can be as simple as publishing a monitored email address or web form that can receive reports, including notification authorizing good-faith research and disclosure of security vulnerabilities. Organizations generally expect that such research is happening with or without their authorization and can use public vulnerability disclosure channels to increase the likelihood that discovered vulnerabilities are reported directly to the organization for remediation.

Organizations may also employ the use of financial incentives (also known as "bug bounties" ) to further encourage external security researchers to report discovered vulnerabilities. Bug bounty programs can be tailored to the organization’s needs. Bounties can be operated indefinitely or over a defined period of time and can be offered to the general public or to a curated group. Organizations may run public and private bounties simultaneously and could choose to offer partially credentialed access to certain participants in order to evaluate security vulnerabilities from privileged vantage points.

---

### SA-8 — Security and Privacy Engineering Principles

**Control**

Apply the following systems security and privacy engineering principles in the specification, design, development, implementation, and modification of the system and system components: [assignment: organization-defined organization-defined systems security and privacy engineering principles].

**Discussion**

Systems security and privacy engineering principles are closely related to and implemented throughout the system development life cycle (see [SA-3] ). Organizations can apply systems security and privacy engineering principles to new systems under development or to systems undergoing upgrades. For existing systems, organizations apply systems security and privacy engineering principles to system upgrades and modifications to the extent feasible, given the current state of hardware, software, and firmware components within those systems.

The application of systems security and privacy engineering principles helps organizations develop trustworthy, secure, and resilient systems and reduces the susceptibility to disruptions, hazards, threats, and the creation of privacy problems for individuals. Examples of system security engineering principles include: developing layered protections; establishing security and privacy policies, architecture, and controls as the foundation for design and development; incorporating security and privacy requirements into the system development life cycle; delineating physical and logical security boundaries; ensuring that developers are trained on how to build secure software; tailoring controls to meet organizational needs; and performing threat modeling to identify use cases, threat agents, attack vectors and patterns, design patterns, and compensating controls needed to mitigate risk.

Organizations that apply systems security and privacy engineering concepts and principles can facilitate the development of trustworthy, secure systems, system components, and system services; reduce risk to acceptable levels; and make informed risk management decisions. System security engineering principles can also be used to protect against certain supply chain risks, including incorporating tamper-resistant hardware into a design.

---

### SC-2 — Separation of System and User Functionality

**Control**

Separate user functionality, including user interface services, from system management functionality.

**Discussion**

System management functionality includes functions that are necessary to administer databases, network components, workstations, or servers. These functions typically require privileged user access. The separation of user functions from system management functions is physical or logical. Organizations may separate system management functions from user functions by using different computers, instances of operating systems, central processing units, or network addresses; by employing virtualization techniques; or some combination of these or other methods. Separation of system management functions from user functions includes web administrative interfaces that employ separate authentication methods for users of any other system resources. Separation of system and user functions may include isolating administrative interfaces on different domains and with additional access controls. The separation of system and user functionality can be achieved by applying the systems security engineering design principles in [SA-8] , including [SA-8(1)], [SA-8(3)], [SA-8(4)], [SA-8(10)], [SA-8(12)], [SA-8(13)], [SA-8(14)] , and [SA-8(18)].

---

### SC-4 — Information in Shared System Resources

**Control**

Prevent unauthorized and unintended information transfer via shared system resources.

**Discussion**

Preventing unauthorized and unintended information transfer via shared system resources stops information produced by the actions of prior users or roles (or the actions of processes acting on behalf of prior users or roles) from being available to current users or roles (or current processes acting on behalf of current users or roles) that obtain access to shared system resources after those resources have been released back to the system. Information in shared system resources also applies to encrypted representations of information. In other contexts, control of information in shared system resources is referred to as object reuse and residual information protection. Information in shared system resources does not address information remanence, which refers to the residual representation of data that has been nominally deleted; covert channels (including storage and timing channels), where shared system resources are manipulated to violate information flow restrictions; or components within systems for which there are only single users or roles.

---

### SC-7 — Boundary Protection

**Control**

  a. Monitor and control communications at the external managed interfaces to the system and at key internal managed interfaces within the system;  
  b. Implement subnetworks for publicly accessible system components that are [selection (one): physically; logically] separated from internal organizational networks; and  
  c. Connect to external networks or systems only through managed interfaces consisting of boundary protection devices arranged in accordance with an organizational security and privacy architecture.

**Discussion**

Managed interfaces include gateways, routers, firewalls, guards, network-based malicious code analysis, virtualization systems, or encrypted tunnels implemented within a security architecture. Subnetworks that are physically or logically separated from internal networks are referred to as demilitarized zones or DMZs. Restricting or prohibiting interfaces within organizational systems includes restricting external web traffic to designated web servers within managed interfaces, prohibiting external traffic that appears to be spoofing internal addresses, and prohibiting internal traffic that appears to be spoofing external addresses. [SP 800-189] provides additional information on source address validation techniques to prevent ingress and egress of traffic with spoofed addresses. Commercial telecommunications services are provided by network components and consolidated management systems shared by customers. These services may also include third party-provided access lines and other service elements. Such services may represent sources of increased risk despite contract security provisions. Boundary protection may be implemented as a common control for all or part of an organizational network such that the boundary to be protected is greater than a system-specific boundary (i.e., an authorization boundary).

---

### SC-8 — Transmission Confidentiality and Integrity

**Control**

Protect the [selection (one-or-more): confidentiality; integrity] of transmitted information.

**Discussion**

Protecting the confidentiality and integrity of transmitted information applies to internal and external networks as well as any system components that can transmit information, including servers, notebook computers, desktop computers, mobile devices, printers, copiers, scanners, facsimile machines, and radios. Unprotected communication paths are exposed to the possibility of interception and modification. Protecting the confidentiality and integrity of information can be accomplished by physical or logical means. Physical protection can be achieved by using protected distribution systems. A protected distribution system is a wireline or fiber-optics telecommunications system that includes terminals and adequate electromagnetic, acoustical, electrical, and physical controls to permit its use for the unencrypted transmission of classified information. Logical protection can be achieved by employing encryption techniques.

Organizations that rely on commercial providers who offer transmission services as commodity services rather than as fully dedicated services may find it difficult to obtain the necessary assurances regarding the implementation of needed controls for transmission confidentiality and integrity. In such situations, organizations determine what types of confidentiality or integrity services are available in standard, commercial telecommunications service packages. If it is not feasible to obtain the necessary controls and assurances of control effectiveness through appropriate contracting vehicles, organizations can implement appropriate compensating controls.

---

### SC-10 — Network Disconnect

**Control**

Terminate the network connection associated with a communications session at the end of the session or after [assignment: organization-defined time period] of inactivity.

**Discussion**

Network disconnect applies to internal and external networks. Terminating network connections associated with specific communications sessions includes de-allocating TCP/IP address or port pairs at the operating system level and de-allocating the networking assignments at the application level if multiple application sessions are using a single operating system-level network connection. Periods of inactivity may be established by organizations and include time periods by type of network access or for specific network accesses.

---

### SC-12 — Cryptographic Key Establishment and Management

**Control**

Establish and manage cryptographic keys when cryptography is employed within the system in accordance with the following key management requirements: [assignment: organization-defined requirements].

**Discussion**

Cryptographic key management and establishment can be performed using manual procedures or automated mechanisms with supporting manual procedures. Organizations define key management requirements in accordance with applicable laws, executive orders, directives, regulations, policies, standards, and guidelines and specify appropriate options, parameters, and levels. Organizations manage trust stores to ensure that only approved trust anchors are part of such trust stores. This includes certificates with visibility external to organizational systems and certificates related to the internal operations of systems. [NIST CMVP] and [NIST CAVP] provide additional information on validated cryptographic modules and algorithms that can be used in cryptographic key management and establishment.

---

### SC-13 — Cryptographic Protection

**Control**

  a. Determine the [assignment: organization-defined cryptographic uses] ; and  
  b. Implement the following types of cryptography required for each specified cryptographic use: [assignment: organization-defined types of cryptography].

**Discussion**

Cryptography can be employed to support a variety of security solutions, including the protection of classified information and controlled unclassified information, the provision and implementation of digital signatures, and the enforcement of information separation when authorized individuals have the necessary clearances but lack the necessary formal access approvals. Cryptography can also be used to support random number and hash generation. Generally applicable cryptographic standards include FIPS-validated cryptography and NSA-approved cryptography. For example, organizations that need to protect classified information may specify the use of NSA-approved cryptography. Organizations that need to provision and implement digital signatures may specify the use of FIPS-validated cryptography. Cryptography is implemented in accordance with applicable laws, executive orders, directives, regulations, policies, standards, and guidelines.

---

### SC-15 — Collaborative Computing Devices and Applications

**Control**

  a. Prohibit remote activation of collaborative computing devices and applications with the following exceptions: [assignment: organization-defined exceptions where remote activation is to be allowed] ; and  
  b. Provide an explicit indication of use to users physically present at the devices.

**Discussion**

Collaborative computing devices and applications include remote meeting devices and applications, networked white boards, cameras, and microphones. The explicit indication of use includes signals to users when collaborative computing devices and applications are activated.

---

### SC-18 — Mobile Code

**Control**

  a. Define acceptable and unacceptable mobile code and mobile code technologies; and  
  b. Authorize, monitor, and control the use of mobile code within the system.

**Discussion**

Mobile code includes any program, application, or content that can be transmitted across a network (e.g., embedded in an email, document, or website) and executed on a remote system. Decisions regarding the use of mobile code within organizational systems are based on the potential for the code to cause damage to the systems if used maliciously. Mobile code technologies include Java applets, JavaScript, HTML5, WebGL, and VBScript. Usage restrictions and implementation guidelines apply to both the selection and use of mobile code installed on servers and mobile code downloaded and executed on individual workstations and devices, including notebook computers and smart phones. Mobile code policy and procedures address specific actions taken to prevent the development, acquisition, and introduction of unacceptable mobile code within organizational systems, including requiring mobile code to be digitally signed by a trusted source.

---

### SC-19 — Voice Over Internet Protocol  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5.

NIST note: Technology-specific; addressed as any other technology or protocol.

---

### SC-23 — Session Authenticity

**Control**

Protect the authenticity of communications sessions.

**Discussion**

Protecting session authenticity addresses communications protection at the session level, not at the packet level. Such protection establishes grounds for confidence at both ends of communications sessions in the ongoing identities of other parties and the validity of transmitted information. Authenticity protection includes protecting against "man-in-the-middle" attacks, session hijacking, and the insertion of false information into sessions.

---

### SC-28 — Protection of Information at Rest

**Control**

Protect the [selection (one-or-more): confidentiality; integrity] of the following information at rest: [assignment: organization-defined information at rest].

**Discussion**

Information at rest refers to the state of information when it is not in process or in transit and is located on system components. Such components include internal or external hard disk drives, storage area network devices, or databases. However, the focus of protecting information at rest is not on the type of storage device or frequency of access but rather on the state of the information. Information at rest addresses the confidentiality and integrity of information and covers user information and system information. System-related information that requires protection includes configurations or rule sets for firewalls, intrusion detection and prevention systems, filtering routers, and authentication information. Organizations may employ different mechanisms to achieve confidentiality and integrity protections, including the use of cryptographic mechanisms and file share scanning. Integrity protection can be achieved, for example, by implementing write-once-read-many (WORM) technologies. When adequate protection of information at rest cannot otherwise be achieved, organizations may employ other controls, including frequent scanning to identify malicious code at rest and secure offline storage in lieu of online storage.

---

### SI-2 — Flaw Remediation

**Control**

  a. Identify, report, and correct system flaws;  
  b. Test software and firmware updates related to flaw remediation for effectiveness and potential side effects before installation;  
  c. Install security-relevant software and firmware updates within [assignment: organization-defined time period] of the release of the updates; and  
  d. Incorporate flaw remediation into the organizational configuration management process.

**Discussion**

The need to remediate system flaws applies to all types of software and firmware. Organizations identify systems affected by software flaws, including potential vulnerabilities resulting from those flaws, and report this information to designated organizational personnel with information security and privacy responsibilities. Organizations consider establishing a controlled patching environment for mission-critical systems. Security-relevant updates include patches, service packs, and malicious code signatures. Organizations also address flaws discovered during assessments, continuous monitoring, incident response activities, and system error handling. By incorporating flaw remediation into configuration management processes, required remediation actions can be tracked and verified.

Organization-defined time periods for updating security-relevant software and firmware may vary based on a variety of risk factors, including the security category of the system, the criticality of the update (i.e., severity of the vulnerability related to the discovered flaw), the organizational risk tolerance, the mission supported by the system, or the threat environment. Some types of flaw remediation may require more testing than other types. Organizations determine the type of testing needed for the specific type of flaw remediation activity under consideration and the types of changes that are to be configuration-managed. Flaw remediation testing addresses both effectiveness of addressing security issues and for potential side effects on functionality, system and system component performance and operations. When implementing remediation activities, organizations consider the order and timing of updates to validate correct execution within the system environment, and to support system and component availability needs (i.e., implementing a staggered deployment strategy). In some situations, organizations may determine that the testing of software or firmware updates is not necessary or practical, such as when implementing simple malicious code signature updates. In testing decisions, organizations consider whether security-relevant software or firmware updates are obtained from authorized sources with appropriate digital signatures.

When implementing remediation activities, organizations consider the order and timing of updates to validate correct execution within the system environment, and to support system and component availability needs (i.e., implementing a staggered deployment strategy). Organizations verify that software and firmware updates come from authorized sources prior to downloading.

---

### SI-3 — Malicious Code Protection

**Control**

  a. Implement [selection (one-or-more): signature-based; non-signature-based] malicious code protection mechanisms at system entry and exit points to detect and eradicate malicious code;  
  b. Automatically update malicious code protection mechanisms as new releases are available in accordance with organizational configuration management policy and procedures;  
  c. Configure malicious code protection mechanisms to:  
    1. Perform periodic scans of the system [assignment: organization-defined frequency] and real-time scans of files from external sources at [selection (one-or-more): endpoint; network entry and exit points] as the files are downloaded, opened, or executed in accordance with organizational policy; and  
    2. [selection (one-or-more): block malicious code; quarantine malicious code; take [assignment: organization-defined action] ] ; and send alert to [assignment: organization-defined personnel or roles] in response to malicious code detection; and  
  d. Address the receipt of false positives during malicious code detection and eradication and the resulting potential impact on the availability of the system.

**Discussion**

System entry and exit points include firewalls, remote access servers, workstations, electronic mail servers, web servers, proxy servers, notebook computers, and mobile devices. Malicious code includes viruses, worms, Trojan horses, and spyware. Malicious code can also be encoded in various formats contained within compressed or hidden files or hidden in files using techniques such as steganography. Malicious code can be inserted into systems in a variety of ways, including by electronic mail, the world-wide web, and portable storage devices. Malicious code insertions occur through the exploitation of system vulnerabilities. A variety of technologies and methods exist to limit or eliminate the effects of malicious code.

Malicious code protection mechanisms include both signature- and nonsignature-based technologies. Nonsignature-based detection mechanisms include artificial intelligence techniques that use heuristics to detect, analyze, and describe the characteristics or behavior of malicious code and to provide controls against such code for which signatures do not yet exist or for which existing signatures may not be effective. Malicious code for which active signatures do not yet exist or may be ineffective includes polymorphic malicious code (i.e., code that changes signatures when it replicates). Nonsignature-based mechanisms also include reputation-based technologies. In addition to the above technologies, pervasive configuration management, comprehensive software integrity controls, and anti-exploitation software may be effective in preventing the execution of unauthorized code. Malicious code may be present in commercial off-the-shelf software as well as custom-built software and could include logic bombs, backdoors, and other types of attacks that could affect organizational mission and business functions.

In situations where malicious code cannot be detected by detection methods or technologies, organizations rely on other types of controls, including secure coding practices, configuration management and control, trusted procurement processes, and monitoring practices to ensure that software does not perform functions other than the functions intended. Organizations may determine that, in response to the detection of malicious code, different actions may be warranted. For example, organizations can define actions in response to malicious code detection during periodic scans, the detection of malicious downloads, or the detection of maliciousness when attempting to open or execute files.

---

### SI-4 — System Monitoring

**Control**

  a. Monitor the system to detect:  
    1. Attacks and indicators of potential attacks in accordance with the following monitoring objectives: [assignment: organization-defined monitoring objectives] ; and  
    2. Unauthorized local, network, and remote connections;  
  b. Identify unauthorized use of the system through the following techniques and methods: [assignment: organization-defined techniques and methods];  
  c. Invoke internal monitoring capabilities or deploy monitoring devices:  
    1. Strategically within the system to collect organization-determined essential information; and  
    2. At ad hoc locations within the system to track specific types of transactions of interest to the organization;  
  d. Analyze detected events and anomalies;  
  e. Adjust the level of system monitoring activity when there is a change in risk to organizational operations and assets, individuals, other organizations, or the Nation;  
  f. Obtain legal opinion regarding system monitoring activities; and  
  g. Provide [assignment: organization-defined system monitoring information] to [assignment: organization-defined personnel or roles] [selection (one-or-more): as needed; [assignment: organization-defined frequency] ].

**Discussion**

System monitoring includes external and internal monitoring. External monitoring includes the observation of events occurring at external interfaces to the system. Internal monitoring includes the observation of events occurring within the system. Organizations monitor systems by observing audit activities in real time or by observing other system aspects such as access patterns, characteristics of access, and other actions. The monitoring objectives guide and inform the determination of the events. System monitoring capabilities are achieved through a variety of tools and techniques, including intrusion detection and prevention systems, malicious code protection software, scanning tools, audit record monitoring software, and network monitoring software.

Depending on the security architecture, the distribution and configuration of monitoring devices may impact throughput at key internal and external boundaries as well as at other locations across a network due to the introduction of network throughput latency. If throughput management is needed, such devices are strategically located and deployed as part of an established organization-wide security architecture. Strategic locations for monitoring devices include selected perimeter locations and near key servers and server farms that support critical applications. Monitoring devices are typically employed at the managed interfaces associated with controls [SC-7] and [AC-17] . The information collected is a function of the organizational monitoring objectives and the capability of systems to support such objectives. Specific types of transactions of interest include Hypertext Transfer Protocol (HTTP) traffic that bypasses HTTP proxies. System monitoring is an integral part of organizational continuous monitoring and incident response programs, and output from system monitoring serves as input to those programs. System monitoring requirements, including the need for specific types of system monitoring, may be referenced in other controls (e.g., [AC-2g], [AC-2(7)], [AC-2(12)(a)], [AC-17(1)], [AU-13], [AU-13(1)], [AU-13(2)], [CM-3f], [CM-6d], [MA-3a], [MA-4a], [SC-5(3)(b)], [SC-7a], [SC-7(24)(b)], [SC-18b], [SC-43b] ). Adjustments to levels of system monitoring are based on law enforcement information, intelligence information, or other sources of information. The legality of system monitoring activities is based on applicable laws, executive orders, directives, regulations, policies, standards, and guidelines.

---

### SI-5 — Security Alerts, Advisories, and Directives

**Control**

  a. Receive system security alerts, advisories, and directives from [assignment: organization-defined external organizations] on an ongoing basis;  
  b. Generate internal security alerts, advisories, and directives as deemed necessary;  
  c. Disseminate security alerts, advisories, and directives to: [selection (one-or-more): [assignment: organization-defined personnel or roles] ; [assignment: organization-defined elements] ; [assignment: organization-defined external organizations] ] ; and  
  d. Implement security directives in accordance with established time frames, or notify the issuing organization of the degree of noncompliance.

**Discussion**

The Cybersecurity and Infrastructure Security Agency (CISA) generates security alerts and advisories to maintain situational awareness throughout the Federal Government. Security directives are issued by OMB or other designated organizations with the responsibility and authority to issue such directives. Compliance with security directives is essential due to the critical nature of many of these directives and the potential (immediate) adverse effects on organizational operations and assets, individuals, other organizations, and the Nation should the directives not be implemented in a timely manner. External organizations include supply chain partners, external mission or business partners, external service providers, and other peer or supporting organizations.

---

### AC-6(1) — Authorize Access to Security Functions

**Control**

Authorize access for [assignment: organization-defined individuals and roles] to:  
  (a) [assignment: organization-defined organization-defined security functions (deployed in hardware, software, and firmware)] ; and  
  (b) [assignment: organization-defined security-relevant information].

**Discussion**

Security functions include establishing system accounts, configuring access authorizations (i.e., permissions, privileges), configuring settings for events to be audited, and establishing intrusion detection parameters. Security-relevant information includes filtering rules for routers or firewalls, configuration parameters for security services, cryptographic key management information, and access control lists. Authorized personnel include security administrators, system administrators, system security officers, system programmers, and other privileged users.

---

### AC-6(2) — Non-privileged Access for Nonsecurity Functions

**Control**

Require that users of system accounts (or roles) with access to [assignment: organization-defined security functions or security-relevant information] use non-privileged accounts or roles, when accessing nonsecurity functions.

**Discussion**

Requiring the use of non-privileged accounts when accessing nonsecurity functions limits exposure when operating from within privileged accounts or roles. The inclusion of roles addresses situations where organizations implement access control policies, such as role-based access control, and where a change of role provides the same degree of assurance in the change of access authorizations for the user and the processes acting on behalf of the user as would be provided by a change between a privileged and non-privileged account.

---

### AC-6(5) — Privileged Accounts

**Control**

Restrict privileged accounts on the system to [assignment: organization-defined personnel or roles].

**Discussion**

Privileged accounts, including super user accounts, are typically described as system administrator for various types of commercial off-the-shelf operating systems. Restricting privileged accounts to specific personnel or roles prevents day-to-day users from accessing privileged information or privileged functions. Organizations may differentiate in the application of restricting privileged accounts between allowed privileges for local accounts and for domain accounts provided that they retain the ability to control system configurations for key parameters and as otherwise necessary to sufficiently mitigate risk.

---

### AC-6(9) — Log Use of Privileged Functions

**Control**

Log the execution of privileged functions.

**Discussion**

The misuse of privileged functions, either intentionally or unintentionally by authorized users or by unauthorized external entities that have compromised system accounts, is a serious and ongoing concern and can have significant adverse impacts on organizations. Logging and analyzing the use of privileged functions is one way to detect such misuse and, in doing so, help mitigate the risk from insider threats and the advanced persistent threat.

---

### AC-6(10) — Prohibit Non-privileged Users from Executing Privileged Functions

**Control**

Prevent non-privileged users from executing privileged functions.

**Discussion**

Privileged functions include disabling, circumventing, or altering implemented security or privacy controls, establishing system accounts, performing system integrity checks, and administering cryptographic key management activities. Non-privileged users are individuals who do not possess appropriate authorizations. Privileged functions that require protection from non-privileged users include circumventing intrusion detection and prevention mechanisms or malicious code protection mechanisms. Preventing non-privileged users from executing privileged functions is enforced by [AC-3].

---

### AC-11(1) — Pattern-hiding Displays

**Control**

Conceal, via the device lock, information previously visible on the display with a publicly viewable image.

**Discussion**

The pattern-hiding display can include static or dynamic images, such as patterns used with screen savers, photographic images, solid colors, clock, battery life indicator, or a blank screen with the caveat that controlled unclassified information is not displayed.

---

### AC-17(1) — Monitoring and Control

**Control**

Employ automated mechanisms to monitor and control remote access methods.

**Discussion**

Monitoring and control of remote access methods allows organizations to detect attacks and help ensure compliance with remote access policies by auditing the connection activities of remote users on a variety of system components, including servers, notebook computers, workstations, smart phones, and tablets. Audit logging for remote access is enforced by [AU-2] . Audit events are defined in [AU-2a].

---

### AC-17(2) — Protection of Confidentiality and Integrity Using Encryption

**Control**

Implement cryptographic mechanisms to protect the confidentiality and integrity of remote access sessions.

**Discussion**

Virtual private networks can be used to protect the confidentiality and integrity of remote access sessions. Transport Layer Security (TLS) is an example of a cryptographic protocol that provides end-to-end communications security over networks and is used for Internet communications and online transactions.

---

### AC-17(3) — Managed Access Control Points

**Control**

Route remote accesses through authorized and managed network access control points.

**Discussion**

Organizations consider the Trusted Internet Connections (TIC) initiative [DHS TIC] requirements for external network connections since limiting the number of access control points for remote access reduces attack surfaces.

---

### AC-17(4) — Privileged Commands and Access

**Control**

  (a) Authorize the execution of privileged commands and access to security-relevant information via remote access only in a format that provides assessable evidence and for the following needs: [assignment: organization-defined organization-defined needs] ; and  
  (b) Document the rationale for remote access in the security plan for the system.

**Discussion**

Remote access to systems represents a significant potential vulnerability that can be exploited by adversaries. As such, restricting the execution of privileged commands and access to security-relevant information via remote access reduces the exposure of the organization and the susceptibility to threats by adversaries to the remote access capability.

---

### AC-18(1) — Authentication and Encryption

**Control**

Protect wireless access to the system using authentication of [selection (one-or-more): users; devices] and encryption.

**Discussion**

Wireless networking capabilities represent a significant potential vulnerability that can be exploited by adversaries. To protect systems with wireless access points, strong authentication of users and devices along with strong encryption can reduce susceptibility to threats by adversaries involving wireless technologies.

---

### AC-19(5) — Full Device or Container-based Encryption

**Control**

Employ [selection (one): full-device encryption; container-based encryption] to protect the confidentiality and integrity of information on [assignment: organization-defined mobile devices].

**Discussion**

Container-based encryption provides a more fine-grained approach to data and information encryption on mobile devices, including encrypting selected data structures such as files, records, or fields.

---

### AC-20(1) — Limits on Authorized Use

**Control**

Permit authorized individuals to use an external system to access the system or to process, store, or transmit organization-controlled information only after:  
  (a) Verification of the implementation of controls on the external system as specified in the organization’s security and privacy policies and security and privacy plans; or  
  (b) Retention of approved system connection or processing agreements with the organizational entity hosting the external system.

**Discussion**

Limiting authorized use recognizes circumstances where individuals using external systems may need to access organizational systems. Organizations need assurance that the external systems contain the necessary controls so as not to compromise, damage, or otherwise harm organizational systems. Verification that the required controls have been implemented can be achieved by external, independent assessments, attestations, or other means, depending on the confidence level required by organizations.

---

### AC-20(2) — Portable Storage Devices — Restricted Use

**Control**

Restrict the use of organization-controlled portable storage devices by authorized individuals on external systems using [assignment: organization-defined restrictions].

**Discussion**

Limits on the use of organization-controlled portable storage devices in external systems include restrictions on how the devices may be used and under what conditions the devices may be used.

---

### AT-2(2) — Insider Threat

**Control**

Provide literacy training on recognizing and reporting potential indicators of insider threat.

**Discussion**

Potential indicators and possible precursors of insider threat can include behaviors such as inordinate, long-term job dissatisfaction; attempts to gain access to information not required for job performance; unexplained access to financial resources; bullying or harassment of fellow employees; workplace violence; and other serious violations of policies, procedures, directives, regulations, rules, or practices. Literacy training includes how to communicate the concerns of employees and management regarding potential indicators of insider threat through channels established by the organization and in accordance with established policies and procedures. Organizations may consider tailoring insider threat awareness topics to the role. For example, training for managers may be focused on changes in the behavior of team members, while training for employees may be focused on more general observations.

---

### AU-2(3) — Reviews and Updates  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Incorporated into AU-2.

---

### AU-3(1) — Additional Audit Information

**Control**

Generate audit records containing the following additional information: [assignment: organization-defined additional information].

**Discussion**

The ability to add information generated in audit records is dependent on system functionality to configure the audit record content. Organizations may consider additional information in audit records including, but not limited to, access control or flow control rules invoked and individual identities of group account users. Organizations may also consider limiting additional audit record information to only information that is explicitly needed for audit requirements. This facilitates the use of audit trails and audit logs by not including information in audit records that could potentially be misleading, make it more difficult to locate information of interest, or increase the risk to individuals' privacy.

---

### AU-6(3) — Correlate Audit Record Repositories

**Control**

Analyze and correlate audit records across different repositories to gain organization-wide situational awareness.

**Discussion**

Organization-wide situational awareness includes awareness across all three levels of risk management (i.e., organizational level, mission/business process level, and information system level) and supports cross-organization awareness.

---

### AU-8(1) — Synchronization with Authoritative Time Source  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Moved to SC-45(1).

---

### AU-9(4) — Access by Subset of Privileged Users

**Control**

Authorize access to management of audit logging functionality to only [assignment: organization-defined subset of privileged users or roles].

**Discussion**

Individuals or roles with privileged access to a system and who are also the subject of an audit by that system may affect the reliability of the audit information by inhibiting audit activities or modifying audit records. Requiring privileged access to be further defined between audit-related privileges and other privileges limits the number of users or roles with audit-related privileges.

---

### CM-7(1) — Periodic Review

**Control**

  (a) Review the system [assignment: organization-defined frequency] to identify unnecessary and/or nonsecure functions, ports, protocols, software, and services; and  
  (b) Disable or remove [assignment: organization-defined organization-defined functions, ports, protocols, software, and services within the system deemed to be unnecessary and/or nonsecure].

**Discussion**

Organizations review functions, ports, protocols, and services provided by systems or system components to determine the functions and services that are candidates for elimination. Such reviews are especially important during transition periods from older technologies to newer technologies (e.g., transition from IPv4 to IPv6). These technology transitions may require implementing the older and newer technologies simultaneously during the transition period and returning to minimum essential functions, ports, protocols, and services at the earliest opportunity. Organizations can either decide the relative security of the function, port, protocol, and/or service or base the security decision on the assessment of other entities. Unsecure protocols include Bluetooth, FTP, and peer-to-peer networking.

---

### CM-7(2) — Prevent Program Execution

**Control**

Prevent program execution in accordance with [selection (one-or-more): [assignment: organization-defined policies, rules of behavior, and/or access agreements regarding software program usage and restrictions] ; rules authorizing the terms and conditions of software program usage].

**Discussion**

Prevention of program execution addresses organizational policies, rules of behavior, and/or access agreements that restrict software usage and the terms and conditions imposed by the developer or manufacturer, including software licensing and copyrights. Restrictions include prohibiting auto-execute features, restricting roles allowed to approve program execution, permitting or prohibiting specific software programs, or restricting the number of program instances executed at the same time.

---

### CM-7(4) — Unauthorized Software — Deny-by-exception

**Control**

  (a) Identify [assignment: organization-defined software programs];  
  (b) Employ an allow-all, deny-by-exception policy to prohibit the execution of unauthorized software programs on the system; and  
  (c) Review and update the list of unauthorized software programs [assignment: organization-defined frequency].

**Discussion**

Unauthorized software programs can be limited to specific versions or from a specific source. The concept of prohibiting the execution of unauthorized software may also be applied to user actions, system ports and protocols, IP addresses/ranges, websites, and MAC addresses.

---

### CM-7(5) — Authorized Software — Allow-by-exception

**Control**

  (a) Identify [assignment: organization-defined software programs];  
  (b) Employ a deny-all, permit-by-exception policy to allow the execution of authorized software programs on the system; and  
  (c) Review and update the list of authorized software programs [assignment: organization-defined frequency].

**Discussion**

Authorized software programs can be limited to specific versions or from a specific source. To facilitate a comprehensive authorized software process and increase the strength of protection for attacks that bypass application level authorized software, software programs may be decomposed into and monitored at different levels of detail. These levels include applications, application programming interfaces, application modules, scripts, system processes, system services, kernel functions, registries, drivers, and dynamic link libraries. The concept of permitting the execution of authorized software may also be applied to user actions, system ports and protocols, IP addresses/ranges, websites, and MAC addresses. Organizations consider verifying the integrity of authorized software programs using digital signatures, cryptographic checksums, or hash functions. Verification of authorized software can occur either prior to execution or at system startup. The identification of authorized URLs for websites is addressed in [CA-3(5)] and [SC-7].

---

### CM-8(1) — Updates During Installation and Removal

**Control**

Update the inventory of system components as part of component installations, removals, and system updates.

**Discussion**

Organizations can improve the accuracy, completeness, and consistency of system component inventories if the inventories are updated as part of component installations or removals or during general system updates. If inventories are not updated at these key times, there is a greater likelihood that the information will not be appropriately captured and documented. System updates include hardware, software, and firmware components.

---

### IA-2(1) — Multi-factor Authentication to Privileged Accounts

**Control**

Implement multi-factor authentication for access to privileged accounts.

**Discussion**

Multi-factor authentication requires the use of two or more different factors to achieve authentication. The authentication factors are defined as follows: something you know (e.g., a personal identification number [PIN]), something you have (e.g., a physical authenticator such as a cryptographic private key), or something you are (e.g., a biometric). Multi-factor authentication solutions that feature physical authenticators include hardware authenticators that provide time-based or challenge-response outputs and smart cards such as the U.S. Government Personal Identity Verification (PIV) card or the Department of Defense (DoD) Common Access Card (CAC). In addition to authenticating users at the system level (i.e., at logon), organizations may employ authentication mechanisms at the application level, at their discretion, to provide increased security. Regardless of the type of access (i.e., local, network, remote), privileged accounts are authenticated using multi-factor options appropriate for the level of risk. Organizations can add additional security measures, such as additional or more rigorous authentication mechanisms, for specific types of access.

---

### IA-2(2) — Multi-factor Authentication to Non-privileged Accounts

**Control**

Implement multi-factor authentication for access to non-privileged accounts.

**Discussion**

Multi-factor authentication requires the use of two or more different factors to achieve authentication. The authentication factors are defined as follows: something you know (e.g., a personal identification number [PIN]), something you have (e.g., a physical authenticator such as a cryptographic private key), or something you are (e.g., a biometric). Multi-factor authentication solutions that feature physical authenticators include hardware authenticators that provide time-based or challenge-response outputs and smart cards such as the U.S. Government Personal Identity Verification card or the DoD Common Access Card. In addition to authenticating users at the system level, organizations may also employ authentication mechanisms at the application level, at their discretion, to provide increased information security. Regardless of the type of access (i.e., local, network, remote), non-privileged accounts are authenticated using multi-factor options appropriate for the level of risk. Organizations can provide additional security measures, such as additional or more rigorous authentication mechanisms, for specific types of access.

---

### IA-2(3) — Local Access to Privileged Accounts  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Incorporated into IA-2(1).

---

### IA-2(8) — Access to Accounts — Replay Resistant

**Control**

Implement replay-resistant authentication mechanisms for access to [selection (one-or-more): privileged accounts; non-privileged accounts].

**Discussion**

Authentication processes resist replay attacks if it is impractical to achieve successful authentications by replaying previous authentication messages. Replay-resistant techniques include protocols that use nonces or challenges such as time synchronous or cryptographic authenticators.

---

### IA-2(9) — Network Access to Non-privileged Accounts — Replay Resistant  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Incorporated into IA-2(8).

---

### IA-5(1) — Password-based Authentication

**Control**

For password-based authentication:  
  (a) Maintain a list of commonly-used, expected, or compromised passwords and update the list [assignment: organization-defined frequency] and when organizational passwords are suspected to have been compromised directly or indirectly;  
  (b) Verify, when users create or update passwords, that the passwords are not found on the list of commonly-used, expected, or compromised passwords in IA-5(1)(a);  
  (c) Transmit passwords only over cryptographically-protected channels;  
  (d) Store passwords using an approved salted key derivation function, preferably using a keyed hash;  
  (e) Require immediate selection of a new password upon account recovery;  
  (f) Allow user selection of long passwords and passphrases, including spaces and all printable characters;  
  (g) Employ automated tools to assist the user in selecting strong password authenticators; and  
  (h) Enforce the following composition and complexity rules: [assignment: organization-defined composition and complexity rules].

**Discussion**

Password-based authentication applies to passwords regardless of whether they are used in single-factor or multi-factor authentication. Long passwords or passphrases are preferable over shorter passwords. Enforced composition rules provide marginal security benefits while decreasing usability. However, organizations may choose to establish certain rules for password generation (e.g., minimum character length for long passwords) under certain circumstances and can enforce this requirement in IA-5(1)(h). Account recovery can occur, for example, in situations when a password is forgotten. Cryptographically protected passwords include salted one-way cryptographic hashes of passwords. The list of commonly used, compromised, or expected passwords includes passwords obtained from previous breach corpuses, dictionary words, and repetitive or sequential characters. The list includes context-specific words, such as the name of the service, username, and derivatives thereof.

---

### MA-3(1) — Inspect Tools

**Control**

Inspect the maintenance tools used by maintenance personnel for improper or unauthorized modifications.

**Discussion**

Maintenance tools can be directly brought into a facility by maintenance personnel or downloaded from a vendor’s website. If, upon inspection of the maintenance tools, organizations determine that the tools have been modified in an improper manner or the tools contain malicious code, the incident is handled consistent with organizational policies and procedures for incident handling.

---

### MA-3(2) — Inspect Media

**Control**

Check media containing diagnostic and test programs for malicious code before the media are used in the system.

**Discussion**

If, upon inspection of media containing maintenance, diagnostic, and test programs, organizations determine that the media contains malicious code, the incident is handled consistent with organizational incident handling policies and procedures.

---

### MP-5(4) — Cryptographic Protection  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Incorporated into SC-28(1).

---

### MP-7(1) — Prohibit Use Without Owner  [WITHDRAWN in SP 800-53 Rev 5]

Withdrawn in SP 800-53 Rev 5. Incorporated into MP-7.

---

### RA-5(5) — Privileged Access

**Control**

Implement privileged access authorization to [assignment: organization-defined system components] for [assignment: organization-defined vulnerability scanning activities].

**Discussion**

In certain situations, the nature of the vulnerability scanning may be more intrusive, or the system component that is the subject of the scanning may contain classified or controlled unclassified information, such as personally identifiable information. Privileged access authorization to selected system components facilitates more thorough vulnerability scanning and protects the sensitive nature of such scanning.

---

### SC-7(5) — Deny by Default — Allow by Exception

**Control**

Deny network communications traffic by default and allow network communications traffic by exception [selection (one-or-more): at managed interfaces; for [assignment: organization-defined systems] ].

**Discussion**

Denying by default and allowing by exception applies to inbound and outbound network communications traffic. A deny-all, permit-by-exception network communications traffic policy ensures that only those system connections that are essential and approved are allowed. Deny by default, allow by exception also applies to a system that is connected to an external system.

---

### SC-7(7) — Split Tunneling for Remote Devices

**Control**

Prevent split tunneling for remote devices connecting to organizational systems unless the split tunnel is securely provisioned using [assignment: organization-defined safeguards].

**Discussion**

Split tunneling is the process of allowing a remote user or device to establish a non-remote connection with a system and simultaneously communicate via some other connection to a resource in an external network. This method of network access enables a user to access remote devices and simultaneously, access uncontrolled networks. Split tunneling might be desirable by remote users to communicate with local system resources, such as printers or file servers. However, split tunneling can facilitate unauthorized external connections, making the system vulnerable to attack and to exfiltration of organizational information. Split tunneling can be prevented by disabling configuration settings that allow such capability in remote devices and by preventing those configuration settings from being configurable by users. Prevention can also be achieved by the detection of split tunneling (or of configuration settings that allow split tunneling) in the remote device, and by prohibiting the connection if the remote device is using split tunneling. A virtual private network (VPN) can be used to securely provision a split tunnel. A securely provisioned VPN includes locking connectivity to exclusive, managed, and named environments, or to a specific set of pre-approved addresses, without user control.

---

### SC-8(1) — Cryptographic Protection

**Control**

Implement cryptographic mechanisms to [selection (one-or-more): prevent unauthorized disclosure of information; detect changes to information] during transmission.

**Discussion**

Encryption protects information from unauthorized disclosure and modification during transmission. Cryptographic mechanisms that protect the confidentiality and integrity of information during transmission include TLS and IPSec. Cryptographic mechanisms used to protect information integrity include cryptographic hash functions that have applications in digital signatures, checksums, and message authentication codes.

---

