---
title: L’enregistrement des données dans les fichiers projet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 35514385a4ed1d28052ebb21d12ed0b053dd52dc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="saving-data-in-project-files"></a>L’enregistrement des données dans les fichiers projet
Un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier projet. Managed Package Framework (MPF) fournit deux interfaces pour accomplir cette tâche :  
  
-   Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interface permet d’accéder aux valeurs de propriété à partir de la **MSBuild** section du fichier projet. Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> peut être appelée par n’importe quel utilisateur chaque fois que l’utilisateur doit charger ou enregistrer génèrent des données associées.  
  
-   Le <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> est utilisé pour conserver les données connexes de build non XML de forme libre. Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sont appelées par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chaque fois que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doivent être conservés non-génération des données connexes dans le fichier projet.  
  
 Pour plus d’informations sur la façon de conserver build et non-génération des données connexes, consultez [persistance des données dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## <a name="saving-and-retrieving-build-related-data"></a>Enregistrement et récupération de génération des données liées  
  
#### <a name="to-save-a-build-related-data-in-the-project-file"></a>Pour enregistrer une version des données liées dans le fichier projet  
  
-   Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode pour enregistrer un chemin d’accès complet du fichier projet.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string newFullPath = GetNewFullPath();  
    // Set a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));  
    ```  
  
#### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Pour récupérer la génération des données liées à partir du fichier de projet  
  
-   Appelez le <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> méthode pour récupérer un chemin d’accès complet du fichier projet.  
  
    ```  
    private SpecializedProject project;  
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;  
    string fullPath;  
    // Get a full path of the project file.  
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(  
        "MSBuildProjectDirectory",  
        String.Empty,  
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));  
    ```  
  
## <a name="saving-and-retrieving-non-build-related-data"></a>L’enregistrement et la récupération non-génération des données associées  
  
#### <a name="to-save-non-build-related-data-in-the-project-file"></a>Pour enregistrer la build non des données liées dans le fichier projet  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> méthode pour déterminer si un fragment XML a été modifiée depuis le dernier est enregistré dans son fichier en cours.  
  
    ```  
    public int IsFragmentDirty(uint storage, out int pfDirty)  
    {  
        pfDirty = 0;  
        switch (storage)  
        {  
            case (uint)_PersistStorageType.PST_PROJECT_FILE:  
            {  
                if (isDirty)  
                    pfDirty |= 1;  
                break;  
            }  
            case (uint)_PersistStorageType.PST_USER_FILE:  
            {  
                // We do not store anything in the user file.  
                break;  
            }  
        }  
  
        // Forward the call to inner flavor(s)   
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);  
  
        return VSConstants.S_OK;  
  
    }  
    ```  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> méthode pour enregistrer les données XML dans le fichier projet.  
  
    ```  
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)  
    {  
        pbstrXMLFragment = null;  
  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Create XML for our data.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode root = doc.CreateElement(this.GetType().Name);  
  
                    XmlNode node = doc.CreateElement(targetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));  
                    root.AppendChild(node);  
  
                    node = doc.CreateElement(updateTargetsTag);  
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));  
                    root.AppendChild(node);  
  
                    doc.AppendChild(root);  
                    // Get XML fragment representing our data  
                    pbstrXMLFragment = doc.InnerXml;  
  
                    if (fClearDirty != 0)  
                        isDirty = false;  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
#### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Pour récupérer des données connexes de build non dans le fichier projet  
  
1.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> méthode pour initialiser les propriétés d’extension de projet et d’autres données indépendant de la build. Cette méthode est appelée si aucune donnée de configuration XML présente dans le fichier projet.  
  
    ```  
    public int InitNew(ref Guid guidFlavor, uint storage)  
    {  
        //Return,if it is our guid.  
        if (IsMyFlavorGuid(ref guidFlavor))  
            return VSConstants.S_OK;  
  
        //Forward the call to inner flavor(s).  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);  
  
        return VSConstants.S_OK;  
    ```  
  
2.  Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> méthode pour charger les données XML à partir du fichier projet.  
  
    ```  
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)  
    {  
        if (IsMyFlavorGuid(ref guidFlavor))  
        {  
            switch (storage)  
            {  
                case (uint)_PersistStorageType.PST_PROJECT_FILE:  
                {  
                    // Load our data from the XML fragment.  
                    XmlDocument doc = new XmlDocument();  
                    XmlNode node = doc.CreateElement(this.GetType().Name);  
                    node.InnerXml = pszXMLFragment;  
                    if (node == null  
                        || node.FirstChild == null  
                        || node.FirstChild.ChildNodes.Count == 0  
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)  
                        break;  
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;  
  
                    if (node.FirstChild.ChildNodes.Count <= 1  
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)  
                        break;  
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);  
                    break;  
                }  
                case (uint)_PersistStorageType.PST_USER_FILE:  
                {  
                    // We do not store anything in the user file.  
                    break;  
                }  
            }  
        }  
  
        // Forward the call to inner flavor(s)  
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)  
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);  
  
        return VSConstants.S_OK;  
    }  
    ```  
  
> [!NOTE]
>  Tous les exemples de code fournis dans cette rubrique font partie d’un exemple plus complet dans [exemples d’extensibilité Visual Studio](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>Voir aussi  
 [Données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)