---
title: "Écriture dans la banque de paramètres utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>Écriture dans le magasin de paramètres utilisateur
Paramètres utilisateur sont des paramètres accessible en écriture, comme celles dans les **Outils / Options** boîte de dialogue, les fenêtres de propriétés et certaines autres boîtes de dialogue. Extensions Visual Studio peuvent utiliser pour stocker de petites quantités de données. Cette procédure pas à pas montre comment ajouter le bloc-notes dans Visual Studio en tant qu’outil externe en lecture et écriture dans le magasin de paramètres.  
  
### <a name="backing-up-your-user-settings"></a>Sauvegarde de vos paramètres utilisateur  
  
1.  Vous devez être en mesure de réinitialiser les paramètres d’outils externes afin que vous puissiez déboguer et répétez la procédure. Pour ce faire, vous devez enregistrer les paramètres d’origine afin que vous pouvez les restaurer en fonction des besoins.  
  
2.  Ouvrez Regedit.exe.  
  
3.  Accédez aux outils de HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Assurez-vous que vous examinez la clé qui contient \14.0Exp\ et non \14.0\\. Lorsque vous exécutez l’instance expérimentale de Visual Studio, les paramètres utilisateur sont dans la ruche de Registre « 14.0Exp ».  
  
4.  Avec le bouton droit de la sous-clé \External Tools\, puis cliquez sur **exportation**. Assurez-vous que **branche sélectionnée** est sélectionnée.  
  
5.  Enregistrez le fichier externe Tools.reg résultant.  
  
6.  Plus tard, lorsque vous souhaitez réinitialiser les paramètres d’outils externes, sélectionnez la clé de Registre HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External partagés\ et cliquez sur **supprimer** dans le menu contextuel.  
  
7.  Lors de la **confirmer la suppression de la clé** boîte de dialogue s’affiche, cliquez sur **Oui**.  
  
8.  Cliquez sur le fichier Tools.reg externe que vous avez enregistré précédemment, cliquez sur **ouvrir avec**, puis cliquez sur **l’Éditeur du Registre**.  
  
## <a name="writing-to-the-user-settings-store"></a>Écriture dans le magasin de paramètres utilisateur  
  
1.  Créez un projet VSIX nommé UserSettingsStoreExtension, puis ajoutez une commande personnalisée nommée UserSettingsStoreCommand. Pour plus d’informations sur la création d’une commande personnalisée, consultez [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  Dans UserSettingsStoreCommand.cs, ajoutez les instructions using :  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  MenuItemCallback, supprimez le corps de la méthode et obtenir de l’utilisateur de stockent les paramètres, comme suit :  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Découvrez maintenant si le bloc-notes est déjà défini comme un outil externe. Vous devez effectuer une itération dans tous les outils externes pour déterminer si le paramètre ToolCmd est « Notepad », comme suit :  
  
    ```c#  
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
  
5.  Si le bloc-notes n’a pas été défini comme un outil externe, définie comme suit :  
  
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
  
6.  Tester le code. N’oubliez pas qu’il ajoute le bloc-notes comme un outil externe, donc vous devez restaurer le Registre avant d’exécuter une deuxième fois.  
  
7.  Générer le code et démarrer le débogage.  
  
8.  Sur le **outils** menu, cliquez sur **UserSettingsStoreCommand appeler**. Cette opération ajoute le bloc-notes pour le **outils** menu.  
  
9. À présent, vous devez voir le bloc-notes dans le menu Outils / Options de menu, puis en cliquant sur **bloc-notes** doit afficher une instance de bloc-notes.
