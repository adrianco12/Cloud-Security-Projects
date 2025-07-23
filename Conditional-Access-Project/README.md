Conditional Access (CA) Policies 
  Conditional Access Policies in Azure are a security feature in Azure Active Directory (or Microsoft Entra ID) that helps you enforce rules that determine who can access what and under what circumstances. 
  It operates similarly to “if-then” statements in programming. For example: If the user signs in under specific conditions, then enforce a policy (like MFA, blocking access, or allowing access only from compliant devices).
  The “IF” part of the statement would be the user or group (ex: admins or HR team), the application being accessed (ex: SharePoint, Teams), the location, the device platform (IOS, Android, Windows), the client app, and more. 
  The “THEN” part of the statement would grant controls (Ex: require MFA), block access, or enforce session controls (Ex: limit session length, enforce read-only access, etc). 
  Here is an example of a policy in terms of a conditional statement: IF a user tries to access Microsoft 365 from an unmanaged device, THEN require MFA and only allows web access. 

Preparing a CA Policy
  When creating a conditional access policy, it’s important to consider the following: 
    - When testing policies, report-only mode should be used. 
    - Exclude one break-glass account from all CA policies in the event of an emergency. 
    - Review sign-in logs to monitor impact 
    - Use “What if” tool to simulate policy effects. 

  Key Tools Used to Design Conditional Access Policies:  
    To determine what rules to implement, Microsoft provides key Azure tools that can be used to create and configure CA Policies.
    The following were used to justify why certain policies should be implemented:     
    - Sign-in Logs (Microsoft Entra ID)   
      - Looking at sign-in logs helps to identify risky sign-ins, legacy and authentication use, and unprotected logins.   
      - You can look for users logging in without MFA, logins from unexpected countries/IPs, legacy protocols (POP, IMAP, SMTP), sign-ins from unmanaged devices, etc.   
      - This would justify policies such as ‘Require MFA’ or ‘Block legacy auth’.   
      - In my review of logs, I noticed that there were attempts to sign in from China and Russia.  
    - Conditional Access Insights Workbook   
      - This tool helps visualize which CA policies are applied (or not), and their impact. This helps with determining how the policy is being used, which users and apps are affected, gaps in coverage, and how effective the policy is.   
      - I reviewed exisisting CA policies and evaluated their effectiveness.  
    - Microsoft Secure Score   
      - This tool allows you to assess your overall Microsoft 365/Azure AD security posture and get recommended actions.      
      - The secure score I recieved was at 54%. I reviewed the recommendations and used them to evaluate the next steps in creating a CA Policy.  
        - For example, a key reccommendation was to Enable Conditional Access policies to block legacy authentication. This would increase my score by 12%. It also gave a justification for it: "Today, most compromising sign-in attempts come from legacy authentication."  
    - Identity Protection (Premium P2)   
      - Detects risky users and sign-ins using machine learning.   
      - Using this tool, I identified risky users and why they may be at risk.  
      - Furthermore, I reviewed risky sign-ins, and determine that location and legacy authentication were putting sign-ins at a big risk.  
    - Access Reviews   
      - Review who has access to apps, roles, or groups—and determine if Conditional Access should apply more narrowly. This helps create more target CA rules.    
    - Microsoft’s Conditional Access Recommendations   
      - Microsoft provides baseline and advanced recommendations based on their research and feedback. For example, they recommend MFA for all users, blocking legacy authentication, requiring compliant devices for admins, and more.   
    - NIST Cybersecurity Framework (NIST CSF)   
      - NIST is widely adopted globally for setting security controls. Some relevant controls include PR.AC-1 to PR.AC-7 (IAM), DE.CM-7, PR.AC-4.   
    - CIS Microsoft 365 Benchmarks   
      - CIS provides hardening guides for Microsoft 365 and Azure.  
      - CIS Control 4.4 recommends to restrict access based on geolocation.  
    - Zero Trust Architecture Principles    
      - Verify explicitly, use least privilege access, assume breach   

Based on my findings, these are the CA Policies that I should implement:
  - Location-based sign in access
  - Block Basic/Legacy Authentication 
  - Block High-Risk Users

Creating CA Policies
  In a real world application, I would present my findings to the team or the executive board, and we would determine if they should be implemented. Here are the steps to implement these policies:
  1. Location-Based Sign-In Access
    Created a new Conditional Access policy in Microsoft Entra.
    Targeted specific users and included all cloud apps.
    Under Conditions, enabled Locations and selected a named location group (e.g., Trusted IPs or countries).
    Configured the policy to block access if sign-ins originated outside trusted locations.
    Enabled the policy after verifying impact using report-only mode.
2. Block Basic/Legacy Authentication
  Created a CA policy to prevent use of outdated protocols like POP, IMAP, SMTP, and older Office clients.
  Assigned the policy to all users and applied it to all cloud apps.
  In Client Apps condition, selected "Other clients" to target legacy authentication.
  Set the grant control to block access, effectively disabling basic auth sign-ins.
  Validated impact by reviewing sign-in logs for legacy protocols before enabling.
3. Block High-Risk Users
  Configured a CA policy to respond to high-risk user activity using Microsoft Entra ID Protection.
  Targeted all users and applied the policy to all cloud apps.
  In the User Risk condition, selected "High" risk level.
  Set access control to block access immediately for users detected as high risk.
  Enabled the policy to automatically protect the tenant from compromised accounts.

Conclusion:  
Implementing Conditional Access policies significantly enhanced the security posture of the cloud environment by enforcing identity-based controls. 
By targeting key risk areas—such as blocking legacy authentication, restricting access based on location, and mitigating high-risk user sign-ins—I was able to demonstrate a proactive, policy-driven approach to access management. 
These policies align with best practices from Microsoft and CIS Benchmarks, and showcase how Conditional Access can effectively reduce the attack surface while maintaining user productivity. 
This project reflects my ability to apply real-world security principles using Microsoft Entra tools and contributes to a more secure and resilient cloud infrastructure.
