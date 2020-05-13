---
title: Gestion des projets Windows Universels (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc6894bcfe3bfab3b0246d716b0bd85152ad17e2
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744934"
---
# <a name="manage-universal-windows-projects"></a>Gérer les projets Windows universels

Les applications Windows universelles sont des applications qui ciblent Windows 8.1 et Windows Phone 8.1, permettant aux développeurs d’utiliser du code et d’autres actifs sur les deux plates-formes. Le code et les ressources partagés sont conservés dans un projet partagé, tandis que le code et les ressources spécifiques à la plate-forme sont conservés dans des projets distincts, l’un pour Windows et l’autre pour Windows Phone. Pour plus d’informations sur les applications Windows universelles, voir [les applications Windows universelles](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). Les extensions Visual Studio qui gèrent des projets doivent être conscientes que les projets universels d’applications Windows ont une structure qui diffère des applications monoplateformes. Cette procédure pas à pas vous montre comment naviguer dans le projet partagé et gérer les éléments partagés.

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Naviguez dans le projet partagé

1. Créer un projet VSIX CMD nommé **TestUniversalProject**. (**Fichier** > **Nouveau** > **Projet,** puis C**Extensibility** >  **C#** > **Visual Studio Package**). Ajoutez un modèle d’élément de projet **Custom Command** (sur la **Solution Explorer**, cliquez à droite sur le nœud du projet et **sélectionnez Ajouter** > **un nouvel élément,** puis aller à **Extensibility**). Nommez le fichier **TestUniversalProject**.

2. Ajoutez une référence à *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* et *Microsoft.VisualStudio.Shell.Interop.14.0.DesignTime.dll* (dans la section **Extensions).**

3. Ouvrez *TestUniversalProject.cs* et ajoutez `using` les directives suivantes :

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

4. Dans `TestUniversalProject` la classe ajouter un champ privé pointant vers la fenêtre **de sortie.**

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Définissez la référence à la vitre à l’intérieur du constructeur TestUniversalProject :

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

6. Supprimer le code `ShowMessageBox` existant de la méthode :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Obtenez l’objet DTE, que nous utiliserons à plusieurs fins différentes dans cette procédure pas à pas. Aussi, assurez-vous qu’une solution est chargée lorsque le bouton du menu est cliqué.

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

8. Trouvez le projet partagé. Le projet partagé est un conteneur pur; il ne construit ni ne produit de sorties. La méthode suivante trouve le premier projet partagé <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> dans la solution en recherchant l’objet qui a la capacité de projet partagée.

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

9. Dans `ShowMessageBox` la méthode, la sortie de la légende (le nom du projet qui apparaît dans la **Solution Explorer**) du projet partagé.

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

10. Obtenez le projet de plate-forme active. Les projets de plate-forme sont les projets qui contiennent un code et des ressources spécifiques à la plate-forme. La méthode suivante utilise <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> le nouveau champ pour obtenir le projet de plate-forme active.

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

11. Dans `ShowMessageBox` la méthode, la sortie de la légende du projet de plate-forme active.

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

12. Itérer à travers les projets de plate-forme. La méthode suivante obtient tous les projets d’importation (plateforme) du projet partagé.

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
    > Si l’utilisateur a ouvert un projet d’application Windows universel CMD dans l’instance expérimentale, le code ci-dessus jette une exception. Il s'agit d'un problème connu. Pour éviter l’exception, remplacez le `foreach` bloc ci-dessus par les éléments suivants :

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. Dans `ShowMessageBox` la méthode, la sortie de la légende de chaque projet de plate-forme. Insérez le code suivant après la ligne qui produit la légende du projet de plate-forme active. Seuls les projets de plate-forme qui sont chargés apparaissent dans cette liste.

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

14. Modifier le projet de plate-forme active. La méthode suivante définit <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>le projet actif à l’aide de .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. Dans `ShowMessageBox` la méthode, changer le projet de plate-forme active. Insérez `foreach` ce code à l’intérieur du bloc.

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

16. Maintenant, essayez-le. Appuyez sur F5 pour lancer l’instance expérimentale. Créez un projet d’application de hub universel CMD dans l’exemple expérimental (dans la boîte de dialogue **du nouveau projet,** **Visual C'** > **Windows** > **Windows 8** > **Universal** > **Hub App**). Une fois la solution chargée, allez au menu **Tools** et cliquez sur **Invoke TestUniversalProject**, puis vérifiez le texte dans le volet **sortie.** Un résultat tel que celui-ci doit s’afficher :

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gérer les éléments partagés dans le projet de plate-forme

1. Trouvez les éléments partagés dans le projet de plate-forme. Les éléments du projet partagé apparaissent dans le projet de plate-forme sous forme d’éléments partagés. Vous ne pouvez pas les voir dans la **Solution Explorer**, mais vous pouvez marcher la hiérarchie du projet pour les trouver. La méthode suivante parcourt la hiérarchie et recueille tous les objets partagés. Il extrade optionnellement la légende de chaque article,. Les objets partagés sont <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>identifiés par la nouvelle propriété .

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

2. Dans `ShowMessageBox` la méthode, ajoutez le code suivant pour marcher les éléments de hiérarchie du projet de plate-forme. Insérez-le à l’intérieur du `foreach` bloc.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Lisez les articles partagés. Les éléments partagés apparaissent dans le projet de plate-forme sous forme de fichiers liés cachés, et vous pouvez lire toutes les propriétés en tant que fichiers liés ordinaires. Le code suivant lit le chemin complet du premier élément partagé.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Maintenant, essayez-le. Appuyez **sur F5** pour lancer l’instance expérimentale. Créez un projet d’application de hub universel CMD dans l’exemple expérimental (dans la boîte de dialogue **du nouveau projet,** **Visual C'** > **Windows** > **Windows 8** > **Universal** > **Hub App**) allez au menu **Tools** et cliquez sur **Invoke TestUniversalProject**, puis vérifiez le texte dans le volet **Sortie.** Un résultat tel que celui-ci doit s’afficher :

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

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Détecter les changements dans les projets de plate-forme et les projets partagés

1. Vous pouvez utiliser des événements de hiérarchie et de projet pour détecter les changements dans les projets partagés, tout comme vous le pouvez pour les projets de plate-forme. Toutefois, les éléments du projet dans le projet partagé ne sont pas visibles, ce qui signifie que certains événements ne s’enflammerent pas lorsque des éléments de projet partagés sont modifiés.

    Considérez la séquence des événements lorsqu’un fichier d’un projet est renommé :

   1. Le nom du fichier est changé sur disque.

   2. Le dossier du projet est mis à jour pour inclure le nouveau nom du fichier.

      Les événements de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>hiérarchie (par exemple) suivent généralement les changements affichés dans l’interface utilisateur, comme dans l’explorer **de solution**. Les événements de hiérarchie considèrent qu’une opération de renommer un fichier consiste en une suppression de fichiers, puis un ajout de fichier. Cependant, lorsque des éléments invisibles sont <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> modifiés, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> le système d’événements hiérarchique déclenche un événement, mais pas un événement. Par conséquent, si vous renommez un fichier <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> dans <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>un projet de plate-forme, vous obtenez les <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>deux et , mais si vous renommez un fichier dans un projet partagé, vous obtenez seulement .

      Pour suivre les changements dans les éléments du projet, vous <xref:EnvDTE.ProjectItemsEventsClass>pouvez gérer les événements de l’élément du projet DTE (ceux que l’on trouve dans ). Cependant, si vous traitez un grand nombre d’événements, <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>vous pouvez obtenir une meilleure gestion des performances des événements en . Dans cette procédure pas à pas, nous ne montrons que les événements de hiérarchie et les événements DTE. Dans cette procédure, vous ajoutez un auditeur d’événements à un projet commun et un projet de plate-forme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plate-forme, vous pouvez voir les événements qui sont tirés pour chaque opération de renom.

      Dans cette procédure, vous ajoutez un auditeur d’événements à un projet commun et un projet de plate-forme. Ensuite, lorsque vous renommez un fichier dans un projet partagé et un autre fichier dans un projet de plate-forme, vous pouvez voir les événements qui sont tirés pour chaque opération de renom.

2. Ajouter un auditeur d’événement. Ajoutez un nouveau fichier de classe au projet et appelez-le *HierarchyEventListener.cs*.

3. Ouvrez le fichier *HierarchyEventListener.cs* et ajoutez les directives suivantes à l’aide de directives :

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Faites `HierarchyEventListener` en <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>mettre en œuvre la classe :

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>les membres de , comme dans le code ci-dessous.

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

6. Dans la même classe ajouter un autre <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>gestionnaire d’événement pour l’événement DTE , qui se produit chaque fois qu’un élément de projet est renommé.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Inscrivez-vous aux événements de la hiérarchie. Vous devez vous inscrire séparément pour chaque projet que vous suivez. Ajoutez le code `ShowMessageBox`suivant , l’un pour le projet partagé, et l’autre pour l’un des projets de la plate-forme.

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

8. Inscrivez-vous à l’événement <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>d’élément du projet DTE . Ajoutez le code suivant après avoir branché le deuxième auditeur.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modifier l’élément partagé. Vous ne pouvez pas modifier les éléments partagés dans un projet de plate-forme ; au lieu de cela, vous devez les modifier dans le projet partagé qui est le propriétaire réel de ces articles. Vous pouvez obtenir l’ID d’élément correspondant dans le projet partagé avec, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>lui donnant le chemin complet de l’élément partagé. Ensuite, vous pouvez modifier l’élément partagé. Le changement est propagé aux projets de plate-forme.

    > [!IMPORTANT]
    > Vous devez savoir si un élément de projet est ou non un élément partagé avant de le modifier.

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

10. Appelez cette méthode après tout `ShowMessageBox` le code pour modifier le nom de fichier de l’élément dans le projet partagé. Insérez ceci après le code qui obtient le chemin complet de l’élément dans le projet partagé.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Générez et exécutez le projet. Créez une application de hub universel C DANS l’exemple expérimental, allez au menu **Tools** et cliquez sur **Invoke TestUniversalProject**, et vérifiez le texte dans le volet de sortie générale. Le nom du premier élément du projet partagé (nous nous attendons à ce qu’il soit le <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> fichier *App.xaml)* doit être changé, et vous devriez voir que l’événement a été déclenché. Dans ce cas, puisque le changement de nom *App.xaml* provoque *App.xaml.cs* être rebaptisé ainsi, vous devriez voir quatre événements (deux pour chaque projet de plate-forme). (Les événements DTE ne suivent pas les éléments du projet partagé.) Vous devriez <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> voir deux événements (un pour <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> chacun des projets de plate-forme), mais pas d’événements.

12. Maintenant, essayez de renommer un fichier dans un projet de plate-forme, et vous pouvez voir la différence dans les événements qui se font virer. Ajouter le code `ShowMessageBox` suivant après `ModifyFileName`l’appel à .

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

13. Générez et exécutez le projet. Créez un projet universel C DANS l’exemple expérimental, allez au menu **Tools** et cliquez sur **Invoke TestUniversalProject**, et vérifiez le texte dans le volet de sortie générale. Une fois que le fichier du projet de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> plate-forme <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> est renommé, vous devriez voir à la fois un événement et un événement. Depuis que la modification du fichier n’a pas modifié d’autres fichiers et que les modifications apportées aux éléments d’un projet de plate-forme ne se propagent nulle part, il n’y a qu’un seul de ces événements.
