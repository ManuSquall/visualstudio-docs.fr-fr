---
title: "&#201;tendre le filtre de l’Explorateur de solutions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "L’Explorateur de solutions, extension"
  - "extensibilité (Visual Studio), projets et solutions"
ms.assetid: df976c76-27ec-4f00-ab6d-a26a745dc6c7
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# &#201;tendre le filtre de l’Explorateur de solutions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez étendre **l’Explorateur de solutions** fonctionnalité pour afficher ou masquer les différents fichiers de filtre. Par exemple, vous pouvez créer un filtre qui présente uniquement classe factory fichiers c\# dans les **l’Explorateur de solutions**, comme le montre cette procédure pas à pas.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
### Créer un Package Visual Studio  
  
1.  Créez un projet VSIX nommé `FileFilter`. Ajouter un modèle d’élément commande personnalisée nommé **FileFilter**. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Ajoutez une référence à `System.ComponentModel.Composition` et `Microsoft.VisualStudio.Utilities`.  
  
3.  Afficher la commande de menu sur le **l’Explorateur de solutions** barre d’outils. Ouvrez le fichier FileFilterPackage.vsct.  
  
4.  Modifier la `<Button>` bloc pour les éléments suivants :  
  
    ```xml  
    <Button guid="guidFileFilterPackageCmdSet" id="FileFilterId" priority="0x0400" type="Button">  
        <Parent guid="guidSHLMainMenu" id="IDG_VS_TOOLBAR_PROJWIN_FILTERS" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <Strings>  
            <ButtonText>FileNameFilter</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
### Mettre à jour le fichier manifeste  
  
1.  Dans le fichier source.extension.vsixmanifest, ajoutez un élément multimédia qui est un composant MEF.  
  
2.  Sur le **actifs** choisir le **nouveau** bouton.  
  
3.  Dans le **Type** choisissez **Microsoft.VisualStudio.MefComponent**.  
  
4.  Dans le **Source** choisissez **un projet dans la solution actuelle**.  
  
5.  Dans le **projet** choisissez **FileFilter**, puis choisissez le **OK** bouton.  
  
### Ajoutez le Code de filtre  
  
1.  Ajoutez des GUID dans le fichier FileFilterPackageGuids.cs :  
  
    ```c#  
    public const string guidFileFilterPackageCmdSetString = "00000000-0000-0000-0000-00000000"; // get your GUID from the .vsct file  
    public const int FileFilterId = 0x100;  
    ```  
  
2.  Ajoutez un fichier de classe au projet FileFilter nommé FileNameFilter.cs.  
  
3.  Remplacez l’espace de noms vide et le vide par le code ci\-dessous.  
  
     Le `Task<IReadOnlyObservableSet> GetIncludedItemsAsync(IEnumerable<IVsHierarchyItem rootItems)` méthode accepte la collection qui contient la racine de la solution \(`rootItems`\) et retourne la collection d’éléments à inclure dans le filtre.  
  
     Le `ShouldIncludeInFilter` méthode filtre les éléments de la **l’Explorateur de solutions** hiérarchie basée à condition que vous spécifiez.  
  
    ```c#  
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
  
4.  Dans FileFilter.cs, supprimez le code de positionnement et la gestion des commandes à partir du constructeur FileFilter. Le résultat doit ressembler à ceci :  
  
    ```c#  
    private FileFilter(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException("package");  
        }  
  
        this.package = package;  
    }  
    ```  
  
     Supprimez la méthode ShowMessageBox\(\).  
  
5.  Dans FileFilterPackage, cs, remplacez le code dans la méthode par le code suivant :  
  
    ```c#  
    protected override void Initialize()  
    {  
        Debug.WriteLine (string.Format(CultureInfo.CurrentCulture, "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
    }  
    ```  
  
### Tester votre Code  
  
1.  Générez et exécutez le projet. Une deuxième instance de Visual Studio s’affiche. Il s’agit de l’instance expérimentale.  
  
2.  Dans l’instance expérimentale de Visual Studio, ouvrez un projet c\#.  
  
3.  Recherchez le bouton que vous avez ajouté dans la barre d’outils de l’Explorateur de solutions. Il doit être le quatrième bouton de gauche.  
  
4.  Lorsque vous cliquez sur le bouton, tous les fichiers doivent être filtrés, et vous devez voir « tous les éléments ont été filtrées à partir de la vue. » dans l’Explorateur de solutions.