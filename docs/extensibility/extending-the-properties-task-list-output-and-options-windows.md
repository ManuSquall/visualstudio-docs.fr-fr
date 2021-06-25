---
title: Étendre les propriétés, Liste des tâches, sortie, fenêtres d’options
description: Découvrez comment intégrer des informations sur votre fenêtre outil dans Visual Studio dans une nouvelle page d’options et un nouveau paramètre dans la page Propriétés.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3334ba3694ee3c1354c152b013c38472e4b90b72
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903279"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Étendre les fenêtres propriétés, Liste des tâches, sortie et options
Vous pouvez accéder à n’importe quelle fenêtre outil dans Visual Studio. Cette procédure pas à pas montre comment intégrer des informations sur votre fenêtre outil dans une nouvelle page d' **options** et un nouveau paramètre dans la page **Propriétés** , et comment écrire dans les fenêtres de **liste des tâches** et de **sortie** .

## <a name="prerequisites"></a>Prérequis
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre outil

1. Créez un projet nommé **ToDoList** à l’aide du modèle VSIX, puis ajoutez un modèle d’élément de fenêtre outil personnalisé nommé **TodoWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configurer la fenêtre outil
 Ajoutez une zone de texte dans laquelle vous pouvez taper un nouvel élément ToDo, un bouton pour ajouter le nouvel élément à la liste et un contrôle ListBox pour afficher les éléments de la liste.

1. Dans *TodoWindow. Xaml*, supprimez les contrôles Button, TextBox et StackPanel du UserControl.

    > [!NOTE]
    > Cela ne supprime pas le gestionnaire d’événements **Button1_Click** , que vous allez réutiliser dans une étape ultérieure.

2. À partir de la section **tous les contrôles WPF** de la **boîte à outils**, faites glisser un contrôle **Canvas** vers la grille.

