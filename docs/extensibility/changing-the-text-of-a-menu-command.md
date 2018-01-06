---
title: "Modification du texte d’une commande de Menu | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: "25"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 48443396038e703ed226c035ede34861fe50fa61
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="changing-the-text-of-a-menu-command"></a>Modification du texte d’une commande de Menu
Les étapes suivantes montrent comment modifier l’étiquette de texte d’une commande de menu à l’aide de la <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>La modification d’une étiquette de commande de menu avec le IMenuCommandService  
  
1.  Créez un projet VSIX nommé `MenuText` avec une commande de menu nommé **ChangeMenuText**. Pour plus d’informations, consultez [avec une commande de Menu pour créer une Extension](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
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
  
3.  Dans le fichier ChangeMenuText.cs, créez un gestionnaire d’événements qui sera appelé avant l’affichage de la commande de menu.  
  
    ```csharp  
    private void OnBeforeQueryStatus(object sender, EventArgs e)  
    {  
        var myCommand = sender as OleMenuCommand;  
        if (null != myCommand)  
        {  
            myCommand.Text = "New Text";  
        }  
    }  
    ```  
  
     Vous pouvez également actualiser l’état de la commande de menu dans cette méthode en modifiant le <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, et <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> propriétés sur le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objet.  
  
4.  Dans le constructeur ChangeMenuText, remplacez le code d’origine de l’initialisation et le placement de commande avec le code qui crée un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (plutôt qu’un `MenuCommand`) qui représente la commande de menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements, ainsi que le menu commande au service de commande de menu.  
  
     Voici ce qui doit ressembler à :  
  
    ```csharp  
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
  
6.  Sur le **outils** menu, vous devez voir une commande nommée **ChangeMenuText d’appeler**.  
  
7.  Cliquez sur la commande. Vous devez voir la boîte de message annonce que MenuItemCallback a été appelée. Lorsque vous fermez la boîte de message, vous devez voir que le nom de la commande dans le menu Outils est désormais **nouveau texte**.
