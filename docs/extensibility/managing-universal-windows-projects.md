---
title: Gestion des projets Windows universels | Microsoft Docs
description: Pour prendre en charge les applications Windows universelles, les extensions Visual Studio qui gèrent les projets doivent être conscientes de la structure de projet d’application Windows universelle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8af418d8ffcaad18aca4497078f4e24f9bb679fd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090640"
---
# <a name="manage-universal-windows-projects"></a>Gérer les projets Windows universels

Les applications Windows universelles sont des applications qui ciblent à la fois Windows 8.1 et Windows Phone 8,1, ce qui permet aux développeurs d’utiliser du code et d’autres ressources sur les deux plateformes. Le code et les ressources partagés sont conservés dans un projet partagé, tandis que le code et les ressources spécifiques à la plateforme sont conservés dans des projets distincts, un pour Windows et l’autre pour Windows Phone. Pour plus d’informations sur les applications Windows universelles, consultez [applications Windows universelles](/windows/uwp/get-started/create-uwp-apps). Les extensions Visual Studio qui gèrent des projets doivent savoir que les projets d’application Windows universelle ont une structure qui diffère des applications à plateforme unique. Cette procédure pas à pas vous montre comment naviguer dans le projet partagé et gérer les éléments partagés.

## <a name="prerequisites"></a>Prérequis

À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Naviguer dans le projet partagé

1. Créez un projet VSIX C# nommé **TestUniversalProject**. (**Fichier**  >  **Nouveau**  >  **Projet** , puis   >  **extensibilité** C#  >  **package Visual Studio**). Ajoutez un modèle d’élément de projet de **commande personnalisé** (sur le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter**  >  **un nouvel élément**, puis accédez à **extensibilité**). Nommez le fichier **TestUniversalProject**.

2. Ajoutez une référence à *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* et à *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (dans la section **Extensions** ).

3. Ouvrez *TestUniversalProject. cs* et ajoutez les `using` directives suivantes :

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. Dans la `TestUniversalProject` classe, ajoutez un champ privé pointant vers la fenêtre **sortie** .

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Définissez la référence au volet de sortie à l’intérieur du constructeur TestUniversalProject :

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }

        // get a reference to the Output window
        output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Supprimez le code existant de la `ShowMessageBox` méthode :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Récupérez l’objet DTE, que nous utiliserons à plusieurs fins dans cette procédure pas à pas. En outre, assurez-vous qu’une solution est chargée lorsque l’utilisateur clique sur le bouton de menu.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Recherchez le projet partagé. Le projet partagé est un conteneur pur ; elle ne génère pas ou ne produit pas de sorties. La méthode suivante recherche le premier projet partagé dans la solution en recherchant l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet qui possède la fonctionnalité de projet partagé.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. Dans la `ShowMessageBox` méthode, génère la légende (nom du projet qui apparaît dans le **Explorateur de solutions**) du projet partagé.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Procurez-vous le projet de plateforme actif. Les projets de plateforme sont les projets qui contiennent du code et des ressources spécifiques à la plateforme. La méthode suivante utilise le nouveau champ <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> pour accéder au projet de plateforme actif.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. Dans la `ShowMessageBox` méthode, génère la légende du projet de plateforme actif.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                    MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
            }
        }
        else
        {
            MessageBox.Show("No solution is open");
        }
    }
    ```

12. Itérez au sein des projets de plateforme. La méthode suivante obtient tous les projets d’importation (plateforme) à partir du projet partagé.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Si l’utilisateur a ouvert un projet d’application Windows universelle C++ dans l’instance expérimentale, le code ci-dessus lève une exception. Il s’agit d’un problème connu. Pour éviter cette exception, remplacez le `foreach` bloc ci-dessus par ce qui suit :

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Dans la `ShowMessageBox` méthode, génère la légende de chaque projet de plateforme. Insérez le code suivant après la ligne qui génère la légende du projet de plateforme actif. Seuls les projets de plateforme chargés s’affichent dans cette liste.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Modifiez le projet de plateforme active. La méthode suivante définit le projet actif à l’aide de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A> .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Dans la `ShowMessageBox` méthode, modifiez le projet de plateforme active. Insérez ce code à l’intérieur du `foreach` bloc.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Essayez maintenant. Appuyez sur F5 pour lancer l’instance expérimentale. Créez un projet d’application de concentrateur universel C# dans l’instance expérimentale (dans la boîte de dialogue **nouveau projet** , dans **Visual C#**,  >    >    >    >  **application concentrateur** universel Windows 8 Windows 8). Une fois la solution chargée, accédez au menu **Outils** et cliquez sur **appeler TestUniversalProject**, puis vérifiez le texte dans le volet **sortie** . Un résultat tel que celui-ci doit s’afficher :

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gérer les éléments partagés dans le projet de plateforme

1. Recherchez les éléments partagés dans le projet de plateforme. Les éléments du projet partagé s’affichent dans le projet de plateforme en tant qu’éléments partagés. Vous ne pouvez pas les voir dans le **Explorateur de solutions**, mais vous pouvez parcourir la hiérarchie de projet pour les Rechercher. La méthode suivante parcourt la hiérarchie et collecte tous les éléments partagés. Il renvoie éventuellement la légende de chaque élément,. Les éléments partagés sont identifiés par la nouvelle propriété <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem> .

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
        }
    }
    ```

