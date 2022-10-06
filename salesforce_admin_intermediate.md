**<h1 align=center>DATA SECURITY</h1>**
---
# **[Overview of Data Security](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_overview?trail_id=force_com_admin_intermediate&trailmix_creator_id=strailhead&trailmix_slug=build-your-admin-career-on-salesforce)**

## **Explain the importance of giving the right people access to the right data.**
The goal is to limit what people can see, to what they should see. There are various ways to do this. With the platform you can control what users can view, create, edit, or delete a record or a field. 

Through the four different levels, you can customize how you achieve this.

## **List the four levels at which you can control data access.**
Data access can be controled <u>four ways</u>:

### **1. Organization**
For your organization you control users, password policies, login limits (hours, locations).

### **2. Objects**
Objects can be limited to who can create them, view them, edit them, delete them.

Permission Sets can be used to add access (never remove access).

### **3. Fields**
Fields can be restricted even if the user has access to the object they are on.

### **4. Records**
Individual records can also be restricted for certain users.

Record-level access is controled four ways:
1. Organization-wide defaults - set default level of access users have to each others records, then expand from there.
2. Role hierarchies - allow those higher in the hierarchy to access records from those beneath them.
3. Sharing rules - exceptions to org-wide defaults for groups.
4. Manual sharing - owners of records can share with others.

![](https://res.cloudinary.com/hy4kyit2a/f_auto,fl_lossy,q_70/learn/modules/data_security/data_security_overview/images/ab1b4360799e29b571fb9fc51cd003e8_adg-security-sharing-concepts.jpg)

## **Audit System Use**
Do it regularily to detect abuse. ***Record modification fields*** show the name of the user that changed the record. ***Login History*** shows successful/failed logins. ***Field History Tracking*** track changes of individual fields. ***Setup Audit Trail*** logs when modifications are made to your organization's configuration.

# **[Control Access to the Org](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_org?trail_id=force_com_admin_intermediate&trailmix_creator_id=strailhead&trailmix_slug=build-your-admin-career-on-salesforce)**

## 