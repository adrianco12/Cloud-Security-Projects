# Project 5: DLP in Purview

**Created by Adrian Cortez — 07/23/2025**

---

## Overview

The goal of this project is to prevent sensitive information from being shared via email or Teams. This will be done by identifying and labeling sensitive information types, creating DLP policies to monitor or block sharing, and simulating the policy in action. The desired outcome is to demonstrate how effective the policy can be and show risk reduction.

---

## DLP in Purview

Data Loss Prevention (DLP) in Microsoft Purview enables organizations to identify, monitor, and protect sensitive information across Microsoft 365 services. Its main goal is to prevent accidental or intentional data leaks, especially in industries handling personally identifiable information (PII) or intellectual property (IP).

Purview uses built-in patterns (e.g., credit cards, social security numbers) and scans content across Exchange, SharePoint, Teams, and more. Administrators can also classify custom sensitive information such as project names or client IDs. When the DLP policy detects sensitive data, it can block the action, warn the user, or notify administrators or security teams.

This helps organizations comply with regulations such as PCI-DSS, PIPA, and others. DLP policies prevent unauthorized data sharing and provide visibility and reporting to guide employee education.

---

## Planning

### Identify Stakeholders

Effective DLP implementation requires identifying stakeholders who understand:

- Applicable regulations and laws  
- Categories of sensitive items to protect  
- Business processes involving these items  
- Risky behaviors to limit  
- Data prioritization for protection  

Stakeholders may include regulatory/compliance officers, business data owners, legal teams, and more.

### Describe Categories of Sensitive Information to Protect

Stakeholders define categories of sensitive information that require protection.

### Set Goals and Strategies

The IT team maps out the starting state and desired state for DLP implementation, planning phased adoption and enforcement.

---

## Configure DLP Policies in Microsoft Purview: Detailed Process

### Step 1: Access the Purview Compliance Portal

- Log into [Microsoft Purview compliance portal](https://compliance.microsoft.com)  
- Navigate to **Data loss prevention** under **Solutions**

### Step 2: Define the Sensitive Information to Protect

Utilize built-in sensitive information types such as:

- **Personally Identifiable Information (PII):** SSNs, Passport numbers, Driver’s Licenses, National IDs  
- **Financial Information:** Credit card numbers, Bank account numbers, SWIFT codes, IBANs  
- **Health Information:** PHI such as medical record numbers, health insurance IDs  
- **Intellectual Property:** Custom keywords or patterns (e.g., proprietary formulas, designs)  

Create custom sensitive information types as needed using keywords, regex, or dictionary lists.

### Step 3: Create a New DLP Policy

- Click **Create policy**  
- Choose a template (e.g., Financial Data, Privacy, HIPAA) or start from scratch  
- Name the policy clearly (e.g., “Financial Data Protection Policy”)

### Step 4: Choose Locations to Apply the Policy

Select where the policy applies:

- Exchange email  
- SharePoint sites and OneDrive accounts  
- Microsoft Teams chat and channel messages  
- Optionally endpoints or third-party cloud apps via Defender for Cloud Apps

### Step 5: Define Policy Rules and Conditions

Configure rules specifying:

- Sensitive information types to detect (e.g., 1+ credit card numbers or 3+ SSNs)  
- Conditions like sharing outside the organization or to specific recipients  
- Thresholds and confidence levels to minimize false positives

### Step 6: Set Actions and User Notifications

Define actions when rules match:

- **Block content:** prevent sending or sharing  
- **Restrict access:** encrypt or limit permissions  
- **Notify users:** show policy tips with guidance  
- **Send incident reports:** alert compliance or security teams  

Configure user override options where appropriate.

### Step 7: Configure Policy Mode and Testing

- Start in **Test mode (Policy Tips only)** to monitor impact without blocking  
- Review alerts and tune policies to reduce false positives  
- Move to **Enforce mode** when ready

### Step 8: Review and Publish the Policy

- Verify settings  
- Publish to activate

### Step 9: Monitor and Adjust

- Regularly review DLP reports and alerts  
- Refine policies and educate users

---

## Conclusion

Implementing DLP through Microsoft Purview with this structured approach is essential to systematically protect an organization’s sensitive data from accidental or intentional exposure. By clearly defining protected information, setting strategic goals aligned with compliance, and carefully configuring and testing policies, the organization reduces data breach risks and regulatory penalties. This process balances security with productivity, fostering a culture of data responsibility. Ultimately, effective DLP implementation preserves trust, compliance, and competitive advantage.

---
