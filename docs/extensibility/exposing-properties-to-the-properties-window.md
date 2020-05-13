---
title: Exposer les propriétés à la fenêtre des propriétés (fr) Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], exposing in Property Browser
- properties [Visual Studio SDK]
- Property Browser, exposing properties
ms.assetid: 47f295b5-1ca5-4e7b-bb52-7b926b136622
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f84962628ae550676e2c2eeb10c0f3baeca1bb58
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711829"
---
# <a name="expose-properties-to-the-properties-window"></a>Exposer les propriétés à la fenêtre Propriétés

Cette procédure pas à pas expose les propriétés publiques d’un objet à la fenêtre **Propriétés.** Les modifications que vous faites à ces propriétés sont reflétées dans la fenêtre **propriétés.**

## <a name="prerequisites"></a>Prérequis

A partir de Visual Studio 2015, vous n’installez pas le Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="expose-properties-to-the-properties-window"></a>Exposer les propriétés à la fenêtre Propriétés

Dans cette section, vous créez une fenêtre d’outil personnalisée et affichez les propriétés publiques de l’objet de vitre associé dans la fenêtre **Propriétés.**

### <a name="to-expose-properties-to-the-properties-window"></a>Exposer les propriétés à la fenêtre Propriétés

1. Chaque extension Visual Studio commence par un projet de déploiement VSIX, qui contiendra les actifs d’extension. Créer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un projet `MyObjectPropertiesExtension`VSIX nommé . Vous pouvez trouver le modèle de projet VSIX dans le dialogue **du nouveau projet** en recherchant "vsix".

2. Ajoutez une fenêtre d’outil en ajoutant `MyToolWindow`un modèle d’élément de fenêtre d’outil personnalisé nommé . Dans la **Solution Explorer**, cliquez à droite sur le nœud du projet et sélectionnez **Ajouter** > **un nouvel article**. Dans le **dialogue Add New Item**, rendez-vous sur Visual **C’Items** > **Extensibility** et **sélectionnez Custom Tool Window**. Dans le champ **Nom** au bas du dialogue, changer le nom du fichier pour *MyToolWindow.cs*. Pour plus d’informations sur la façon de créer une fenêtre d’outil personnalisée, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Ouvrez *MyToolWindow.cs* et ajoutez l’instruction suivante à l’aide de :

   ```csharp
   using System.Collections;
   using System.ComponentModel;
   using Microsoft.VisualStudio.Shell.Interop;
   ```

4. Ajoutez maintenant les champs `MyToolWindow` suivants à la classe.

   ```csharp
   private ITrackSelection trackSel;
   private SelectionContainer selContainer;

   ```

5. Ajoutez le code suivant à la classe `MyToolWindow` .

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

    La `TrackSelection` propriété `GetService` utilise `STrackSelection` pour obtenir un <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> service, qui fournit une interface. Le `OnToolWindowCreated` gestionnaire `SelectList` d’événements et la méthode créent ensemble une liste d’objets sélectionnés qui ne contient que l’objet de vitre d’outil lui-même. La `UpdateSelection` méthode indique à la fenêtre **Properties** d’afficher les propriétés publiques de la vitre de l’outil.

6. Générez le projet et commencez le débogage. L’exemple expérimental de Visual Studio devrait apparaître.

7. Si la fenêtre **Propriétés** n’est pas visible, ouvrez-la en appuyant sur **F4**.

8. Ouvrez la fenêtre **MyToolWindow.** Vous pouvez le trouver dans **Voir** > **d’autres Fenêtres**.

    La fenêtre s’ouvre et les propriétés publiques de la vitre apparaissent dans la fenêtre **Propriétés.**

9. Modifier la propriété **caption** dans la fenêtre **Propriétés** à **Mes propriétés d’objet**.

     La légende de la fenêtre MyToolWindow change en conséquence.

## <a name="expose-tool-window-properties"></a>Exposer les propriétés des fenêtres de l’outil

Dans cette section, vous ajoutez une fenêtre d’outil et exposez ses propriétés. Les modifications que vous faites aux propriétés sont reflétées dans la fenêtre **Propriétés.**

### <a name="to-expose-tool-window-properties"></a>Exposer les propriétés des fenêtres d’outils

1. Ouvrez *MyToolWindow.cs*, et ajoutez la propriété publique `MyToolWindow` boolean IsChecked à la classe.

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

     Cette propriété obtient son état de la case à cocher WPF que vous allez créer plus tard.

