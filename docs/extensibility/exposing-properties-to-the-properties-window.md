---
title: Exposition de propriétés à la fenêtre Propriétés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 12dcb30374250ca7aa917cf19b3a01ba57862c6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134260"
---
# <a name="exposing-properties-to-the-properties-window"></a>Exposition de propriétés à la fenêtre Propriétés
Cette procédure pas à pas expose les propriétés publiques d’un objet pour le **propriétés** fenêtre. Les modifications apportées à ces propriétés sont répercutées dans le **propriétés** fenêtre.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Exposition de propriétés à la fenêtre Propriétés  
 Dans cette section, vous créez une fenêtre Outil personnalisée et afficher les propriétés publiques de l’objet de volet de fenêtre associée dans le **propriétés** fenêtre.  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Pour exposer des propriétés dans la fenêtre Propriétés  
  
1.  Chaque extension de Visual Studio commence par un projet de déploiement VSIX qui contient les composants d’extension. Créer un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projet VSIX nommé `MyObjectPropertiesExtension`. Vous pouvez trouver le modèle de projet VSIX dans le **nouveau projet** boîte de dialogue sous **Visual c# / extensibilité**.  
  
2.  Ajouter une fenêtre outil en ajoutant un modèle d’élément de fenêtre de l’outil personnalisé nommé `MyToolWindow`. Dans le **l’Explorateur de solutions**, cliquez sur le nœud du projet et sélectionnez **Ajouter / nouvel élément**. Dans le **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual c# / extensibilité** et sélectionnez **fenêtre de l’outil personnalisé**. Dans le **nom** au bas de la boîte de dialogue, modifiez le nom de fichier à `MyToolWindow.cs`. Pour plus d’informations sur la création d’une fenêtre Outil personnalisée, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Ouvrez MyToolWindow.cs et ajoutez le code suivant à l’aide d’instruction :  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4.  Maintenant ajouter les champs suivants à la `MyToolWindow` classe.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5.  Ajoutez le code suivant à la classe MyToolWindow.  
  
    ```csharp  
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
  
    public void UpdateSelection()  
    {  
        ITrackSelection track = TrackSelection;  
        if (track != null)  
            track.OnSelectChange((ISelectionContainer)selContainer);  
    }  
  
    public void SelectList(ArrayList list)  
    {  
        selContainer = new SelectionContainer(true, false);  
        selContainer.SelectableObjects = list;  
        selContainer.SelectedObjects = list;  
        UpdateSelection();  
    }  
  
    public override void OnToolWindowCreated()  
    {  
        ArrayList listObjects = new ArrayList();  
        listObjects.Add(this);  
        SelectList(listObjects);  
    }  
    ```  
  
     Le `TrackSelection` propriété utilise `GetService` pour obtenir un `STrackSelection` service, qui fournit un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Le `OnToolWindowCreated` Gestionnaire d’événements et `SelectList` méthode forment une liste des objets sélectionnés contenant uniquement l’objet fenêtre outil volet lui-même. Le `UpdateSelection` méthode indique le **propriétés** fenêtre pour afficher les propriétés publiques du volet de fenêtre outil.  
  
6.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
7.  Si le **propriétés** fenêtre n’est pas visible, ouvrez-la en appuyant sur F4.  
  
8.  Ouvrez le **MyToolWindow** fenêtre. Vous pouvez le trouver dans **affichage / autres fenêtres**.  
  
     La fenêtre s’ouvre et les propriétés publiques du volet de fenêtre qui s’affichent dans le **propriétés** fenêtre.  
  
9. Modifier la **légende** propriété dans le **propriétés** fenêtre **mes propriétés de l’objet**.  
  
     La légende de fenêtre MyToolWindow modifie en conséquence.  
  
## <a name="exposing-tool-window-properties"></a>Exposition de propriétés de la fenêtre outil  
 Dans cette section, vous ajoutez une fenêtre outil et exposez ses propriétés. Les modifications apportées aux propriétés sont répercutées dans le **propriétés** fenêtre.  
  
#### <a name="to-expose-tool-window-properties"></a>Pour exposer les propriétés de la fenêtre outil  
  
1.  Ouvrez MyToolWindow.cs et ajoutez la propriété booléenne publique IsChecked à la classe MyToolWindow.  
  
    ```csharp  
    [Category("My Properties")]  
    [Description("MyToolWindowControl properties")]  
    public bool IsChecked  
    {  
        get {  
            if (base.Content == null)  return false;  
            return (bool)(( MyToolWindowControl) base.Content).checkBox.IsChecked;   
        }  
        set {  
            ((MyToolWindowControl) base.Content).checkBox.IsChecked = value;  
        }  
    }  
    ```  
  
     Cette propriété obtient son état à partir de la case à cocher WPF que vous créerez ultérieurement.  
  
