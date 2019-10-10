---
lab:
    title: 'Lab 01: Data Modeling'
    module: 'Module 01: Introduction to developing with the Power Platform'
---

# MB-400: Microsoft PowerApps + Dynamics 365 Developer
## Module 1, Lab 1 – Data Modeling


Scenario
========

A regional building department issues and tracks permits for new buildings and updates permits for building remodels. Throughout this course you will
build applications and perform automation to enable the regional building
department to manage the permitting process. This will be an end-to-end solution
which will help you understand the overall process flow.

In this lab, you will set up a development and production environment and create
solutions to track your changes. You will also create a data model to support
the following requirements:

-   R1 – Track the status of permits issued for new buildings and existing
    building modifications

-   R2 – Associate permits with a Build Site, which represents the building
    or land being modified

-   R3 – Track permit type to indicate the type of permit, any inspections, or other data
    that might be required on a permit

-   R4 – Track inspections completed on the permit for the
    entire process (i.e., from request of inspection to the pass or fail of the
    inspection)

-   R5 – Track the permit requestor 

High-level lab steps
======================

To prepare your learning environments you will create a solution and publisher,
add both new and existing components that are necessary to meet the application
requirements. Refer to the data model document for the metadata description
(entities, field types and relationships). Your solution will contain several
entities upon completion of all the customizations:

-   Contact

-   Build Site

-   Inspection

-   Permit

-   Permit Type

-   User

Things to consider before you begin
-----------------------------------

-   What are considered as best practices for managing changes in between
    environments (“Dev” to “Test” to “Prod”)?

-   What all entities a user might need in the scenario that we are building?

-   What relationship behaviors would we consider enabling users to complete
    their tasks?

-   Remember to work in your DEVELOPMENT environment with the customizations.
    Once the customizations are completed, published and tested in “Dev”, and if
    everything works fine, the same will be deployed to “Prod”.

<br>Exercise \#1: Create Environments and Solution
==================================================

**Objective:** In this exercise, you will create both development and production
environments.

Task \#1: Create Environments
-----------------------------

First, we will create the Production Environment.

1.  Sign in to <https://aka.ms/ppac>

2.  Select **Environments** and click **New** from the top menu. This will open
    a menu on the right-hand side of the window.

3.  Enter **[Your Last Name] Prod** for **Name**.

4.  Select **Production** in the dropdown for **Type.**

5.  Select your **Region**

6.  Enter the **Purpose** for creating this environment (Optional). Now, either
    follow (g) or (h) to configure the environment.

7.  Turn on the **toggle** to **create a database for this environment** if you
    wish to create the database along with this, otherwise this can be done once
    the environment is configured.

8.  Click **Next.**

9.  Select **Language** and **Currency**. For the purposes of these labs, the
    environments have **English** and **US dollars** (USD) selected.

10. Leave the **Enable Dynamics 365 apps** disabled for the purpose of these
    labs.

11. Leave the **Deploy Sample apps and data** disabled for the purpose of these
    labs.

12. Click **Save**.

13. If the toggle is not turned on here, Click **Save.**

14. Once the environment is provisioned, **Select** the newly created
    environment.

15. Click **Create my database**.

16. Select **Currency** and **Language**. For the purposes of these labs, the
    environments have **US dollars** (USD) and **English** selected.

17. Click **Create my Database**.

Next, we will create the Development Environment.

1.  Select **Environments** and click **New** from the top menu. This will again
    open a menu on the right-hand side of the window.

2.  Enter **[Your Last Name] Dev** for **Name**.

3.  Select **Production** in the dropdown for **Type**.

4.  Select your **Region**.

5.  Enter the **Purpose** for creating this environment (Optional). Now, either
    follow (f) or (g) to configure the environment.

6.  Turn on the **toggle** to **create a database for this environment** if you
    wish to create the database along with this, otherwise this can be done once
    the environment is configured.

7.  Click **Next.**

8.  Select **Language** and **Currency**. For the purposes of these labs, the
    environments have **English** and **US dollars** (USD) selected.

9.  Leave the **Enable Dynamics 365 apps** disabled for the purpose of these
    labs.

10. Leave the **Deploy Sample apps and data** disabled for the purpose of these
    labs.

11. Click **Save**.

12. If the toggle is not turned on here, Click **Save.**

13. Once the environment is provisioned, **Select** the newly created
    environment.

14. Click **Create my database**.

15. Select **Currency** and **Language**. For the purposes of these labs, the
    environments have **US dollars** (USD) and **English** selected.

16. Click **Create my Database**.

You should now have the default environment and the two environments listed
under environments.

Task \#2: Create Solution and Publisher
---------------------------------------

1.  Create Solution

    -   Sign in to <https://make.powerapps.com>

    -   Select your Dev environment.

    -   Select **Solutions** from the left menu and click **New Solution**.

    -   Enter **Permit Management** for **Display Name**.

