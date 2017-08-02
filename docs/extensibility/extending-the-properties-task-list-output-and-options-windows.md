---
title: "Extension de propriétés, liste des tâches, sortie, les Options Windows | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties pane
- task list
- output window
- properties window
- tutorials
- tool windows
ms.assetid: 06990510-5424-44b8-9fd9-6481acec5c76
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 75937e3f2cf1d3fa9c5c78de8b7df5f8869ef49e
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-properties-task-list-output-and-options-windows"></a>Extension de propriétés, liste des tâches, sortie, les Options Windows
Vous pouvez accéder n’importe quelle fenêtre outil dans Visual Studio. Cette procédure pas à pas montre comment intégrer les informations concernant votre fenêtre outil dans une nouvelle **Options** page et un nouveau paramètre sur le **propriétés** page et également comment écrire dans le **liste des tâches** et **sortie** windows.  
  
## <a name="prerequisites"></a>Conditions préalables  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-tool-window"></a>Créer une Extension avec une fenêtre outil  
  
1.  Créez un projet nommé **TodoList** à l’aide du modèle VSIX et ajouter un modèle d’élément de fenêtre Outil personnalisée nommé **TodoWindow**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="set-up-the-tool-window"></a>Configurer la fenêtre d’outils  
 Ajoutez une zone de texte dans laquelle vous pouvez entrer un nouvel élément ToDo, un bouton pour ajouter le nouvel élément à la liste et une zone de liste pour afficher les éléments dans la liste.  
  
1.  Dans TodoWindow.xaml, supprimer les contrôles de bouton, zone de texte et StackPanel de UserControl.  
  
    > [!NOTE]
    >  Cette opération ne supprime pas le **button1_Click** Gestionnaire d’événements qui vous réutiliserez dans une étape ultérieure.  
  
2.  À partir de la **tous les contrôles WPF** section de la **boîte à outils**, faites glisser un **canevas** contrôle à la grille.  
  
3.  Faites glisser un **zone de texte**, un **bouton**et un **ListBox** à la zone de dessin. Organiser des éléments afin que la zone de texte et le bouton se trouvent sur le même niveau, et la zone de liste remplisse le reste de la fenêtre ci-dessous, comme dans l’image ci-dessous.  
  
     ![Fin de fenêtre outil](~/docs/extensibility/media/t5-toolwindow.png "T5-(fenêtre outil)")  
  
4.  Dans le volet XAML, recherchez le bouton et affectez à sa propriété de contenu **ajouter**. Reconnectez le Gestionnaire d’événements de bouton pour le contrôle bouton en ajoutant un `Click="button1_Click"` attribut. Le bloc de la zone de dessin doit ressembler à ceci :  
  
    ```xml  
    <Canvas HorizontalAlignment="Left" Width="306">  
        <TextBox x:Name="textBox" HorizontalAlignment="Left" Height="23" Margin="10,10,0,0" TextWrapping="Wrap" Text="TextBox" VerticalAlignment="Top" Width="208"/>  
            <Button x:Name="button" Content="Add" HorizontalAlignment="Left" Margin="236,13,0,0" VerticalAlignment="Top" Width="48" Click="button1_Click"/>  
            <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="222" Margin="10,56,0,0" VerticalAlignment="Top" Width="274"/>  
    </Canvas>  
    ```  
  
#### <a name="customize-the-constructor"></a>Personnaliser le constructeur  
  
1.  Dans le fichier TodoWindowControl.xaml.cs, ajoutez l’instruction using :  
  
    ```c#  
    using System;  
    ```  
  
2.  Ajouter une référence pour le TodoWindow public et avoir le constructeur TodoWindowControl prennent un paramètre TodoWindow. Le code doit ressembler à ceci :  
  
    ```c#  
    public TodoWindow parent;  
  
    public TodoWindowControl(TodoWindow window)  
    {  
        InitializeComponent();  
        parent = window;  
    }  
    ```  
  
3.  Dans TodoWindow.cs, modifiez le constructeur TodoWindowControl pour inclure le paramètre TodoWindow. Le code doit ressembler à ceci :  
  
    ```c#  
    public TodoWindow() : base(null)  
    {  
        this.Caption = "TodoWindow";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
  
         this.Content = new TodoWindowControl(this);  
    }  
    ```  
  
## <a name="create-an-options-page"></a>Créer une Page Options  
 Vous pouvez fournir une page dans le **Options** la boîte de dialogue afin que les utilisateurs peuvent modifier les paramètres de la fenêtre outil. Création d’une page Options nécessite à la fois une classe qui décrit les options et une entrée dans le fichier TodoListPackage.cs ou TodoListPackage.vb.  
  
