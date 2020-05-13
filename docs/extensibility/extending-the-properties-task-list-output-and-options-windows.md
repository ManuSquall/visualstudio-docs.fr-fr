---
title: Étendre les propriétés, la liste de tâches, la sortie, les fenêtres d’options
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db14068c97ff6868f5fb73c9ddd790020e99e7c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711636"
---
# <a name="extend-the-properties-task-list-output-and-options-windows"></a>Étendre les propriétés, la liste de tâches, la sortie et les fenêtres d’options
Vous pouvez accéder à n’importe quelle fenêtre d’outil dans Visual Studio. Ce pas-à-porter montre comment intégrer des informations sur votre fenêtre d’outil dans une nouvelle page **Options** et un nouveau paramètre sur la page **Propriétés,** ainsi que la façon d’écrire sur la **liste de tâches** et les fenêtres de **sortie.**

## <a name="prerequisites"></a>Prérequis
 A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-tool-window"></a>Créer une extension avec une fenêtre d’outils

1. Créez un projet nommé **TodoList** à l’aide du modèle VSIX et ajoutez un modèle personnalisé d’élément de fenêtre d’outil nommé **TodoWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre d’outil, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="set-up-the-tool-window"></a>Configurer la fenêtre d’outils
 Ajoutez une TextBox pour taper un nouvel élément ToDo, un bouton pour ajouter le nouvel élément à la liste et une ListBox pour afficher les éléments de la liste.

1. Dans *TodoWindow.xaml*, supprimez les commandes Button, TextBox et StackPanel de l’UserControl.

    > [!NOTE]
    > Cela ne supprime pas le **gestionnaire d’événements button1_Click,** que vous réutilisez dans une étape ultérieure.

2. De la section **Tous les contrôles WPF** de la **boîte à outils**, faites glisser un contrôle **de toile** à la grille.

3. Faites glisser une **TextBox**, un **bouton**, et une **ListBox** à la toile. Disposer les éléments de sorte que la TextBox et le bouton sont au même niveau, et la ListBox remplit le reste de la fenêtre en dessous d’eux, comme dans l’image ci-dessous.

     ![Fenêtre Outil fini](../extensibility/media/t5-toolwindow.png "T5-ToolWindow")

4. Dans la vitre XAML, trouvez le bouton et définissez sa propriété Content à **ajouter**. Reconnectez le gestionnaire d’événements bouton `Click="button1_Click"` au contrôle de bouton en ajoutant un attribut. Le bloc canvas devrait ressembler à ceci:

    ```xml
    <Canvas HorizontalAlignment="Left" Width="306">
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>
    </Canvas>
    ```

### <a name="customize-the-constructor"></a>Personnaliser le constructeur

1. Dans le fichier *TodoWindowControl.xaml.cs,* ajoutez la directive suivante à l’aide :

    ```csharp
    using System;
    ```

2. Ajoutez une référence publique au TodoWindow et demandez au constructeur TodoWindowControl de prendre un paramètre TodoWindow. Le code devrait ressembler à ceci:

    ```csharp
    public TodoWindow parent;

    public TodoWindowControl(TodoWindow window)
    {
        InitializeComponent();
        parent = window;
    }
    ```

3. Dans *TodoWindow.cs*, modifier le constructeur TodoWindowControl pour inclure le paramètre TodoWindow. Le code devrait ressembler à ceci:

    ```csharp
    public TodoWindow() : base(null)
    {
        this.Caption = "TodoWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;

         this.Content = new TodoWindowControl(this);
    }
    ```

## <a name="create-an-options-page"></a>Créer une page Options
 Vous pouvez fournir une page dans la boîte de dialogue **Options** afin que les utilisateurs puissent modifier les paramètres de la fenêtre d’outil. La création d’une page Options nécessite à la fois une classe qui décrit les options et une entrée dans le *fichier TodoListPackage.cs* ou *TodoListPackage.vb.*