2.  Create Publisher

    -   Click on the **Publisher** dropdown and select **+ Publisher**.

    -   Enter **Contoso** for **Display Name** and **contoso** for **Prefix**

    -   Click **Save and Close**.

3.  Complete the solution creation.

    -   Now, click on the **Publisher** dropdown and select the **Contoso**
        publisher you just created.

    -   Enter **1.0.0.0** for **Version** and click **Create**.

Task \#3: Add Existing Entity
-----------------------------

1.  Click to open the **Permit Management** solution you just created.

2.  Click **Add Existing** and select **Entity**.

3.  Search for **Contact** and select it.

4.  Click **Next**.

5.  Click **Select Components**.

6.  Select the **Views** tab and select the **Active Contacts** view. Click
    **Add**.

7.  Click **Select Components**.

8.  Select the **Forms** tab and select the **Contact** form.

9.  Click **Add**.

10. You should have **1 View** and **1 Form** selected. Click **Add** again.
    This will add the Contact entity to the newly created solution. Next, we
    will add the User entity.

11. Click Add Existing and select **Entity**.

12. Search for **User** and select it.

13. Click **Next**.

14. **DO NOT** select any components. Click **Add**.

15. Your solution should now have two entities: Contact and User.

Exercise \#2: Create Entities and Fields
========================================

**Objective:** In this exercise, you will create entities and add fields to
these entities and edit the **Status Reason** options for the **Permit** and
**Inspection** entities.

Task \#1: Create Permit Entity and Fields
-----------------------------------------

1.  Continuing in your development environment, open the Permit Management
    solution

    -   Sign in to <https://make.powerapps.com>

    -   Select **Solutions** and click to open the **Permit Management**
        solution you just created.

2.  Create Permit entity

    -   Click **New** and select **Entity**.

    -   Enter **Permit** for **Display Name** and click **Create**. This will
        start provisioning the entity in background while you can start adding
        other fields.

3.  Create Start Date field.

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Start Date** for **Display Name**.

    -   Select **Date Only** for **Data Type**.

    -   Check the **Required** checkbox.

    -   Click **Done**.

4.  Create Expiration Date field.

    -   Click **Add Field**.

    -   Enter **Expiration Date** for **Display Name**.

    -   Select **Date Only** for **Data Type**.

    -   Click **Done**.

5.  Create New Size field.

    -   Click **Add Field**.

    -   Enter **New Size** for **Display Name**.

    -   Select **Whole Number** for **Data Type.**

    -   Click **Done**.

    -   Click **Save Entity**.

Task \#2: Create Permit Type Entity and Fields
----------------------------------------------

1.  Create Permit Type entity

    -   Click on the solution name. This action will take you back to the
        Solution.

    -   Click **New** and select **Entity**.

    -   Enter **Permit Type** for **Display Name**.

    -   Click **Create**.

2.  Create Require Inspections field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Require Inspections** for **Display Name**.

    -   Select **Two Options** for **Data Type**.

    -   Click **Done**.

3.  Create Require Size field

    -   Click **Add Field**.

    -   Enter **Require Size** for **Display Name**.

    -   Select **Two Options** for **Data Type**.

    -   Click **Done**.

4.  Click Save Entity.

Task \#3: Create Build Site Entity and Fields
---------------------------------------------

1.  Create Build Site entity

    -   Click on the solution name. This action will take you back to the
        Solution.

    -   Click **New** and select **Entity**.

    -   Enter **Build Site** for **Display Name.**

    -   Change the **Display Name** of the **Primary Field** to **Street
        Address.**

    -   Change the **Name** of the **Primary Field** to **street1.**

    -   Click **Create**.

2.  Add City field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **City** for **Display Name** and change the **Name** to **city**.

    -   Make sure **Text** is selected for **Data Type**.

    -   Check the **Required** checkbox.

    -   Click **Done**.

3.  Add Zip/Postal Code field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **ZIP/Postal Code** for **Display Name** and change the **Name**
        to **postalcode**.

    -   Make sure **Text** is selected for **Data Type**.

    -   Check the **Required** checkbox.

    -   Click **Done**.

4.  Add State/Province field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **State/Province** for **Display Name** and change the **Name** to
        **stateprovince**.

    -   Make sure **Text** is selected for **Data Type**.

    -   Check the **Required** checkbox.

    -   Click **Done**.

5.  Add Country Region field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Country/Region** for **Display Name** and change the **Name** to
        **country**.

    -   Make sure **Text** is selected for **Data Type.**

    -   Click **Done**.

6.  Click **Save Entity**.

Task \#4: Create Inspection Entity and Fields
---------------------------------------------

1.  Create Inspection entity

    -   Click on the solution name. This action will take you back to the
        Solution.

    -   Click **New** and select **Entity**.

    -   Enter **Inspection** for **Display Name.**

    -   Click **Create**.

