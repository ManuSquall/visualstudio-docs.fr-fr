---
title: Étendre le filtre Solution Explorer (fr) Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711573"
---
# <a name="extend-the-solution-explorer-filter"></a>Étendre le filtre Solution Explorer
Vous pouvez étendre la fonctionnalité de filtre **Solution Explorer** pour afficher ou masquer différents fichiers. Par exemple, vous pouvez créer un filtre qui n’affiche que des fichiers d’usine de classe C dans la **Solution Explorer**, comme le démontre cette procédure pas à pas.

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-package-project"></a>Créer un projet de forfait Visual Studio

1. Créer un projet `FileFilter`VSIX nommé . Ajoutez un modèle d’élément de commande personnalisé nommé **FileFilter**. Pour plus d’informations, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Ajouter une `System.ComponentModel.Composition` référence `Microsoft.VisualStudio.Utilities`à et .

3. Faites apparaître la commande du menu sur la barre d’outils **Solution Explorer.** Ouvrez le fichier *FileFilterPackage.vsct.*

4. Modifier `<Button>` le bloc pour ce qui suit :

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

1. Dans le fichier *source.extension.vsixmanifest,* ajoutez un actif qui est un composant MEF.

2. Sur l’onglet **Actifs,** choisissez le **nouveau** bouton.

3. Dans le domaine **Type,** choisissez **Microsoft.VisualStudio.MefComponent**.

4. Dans le domaine **Source,** choisissez **un projet dans la solution actuelle.**

5. Dans le domaine **du projet,** choisissez **FileFilter,** puis choisissez le bouton **OK.**

### <a name="add-the-filter-code"></a>Ajouter le code de filtre

1. Ajoutez quelques TME au fichier *FileFilterPackageGuids.cs* :

    ```csharp
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file
    public const int FileFilterId = 0x100;
    ```

2. Ajoutez un fichier de classe au projet FileFilter nommé *FileNameFilter.cs*.

3. Remplacez l’espace nom vide et la classe vide par le code ci-dessous.

     La `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` méthode prend la collection qui contient`rootItems`la racine de la solution ( ) et retourne la collection d’articles à inclure dans le filtre.

     La `ShouldIncludeInFilter` méthode filtre les éléments de la hiérarchie **Solution Explorer** en fonction de l’état que vous spécifiez.

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

4. Dans *FileFilter.cs,* supprimez le code de placement et de manutention de commande du constructeur FileFilter. Le résultat devrait ressembler à ceci:

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

     Enlevez la `ShowMessageBox()` méthode ainsi.

5. Dans *FileFilterPackage.cs*, remplacer le code `Initialize()` dans la méthode par ce qui suit:

    ```csharp
    protected override void Initialize()
    {
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));
        base.Initialize();
    }
    ```

### <a name="test-your-code"></a>Test de votre code

1. Générez et exécutez le projet. Une seconde instance de Visual Studio apparaît. C’est ce qu’on appelle l’instance expérimentale.

2. Dans le cas expérimental de Visual Studio, ouvrez un projet C.

3. Recherchez le bouton que vous avez ajouté sur la barre d’outils **Solution Explorer.** Il devrait être le quatrième bouton de la gauche.

4. Lorsque vous cliquez sur le bouton, tous les fichiers doivent être filtrés, et vous devez voir **tous les éléments ont été filtrés de la vue.** dans la **Solution Explorer**.