1. Ajoutez une classe nommée `ToolsOptions.cs`. Faire `ToolsOptions` la classe <xref:Microsoft.VisualStudio.Shell.DialogPage>hériter de .

   ```csharp
   class ToolsOptions : DialogPage
   {
   }
   ```

2. Ajoutez la directive using suivante :

   ```csharp
   using Microsoft.VisualStudio.Shell;
   ```

3. La page Options dans cette procédure pas à pas ne fournit qu’une seule option nommée DaysAhead. Ajouter un champ privé nommé **daysAhead** et une `ToolsOptions` propriété nommée **DaysAhead** à la classe:

   ```csharp
   private double daysAhead;

   public double DaysAhead
   {
       get { return daysAhead; }
       set { daysAhead = value; }
   }
   ```

   Maintenant, vous devez informer le projet de cette page Options.

### <a name="make-the-options-page-available-to-users"></a>Mettre la page Options à la disposition des utilisateurs

1. En *TodoWindowPackage.cs*, ajouter <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute> un `TodoWindowPackage` à la classe:

    ```csharp
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]
    ```

2. Le premier paramètre du constructeur ProvideOptionPage est `ToolsOptions`le type de classe , que vous avez créé plus tôt. Le deuxième paramètre, "ToDo", est le nom de la catégorie dans la boîte de dialogue **Options.** Le troisième paramètre, "Général", est le nom de la sous-catégorie de la boîte de dialogue **Options** où la page Options sera disponible. Les deux paramètres suivants sont les Œd de ressources pour les cordes; le premier est le nom de la catégorie, et le second est le nom de la sous-catégorie. Le paramètre final détermine si cette page peut être consultée en utilisant l’automatisation.

     Lorsqu’un utilisateur ouvre votre page Options, il doit ressembler à l’image suivante.

     ![Page Options](../extensibility/media/t5optionspage.gif "T5OptionsPage")

     Notez la catégorie **ToDo** et la sous-catégorie **générale**.

## <a name="make-data-available-to-the-properties-window"></a>Mettre les données à la disposition de la fenêtre Propriétés
 Vous pouvez rendre les informations de liste `TodoItem` ToDo disponibles en créant une classe nommée qui stocke des informations sur les éléments individuels dans la liste ToDo.

1. Ajoutez une classe nommée `TodoItem.cs`.

     Lorsque la fenêtre d’outils est disponible pour les utilisateurs, les éléments de la ListBox seront représentés par TodoItems. Lorsque l’utilisateur sélectionne l’un de ces éléments dans la ListBox, la fenêtre **Propriétés** affiche des informations sur l’élément.

     Pour rendre les données disponibles dans la fenêtre **Propriétés,** vous `Description` transformez les données en propriétés publiques qui ont deux attributs spéciaux, et `Category`. `Description`est le texte qui apparaît au bas de la fenêtre **propriétés.** `Category`détermine où la propriété doit apparaître lorsque la fenêtre **propriété** est affichée dans la vue **catégorisée.** Dans l’image suivante, la fenêtre **Propriétés** est en vue **catégorisée,** la propriété **Nom** dans la catégorie **ToDo Fields** est sélectionnée, et la description de la propriété **Nom** est affichée au bas de la fenêtre.

     ![Fenêtre de propriétés](../extensibility/media/t5properties.png "T5Properties (T5Properties)")

