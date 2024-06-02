# Table top excersice discussion
Use this document with the provided TabletopReview.tm7 to conduct a table top review. All questions are grouped with a **Reviewer question**
 and a **Designer proposed answer**. The 16 questions are provided as seed discussion and starting point for a review.

1. **Reviewer question:** What protocols are employed for secure token transmission from Entra Identity to the Contoso status web service?
   **Designer proposed answer:** Transactions use HTTPS. With TLS 1.3 (or latest)  

2. **Reviewer question:** How are logs generated and stored for the 'Get Service Request' data flow from the browser to the Contoso status web service? 
   **Designer proposed answer:** All transactions are logged into log analytics (LA), and collected into Microsoft Sentinel for analysis  

3. **Reviewer question:** How does the Entra Identity service validate the tenant identity before issuing a token for the user?
**Designer proposed answer:** Service is validated using a valid client registration with the Entra provider. Next using HTTP GET /authorize. Only support OpenID Connect features. Only using well known endpoints can get access the token. Provisioning process is done during deployment and setup of the service. Deprovisioning will ensure all tokens are removed.  

4. **Reviewer question:** How does the 'Status Update Database' handle excessive requests from the 'Contoso WebProcessor'? Is there a mechanism to detect and mitigate potential DDoS attacks?
   **Designer proposed answer:** The Microsoft DDOS standard protection is enabled on the VNET  

5. **Reviewer question:** How does the Contoso status web service authenticate the Contoso WebProcessor before executing it?
   **Designer proposed answer:** Authentication should be done using approved methods such as Azure Active Directory, certificates, or API keys.   

6. **Reviewer question:** How are access logs to the Azure Key Vault managed and monitored?
   **Designer proposed answer:** Access logs to Azure Key Vault should be enabled and configured for monitoring. These logs should be ingested into a SIEM tool like Microsoft Sentinel for proper monitoring and handling of security incidents.  

7. **Reviewer question:** Are database queries parametrized to prevent SQL injection attacks?
   **Designer proposed answer:** The recommended way to prevent SQL injection attacks is to use parameterized queries or stored procedures. This ensures that user input is always treated as literal data and not part of the SQL command.   

8.  **Reviewer question:**  What measures are in place to prevent SQL injection or similar attacks on the Status Update Database?
    **Designer proposed answer:** The recommended way to prevent SQL injection is to use parameterized queries or stored procedures instead of building dynamic queries with untrusted data using string concatenation. Additionally, all user input should be validated using strong type checking where possible to eliminate harmful input.   

9. **Reviewer question:** How are the secrets managed in Azure Key Vault and how are they accessed by the Contoso WebProcessor?
    **Designer proposed answer:**  The recommended way is that secrets are not embedded into the code or configuration files, and how often are these secrets rotated and purged when no longer in use  

10. **Reviewer question:**  How does the Browser authenticate itself to the Contoso status web service? Is there any form of user authentication involved?
    **Designer proposed answer:** The recommended way is to use passwordless methods or multi-factor authentication (MFA) as default. If password-based authentication is still in use, ensure password security best practices are followed.  

11. **Reviewer question:** How does the Status Update Database validate the token provided by the Contoso WebProcessor before allowing database operations?
**Designer proposed answer:** The recommended way is to use Azure AD for identity management and token validation. Azure AD provides built-in features for managing the identity and access lifecycle, including token validation.   

12.  **Reviewer question:** How are database operations logged and audited, especially in the case of the 'Database put' operation that requires a valid token?
**Designer proposed answer:** The recommended way is to enable and configure audit logging capabilities in your environments. These logs should be monitored and ingested into a SIEM tool like Microsoft Sentinel for proper handling of security incidents.   

13. **Reviewer question:**  How does the Contoso status web service validate and sanitize input from the browser to mitigate Injection attacks?
**Designer proposed answer:**
Recommendation is that you should validate data type, length, and other criteria. For instance, in PHP, you can validate input using functions like is_numeric() or custom validation logic.


|---|---|
|   |Input Sanitization:|
|   |- Escaping Special Characters: Use libraries or functions to escape characters like <, >, and &. This prevents HTML injection attacks.|
|   |- Removing HTML Tags: Sanitize user input to prevent cross-site scripting (XSS) attacks. For example, use a library like Validator.js to strip HTML tags from input.|
|   |- Parameterized Queries: When interacting with databases, use parameterized queries or prepared statements. These prevent SQL injection by separating user input from SQL commands. Encoding User Input: Encode user input before displaying it. For instance, convert special characters to their HTML entities |

14.   **Reviewer question:** How does the Azure Key Vault ensure that tokens used for the processor to access the database are securely stored and transmitted?
    **Designer proposed answer:** Specify which IP addresses have access to your Key Vaults. You can use virtual network service endpoints to limit access to a specified virtual network or a list of IPv4 address ranges. This ensures that only authorized sources can connect to your Key Vault.
-  Consider using Azure Private Link to access Azure Key Vault securely within your virtual network. It allows you to connect privately and directly to the service without exposing it to the public Internet. No gateways, NAT devices, or public IP addresses are needed.  
-  Consider using the Azure Key Vault Premium tier, that includes hardware security modules (HSMs) for added protection.    

15.  **Reviewer question:** What DDoS mitigation strategies are in place to protect the 'Contoso status web service' from high volumes of requests from the 'Browser'?
**Designer proposed answer:** It's recommended that you wnable Azure DDoS Network Protection. This automatically defends the Azure resources within the enviroment against DDoS attacks.  

16.   **Reviewer question:** Are there any auditing mechanisms in place to track the execution and completion of the Contoso WebProcessor?
**Designer proposed answer:** Utilizing Microsoft Sentinel, Microsoft Defender for Cloud, Azure Automanage Machine Configuration, Azure Resource Manager templates, custom operating system images, Azure Automation State Configuration, Change Tracking and Inventory in Azure Automation, and the Guest Attestation agent on virtual machines  ensure that audit information is collected and centralized for security tracking.



