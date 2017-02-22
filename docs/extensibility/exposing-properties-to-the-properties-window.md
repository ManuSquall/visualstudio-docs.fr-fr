---
title: "Exposition de propri&#233;t&#233;s dans la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Propriétés (Visual Studio SDK), exposant dans l'Explorateur de propriétés"
  - "Propriétés (Visual Studio SDK)"
  - "Explorateur de propriétés, exposer des propriétés"
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Exposition de propri&#233;t&#233;s dans la fen&#234;tre Propri&#233;t&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette procédure expose les propriétés publiques d'un objet pour le **propriétés** fenêtre. Les modifications que vous apportez à ces propriétés sont répercutées dans le **propriétés** fenêtre.  
  
## Composants requis  
 À partir de Visual Studio 2015, vous n'installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d'installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d'informations, consultez [L'installation du Kit de développement logiciel de Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Exposition de propriétés dans la fenêtre Propriétés  
 Dans cette section, vous créez une fenêtre Outil personnalisée et afficher les propriétés publiques de l'objet du volet de fenêtre associée dans le **propriétés** fenêtre.  
  
#### Pour exposer les propriétés dans la fenêtre Propriétés  
  
1.  Chaque extension de Visual Studio démarre avec un projet de déploiement VSIX qui contient les composants d'extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `MyObjectPropertiesExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **Nouveau projet** boîte de dialogue sous **Visual C\# \/ extensibilité**.  
  
2.  Ajouter une fenêtre outil en ajoutant un modèle d'élément de fenêtre de l'outil personnalisé nommé `MyToolWindow`. Dans le **l'Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter \/ nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual C\# \/ extensibilité** et sélectionnez **fenêtre de l'outil personnalisé**. Dans le **nom** en bas de la boîte de dialogue, modifiez le nom du fichier à `MyToolWindow.cs`. Pour plus d'informations sur la création d'une fenêtre Outil personnalisée, consultez [Création d'une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Ouvrez MyToolWindow.cs et ajoutez l'instruction using :  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Ajoutez maintenant les champs suivants à la `MyToolWindow` classe.  
  
    ```c#  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Ajoutez le code suivant à la classe MyToolWindow.  
  
    ```c#  
    private ITrackSelection TrackSelection  
    {  
        get  
        {  
            if (trackSel == null)  
                trackSel =  
                   GetService(typeof(STrackSelection)) as ITrackSelection;  
            return trackSel;  
        }  
    }  
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Le `TrackSelection` propriété utilise `GetService` pour obtenir un `STrackSelection` service, qui offre une <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Le `OnToolWindowCreated` Gestionnaire d'événements et `SelectList` méthode forment une liste d'objets sélectionnés qui contient uniquement l'outil fenêtre volet objet lui\-même. Le `UpdateSelection` méthode indique le **propriétés** fenêtre pour afficher les propriétés publiques du volet de fenêtre outil.  
  
6.  Générez le projet et commencez le débogage. L'instance expérimentale de Visual Studio doit s'afficher.  
  
7.  Si le **propriétés** fenêtre n'est pas visible, ouvrez\-le en appuyant sur F4.  
  
8.  Ouvrez la **MyToolWindow** fenêtre. Vous pouvez le trouver dans **affichage \/ autres fenêtres**.  
  
     La fenêtre s'ouvre et les propriétés publiques du volet de fenêtre apparaissent dans le **propriétés** fenêtre.  
  
9. Modifier la **légende** propriété dans le **propriétés** fenêtre **Mes propriétés de l'objet**.  
  
     La légende de fenêtre MyToolWindow change en conséquence.  
  
## Exposition de propriétés de la fenêtre outil  
 Dans cette section, vous ajoutez une fenêtre outil et exposez ses propriétés. Les modifications apportées aux propriétés sont répercutées dans le **propriétés** fenêtre.  
  
#### Pour exposer les propriétés de la fenêtre outil  
  
1.  Ouvrez MyToolWindow.cs et ajoutez la propriété booléenne publique IsChecked à la classe MyToolWindow.  
  
    ```c#  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Cette propriété obtient son état à partir de la case à cocher WPF que vous créerez ultérieurement.  
  
2.  Ouvrez MyToolWindowControl.xaml.cs et remplacez le constructeur MyToolWindowControl par le code suivant.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Cela donne `MyToolWindowControl` l'accès à la `MyToolWindow` volet.  
  
3.  Dans MyToolWindow.cs, modifiez le `MyToolWindow` constructeur comme suit :  
  
    ```c#  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Passez en mode conception de MyToolWindowControl.  
  
5.  Le bouton Supprimer et ajouter une case à cocher de la **boîte à outils** dans l'angle supérieur gauche.  
  
6.  Ajoutez les événements Checked et Unchecked. Sélectionnez la case à cocher en mode design. Dans le **propriétés** fenêtre, cliquez sur le bouton de gestionnaires d'événements \(en haut à droite de la **propriétés** fenêtre\). Recherchez **Checked** et type **checkbox\_Checked** dans la zone de texte, puis recherchez **Unchecked** et type **checkbox\_Unchecked** dans la zone de texte.  
  
7.  Ajoutez les gestionnaires d'événements de case à cocher :  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = true;  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.UpdateSelection();  
    }  
    ```  
  
8.  Générez le projet et commencez le débogage.  
  
9. Dans l'instance expérimentale, ouvrez le **MyToolWindow** fenêtre.  
  
     Rechercher les propriétés de la fenêtre dans le **propriétés** fenêtre. Le **IsChecked** propriété apparaît en bas de la fenêtre, sous le **Mes propriétés** catégorie.  
  
10. Activer la case à cocher dans le **MyToolWindow** fenêtre.**IsChecked** dans les **propriétés** fenêtre change à **True**. Désactivez la case à cocher dans le **MyToolWindow** fenêtre.**IsChecked** dans les **propriétés** fenêtre change à **False**. Modifiez la valeur de **IsChecked** dans les **propriétés** fenêtre. La case à cocher dans le **MyToolWindow** fenêtre change pour correspondre à la nouvelle valeur.  
  
    > [!NOTE]
    >  Si vous devez supprimer un objet qui est affiché dans le **propriétés** fenêtre, appelez `OnSelectChange` avec un `null` conteneur de sélection du premier. Après avoir supprimé la propriété ou l'objet, vous pouvez modifier dans un conteneur de sélection qui a mis à jour <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> et <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> répertorie.  
  
## Modification des listes de sélection  
 Dans cette section, vous ajoutez une liste de sélection d'une classe de propriété de base et l'interface de la fenêtre outil permet de choisir quelle liste de sélection à afficher.  
  
#### Pour modifier les listes de sélection  
  
1.  Ouvrez MyToolWindow.cs et ajoutez une classe publique nommée `Simple`.  
  
    ```c#  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
        {  
            get { return someText; }  
            set { someText = value; }  
        }  
  
        [Category("My Properties")]  
        [Description("Read-only property")]  
        public bool ReadOnly  
        {  
            get { return false; }  
        }  
    }  
    ```  
  
2.  Ajouter une propriété SimpleObject à la classe MyToolWindow, ainsi que deux méthodes pour basculer le **propriétés** entre le volet de sélection de la fenêtre et la `Simple` objet.  
  
    ```c#  
    private Simple simpleObject = null;  
    public Simple SimpleObject  
    {  
        get  
        {  
            if (simpleObject == null) simpleObject = new Simple();  
            return simpleObject;  
        }  
    }  
  
    public void SelectSimpleList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(SimpleObject);  
        SelectList(listObjects);  
    }  
  
    public void SelectThisList()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