2.  Ouvrez MyToolWindowControl.xaml.cs et remplacez le constructeur de MyToolWindowControl par le code suivant.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Cela donne `MyToolWindowControl` l’accès à la `MyToolWindow` volet.  
  
3.  Dans MyToolWindow.cs, modifiez le `MyToolWindow` constructeur comme suit :  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4.  Modifier le mode design MyToolWindowControl.  
  
5.  Supprimez le bouton et ajoutez une case à cocher à partir de la **boîte à outils** dans le coin supérieur gauche.  
  
6.  Ajoutez les événements Checked et Unchecked. Sélectionnez la case à cocher dans la vue de conception. Dans le **propriétés** fenêtre, cliquez sur le bouton de gestionnaires d’événements (en haut à droite de la **propriétés** fenêtre). Rechercher **Checked** et type **checkbox_Checked** dans la zone de texte, puis recherchez **Unchecked** et type **checkbox_Unchecked** dans la zone de texte.  
  
7.  Ajoutez les gestionnaires d’événements de case à cocher :  
  
    ```csharp  
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
  
9. Dans l’instance expérimentale, ouvrez le **MyToolWindow** fenêtre.  
  
     Rechercher les propriétés de la fenêtre dans le **propriétés** fenêtre. Le **IsChecked** propriété apparaît en bas de la fenêtre, sous le **propriétés de My** catégorie.  
  
10. Activer la case à cocher dans la **MyToolWindow** fenêtre. **IsChecked** dans les **propriétés** fenêtre change pour **True**. Désactivez la case à cocher dans la **MyToolWindow** fenêtre. **IsChecked** dans les **propriétés** fenêtre change pour **False**. Modifiez la valeur de **IsChecked** dans les **propriétés** fenêtre. La case à cocher dans la **MyToolWindow** de fenêtre change pour correspondre à la nouvelle valeur.  
  
    > [!NOTE]
    >  Si vous devez supprimer un objet qui est affiché dans le **propriétés** fenêtre, appelez `OnSelectChange` avec un `null` le conteneur de sélection premier. Après avoir supprimé la propriété ou l’objet, vous pouvez modifier dans un conteneur de sélection qui a mis à jour <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> et <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> répertorie.  
  
## <a name="changing-selection-lists"></a>Modification des listes de sélection  
 Dans cette section, vous ajoutez une liste de sélection d’une classe de propriété de base et permet de choisir quelle liste de sélection pour afficher l’interface de la fenêtre outil.  
  
#### <a name="to-change-selection-lists"></a>Pour modifier les listes de sélection  
  
1.  Ouvrez MyToolWindow.cs et ajoutez une classe publique nommée `Simple`.  
  
    ```csharp  
    public class Simple  
    {  
        private string someText = "";  
  
        [Category("My Properties")]  
        [Description("Simple Properties")]  
        [DisplayName("My Text")]  
        public string SomeText  
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
  
2.  Ajouter une propriété SimpleObject à la classe MyToolWindow, ainsi que les deux méthodes pour basculer le **propriétés** entre le volet de sélection de la fenêtre et la `Simple` objet.  
  
    ```csharp  
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
  
3.  Dans MyToolWindowControl.cs, remplacez les gestionnaires de case à cocher avec ces lignes de code :  
  
    ```csharp  
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
  
5.  Dans l’instance expérimentale, ouvrez le **MyToolWindow** fenêtre.  
  
6.  Activez la case à cocher dans la **MyToolWindow** fenêtre. Le **propriétés** fenêtre affiche la `Simple` propriétés, de l’objet **SomeText** et **ReadOnly**. Désactivez la case à cocher. Les propriétés publiques de la fenêtre s’affichent dans le **propriétés** fenêtre.  
  
    > [!NOTE]
    >  Le nom complet de **SomeText** est **mon texte**.  
  
## <a name="best-practice"></a>Meilleures pratiques  
 Dans cette procédure pas à pas, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est implémentée afin que la collection d’objets pouvant être sélectionnées et de la collection d’objets sélectionnés sont la même collection. Seul l’objet sélectionné apparaît dans la liste de l’Explorateur de propriétés. Pour une implémentation de ISelectionContainer plus complète, consultez les exemples Reference.ToolWindow.  
  
 Fenêtres Outil Visual Studio persistent entre les sessions de Visual Studio. Pour plus d’informations sur la conservation de l’état de la fenêtre outil, consultez <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)