---
title: "Enregistrer les donn&#233;es dans les fichiers projet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "données (Visual Studio), l'enregistrement dans les fichiers projet"
  - "fichiers projet"
  - "fichiers de projet, l'enregistrement des données"
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Enregistrer les donn&#233;es dans les fichiers projet
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un sous\-type de projet peut enregistrer et récupérer des données spécifiques de sous\-type dans le fichier projet.  Managed package \(MPF\) fournit deux interfaces pour accomplir cette tâche :  
  
-   L'interface d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> autorise des valeurs de propriété d'accès de la section d' **MSBuild** du fichier projet.  Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> peuvent être appelées par tout utilisateur chaque fois que l'utilisateur doit charger ou enregistrer des données connexes de génération.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> est utilisé pour rendre persistantes les données liées de non\-génération dans le format libre XML.  Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sont appelées par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chaque fois que les besoins des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de rendre persistantes des données liées de non\-génération dans le fichier projet.  
  
 Pour plus d'informations sur la façon de rendre des données liées de génération et de non\-génération, consultez [Données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).  
  
## Le stockage et la récupération des données connexes de génération  
  
#### Pour enregistrer les données connexes de génération dans le fichier projet  
  
-   Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> pour enregistrer un chemin d'accès complet du fichier projet.  
  
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
  
#### Pour récupérer des données connexes de génération du fichier projet  
  
-   Appelez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> pour récupérer un chemin d'accès complet du fichier projet.  
  
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
  
## Le stockage et la récupération des données liées de non\-génération  
  
#### Pour enregistrer des données liées de non\-génération dans le fichier projet  
  
1.  Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> pour déterminer si un fragment XML a été modifié depuis lequel il a été en dernier stocké dans son fichier en cours.  
  
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
  
2.  Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> pour enregistrer les données XML dans le fichier projet.  
  
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
  
#### Pour récupérer des données liées de non\-génération dans le fichier projet  
  
1.  Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> pour initialiser les propriétés d'extension de projet et d'autres données génération\-indépendantes.  Cette méthode est appelée s'il n'existe pas de données de configuration XML actuelle dans le fichier projet.  
  
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
  
2.  Implémentez la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> pour charger les données XML du fichier projet.  
  
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
>  Tous les exemples de code fournis dans cette rubrique font partie d'un exemple plus complet, [Exemples d’extensibilité Visual Studio](../misc/vssdk-samples.md).  
  
## Voir aussi  
 [Données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)