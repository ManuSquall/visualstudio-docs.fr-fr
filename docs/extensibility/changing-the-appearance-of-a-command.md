---
title: Changer l’apparence d’une commande ( Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739854"
---
# <a name="change-the-appearance-of-a-command"></a>Modifier l’apparence d’une commande
Vous pouvez fournir des commentaires à votre utilisateur en modifiant l’apparence d’une commande. Par exemple, vous pouvez vouloir qu’une commande ait l’air différente lorsqu’elle n’est pas disponible. Vous pouvez rendre les commandes disponibles ou indisponibles, les masquer ou les montrer, ou les vérifier ou les décocher sur le menu.

Pour changer l’apparence d’une commande, exécutez l’une de ces actions :

- Spécifier les drapeaux appropriés dans la définition de commande dans le fichier de la table de commande.

- Utilisez <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> le service.

- Implémenter l’interface <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> et modifier les objets de commande bruts.

  Les étapes suivantes montrent comment trouver et mettre à jour l’apparence d’une commande en utilisant le cadre de paquet géré (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Pour changer l’apparence d’une commande de menu

1. Suivez les instructions dans [Changez le texte d’une commande de menu](../extensibility/changing-the-text-of-a-menu-command.md) pour créer un élément de menu nommé `New Text`.

2. Dans le fichier *ChangeMenuText.cs,* ajoutez l’instruction suivante à l’aide de :

    ```csharp
    using System.Security.Permissions;
    ```

3. Dans le fichier *ChangeMenuTextPackageGuids.cs,* ajoutez la ligne suivante :

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. Dans le *fichier ChangeMenuText.cs,* remplacez le code dans la méthode ShowMessageBox par les éléments suivants :

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Obtenez la commande que vous <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> souhaitez mettre à jour à partir de l’objet, puis définissez les propriétés appropriées sur l’objet de commande. Par exemple, la méthode suivante rend la commande spécifiée à partir d’un ensemble de commande VSPackage disponible ou indisponible. Le code suivant rend `New Text` l’élément de menu nommé indisponible après avoir été cliqué.

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
        return cmdUpdated;
    }
    ```

6. Générez le projet et commencez le débogage. L’exemple expérimental de Visual Studio devrait apparaître.

7. Sur le menu **Tools,** cliquez sur la commande **Invoke ChangeMenuText.** À ce stade, le nom de commande est **Invoke ChangeMenuText**, de sorte que le gestionnaire de commande n’appelle pas **ChangeMyCommand()**.

8. Sur le menu **Outils,** vous devriez maintenant voir **New Text**. Cliquez sur **nouveau texte**. La commande doit maintenant être grisée.

## <a name="see-also"></a>Voir aussi
- [Commandes, menus et barres d’outils](../extensibility/internals/commands-menus-and-toolbars.md)
- [Comment VSPackages ajoute des éléments d’interface utilisateur](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [Table de commande Visual Studio (. Vsct) Fichiers](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
