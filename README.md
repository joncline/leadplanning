# Lead Planning Salesforce Metadata Package

## Overview

[Lead Management and Human Connection.webm](https://github.com/user-attachments/assets/ca1f9607-7a0f-46a0-8963-64135efce950)



This package provides customizations and automation for Salesforce Lead management, an activity management innovation that emphasizes internal motivation - checking off boxes, crossing off your to-do list, activites like that. Lead management is focused on planning and tracking next steps. It includes custom fields, a flow for automating task creation, a list view, and a permission set for user access.

## Overview Steps

1. Add the Activity Type, Next Step, and Next Step Date to the page layout or lightning record page
2. Open or create a Lead 
3. Fill out the Activity Type, Next Step, and Next Step Date. Set the Next Step Date to a day within this week
4. Open the My Leads Next 7 Days List View
5. Any Leads with a Next Step Date less than or equal to 7 days away will appear
6. Fill out the Completed Step Notes field
7. Click Save
8. Expected Result: The Activity Type, Next Step, and Next Step Date fields are nulled out. 
9. This enables you to write down the next step and prepares you to do this again next week!
10. Set the Next Step Date to more than a week away from today
11. When you save the edits and refresh the list view, the Lead is removed from your To-Do items
12. Congrats! Take a deep breath of satisfaction! You've finished your Lead Activities!


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

## Permissions: Lead Planning Permission Set

- Grants read/edit access to custom Lead fields (except `Next_Step_Days_From_Now__c`, which is read-only).
- Allows create, read, and edit access to the Lead object (no delete).
- Makes the Lead tab visible.

## Deployment Instructions

- **Deploy from GitHub to Salesforce**
Click this link here to bring this metadata into your org!

https://githubsfdeploy.herokuapp.com/app/githubdeploy/joncline/leadplanning

- Users with the "Lead Planning" permission set can view and update the custom Lead fields.
- When a user completes a step and enters notes, a Task is automatically created and the Lead's planning fields are reset for the next cycle.
- The custom list view "My Leads - Next 7 Days" helps users focus on upcoming follow-ups.


## Next Steps:
We help you deliver better Salesforce outcomes—no matter where you're starting from:

- **✅ Done For You** – Let us take the reins and deliver a fully executed solution while you focus on results.
- **✅ Done With You** – Collaborate side by side with our experts to design and build together.
- **✅ Develop Your Team** – Invest in your people with professional development that sharpens their skills and elevates project success.

👉 Contact us today to get the right support for your project and your team—so you can move forward with clarity, speed, and confidence. https://www.linkedin.com/in/joncline/

## Version

- **API Version:** 64.0

## COPYRIGHT:
Copyright 2025 PEOPLE FIRST CRM

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---
