---
title: Écriture dans le magasin des paramètres utilisateur | Microsoft Docs
description: Découvrez comment ajouter le bloc-notes à Visual Studio en tant qu’outil externe en lisant et en écrivant dans le magasin des paramètres utilisateur à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55e17693bee1ced0354b21ee5cc736961a994c6f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876920"
---
# <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur
Les paramètres utilisateur sont des paramètres inscriptibles tels que ceux de la boîte de dialogue **Outils/Options** , des fenêtres de propriétés et d’autres boîtes de dialogue. Les extensions Visual Studio peuvent les utiliser pour stocker de petites quantités de données. Cette procédure pas à pas montre comment ajouter le bloc-notes à Visual Studio en tant qu’outil externe en lisant et en écrivant dans le magasin des paramètres utilisateur.

## <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur

1. Créez un projet VSIX nommé UserSettingsStoreExtension, puis ajoutez une commande personnalisée nommée UserSettingsStoreCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans UserSettingsStoreCommand.cs, ajoutez les directives d’utilisation suivantes :

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Dans MenuItemCallback, supprimez le corps de la méthode et récupérez la Banque de paramètres utilisateur, comme suit :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. À présent, déterminez si le bloc-notes est déjà défini en tant qu’outil externe. Vous devez itérer au sein de tous les outils externes pour déterminer si le paramètre ToolCmd est « Notepad », comme suit :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Si le bloc-notes n’a pas été défini comme un outil externe, définissez-le comme suit :

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Testez le code. N’oubliez pas qu’il ajoute Notepad comme outil externe. vous devez donc restaurer le registre avant de l’exécuter une deuxième fois.

7. Générez le code et démarrez le débogage.

8. Dans le menu **Outils** , cliquez sur **appeler UserSettingsStoreCommand**. Cette opération ajoute le bloc-notes au menu **Outils** .

9. Vous devez maintenant voir le bloc-notes dans le menu Outils/Options, puis cliquer sur **le bloc-notes** pour afficher une instance du bloc-notes.
