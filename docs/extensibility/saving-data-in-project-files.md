---
title: Enregistrement des données dans les fichiers projet | Microsoft Docs
description: Découvrez les interfaces que le Managed package Framework fournit pour enregistrer et récupérer des données spécifiques aux sous-types dans le fichier projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5859fc9286a3e584c04ccacc1d8b8a35d98dea89
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904979"
---
# <a name="save-data-in-project-files"></a>Enregistrer des données dans les fichiers projet
Un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier projet. Managed package Framework (MPF) fournit deux interfaces pour accomplir cette tâche :

- L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interface permet à d’accéder aux valeurs de propriété à partir de la section **MSBuild** du fichier projet. Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> peuvent être appelées par n’importe quel utilisateur chaque fois que l’utilisateur a besoin de charger ou d’enregistrer des données liées à la génération.

- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>Est utilisé pour rendre persistantes les données non liées à la génération au format XML libre. Les méthodes fournies par <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> sont appelées par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] chaque fois que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] doit rendre persistantes les données non liées à la génération dans le fichier projet.

  Pour plus d’informations sur la façon de rendre persistants les données de build et non liées à la génération, consultez [rendre les données persistantes dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Enregistrer et récupérer des données liées à la génération

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Pour enregistrer les données relatives à la build dans le fichier projet

- Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> méthode pour enregistrer un chemin d’accès complet au fichier projet.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Pour récupérer les données liées à la génération à partir du fichier projet

- Appelez la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> méthode pour récupérer un chemin d’accès complet au fichier projet.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Enregistrer et récupérer des données non liées à la génération

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Pour enregistrer les données non liées à la génération dans le fichier projet

1. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> méthode pour déterminer si un fragment XML a été modifié depuis son dernier enregistrement dans son fichier actuel.

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

2. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> méthode pour enregistrer les données XML dans le fichier projet.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Pour récupérer les données non liées à la génération dans le fichier projet

1. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> méthode pour initialiser les propriétés d’extension de projet et d’autres données indépendantes de la génération. Cette méthode est appelée si aucune donnée de configuration XML n’est présente dans le fichier projet.

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

2. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> méthode pour charger les données XML à partir du fichier projet.

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
> Tous les exemples de code fournis dans cette rubrique sont des parties d’un exemple plus complet dans les [exemples VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Voir aussi
- [Conserver les données dans le fichier projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
