---
title: "Modification de l’apparence d’une commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "commandes, modification de l’apparence"
  - "commandes de menu, modification de l’apparence"
  - "menus, modification de l’apparence de la commande"
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Modification de l’apparence d’une commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous souhaiterez peut\-être une commande à un aspect différent lorsqu’il n’est pas disponible. Vous pouvez rendre des commandes disponibles ou indisponibles, masquer ou afficher, ou vérifiez ou désactivez\-les dans le menu.  
  
 Pour modifier l’apparence d’une commande, effectuez une des actions suivantes :  
  
-   Spécifier les indicateurs appropriés dans la définition de la commande dans le fichier de la table commandes.  
  
-   Utilisez la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
-   Implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> de l’interface et de modifier les objets de commande brute.  
  
 Les étapes suivantes montrent comment rechercher et mettre à jour l’apparence d’une commande à l’aide de Managed Package Framework \(MPF\).  
  
### Pour modifier l’apparence d’une commande de menu  
  
1.  Suivez les instructions de [Modification du texte d’une commande de Menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text`.  
  
2.  Dans le fichier ChangeMenuText.cs, ajoutez l’instruction using :  
  
    ```c#  
    using System.Security.Permissions;  
    ```  
  
3.  Dans le fichier ChangeMenuTextPackageGuids.cs, ajoutez la ligne suivante :  
  
    ```c#  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Dans le fichier ChangeMenuText.cs, remplacez le code dans la méthode ShowMessageBox avec les éléments suivants :  
  
    ```c#  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtenir la commande que vous souhaitez mettre à jour à partir de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de l’objet et ensuite définir les propriétés appropriées sur l’objet de commande. Par exemple, la méthode suivante rend la commande spécifiée à partir d’une commande VSPackage définir disponible ou indisponible. Le code suivant permet de l’élément de menu nommé `New Text` indisponible après qu’il a été cliqué.  
  
    ```c#  
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
  
6.  Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit s’afficher.  
  
7.  Sur le **outils** menu, cliquez sur le **ChangeMenuText appeler** commande. À ce stade est le nom de la commande **ChangeMenuText appeler**, de sorte que le Gestionnaire de commandes n’appelle pas ChangeMyCommand\(\).  
  
8.  Sur le **outils** menu, vous devez maintenant voir **nouveau texte**. Cliquez sur **nouveau texte**. La commande doit maintenant être grisée.  
  
## Voir aussi  
 [Commandes, Menus et barres d'outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Comment ajouter des éléments d'Interface utilisateur dans les packages VS](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)