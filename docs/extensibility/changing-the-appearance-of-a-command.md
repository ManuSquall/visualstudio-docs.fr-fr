---
title: Modification de l’apparence d’une commande | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fa212ec1c01a19668cafd951ea5defe5383b17ed
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232242"
---
# <a name="change-the-appearance-of-a-command"></a>Modifier l’apparence d’une commande
Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous souhaiterez une commande à un aspect différent quand il n’est pas disponible. Vous pouvez activer ou désactiver les commandes, masquer ou afficher, ou vérifier ou décochez la case dans le menu.  
  
 Pour modifier l’apparence d’une commande, effectuez l’une des actions suivantes :  
  
-   Spécifier les indicateurs appropriés dans la définition de commande dans le fichier de table de commande.  
  
-   Utilisez le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.  
  
-   Implémentez le <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> d’interface et de modifier les objets de commande brutes.  
  
 Les étapes suivantes montrent comment rechercher et mettre à jour l’apparence d’une commande à l’aide de Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Pour modifier l’apparence d’une commande de menu  
  
1.  Suivez les instructions de [modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text`.  
  
2.  Dans le *ChangeMenuText.cs* de fichier, ajoutez le code suivant à l’aide d’instruction :  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  Dans le *ChangeMenuTextPackageGuids.cs* , ajoutez la ligne suivante :  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  Dans le *ChangeMenuText.cs* fichier, remplacez le code dans la méthode ShowMessageBox par le code suivant :  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5.  Obtenir la commande que vous souhaitez mettre à jour à partir de la <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> de l’objet et ensuite définir les propriétés appropriées sur l’objet command. Par exemple, la méthode suivante fait la commande spécifiée à partir d’une commande VSPackage définir disponibles ou non disponible. Le code suivant fait l’élément de menu nommé `New Text` indisponible après qu’il a été cliqué.  
  
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
  
7.  Sur le **outils** menu, cliquez sur le **ChangeMenuText appeler** commande. À ce stade le nom de la commande est **ChangeMenuText appeler**, de sorte que le Gestionnaire de commandes n’appelle pas **ChangeMyCommand()**.  
  
8.  Sur le **outils** menu vous devriez maintenant voir **nouveau texte**. Cliquez sur **nouveau texte**. La commande doit maintenant être apparaît en grisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Extension des menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Table de commande Visual Studio (. Fichiers VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)