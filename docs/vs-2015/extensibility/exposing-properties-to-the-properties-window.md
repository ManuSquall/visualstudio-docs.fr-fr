---
title: Exposition des propriétés à la fenêtre Propriétés | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
caps.latest.revision: 37
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c28a0520680951920ee19e91f3df098066f432dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839393"
---
# <a name="exposing-properties-to-the-properties-window"></a>Exposition des propriétés dans la fenêtre Propriétés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette procédure pas à pas expose les propriétés publiques d’un objet dans la fenêtre **Propriétés** . Les modifications que vous apportez à ces propriétés sont répercutées dans la fenêtre **Propriétés** .  
  
## <a name="prerequisites"></a>Prérequis  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="exposing-properties-to-the-properties-window"></a>Exposition des propriétés dans la fenêtre Propriétés  
 Dans cette section, vous allez créer une fenêtre outil personnalisée et afficher les propriétés publiques de l’objet volet de fenêtre associé dans la fenêtre **Propriétés** .  
  
#### <a name="to-expose-properties-to-the-properties-window"></a>Pour exposer des propriétés au Fenêtre Propriétés  
  
1. Chaque extension Visual Studio commence par un projet de déploiement VSIX qui contiendra les ressources d’extension. Créez un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projet VSIX nommé `MyObjectPropertiesExtension` . Vous pouvez trouver le modèle de projet VSIX dans la boîte de dialogue **nouveau projet** sous **Visual C#/extensibilité**.  
  
2. Ajoutez une fenêtre outil en ajoutant un modèle d’élément de fenêtre outil personnalisé nommé `MyToolWindow` . Dans le **Explorateur de solutions**, cliquez avec le bouton droit sur le nœud du projet et sélectionnez **Ajouter/nouvel élément**. Dans la **boîte de dialogue Ajouter un nouvel élément**, accédez à **éléments Visual C#/extensibilité** , puis sélectionnez **fenêtre outil personnalisée**. Dans le champ **nom** en bas de la boîte de dialogue, remplacez le nom de fichier par `MyToolWindow.cs` . Pour plus d’informations sur la création d’une fenêtre outil personnalisée, consultez [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3. Ouvrez MyToolWindow.cs et ajoutez l’instruction using suivante :  
  
    ```  
    using System.Collections;  
    using System.ComponentModel;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
4. Ajoutez maintenant les champs suivants à la `MyToolWindow` classe.  
  
    ```csharp  
    private ITrackSelection trackSel;  
    private SelectionContainer selContainer;  
  
    ```  
  
5. Ajoutez le code suivant à la classe MyToolWindow.  
  
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
  
     La `TrackSelection` propriété utilise `GetService` pour obtenir un `STrackSelection` service, qui fournit une <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interface. Le `OnToolWindowCreated` Gestionnaire d’événements et la `SelectList` méthode créent ensemble une liste d’objets sélectionnés qui contient uniquement l’objet du volet de la fenêtre outil lui-même. La `UpdateSelection` méthode indique à la fenêtre **Propriétés** d’afficher les propriétés publiques du volet de la fenêtre outil.  
  
6. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
7. Si la fenêtre **Propriétés** n’est pas visible, ouvrez-la en appuyant sur F4.  
  
8. Ouvrez la fenêtre **MyToolWindow** . Vous pouvez le trouver dans **affichage/autres fenêtres**.  
  
     La fenêtre s’ouvre et les propriétés publiques du volet de la fenêtre s’affichent dans la fenêtre **Propriétés** .  
  
9. Remplacez la propriété **Caption** de la fenêtre **Propriétés** par **Mes propriétés d’objet**.  
  
     La légende de la fenêtre MyToolWindow change en conséquence.  
  
## <a name="exposing-tool-window-properties"></a>Exposition des propriétés de la fenêtre outil  
 Dans cette section, vous allez ajouter une fenêtre outil et exposer ses propriétés. Les modifications que vous apportez aux propriétés sont répercutées dans la fenêtre **Propriétés** .  
  
#### <a name="to-expose-tool-window-properties"></a>Pour exposer les propriétés d’une fenêtre outil  
  
1. Ouvrez MyToolWindow.cs et ajoutez la propriété booléenne publique IsChecked à la classe MyToolWindow.  
  
    ```csharp  
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
  
     Cette propriété obtient son état à partir de la case à cocher WPF que vous allez créer ultérieurement.  
  
