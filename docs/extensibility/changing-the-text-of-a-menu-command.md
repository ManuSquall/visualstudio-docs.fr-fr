---
title: Modification du texte d’une commande de Menu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: df943221fc2f154e8f18007bd5f7ff5454434d84
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39234838"
---
# <a name="change-the-text-of-a-menu-command"></a>Modifier le texte d’une commande de menu
Les étapes suivantes montrent comment modifier l’étiquette de texte d’une commande de menu à l’aide de la <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Changer une étiquette de commande de menu avec le IMenuCommandService  
  
1.  Créez un projet VSIX nommé `MenuText` avec une commande de menu nommée **ChangeMenuText**. Pour plus d’informations, consultez [créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Dans le *.vsct* , ajoutez le `TextChanges` indicateur à votre commande de menu, comme indiqué dans l’exemple suivant.  
  
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
  
3.  Dans le *ChangeMenuText.cs* de fichiers, créez un gestionnaire d’événements qui sera appelé avant que la commande de menu est affichée.  
  
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
  
     Vous pouvez également modifier l’état de la commande de menu dans cette méthode en modifiant le <xref:System.ComponentModel.Design.MenuCommand.Visible%2A>, <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>, et <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> propriétés sur le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objet.  
  
4.  Dans le constructeur ChangeMenuText, remplacez le code d’origine de l’initialisation et le positionnement de commande avec le code qui crée un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (au lieu d’un `MenuCommand`) qui représente la commande de menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements et donne le menu commande pour le service de commande de menu.  
  
     Voici à quoi il doit ressembler :  
  
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
  
6.  Sur le **outils** menu, vous devez voir une commande nommée **ChangeMenuText appeler**.  
  
7.  Cliquez sur la commande. Vous devriez voir la boîte de message qui annonce **MenuItemCallback** a été appelée. Lorsque vous fermez la boîte de message, vous devez voir que le nom de la commande dans le menu Outils est désormais **nouveau texte**.
