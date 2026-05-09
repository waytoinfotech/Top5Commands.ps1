# Top5Commands.ps1

# M365 PowerShell Essentials - Top 5 Commands 🚀

यह रिपॉजिटरी मेरे यूट्यूब वीडियो **"Top 5 PowerShell Commands every M365 Admin should know"** का हिस्सा है। यहाँ उन सभी कमांड्स की लिस्ट और उनके इस्तेमाल का तरीका दिया गया है जो मैंने वीडियो में दिखाए हैं।

## 📺 वीडियो लिंक


---

## 🛠️ Commands Covered

### 1. Connect to Exchange Online (V3 Module)
सबसे पहले मॉडर्न ऑथेंटिकेशन (MFA) के साथ कनेक्ट करने के लिए:

```powershell
Connect-ExchangeOnline -UserPrincipalName <YourAdminEmail@domain.com>

----------------------
2. Check Mailbox Storage (Top Consumers)
पूरी ऑर्गेनाइजेशन में कौन सा यूजर सबसे ज्यादा स्पेस ले रहा है, यह जानने के लिए:

Get-EXOMailbox -ResultSize Unlimited | Get-EXOMailboxStatistics | Select-Object DisplayName, TotalItemSize | Sort-Object TotalItemSize -Descending

-----------------------
3. Enable Mailbox Auditing
सिक्योरिटी और ट्रैकिंग के लिए किसी स्पेसिफिक यूजर की ऑडिटिंग ऑन करने के लिए:
PowerShell
Set-Mailbox -Identity "User@domain.com" -AuditEnabled $true

-----------------------
4. Test Migration Endpoint (Hybrid Environments)
हाइब्रिड माइग्रेशन शुरू करने से पहले कनेक्शन चेक करने के लिए:

PowerShell
Test-MigrationServerAvailability -ExchangeRemoteMove -RemoteServer <Your-FQDN> -Credentials (Get-Credential)

-----------------------
5. Audit Inbox Rules (Security Check)
किसी भी संदिग्ध (Suspicious) फॉरवर्डिंग रूल को चेक करने के लिए:

PowerShell
Get-InboxRule -Mailbox "User@domain.com" | Select-Object Name, Enabled, RedirectTo, ForwardTo

========================
Prerequisites
Windows PowerShell 5.1 या PowerShell 7+

Exchange Online Management Module (V3)

इनस्टॉल करने के लिए: Install-Module -Name ExchangeOnlineManagement

