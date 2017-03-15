---
title: "Ajout et suppression de Pages de propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pages de propriétés, ajout"
  - "pages de propriétés, sous-types de projets"
  - "pages de propriétés, suppression"
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Ajout et suppression de Pages de propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Concepteur de projets fournit un emplacement centralisé pour gérer des propriétés de projet, les paramètres, et les ressources dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il apparaît comme une fenêtre unique dans l'environnement de développement intégré \(IDE\) de \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et contient plusieurs volets de droite accessibles via les onglets à gauche.  Les volets \(souvent appelés pages de propriétés\) dans le Concepteur de projets varie selon le type et le langage du projet.  Le Concepteur de projets sont accessibles avec la commande de **Propriétés** dans le menu de **Projet** .  
  
 Un sous\-type de projet doit souvent afficher les pages de propriétés supplémentaires dans le Concepteur de projets.  De même, des sous\-types de projet peuvent requérir que des pages de propriétés intégrées été supprimées.  Pour faire l'une ou l'autre, votre sous\-type de projet doit implémenter l'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> et substituer la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> .  En substituant cette méthode et en utilisant le paramètre d' `propId` contenant une des valeurs de l'énumération d' <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> , vous pouvez filtrer, ajouter ou supprimer des propriétés du projet.  Par exemple, vous devrez peut\-être ajouter une page aux pages de propriétés de configuration.  Pour ce faire, vous devez filtrer les pages de propriétés de configuration puis une nouvelle page à la liste existante.  
  
## Ajout et suppression de pages de propriétés du Concepteur de projets  
  
#### Pour supprimer une page de propriétés du Concepteur de projets  
  
1.  substituez la méthode d' `GetProperty(uint itemId, int propId, out object property)` aux pages de Filter, propriété et obtenez une liste d' `clsids` .  
  
    ```vb#  
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-independent property pages.  
        Select Case propId  
            ....   
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))  
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)  
                'Remove the property page here  
                   ....  
            ....  
        End Select  
            ....   
        Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-independent property pages.  
        switch (propId)  
        {  
            . . . .  
  
            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);  
                    //Remove the property page here  
                    . . . .  
                }  
             . . . .  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
2.  supprimez la page d' **Événements de build** de la liste obtenue d' `clsids` .  
  
    ```vb#  
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"  
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)  
    If index <> -1 Then  
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1  
        If index2 >= propertyPagesList.Length Then  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)  
        Else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)  
        End If  
    End If  
    'New property value  
    property = propertyPagesList  
    ```  
  
    ```c#  
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";  
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);  
    if (index != -1)  
    {  
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        int index2 = index + buildEventsPageGuid.Length + 1;  
        if (index2 >= propertyPagesList.Length)  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');  
        else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);  
    }  
    //New property value  
    property = propertyPagesList;  
    ```  
  
#### Pour ajouter une page de propriétés du Concepteur de projets  
  
1.  Créez une page de propriétés que vous souhaitez ajouter.  
  
    ```vb#  
    Class DeployPropertyPage  
            Inherits Form  
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
        'Summary: Return a stucture describing your property page.  
        ....   
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())  
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()  
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))  
            info.dwHelpContext = 0  
            info.pszDocString = Nothing  
            info.pszHelpFile = Nothing  
            info.pszTitle = "Deployment" 'Assign tab name  
            info.SIZE.cx = Me.Size.Width  
            info.SIZE.cy = Me.Size.Height  
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then  
                pPageInfo(0) = info  
            End If  
        End Sub  
    End Class  
    ```  
  
    ```c#  
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
    {  
        . . . .   
        //Summary: Return a stucture describing your property page.  
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)  
        {  
            PROPPAGEINFO info = new PROPPAGEINFO();  
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));  
            info.dwHelpContext = 0;  
            info.pszDocString = null;  
            info.pszHelpFile = null;  
            info.pszTitle = "Deployment";  //Assign tab name  
            info.SIZE.cx = this.Size.Width;  
            info.SIZE.cy = this.Size.Height;  
            if (pPageInfo != null && pPageInfo.Length > 0)  
                pPageInfo[0] = info;  
        }  
    }  
    ```  
  
2.  enregistrez votre nouvelle page de propriétés.  
  
    ```vb#  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```c#  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3.  substituez la méthode d' `GetProperty(uint itemId, int propId, out object property)` aux pages de Filter, propriété, obtenez une liste d' `clsids` et ajoutez une nouvelle page de propriétés.  
  
    ```vb#  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-dependent property pages.  
        Select Case propId  
            ....   
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):  
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                'Add the Deployment property page.  
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")  
        End Select  
            ....   
            Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
    ```  
  
    ```c#  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-dependent property pages.  
        switch (propId)  
        {  
            . . . .  
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    //Add the Deployment property page.  
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");  
                }  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
> [!NOTE]
>  Tous les exemples de code fournis dans cette rubrique font partie d'un exemple plus complet, [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
## Voir aussi  
 [Sous\-types de projets](../extensibility/internals/project-subtypes.md)