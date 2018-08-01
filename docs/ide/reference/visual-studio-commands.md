---
title: Commandes Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Visual Studio, commands
- commands, Visual Studio
- command syntax
ms.assetid: 76ffa394-ee89-4629-aba9-1a62b72e6cc1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75b2a889c00245b983305d56e9eb79d78d0d4966
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176864"
---
# <a name="visual-studio-commands"></a>Commandes Visual Studio
Les commandes Visual Studio vous permettent d’appeler une commande depuis la fenêtre **Commande** , depuis la fenêtre **Exécution** ou depuis la zone **Rechercher/Commande** . Dans chaque cas, le signe Supérieur à (`>`) est utilisé pour indiquer qu’une commande doit suivre, et non pas une opération de recherche ou de débogage.

 Vous pouvez trouver une liste complète des commandes et leur syntaxe dans la boîte de dialogue **Clavier, Options d’environnement** .

 Le caractère d’échappement pour les commandes Visual Studio est un caractère d’accent circonflexe (^), ce qui signifie que le caractère qui le suit immédiatement est interprété littéralement et non pas comme un caractère de contrôle. Ceci permet d’incorporer des guillemets ("), des espaces, des barres obliques, des accents circonflexes ou tout autre caractère littéral dans une valeur de paramètre ou de commutateur, à l’exception des noms de commutateur. Par exemple :

```
>Edit.Find ^^t /regex
```

 Un accent circonflexe fonctionne de la même façon, qu’il soit à l’intérieur ou en dehors des guillemets. Si un accent circonflexe est le dernier caractère de la ligne, il est ignoré.

 Dans les versions localisées de l’IDE, les noms des commandes peuvent être entrés dans la langue native de l’IDE ou en anglais. Par exemple, vous pouvez taper `File.NewFile` ou `Fichier.NouveauFichier` dans l’IDE localisé en français pour exécuter la même commande.

 De nombreuses commandes ont des alias. Pour obtenir la liste des alias de commande, consultez [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md).

 Les commandes suivantes prennent des arguments et/ou des commutateurs.

|Nom de la commande|Description|
|------------------|-----------------|
|[Ajouter un élément existant](../../ide/reference/add-existing-item-command.md)|Ajoute un fichier existant à la solution actuelle et l’ouvre.|
|[Ajouter un projet existant](../../ide/reference/add-existing-project-command.md)|Ajoute un projet existant à la solution actuelle.|
|[Ajouter un nouvel élément](../../ide/reference/add-new-item-command.md)|Ajoute un nouvel élément de solution, par exemple un fichier .htm, .css ou .txt, ou un jeu de frames, à la solution actuelle et l’ouvre.|
|[Alias](../../ide/reference/alias-command.md)|Crée un alias pour une commande complète, pour une commande complète et des arguments, ou même pour un autre alias.|
|[Évaluer l'instruction](../../ide/reference/evaluate-statement-command.md)|Évalue et affiche l’instruction donnée.|
|[Find](../../ide/reference/find-command.md)|Recherche des fichiers en utilisant un sous-ensemble des options disponibles sur le contrôle **Rechercher et remplacer** .|
|[Rechercher dans les fichiers](../../ide/reference/find-in-files-command.md)|Recherche des fichiers en utilisant un sous-ensemble des options disponibles sur le contrôle [Rechercher dans les fichiers](../../ide/find-in-files.md).|
|[Atteindre](../../ide/reference/go-to-command.md)|Déplace le curseur à la ligne spécifiée.|
|[Afficher la pile des appels](../../ide/reference/list-call-stack-command.md)|Affiche la pile des appels actuelle.|
|[Afficher le code machine](../../ide/reference/list-disassembly-command.md)|Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.|
|[Afficher la mémoire](../../ide/reference/list-memory-command.md)|Affiche le contenu de la plage de mémoire spécifiée.|
|[Afficher les modules](../../ide/reference/list-modules-command.md)|Répertorie les modules pour le processus en cours.|
|[Afficher les registres](../../ide/reference/list-registers-command.md)|Affiche une liste de registres.|
|[Afficher la source](../../ide/reference/list-source-command.md)|Affiche les lignes de code source spécifiées.|
|[Afficher les threads](../../ide/reference/list-threads-command.md)|Affiche une liste des threads du programme en cours.|
|[Enregistrer la sortie de la fenêtre Commande](../../ide/reference/log-command-window-output-command.md)|Copie toutes les entrées et sorties de la fenêtre Commande dans un fichier.|
|[Nouveau fichier](../../ide/reference/new-file-command.md)|Crée un fichier et l’ajoute au projet actuellement sélectionné.|
|[Ouvrir un fichier](../../ide/reference/open-file-command.md)|Ouvre un fichier existant et vous permet de spécifier un éditeur.|
|[Ouvrir un projet](../../ide/reference/open-project-command.md)|Ouvre un projet existant et vous permet de l’ajouter à la solution actuelle.|
|[Imprimer](../../ide/reference/print-command.md)|Évalue l’expression, et affiche le résultat ou le texte spécifié.|
|[Espion express, commande](../../ide/reference/quick-watch-command.md)|Affiche le texte sélectionné ou spécifié dans le champ **Expression** de la boîte de dialogue **Espion instantané** .|
|[Remplacer](../../ide/reference/replace-command.md)|Remplace du texte dans des fichiers en utilisant un sous-ensemble des options disponibles sur le contrôle **Rechercher et remplacer** .|
|[Remplacer dans les fichiers](../../ide/reference/replace-in-files-command.md)|Remplace du texte dans des fichiers en utilisant un sous-ensemble des options disponibles dans [Remplacer dans les fichiers](../../ide/replace-in-files.md).|
|[Définir le frame de pile en cours](../../ide/reference/set-current-stack-frame-command.md)|Vous permet d’afficher un frame de pile spécifique.|
|[Définir le thread actuel](../../ide/reference/set-current-thread-command.md)|Vous permet d’afficher un thread spécifique.|
|[Définir la base](../../ide/reference/set-radix-command.md)|Détermine le nombre d’octets à afficher.|
|[Shell](../../ide/reference/shell-command.md)|Lance les programmes à partir de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] comme si la commande avait été exécutée à partir de l’invite de commandes.|
|[Afficher le navigateur Web, commande](../../ide/reference/showwebbrowser-command.md)|Affiche l’URL spécifiée dans une fenêtre de navigateur web au sein ou en dehors de l’environnement de développement intégré (IDE).|
|[Démarrer](../../ide/reference/start-command.md)|Commence le processus de débogage et permet de spécifier comment les erreurs sont gérées.|
|[Chemin d’accès](../../ide/reference/symbol-path-command.md)|Définit la liste des répertoires où le débogueur recherche des symboles.|
|[Point d'arrêt](../../ide/reference/toggle-breakpoint-command.md)|Active ou désactive le point d’arrêt, en fonction de son état actuel, à l’emplacement actuel dans le fichier.|
|[Espion, commande](../../ide/reference/watch-command.md)|Crée et ouvre une instance spécifiée d’une fenêtre **Espion** .|

## <a name="see-also"></a>Voir aussi

- [Commande, fenêtre](../../ide/reference/command-window.md)
- [Rechercher/Commande, zone](../../ide/find-command-box.md)
- [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)