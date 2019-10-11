---
lab:
    title: 'Lab 02: Model driven app'
    module: 'Module 01: Introduction to developing with the Power Platform'
---

# MB-400: Microsoft PowerApps + Dynamics 365 Developer
## Module 1, Lab 2 - Model driven app

Scenario
========

A regional building department issues and tracks permits for new buildings and
tracks updates for remodeling of existing buildings. Throughout this course you will
build applications and automation to enable the regional building department to
manage the permitting process. This will be an end-to-end solution which will
help you understand the overall process flow.

In this lab we will continue to build on top of the components created in the
previous module. We will now build a PowerApps model-driven app to allow the
office staff to manage records for the inspectors and to empower the inspectors to manage
their own records as needed.

High-level lab steps
======================

As part of creating the model-driven app, you will complete the following:

-   Create a new model-driven app named Permit Management

-   Edit the app navigation to reference the required entities

-   Customize the forms and views of the required entities for the app

We will work with the following components:

- **Views**: Views allow the user to display the existing data in the form
of table.

- **Forms**: This is where the user creates/updates new records in the entities.

Both will be integrated to the model-driven app for a better user-experience.

Things to consider before you begin
-----------------------------------

-   What changes should we make to improve the user experience?

-   What should we include in a model-driven app based on the data model we’ve
    built?

-   What customizations can be made on the sitemap of a model-driven app?

-   Remember to continue working in your DEVELOPMENT environment. We’ll move
    everything to production once everything is built and tested.

Exercise \#1: Customize Views and Forms
=======================================

**Objective:** In this exercise, you will customize views and forms of the
custom created entities that will be used in the model-driven app.

Task \#1: Edit Permit Form and View
-----------------------------------

1.  Open your browser inside of your Virtual Machine.

2.  Sign in to <https://make.powerapps.com> if you are not already signed in.

3.  Select your **Dev environment.**

4.  Select **Solutions**.

5.  Click to open the **Permit Management** solution.

6.  Click to open the **Permit** entity.

7.  Select the **Forms** tab and click to open the **Main** form. By default the
    form has two fields, Name (Primary Field) and Owner.

8.  Drag the **Permit Type** field to the form and place it below the **Name**
    field.

9.  Add **Build Site** lookup, **Contact** lookup, **Start Date** and **New Size** to the form. The form should now look like the image below.

10. Drag the **Status Reason** field and drop it in the right side of the form
    header. (You may need to minimize the Properties pop-out on the right side of the screen to see the field on the form.)

11. To add new tab for **Inspections** to the form, focus on the main body of
    the form (not in the header) click **Add Component**.

12. Select **One Column Tab**.

13. Go to the **Properties** pane on the right side, change the **Tab Label** to **Inspections**
    and the **Name** to **inspectionsTab**.

14. To add a Sub-Grid to the Permit form, select the **Inspections** tab. Make
    sure that you have selected the whole Tab and not just a section.

15. Click **Add Component**.

16. Scroll down and select **Subgrid,** this will open a pop-up to select
    Entity.

17. Check the **Related Records** checkbox, select **Inspections (Permit)** for
    **Entity**, select Active **Inspections** for **Default View** and click
    **Done**.

18. To edit Sub-Grid properties, go to the sub-grid properties pane and change
    the Label to **Inspections**.

19. To hide the section label, click to select the section.

20. Go to the **Properties** pane and check the **Hide Label** checkbox.

21. Click **Save** and wait for the save to complete.

22. Click **Publish** and wait for the publishing to complete.

23. Click on the back button in the browser. You should now be back to the
    Permit entity Forms Tab.

24. To edit the Active Permits view, select the **Views** tab and click to open
    the **Active Permits** view.

25. Drag the **Build Site** field and drop it between the **Name** and **Created
    On** fields.

26. Click on the **Permit Type** field. The Permit Type field will be added to
    the view.

27. Click on the **Contact** field. The **Contact** field will be added to the
    view.

28. Go to the view designer and click on the chevron icon of the **Created On**
    column.

29. Click **Remove**. **Created On** field will now be removed from the view.

30. Click **Save** and wait until the changes are saved.

31. Click **Publish** and wait for the publishing to complete

32. Click on the back button in the browser.

Task \#2: Edit Build Site Form and View
---------------------------------------

1.  Open the Permit Management solution.

2.  Sign in to <https://make.powerapps.com>

3.  While in your dev environment click to open the **Permit Management**
    solution.

4.  Edit the Build Site entity form.

5.  Click to open the **Build Site** entity.

6.  Select the **Forms** tab and click to open the **Main** form.

7.  Add **City**, **State/Province**, **Zip/Postal Code**, and **Country
    Region** fields to the form between **Street Address** and **Owner**.