1.  Ajoutez une classe nommée `ToolsOptions.cs`. Faites en sorte que la classe OutilsOptions hérite <xref:Microsoft.VisualStudio.Shell.DialogPage>.</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
    ```c#  
    class ToolsOptions : DialogPage  
    {  
    }  
    ```  
  
2.  Ajoutez l’instruction using :  
  
    ```c#  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
3.  La page Options de cette procédure pas à pas fournit uniquement une option nommée DaysAhead. Ajoutez un champ privé nommé **daysAhead** et une propriété nommée **DaysAhead** à la classe OutilsOptions :  
  
    ```c#  
    private double daysAhead;  
  
    public double DaysAhead  
    {  
        get { return daysAhead; }  
        set { daysAhead = value; }  
    }  
    ```  
  
 Vous devez maintenant vous le projet prenant en charge de cette page d’Options.  
  
#### <a name="make-the-options-page-available-to-users"></a>Rendre la page d’Options disponibles aux utilisateurs  
  
1.  Dans TodoWindowPackage.cs, ajoutez un <xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>à la classe TodoWindowPackage :</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>  
  
    ```c#  
    [ProvideOptionPage(typeof(ToolsOptions), "ToDo", "General", 101, 106, true)]  
    ```  
  
2.  Le premier paramètre au constructeur ProvideOptionPage est le type de la classe OutilsOptions, que vous avez créé précédemment. Le deuxième paramètre, « ToDo », est le nom de la catégorie dans le **Options** boîte de dialogue. Le troisième paramètre, « Général », est le nom de la sous-catégorie de la **Options** boîte de dialogue dans laquelle la page Options sera disponible. Les deux paramètres sont des ID de ressources pour les chaînes ; le premier est le nom de la catégorie et le deuxième est le nom de la sous-catégorie. Le paramètre final détermine si cette page est accessible à l’aide d’automation.  
  
     Lorsqu’un utilisateur ouvre votre page d’Options, il doit ressembler à l’image suivante.  
  
     ![Page Options](~/docs/extensibility/media/t5optionspage.gif "T5OptionsPage")  
  
     Notez que la catégorie **ToDo** et la sous-catégorie **général**.  
  
## <a name="make-data-available-to-the-properties-window"></a>Rendre les données disponibles dans la fenêtre Propriétés  
 Vous pouvez permettre des informations sur la liste à faire en créant une classe nommée TodoItem qui stocke des informations sur les éléments individuels dans la liste des tâches.  
  
1.  Ajoutez une classe nommée `TodoItem.cs`.  
  
     Lorsque la fenêtre outil est disponible pour les utilisateurs, les éléments dans la zone de liste seront représentés par TodoItems. Lorsque l’utilisateur sélectionne un de ces éléments dans la zone de liste, les **propriétés** fenêtre affiche des informations sur l’élément.  
  
     Pour rendre les données disponibles dans le **propriétés** fenêtre, vous pouvez convertir les données en propriétés publiques qui ont deux attributs spéciaux, `Description` et `Category`. `Description`est le texte qui apparaît au bas de la **propriétés** fenêtre. `Category`détermine où la propriété doit apparaître lorsque le **propriétés** fenêtre s’affiche dans le **par catégorie** vue. Dans l’image suivante, le **propriétés** fenêtre est **par catégorie** vue, le **nom** propriété dans le **ToDo Fields** la catégorie sélectionnée et la description de la **nom** propriété s’affiche en bas de la fenêtre.  
  
     ![Fenêtre Propriétés](~/docs/extensibility/media/t5properties.png "T5Properties")  
  
2.  Ajoutez le code suivant à l’aide des instructions du fichier TodoItem.cs.  
  
    ```c#  
    using System.ComponentModel;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
3.  Ajouter la `public` modificateur d’accès à la déclaration de classe.  
  
    ```c#  
    public class TodoItem  
    {  
    }  
    ```  
  
     Ajoutez les deux propriétés, le nom et DueDate. Nous ferons le UpdateList() et CheckForErrors() plus tard.  
  
    ```c#  
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
  
4.  Ajoutez une référence au contrôle utilisateur privée. Ajoutez un constructeur qui prend le contrôle utilisateur et le nom de cet élément ToDo. Pour rechercher la valeur de daysAhead, il obtient la propriété de la page Options.  
  
    ```c#  
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
  
