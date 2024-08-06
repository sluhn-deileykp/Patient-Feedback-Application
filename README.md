
# Patient Feedback Developer Guide

|     |     |
| --- | --- |
| Author | Kane.Deiley@sluhn.org |
| Last Modified | 8/6/2024 |
| Lead Developer | Kane.Deiley@sluhn.org |
| DEV Dept. | IT Solutioning |
| Operational Dept. | Clinical Risk Management |
| Super Users | [FeedbackSuperAdmins](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Overview/groupId/1009d108-fa1b-46f3-92ae-7056f17838b2/menuId/) |
| Teams Channel | [Patient Feedback System](https://teams.microsoft.com/l/team/19%3AXUYU6Wg6kRH69YvJ7mZ51ANBeRKUqZIyWjY75ujGiUc1%40thread.tacv2/conversations?groupId=ac0774cb-b640-43db-9aed-6c2e6bf99789&tenantId=ef4fd2f8-4c96-45ab-9b15-7831920f55cf) |

## Overall Description:

The Patient Feedback System consists of a network-wide form accessible to all internal users and an admin application for managing and analyzing the collected data. Patients can use the form to provide feedback on various aspects of their care, such as provider interactions, wait times, and overall satisfaction. The admin application allows staff to centralize feedback, generate reports, identify trends, and assign feedback for action. The system is designed to be scalable, secure, and user-friendly, with a focus on data privacy and accessibility. By leveraging technology, the system aims to provide valuable insights into patient experiences, enabling St. Luke's to make data-driven improvements in care delivery.

## Workflow:

1. Feedback Tracking Form Submitted Location informs Manager for next step


2. Manager Notfied & Handles via Admin App Handles Log via Canvas App & Closes informing reviewer for next step


3. Reviewer Notfied & Handles via Admin App Reviews log & verifies it's validity w/ Canvas App

## Technology:

### Feedback Tracking Form:

|     |     |
| --- | --- |
| Platform | Power Platform |
| Interface | Canvas App |
| Users | All Internal Users |
| Solution | [Feedback Tracking Form](https://make.powerapps.com/environments/Default-ef4fd2f8-4c96-45ab-9b15-7831920f55cf/solutions/487c573a-5d7e-ee11-8179-002248208775) |
| Canvas App | [Feedback Tracking Form](https://apps.powerapps.com/play/e/default-ef4fd2f8-4c96-45ab-9b15-7831920f55cf/a/cda9998d-c7f4-4cdf-bfff-1db468d55381?tenantId=ef4fd2f8-4c96-45ab-9b15-7831920f55cf&hint=c9787dae-7da2-4b9f-9ff9-29737c091bd6&sourcetime=1722876171637) |
| Environment | [Personal PROD](https://make.powerapps.com/environments/Default-ef4fd2f8-4c96-45ab-9b15-7831920f55cf/home) |
| Database | [Sharepoint](https://sluhn.sharepoint.com/sites/ITSolutioning) |
| Form Submission Database | [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) |
| Location Database | [Feedback Location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) |

#### Description:

Enables all users in the network to submit a Feedback Form modeled off a PDF created by Clinical Risk Management to handle Patient Feedback. The form has a location picker, utilizing the dynamic Location Database to attach it's self as a lookup record to the Form Submission database. The location informs the users assigned to the record as well as who is notified upon the form's submission.

#### Functionality:

Canvas App enables form submission creating a record within the Form Submission Database, containing preliminary info regarding the Patient Feedback & a child record from the location database. Records are not visible to users after submission.

#### Roles:

All Internal Users:

|     |     |     |
| --- | --- | --- |
| Table | Rights | Description |
| [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) | Add Items & View Items ('Organizational' Permission Level) | Allows all internal users to submit Patient Feedback |
| [Feedback location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) | View Items ('Viewership' Permission Level) | Allows all internal users to view Patient Feedback Location data |

### Patient Feedback Application:

|     |     |
| --- | --- |
| Platform | Power Platform |
| Interface | Canvas App |
| Users | [Azure\_PP\_App\_PATIENTFEEDBACK\_Prod\_uGrp](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Members/groupId/fbaad8fd-41dd-4f53-8908-c3677db6d2e5/menuId/) |
| Roles | [Manager](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Overview/groupId/3fa37acc-3fa4-41ae-a26a-fff12f7f93e9/menuId/)  <br>[Reviewer](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Overview/groupId/58f4ffc0-93a7-41b9-b81a-2800e102eada/menuId/)  <br>[LocationAdmin](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Overview/groupId/2bc17ccf-8db9-4815-bfdf-5ef68d1ac370/menuId/)  <br>[SuperUser](https://portal.azure.com/#view/Microsoft_AAD_IAM/GroupDetailsMenuBlade/~/Overview/groupId/1009d108-fa1b-46f3-92ae-7056f17838b2/menuId/) |
| Solution | [Sharepoint Online - Feedback Application](https://make.powerapps.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b) |
| Canvas App | [Patient Feedback Application](https://apps.powerapps.com/play/e/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/a/f71b35df-2e12-4e6b-a4a3-8bb72ada9315?tenantId=ef4fd2f8-4c96-45ab-9b15-7831920f55cf&hint=a0f2b6aa-9c1a-4d55-a183-401089c0e9f5&sourcetime=1722879793897) |
| Environment | [SLUHN\_PowerPlatformDEV](sluhnpowerdev.crm.dynamics.com<br>            )  <br>[SLUHN\_PowerPlatform](sluhnpower.crm.dynamics.com) |
| Database | [Sharepoint](https://sluhn.sharepoint.com/sites/ITSolutioning) |
| Form Submission Database | [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) |
| Location Database | [Feedback Location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) |
| Document Database | [Feedback Letter List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Letter%20List/AllItems.aspx) |

#### Description:

An administrative Application to allow for Individuals who participate in Clinical Risk Management to handle Patient Feedback in an electronic and standardized fashion. The application provides a large user group the ability to modify each submission, but users are split into roles which have defining features. Every location in the location Database has three role columns which defines how a user in the system - interacts / Receives notifications / views reports. Each submission that comes in retains a location, this then informs which users are assigned at what role for each individual submission. If a submission comes in with no location it is assigned to super users. Roles and Functionality include  
  

#### Roles:

Manager - Receives Notification when the Form is Submitted. Handles submission until is closed. Sends a follow-up letter, makes sure there are steps recorded and in place to resolve the issue. Can share the submission with other individuals, as well as reassign it to a new location. Can archive the log if it is deemed invalid in some manner. Has location specific reporting.  

|     |     |     |
| --- | --- | --- |
| Table | Rights | Description |
| [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Managers users to submit & manage Patient Feedback |
| [Feedback location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) | View Items ('Viewership' Permission Level) | Allows all Managers to view Patient Feedback Location data |
| [Feedback Letter List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Letter%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Managers to add leters & edit to the Patient Feedback System |

  
Reviewer - Receives Notification when the Submission is Closed. Verifies the submission has been handled appropriately and marks the log as Reviewed. Can Request the submission to be re-opened, routing it back to the location assigned managers. Can archive submissions. Can modify locations they are assigned and change roles within them via edit of the location database. Has location specific reporting.  

|     |     |     |
| --- | --- | --- |
| Table | Rights | Description |
| [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Reviewers to submit & manage Patient Feedback |
| [Feedback location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) | Edit & View Items ('Administrative' Permission Level) | Allows all Reviewers to Edit & View Patient Feedback Location data |
| [Feedback Letter List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Letter%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Reviewers to add leters & edit to the Patient Feedback System |

  
Location Admin \- Assumes the same functions as the Manager, but is notified less, as there is typically less involvement of this individual. Has location specific reporting. Has 'Keep with Me' Functionality (to be discussed later in the doc).  

|     |     |     |
| --- | --- | --- |
| Table | Rights | Description |
| [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Location Admins users to submit & manage Patient Feedback |
| [Feedback location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) | View Items ('Viewership' Permission Level) | Allows all Location Admins to view Patient Feedback Location data |
| [Feedback Letter List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Letter%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Location Admins to add letters & edit to the Patient Feedback System |

  
Super User \- Assumes every role for Submissions that are NOT assigned a location. Can view every log in the system at anytime. Can change any location within the system. Has Global Reporting Rights. Has 'Keep with Me' Functionality (to be discussed later in the doc).  

|     |     |     |
| --- | --- | --- |
| Table | Rights | Description |
| [Grievance List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Grievance%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Super Users to submit & manage Patient Feedback |
| [Feedback location](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Location/AllItems.aspx) | Edit & View Items ('Administrative' Permission Level) | Allows all Super Users to Edit & View Patient Feedback Location data |
| [Feedback Letter List](https://sluhn.sharepoint.com/sites/ITSolutioning/Lists/Feedback%20Letter%20List/AllItems.aspx) | Allows Users to Add, Edit, Delete & View Items ('Administrative' Permission Level) | Allows all Super Users to add letters & edit to the Patient Feedback System |

#### Functionality:

##### Initial Assignment

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Manager Notification | Feedback Tracking Form | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/5d51c121-ca0b-4041-b4e0-8d34beb5d12c/details?utm_source=solution_explorer) | Takes in Submission ID, triggered on record creation via Feedback Tracking Form. With ID it grabs assigned users and notifies the submission is now visible in their queue via Patient Feedback App |

##### Sharing

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Share Trigger | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/f1eb1228-f9d3-4803-8a76-0b4a75a4a3e1/details?utm_source=solution_explorer) | Takes in Submission ID and User Claims. Appends user claims to submission's shared field via ID, notifies selected users of share. Provides visibility to said users in Patient Feedback App. |

##### Closing

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Confirmation Flow | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/b5196d33-fd66-4045-afa0-9bdbd69da8e1/details?utm_source=solution_explorer) | Takes in Submission ID, and marks the selected submission as closed. Via Location assignment it notifies the proper reviewer to finalize the submission |

##### PDF Export

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| PDF Flow | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/ad1ad019-384e-475a-90b6-9f52b021a28f/details?utm_source=solution_explorer) | Takes in Submission ID, and converts database record to an html table. This html content is then ported to a pdf and emailed to the user who submitted the request |

##### Reassignment

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Reassignment Flow | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/flows/4f471371-3c99-4e5e-aab0-d8cccdc9de44/details) | Takes in Submission ID, and changes the locations lookup record to the newly selected location. It uses the submission ID to then find the new managers and notifies them that a look has been reassigned as a part of their queue. |

##### Letter Approval

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Approvals Letter Flow | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/401319ad-f30f-4b05-b59e-fd5c357605b8/details?utm_source=solution_explorer) | Takes in Letter ID from Document Database and creates an Approvals request with the attached word document & the chosen approvers. |

##### Late Submissions

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Late Feedback Flow | Time Triggered | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/499e3a9d-9dcc-4958-b57b-b5148382fb09/details?utm_source=solution_explorer) | Runs every weekday, to determine if a submission has been open for more than 7 days, if so it notifies the submissions manager. |

##### Re-Open

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Re-Open Approval Flow | Patient Feedback App | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/7bc24f3d-8217-42fe-acb2-b9fc6217f80d/details?utm_source=solution_explorer) | Manager requests log to be re-opened, with submission id it creates the an approval request with the submissions reviewer, for the submission to be re-opened. |

##### Role Validation

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Persona Checking | Time Triggered | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/e5d346d8-f1b5-46c4-afd6-7bb794cfe658/details?v3=false) | Runs everyday at 4AM to determine if a user in one of the 4 role AD groups is still assigned to a location with that specific role. If they are no longer provisioned a role by a location they will be removed from said AD Group, removing their access to certain functionalities within the application |

##### License Group Validation

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Group Comparison | Time Triggered | [Power Automate](https://make.powerautomate.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/flows/8506d368-5d2e-4366-b17d-53167ec1c3d6/details?v3=false) | Runs everyday around 3AM to make sure no user who is assigned a role in the Location Database is outside of the licensed AD Group. |

##### Role Automation

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Feedback User Role Automation | Location Modification Triggered | [Power Automate](https://make.powerapps.com/environments/6ce136ba-4d43-4f6d-8726-d26f328fbeb3/solutions/6ffc3389-3bea-41fb-97f8-5a5e5866156b/objects/cloudflows/bdcc9b35-7a69-4b07-b173-cc308ba1bdf4/view) | Runs when a location is updated in the location database and if a user new user is assigned a role via a location, it provisions them access to one of the four AD Role groups if applicable |

##### Keep with Me

|     |     |     |     |
| --- | --- | --- | --- |
| Name | Initiator | Mechanism | Description |
| Submit & Manage | New Submission | Limited to Super Users & Reviewers in Patient Feedback App | Option when a user creates a new submission from the Patient Feedback App, where location assignment is ignored and the submission remains in the queue of the reviewer or super user who intends to keep it |

## Onboarding Documentation

ServiceNow Linkout

## Reporting:

|     |     |
| --- | --- |
| Name | [Patient Feedback Dashboard](https://app.powerbi.com/links/DmihH8QXvV?ctid=ef4fd2f8-4c96-45ab-9b15-7831920f55cf&pbi_source=linkShare) |
| Workspace | [IT Solutioning](https://app.powerbi.com/groups/3958a0a9-5042-469c-9d4e-d1714e5a79ed/list?experience=power-bi) |
| Refresh | 6:00 AM  <br>12:00 PM  <br>4:00 PM |
| Dataset | Feedback Dataset |

### Features:

*   Location Specific
*   Location Filtering
*   Grievance KPI's
*   Employee's of Concern
*   Compliment Dashboard
*   Location & Submission Overview