3. Faites glisser une **zone de texte**, un **bouton** et une zone de **liste** vers la zone de dessin. Réorganisez les éléments afin que la zone de texte et le bouton se trouvent au même niveau et que la zone de liste remplisse le reste de la fenêtre en dessous, comme dans l’image ci-dessous.

     ![Fenêtre Outil fini](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. Dans le volet XAML, recherchez le bouton et affectez à sa propriété Content la valeur **Add**. Reconnectez le gestionnaire d’événements Button au contrôle Button en ajoutant un `Click="button1_Click"` attribut. Le bloc Canvas doit se présenter comme suit :

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personnaliser le constructeur

1. Dans le fichier *TodoWindowControl. Xaml. cs* , ajoutez la directive using suivante :

    ```csharp
    using System;
    ```

2. Ajoutez une référence publique à TodoWindow et faites en sorte que le constructeur TodoWindowControl prenne un paramètre TodoWindow. Le code doit se présenter comme ceci :

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. Dans *TodoWindow. cs*, modifiez le constructeur TodoWindowControl pour inclure le paramètre TodoWindow. Le code doit se présenter comme ceci :

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Créer une page d’options
 Vous pouvez fournir une page dans la boîte de dialogue **options** afin que les utilisateurs puissent modifier les paramètres de la fenêtre outil. La création d’une page d’options nécessite à la fois une classe qui décrit les options et une entrée dans le fichier *TodoListPackage. cs* ou *TodoListPackage. vb* .

1. Ajoutez une classe nommée `ToolsOptions.cs`. Faites en sorte que la `ToolsOptions` classe hérite de <xref:Microsoft.VisualStudio.Shell.DialogPage> .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Ajoutez la directive using suivante :

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. La page Options de cette procédure pas à pas fournit une seule option nommée DaysAhead. Ajoutez un champ privé nommé **daysAhead** et une propriété nommée **daysAhead** à la `ToolsOptions` classe :

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Vous devez à présent que le projet soit informé de cette page d’options.

### <a name="make-the-options-page-available-to-users"></a>Rendre la page Options accessible aux utilisateurs

1. Dans *TodoWindowPackage. cs*, ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> à la `TodoWindowPackage` classe :

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Le premier paramètre du constructeur ProvideOptionPage est le type de la classe `ToolsOptions` , que vous avez créée précédemment. Le deuxième paramètre, « ToDo », est le nom de la catégorie dans la boîte de dialogue **options** . Le troisième paramètre, « General », est le nom de la sous-catégorie de la boîte de dialogue **options** dans laquelle la page Options sera disponible. Les deux paramètres suivants sont des ID de ressource pour les chaînes ; le premier est le nom de la catégorie, tandis que le deuxième est le nom de la sous-catégorie. Le paramètre final détermine si cette page est accessible à l’aide de l’automatisation.

     Quand un utilisateur ouvre la page Options, il doit ressembler à l’image suivante.

     ![Page Options](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Notez la catégorie **TODO** et la sous-catégorie **général**.

## <a name="make-data-available-to-the-properties-window"></a>Rendre les données disponibles pour le Fenêtre Propriétés
 Vous pouvez rendre les informations de liste ToDo disponibles en créant une classe nommée `TodoItem` qui stocke des informations sur les éléments individuels de la liste de tâches.

1. Ajoutez une classe nommée `TodoItem.cs`.

     Lorsque la fenêtre outil est disponible pour les utilisateurs, les éléments de la zone de liste sont représentés par TodoItems. Lorsque l’utilisateur sélectionne l’un de ces éléments dans la zone de liste, la fenêtre **Propriétés** affiche des informations sur l’élément.

     Pour rendre les données disponibles dans la fenêtre **Propriétés** , transformez les données en propriétés publiques qui ont deux attributs spéciaux, `Description` et `Category` . `Description` texte qui apparaît en bas de la fenêtre **Propriétés** . `Category` détermine l’emplacement où la propriété doit apparaître lorsque la fenêtre **Propriétés** est affichée dans la vue par **catégorie** . Dans l’image suivante, la fenêtre **Propriétés** est en mode par **catégorie** , la propriété **nom** de la catégorie **champs todo** est sélectionnée et la description de la propriété **Name** est affichée en bas de la fenêtre.

     ![Fenêtre Propriétés](../extensibility/media/t5properties.png "T5Properties")

2. Ajoutez les directives using suivantes dans le fichier *TodoItem. cs* .

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Ajoutez le `public` modificateur d’accès à la déclaration de classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Ajoutez les deux propriétés, `Name` et `DueDate` . Nous allons effectuer la `UpdateList()` et `CheckForErrors()` versions ultérieures.

    ```csharp
    public class TodoItem
    {
        private TodoWindowControl parent;
        private string name;
        [Description("Name of the ToDo item")]
        [Category("ToDo Fields")]
        public string Name
        {
            get { return name; }
            set
            {
                name = value;
                parent.UpdateList(this);
            }
        }

        private DateTime dueDate;
        [Description("Due date of the ToDo item")]
        [Category("ToDo Fields")]
        public DateTime DueDate
        {
            get { return dueDate; }
            set
            {
                dueDate = value;
                parent.UpdateList(this);
                parent.CheckForErrors();
            }
        }
    }
    ```

4. Ajoutez une référence privée au contrôle utilisateur. Ajoutez un constructeur qui prend le contrôle utilisateur et le nom de cet élément ToDo. Pour trouver la valeur pour `daysAhead` , elle obtient la propriété de la page Options.

    ```csharp
    private TodoWindowControl parent;

    public TodoItem(TodoWindowControl control, string itemName)
    {
        parent = control;
        name = itemName;
        dueDate = DateTime.Now;

        double daysAhead = 0;
        IVsPackage package = parent.parent.Package as IVsPackage;
        if (package != null)
        {
            object obj;
            package.GetAutomationObject("ToDo.General", out obj);

            ToolsOptions options = obj as ToolsOptions;
            if (options != null)
            {
                daysAhead = options.DaysAhead;
            }
        }

        dueDate = dueDate.AddDays(daysAhead);
    }
    ```

5. Étant donné que les instances de la `TodoItem` classe seront stockées dans la zone de liste et que la zone de liste appellera la `ToString` fonction, vous devez surcharger la `ToString` fonction. Ajoutez le code suivant à *TodoItem. cs*, après le constructeur et avant la fin de la classe.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. Dans *TodoWindowControl. Xaml. cs*, ajoutez des méthodes stub à la `TodoWindowControl` classe pour `CheckForError` les `UpdateList` méthodes et. Placez-les après le ProcessDialogChar et avant la fin du fichier.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     La `CheckForError` méthode appellera une méthode portant le même nom dans l’objet parent, et cette méthode vérifiera si des erreurs se sont produites et les gérera correctement. La `UpdateList` méthode met à jour la zone de liste dans le contrôle parent ; la méthode est appelée lorsque les `Name` `DueDate` Propriétés et de cette classe changent. Ils seront implémentés ultérieurement.

## <a name="integrate-into-the-properties-window"></a>Intégrer dans le Fenêtre Propriétés
 À présent, écrivez le code qui gère la zone de liste, qui sera liée à la fenêtre **Propriétés** .

 Vous devez modifier le gestionnaire de clic de bouton pour lire la zone de texte, créer un TodoItem, puis l’ajouter à la zone de liste.

1. Remplacez la `button1_Click` fonction existante par du code qui crée un nouveau TodoItem et l’ajoute à la zone de liste. Elle appelle `TrackSelection()` , qui sera définie ultérieurement.

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Dans la Mode Création sélectionnez le contrôle ListBox. Dans la fenêtre **Propriétés** , cliquez sur le bouton **gestionnaires d’événements** et recherchez l’événement **SelectionChanged** . Renseignez la zone de texte avec **listBox_SelectionChanged**. Cela ajoute un stub pour un gestionnaire SelectionChanged et l’assigne à l’événement.

3. Implémentez la méthode `TrackSelection()`. Étant donné que vous devrez fournir les <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> services, vous devez rendre le <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> accessible par le TodoWindowControl. Ajoutez la méthode suivante à la classe `TodoWindow` :

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Ajoutez les directives using suivantes à *TodoWindowControl. Xaml. cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Renseignez le gestionnaire SelectionChanged comme suit :

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. À présent, renseignez la fonction TrackSelection, qui fournira une intégration avec la fenêtre **Propriétés** . Cette fonction est appelée lorsque l’utilisateur ajoute un élément à la zone de liste ou clique sur un élément de la zone de liste. Il ajoute le contenu de la zone de liste à un SelectionContainer et passe le SelectionContainer au gestionnaire d’événements de la fenêtre **Propriétés** <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> . Le service TrackSelection effectue le suivi des objets sélectionnés dans l’interface utilisateur (IU) et affiche leurs propriétés.

    ```csharp
    private SelectionContainer mySelContainer;
    private System.Collections.ArrayList mySelItems;
    private IVsWindowFrame frame = null;

    private void TrackSelection()
    {
        if (frame == null)
        {
            var shell = parent.GetVsService(typeof(SVsUIShell)) as IVsUIShell;
            if (shell != null)
            {
                var guidPropertyBrowser = new
                Guid(ToolWindowGuids.PropertyBrowser);
                shell.FindToolWindow((uint)__VSFINDTOOLWIN.FTW_fForceCreate,
                ref guidPropertyBrowser, out frame);
            }
        }
        if (frame != null)
            {
                frame.Show();
            }
        if (mySelContainer == null)
        {
            mySelContainer = new SelectionContainer();
        }

        mySelItems = new System.Collections.ArrayList();

        var selected = listBox.SelectedItem as TodoItem;
        if (selected != null)
        {
            mySelItems.Add(selected);
        }

        mySelContainer.SelectedObjects = mySelItems;

        ITrackSelection track = parent.GetVsService(typeof(STrackSelection))
                                as ITrackSelection;
        if (track != null)
        {
            track.OnSelectChange(mySelContainer);
        }
    }
    ```

     Maintenant que vous avez une classe que la fenêtre **Propriétés** peut utiliser, vous pouvez intégrer la fenêtre **Propriétés** à la fenêtre outil. Quand l’utilisateur clique sur un élément de la zone de liste dans la fenêtre outil, la fenêtre **Propriétés** doit être mise à jour en conséquence. De même, lorsque l’utilisateur modifie un élément ToDo dans la fenêtre **Propriétés** , l’élément associé doit être mis à jour.

7. À présent, ajoutez le reste du code de la fonction UpdateList dans *TodoWindowControl. Xaml. cs*. Il doit supprimer et rajouter les TodoItem modifiés à partir de la zone de liste.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Testez votre code. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.

9. Ouvrez la   >  page **options** des outils. Vous devez voir la catégorie ToDo dans le volet gauche. Les catégories sont répertoriées par ordre alphabétique, donc Regardez sous le TS.

10. Dans la page options **TODO** , la propriété doit être `DaysAhead` définie sur **0**. Remplacez-la par **2**.

11. Dans le menu **affichage/autres fenêtres** , ouvrez **TodoWindow**. Tapez **EndDate** dans la zone de texte, puis cliquez sur **Ajouter**.

12. Dans la zone de liste, vous devriez voir une date postérieure de deux jours à la date du jour.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Ajoutez du texte à la fenêtre sortie et aux éléments de la Liste des tâches
 Pour la **liste des tâches**, vous créez un nouvel objet de type Task, puis vous ajoutez cet objet Task à la **liste des tâches** en appelant sa `Add` méthode. Pour écrire dans la fenêtre **sortie** , vous appelez sa `GetPane` méthode pour obtenir un objet Pane, puis vous appelez la `OutputString` méthode de l’objet Pane.

1. Dans *TodoWindowControl. Xaml. cs*, dans la `button1_Click` méthode, ajoutez le code pour obtenir le volet **général** de la fenêtre **sortie** (qui est la valeur par défaut) et y écrire. La méthode doit ressembler à ceci :

    ```csharp
    private void button1_Click(object sender, EventArgs e)
    {
        if (textBox.Text.Length > 0)
        {
            var item = new TodoItem(this, textBox.Text);
            listBox.Items.Add(item);

            var outputWindow = parent.GetVsService(
                typeof(SVsOutputWindow)) as IVsOutputWindow;
            IVsOutputWindowPane pane;
            Guid guidGeneralPane = VSConstants.GUID_OutWindowGeneralPane;
            outputWindow.GetPane(ref guidGeneralPane, out pane);
            if (pane != null)
            {
                 pane.OutputString(string.Format(
                    "To Do item created: {0}\r\n",
                 item.ToString()));
        }
            TrackSelection();
            CheckForErrors();
        }
    }
    ```

2. Pour ajouter des éléments à la Liste des tâches, vous devez ajouter une classe imbriquée à la classe TodoWindowControl. La classe imbriquée doit dériver de <xref:Microsoft.VisualStudio.Shell.TaskProvider> . Ajoutez le code suivant à la fin de la `TodoWindowControl` classe.

    ```csharp
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]
    public class TodoWindowTaskProvider : TaskProvider
    {
        public TodoWindowTaskProvider(IServiceProvider sp)
            : base(sp)
        {
        }
    }
    ```

3. Ajoutez ensuite une référence privée à `TodoTaskProvider` et une `CreateProvider()` méthode à la `TodoWindowControl` classe. Le code doit se présenter comme ceci :

    ```csharp
    private TodoWindowTaskProvider taskProvider;
    private void CreateProvider()
    {
        if (taskProvider == null)
        {
            taskProvider = new TodoWindowTaskProvider(parent);
            taskProvider.ProviderName = "To Do";
        }
    }
    ```

4. Ajoutez `ClearError()` , qui efface le liste des tâches et `ReportError()` , qui ajoute une entrée à la liste des tâches, à la `TodoWindowControl` classe.

    ```csharp
    private void ClearError()
    {
        CreateProvider();
        taskProvider.Tasks.Clear();
    }
    private void ReportError(string p)
    {
        CreateProvider();
        var errorTask = new Task();
        errorTask.CanDelete = false;
        errorTask.Category = TaskCategory.Comments;
        errorTask.Text = p;

        taskProvider.Tasks.Add(errorTask);

        taskProvider.Show();

        var taskList = parent.GetVsService(typeof(SVsTaskList))
            as IVsTaskList2;
        if (taskList == null)
        {
            return;
        }

        var guidProvider = typeof(TodoWindowTaskProvider).GUID;
         taskList.SetActiveProvider(ref guidProvider);
    }
    ```

5. Implémentez maintenant la `CheckForErrors` méthode, comme suit.

    ```csharp
    public void CheckForErrors()
    {
        foreach (TodoItem item in listBox.Items)
        {
            if (item.DueDate < DateTime.Now)
            {
                ReportError("To Do Item is out of date: "
                    + item.ToString());
            }
        }
    }
    ```

## <a name="try-it-out"></a>Faire un essai

1. Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.

2. Ouvrez **TodoWindow** (**voir**  >  **autres fenêtres**  >  **TodoWindow**).

3. Tapez un nom dans la zone de texte, puis cliquez sur **Ajouter**.

     Une date d’échéance de 2 jours après la date du jour est ajoutée à la zone de liste. Aucune erreur n’est générée, et la **liste des tâches** (**vue**  >  **liste des tâches**) ne doit pas contenir d’entrées.

4. À présent, remplacez le paramètre de la  >    >  page **TODO** des  options outils par **0**.

5. Tapez un autre nom dans le **TodoWindow** , puis cliquez à nouveau sur **Ajouter** . Cela déclenche une erreur et également une entrée dans le **liste des tâches**.

     À mesure que vous ajoutez des éléments, la date initiale est définie sur maintenant plus 2 jours.

6. Dans le menu **affichage** , cliquez sur **sortie** pour ouvrir la fenêtre **sortie** .

     Notez que chaque fois que vous ajoutez un élément, un message s’affiche dans le volet **liste des tâches** .

7. Cliquez sur l’un des éléments de la zone de liste.

     La fenêtre **Propriétés** affiche les deux propriétés de l’élément.

8. Modifiez l’une des propriétés, puis appuyez sur **entrée**.

     L’élément est mis à jour dans la zone de liste.