5.  Car les instances de la `TodoItem` classe est stockée dans la zone de liste et la zone de liste appellera le `ToString` (fonction), vous devez surcharger la `ToString` (fonction). Ajoutez le code suivant à TodoItem.cs, après le constructeur et avant la fin de la classe.  
  
    ```c#  
    public override string ToString()  
    {  
        return name + " Due: " + dueDate.ToShortDateString();  
    }  
    ```  
  
6.  Dans TodoWindowControl.xaml.cs, ajoutez les méthodes stub pour la classe TodoWindowControl pour la `CheckForError` et `UpdateList` méthodes. Placez-les après le ProcessDialogChar et avant la fin du fichier.  
  
    ```c#  
    public void CheckForErrors()  
    {  
    }  
    public void UpdateList(TodoItem item)  
    {  
    }  
    ```  
  
     Le `CheckForError` méthode appelle une méthode qui porte le même nom dans l’objet parent, et cette méthode vérifie si des erreurs se sont produites et de les traiter correctement. Le `UpdateList` méthode met à jour la zone de liste dans le contrôle parent, la méthode est appelée lorsque le `Name` et `DueDate` propriétés lors de cette modification de la classe. Elles feront plus tard.  
  
## <a name="integrate-into-the-properties-window"></a>Intégrer dans la fenêtre Propriétés  
 Maintenant écrire le code qui gère la zone de liste, qui sera associée à la **propriétés** fenêtre.  
  
 Vous devez modifier le bouton Cliquez sur Gestionnaire de lecture de la zone de texte, créez un TodoItem et l’ajoute à la zone de liste.  
  
1.  Remplacez la `button1_Click` fonction avec du code qui crée un nouvel élément TodoItem et l’ajoute à la zone de liste. Il appelle TrackSelection(), qui seront définis ultérieurement.  
  
    ```c#  
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
  
2.  En mode Design, sélectionnez le contrôle ListBox. Dans le **propriétés** fenêtre cliquez sur le **gestionnaires d’événements** bouton et recherchez l’événement SelectionChanged. Renseignez la zone de texte avec **listBox_SelectionChanged**. Cette opération ajoute un stub pour un gestionnaire d’événement SelectionChanged et affecte à l’événement.  
  
3.  Implémentez la méthode TrackSelection(). Étant donné que vous devez obtenir le <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>services, vous devez rendre le <xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A>accessible par le TodoWindowControl.</xref:Microsoft.VisualStudio.Shell.WindowPane.GetService%2A> </xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection></xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Ajoutez la méthode suivante à la classe TodoWindow :  
  
    ```  
    internal object GetVsService(Type service)  
    {  
        return GetService(service);  
    }  
    ```  
  
4.  Ajoutez les instructions using vers TodoWindowControl.xaml.cs :  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    ```  
  
5.  Remplissez le Gestionnaire d’événement SelectionChanged comme suit :  
  
    ```  
    private void listBox_SelectionChanged(object sender, SelectionChangedEventArgs e)  
    {  
        TrackSelection();  
    }  
    ```  
  