2.  Add Inspection Type field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Inspection Type** for **Display Name**.

    -   Select **Option Set** for **Data Type**.

    -   Click on the **Option Set** dropdown and select +**New Option Set.**

    -   Enter **Initial Inspection** and click **Add New Item**.

    -   Enter **Final Inspection** and click **Save**.

    -   Click **Done**.

3.  Add Scheduled Date field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Scheduled Date** for **Display Name**.

    -   Select **Date Only** for **Data Type**.

    -   Check the **Required** checkbox.

    -   Click **Done**.

4.  Add Comments field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Comments** for **Display Name**.

    -   Make sure **Text** is selected for **Data Type.**

    -   **Set Max length to 1000 in the Advanced options**

    -   Click **Done**.

5.  Add Sequence field

    -   Make sure you have the **Fields** tab selected and click **Add Field**.

    -   Enter **Sequence** for **Display Name**.

    -   Make sure **Text** is selected for **Data Type**.

    -   Click **Done**.

6.  Click **Save Entity**.

7.  Select **Solutions** on the top and this action will take you back to the
    Solutions page.

8.  Click **Publish All Customizations.**

Task \#5: Edit Status Reason Options
------------------------------------

1.  Open the Permit Management solution

    -   Sign in to <https://make.powerapps.com>

    -   Select **Solutions** from the left menu and click to open the **Permit
        Management** solution you have created.

    -   Click on the **…** icon and select **Switch to Classic**.

2.  Edit Inspection entity Status Reason options

    -   Expand **Entities**.

    -   Expand the **Inspection** entity and select **Fields**.

    -   Locate and double click to open the **statuscode** field.

3.  Change the Active option label

    -   Make sure you have the **Active** selected for **Status**.

    -   Select the **Active** option and click **Edit**.

    -   Change the **Label** to **New Request** and click **OK**.

4.  Add the Pending Option

    -   Click **Add**.

    -   Enter **Pending** for **Label** and click **OK**.

5.  Add the Passed Option

    -   Click **Add**.

    -   Enter **Passed** for **Label** and click **OK.**

6.  Add the Failed Option

    -   Click **Add**.

    -   Enter **Failed** for **Label** and click **OK.**

7.  Add the Canceled Option

    -   Click **Add**.

    -   Enter **Canceled** for **Label** and click **OK.**

8.  Your option-set should now have 5 options for the **Active** state.

9.  Select Pending as the Default Value and click **Save and Close**. from the
    top menu.

10. Edit Permit entity Status Reason options

    -   Expand the **Permit** entity and select **Fields**.

    -   Locate and double click to open the **statuscode** field.

11. Add the Locked option

    -   Make sure you have the **Active** selected for **Status**.

    -   Click **Add**.

    -   Enter **Locked** for Label and click **OK**.

12. Add the Completed option

    -   Click **Add**.

    -   Enter **Completed** for Label and click **OK**.

13. Add the Canceled option

    -   Click **Add**.

    -   Enter **Canceled** for Label and click **OK**.

14. Add the Expired option

    -   Click **Add**.

    -   Enter **Expired** for Label and click **OK**.

15. Your option-set should now have 5 options for the **Active** state.

16. Select the **Active** for the **Default Value** and click **Save and Close**
    from the top menu.

17. Select **Information** from the left side menu and click **Save and Close**
    to close classic solution explorer.

18. Select **Solutions** from the top menu and click **Publish All
    Customizations**.

Exercise \#3: Create Relationships 
===================================

**Objective:** In this exercise, you will create relationships.

Task \#1: Create Relationships
------------------------------

1.  Open the Permit Management solution

2.  Sign in to <https://make.powerapps.com>

3.  Select **Solutions** and click to open the **Permit Management** solution
    just created.

4.  Create Permit to Contact relationship

5.  Click to open the **Permit** entity.

6.  Select the **Relationships** tab.

7.  Click **Add Relationship** and select **Many-to-one**.

8.  Select Contact for **Related (One)** and click **Done**.

9.  Create Permit to Inspection relationship

10. Click **Add Relationship** and select **One-to-Many**.

11. Select **Inspection** for **Entity** in the **Related (Many)** and click
    **Advanced Options**.

12. Change the **Type of Behavior** to **Parental** and click **Done**.

13. Create Permit to Build Site relationship

14. Click **Add Relationship** and select **Many-to-One**.

15. Select **Build Site** for **Related (One) Entity** and click **Advanced
    Options**.

16. Change the **Delete** to **Restrict** and click **Done**.

17. Create Permit to Permit Type relationship

18. Click **Add Relationship** and select **Many-to-One**.

19. Select **Permit Type** for **Related (One) Entity** and click **Done**.

20. Click **Save Entity**.

21. Select **Solutions** from the top menu and click **Publish All
    Customizations.**
