<!---< Securely deploying a cloud-native application with ARM template. -->
__Securely deploy a cloud-native application using an ARM template to meet several solution requirements.__

##

<br>
Architecture of the event-based application which generates a thumbnail of images uploaded by users:

<!---<img src="https://github.com/user-attachments/assets/65e5a86a-a14d-4edc-91f9-45f050a70473" alt="Cloud App Deployment" style="height: 400px; width:1400px;"/> --->


<table>
  <tr>
    <td>
      <img src="https://github.com/user-attachments/assets/65e5a86a-a14d-4edc-91f9-45f050a70473" alt="Cloud App Deployment" style="height: 400px; width:1000px;"/> 
    </td>
    <td>
      
__Web App__: Front-end for users to upload images. 

__Storage Acccount__: Stores user's images .

__Event Grid Topics__: Configured to trigger Azure function app.

__Function App__: Runs the resize code that reduces the image to a thumbnail.
    </td>
  </tr>
</table>

##

__Deployment Guide__: 

+ Review and Deploy the ARM template in the same location with Resource Group:
    - Search 'deployment custom template' in Azure portal and select the option below: 
 
    - <img width="665" alt="image" src="https://github.com/user-attachments/assets/3fac8ec5-5d04-4b6b-9106-e9f80bff7877">

+ Paste and review the ARM Template 'azuredeploy.json' in the editor:
    - <img width="706" alt="image" src="https://github.com/user-attachments/assets/8c95e5c2-752f-40ea-8876-449d2704c0d0">

+ To meet the solution requirements, the ARM template is modified as follows:

<table>
  <tr>
    <td>
      <img src="https://github.com/user-attachments/assets/13b467aa-28d5-49dc-ae6c-e173215a48da" alt="Cloud App Deployment" style="height: 400px; width:1000px;"/> 
    </td>
    <td>
      
__Autoscale Via Rules and 10 daily backups and 5 staging slots__:  Update the SKU property to 'S1 standard' on line #30:  **_"name": "S1",_**

__Web and Function App must support only HTTPs__: Update the HTTPS property to 'True' on line #41 and #133:  **_"httpsOnly": true,_**.

__Replicate storage account data to secondary region__: Update the SKU property to 'Standard GRS' on line #88:  **_"name": "Standard_GRS",_**

__Transfers to/from storage account via HTTPs__: Update the HTTPS property to 'True' on line #91:  **_"supportsHttpsTrafficOnly": true,_**
    </td>
  </tr>
</table>

+ Save and visualize the ARM architecture

  - <img width="526" alt="image" src="https://github.com/user-attachments/assets/f35bbc96-07c5-4112-a428-398729125aa1">
  
  <br>
  
  - <img width="631" alt="image" src="https://github.com/user-attachments/assets/98b3b975-f7da-437e-ae61-c1fcefc25210">

  - Click "Review + Create" to deploy
 
+ Verify deployment configuration meets requirements:

  - Navigate to 'resource group', first select the app service:
  - <img width="500" alt="image" src="https://github.com/user-attachments/assets/9a960ec0-7271-4486-937f-157b128da12c">
  - From left-hand menu, expand 'Settings' then click 'Scale up(App service Plan)'; confirm S1 standard 10 daily backups are enabled:
  - 







  



