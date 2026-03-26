# Group Policy Password Configuration & Verification Lab

## Objective
Configure domain password policies through Group Policy Management (GPO) and verify that the policy applies successfully to domain users in an enterprise environment.

---

## Lab Environment
- Windows Server 2019 Virtual Machine
- Windows 11 Pro Virtual Machine
- Group Policy Management (GPO)

---

## Step-by-Step Configuration

---

### 1. Start Windows Server and Open Group Policy Management
Opened Windows Server 2019 virtual machine, navigated through tools and opened Group Policy Management. 

![Screenshot 1](1-windows-server.png)

![Screenshot 2](2-gpo.png)

---

### 2. Locate the Default Domain Policy
In GPO, navigated through Forest → Domain → Default Domain Policy where all policies are located for users and computers.

![Screenshot 3](3-default-domain-policy.png)

---

### 3. Configure the Password Policy
Right clicked on "Default Domain Policy" and navigated through Edit → Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Password Policy to configure the password policies. 

**Configuration:**

![Screenshot 4](4-password-policy-update.png)

Password History: prevents reuse of previous passwords
Maximum Password Age: forces password changes every (#) days
Minimum Password Age: prevents immediate password changes to bypass history
Minimum Password Length: requires longer passwords for stronger security
Minimum Password Length Audit: not enforcing a minimum password length
Password Must Meet Complexity Requirements: requires a mix of character types to block simple passwords
Store Passwords Using Reversible Encryption: ensures passwords are securely hashed and not reversible

---

### 4. Configure Account Lockout Policy
Opened "Account Lockout Policy" and configured policies. 

**Configuration:**

![Screenshot 5](5-account-lockout-policy.png)

Account Lockout Duration: amount of time the account remains locked before automatically unlocks 
Account Lockout Threshold: number of failed logon attempts allowed before account is locked
Allow Administrator Account Lockout: determines if built-in Administrator account can be locked after failed logon attempts
Reset Account Lockout Counter After: time after failed logon attempts are reset to zero

---

### 5. Apply the Policy
Logged on to a domain user account client machine and entered `gpupdate /force` on the Command Prompt to update the password and account lockout policy newly configured. 

**Command Used**
```
gpupdate /force
```

![Screenshot 6](6-gpupdate-force.png)

---

### 6. Verify Newly Configured Policy with Password Test
Attempted to change password of domain user to a short password and received error message indicating updated password policy configuration was updated. Secondly, attempted to change password following the update password policy of complexity and minimum password length 

