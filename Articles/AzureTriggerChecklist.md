This checklist is a security reviewers list of question to consider when running a review. This list is not exhaustilve, and only addresses Microsoft Azure solutions. Call to the community is to expand it and address more services, and providers.

### List is Alphabetical 

#### API or Endpoint
- Insecure Direct Object Reference (e.g., substitute an identifier in a string, enumeration threat)
- Has it been scanned?
- Has it been fuzzed?  
 
#### Azure Active Directory
- Are passwords being used? 
- Is MFA enabled?
- Single Tenant?, is multitenant is what are the permissions? Has least privlidged been applied?
- All user experiences should be designed around single AAD tenant.
- Privileged role need to be limited. And should be reviewed regularly. 
- Only use approved Certificate Authorities 
- Do not use Self-signed certificates
- Implement Azure Baseline Configuration

#### Azure DevOps
- Are Personal Access Tokens (PAT) being used?
  - If so, recommend using Azure Active Directory
  - If using PAT consider implementing rotation 
https://shopify.engineering/automatically-rotate-github-tokens
 

#### Containers
- How is isolation between different containers ensured?
- What measures are in place to prevent container breakout attacks?
- How are container images verified before use?
- How is access control managed within containers?
- What network security measures are in place for containers?
- Is there an inventory of all systems and devices? 
- Encrypt Data in Transit Using Approved Cryptographic solutions
- Customer data must be encrypted at-rest
- Security update must be continuously validated
- Implement protections against Server Side Request Forgery (SSRF) attacks
 
#### Cryptography
- Can you use TLS everywhere (1.3+)?
- Is your bypher suite is correct?
- Encryption at rest?
- Encryption in transit? 

#### Databases
- What has been implemented to protect data in your stores? 
- Who is granted privlidged access?
- What account are SQL scripts running as SQL Admins?
- WHo can add or delete tables, datasets? 
- Are you using dynamic SQL?
- Do you have any parameterized SQL queries?
- Are certificates being used for database authentication?
- Have least privlidged been applied to all roles? 
- Are all database items enumerated in your inventory? 
- Encrypt Data in Transit Using Approved Cryptographic solutions
- Customer data must be encrypted at-rest
- Implement the SQL Server Baseline Configuration
- Implement security monitoring
- Has static analysis been run to identify security defects?


#### Docker
- Have all images been verified for authenticity and integrity before use?
- What measures are in place to prevent the use of outdated or vulnerable Docker images?
- How is access control managed for Docker containers?
- How is sensitive data handled within Docker containers?

#### Functions App (Serverless)
- are you using restrict IP
- Has there been input validation
- Is least privilege principle applied
- has monitoring of 3rd party dependencies been enabled
- Are cloud storage accounts secured
- Evaluate enforcement of Authentication and Authorization
 

#### Microsoft Key Vault
- Have access policies been established?
- Is RBAC configured properly
- Can your keyvault be accessed via Azure Portal, Azure CLI, Azure PowerShell? if so why? 
- Are you using Zero Trust to isolate access, using a PAW?
- How are you protecting your Key Vault Management REST APIs?
- Are you monitoring all Key Vault activity?
- Secrets must not be present in code, documentation, telemetry or pipelines
- Services should only use KV storage for all credential management
- Certificates must be acquired from approved CAs
- Trusted root CAs must be limited to the minimum required to operate the service
 
 
#### Virtual Machines
- How are the virtual machines isolated from each other?
- What security measures are in place to prevent VM escape vulnerabilities?
- How are patches and updates managed for VM software and guest operating systems?
- How is the host system secured against attacks from compromised VMs?
- What network security measures are in place for VMs?
- Is there an inventory of all systems and devices? 
- All data in VM's encrypted?
- Are security update continuously validated?
- Services such as webserver, database, applications, evaluated (use checklist for each)
- Has all code in VM be fuzz tested


#### Web Services
- What are the valuable assets within your web service?
- Evaluate all likeliest targets for cyberattacks?
- Which system would cause the most significant disruption if compromised?
- Is there flood/DDOS protection in front of web server?
- Are there proxy, or other isolation services set up?
- Implement security monitoring
- Has static analysis been run to identify security defects?
- What network security measures are in place?
- Is there an inventory of all systems and devices?
- What certificatates are in use? All CA's validated?
- Implement the web server (e.g. IIS, Apache) Security Baseline Configuration
- What patching program is in place?
- Perform input validation and/or filtering on traffic
 

 
