---
title: Gestion de projets de Windows universelle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28f6cf6424799cfbe68734d8fa077eea3c2b2c1a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047396"
---
# <a name="manage-universal-windows-projects"></a>Gérer les projets Windows universel

Les applications Windows universelles sont des applications qui ciblent Windows 8.1 et Windows Phone 8.1, ce qui permet aux développeurs d’utiliser le code et autres ressources sur les deux plateformes. Le code partagé et les ressources sont conservées dans un projet partagé, tandis que le code spécifique à la plateforme et les ressources sont conservés dans des projets distincts, un pour Windows et l’autre pour Windows Phone. Pour plus d’informations sur les applications Windows universelles, consultez [les applications Windows universelles](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Les extensions de Visual Studio qui gèrent les projets devraient être conscient que les projets d’application Windows universelles ont une structure qui diffère des applications de plateforme unique. Cette procédure pas à pas vous montre comment naviguer dans le projet partagé et de gérer les éléments partagés.

## <a name="prerequisites"></a>Prérequis

À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Parcourir le projet partagé

1. Créez un projet VSIX c# nommé **TestUniversalProject**. (**Fichier** > **nouveau** > **projet** , puis **c#**  >   **Extensibilité** > **Package Visual Studio**). Ajouter un **commande personnalisée** modèle d’élément de projet (sur le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **ajouter** > **un nouvel élément** , puis accédez à **extensibilité**). Nommez le fichier **TestUniversalProject**.

2. Ajoutez une référence à *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* et *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (dans le **Extensions** section).

3. Ouvrez *TestUniversalProject.cs* et ajoutez le code suivant `using` instructions :

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

4. Dans le `TestUniversalProject` classe ajouter un champ privé qui pointe vers le **sortie** fenêtre.

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Définissez la référence dans le volet de sortie à l’intérieur du constructeur de TestUniversalProject :

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

6. Supprimez le code existant à partir de la `ShowMessageBox` méthode :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Obtenez l’objet DTE, que nous utiliserons pour plusieurs objectifs différents dans cette procédure pas à pas. En outre, assurez-vous qu’une solution est chargée de la suite d’un clic sur le bouton de menu.

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

8. Recherchez le projet partagé. Le projet partagé est un conteneur pur ; Il ne pas créer ou produire des sorties. La méthode suivante recherche le premier projet partagé dans la solution en recherchant le <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objet qui a la possibilité de projet partagé.

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

9. Dans le `ShowMessageBox` (méthode), la légende de sortie (le nom du projet qui s’affiche dans le **l’Explorateur de solutions**) du projet partagé.

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

10. Obtenir le projet de plateforme active. Projets de plateforme sont les projets qui contiennent des ressources et le code spécifique à la plateforme. La méthode suivante utilise le nouveau champ <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> pour obtenir le projet de plateforme active.

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

11. Dans le `ShowMessageBox` (méthode), la légende du projet de plateforme active de sortie.

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
                return;
            }
        }
        else
            {
                MessageBox.Show("No solution is open");
                return;
            }
        }
    }
    ```

12. Itérer dans les projets de plateforme. La méthode suivante obtient tous les projets (plate-forme) importation à partir du projet partagé.

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
    > Si l’utilisateur a ouvert un projet d’application Windows universelle C++ dans l’instance expérimentale, le code ci-dessus lève une exception. Il s'agit d'un problème connu. Pour éviter l’exception, remplacez la `foreach` block ci-dessus par le code suivant :

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Dans le `ShowMessageBox` (méthode), la légende de chaque projet de plateforme de sortie. Insérez le code suivant après la ligne qui génère la légende du projet de plateforme active. Seuls les projets de plateforme qui sont chargés apparaissent dans cette liste.

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

14. Modifier le projet de plateforme active. La méthode suivante définit le projet actif à l’aide <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Dans le `ShowMessageBox` (méthode), modifiez le projet de plateforme active. Insérez ce code dans le `foreach` bloc.

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

16. Essayez maintenant. Appuyez sur F5 pour lancer l’instance expérimentale. Créer un projet d’application universelle hub c# dans l’instance expérimentale (dans le **nouveau projet** boîte de dialogue, **Visual C#** > **Windows**  >   **Windows 8** > **universelle** > **application Hub**). Une fois la solution est chargée, accédez à la **outils** menu et cliquez sur **TestUniversalProject appeler**, puis vérifiez le texte le **sortie** volet. Vous devriez voir quelque chose qui ressemble à ce qui suit :

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gérer les éléments partagés dans le projet de plateforme

1. Rechercher les éléments partagés dans le projet de plateforme. Les éléments dans le projet partagé s’affichent dans le projet de plateforme en tant qu’éléments partagés. Vous ne pouvez pas afficher ces journaux dans le **l’Explorateur de solutions**, mais vous pouvez parcourir la hiérarchie de projet pour les trouver. La méthode suivante parcourt la hiérarchie et collecte tous les éléments partagés. Si vous le souhaitez la légende de chaque élément, la sortie. Les éléments partagés sont identifiés par la nouvelle propriété <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>.

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

2. Dans le `ShowMessageBox` (méthode), ajoutez le code suivant pour guider les éléments de hiérarchie de projet de plateforme. Insérez-le dans le `foreach` bloc.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lire les éléments partagés. Les éléments partagés s’affichent dans le projet de plateforme en tant que fichiers liés masquées, et vous pouvez lire toutes les propriétés en tant que fichiers liés ordinaires. Le code suivant lit le chemin d’accès complet du premier élément partagé.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Essayez maintenant. Appuyez sur **F5** pour lancer l’instance expérimentale. Créer un C# projet d’application universelle hub dans l’instance expérimentale (dans le **nouveau projet** boîte de dialogue, **Visual C#**   >  **Windows**  >  **Windows 8** > **universelle** > **application Hub**) accédez à la **outils** menu et cliquez sur  **Appeler TestUniversalProject**, puis vérifiez le texte le **sortie** volet. Vous devriez voir quelque chose qui ressemble à ce qui suit :

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Détecter les modifications dans les projets de plateforme et de projets partagés

1. Vous pouvez utiliser des événements de hiérarchie et de projet pour détecter des modifications dans les projets partagés, comme vous pouvez le faire pour les projets de plateforme. Toutefois, les éléments de projet dans le projet partagé ne sont pas visibles, ce qui signifie que certains événements ne se déclenchent pas lorsque les éléments de projet partagé sont modifiés.

    Examinez la séquence d’événements lorsqu’un fichier dans un projet est renommé :

   1. Le nom de fichier est modifié sur le disque.

   2. Le fichier projet est mis à jour pour inclure le nouveau nom du fichier.

      Événements de hiérarchie (par exemple, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>) généralement le suivi des modifications affichées dans l’interface utilisateur, comme dans le **l’Explorateur de solutions**. Événements de hiérarchie prendre en compte une opération de changement de nom de fichier se composer d’une suppression de fichier, puis un ajout de fichier. Toutefois, lorsque les éléments invisibles sont modifiés, le système d’événements de hiérarchie déclenche une <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événement mais pas un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événement. Par conséquent, si vous renommez un fichier dans un projet de plateforme, vous obtenez deux <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> et <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>, mais si vous renommez un fichier dans un projet partagé, vous obtenez uniquement <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>.

      Pour effectuer le suivi des modifications dans les éléments de projet, vous pouvez gérer les événements d’élément de projet DTE (ceux trouvés dans <xref:EnvDTE.ProjectItemsEventsClass>). Toutefois, si vous gérez un grand nombre d’événements, vous pouvez obtenir de meilleures performances, gestion des événements dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>. Dans cette procédure pas à pas, nous montrons uniquement les événements de la hiérarchie et les événements DTE. Dans cette procédure, vous ajoutez un écouteur d’événements à un projet partagé et un projet de plateforme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plateforme, vous pouvez voir les événements qui sont déclenchés pour chaque opération de changement de nom.

      Dans cette procédure, vous ajoutez un écouteur d’événements à un projet partagé et un projet de plateforme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plateforme, vous pouvez voir les événements qui sont déclenchés pour chaque opération de changement de nom.

2. Ajouter un écouteur d’événements. Ajoutez un nouveau fichier de classe au projet et appelez-la *HierarchyEventListener.cs*.

3. Ouvrez le *HierarchyEventListener.cs* fichier et ajoutez le code suivant à l’aide d’instructions :

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Avoir le `HierarchyEventListener` implémentent <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implémenter les membres de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>, comme dans le code ci-dessous.

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

6. Dans la même classe, ajoutez un autre gestionnaire d’événements pour l’événement DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>, ce qui se produit chaque fois qu’un élément de projet est renommé.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Inscrivez-vous pour les événements de hiérarchie. Vous devez vous inscrire séparément pour chaque projet que vous effectuez le suivi. Ajoutez le code suivant dans `ShowMessageBox`, un pour le projet partagé et l’autre pour un des projets de plateforme.

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

8. S’inscrire pour l’événement d’élément de projet DTE <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>. Ajoutez le code suivant, une fois que vous raccorder le deuxième écouteur.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modifier l’élément partagé. Vous ne pouvez pas modifier les éléments partagés dans un projet de plateforme. au lieu de cela, vous devez les modifier dans le projet partagé qui est le propriétaire réel de ces éléments. Vous pouvez obtenir l’ID d’élément correspondant dans le projet partagé avec <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>, en lui attribuant un chemin d’accès complet de l’élément partagé. Vous pouvez ensuite modifier l’élément partagé. La modification est propagée vers les projets de plateforme.

    > [!IMPORTANT]
    > Vous devez rechercher si un élément de projet est un élément partagé avant de le modifier.

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

10. Appelez cette méthode une fois toutes les autres codes de `ShowMessageBox` pour modifier le nom du fichier l’élément dans le projet partagé. Insérez ceci après le code qui obtient le chemin d’accès complet de l’élément dans le projet partagé.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Générez et exécutez le projet. Créer une application de hub universel c# dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **TestUniversalProject appeler**et vérifiez le texte dans le volet de sortie général. Le nom du premier élément dans le projet partagé (il doit être le *App.xaml* fichier) doit être modifiée, et vous devez voir que le <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> événement a été déclenché. Dans ce cas, depuis la modification du nom *App.xaml* provoque *App.xaml.cs* pour être également renommé, vous devez voir quatre événements (deux pour chaque projet de plateforme). (Les événements DTE ne pas me suivre les éléments dans le projet partagé.) Vous devriez voir deux <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événements (une pour chacun des projets de plateforme), mais pas <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événements.

12. Maintenant essayez de renommer un fichier dans un projet de plateforme, et vous pouvez voir la différence dans les événements qui sont déclenchées. Ajoutez le code suivant dans `ShowMessageBox` après l’appel à `ModifyFileName`.

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

13. Générez et exécutez le projet. Créer un projet universel c# dans l’instance expérimentale, accédez à la **outils** menu et cliquez sur **TestUniversalProject appeler**et vérifiez le texte dans le volet de sortie général. Une fois que le fichier dans le projet de plateforme est renommé, vous devez voir les deux un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> événement et un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> événement. Parce que la modification du fichier à l’origine aucun autre fichier à modifier, et dans la mesure où les modifications apportées aux éléments dans un projet de plateforme ne sont propagées de n’importe où, il existe un seul chaque de ces événements.
