---
title: Ajout d’une fenêtre outil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ee669d2acd5bc69c7268b19ad04e9fa7b506e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633420"
---
# <a name="add-a-tool-window"></a>Ajouter une fenêtre outil

Dans cette procédure pas à pas, vous allez apprendre à créer une fenêtre outil et à l’intégrer dans Visual Studio de la manière suivante :

- Ajoutez un contrôle à la fenêtre outil.

- Ajoutez une barre d’outils à une fenêtre outil.

- Ajoutez une commande à la barre d’outils.

- Implémentez les commandes.

- Définissez la position par défaut de la fenêtre outil.

## <a name="prerequisites"></a>Configuration requise

Le kit de développement logiciel (SDK) Visual Studio est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Créer une fenêtre outil

1. Créez un projet nommé **FirstToolWin** à l’aide du modèle VSIX, puis ajoutez un modèle d’élément de fenêtre outil personnalisé nommé **FirstToolWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Ajouter un contrôle à la fenêtre outil

1. Supprimez le contrôle par défaut. Ouvrez *FirstToolWindowControl. Xaml* et supprimez l' **utilisateur click me !** disproportionnée.

2. Dans la **boîte à outils**, développez la section **tous les contrôles WPF** , puis faites glisser le contrôle **Media Element** vers le formulaire **FirstToolWindowControl** . Sélectionnez le contrôle et, dans la fenêtre **Propriétés** , nommez cet élément **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Ajouter une barre d’outils à la fenêtre outil
En ajoutant une barre d’outils de la manière suivante, vous garantissez que ses dégradés et couleurs sont cohérents avec le reste de l’IDE.

1. Dans **Explorateur de solutions**, ouvrez *FirstToolWindowPackage. vsct*. Le fichier *. vsct* définit les éléments de l’interface utilisateur graphique (GUI) dans votre fenêtre outil à l’aide de XML.

2. Dans la section `<Symbols>`, recherchez le nœud `<GuidSymbol>` dont l’attribut `name` est `guidFirstToolWindowPackageCmdSet`. Ajoutez les deux éléments `<IDSymbol>` suivants à la liste des éléments `<IDSymbol>` de ce nœud pour définir une barre d’outils et un groupe de barres d’outils.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Juste au-dessus de la section `<Buttons>`, créez une `<Menus>` section qui ressemble à ceci :

    ```xml
    <Menus>
        <Menu guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" priority="0x0000" type="ToolWindowToolbar">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
            <Strings>
                <ButtonText>Tool Window Toolbar</ButtonText>
                <CommandName>Tool Window Toolbar</CommandName>
            </Strings>
        </Menu>
    </Menus>
    ```

    Il existe différents types de menu. Ce menu est une barre d’outils dans une fenêtre outil, définie par son attribut `type`. Les paramètres `guid` et `id` composent l’ID complet de la barre d’outils. En général, le `<Parent>` d’un menu est le groupe conteneur. Toutefois, une barre d’outils est définie comme son propre parent. Par conséquent, le même identificateur est utilisé pour les éléments `<Menu>` et `<Parent>`. L’attribut `priority` est simplement' 0 '.

4. Les barres d’outils ressemblent à des menus de nombreuses façons. Par exemple, tout comme un menu peut avoir des groupes de commandes, les barres d’outils peuvent également avoir des groupes. (Dans les menus, les groupes de commandes sont séparés par des lignes horizontales. Sur les barres d’outils, les groupes ne sont pas séparés par des séparateurs visuels.)

    Ajoutez une section `<Groups>` qui contient un élément `<Group>`. Cela définit le groupe dont vous avez déclaré l’ID dans la section `<Symbols>`. Ajoutez la section `<Groups>` juste après la section `<Menus>`.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    En définissant le GUID et l’ID parents sur le GUID et l’ID de la barre d’outils, vous ajoutez le groupe à la barre d’outils.

## <a name="add-a-command-to-the-toolbar"></a>Ajouter une commande à la barre d’outils

Ajoutez une commande à la barre d’outils, qui s’affiche sous forme de bouton.

1. Dans la section `<Symbols>`, déclarez les éléments IDSymbol suivants juste après les déclarations de barre d’outils et de groupes de barres d’outils.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Ajoutez un élément Button à l’intérieur de la section `<Buttons>`. Cet élément apparaît dans la barre d’outils de la fenêtre outil, avec une icône de **recherche** (loupe).

    ```xml
    <Button guid="guidFirstToolWindowPackageCmdSet" id="cmdidWindowsMediaOpen" priority="0x0101" type="Button">
        <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID"/>
        <Icon guid="guidImages" id="bmpPicSearch" />
        <Strings>
            <CommandName>cmdidWindowsMediaOpen</CommandName>
            <ButtonText>Load File</ButtonText>
        </Strings>
    </Button>
    ```

3. Ouvrez *FirstToolWindowCommand.cs* et ajoutez les lignes suivantes dans la classe juste après les champs existants.

    ```csharp
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file
    public const uint cmdidWindowsMedia = 0x100;
    public const int cmdidWindowsMediaOpen = 0x132;
    public const int ToolbarID = 0x1000;
    ```

    Cela rend vos commandes disponibles dans le code.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Ajouter une propriété MediaPlayer à FirstToolWindowControl
