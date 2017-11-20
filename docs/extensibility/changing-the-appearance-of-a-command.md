---
title: "Modification de l’apparence d’une commande | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7ffb8aed183b50958c8835b2a1e79b808ac20174
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="changing-the-appearance-of-a-command"></a>Modification de l’apparence d’une commande
Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous souhaiterez une commande à un aspect différent quand il n’est pas disponible. Vous pouvez rendre les commandes disponibles ou non disponible, masquer ou afficher, ou vérifiez ou désactivez les dans le menu.  
  
 Pour modifier l’apparence d’une commande, effectuez l’une des actions suivantes :  
  
-   Spécifier les indicateurs appropriés dans la définition de commande dans le fichier de la table commandes.  
  
-   Utilisez la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
-   Implémentez la <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et de modifier les objets de commande brut.  
  
 Les étapes suivantes montrent comment rechercher et mettre à jour l’apparence d’une commande à l’aide de Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Pour modifier l’apparence d’une commande de menu  
  
1.  Suivez les instructions de [modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text`.  
  
2.  Dans le fichier ChangeMenuText.cs, ajoutez le code suivant à l’aide d’instruction :  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Dans le fichier ChangeMenuTextPackageGuids.cs, ajoutez la ligne suivante :  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Dans le fichier ChangeMenuText.cs, remplacez le code dans la méthode ShowMessageBox avec les éléments suivants :  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtenir la commande que vous souhaitez mettre à jour à partir de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de l’objet, puis définissez les propriétés appropriées sur l’objet de commande. Par exemple, la méthode suivante fait la commande spécifiée à partir d’une commande VSPackage définir disponible ou non disponible. Le code suivant fait l’élément de menu nommé `New Text` indisponible une fois qu’il a été activé.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;    }  
    }  
    ```  
  
6.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.  
  
7.  Sur le **outils** menu, cliquez sur le **ChangeMenuText d’appeler** commande. À ce stade le nom de la commande est **ChangeMenuText d’appeler**, de sorte que le Gestionnaire de commandes n’appelle pas ChangeMyCommand().  
  
8.  Sur le **outils** menu, vous devez maintenant voir **nouveau texte**. Cliquez sur **nouveau texte**. La commande doit maintenant être grisée.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, Menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Comment les VSPackages ajouter les éléments d’Interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Fichiers Visual Studio Command Table (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)