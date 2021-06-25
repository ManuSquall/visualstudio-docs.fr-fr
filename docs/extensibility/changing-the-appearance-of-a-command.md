---
title: Modification de l’apparence d’une commande | Microsoft Docs
description: Découvrez comment fournir des commentaires sur la modification de l’apparence d’une commande, par exemple rendre les commandes disponibles/non disponibles, masquées/affichées, ou cochées/décochées.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ddeed08d7bc33b9a9ae5405876f3b28459d4eaf2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905031"
---
# <a name="change-the-appearance-of-a-command"></a>Modifier l’apparence d’une commande
Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous souhaiterez peut-être qu’une commande ait un aspect différent lorsqu’elle n’est pas disponible. Vous pouvez rendre les commandes disponibles ou non disponibles, les masquer ou les afficher, ou les activer ou les désactiver dans le menu.

Pour modifier l’apparence d’une commande, effectuez l’une des actions suivantes :

- Spécifiez les indicateurs appropriés dans la définition de la commande dans le fichier de table de commandes.

- Utilisez le <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> service.

- Implémentez l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface et modifiez les objets de commande bruts.

  Les étapes suivantes montrent comment rechercher et mettre à jour l’apparence d’une commande à l’aide de Managed package Framework (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Pour modifier l’apparence d’une commande de menu

1. Suivez les instructions dans [modifier le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text` .

2. Dans le fichier *ChangeMenuText. cs* , ajoutez l’instruction using suivante :

    ```csharp
    using System.Security.Permissions;
    ```

3. Dans le fichier *ChangeMenuTextPackageGuids. cs* , ajoutez la ligne suivante :

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. Dans le fichier *ChangeMenuText. cs* , remplacez le code dans la méthode méthode ShowMessageBox par ce qui suit :

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Obtenez la commande que vous souhaitez mettre à jour à partir de l' <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> objet, puis définissez les propriétés appropriées sur l’objet de commande. Par exemple, la méthode suivante rend la commande spécifiée à partir d’un jeu de commandes VSPackage disponible ou non disponible. Le code suivant fait en sorte que l’élément de menu nommé `New Text` n’est pas disponible après avoir cliqué dessus.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);
        MenuCommand mc = mcs.FindCommand(newCmdID);
        if (mc != null)
        {
            mc.Enabled = enableCmd;
            cmdUpdated = true;
        }
        return cmdUpdated;
    }
    ```

6. Générez le projet et commencez le débogage. L’instance expérimentale de Visual Studio doit apparaître.

7. Dans le menu **Outils** , cliquez sur la commande **appeler ChangeMenuText** . À ce stade, le nom de commande est **Invoke ChangeMenuText**, de sorte que le gestionnaire de commandes n’appelle pas **ChangeMyCommand ()**.

8. Dans le menu **Outils** , vous devez maintenant voir le **nouveau texte**. Cliquez sur **nouveau texte**. La commande doit maintenant être grisée.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Comment les VSPackages ajoutent des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [Table de commandes Visual Studio (. Fichiers vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