2. Ajoutez ce qui suit à l’aide des directives du *fichier TodoItem.cs.*

    ```csharp
    using System.ComponentModel;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Ajouter `public` le modificateur d’accès à la déclaration de classe.

    ```csharp
    public class TodoItem
    {
    }
    ```

     Ajouter les deux `Name` `DueDate`propriétés, et . On fera le `UpdateList()` `CheckForErrors()` et plus tard.

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

4. Ajoutez une référence privée au contrôle de l’utilisateur. Ajoutez un constructeur qui prend le contrôle de l’utilisateur et le nom de cet élément ToDo. Pour trouver la `daysAhead`valeur pour , il obtient la propriété de la page Options.

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

5. Étant donné `TodoItem` que les instances de la classe seront stockées dans la ListBox et que la ListBox appellera la `ToString` fonction, vous devez surcharger la `ToString` fonction. Ajoutez le code suivant à *TodoItem.cs,* après le constructeur et avant la fin de la classe.

    ```csharp
    public override string ToString()
    {
        return name + " Due: " + dueDate.ToShortDateString();
    }
    ```

6. Dans *TodoWindowControl.xaml.cs*, ajouter des méthodes `TodoWindowControl` de talon `CheckForError` `UpdateList` à la classe pour les méthodes et les méthodes. Mettez-les après le ProcessDialogChar et avant la fin du fichier.

    ```csharp
    public void CheckForErrors()
    {
    }
    public void UpdateList(TodoItem item)
    {
    }
    ```

     La `CheckForError` méthode appellera une méthode qui a le même nom dans l’objet parent, et cette méthode vérifiera si des erreurs se sont produites et les traiter correctement. La `UpdateList` méthode mettra à jour la ListBox dans le contrôle parent; la méthode est `Name` appelée `DueDate` lorsque le et les propriétés dans cette classe changent. Ils seront mis en œuvre plus tard.

## <a name="integrate-into-the-properties-window"></a>Intégrer dans la fenêtre Propriétés
 Maintenant, écrivez le code qui gère la ListBox, qui sera liée à la fenêtre **Propriétés.**

 Vous devez modifier le bouton click handler pour lire la TextBox, créer un TodoItem, et l’ajouter à la ListBox.

1. Remplacez `button1_Click` la fonction existante par du code qui crée un nouveau TodoItem et l’ajoute à la ListBox. Il `TrackSelection()`appelle , qui sera défini plus tard.

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

2. Dans la vue de conception sélectionnez le contrôle ListBox. Dans la fenêtre **Propriétés** cliquez sur le bouton **des gestionnaires d’événements** et trouvez l’événement **SelectionChanged.** Remplissez la boîte de texte avec **listBox_SelectionChanged**. Cela ajoute un talon pour un gestionnaire SelectionChanged et l’attribue à l’événement.

3. Implémentez la méthode `TrackSelection()`. Puisque vous aurez besoin <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> d’obtenir les <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> services, vous devez rendre l’accessible par le TodoWindowControl. Ajoutez la méthode suivante à la classe `TodoWindow` :

    ```
    internal object GetVsService(Type service)
    {
        return GetService(service);
    }
    ```

4. Ajouter ce qui suit en utilisant des directives à *TodoWindowControl.xaml.cs*:

    ```csharp
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.Shell.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    ```

5. Remplissez le gestionnaire SelectionChanged comme suit :

    ```
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)
    {
        TrackSelection();
    }
    ```

6. Maintenant, remplissez la fonction TrackSelection, qui fournira l’intégration avec la fenêtre **Propriétés.** Cette fonction s’appelle lorsque l’utilisateur ajoute un élément à la ListBox ou clique sur un élément dans la ListBox. Il ajoute le contenu de la ListBox à un SelectionContainer et passe <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> le SelectionContainer au gestionnaire d’événements de la fenêtre **Propriétés.** Le service TrackSelection suit certains objets dans l’interface utilisateur (interface utilisateur) et affiche leurs propriétés

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

     Maintenant que vous avez une classe que la fenêtre **Propriétés** peut utiliser, vous pouvez intégrer la fenêtre **Propriétés** avec la fenêtre d’outil. Lorsque l’utilisateur clique sur un élément dans la ListBox dans la fenêtre de l’outil, la fenêtre **Propriétés** doit être mise à jour en conséquence. De même, lorsque l’utilisateur modifie un élément ToDo dans la fenêtre **Propriétés,** l’élément associé doit être mis à jour.

7. Maintenant, ajoutez le reste du code de fonction UpdateList dans *TodoWindowControl.xaml.cs*. Il devrait laisser tomber et ré-ajouter le TodoItem modifié de la ListBox.

    ```csharp
    public void UpdateList(TodoItem item)
    {
        var index = listBox.SelectedIndex;
        listBox.Items.RemoveAt(index);
        listBox.Items.Insert(index, item);
        listBox.SelectedItem = index;
    }
    ```

8. Testez votre code. Générez le projet et commencez le débogage. L’instance expérimentale devrait apparaître.

9. Ouvrez la page **Options Outils.** > **Options** Vous devriez voir la catégorie ToDo dans la vitre gauche. Les catégories sont répertoriées par ordre alphabétique, alors regardez sous les T.

10. Sur la page d’options **Todo,** vous devriez voir la `DaysAhead` propriété définie à **0**. Changez-le à **2**.

11. Sur le **menu View / Autres Fenêtres,** ouvert **TodoWindow**. Type **EndDate** dans la boîte de texte et cliquez sur **Ajouter**.

12. Dans la boîte de liste, vous devriez voir une date deux jours plus tard qu’aujourd’hui.

## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Ajouter du texte à la fenêtre de sortie et des éléments à la liste de tâches
 Pour la **liste de tâches**, vous créez un nouvel objet de type Tâche, puis ajoutez cet objet de tâche à la liste de **tâches** en appelant sa `Add` méthode. Pour écrire à la fenêtre `GetPane` **de sortie,** vous appelez sa méthode `OutputString` pour obtenir un objet de vitre, puis vous appelez la méthode de l’objet de vitre.

1. Dans *TodoWindowControl.xaml.cs*, dans `button1_Click` la méthode, ajouter du code pour obtenir la vitre **générale** de la fenêtre **de sortie** (qui est la valeur par défaut), et y écrire. La méthode doit ressembler à ceci :

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

2. Afin d’ajouter des éléments à la liste de tâches, vous avez besoin d’un pour ajouter une classe imbriquée à la classe TodoWindowControl. La classe imbriquée <xref:Microsoft.VisualStudio.Shell.TaskProvider>doit dériver de . Ajoutez le code suivant à `TodoWindowControl` la fin de la classe.

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

3. Ajoutez ensuite une `TodoTaskProvider` référence `CreateProvider()` privée et `TodoWindowControl` une méthode à la classe. Le code devrait ressembler à ceci:

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

4. Ajouter `ClearError()`, qui efface la `ReportError()`liste de tâches, et , qui `TodoWindowControl` ajoute une entrée à la liste de tâches, à la classe.

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

5. Maintenant implémenter la `CheckForErrors` méthode, comme suit.

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

## <a name="try-it-out"></a>Faites un essai

1. Générez le projet et commencez le débogage. L’instance expérimentale apparaît.

2. Ouvrez le **TodoWindow** **(Voir** > **d’autres Windows** > **TodoWindow**).

3. Tapez quelque chose dans la boîte de texte, puis cliquez sur **Ajouter**.

     Une date d’échéance 2 jours après aujourd’hui est ajoutée à la case liste. Aucune erreur n’est générée, et la **liste de tâches** **(Voir** > **la liste des tâches**) ne devrait pas avoir d’entrées.

4. Maintenant, changez le paramètre sur la page **Tools** > **Options** > **ToDo** de **2** à **0**.

5. Tapez autre chose dans le **TodoWindow,** puis cliquez sur **Ajouter** à nouveau. Cela déclenche une erreur et aussi une entrée dans la **liste des tâches**.

     Lorsque vous ajoutez des éléments, la date initiale est fixée à maintenant plus 2 jours.

6. Sur le menu **View,** cliquez sur **Sortie** pour ouvrir la fenêtre **de sortie.**

     Notez que chaque fois que vous ajoutez un élément, un message est affiché dans le volet **Liste des tâches.**

7. Cliquez sur l’un des éléments de la ListBox.

     La fenêtre **Propriété** affiche les deux propriétés de l’article.

8. Changer l’une des propriétés, puis appuyez **sur Entrez**.

     L’élément est mis à jour dans la ListBox.
