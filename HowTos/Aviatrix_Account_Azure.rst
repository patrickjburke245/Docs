.. meta::
   :description: Aviatrix Cloud Account for Azure
   :keywords: Aviatrix account, Azure, Aviatrix Azure account credential, API credential

===========================================================
Azure Account Onboarding Guide
===========================================================

1. Overview
=============

The Aviatrix Controller uses the Azure API extensively to launch Aviatrix
gateways, configure encrypted peering, and more.

In order for the Controller to call the Azure API, you need to first create an Aviatrix `Access
Account <https://docs.aviatrix.com/HowTos/aviatrix_account.html>`_ on the Aviatrix controller. This access account corresponds
to a valid Azure subscription with API credentials. You need to create an access account for each subscription. 

This document describes, for a given subscription, how to obtain the necessary information,
specifically the ARM Subscription ID, Application ID, Application Key (Client secret), and
Directory ID to create an Aviatrix Access Account so that the Controller can execute APIs on that subscription.


2. Azure UI Steps
========================================

There are 3 main steps to configuring Azure to allow Aviatrix to make API calls:

1. Register an Aviatrix Controller Application with Azure Active Directory.

2. Assign a role to that application.

3. Retrieve the Application ID, Application Key (Client secret), and Directory ID.

**Important:** Complete the following steps in order.

2.1 – Register Aviatrix Controller Application
-------------------------------------------------------

Login to the `Azure Portal <https://portal.azure.com>`.


1. From the Azure portal click on "All services" and search for “Azure Active Directory” and click on “Azure Active Directory”.

2. Click “App registrations".  Do not choose "App registrations (Legacy)".

|image03|

3. Click “+ New registration”.

|image04|

   a. Name = Aviatrix Controller

   b. Supported account types = Accounts in this organizational directory only

   c. Click Register.

3. Done

2.2 – Assign a role to the Aviatrix Application
------------------------------------------------------------


1. On the top left, click All services, search for “Subscriptions”.

  |image11|

2. Copy the Subscription ID (to notepad or a convenient location).

|image12|

3. Click on the Subscription name.

4. Then select “Access control (IAM)”.

|image13|


5. Click Add and then select the “Contributor” role. If the "Contributor" role is too broad, you can later replace it with a custom role with specific permissions. Refer to `Use Azure IAM Custom Role <https://docs.aviatrix.com/HowTos/azure_custom_role.html>`_ for instructions. 


6. In the Select search field, type in “Aviatrix”. The Aviatrix Controller app (that you created in section 2.1) should show up. Select this one and click Select at the bottom of the page.

2.3 – Retrieve Information for Programmatic Access
------------------------------------------------------------

1. From the Azure portal, click All services and search for “Azure Active Directory”. Click “App registrations” and then the application to see the Application (client) ID and Directory (tenant) ID.

   |image01|

2. Retrieve the **Application (client) ID** and **Directory (tenant) ID**.

   |image14|
   
3. Retrieve the **Client Secret**.

   A. Click Certificates & secrets.

   B. Click "+ New client secret".

   |image06|


   C. Enter in the following, and then click Add

      1. Description = Aviatrix

      2. Expires = Never
      
   |image07|

   D. You should see the new secret as shown below.
   
   |image15|

   E. Copy the secret.  This will be used as the Application Key in the Aviatrix Controller.

4. Add **API permissions**.

   Go to Azure Active Directory -> select the "Aviatrix Controller" application, click into the application. 

   A. Click "API permissions".

   |Image08|

   B. Click "+Add a permission".
   
   C. Choose Azure Service Management
   
   |Image09|
   
   |Image10|

5. Done

At this point you should have the following information to create an access account on Azure.

==========================================               ======================
Access Account Setup Input Field                         Value
==========================================               ======================
ARM Subscription ID                                      From section 2.2
Directory ID                                             From section 2.3
Application ID                                           From section 2.3
Application Key (Client Secret)                          From section 2.3
==========================================               ======================

Additional References
=======================

If you need additional information, refer to `How to: Use the portal to create an Azure AD application and service principal that can access resources <https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal>`_ on Azure documentation.

Azure China notes
==================

Deploying Aviatrix Gateways in the Azure China Cloud
-----------------------------------------------------------

Prerequisites:

- You must already have a Microsoft Azure China account and Aviatrix Controller in AWS China to deploy an Aviatrix Gateway in the Azure China Cloud.


1.	Go to Onboarding and select Azure China. 

2.	Enter the Aviatrix Customer ID.

3.	Enter the Certificate Domain.

4.	Create the Primary Access Account.

5. Deploy an Aviatrix gateway from the Gateway page in the Aviatrix Controller or the Multi-Cloud Transit Solution page.

For more information, see `“What is a China ICP License?” <https://docs.aviatrix.com/HowTos/aviatrix_china_overview.html#what-is-a-china-icp-license>`

.. |image01| image:: AviatrixAccountForAzure_media/az-ad-01.PNG
   :width: 5.20313in
   :height: 1.50209in
.. |image02| image:: AviatrixAccountForAzure_media/az-ad-directory-id-02.PNG
   :width: 5.65600in
   :height: 2.39763in
.. |image03| image:: AviatrixAccountForAzure_media/Image03.png
   :width: 100%
.. |image04| image:: AviatrixAccountForAzure_media/Image04.png
   :width: 100%
.. |image05| image:: AviatrixAccountForAzure_media/az-ad-list-all-apps-05.PNG
   :width: 5.65600in
   :height: 2.39763in
.. |image06| image:: AviatrixAccountForAzure_media/Image06.png
   :width: 100%
.. |image07| image:: AviatrixAccountForAzure_media/Image07.png
   :width: 100%
.. |image08| image:: AviatrixAccountForAzure_media/Image08.png
   :width: 100%
.. |image09| image:: AviatrixAccountForAzure_media/Image09.png
   :width: 100%
.. |image10| image:: AviatrixAccountForAzure_media/Image10.png
   :width: 100%
.. |image11| image:: AviatrixAccountForAzure_media/az-ad-sub-role-11.PNG
   :width: 5.65600in
   :height: 2.39763in
.. |image12| image:: AviatrixAccountForAzure_media/az-ad-sub-list-12.PNG
   :width: 6.98958in
   :height: 3.02083in
.. |image13| image:: AviatrixAccountForAzure_media/az-ad-sub-contrib-13.PNG
   :width: 6.98958in
   :height: 3.02083in
   
.. |image14| image:: AviatrixAccountForAzure_media/Image14.png
   :width: 100%
.. |image15| image:: AviatrixAccountForAzure_media/Image15.png
   :width: 100%


.. add in the disqus tag

.. disqus::   
