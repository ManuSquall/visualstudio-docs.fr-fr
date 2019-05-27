---
title: Écriture dans le Store de paramètres utilisateur | Microsoft Docs
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe8187fe11f4818433aed847a7bc67d4a889ad3a
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66206882"
---
# <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur
Paramètres de l’utilisateur sont des paramètres accessible en écriture telles que celles dans les **Outils / Options** boîte de dialogue, fenêtres Propriétés et certaines autres boîtes de dialogue. Extensions Visual Studio peuvent utiliser pour stocker de petites quantités de données. Cette procédure pas à pas montre comment ajouter le bloc-notes à Visual Studio comme un outil externe en lecture et écriture à la banque de paramètres utilisateur.

## <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur

1. Créez un projet VSIX nommé UserSettingsStoreExtension, puis ajoutez une commande personnalisée nommée UserSettingsStoreCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Dans UserSettingsStoreCommand.cs, ajoutez le code suivant à l’aide d’instructions :

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. Dans MenuItemCallback, supprimez le corps de la méthode et obtenir de l’utilisateur de stocker des paramètres, comme suit :

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Découvrez maintenant si le bloc-notes est déjà défini comme un outil externe. Vous devez effectuer une itération dans tous les outils externes pour déterminer si le paramètre ToolCmd est « Notepad », comme suit :

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

5. Si le bloc-notes n’a pas été défini comme un outil externe, définie comme suit :

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

6. Tester le code. N’oubliez pas qu’il ajoute le bloc-notes en tant qu’un outil externe, donc vous devez restaurer le Registre avant de l’exécuter une deuxième fois.

7. Générer le code et démarrer le débogage.

8. Sur le **outils** menu, cliquez sur **UserSettingsStoreCommand appeler**. Cela ajoutera le bloc-notes pour le **outils** menu.

9. Doit maintenant apparaître le bloc-notes dans le menu Outils / Options de menu, puis en cliquant sur **le bloc-notes** doit afficher une instance de bloc-notes.