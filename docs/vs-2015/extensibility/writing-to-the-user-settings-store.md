---
title: Écriture dans le magasin des paramètres utilisateur | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839978"
---
# <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les paramètres utilisateur sont des paramètres inscriptibles tels que ceux de la boîte de dialogue **Outils/Options** , des fenêtres de propriétés et d’autres boîtes de dialogue. Les extensions Visual Studio peuvent les utiliser pour stocker de petites quantités de données. Cette procédure pas à pas montre comment ajouter le bloc-notes à Visual Studio en tant qu’outil externe en lisant et en écrivant dans le magasin des paramètres utilisateur.  
  
### <a name="backing-up-your-user-settings"></a>Sauvegarde de vos paramètres utilisateur  
  
1. Vous devez être en mesure de réinitialiser les paramètres des outils externes pour pouvoir déboguer et répéter la procédure. Pour ce faire, vous devez enregistrer les paramètres d’origine afin de pouvoir les restaurer en fonction des besoins.  
  
2. Ouvrez Regedit.exe.  
  
3. Accédez à HKEY_CURRENT_USER outils \Software\Microsoft\VisualStudio\14.0Exp\External \\ .  
  
    > [!NOTE]
    > Vérifiez que vous examinez la clé qui contient \14.0Exp\ et non \ 14,0 \\ . Quand vous exécutez l’instance expérimentale de Visual Studio, vos paramètres utilisateur se trouvent dans la ruche de Registre « 14.0 exp ».  
  
4. Cliquez avec le bouton droit sur la sous-clé \External Tools \, puis cliquez sur **Exporter**. Assurez-vous que l’option **branche sélectionnée** est sélectionnée.  
  
5. Enregistrez le fichier Tools externe. reg résultant.  
  
6. Par la suite, lorsque vous souhaitez réinitialiser les paramètres des outils externes, sélectionnez l’HKEY_CURRENT_USER la clé de Registre \Software\Microsoft\VisualStudio\14.0Exp\External Tools \, puis cliquez sur **supprimer** dans le menu contextuel.  
  
7. Quand la boîte de dialogue **confirmer la suppression** de la clé s’affiche, cliquez sur **Oui**.  
  
8. Cliquez avec le bouton droit sur le fichier External Tools. reg que vous avez enregistré précédemment, cliquez sur **Ouvrir avec**, puis cliquez sur **éditeur du registre**.  
  
## <a name="writing-to-the-user-settings-store"></a>Écriture dans la banque de paramètres utilisateur  
  
1. Créez un projet VSIX nommé UserSettingsStoreExtension, puis ajoutez une commande personnalisée nommée UserSettingsStoreCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2. Dans UserSettingsStoreCommand.cs, ajoutez les instructions using suivantes :  
  
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
