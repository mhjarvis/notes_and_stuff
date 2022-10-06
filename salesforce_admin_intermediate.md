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

### Hands on - know how to do the following:

* Create / Deactivate a User
* Set a Password Policy
* Specify Trusted IP Ranges
* Restrict Login Access by IP Address Using Profiles
* Restrict Login Access by Time

# **[Control Access to Objects](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_objects?trail_id=force_com_admin_intermediate&trailmix_creator_id=strailhead&trailmix_slug=build-your-admin-career-on-salesforce)**

## **Manage Object Permissions**
Setting permisions on an object is simplest way to control data access. Use profiles or permission sets. 

## **Use Profiles to Restrict Access**
Each user has a profile. Profiles consist of settings and permissions. These control what a user can see. These can be asigned to many users.

## **Standard Profiles**
Examples are:
* Standard User
* Contract Manager
* System Administrator

Each profile has default settings/permissions. System Admin has two important permissions: *View All Data* and *Modify All Data*. These overide all other sharing settings. Permissions cannot be edited on standard profiles (you will need to clone them).

Profile functionality is dependent on user license type.

### Hands on - know how to do the following:
* Manage profiles
* Create a profile
* Assign a profile
* Use Permission Sets to grant access
* Manage Permission Sets
* Create a Permission Set

# **[Control Access to Fields](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_fields?trail_id=force_com_admin_intermediate&trailmix_creator_id=strailhead&trailmix_slug=build-your-admin-career-on-salesforce)**

## **Modify Field-Level Security**
This should come after restricting object-level access. Use this to restrict what they can see on objects. It controls if someone can view, edit, and delete the fields value.

Use this over page layouts (which only hide fields). Field-level security controls the visibility of fields in any part of the app, including related lists, list views, reports, and search results.

### Hands on - know how to do the following:
* Restrict Field Access with a Profile
* Add Field Access with a Permission Set

# **[Control Access to Records](https://trailhead.salesforce.com/content/learn/modules/data_security/data_security_records?trail_id=force_com_admin_intermediate&trailmix_creator_id=strailhead&trailmix_slug=build-your-admin-career-on-salesforce)**

