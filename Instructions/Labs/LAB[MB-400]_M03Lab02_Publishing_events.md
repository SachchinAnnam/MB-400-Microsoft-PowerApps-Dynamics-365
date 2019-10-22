---
lab:
    title: 'Lab 01: Publishing events externally'
    module: 'Module 03: Extending the Power Platform user experience'
---

# MB-400: Microsoft PowerApps + Dynamics 365 Developer
## Module 3, Lab 1 - Publishing events externally

Scenario
========

A regional building department issues and tracks permits for new buildings and
updates for remodeling of existing buildings. Throughout this course you will
build applications and perform automation to enable the regional building
department to manage the permitting process. This will be an end-to-end solution
which will help you understand the overall process flow.

In this lab you will use the event publishing capability of the Common Data
Service. When a permit results in changing the size of the build site, an
external taxing authority needs to be notified so they can evaluate if
additional taxing is required. You will configure CDS to publish permits with
size changes using the web hook option. To simulate the taxing authority
receiving the information you will create a simple Azure function to receive the
post.

High-level lab steps
======================

As part of configuring the event publishing, you will complete the following:

-   Create an Azure Function to receive the web hook post

-   Configure CDS to publish events using a web hook

-   Test publishing of events

Things to consider before you begin
-----------------------------------

-   Do we know what events will trigger our web hook?

-   Could what we are doing with the web hook, be done using Microsoft Flow?

-   Remember to continue working in your DEVELOPMENT environment. We’ll move
    everything to production soon.

Exercise \#1: Create an Azure Function
======================================

**Objective:** In this exercise, you will create an Azure Function that will be
the endpoint to accept and log incoming web requests.

Task \#1: Create Azure Function App
-----------------------------------

1.  Create new function application

    -  Sign in to <https://portal.azure.com> and login.

    -  Select + **Create a Resource**.

    -  Search for Function App and select it.

    -  Click **Create**.

    -  Enter your initials plus today’s date for **App Name**, select your
        **Subscription**, and select **Create New** for **Resource Group**.

    -  Select **Consumption Plan** for **Hosting Plan**, select location in the
        same region as **CDS**, **Create New Storage**, and click **Create**.

    -  Wait for the function app to be created.

Task \#2: Create an Azure Function
----------------------------------

1.  Create a new function

   -  Select **All Resources**, search for the function application you
        created and open it.

    -  Create new function by selecting the + icon.

    -  Select **In-Portal** and click **Continue.**

    -  Select **Webhook + API** and click **Create**.

2.  Test the function

    -  Click on the **Test** pane.

    -  Click **Run**.

    -  You should see **Hello, Azure** in the output.

3.  Edit the function

    -  Identify the following lines in the code and remove them. Do not remove any lines between the following lines.

			string name = req.Query["name"];

			name = name ?? data?.name;

			return name != null
				? (ActionResult) new OkObjectResult($"Hello, {name}")
				: new BadRequestObjectResult("Please pass a name on the query string or in the request body");

	- 	Change the method signature from Task<IActionResult> to void.
	
	- 	Add the code below to the function.
	
			string indentedJson = JsonConvert.SerializeObject(data, Formatting.Indented);
			log.LogInformation(indentedJson);

	- Click **Save.**
	
4.  Remove HTTP output

    -   Select **Integrate**.

    -   Select the **HTTP Output**.

    -   Click **Delete**.

    -   Select the function and click **Save** again.

5.  Get the function URL

    -   Click Get Function URL.

    -   Click **Copy** and the close the popup.

    -   Save the **URL**, you will need it in the next exercise.

Exercise \#2: Configure Web Hook
================================

Task \#1: Configure publishing to a web hook
--------------------------------------------

1.  Download the SDK Toolkit. If you already have the Plugin Registration tool
    from the previous lab you can proceed to step 3 of this task.

    -   Navigate to <https://xrm.tools/SDK>

    -   Click **Download SDK Zip File**.

    -   Save the zip file on your machine.

    -   Right click on the downloaded **sdk.zip** file and select
        **Properties**.

    -   Check the **Unblock** checkbox and click Apply.

    -   Click **OK**.

    -   Right click on the **sdk.zip** file again and select **Extract All**.

    -   Complete extracting.

