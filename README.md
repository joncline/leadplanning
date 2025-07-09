# leadplanning

# Lead Planning Salesforce Metadata Package

## Overview

[Lead Management Process Overview.webm](https://github.com/user-attachments/assets/999cbebf-fcc1-44bf-90a6-233bea986659)


This package provides customizations and automation for Salesforce Lead management, an activity management innovation that emphasizes internal motivation - checking off boxes, crossing off your to-do list, activites like that. Lead management is focused on planning and tracking next steps. It includes custom fields, a flow for automating task creation, a list view, and a permission set for user access.

## Contents

- **objects/Lead.object**  
  Customizations to the Lead object, including custom fields for activity tracking, action overrides, and list/search layouts.

- **flows/Lead_On_Update_Lead_Planning.flow**  
  An auto-launched flow that automates the creation of Task records and manages Lead fields when certain updates occur.

- **permissionsets/Lead_Planning.permissionset**  
  A permission set granting access to the custom Lead fields and object-level permissions.

- **package.xml**  
  Salesforce package manifest for deployment.

## Custom Fields on Lead

- **Activity_Type__c** (Picklist):  
  Tracks the type of activity (Call, Meeting, Email, Text, Drop-In, Other).

- **Completed_Step_Notes__c** (TextArea):  
  Notes about the completed step.

- **Next_Step_Date__c** (Date):  
  The date for the next planned step.

- **Next_Step_Days_From_Now__c** (Number, Formula):  
  Calculates the number of days from today to the next step date.

- **Next_Step__c** (Text):  
  Description of the next step.

## Automation: Lead_On_Update_Lead_Planning Flow

- **Trigger:**  
  Runs after a Lead record is updated, specifically when `Completed_Step_Notes__c` is not null and has changed.

- **Logic:**  
  - Creates a Task record with details from the Lead (description, status, subject, whoId, activity date).
  - After creating the Task, it nulls out the Lead's activity fields (`Activity_Type__c`, `Completed_Step_Notes__c`, `Next_Step_Date__c`, `Next_Step__c`).

- **Purpose:**  
  Ensures that completed steps are logged as Tasks and that the Lead is ready for the next planning cycle.

## Permissions: Lead_Planning Permission Set

- Grants read/edit access to custom Lead fields (except `Next_Step_Days_From_Now__c`, which is read-only).
- Allows create, read, and edit access to the Lead object (no delete).
- Makes the Lead tab visible.

## Deployment Instructions

1. **Retrieve or deploy using Salesforce CLI:**
   ```sh
   sfdx force:mdapi:deploy -d . -u <target-org>
   ```
   Or use Workbench/Change Sets as appropriate.
 

- Users with the "Lead Planning" permission set can view and update the custom Lead fields.
- When a user completes a step and enters notes, a Task is automatically created and the Lead's planning fields are reset for the next cycle.
- The custom list view "My Leads - Next 7 Days" helps users focus on upcoming follow-ups.


Next Steps:
If you like what you see here and want further assistance building it - or solutions like it - we have three offers:
✅ Done For You – Let us handle the heavy lifting while you focus on results.
✅ Done With You – Partner with our experts to co-create the solution together.
✅ Project Recovery – If things have gone off track, we specialize in turning projects around—fast.

👉 Contact us today to get started and move your project forward with clarity, confidence, and speed.

## Version

- **API Version:** 64.0

Copyright 2025 PEOPLE FIRST CRM

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---