2. Ouvrez *MyToolWindowControl.xaml.cs* et remplacez le constructeur MyToolWindowControl par le code suivant.

    ```vb
    private MyToolWindow pane;
    public MyToolWindowControl(MyToolWindow pane)
    {
        InitializeComponent();
        this.pane = pane;
        checkBox.IsChecked = false;
    }
    ```

     Cela `MyToolWindowControl` donne accès `MyToolWindow` à la vitre.

3. En *MyToolWindow.cs*, changer `MyToolWindow` le constructeur comme suit:

    ```csharp
    base.Content = new MyToolWindowControl(this);
    ```

4. Changement à la vue de conception de MyToolWindowControl.

5. Supprimer le bouton et ajouter une case à cocher de la boîte à **outils** au coin supérieur gauche.

6. Ajoutez les événements vérifiés et non contrôlés. Sélectionnez la case à cocher dans la vue de conception. Dans la fenêtre **Propriétés,** cliquez sur le bouton des gestionnaires d’événements (en haut à droite de la fenêtre **Propriétés).** Trouver **checked** et taper **checkbox_Checked** dans la boîte de texte, puis trouver **unchecked** et **tapez checkbox_Unchecked** dans la boîte de texte.

7. Ajouter les gestionnaires d’événements de la case à cocher :

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

9. Dans le cas expérimental, ouvrez la fenêtre **MyToolWindow.**

     Recherchez les propriétés de la fenêtre dans la fenêtre **Propriétés.** La propriété **IsChecked** apparaît au bas de la fenêtre, dans la catégorie **My Properties.**

10. Cochez la case à cocher dans la fenêtre **MyToolWindow.** **IsChecked** dans la fenêtre **propriétés** change à **True**. Dégagez la case à cocher dans la fenêtre **MyToolWindow.** **IsChecked** dans la fenêtre **propriétés** change de **faux**. Modifier la valeur **d’IsChecked** dans la fenêtre **Propriétés.** La case à cocher de la fenêtre **MyToolWindow** change pour correspondre à la nouvelle valeur.

    > [!NOTE]
    > Si vous devez disposer d’un objet qui `OnSelectChange` est `null` affiché dans la fenêtre **Propriétés,** appelez d’abord avec un conteneur de sélection. Après avoir éliminé la propriété ou l’objet, vous <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectableObjects%2A> <xref:Microsoft.VisualStudio.Shell.SelectionContainer.SelectedObjects%2A> pouvez passer à un conteneur de sélection qui a mis à jour et énumère.

## <a name="change-selection-lists"></a>Modifier les listes de sélection

 Dans cette section, vous ajoutez une liste de sélection pour une classe de propriété de base et utilisez l’interface de fenêtre d’outil pour choisir la liste de sélection à afficher.

### <a name="to-change-selection-lists"></a>Modifier les listes de sélection

1. Ouvrez *MyToolWindow.cs* et ajoutez une `Simple`classe publique nommée .

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

2. Ajoutez `SimpleObject` une propriété `MyToolWindow` à la classe, plus deux méthodes pour changer `Simple` la sélection de fenêtre **Propriétés** entre la vitre et l’objet.

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

3. Dans *MyToolWindowControl.cs*, remplacez les manutentionnaires de la case à cocher par ces lignes de code :

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

5. Dans le cas expérimental, ouvrez la fenêtre **MyToolWindow.**

6. Sélectionnez la case à cocher dans la fenêtre **MyToolWindow.** La fenêtre **Propriétés** affiche les propriétés de l’objet, `Simple` **SomeText** et **ReadOnly**. Désactivez la case à cocher. Les propriétés publiques de la fenêtre apparaissent dans la fenêtre **Propriétés.**

    > [!NOTE]
    > Le nom d’affichage de **SomeText** est **Mon texte**.

## <a name="best-practice"></a>Bonne pratique

Dans cette procédure pas <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> à pas, est implémenté de sorte que la collection d’objets sélectionnables et la collection d’objets sélectionnés sont la même collection. Seul l’objet sélectionné apparaît dans la liste des navigateurs de propriété. Pour une mise en œuvre ISelectionContainer plus complète, voir les échantillons de Reference.ToolWindow.

Les fenêtres de l’outil Visual Studio persistent entre les sessions Visual Studio. Pour plus d’informations sur la <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>persistance de l’état de fenêtre d’outil, voir .

## <a name="see-also"></a>Voir aussi

- [Étendre les propriétés et la fenêtre de la propriété](../extensibility/extending-properties-and-the-property-window.md)