6.  À présent, renseignez la fonction TrackSelection, qui fournit l’intégration avec les **propriétés** fenêtre. Cette fonction est appelée lorsque l’utilisateur ajoute un élément à la zone de liste ou clique sur un élément dans la zone de liste. Il ajoute le contenu de la zone de liste à un SelectionContainer et transmet le SelectionContainer à la **propriétés** la fenêtre <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A>Gestionnaire d’événements.</xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> Le service TrackSelection effectue le suivi des objets sélectionnés dans l’interface utilisateur (IU) et affiche leurs propriétés  
  
    ```c#  
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
  
     Maintenant que vous avez une classe qui le **propriétés** fenêtre peut utiliser, vous pouvez intégrer le **propriétés** fenêtre avec la fenêtre outil. Lorsque l’utilisateur clique sur un élément dans la zone de liste dans la fenêtre outil, la **propriétés** fenêtre doit être mis à jour en conséquence. De même, lorsque l’utilisateur modifie un élément ToDo de la **propriétés** fenêtre, l’élément associé doit être mis à jour.  
  
7.  Maintenant, ajoutez le reste du code de la fonction UpdateList dans TodoWindowControl.xaml.cs. Il doit supprimer et rajouter TodoItem modifié à partir de la zone de liste.  
  
    ```c#  
    public void UpdateList(TodoItem item)  
    {  
        var index = listBox.SelectedIndex;  
        listBox.Items.RemoveAt(index);  
        listBox.Items.Insert(index, item);  
        listBox.SelectedItem = index;  
    }  
    ```  
  
8.  Testez votre code. Générez le projet et commencez le débogage. L’instance expérimentale doit apparaître.  
  
9. Ouvrez la **Outils / Options** pages. Vous devriez voir la catégorie de tâches dans le volet gauche. Les catégories sont répertoriées dans alphabétique, donc sous le Ts.  
  
10. Sur la page options de la tâche, vous devez voir la propriété DaysAhead la valeur **0**. Remplacez-la par **2**.  
  
11. Sur la vue / menu autres fenêtres, ouvrez **TodoWindow**. Type **EndDate** dans la zone de texte et cliquez sur **ajouter**.  
  
12. Dans la zone de liste, vous devez voir une date ultérieure à aujourd'hui de deux jours.  
  
## <a name="add-text-to-the-output-window-and-items-to-the-task-list"></a>Ajouter du texte dans la fenêtre Sortie et les éléments à la liste des tâches  
 Pour le **liste des tâches**, vous créer un nouvel objet de type de tâche, puis ajoutez cet objet de tâche à la **liste des tâches** en appelant sa méthode Add. Pour écrire dans le **sortie** fenêtre, vous appelez sa méthode GetPane pour obtenir un objet de volet, puis vous appelez la méthode OutputString de l’objet du volet.  
  
1.  Dans TodoWindowControl.xaml.cs, dans le `button1_Click` (méthode), ajouter du code pour obtenir le **général** volet de la **sortie** fenêtre (qui est la valeur par défaut) et l’écriture. La méthode doit ressembler à ceci :  
  
    ```c#  
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
  
2.  Pour ajouter des éléments à la liste des tâches, vous devez un pour ajouter une classe imbriquée à la classe TodoWindowControl. La classe imbriquée doit dériver de <xref:Microsoft.VisualStudio.Shell.TaskProvider>.</xref:Microsoft.VisualStudio.Shell.TaskProvider> Ajoutez le code suivant à la fin de la classe TodoWindowControl.  
  
    ```c#  
    [Guid("72de1eAD-a00c-4f57-bff7-57edb162d0be")]  
    public class TodoWindowTaskProvider : TaskProvider  
    {  
        public TodoWindowTaskProvider(IServiceProvider sp)  
            : base(sp)  
        {  
        }  
    }  
    ```  
  
3.  Ensuite, ajoutez une référence à TodoTaskProvider privée et une méthode CreateProvider() à la classe TodoWindowControl. Le code doit ressembler à ceci :  
  
    ```c#  
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
  
4.  Ajoutez ClearError(), ce qui efface la liste des tâches, et ReportError(), qui ajoute une entrée à la liste des tâches, à la classe TodoWindowControl.  
  
    ```c#  
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
  
5.  À présent implémenter la méthode CheckForErrors, comme suit.  
  
    ```c#  
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
  
## <a name="trying-it-out"></a>Vous l’essayez  
  
1.  Générez le projet et commencez le débogage. L’instance expérimentale s’affiche.  
  
2.  Ouvrez la TodoWindow (**affichage / autres fenêtres / TodoWindow**).  
  
3.  Tapez quelque chose dans la zone de texte, puis cliquez sur **ajouter**.  
  
     Une date d’échéance 2 jours après que aujourd'hui est ajouté à la zone de liste. Aucune des erreurs ne sont générées et le **liste des tâches** (**afficher / tâches liste**) ne doit avoir aucune entrée.  
  
4.  Maintenant modifier le paramètre sur le **Outils / Options / ToDo** page de **2** à **0**.  
  
5.  Tapez un autre élément dans le **TodoWindow** , puis **ajouter** à nouveau. Cela déclenche une erreur, ainsi qu’une entrée dans le **liste des tâches**.  
  
     Lorsque vous ajoutez des éléments, la date initiale est définie à présent plus de 2 jours.  
  
6.  Sur le **affichage** menu, cliquez sur **sortie** pour ouvrir le **sortie** fenêtre.  
  
     Notez que chaque fois que vous ajoutez un élément, un message s’affiche dans le **liste des tâches** volet.  
  
7.  Cliquez sur un des éléments dans la zone de liste.  
  
     Le **propriétés** affiche les deux propriétés de l’élément.  
  
8.  Modifiez l’une des propriétés et appuyez sur ENTRÉE.  
  
     L’élément est mis à jour dans la zone de liste.