8.  Click **Save** and wait until the changes are saved.

9.  Click **Publish** and wait for the publishing to complete.

10. Click on the back button in the browser.

11. Edit the Active Build Sites view.

12. Select the **Views** tab and click to open the **Active Build Sites** view.

13. Add **City** and **Zip/Postal Code** to the view.

14. Remove **Created On** from the view by selecting **Remove** from the options
    in field Chevron.

15. Click **Save** and wait until the changes are saved.

16. Click **Publish** and wait for the publishing to complete.

17. Click on the browser back button.

Task \#3: Edit Inspection Form and View
---------------------------------------

1.  Sign in to <https://make.powerapps.com>

2.  While in your dev environment, select **Solutions** and click to open the
    **Permit Management** solution.

3.  To edit the Inspection entity form, first click to open the **Inspection**
    entity.

4.  Select the **Forms** tab and click to open the **Main** form.

5.  Add **Inspection type**, **Permit**, **Scheduled Date**, and **Comments**
    fields to the form. **Inspection type**, **Permit**, **Scheduled Date**
    should be added between **Name** and **Owner**, while **Comments** will be
    added after the **Owner** field.

6.  Drag the **Status Reason** field **Comments** and drop it in the right side
    of the form header.

7.  Click **Save** and wait until the changes are saved.

8.  Click **Publish** and wait for the publishing to complete.

9.  Click on the back button in the browser.

10. To edit the Active Inspections view, select the **Views** tab and click to
    open the **Active Inspections Sites** view.

11. Add **Inspection Type, Scheduled Date** and **Sequence** to the view.

12. Remove **Created On** from the view by selecting the chevron on the field
    and select **Remove**.

13. Click **Save** and wait until the changes are saved.

14. Click **Publish** and wait for the publishing to complete.

15. Click on the browser back button.

16. To create a new Inspector View for the Inspection entity, make sure you
    still have the **Views** tab selected.

17. Click **Add View**. This will open a new window to create View.

18. Enter **Inspector View** for **Name** and click **Create**.

19. Add **Inspection Type**, **Permit**, **Scheduled Date**, and **Sequence**
    fields to the view.

20. To sort the Inspector View by the Sequence, go to the view properties pane
    and click **Sort By**.

21. Select **Sequence**.

22. To filter the Inspector View, go to the view properties pane and click
    **Edit Filter**. This will open a new pop-up on the right side of the
    window.

23. Click **Add** and select **Add Row**.

24. Set the filter property by Selecting **Status Reason** in first dropdown and
    **Pending** in the third dropdown**.** Now, click **Add** and select **Add
    Row** again.

25. Select **Owner** field in the first dropdown and Equals current user in
    second dropdown and click **OK**.

26. Click **Save** and wait until the changes are saved.

27. Click **Publish** and wait for the publishing to complete.

28. Once the changes are published, close the window and click **Done** on the
    previous window for the PowerApps.

Task \#4: Edit Permit Type Form
-------------------------------

1.  Sign in to <https://make.powerapps.com>

2.  Select your **Dev environment.**

3.  Select **Solutions**.

4.  Click to open the **Permit Management** solution.

5.  Edit the Permit Type entity form.

    -   Click to open the **Permit Type** entity.

    -   Select the **Forms** tab and click to open the **Main** form.

    -   Add **Require Inspections** and **Require Size** fields to the form
        between **Name** and **Owner**.

    -   Click Save and wait until the changes are saved.

6.  Click **Publish** and wait for the publishing to complete.

7.  Click on the browser back button.

8.  Edit the **Permit Type** entity **Active Permit Type** View.

    -   Select the **Views** tab and click to open the **Active Permit Type**
        view.

    -   Add **Require Inspections** and **Require Size** to the view.

    -   Remove **Created On** from the view but selecting the chevron on the
        field and select **Remove**.

9.  Click **Save** and wait until the changes are saved.

10. Click **Publish** and wait for the publishing to complete.

11. Click on the browser back button.

Exercise \#2: Create Model-Driven Application
=============================================

**Objective:** In this exercise, you will create the model-driven app, customize
the sitemap, and test the app.

**Note:** You will see several fields not addressed as you build out your
application, particularly on the sitemap steps. We have taken some short cuts in
the interest of doing the labs. In a real project you would give these items
logical names.

Task \#1: Create Application
----------------------------

1.  Open the Permit Management solution.

    -   Sign in to <https://make.powerapps.com>

    -   While in your dev environment, click to open the **Permit Management**
        solution.

2.  Create the Model-Driven Application

    -   Click **New** and select **App \| Model-Drive App**. This will open a
        new Window.

    -   Enter **Permit Management** for Name and click **Done**.

