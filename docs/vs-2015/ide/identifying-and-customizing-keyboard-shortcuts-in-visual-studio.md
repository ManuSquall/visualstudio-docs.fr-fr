---
title: Identification et personnalisation des raccourcis clavier
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e63395838d7d91170d54edbb07c0b38db548ccdf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670489"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identification et personnalisation des raccourcis clavier dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez identifier les raccourcis clavier pour les commandes Visual Studio, personnaliser ces raccourcis, et les exporter afin que d'autres utilisateurs puissent les utiliser. De nombreux raccourcis appellent toujours les mêmes commandes, mais le comportement d'un raccourci peut varier selon les conditions suivantes :

- Les paramètres d'environnement par défaut que vous avez choisis la première fois que vous avez exécuté Visual Studio (par exemple, les paramètres de développement généraux ou Visual C#).

- Si vous avez personnalisé ou non le comportement du raccourci.

- Le contexte dans lequel vous êtes au moment de choisir le raccourci. Par exemple, le raccourci F2 appelle la commande Edit.EditCell si vous utilisez le concepteur de paramètres et la commande File.Rename si vous utilisez Team Explorer.

  Indépendamment des paramètres, de la personnalisation et du contexte, vous pouvez toujours rechercher et changer un raccourci clavier dans la boîte de dialogue **Options**. Vous pouvez aussi rechercher les raccourcis clavier par défaut pour plusieurs douzaines de commandes dans [Raccourcis clavier par défaut pour les commandes fréquemment utilisées](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), et obtenir la liste complète des raccourcis par défaut (selon les Paramètres de développement généraux) dans [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **Dans cette rubrique**

- [Identification d’un raccourci clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Personnalisation d’un raccourci clavier](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Partage des raccourcis clavier personnalisés](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Si un raccourci est affecté à une commande du contexte global et à aucun autre contexte, ce raccourci appelle toujours cette commande. Mais un raccourci peut être affecté à une commande du contexte global et à une commande différente dans un contexte spécifique. Si vous utilisez un raccourci lorsque vous êtes dans le contexte spécifique, ce raccourci appelle la commande pour ce contexte spécifique, et non le contexte global.

> [!NOTE]
> Les paramètres et l'édition de Visual Studio peuvent modifier le nom et l'emplacement des commandes de menu et les options qui apparaissent dans les boîtes de dialogue. Cette rubrique est basée sur les **Paramètres de développement généraux**.

## <a name="bkmk_identify"></a> Identification d’un raccourci clavier

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Développez **Environnement**, puis choisissez **Clavier**.

     ![Afficher les raccourcis clavier dans la boîte de dialogue Options](../ide/media/optionskeyboard.png "|::ref1::|")

3. Dans la zone **Afficher les commandes contenant**, entrez tout ou partie du nom de la commande sans espaces.

     Vous pouvez, par exemple, rechercher des commandes pour **solutionexplorer**.

4. Dans la liste, choisissez la commande correcte.

     Par exemple, vous pouvez choisir **View.SolutionExplorer**.

5. Si la commande a un raccourci clavier, elle apparaît dans la liste **Raccourcis de la commande sélectionnée**.

     ![Afficher le raccourci d'une commande spécifiée](../ide/media/viewshortcut.png "|::ref2::|")

## <a name="bkmk_assign"></a> Personnalisation d’un raccourci clavier

1. Dans la barre de menus, sélectionnez **Outils**, **Options**.

2. Développez le dossier **Environnement**, puis choisissez **Clavier**.

     ![Afficher les raccourcis clavier dans la boîte de dialogue Options](../ide/media/optionskeyboard.png "|::ref3::|")

3. Dans la zone **Afficher les commandes contenant**, entrez tout ou partie du nom de la commande sans espaces.

     Vous pouvez, par exemple, rechercher des commandes pour **solutionexplorer**.

4. Dans la liste, choisissez la commande à laquelle vous souhaitez associer un raccourci clavier.

5. Dans la liste **Utiliser un nouveau raccourci dans**, choisissez la zone de fonctionnalités dans laquelle vous voulez utiliser le raccourci.

     Par exemple, choisissez **Global** si vous voulez que le raccourci fonctionne dans tous les contextes. Vous pouvez utiliser n'importe quel raccourci qui n'est pas mappé (comme Global) dans un autre éditeur. Sinon, l'éditeur substitue le raccourci.

    > [!NOTE]
    > Vous ne pouvez pas affecter les touches suivantes dans le cadre d’un raccourci clavier dans **Global** : Impr. écran/SYSTÈME, Arrêt défil., Pause/Attn, Tab, Verr. maj, Inser, Début, Fin, Pge préc., Pge suiv., touche du logo Windows, la touche Application, touches de direction ou touche Entrée ; Verr. num., Suppr ou Effacer sur le pavé numérique ; la combinaison Ctrl+Alt+Suppr.

6. Dans la zone **Appuyer sur les touches de raccourci**, entrez le raccourci à utiliser.

    > [!NOTE]
    > Vous pouvez créer un raccourci qui associe une lettre avec la touche Alt, la touche Ctrl, ou les deux. Vous pouvez également créer un raccourci qui associe la touche Maj et une lettre avec la touche Alt, la touche Ctrl, ou les deux.

     Si un raccourci est déjà affecté à une autre commande, il s’affiche dans la zone **Raccourci actuellement utilisé par**. Dans ce cas, choisissez la touche Retour arrière pour supprimer ce raccourci avant d'en essayer un autre.

     ![Attribuer un autre raccourci à une commande](../ide/media/reassignshortcut.png "|::ref4::|")

7. Choisissez le bouton **Assigner**.

    > [!NOTE]
    > Si vous spécifiez un raccourci différent pour une commande, choisissez le bouton **Assigner**, puis choisissez le bouton **Annuler**. La boîte de dialogue se ferme, mais le changement n’est pas restauré.

## <a name="bkmk_transfer"></a> Partage des raccourcis clavier personnalisés
 Vous pouvez partager les raccourcis clavier personnalisés en les exportant vers un fichier, puis en donnant le fichier à d'autres utilisateurs afin de pouvoir importer les données.

#### <a name="to-export-only-keyboard-shortcuts"></a>Pour exporter uniquement les raccourcis clavier

1. Dans la barre de menus, choisissez **Outils**, **Importation et exportation de paramètres**.

2. Choisissez **Exporter les paramètres d’environnement sélectionnés**, puis choisissez le bouton **Suivant**.

3. Sous **Quels paramètres souhaitez-vous exporter ?** , décochez la case **Tous les paramètres**, développez **Options**, puis **Environnement**.

4. Cochez la case **Clavier**, puis choisissez le bouton **Suivant**.

     ![Exporter uniquement les raccourcis clavier personnalisés](../ide/media/exportshortcuts.png "|::ref5::|")

5. Dans les zones **Comment voulez-vous appeler votre fichier des paramètres ?** et **Stocker mon fichier des paramètres dans ce répertoire**, laissez les valeurs par défaut ou spécifiez des valeurs différentes, puis choisissez le bouton **Terminer**.

     Par défaut, les raccourcis sont stockés dans un fichier du dossier %USERPROFILE%\Documents\Visual Studio 2013\Settings. Le nom du fichier reflète la date à laquelle vous avez exporté les paramètres, et l'extension est .vssettings.

#### <a name="to-import-only-keyboard-shortcuts"></a>Pour importer uniquement les raccourcis clavier

1. Dans la barre de menus, choisissez **Outils**, **Importation et exportation de paramètres**.

2. Choisissez la case d’option **Importer les paramètres d’environnement sélectionnés**, puis le bouton **Suivant**.

3. Choisissez la case d’option **Non, importer simplement de nouveaux paramètres en remplaçant mes paramètres actuels**, puis choisissez le bouton **Suivant**.

4. Sous **Mes paramètres**, choisissez le fichier qui contient les raccourcis que vous souhaitez importer, ou choisissez le bouton **Parcourir** pour rechercher le fichier approprié.

5. Choisissez le bouton **Suivant**.

6. Sous **Quels paramètres voulez-vous importer ?** , décochez la case **Tous les paramètres**, développez **Options**, puis **Environnement**.

7. Cochez la case **Clavier**, puis choisissez le bouton **Terminer**.

     ![Importer uniquement les raccourcis clavier personnalisés](../ide/media/importshortcuts.png "|::ref6::|")

## <a name="see-also"></a>Voir aussi
 [Fonctionnalités d’accessibilité de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