2.  Start the Plugin Registration Tool

    -   Open the **sdk** folder you extracted and click to open the
        **PluginRegistration** folder.

    -   Locate and double click PluginRegistration.exe.

3.  Create new connection

    -   Click **Create New Connection**.

    -   Select **Office 365** and check the **Display List of available
        organization** and **Show Advanced** checkboxes. Select **Online
        Region** where your organization is located. If you are unsure what
        region to select, select **Don’t Know**.

    -   Provide your **CDS** credentials and click **Login**.

    -   Select the **Dev** environment and click **Login**.

4.  Register new Web Hook

    -   Click **Register** and select **Register New Web Hook**.

    -   Enter **NewSize** for **Name**.

    -   Go to the notepad where you saved the function URL and copy everything
        before the **‘?’**.

    -   Go back to the **Plugin Registration** tool and paste the **URL** you
        copied in the **Endpoint URL** field.

    -   Select **WebhookKey** for **Authentication**.

    -   Go back to the notepad and copy the key.

    -   Go back to the **Plugin Registration** tool, paste the key you copied in
        the **Value** field and click **Save**.

5.  Register new step

    -   Select the **Web Hook** you registered, click **Register** and select
        **Register New Step**.

    -   Select **Update** for **Message**, **contoso_permit** for **Primary
        Entity**, and click **Filtering Attributes.**

    -   Uncheck all by selecting the checkbox, select **New Size** and click
        **OK**.

    -   Select **Asynchronous** for **Execution Mode** and click **Register New
        Step**.

Task \#2: Test the Web Hook
---------------------------

1.  Start the Permit Management application

    -   Sign in to <https://make.powerapps.com> and make sure you have the
        **Dev** environment selected.

    -   Select Apps and click to open the Permit Management application.

    -   Select **Permits** and open one of the permit records. Create new if you
        don’t have a Permit record.

    -   Change the **New Size** to **5000** and **Save**.

2.  Check Azure Output

    -   Go back to your **Azure Function**.

    -   Open **Logs**. The Output is a
        serialized **RemoteExecutionContextobject** object.

    -   **Hint**: If the log is not showing in the console (sometimes it
        happens), click **Monitor** on the left and check execution log, select
        entry, details will be on the right (could be delayed up to 5 min
        though)

3.  Confirm the function executes only when the New Size value changes

    -   Go back to the **Permit Management** application.

    -   Change the **Start Date** to tomorrow’s date and click **Save**.

    -   Go back to the Azure Function and make sure the function did not
        execute.

Task \#3: Configure an entity image 
------------------------------------

This step allows you to avoid unnecessarily querying CDS and make a request only
when you need information from the primary entity. It can also be used to get
the prior value of a field before an update operation.

1.  Register New Image

    -   Go back to the **Plugin Registration** tool.

    -   Select the **NewSize** step you created, click **Register** and select
        **Register New Image**.

    -   Check both Pre and Post images checkboxes.

    -   Enter **Permit Image** for **Name**, **PermitImage** for **Entity
        Alias**, and click on the **Parameters** button.

    -   Select **Build Site**, **Contact**, **Name**, **New Size**, **Permit
        Type**, and **Start Date**, and then click **OK**.

    -   Click **Register Image**.

2.  Clear Azure log

    -   Go back to the **Azure Function.**

    -   Clear **Logs**.

3.  Update Permit record

    -   Go to the **Permit Management** application.

    -   Select **Permits** and open one of the **Permit** records.

    -   Change the New Size to **4000** and click **Save**

4.  Check Azure logs

    -   Go back to the **Azure Function**.

    -   Expand the log pane.

    -   The logs should now show both **Pre** and **Post** entity images. In
        this case you should see the old value **5000** in **Pre** image and the
        new value **4000** in the **Post** image.

    -   **Note: **technically, we have the data in the Target object already.
        However, if there are plugins modifying the data, PostImage will contain
        the copy as recorded in CDS while Target contains the data as submitted
        on Save. In addition to that, preimage contains data before the save
        operation took place.


