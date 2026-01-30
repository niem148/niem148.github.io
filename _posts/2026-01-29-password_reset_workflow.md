---
title: "Helpdesk Scenario: Password Reset Workflow"
date: 2026-01-28 09:42:05 +0000
categories: [Helpdesk, Troubleshooting]
tags: [Active Directory, User Support, Security]
image: /assets/media/password_reset/password_change.png   
---

<div class="skills-box">
  <strong>Skills:</strong>
  <ul>
    <li>confirming user identity before making account changes</li>
    <li>resetting passwords and checking account status</li>
    <li>enforcing password policies and safe reset procedures</li>
    <li>guiding users through login steps calmly and simply</li>
    <li>recording actions, findings and resolution details</li>
  </ul>
</div>

---

## Overview
A realistic helpdesk-style walkthrough of how I would handle a password reset request from an end user, including verification, security considerations, and Active Directory steps.

## Step 1 — Verify the User's Identity
- Ask for full name, department, manager
- Confirm via ticketing system or HR directory
- Never reset a password without verification

## Step 2 — Check the Account Status in AD

![Commands](/assets/media/password_reset/Screenshot 2026-01-30 104654.png) 

Things to check:
- Account locked?
- Password expired?
- User disabled?

## Step 3 — Reset the Password
- Use “Reset Password” in ADUC
- Force password change at next logon
- Unlock account if needed
- Document the temporary password
  
![Commands](/assets/media/password_reset/Screenshot 2026-01-30 104314.png) 

- Or if user rememebers password they can change it without the reset password
![Commands](/assets/media/password_reset/Screenshot 2026-01-29 184420.png) 

## Step 4 — Communicate Clearly With the User
- Explain the next steps
- Remind them about password policy
- Offer to stay on the line while they log in

## Step 5 — Document the Ticket
Include:
- What the user reported
- What you found
- What you did
- Confirmation that the issue is resolved

## Conclusion
This workflow demonstrates user verification, AD troubleshooting, communication and documentation.
