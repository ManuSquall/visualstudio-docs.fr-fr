---
title: Ajout d’une fenêtre outil | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tutorials
- tool windows
ms.assetid: 8e16c381-03c8-404e-92ef-3614cdf3150a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 550e483ec2a8cd4b4126e4c0838dc8d2870af59c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151929"
---
# <a name="add-a-tool-window"></a>Ajouter une fenêtre outil
Dans cette procédure pas à pas, vous allez apprendre à créer une fenêtre outil et l’intégrer à Visual Studio comme suit :  
  
-   Ajouter un contrôle à la fenêtre outil.  
  
-   Ajouter une barre d’outils à une fenêtre outil.  
  
-   Ajouter une commande à la barre d’outils.  
  
-   Implémenter les commandes.  
  
-   Définir la position par défaut de la fenêtre outil.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-tool-window"></a>Créer une fenêtre outil  
  
1.  Créez un projet nommé **FirstToolWin** en utilisant le modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **FirstToolWindow**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [créer une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Ajouter un contrôle à la fenêtre outil  
  
1.  Supprimez le contrôle par défaut. Ouvrez *FirstToolWindowControl.xaml* et supprimer le **Click Me !** disproportionnée.  
  
2.  Dans le **boîte à outils**, développez le **tous les contrôles WPF** section et faites glisser le **élément média** le contrôle à la **FirstToolWindowControl** formulaire. Sélectionnez le contrôle, puis, dans le **propriétés** fenêtre, nommez cet élément **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Ajouter une barre d’outils à la fenêtre outil  
 En ajoutant une barre d’outils de la manière suivante, vous garantir que ses dégradés et les couleurs sont cohérents avec le reste de l’IDE.  
  
1.  Dans **l’Explorateur de solutions**, ouvrez *FirstToolWindowPackage.vsct*. Le *.vsct* fichier définit les éléments d’interface graphique utilisateur graphique dans votre fenêtre outil à l’aide de XML.  
  
2.  Dans le `<Symbols>` section, recherchez le `<GuidSymbol>` nœud dont `name` attribut est `guidFirstToolWindowPackageCmdSet`. Ajoutez les deux `<IDSymbol>` éléments à la liste des `<IDSymbol>` éléments dans ce nœud pour définir une barre d’outils et un groupe de la barre d’outils.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Juste au-dessus du `<Buttons>` section, créez un `<Menus>` section qui ressemble à ceci :  
  
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
  
     Il existe plusieurs types de menu. Ce menu est une barre d’outils dans une fenêtre outil, défini par son `type` attribut. Le `guid` et `id` paramètres constituent l’ID complet de la barre d’outils. En règle générale, le `<Parent>` d’un menu est le groupe conteneur. Toutefois, une barre d’outils est défini comme son propre parent. Par conséquent, le même identificateur est utilisé pour le `<Menu>` et `<Parent>` éléments. Le `priority` attribut est simplement « 0 ».  
  
4.  Barres d’outils sont semblables aux menus à bien des égards. Par exemple, tout comme un menu peut avoir des groupes de commandes, barres d’outils peuvent également des groupes. (Dans les menus, les groupes de commandes sont séparées par des lignes horizontales. Des barres d’outils, les groupes ne sont pas séparés par des séparateurs de visual.)  
  
     Ajouter un `<Groups>` section qui contient un `<Group>` élément. Définit le groupe dont vous avez déclaré dans l’ID du `<Symbols>` section. Ajouter le `<Groups>` section juste après le `<Menus>` section.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     En définissant le parent GUID et l’ID pour le GUID et l’ID de la barre d’outils, vous ajoutez le groupe à la barre d’outils.  
  
## <a name="add-a-command-to-the-toolbar"></a>Ajouter une commande à la barre d’outils  
 Ajouter une commande à la barre d’outils, qui s’affiche en tant que bouton.  
  
1.  Dans la `<Symbols>` section, déclarer les éléments suivants de IDSymbol juste après la barre d’outils et de la barre d’outils des déclarations de groupe.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Ajouter un élément de bouton à l’intérieur du `<Buttons>` section. Cet élément apparaît alors dans la barre d’outils dans la fenêtre outil, avec un **recherche** icône (Loupe).  
  
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
  
3.  Ouvrez *FirstToolWindowCommand.cs* et ajoutez les lignes suivantes dans la classe juste après les champs existants.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     Cela rend vos commandes disponibles dans le code.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Ajouter une propriété de MediaPlayer à FirstToolWindowControl  
 Gestionnaires d’événements pour les contrôles de barre d’outils, votre code doit être en mesure d’accéder au contrôle Media Player, qui est un enfant de la classe FirstToolWindowControl.  
  
 Dans **l’Explorateur de solutions**, avec le bouton droit *FirstToolWindowControl.xaml*, cliquez sur **afficher le Code**et ajoutez le code suivant à la classe FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Instancier la fenêtre outil et la barre d’outils  
 Ajouter une barre d’outils et une commande de menu qui appelle le **ouvrir un fichier** boîte de dialogue et lit le fichier multimédia sélectionné.  
  
1.  Ouvrez *FirstToolWindow.cs* et ajoutez le code suivant `using` instructions.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  À l’intérieur de la classe FirstToolWindow, ajoutez une référence publique pour le contrôle FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  À la fin du constructeur, définissez cette variable de contrôle sur le contrôle qui vient d’être créé.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Instanciez la barre d’outils à l’intérieur du constructeur.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  À ce stade le constructeur FirstToolWindow doit ressembler à ceci :  
  
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
  
6.  Ajoutez la commande de menu à la barre d’outils. Dans la classe FirstToolWindowCommand.cs, ajoutez le code suivant à l’aide d’instruction  
  
    ```csharp  
    using System.Windows.Forms;  
    ```  
  
7.  Dans la classe FirstToolWindowCommand, ajoutez le code suivant à la fin de la méthode ShowToolWindow(). La commande ButtonHandler sera implémentée dans la section suivante.  
  
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
  
1.  Dans la classe FirstToolWindowCommand, ajoutez une méthode ButtonHandler qui appelle le **ouvrir un fichier** boîte de dialogue. Lorsqu’un fichier a été sélectionné, il lit le fichier multimédia.  
  
2.  Dans la classe FirstToolWindowCommand, ajoutez une référence à la fenêtre FirstToolWindow qui est créée dans la méthode FindToolWindow() privée.  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Modifier la méthode ShowToolWindow() pour définir la fenêtre définie ci-dessus (afin que le Gestionnaire de commandes ButtonHandler peut accéder au contrôle de fenêtre. Voici la méthode ShowToolWindow() complète.  
  
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
  
4.  Ajoutez la méthode ButtonHandler. Il crée un OpenFileDialog pour l’utilisateur de spécifier le fichier multimédia à lire, et puis lit le fichier sélectionné.  
  
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
 Ensuite, spécifiez un emplacement par défaut dans l’IDE de la fenêtre outil. Informations de configuration de la fenêtre outil sont dans le *FirstToolWindowPackage.cs* fichier.  
  
1.  Dans *FirstToolWindowPackage.cs*, trouver la <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> attribut sur la `FirstToolWindowPackage` classe, qui transmet le type FirstToolWindow au constructeur. Pour spécifier une position par défaut, vous devez ajouter davantage de paramètres au constructeur de l’exemple suivant.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Le premier paramètre nommé est `Style` et sa valeur est `Tabbed`, ce qui signifie que la fenêtre sera un onglet dans une fenêtre existante. La position d’ancrage est spécifiée par le `Window` paramètre, n ce cas, le GUID de la **l’Explorateur de solutions**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les types de fenêtres dans l’IDE, consultez <xref:EnvDTE.vsWindowType>.  
  
## <a name="test-the-tool-window"></a>La fenêtre outil de test  
  
1.  Appuyez sur **F5** pour ouvrir une nouvelle instance de la build expérimentale de Visual Studio.  
  
2.  Sur le **vue** menu, pointez sur **Windows autres** puis cliquez sur **première fenêtre d’outil**.  
  
     La fenêtre outil du lecteur multimédia doit s’ouvrir dans la même position que **l’Explorateur de solutions**. S’il apparaît toujours dans la même position que précédemment, réinitialiser la disposition de fenêtre (**fenêtre / rétablir la disposition de fenêtre**).  
  
3.  Cliquez sur le bouton (il a la **recherche** icône) dans la fenêtre outil. Sélectionnez un son pris en charge ou un fichier vidéo, par exemple, *C:\windows\media\chimes.wav*, puis appuyez sur **Open**.  
  
     Vous devez entendre le son de carillon.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)