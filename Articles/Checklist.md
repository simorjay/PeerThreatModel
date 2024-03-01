### General Questions:
1. What is the purpose of the Threat Model Review?
    - New Service/Product
    - Updated Service/Product
    - Other

2. If “Updated Service/Product,” provide the threat modeling diagram and notes from the previous review.
    - Answer:

3. If “Other,” provide details. For example, monitoring system identified the last threat model review was a year ago.
    - Answer:

### Identity and Access Management (IAM) Questions:
1. How is the sensitivity of data determined?
    - Consider data classification (public, internal, confidential).
    - Define access control requirements based on data sensitivity.
    - Implement fine-grained access controls to limit exposure.

2. What sensitive data is handled by the application?
    - Identify the types of data processed (e.g., user credentials, personal information).
    - Ensure proper encryption and protection mechanisms.
    - Implement data masking or tokenization where applicable.

3. Where does sensitive data enter and leave the application?
    - Map data flows within the system.
    - Identify entry points (e.g., APIs, user interfaces) and exit points (e.g., data exports).
    - Apply input validation and output encoding to prevent injection attacks.

4. How is sensitive data secured while in transit and at rest?
    - Evaluate encryption mechanisms:
        - In Transit: Use TLS/SSL for secure communication.
        - At Rest: Encrypt data stored in databases or files.
    - Implement robust key management practices.

5. What authentication mechanisms are in place?
    - Consider multifactor authentication (MFA) for stronger user verification.
    - Implement secure password policies and account lockout mechanisms.
    - Explore adaptive authentication based on risk assessment.

### Zero Trust Questions:
1. What is the default trust level for all entities?
    - Assume no inherent trust (Zero Trust principle).
    - Verify trust explicitly based on context and policies.
    - Implement continuous authentication and authorization checks.

2. Have trust boundaries been defined?
    - Identify zones where trust levels change (e.g., internal network, external connections).
    - Apply strict controls at these boundaries (e.g., micro-segmentation).
    - Implement network access controls (NAC) and firewalls.

3. What authentication and authorization mechanisms are used?
    - Evaluate:
        - Authentication: MFA, SSO, OAuth, OpenID Connect.
        - Authorization: Role-based access control (RBAC), attribute-based access control (ABAC).
    - Implement just-in-time (JIT) access provisioning.

4. Is continuous monitoring and validation part of the design?
    - Implement real-time monitoring, anomaly detection, and behavior analysis.
    - Use security information and event management (SIEM) solutions.
    - Regularly review access logs and audit trails.