2. Dans la `ShowMessageBox` méthode, ajoutez le code suivant pour parcourir les éléments de la hiérarchie du projet de plateforme. Insérez-le dans le `foreach` bloc.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lire les éléments partagés. Les éléments partagés apparaissent dans le projet de plateforme en tant que fichiers liés masqués, et vous pouvez lire toutes les propriétés en tant que fichiers liés ordinaires. Le code suivant lit le chemin d’accès complet du premier élément partagé.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Essayez maintenant. Appuyez sur **F5** pour lancer l’instance expérimentale. Créer un projet d’application de concentrateur universel C# dans l’instance expérimentale (dans la boîte de dialogue **nouveau projet** , application de   >    >  concentrateur universel Windows **Windows 8** Visual C#  >    >  ) accédez au menu **Outils** et cliquez sur **appeler TestUniversalProject**, puis vérifiez le texte dans le volet de **sortie** . Un résultat tel que celui-ci doit s’afficher :

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Détecter les modifications dans les projets de plateforme et les projets partagés

1. Vous pouvez utiliser des événements de hiérarchie et de projet pour détecter les modifications apportées aux projets partagés, comme vous le feriez pour les projets de plateforme. Toutefois, les éléments de projet dans le projet partagé ne sont pas visibles, ce qui signifie que certains événements ne se déclenchent pas lorsque des éléments de projet partagés sont modifiés.

    Considérez la séquence d’événements lorsqu’un fichier d’un projet est renommé :

   1. Le nom de fichier est modifié sur le disque.

   2. Le fichier projet est mis à jour pour inclure le nouveau nom du fichier.

      Les événements de hiérarchie (par exemple, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> ) suivent généralement les modifications affichées dans l’interface utilisateur, comme dans le **Explorateur de solutions**. Les événements de hiérarchie considèrent qu’une opération de modification de nom de fichier consiste à supprimer un fichier, puis à ajouter un fichier. Toutefois, lorsque des éléments invisibles sont modifiés, le système d’événements de la hiérarchie déclenche un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événement, mais pas un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événement. Par conséquent, si vous renommez un fichier dans un projet de plateforme, vous recevez à la fois <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> , mais si vous renommez un fichier dans un projet partagé, vous recevez uniquement <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> .

      Pour suivre les modifications apportées aux éléments de projet, vous pouvez gérer les événements d’élément de projet DTE (ceux qui se trouvent dans <xref:EnvDTE.ProjectItemsEventsClass> ). Toutefois, si vous gérez un grand nombre d’événements, vous pouvez obtenir de meilleures performances pour gérer les événements dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> . Dans cette procédure pas à pas, nous affichons uniquement les événements de hiérarchie et les événements DTE. Dans cette procédure, vous ajoutez un écouteur d’événements à un projet partagé et à un projet de plateforme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plateforme, vous pouvez voir les événements qui sont déclenchés pour chaque opération de changement de nom.

      Dans cette procédure, vous ajoutez un écouteur d’événements à un projet partagé et à un projet de plateforme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plateforme, vous pouvez voir les événements qui sont déclenchés pour chaque opération de changement de nom.

