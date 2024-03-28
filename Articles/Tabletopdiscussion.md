# Table top excersice discussion
Use this document with the provided TabletopReview.tm7 

All items are grouped
**Reviewer question:**
**Designer proposed answer:**

1. **Reviewer question:** What protocols are employed for secure token transmission from Entra Identity to the Contoso status web service?
   **Designer proposed answer:** Transactions use HTTPS. With TLS 1.3 (or latest)  
2. **Reviewer question:** How are logs generated and stored for the 'Get Service Request' data flow from the browser to the Contoso status web service? 
   **Designer proposed answer:** All transactions are logged into log analytics (LA), and collected into Microsoft Sentinel for analysis
3. How is the source code for the Contoso status web service and Contoso WebProcessor secured, and what measures are in place to prevent unauthorized access or modifications?
4. **Reviewer question:** How does the Entra Identity service validate the tenant identity before issuing a token for the user?
**Designer proposed answer:** Service is validated using a valid client registration with the Entra provider. Next using HTTP GET /authorize. Only support OpenID Connect features. Only using well known endpoints can get access the token. Provisioning process is done during deployment and setup of the service. Deprovisioning will ensure all tokens are removed.
5. How is sensitive data protected during transmission between the Contoso status web service and the browser?
6. **Reviewer question:** How does the 'Status Update Database' handle excessive requests from the 'Contoso WebProcessor'? Is there a mechanism to detect and mitigate potential DDoS attacks?
   **Designer proposed answer:** The Microsoft DDOS standard protection is enabled on the VNET
7. How does the Contoso status web service authenticate the Contoso WebProcessor before executing it?
8. How are access logs to the Azure Key Vault managed and monitored?
9.  Are database queries parametrized to prevent SQL injection attacks?
10. What measures are in place to prevent SQL injection or similar attacks on the Status Update Database?
11. How are the secrets managed in Azure Key Vault and how are they accessed by the Contoso WebProcessor?
12. How does the Browser authenticate itself to the Contoso status web service? Is there any form of user authentication involved?
13. How does the Status Update Database validate the token provided by the Contoso WebProcessor before allowing database operations?
14. How are database operations logged and audited, especially in the case of the 'Database put' operation that requires a valid token?
15. Are the databases backed up and do we periodically test to restore them?
16. How does the Contoso status web service validate and sanitize input from the browser to mitigate Injection attacks?
17. How does the Azure Key Vault ensure that tokens used for the processor to access the database are securely stored and transmitted?
18. What DDoS mitigation strategies are in place to protect the 'Contoso status web service' from high volumes of requests from the 'Browser'?
19. Is encryption at rest enabled for the Status Update Database? Who controls those keys?
20. How is the access to the Status Update Database controlled and monitored, especially in the context of the token validation?
21. **Reviewer question:** Are there any auditing mechanisms in place to track the execution and completion of the Contoso WebProcessor?
**Designer proposed answer:** Utilizing Microsoft Sentinel, Microsoft Defender for Cloud, Azure Automanage Machine Configuration, Azure Resource Manager templates, custom operating system images, Azure Automation State Configuration, Change Tracking and Inventory in Azure Automation, and the Guest Attestation agent on virtual machines  ensure that audit information is collected and centralized for security tracking.
Designer proposed answer