À partir des gestionnaires d’événements pour les contrôles ToolBar, votre code doit être en mesure d’accéder au contrôle Media Player, qui est un enfant de la classe FirstToolWindowControl.

Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *FirstToolWindowControl. Xaml*, cliquez sur **afficher le code**, puis ajoutez le code suivant à la classe FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instancier la fenêtre outil et la barre d’outils
Ajoutez une barre d’outils et une commande de menu qui appelle la boîte de dialogue **ouvrir un fichier** et qui lit le fichier multimédia sélectionné.

1. Ouvrez *FirstToolWindow.cs* et ajoutez les directives de `using` suivantes :

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. À l’intérieur de la classe FirstToolWindow, ajoutez une référence publique au contrôle FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. À la fin du constructeur, définissez cette variable de contrôle sur le contrôle qui vient d’être créé.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Instanciez la barre d’outils dans le constructeur.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. À ce stade, le constructeur FirstToolWindow doit ressembler à ceci :

    ```csharp
    public FirstToolWindow() : base(null)
    {
        this.Caption = "FirstToolWindow";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
        control = new FirstToolWindowControl();
        base.Content = control;
        this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.ToolbarID);
            this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    }
    ```

6. Ajoutez la commande de menu à la barre d’outils. Dans la classe FirstToolWindowCommand.cs, ajoutez la directive using suivante :

    ```csharp
    using System.Windows.Forms;
    ```

7. Dans la classe FirstToolWindowCommand, ajoutez le code suivant à la fin de la méthode ShowToolWindow (). La commande ButtonHandler sera implémentée dans la section suivante.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Pour implémenter une commande de menu dans la fenêtre outil

1. Dans la classe FirstToolWindowCommand, ajoutez une méthode ButtonHandler qui appelle la boîte de dialogue **ouvrir un fichier** . Lorsqu’un fichier a été sélectionné, il lit le fichier multimédia.

2. Dans la classe FirstToolWindowCommand, ajoutez une référence privée à la fenêtre FirstToolWindow qui est créée dans la méthode FindToolWindow ().

    ```csharp
    private FirstToolWindow window;
    ```

3. Modifiez la méthode ShowToolWindow () pour définir la fenêtre que vous avez définie ci-dessus (afin que le gestionnaire de commandes ButtonHandler puisse accéder au contrôle de fenêtre. Voici la méthode ShowToolWindow () complète.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        window = (FirstToolWindow) this.package.FindToolWindow(typeof(FirstToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create tool window");
        }

        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommandguidFirstToolWindowPackageCmdSet),
            FirstToolWindowCommand.cmdidWindowsMediaOpen);
        var menuItem = new MenuCommand(new EventHandler(
            ButtonHandler), toolbarbtnCmdID);
        mcs.AddCommand(menuItem);
    }
    ```

4. Ajoutez la méthode ButtonHandler. Il crée un OpenFileDialog pour que l’utilisateur spécifie le fichier multimédia à lire, puis lit le fichier sélectionné.

    ```csharp
    private void ButtonHandler(object sender, EventArgs arguments)
    {
        OpenFileDialog openFileDialog = new OpenFileDialog();
        DialogResult result = openFileDialog.ShowDialog();
        if (result == DialogResult.OK)
        {
            window.control.MediaPlayer.Source = new System.Uri(openFileDialog.FileName);
        }
    }
    ```

## <a name="set-the-default-position-for-the-tool-window"></a>Définir la position par défaut de la fenêtre outil

Ensuite, spécifiez un emplacement par défaut dans l’IDE pour la fenêtre outil. Les informations de configuration de la fenêtre outil se trouvent dans le fichier *FirstToolWindowPackage.cs* .

1. Dans *FirstToolWindowPackage.cs*, recherchez l’attribut <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> sur la classe `FirstToolWindowPackage`, qui passe le type FirstToolWindow au constructeur. Pour spécifier une position par défaut, vous devez ajouter des paramètres à l’exemple de constructeur suivant.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Le premier paramètre nommé est `Style` et sa valeur est `Tabbed`, ce qui signifie que la fenêtre est un onglet dans une fenêtre existante. La position d’ancrage est spécifiée par le paramètre `Window`, n ce cas, le GUID du **Explorateur de solutions**.

    > [!NOTE]
    > Pour plus d’informations sur les types de fenêtres dans l’IDE, consultez <xref:EnvDTE.vsWindowType>.

## <a name="test-the-tool-window"></a>Tester la fenêtre outil

1. Appuyez sur **F5** pour ouvrir une nouvelle instance de la build expérimentale Visual Studio.

2. Dans le menu **affichage** , pointez sur **autres fenêtres** , puis cliquez sur la **première fenêtre outil**.

    La fenêtre de l’outil Media Player doit s’ouvrir à la même position que **Explorateur de solutions**. S’il apparaît toujours à la même position que précédemment, réinitialisez la disposition de fenêtre (**fenêtre/réinitialiser la disposition de fenêtre**).

3. Cliquez sur le bouton (l’icône de **recherche** ) dans la fenêtre outil. Sélectionnez un fichier audio ou vidéo pris en charge, par exemple, *C:\Windows\Media\chimes.wav*, puis appuyez sur **ouvrir**.

    Vous devez entendre le son de la sonnerie.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
