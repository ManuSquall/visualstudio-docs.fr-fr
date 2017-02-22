---
title: "Modification du texte d’une commande de Menu | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus, modification du texte"
  - "texte, menus"
  - "commandes, modification du texte"
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Modification du texte d’une commande de Menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les étapes suivantes montrent comment modifier l’étiquette de texte d’une commande de menu à l’aide de la <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## Modification d’une étiquette de commande de menu avec le IMenuCommandService  
  
1.  Créez un projet VSIX nommé `MenuText` avec une commande de menu nommée **ChangeMenuText**. Pour plus d'informations, consultez [Création d'une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Dans le fichier .vstc, ajoutez le `TextChanges` indicateur à votre commande de menu, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">  
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />  
        <Icon guid="guidImages" id="bmpPic1" />  
        <CommandFlag>TextChanges</CommandFlag>  
        <Strings>  
            <ButtonText>Invoke ChangeMenuText</ButtonText>  
        </Strings>  
    </Button>  
    ```  
  
3.  Dans le fichier ChangeMenuText.cs, créez un gestionnaire d’événements qui sera appelé avant que la commande de menu s’affiche.  
  
    ```c#  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
                    }  
    }  
    ```  
  
     Vous pouvez également modifier l’état de la commande de menu dans cette méthode en modifiant le <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, et <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> propriétés sur le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objet.  
  
4.  Dans le constructeur ChangeMenuText, remplacez le code d’origine de l’initialisation et le placement de commande avec le code qui crée un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> \(plutôt que `MenuCommand`\) qui représente la commande de menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements et donne le menu de commande au service de commande de menu.  
  
     Voici ce qui doit ressembler à :  
  
    ```c#  
    private ChangeMenuText(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.ShowMessageBox;  
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);  
            menuItem.BeforeQueryStatus +=  
                new EventHandler(OnBeforeQueryStatus);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
5.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
6.  Sur le **outils** menu, vous devez voir une commande nommée **ChangeMenuText appeler**.  
  
7.  Cliquez sur la commande. Vous devez voir la boîte de message annonce que MenuItemCallback a été appelé. Lorsque vous fermez la boîte de message, vous devez voir que le nom de la commande dans le menu Outils est désormais **nouveau texte**.