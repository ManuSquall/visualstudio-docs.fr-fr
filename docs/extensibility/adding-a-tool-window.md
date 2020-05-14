---
title: Ajout d’une fenêtre d’outil (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 573f01043d8b1b0c2293a3ebf6e0c246a8727d6a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740257"
---
# <a name="add-a-tool-window"></a>Ajouter une fenêtre d’outil

Dans ce pas-là, vous apprenez à créer une fenêtre d’outils et à l’intégrer dans Visual Studio de la manière suivante :

- Ajoutez un contrôle à la fenêtre de l’outil.

- Ajouter une barre d’outils à une fenêtre d’outils.

- Ajoutez une commande à la barre d’outils.

- Implémenter les commandes.

- Définissez la position par défaut pour la fenêtre d’outil.

## <a name="prerequisites"></a>Prérequis

Le Visual Studio SDK est inclus comme une fonctionnalité facultative dans la configuration Visual Studio. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-tool-window"></a>Créer une fenêtre d’outil

1. Créez un projet nommé **FirstToolWin** à l’aide du modèle VSIX et ajoutez un modèle personnalisé d’élément de fenêtre d’outil nommé **FirstToolWindow**.

    > [!NOTE]
    > Pour plus d’informations sur la création d’une extension avec une fenêtre d’outil, voir [Créer une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="add-a-control-to-the-tool-window"></a>Ajouter un contrôle à la fenêtre d’outil

1. Supprimer le contrôle par défaut. Ouvrez *FirstToolWindowControl.xaml* et supprimez le **Click Me!** .

2. Dans la **boîte à outils**, étendre la section Tous les contrôles **WPF** et faire glisser le contrôle **de l’élément média** à la forme **FirstToolWindowControl.** Sélectionnez le contrôle, et dans la fenêtre **Propriétés,** nom de cet élément **mediaElement1**.

## <a name="add-a-toolbar-to-the-tool-window"></a>Ajouter une barre d’outils à la fenêtre d’outils
En ajoutant une barre d’outils de la manière suivante, vous garantissez que ses gradients et couleurs sont compatibles avec le reste de l’IDE.

1. Dans **Solution Explorer**, ouvert *FirstToolWindowPackage.vsct*. Le fichier *.vsct* définit les éléments d’interface utilisateur graphique (GUI) dans votre fenêtre d’outil en utilisant XML.

2. Dans `<Symbols>` la section, `<GuidSymbol>` trouver `name` le `guidFirstToolWindowPackageCmdSet`nœud dont l’attribut est . Ajoutez les `<IDSymbol>` deux éléments suivants `<IDSymbol>` à la liste des éléments de ce nœud pour définir une barre d’outils et un groupe de barres d’outils.

    ```xml
    <IDSymbol name="ToolbarID" value="0x1000" />
    <IDSymbol name="ToolbarGroupID" value="0x1001" />
    ```

3. Juste au-dessus de la `<Buttons>` section, créez une `<Menus>` section qui ressemble à ceci :

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

    Il existe plusieurs types de menu. Ce menu est une barre d’outils `type` dans une fenêtre d’outil, définie par son attribut. L’id `guid` et `id` les réglages constituent l’ID entièrement qualifié de la barre d’outils. Typiquement, `<Parent>` le menu est le groupe contenant. Cependant, une barre d’outils est définie comme son propre parent. Par conséquent, le même `<Menu>` identifiant `<Parent>` est utilisé pour les éléments et les éléments. L’attribut `priority` est juste '0'.

4. Les barres d’outils ressemblent à des menus à bien des égards. Par exemple, tout comme un menu peut avoir des groupes de commandes, les barres d’outils peuvent également avoir des groupes. (Sur les menus, les groupes de commandement sont séparés par des lignes horizontales. Sur les barres d’outils, les groupes ne sont pas séparés par des diviseurs visuels.)

    Ajouter `<Groups>` une section `<Group>` qui contient un élément. Cela définit le groupe dont vous `<Symbols>` avez déclaré la pièce d’identité dans la section. Ajouter `<Groups>` la section `<Menus>` juste après la section.

    ```xml
    <Groups>
        <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">
            <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />
        </Group>
    </Groups>
    ```

    En définissant le GUID parent et l’ID au GUID et à l’ID de la barre d’outils, vous ajoutez le groupe à la barre d’outils.

## <a name="add-a-command-to-the-toolbar"></a>Ajouter une commande à la barre d’outils

Ajoutez une commande à la barre d’outils, qui s’affiche sous forme de bouton.

1. Dans `<Symbols>` la section, déclarez les éléments IDSymbol suivants juste après les déclarations de groupe de barre d’outils et de barre d’outils.

    ```xml
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />
    ```

2. Ajoutez un élément `<Buttons>` bouton à l’intérieur de la section. Cet élément apparaîtra sur la barre d’outils de la fenêtre de l’outil, avec une icône **de recherche** (loupe).

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

    Cela rend vos commandes disponibles en code.

## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Ajouter une propriété MediaPlayer à FirstToolWindowControl
Parmi les responsables de l’événement pour les commandes de la barre d’outils, votre code doit être en mesure d’accéder au contrôle media Player, qui est un enfant de la classe FirstToolWindowControl.

Dans **Solution Explorer**, cliquez à droite *FirstToolWindowControl.xaml*, cliquez sur Code De **vue**, et ajoutez le code suivant à la classe FirstToolWindowControl.

```csharp
public System.Windows.Controls.MediaElement MediaPlayer
{
    get { return mediaElement1; }
}
```

## <a name="instantiate-the-tool-window-and-toolbar"></a>Instantané de la fenêtre d’outils et de la barre d’outils
Ajoutez une barre d’outils et une commande de menu qui invoque le dialogue **Open File** et joue le fichier multimédia sélectionné.

1. Ouvrez *FirstToolWindow.cs* et ajoutez `using` les directives suivantes :

    ```csharp
    using System.ComponentModel.Design;
    using System.Windows.Forms;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

2. À l’intérieur de la classe FirstToolWindow, ajoutez une référence publique au contrôle FirstToolWindowControl.

    ```csharp
    public FirstToolWindowControl control;
    ```

3. À la fin du constructeur, définissez cette variable de contrôle au contrôle nouvellement créé.

    ```csharp
    control = new FirstToolWindowControl();
    base.Content = control;
    ```

4. Instantané de la barre d’outils à l’intérieur du constructeur.

    ```csharp
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.ToolbarID);
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;
    ```

5. À ce stade, le constructeur FirstToolWindow devrait ressembler à ceci:

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

6. Ajoutez la commande du menu à la barre d’outils. Dans la classe FirstToolWindowCommand.cs, ajoutez la directive suivante à l’aide :

    ```csharp
    using System.Windows.Forms;
    ```

7. Dans la classe FirstToolWindowCommand, ajoutez le code suivant à la fin de la méthode ShowToolWindow(). La commande ButtonHandler sera implémentée dans la section suivante.

    ```csharp
    // Create the handles for the toolbar command.
    var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    var toolbarbtnCmdID = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),
        FirstToolWindowCommand.cmdidWindowsMediaOpen);
    var menuItem = new MenuCommand(new EventHandler(
        ButtonHandler), toolbarbtnCmdID);
    mcs.AddCommand(menuItem);
    ```

### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Pour implémenter une commande de menu dans la fenêtre d’outil

1. Dans la classe FirstToolWindowCommand, ajoutez une méthode ButtonHandler qui invoque le dialogue **Open File.** Lorsqu’un fichier a été sélectionné, il joue le fichier multimédia.

2. Dans la classe FirstToolWindowCommand, ajoutez une référence privée à la fenêtre FirstToolWindow qui est créée dans la méthode FindToolWindow() .

    ```csharp
    private FirstToolWindow window;
    ```

3. Modifiez la méthode ShowToolWindow() pour définir la fenêtre que vous avez définie ci-dessus (afin que le gestionnaire de commande ButtonHandler puisse accéder au contrôle de la fenêtre. Voici la méthode complète ShowToolWindow() .

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

4. Ajoutez la méthode ButtonHandler. Il crée un OpenFileDialog pour l’utilisateur de spécifier le fichier multimédia à jouer, puis joue le fichier sélectionné.

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

## <a name="set-the-default-position-for-the-tool-window"></a>Définissez la position par défaut pour la fenêtre d’outil

Ensuite, spécifiez un emplacement par défaut dans l’IDE pour la fenêtre d’outils. Les informations de configuration pour la fenêtre d’outil se situent dans le *fichier FirstToolWindowPackage.cs.*

1. Dans *FirstToolWindowPackage.cs*, trouver <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> l’attribut sur la `FirstToolWindowPackage` classe, qui passe le type FirstToolWindow au constructeur. Pour spécifier une position par défaut, vous devez ajouter plus de paramètres au constructeur à l’exemple suivant.

    ```csharp
    [ProvideToolWindow(typeof(FirstToolWindow),
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
    ```

    Le premier paramètre nommé `Style` `Tabbed`est et sa valeur est , ce qui signifie que la fenêtre sera un onglet dans une fenêtre existante. La position d’amarrage est spécifiée par le `Window` paramètre, n ce cas, le GUID de la Solution **Explorer**.

    > [!NOTE]
    > Pour plus d’informations sur les types <xref:EnvDTE.vsWindowType>de fenêtres dans l’IDE, voir .

## <a name="test-the-tool-window"></a>Testez la fenêtre de l’outil

1. Appuyez sur **F5** pour ouvrir une nouvelle instance de la construction expérimentale Visual Studio.

2. Sur le menu **View,** pointez vers **d’autres fenêtres,** puis cliquez sur **La fenêtre du premier outil**.

    La fenêtre de l’outil de lecteur multimédia doit s’ouvrir dans la même position que **Solution Explorer**. S’il apparaît toujours dans la même position qu’auparavant, réinitialisez la disposition de la**fenêtre (Fenêtre / Mise à jour de fenêtre de réinitialisation**).

3. Cliquez sur le bouton (il a l’icône **de recherche)** dans la fenêtre de l’outil. Sélectionnez un fichier sonore ou vidéo pris en charge, par exemple, *C: 'windows’media’chimes.wav*, puis appuyez sur **Open**.

    Vous devriez entendre le son de carillon.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
