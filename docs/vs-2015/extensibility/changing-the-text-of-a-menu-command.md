---
title: Modification du texte d’une commande de Menu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184494"
---
# <a name="changing-the-text-of-a-menu-command"></a>Modification du texte d’une commande de menu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes suivantes montrent comment modifier l’étiquette de texte d’une commande de menu à l’aide de la <xref:System.ComponentModel.Design.IMenuCommandService> service.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Changer une étiquette de commande de menu avec le IMenuCommandService  
  
1. Créez un projet VSIX nommé `MenuText` avec une commande de menu nommée **ChangeMenuText**. Pour plus d’informations, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Dans le fichier .vstc, ajoutez le `TextChanges` indicateur à votre commande de menu, comme indiqué dans l’exemple suivant.  
  
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
  
3. Dans le fichier ChangeMenuText.cs, créez un gestionnaire d’événements qui sera appelé avant que la commande de menu est affichée.  
  
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
  
4. Dans le constructeur ChangeMenuText, remplacez le code d’origine de l’initialisation et le positionnement de commande avec le code qui crée un <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (au lieu d’un `MenuCommand`) qui représente la commande de menu, ajoute le <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> Gestionnaire d’événements et donne le menu commande pour le service de commande de menu.  
  
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
  
5. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio s’affiche.  
  
6. Sur le **outils** menu, vous devez voir une commande nommée **ChangeMenuText appeler**.  
  
7. Cliquez sur la commande. Vous devriez voir la boîte de message annonce que MenuItemCallback a été appelé. Lorsque vous fermez la boîte de message, vous devez voir que le nom de la commande dans le menu Outils est désormais **nouveau texte**.
