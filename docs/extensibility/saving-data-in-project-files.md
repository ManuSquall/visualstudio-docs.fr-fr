---
title: Enregistrement de données dans les fichiers de projets ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701355"
---
# <a name="save-data-in-project-files"></a>Enregistrer les données dans les fichiers de projets
Un sous-type de projet peut enregistrer et récupérer des données spécifiques au sous-type dans le fichier du projet. Le Cadre de paquet géré (MPF) fournit deux interfaces pour accomplir cette tâche :

- L’interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> permet d’accéder aux valeurs des propriétés à partir de la section **MSBuild** du fichier de projet. Les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> fournies par peuvent être appelées par n’importe quel utilisateur chaque fois que l’utilisateur a besoin de charger ou d’enregistrer des données connexes de construction.

- L’est <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> utilisé pour persister les données non-build connexes dans la forme libre XML. Les méthodes <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> fournies par [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sont appelées par chaque fois que les besoins doivent persister les données non-build connexes dans le fichier du projet.

  Pour plus d’informations sur la façon de continuer à construire et non-construire des données connexes, voir [les données Persist dans le fichier du projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Enregistrer et récupérer les données connexes

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Pour enregistrer une analyse des données dans le fichier du projet

- Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> la méthode pour enregistrer un chemin complet du fichier du projet.

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

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Pour récupérer les données connexes du fichier du projet

- Appelez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> la méthode pour récupérer un chemin complet du fichier du projet.

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

## <a name="save-and-retrieve-non-build-related-data"></a>Enregistrer et récupérer les données non-build connexes

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Pour enregistrer les données non-build connexes dans le fichier du projet

1. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> méthode pour déterminer si un fragment de XML a changé depuis qu’il a été enregistré pour la dernière fois dans son fichier actuel.

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

2. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> méthode pour enregistrer les données XML dans le fichier du projet.

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

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Récupérer les données non-build connexes dans le fichier du projet

1. Mettre <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> en œuvre la méthode pour initialiser les propriétés d’extension du projet et d’autres données indépendantes de la construction. Cette méthode est appelée s’il n’y a pas de données de configuration XML présentes dans le fichier du projet.

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

2. Implémentez la <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> méthode pour charger les données XML du fichier du projet.

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
> Tous les exemples de code fournis dans ce sujet sont des parties d’un exemple plus large dans [les échantillons VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Voir aussi
- [Données persistantes dans le fichier du projet MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