2. Ajoutez un écouteur d’événements. Ajoutez un nouveau fichier de classe au projet et appelez-le *HierarchyEventListener. cs*.

3. Ouvrez le fichier *HierarchyEventListener. cs* et ajoutez les directives d’utilisation suivantes :

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Faire en sorte que la `HierarchyEventListener` classe implémente <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implémentez les membres de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents> , comme dans le code ci-dessous.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Dans la même classe, ajoutez un autre gestionnaire d’événements pour l’événement DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> , qui se produit chaque fois qu’un élément de projet est renommé.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Inscrivez-vous aux événements de hiérarchie. Vous devez vous inscrire séparément pour chaque projet que vous suivez. Ajoutez le code suivant dans `ShowMessageBox` , un pour le projet partagé et l’autre pour l’un des projets de plateforme.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Inscrivez-vous à l’événement d’élément de projet DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> . Ajoutez le code suivant après avoir raccordé le deuxième écouteur.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modifiez l’élément partagé. Vous ne pouvez pas modifier des éléments partagés dans un projet de plateforme. au lieu de cela, vous devez les modifier dans le projet partagé qui est le propriétaire réel de ces éléments. Vous pouvez obtenir l’ID d’élément correspondant dans le projet partagé avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> , en lui donnant le chemin d’accès complet de l’élément partagé. Vous pouvez ensuite modifier l’élément partagé. La modification est propagée aux projets de plateforme.

    > [!IMPORTANT]
    > Vous devez déterminer si un élément de projet est un élément partagé avant de le modifier.

     La méthode suivante modifie le nom d’un fichier d’élément de projet.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Appelez cette méthode après tout l’autre code dans `ShowMessageBox` pour modifier le nom de fichier de l’élément dans le projet partagé. Insérez ceci après le code qui obtient le chemin d’accès complet de l’élément dans le projet partagé.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Générez et exécutez le projet. Créez une application de concentrateur universel C# dans l’instance expérimentale, accédez au menu **Outils** et cliquez sur **appeler TestUniversalProject** et vérifiez le texte dans le volet de sortie général. Le nom du premier élément dans le projet partagé (nous pensons qu’il s’agit du fichier *app. Xaml* ) doit être modifié. vous devez voir que l' <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> événement a été déclenché. Dans ce cas, étant donné que si vous renommez *app. Xaml* , *app. Xaml. cs* est également renommé, vous devriez voir quatre événements (deux pour chaque projet de plateforme). (Les événements DTE n’effectuent pas le suivi des éléments dans le projet partagé.) Vous devez voir deux <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événements (un pour chacun des projets de plateforme), mais aucun <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événement.

12. Essayez à présent de renommer un fichier dans un projet de plateforme, et vous pouvez voir la différence dans les événements qui se sont déclenchés. Ajoutez le code suivant dans `ShowMessageBox` après l’appel à `ModifyFileName` .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Générez et exécutez le projet. Créez un projet C# universel dans l’instance expérimentale, accédez au menu **Outils** et cliquez sur **appeler TestUniversalProject** et vérifiez le texte dans le volet de sortie général. Une fois que le fichier du projet de plateforme a été renommé, vous devez voir un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événement et un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événement. Étant donné que la modification du fichier ne provoquait pas la modification d’autres fichiers, et étant donné que les modifications apportées aux éléments d’un projet de plateforme ne sont pas propagées en tout lieu, il n’y a qu’un seul de ces événements.