3.  Dans MyToolWindowControl.cs, remplacez les gestionnaires de case à cocher avec ces lignes de code :  
  
    ```c#  
    private void checkbox_Checked(object sender, RoutedEventArgs e)  
     {  
        pane.IsChecked = true;  
        pane.SelectSimpleList();  
        pane.UpdateSelection();  
    }  
    private void checkbox_Unchecked(object sender, RoutedEventArgs e)  
    {  
        pane.IsChecked = false;  
        pane.SelectThisList();  
        pane.UpdateSelection();  
    }  
    ```  
  
4.  Générez le projet et commencez le débogage.  
  
5.  Dans l'instance expérimentale, ouvrez le **MyToolWindow** fenêtre.  
  
6.  Activez la case à cocher dans le **MyToolWindow** fenêtre. Le **propriétés** affiche les `Simple` Propriétés, de l'objet **SomeText** et **ReadOnly**. Désactivez la case à cocher. Les propriétés publiques de la fenêtre s'affichent dans le **propriétés** fenêtre.  
  
    > [!NOTE]
    >  Le nom complet de **SomeText** est **Mes texte**.  
  
## Meilleures pratiques  
 Dans cette procédure pas à pas, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est implémentée afin que la collection d'objets pouvant être sélectionnés et la collection d'objets sélectionnés sont la même collection. Seul l'objet sélectionné apparaît dans la liste de l'Explorateur de propriétés. Pour une implémentation de ISelectionContainer plus complète, consultez les exemples de Reference.ToolWindow.  
  
 Fenêtres Outil de Visual Studio sont conservés entre les sessions Visual Studio. Pour plus d'informations sur la conservation de l'état de la fenêtre outil, consultez <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Voir aussi  
 [Étendre les propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)