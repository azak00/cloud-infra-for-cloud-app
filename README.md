<!---< Securely deploying a cloud-native application with ARM template. -->
__Securely deploying a cloud-native application using an ARM template to meet several solution requirements.__

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

__Deployment Guide__