2. Ouvrez MyToolWindowControl.xaml.cs et remplacez le constructeur MyToolWindowControl par le code suivant.  
  
    ```vb  
    private MyToolWindow pane;  
    public MyToolWindowControl(MyToolWindow pane)  
    {  
        InitializeComponent();  
        this.pane = pane;  
        checkBox.IsChecked = false;  
    }  
    ```  
  
     Cela donne `MyToolWindowControl` accès au `MyToolWindow` volet.  
  
3. Dans MyToolWindow.cs, modifiez le `MyToolWindow` constructeur comme suit :  
  
    ```csharp  
    base.Content = new MyToolWindowControl(this);  
    ```  
  
4. Passez en mode création de MyToolWindowControl.  
  
5. Supprimez le bouton et ajoutez une case à cocher de la **boîte à outils** dans le coin supérieur gauche.  
  
6. Ajoutez les événements cochés et non vérifiés. Activez la case à cocher en mode conception. Dans la fenêtre **Propriétés** , cliquez sur le bouton gestionnaires d’événements (en haut à droite de la fenêtre **Propriétés** ). Recherchez **activé** et tapez **checkbox_Checked** dans la zone de texte, puis recherchez **non coché** et tapez **checkbox_Unchecked** dans la zone de texte.  
  
7. Ajoutez les gestionnaires d’événements de case à cocher :  
  
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
  
8. Générez le projet et commencez le débogage.  
  
9. Dans l’instance expérimentale, ouvrez la fenêtre **MyToolWindow** .  
  
     Recherchez les propriétés de la fenêtre dans la fenêtre **Propriétés** . La propriété **IsChecked** s’affiche au bas de la fenêtre, sous la catégorie **Mes propriétés** .  
  
10. Activez la case à cocher dans la fenêtre **MyToolWindow** . **IsChecked** dans la fenêtre **Propriétés** prend la **valeur true**. Désactivez la case à cocher dans la fenêtre **MyToolWindow** . **IsChecked** dans la fenêtre **Propriétés** devient **false**. Modifiez la valeur de **IsChecked** dans la fenêtre **Propriétés** . La case à cocher dans la fenêtre **MyToolWindow** est modifiée pour correspondre à la nouvelle valeur.  
  
    > [!NOTE]
    > Si vous devez supprimer un objet affiché dans la fenêtre **Propriétés** , appelez `OnSelectChange` d’abord avec un `null` conteneur de sélection. Après avoir supprimé la propriété ou l’objet, vous pouvez passer à un conteneur de sélection qui contient <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> des listes et mises à jour <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> .  
  
## <a name="changing-selection-lists"></a>Modification des listes de sélection  
 Dans cette section, vous ajoutez une liste de sélection pour une classe de propriété de base et utilisez l’interface de la fenêtre outil pour choisir la liste de sélection à afficher.  
  
#### <a name="to-change-selection-lists"></a>Pour modifier des listes de sélection  
  
1. Ouvrez MyToolWindow.cs et ajoutez une classe publique nommée `Simple` .  
  
    ```csharp  
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
  
2. Ajoutez une propriété SimpleObject à la classe MyToolWindow, ainsi que deux méthodes pour basculer la sélection de la fenêtre **Propriétés** entre le volet de la fenêtre et l' `Simple` objet.  
  
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
  
3. Dans MyToolWindowControl.cs, remplacez les gestionnaires de cases à cocher par ces lignes de code :  
  
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
  
4. Générez le projet et commencez le débogage.  
  
5. Dans l’instance expérimentale, ouvrez la fenêtre **MyToolWindow** .  
  
6. Activez la case à cocher dans la fenêtre **MyToolWindow** . La fenêtre **Propriétés** affiche les `Simple` Propriétés de l’objet, **someText** et **ReadOnly**. Décochez la case. Les propriétés publiques de la fenêtre s’affichent dans la fenêtre **Propriétés** .  
  
    > [!NOTE]
    > Le nom d’affichage de **someText** est **My Text**.  
  
## <a name="best-practice"></a>Bonne pratique  
 Dans cette procédure pas à pas, <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> est implémenté afin que la collection d’objets sélectionnable et la collection d’objets sélectionnée soient identiques. Seul l’objet sélectionné s’affiche dans la liste de l’Explorateur de propriétés. Pour une implémentation plus complète de ISelectionContainer, consultez les exemples Reference. ToolWindow.  
  
 Les fenêtres Outil Visual Studio sont conservées entre les sessions Visual Studio. Pour plus d’informations sur la persistance de l’état de la fenêtre outil, consultez <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> .  
  
## <a name="see-also"></a>Voir aussi  
 [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)
