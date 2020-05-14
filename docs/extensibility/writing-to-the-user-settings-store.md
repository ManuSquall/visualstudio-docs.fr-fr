---
title: Rédaction au Magasin des paramètres de l’utilisateur ( Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740366"
---
# <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur
Les paramètres de l’utilisateur sont des paramètres évoluant comme ceux du dialogue **Outils /Options,** des fenêtres des propriétés et de certaines autres boîtes de dialogue. Les extensions Visual Studio peuvent les utiliser pour stocker de petites quantités de données. Ce pas-là montre comment ajouter Notepad à Visual Studio comme un outil externe en lisant et en écrivant au magasin de paramètres utilisateur.

## <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur

1. Créez un projet VSIX nommé UserSettingsStoreExtension, puis ajoutez une commande personnalisée nommée UserSettingsStoreCommand. Pour plus d’informations sur la façon de créer une commande personnalisée, voir [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans UserSettingsStoreCommand.cs, ajoutez ce qui suit à l’aide de directives :

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Dans MenuItemCallback, supprimez le corps de la méthode et obtenez le magasin de paramètres de l’utilisateur, comme suit :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Maintenant, découvrez si Notepad est déjà défini comme un outil externe. Vous devez itérer à travers tous les outils externes pour déterminer si le paramètre ToolCmd est "Notepad", comme suit:

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

5. Si Notepad n’a pas été défini comme un outil externe, définissez-le comme suit :

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

6. Testez le code. N’oubliez pas qu’il ajoute Notepad comme un outil externe, de sorte que vous devez annuler le registre avant de l’exécuter une deuxième fois.

7. Construisez le code et commencez à débogage.

8. Sur le menu **Tools,** cliquez sur **Invoke UserSettingsStoreCommand**. Ceci ajoutera Notepad au menu **Tools.**

9. Maintenant, vous devriez voir Notepad sur le menu Outils / Options, et en cliquant **sur Notepad** devrait mettre en place une instance de Notepad.