3.  Edit Sitemap

    -   Click **Edit Site map.**

4.  Edit the default titles

    -   Select **New Area**.

    -   Go to the properties pane and enter **Building Dept**. for **Title**.

    -   Select **New Group**.

    -   Go to the **Properties** pane and enter **Permits** for **Title**.

5.  Add the Permit entity to the sitemap

    -   Select **New Subarea**.

    -   Go to the **Properties** pane and select **Entity** from the dropdown
        for **Type**.

    -   Search for **Permit** entity from the dropdown for **Entity**.

6.  Add the Inspection entity to the sitemap

    -   Select **Permits** group and click **Add**.

    -   Select **Subarea**.

    -   Go to the **Properties** pane.

    -   Select **Entity** from the dropdown for **Type** and search for
        **Inspection** entity from the dropdown for **Entity**.

7.  Add the Permit Type entity to the sitemap

    -   Select **Permits** group and click **Add**.

    -   Select **Subarea**.

    -   Go to the **Properties** pane.

    -   Select **Entity** from the dropdown for **Type** and search for **Permit
        Type** entity from the dropdown for **Entity**.

8.  Add new Group to the sitemap

    -   Select the **Building Dept.** area and click **Add.**

    -   Click **Add** and select **Group**.

    -   Select **Group**.

    -   Go to the **Properties** pane and enter **Contacts** for Title.

9.  Add the Contact entity to the Contacts group.

    -   Select the **Contacts** group.

    -   Click **Add** and select **Subarea.**

    -   Go to the **Properties** pane.

    -   Select **Entity** from the dropdown for **Type** and search for
        **Contact** entity in the dropdown for **Entity**.

10. Add the Build Site entity to the Contacts group.

    -   Select the **Contacts** group.

    -   Click **Add** and select **Subarea.**

    -   Go to the **Properties** pane.

    -   Select **Entity** from the dropdown for **Type** and search for **Build
        Site** entity in the dropdown for **Entity**.

11. Click **Save**, this will show the loading screen while the changes are
    getting saved.

12. Click **Publish** to publish the sitemap and wait for the publishing to
    complete.

13. Click **Save and Close** to close the sitemap editor.

14. You will see the assets for the entities that were added to the sitemap are
    now all in the application.

15. Click **Save** to save the application.

16. Click **Validate** to validate the changes done in the application. This
    will show some warnings but we can ignore them, since we have not referenced
    a specific View and Form for the entities and this will display all the
    Views and Forms.

17. Click **Publish** to publish the application and wait for the publishing to
    complete.

18. Click **Save and Close to** close the app designer.

19. Click **Done**.

20. Now, Select the **Solutions** and select **Publish all Customizations.**

21. Select **Apps** and your application should now be listed in the Recent
    Apps.

Task \#2: Test Application
--------------------------

1.  Start the application

    -   Select **Apps** and click to open the **Permit Management** app in a new
        window.

    -   The application should start.

2.  Create new Contact record

    -   Select **Contacts**

    -   Click **New** from the top menu.

    -   Provide **First Name as John** and **Last Name as Doe**.

    -   Click **Save and Close**.

    -   You should now see the created contact on the **Active Contacts** view.

3.  Create new Build Site record

    -   Select **Build Sites** from the sitemap.

    -   Click **New**.

    -   Provide **Street Address**, **City**, **State/Province**, **Zip/Postal
        Code**, and **Country/Region** as:

        1.  Street Address: One Microsoft Way

        2.  City: Redmond  
            State/Province: WA

        3.  ZIP/Postal Code: 98052

        4.  Country/Region: USA

    -   Click **Save and Close** and this will show the newly created record on
        the Active Build Sites View.

4.  Create new Permit Type record

    -   Select **Permit Types** from the sitemap.

    -   Click **New**.

    -   Provide **Name** as **New Construction** and click **Save and Close**.
        This will create the record and you should be able to see it on the
        Active Permit Type View.

5.  Create new Permit record

    -   Select **Permits** from the sitemap.

    -   Click **New**.

    -   Provide **Name** as **Test Permit**, select the **Permit Type**, **Build
        Site**, and the **Contact** records you created in the previous steps.

    -   Select a future date for the **Start Date** and click **Save**.

6.  Create new Inspection record

    -   Go to the **Inspections** tab

    -   Click **+ New Inspections**.

    -   Provide **Name** as **Framing Inspections**, select **Initial
        Inspection** from the dropdown for **Inspection Type**, and select
        future date for **Scheduled Date**.

    -   Click **Save and Close.**

    -   The **Inspection** record should now show up on the **Permit** sub-grid.

7.  You may add more test records.

