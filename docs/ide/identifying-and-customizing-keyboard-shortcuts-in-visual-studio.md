---
title: Identification et personnalisation des raccourcis clavier dans Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7258a1ba99764fa7af7ce73874f447db99b8b168
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identification et personnalisation des raccourcis clavier dans Visual Studio

Vous pouvez identifier les raccourcis clavier pour les commandes Visual Studio, personnaliser ces raccourcis, et les exporter afin que d'autres utilisateurs puissent les utiliser. De nombreux raccourcis appellent toujours les mêmes commandes, mais le comportement d'un raccourci peut varier selon les conditions suivantes :

- Les paramètres d'environnement par défaut que vous avez choisis la première fois que vous avez exécuté Visual Studio (par exemple, les paramètres de développement généraux ou Visual C#).

- Si vous avez personnalisé ou non le comportement du raccourci.

- Le contexte dans lequel vous êtes au moment de choisir le raccourci. Par exemple, le raccourci F2 appelle la commande Edit.EditCell si vous utilisez le concepteur de paramètres et la commande File.Rename si vous utilisez Team Explorer.

Indépendamment des paramètres, de la personnalisation et du contexte, vous pouvez toujours rechercher et changer un raccourci clavier dans la boîte de dialogue **Options**. Vous pouvez aussi rechercher les raccourcis clavier par défaut pour plusieurs douzaines de commandes dans [Raccourcis clavier par défaut pour les commandes fréquemment utilisées](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), et obtenir la liste complète des raccourcis par défaut (selon les Paramètres de développement généraux) dans [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Si un raccourci est affecté à une commande du contexte global et à aucun autre contexte, ce raccourci appelle toujours cette commande. Mais un raccourci peut être affecté à une commande du contexte global et à une commande différente dans un contexte spécifique. Si vous utilisez un raccourci lorsque vous êtes dans le contexte spécifique, ce raccourci appelle la commande pour ce contexte spécifique, et non le contexte global.

> [!NOTE]
> Les paramètres et l'édition de Visual Studio peuvent modifier le nom et l'emplacement des commandes de menu et les options qui apparaissent dans les boîtes de dialogue. Cette rubrique est basée sur les **Paramètres de développement généraux**.

## <a name="identifying-a-keyboard-shortcut"></a>Identification d'un raccourci clavier

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Développez **Environnement**, puis choisissez **Clavier**.

   ![Afficher les raccourcis clavier dans la boîte de dialogue Options](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. Dans la zone **Afficher les commandes contenant**, entrez tout ou partie du nom de la commande sans espaces.

   Vous pouvez, par exemple, rechercher des commandes pour `solutionexplorer`.

4. Dans la liste, choisissez la commande correcte.

    Par exemple, vous pouvez choisir **View.SolutionExplorer**.

5. Si la commande a un raccourci clavier, elle apparaît dans la liste **Raccourcis de la commande sélectionnée**.

   ![Afficher le raccourci d’une commande spécifiée](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a>Personnalisation d'un raccourci clavier

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Développez le dossier **Environnement**, puis choisissez **Clavier**.

3. Facultatif : filtrez la liste des commandes en entrant tout ou partie du nom de la commande, sans espaces, dans la zone **Afficher les commandes contenant**.

4. Dans la liste, choisissez la commande à laquelle vous souhaitez associer un raccourci clavier.

Dans la liste **Utiliser un nouveau raccourci dans**, choisissez la zone de fonctionnalités dans laquelle vous voulez utiliser le raccourci.

    For example, you can choose **Global** if you want the shortcut to work in all contexts. You can use any shortcut that isn't mapped (as Global) in another editor. Otherwise, the editor overrides the shortcut.

    > [!NOTE]
    > You can't assign the following keys as part of a keyboard shortcut in **Global**: Print Scrn/Sys Rq, Scroll Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, the Windows logo key, the Application key, any of the Arrow keys, or Enter; Num Lock, Delete, or Clear on the numeric keypad; the Ctrl+Alt+Delete key combination.

6. Dans la zone **Appuyer sur les touches de raccourci**, entrez le raccourci à utiliser.

    > [!NOTE]
    > Vous pouvez créer un raccourci qui associe une lettre avec la touche Alt, la touche Ctrl, ou les deux. Vous pouvez également créer un raccourci qui associe la touche Maj et une lettre avec la touche Alt, la touche Ctrl, ou les deux.

     Si un raccourci est déjà affecté à une autre commande, il s’affiche dans la zone **Raccourci actuellement utilisé par**. Dans ce cas, choisissez la touche Retour arrière pour supprimer ce raccourci avant d'en essayer un autre.

    ![Attribuer un autre raccourci à une commande](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Choisissez le bouton **Assigner**.

    > [!NOTE]
    > Si vous spécifiez un raccourci différent pour une commande, choisissez le bouton **Assigner**, puis choisissez le bouton **Annuler**. La boîte de dialogue se ferme, mais le changement n’est pas restauré.

## <a name="sharing-custom-keyboard-shortcuts"></a>Partage des raccourcis clavier personnalisés

Vous pouvez partager les raccourcis clavier personnalisés en les exportant vers un fichier, puis en donnant le fichier à d'autres utilisateurs afin de pouvoir importer les données.

### <a name="to-export-only-keyboard-shortcuts"></a>Pour exporter uniquement les raccourcis clavier

1. Dans la barre de menus, choisissez **Outils**, **Importation et exportation de paramètres**.

2. Choisissez **Exporter les paramètres d’environnement sélectionnés**, puis choisissez le bouton **Suivant**.

3. Sous **Quels paramètres souhaitez-vous exporter ?**, décochez la case **Tous les paramètres**, développez **Options**, puis **Environnement**.

4. Cochez la case **Clavier**, puis choisissez le bouton **Suivant**.

    ![Exporter uniquement les raccourcis clavier personnalisés](../ide/media/exportshortcuts.png "ExportShortcuts")

5. Dans les zones **Comment voulez-vous appeler votre fichier des paramètres ?** et **Stocker mon fichier des paramètres dans ce répertoire**, laissez les valeurs par défaut ou spécifiez des valeurs différentes, puis choisissez le bouton **Terminer**.

    Par défaut, les raccourcis sont enregistrés dans un fichier du dossier %USERPROFILE%\Documents\Visual Studio 2017\Settings. Le nom du fichier reflète la date à laquelle vous avez exporté les paramètres, et l’extension est .vssettings.

### <a name="to-import-only-keyboard-shortcuts"></a>Pour importer uniquement les raccourcis clavier

1. Dans la barre de menus, choisissez **Outils**, **Importation et exportation de paramètres**.

2. Choisissez la case d’option **Importer les paramètres d’environnement sélectionnés**, puis le bouton **Suivant**.

3. Choisissez la case d’option **Non, importer simplement de nouveaux paramètres en remplaçant mes paramètres actuels**, puis choisissez le bouton **Suivant**.

4. Sous **Mes paramètres**, choisissez le fichier qui contient les raccourcis que vous souhaitez importer, ou choisissez le bouton **Parcourir** pour rechercher le fichier approprié.

5. Choisissez le bouton **Suivant**.

6.  Sous **Quels paramètres voulez-vous importer ?**, décochez la case **Tous les paramètres**, développez **Options**, puis **Environnement**.

7. Cochez la case **Clavier**, puis choisissez le bouton **Terminer**.

    ![Importer uniquement les raccourcis clavier personnalisés](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Voir aussi

[Fonctionnalités d’accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)