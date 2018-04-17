---
title: Ajout d’une fenêtre outil | Documents Microsoft
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
ms.openlocfilehash: db06bebd700fa229685d6b79ffcfb014ef301994
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="adding-a-tool-window"></a>Ajout d’une fenêtre outil
Dans cette procédure pas à pas vous allez apprendre à créer une fenêtre outil et l’intégrer dans Visual Studio comme suit :  
  
-   Ajouter un contrôle à la fenêtre outil.  
  
-   Ajouter une barre d’outils à une fenêtre outil.  
  
-   Ajouter une commande à la barre d’outils.  
  
-   Implémenter les commandes.  
  
-   Définir la position par défaut de la fenêtre outil.  
  
## <a name="prerequisites"></a>Prérequis  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-tool-window"></a>Création d’une fenêtre outil  
  
1.  Créez un projet nommé **FirstToolWin** à l’aide du modèle VSIX et ajouter un modèle d’élément de fenêtre outil personnalisé nommé **FirstToolWindow**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur la création d’une extension avec une fenêtre outil, consultez [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="add-a-control-to-the-tool-window"></a>Ajouter un contrôle à la fenêtre outil  
  
1.  Supprimez le contrôle par défaut. Ouvrez FirstToolWindowControl.xaml et supprimez le **Click Me !** disproportionnée.  
  
2.  Dans le **boîte à outils**, développez le **tous les contrôles WPF** section et faites glisser le **élément multimédia** le contrôle à la **FirstToolWindowControl** formulaire. Sélectionnez le contrôle, puis, dans le **propriétés** fenêtre, nom de cet élément **mediaElement1**.  
  
## <a name="add-a-toolbar-to-the-tool-window"></a>Ajouter une barre d’outils de la fenêtre outil  
 En ajoutant une barre d’outils de la manière suivante, vous assurer que les dégradés et les couleurs sont cohérents avec le reste de l’IDE.  
  
1.  Dans **l’Explorateur de solutions**, ouvrez FirstToolWindowPackage.vsct. Le fichier .vsct définit les éléments d’interface graphique utilisateur graphique dans votre fenêtre outil à l’aide de XML.  
  
2.  Dans le `<Symbols>` section, recherchez la `<GuidSymbol>` nœud dont `name` attribut est `guidFirstToolWindowPackageCmdSet`. Ajoutez les deux `<IDSymbol>` éléments à la liste des `<IDSymbol>` éléments dans ce nœud pour définir une barre d’outils et d’un groupe de la barre d’outils.  
  
    ```xml  
    <IDSymbol name="ToolbarID" value="0x1000" />  
    <IDSymbol name="ToolbarGroupID" value="0x1001" />  
    ```  
  
3.  Juste au-dessus du `<Buttons>` en créant un `<Menus>` section qui ressemble à ceci :  
  
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
  
     Il existe plusieurs types de menu. Ce menu est une barre d’outils dans une fenêtre outil, défini par son `type` attribut. Le `guid` et `id` paramètres composent le code complet de la barre d’outils. En règle générale, le `<Parent>` d’un menu est le groupe qui le contient. Toutefois, une barre d’outils est défini comme son propre parent. Par conséquent, le même identificateur est utilisé pour le `<Menu>` et `<Parent>` éléments. Le `priority` attribut est simplement « 0 ».  
  
4.  Barres d’outils sont semblables aux menus de nombreuses manières. Par exemple, tout comme un menu peut avoir des groupes de commandes, barres d’outils peuvent également avoir des groupes. (Dans les menus, les groupes de commandes sont séparées par des lignes horizontales. Des barres d’outils, les groupes ne sont pas séparés par des séparateurs de visual.)  
  
     Ajouter un `<Groups>` section qui contient un `<Group>` élément. Définit le groupe dont vous avez déclarés dans l’ID du `<Symbols>` section. Ajouter le `<Groups>` section juste après le `<Menus>` section.  
  
    ```xml  
    <Groups>  
       <Group guid="guidFirstToolWindowPackageCmdSet" id="ToolbarGroupID" priority="0x0000">  
           <Parent guid="guidFirstToolWindowPackageCmdSet" id="ToolbarID" />  
       </Group>  
    </Groups>  
    ```  
  
     En définissant le parent GUID et l’ID pour le GUID et l’ID de la barre d’outils, vous ajoutez le groupe à la barre d’outils.  
  
## <a name="add-a-command-to-the-toolbar"></a>Ajouter une commande à la barre d’outils  
 Ajouter une commande à la barre d’outils, qui est affiché comme un bouton.  
  
1.  Dans la `<Symbols>` section, déclarer les éléments suivants de IDSymbol juste après la barre d’outils et la barre d’outils de déclarations de groupe.  
  
    ```xml  
    <IDSymbol name="cmdidWindowsMedia" value="0x0100" />  
    <IDSymbol name="cmdidWindowsMediaOpen" value="0x132" />  
    ```  
  
2.  Ajoutez un élément de bouton à l’intérieur de la `<Buttons>` section. Cet élément s’affiche dans la barre d’outils dans la fenêtre outil, avec une icône de recherche (Loupe).  
  
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
  
3.  Ouvrez FirstToolWindowCommand.cs et ajoutez les lignes suivantes dans la classe juste après les champs existants.  
  
    ```csharp  
    public const string guidFirstToolWindowPackageCmdSet = "00000000-0000-0000-0000-0000";  // get the GUID from the .vsct file  
    public const uint cmdidWindowsMedia =        0x100;   
    public const int cmdidWindowsMediaOpen = 0x132;  
    public const int ToolbarID = 0x1000;  
    ```  
  
     Ce faisant, vos commandes disponibles dans le code.  
  
## <a name="add-a-mediaplayer-property-to-firsttoolwindowcontrol"></a>Ajouter une propriété de MediaPlayer à FirstToolWindowControl  
 Gestionnaires d’événements pour les contrôles de barre d’outils, votre code doit être en mesure d’accéder au contrôle Media Player, qui est un enfant de la classe FirstToolWindowControl.  
  
 Dans **l’Explorateur de solutions**, FirstToolWindowControl.xaml d’avec le bouton droit, cliquez sur **afficher le Code**et ajoutez le code suivant à la classe FirstToolWindowControl.  
  
```csharp  
public System.Windows.Controls.MediaElement MediaPlayer  
{  
    get { return mediaElement1; }  
}  
```  
  
## <a name="instantiate-the-tool-window-and-toolbar"></a>Instancier la barre d’outils et la fenêtre outil  
 Ajouter une barre d’outils et d’une commande de menu qui appelle la **ouvrir le fichier** boîte de dialogue et lit le fichier multimédia sélectionné.  
  
1.  Ouvrez FirstToolWindow.cs et ajoutez le code suivant `using` instructions.  
  
    ```csharp  
    using System.ComponentModel.Design;  
    using System.Windows.Forms;  
    using Microsoft.VisualStudio.Shell.Interop;   
    ```  
  
2.  À l’intérieur de la classe FirstToolWindow, ajoutez une référence publique pour le contrôle FirstToolWindowControl.  
  
    ```csharp  
    public FirstToolWindowControl control;  
    ```  
  
3.  À la fin du constructeur, définir cette variable de contrôle pour le contrôle qui vient d’être créé.  
  
    ```csharp  
    control = new FirstToolWindowControl();   
    base.Content = control;  
    ```  
  
4.  Instancier la barre d’outils à l’intérieur du constructeur.  
  
    ```csharp  
    this.ToolBar = new CommandID(new Guid(FirstToolWindowCommand.guidFirstToolWindowPackageCmdSet),   
        FirstToolWindowCommand.ToolbarID);  
    this.ToolBarLocation = (int)VSTWT_LOCATION.VSTWT_TOP;  
    ```  
  
5.  À ce stade, le constructeur FirstToolWindow doit ressembler à ceci :  
  
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
  
6.  Ajouter la commande de menu à la barre d’outils. Dans la classe FirstToolWindowCommand.cs, ajoutez le code suivant à l’aide d’instruction  
  
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
  
#### <a name="to-implement-a-menu-command-in-the-tool-window"></a>Pour implémenter une commande de menu dans la fenêtre outil  
  
1.  Dans la classe FirstToolWindowCommand, ajoutez une méthode de ButtonHandler qui appelle le **ouvrir le fichier** boîte de dialogue. Lorsqu’un fichier a été sélectionné, il lit le fichier multimédia.  
  
2.  Dans la classe FirstToolWindowCommand, ajoutez une référence privée à la fenêtre de FirstToolWindow qui est créée dans la méthode FindToolWindow().  
  
    ```csharp  
    private FirstToolWindow window;  
    ```  
  
3.  Modifier la méthode ShowToolWindow() pour définir la fenêtre que vous avez définie ci-dessus (de sorte que le Gestionnaire de commandes ButtonHandler peut accéder au contrôle de fenêtre. Voici la méthode ShowToolWindow() complète.  
  
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
  
4.  Ajoutez la méthode ButtonHandler. Il crée un OpenFileDialog pour l’utilisateur de spécifier le fichier multimédia à lire, et le lit le fichier sélectionné.  
  
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
  
## <a name="set-the-default-position-for-the-tool-window"></a>Définir la Position par défaut de la fenêtre outil  
 Ensuite, spécifiez un emplacement par défaut dans l’IDE de la fenêtre outil. Informations de configuration de la fenêtre outil sont dans le fichier FirstToolWindowPackage.cs.  
  
1.  Dans FirstToolWindowPackage.cs, recherchez le <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> de l’attribut le `FirstToolWindowPackage` (classe), qui passe le type FirstToolWindow au constructeur. Pour spécifier une position par défaut, vous devez ajouter d’autres paramètres pour le constructeur de l’exemple suivant.  
  
    ```csharp  
    [ProvideToolWindow(typeof(FirstToolWindow),  
        Style = Microsoft.VisualStudio.Shell.VsDockStyle.Tabbed,  
        Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]  
    ```  
  
     Le premier paramètre nommé est `Style` et sa valeur est `Tabbed`, ce qui signifie que la fenêtre n’est pas un onglet dans une fenêtre existante. La position d’ancrage est spécifiée par le `Window` paramètre, n ce cas, le GUID de le **l’Explorateur de solutions**.  
  
    > [!NOTE]
    >  Pour plus d’informations sur les types de fenêtres dans l’IDE, consultez <xref:EnvDTE.vsWindowType>.  
  
## <a name="testing-the-tool-window"></a>Test de la fenêtre outil  
  
1.  Appuyez sur F5 pour ouvrir une nouvelle instance de Visual Studio expérimentale générer.  
  
2.  Sur le **vue** menu, pointez sur **autres fenêtres** puis cliquez sur **première fenêtre d’outil**.  
  
     La fenêtre outil du lecteur media doit s’ouvrir dans la même position que **l’Explorateur de solutions**. S’il apparaît toujours dans la même position qu’avant, réinitialiser la disposition de fenêtre (**fenêtre / rétablir la disposition de fenêtre**).  
  
3.  Dans la fenêtre outil, cliquez sur le bouton (elle possède l’icône de recherche). Sélectionnez un fichier d’audio ou vidéo pris en charge, par exemple, C:\windows\media\chimes.wav, puis appuyez sur **ouvrir**.  
  
     Vous devez entendre le son de sonnerie.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)