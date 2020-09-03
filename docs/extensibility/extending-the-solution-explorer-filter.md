---
title: Extension du filtre de Explorateur de solutions | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Solution Explorer, extending
- extensibility [Visual Studio], projects and solutions
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af0824edd4188481bec8c0703d71043354f5dbcc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711573"
---
# <a name="extend-the-solution-explorer-filter"></a>Étendre le filtre de Explorateur de solutions
Vous pouvez étendre **Explorateur de solutions** fonctionnalité de filtre pour afficher ou masquer des fichiers différents. Par exemple, vous pouvez créer un filtre qui affiche uniquement les fichiers de fabrique de classe C# dans le **Explorateur de solutions**, comme le montre cette procédure pas à pas.

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Créer un projet de package Visual Studio

1. Créez un projet VSIX nommé `FileFilter` . Ajoutez un modèle d’élément de commande personnalisé nommé **FileFilter**. Pour plus d’informations, consultez [créer une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Ajoutez une référence à `System.ComponentModel.Composition` et `Microsoft.VisualStudio.Utilities` .

3. Faites apparaître la commande de menu dans la barre d’outils **Explorateur de solutions** . Ouvrez le fichier *FileFilterPackage. vsct* .

4. Remplacez le `<Button>` bloc par ce qui suit :

    ```xml
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />
        <Icon guid="guidImages" id="bmpPic1" />
        <Strings>
            <ButtonText>FileNameFilter</ButtonText>
        </Strings>
    </Button>
    ```

### <a name="update-the-manifest-file"></a>Mettre à jour le fichier manifeste

1. Dans le fichier *source. extension. vsixmanifest* , ajoutez une ressource qui est un composant MEF.

2. Sous l’onglet **ressources** , cliquez sur le bouton **nouveau** .

3. Dans le champ **type** , choisissez **Microsoft. VisualStudio. MEFComponent**.

4. Dans le champ **source** , choisissez **un projet dans la solution actuelle**.

5. Dans le champ **projet** , choisissez **FiltreFichier**, puis cliquez sur le bouton **OK** .

### <a name="add-the-filter-code"></a>Ajouter le code de filtre

1. Ajoutez des GUID au fichier *FileFilterPackageGuids.cs* :

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Ajoutez un fichier de classe au projet FileFilter nommé *FileNameFilter.cs*.

3. Remplacez l’espace de noms vide et la classe vide par le code ci-dessous.

     La `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` méthode prend la collection qui contient la racine de la solution ( `rootItems` ) et retourne la collection d’éléments à inclure dans le filtre.

     La `ShouldIncludeInFilter` méthode filtre les éléments de la hiérarchie **Explorateur de solutions** en fonction de la condition que vous spécifiez.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Text.RegularExpressions;
    using System.Threading.Tasks;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using Microsoft.VisualStudio.Shell;

    namespace FileFilter
    {
        // Implements ISolutionTreeFilterProvider. The SolutionTreeFilterProvider attribute declares it as a MEF component
        [SolutionTreeFilterProvider(FileFilterPackageGuids.guidFileFilterPackageCmdSetString, (uint)(FileFilterPackageGuids.FileFilterId))]
        public sealed class FileNameFilterProvider : HierarchyTreeFilterProvider
        {
            SVsServiceProvider svcProvider;
            IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

            // Constructor required for MEF composition
            [ImportingConstructor]
            public FileNameFilterProvider(SVsServiceProvider serviceProvider, IVsHierarchyItemCollectionProvider hierarchyCollectionProvider)
            {
                this.svcProvider = serviceProvider;
                this.hierarchyCollectionProvider = hierarchyCollectionProvider;
            }

            // Returns an instance of Create filter class.
            protected override HierarchyTreeFilter CreateFilter()
            {
                return new FileNameFilter(this.svcProvider, this.hierarchyCollectionProvider, FileNamePattern);
            }

            // Regex pattern for CSharp factory classes
            private const string FileNamePattern = @"\w*factory\w*(.cs$)";

            // Implementation of file filtering
            private sealed class FileNameFilter : HierarchyTreeFilter
            {
                private readonly Regex regexp;
                private readonly IServiceProvider svcProvider;
                private readonly IVsHierarchyItemCollectionProvider hierarchyCollectionProvider;

                public FileNameFilter(
                    IServiceProvider serviceProvider,
                    IVsHierarchyItemCollectionProvider hierarchyCollectionProvider,
                    string fileNamePattern)
                {
                    this.svcProvider = serviceProvider;
                    this.hierarchyCollectionProvider = hierarchyCollectionProvider;
                    this.regexp = new Regex(fileNamePattern, RegexOptions.IgnoreCase);
                }

                // Gets the items to be included from this filter provider.
                // rootItems is a collection that contains the root of your solution
                // Returns a collection of items to be included as part of the filter
                protected override async Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem> rootItems)
                {
                    IVsHierarchyItem root = HierarchyUtilities.FindCommonAncestor(rootItems);
                    IReadOnlyObservableSet<IVsHierarchyItem> sourceItems;
                    sourceItems = await hierarchyCollectionProvider.GetDescendantsAsync(
                                        root.HierarchyIdentity.NestedHierarchy,
                                        CancellationToken);

                    IFilteredHierarchyItemSet includedItems = await hierarchyCollectionProvider.GetFilteredHierarchyItemsAsync(
                        sourceItems,
                        ShouldIncludeInFilter,
                        CancellationToken);
                    return includedItems;
                }

                // Returns true if filters hierarchy item name for given filter; otherwise, false</returns>
                private bool ShouldIncludeInFilter(IVsHierarchyItem hierarchyItem)
                {
                    if (hierarchyItem == null)
                    {
                        return false;
                    }
                    return this.regexp.IsMatch(hierarchyItem.Text);
                }
            }
        }
    }

    ```

4. Dans *FileFilter.cs*, supprimez le placement de commande et le code de gestion du constructeur FileFilter. Le résultat doit ressembler à ceci :

    ```csharp
    private FileFilter(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;
    }
    ```

     Supprimez `ShowMessageBox()` également la méthode.

5. Dans *FileFilterPackage.cs*, remplacez le code dans la `Initialize()` méthode par le code suivant :

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Test de votre code

1. Générez et exécutez le projet. Une seconde instance de Visual Studio apparaît. C’est ce que l’on appelle l’instance expérimentale.

2. Dans l’instance expérimentale de Visual Studio, ouvrez un projet C#.

3. Recherchez le bouton que vous avez ajouté dans la barre d’outils **Explorateur de solutions** . Il doit s’agir du quatrième bouton à partir de la gauche.

4. Lorsque vous cliquez sur le bouton, tous les fichiers doivent être filtrés, et **tous les éléments ont été filtrés à partir de l’affichage.** dans le **Explorateur de solutions**.
