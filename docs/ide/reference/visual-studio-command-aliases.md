---
title: Alias de commandes
description: Découvrez comment utiliser des alias de commande pour taper moins de caractères lorsque vous souhaitez exécuter une commande.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54a33d56542065311b2614bad72593132b7908cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836200"
---
# <a name="visual-studio-command-aliases"></a>Alias de commandes Visual Studio

Les alias de commande vous permettent de taper moins de caractères quand vous souhaitez exécuter une commande. Entrez les alias dans la zone **Rechercher/Commande** ou dans la fenêtre **Commande**. Par exemple, au lieu d’entrer le texte `>File.OpenFile` pour afficher la boîte de dialogue **Ouvrir un fichier**, vous pouvez utiliser l’alias prédéfini `>of`.

Tapez `alias` dans la fenêtre **Commande** pour afficher la liste des alias actuels et leurs définitions. Tapez `>cls` pour effacer le contenu de la fenêtre **Commande**. Si vous souhaitez voir l’alias d’une commande spécifique, tapez `alias <command name>`.

Vous pouvez créer facilement votre propre alias pour l’une des commandes Visual Studio (avec ou sans arguments). Par exemple, la syntaxe permettant de créer un alias pour `File.NewFile MyFile.txt` est `alias MyAlias File.NewFile MyFile.txt`. Pour supprimer l’un de vos alias, utilisez `alias <alias name> /delete`.

Le tableau ci-dessous contient une liste des alias de commandes Visual Studio prédéfinis. Certains noms de commande possèdent plusieurs alias prédéfinis. Pour afficher des rubriques d’aide détaillées relatives à la syntaxe correcte, aux arguments et aux commutateurs de ces commandes, cliquez sur les liens correspondant à leurs noms dans le tableau suivant.

|Nom de la commande|Alias|Nom complet|
|------------------|-----------|-------------------|
|[Commande Imprimer](../../ide/reference/print-command.md)|?|Debug.Print|
|[Espion express, commande](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|
|Ajouter un nouveau projet|AddProj|File.AddNewProject|
|[Alias, commande](../../ide/reference/alias-command.md)|Alias|Tools.Alias|
|Automatique (fenêtre)|Autos|Debug.Autos|
|Points d'arrêt (fenêtre)|bl|Debug.Breakpoints|
|Basculer le point d'arrêt|bp|Debug.ToggleBreakPoint|
|Fenêtre Pile des appels|CallStack|Debug.CallStack|
|Effacer les signets|ClearBook|Edit.ClearBookmarks|
|fermez|fermez|File.Close|
|Fermer tous les documents|CloseAll|Window.CloseAllDocuments|
|Effacer tout|sécurité au niveau des colonnes|Edit.ClearAll|
|Mode Commande|cmd|View.CommandWindow|
|Afficher le code|code|View.ViewCode|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères ANSI|da|Debug.ListMemory /Ansi|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Un octet)|db|Debug.ListMemory /Format:OneByte|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères ANSI (format Quatre octets)|dc|Debug.ListMemory /Format:FourBytes /Ansi|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Quatre octets)|jj|Debug.ListMemory /Format:FourBytes|
|Supprimer jusqu'au début de la ligne|DelBOL|Edit.DeleteToBOL|
|Supprimer jusqu'à la fin de la ligne|DelEOL|Edit.DeleteToEOL|
|Supprimer l’espace horizontal|DelHSp|Edit.DeleteHorizontalWhitespace|
|Concepteur de vue|concepteur|View.ViewDesigner|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Float)|df|Debug.ListMemory/Format:Float|
|Code Machine (fenêtre)|disasm|Debug.Disassembly|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Huit octets)|dq|Debug.ListMemory /Format:EightBytes|
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères Unicode|du|Debug.ListMemory /Unicode|
|[Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|
|Quitter|Quitter|File.Exit|
|Mettre la sélection en forme|format|Edit.FormatSelection|
|Plein écran|FullScreen|View.FullScreen|
|[Démarrer, commande](../../ide/reference/start-command.md)|g|Debug.Start|
|[Atteindre, commande](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|
|Atteindre l'accolade|GotoBrace|Edit.GotoBrace|
|F1 Aide|Aide|Help.F1Help|
|Mode immédiat|immed|Tools.ImmediateMode|
|Insérer le fichier comme texte|InsertFile|Edit.InsertFileAsText|
|[Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|
|Mettre en minuscules|Lcase|Edit.MakeLowercase|
|Couper la ligne|LineCut|Edit.LineCut|
|Supprimer la ligne|LineDel|Edit.LineDelete|
|Liste des membres|ListMembers|Edit.ListMembers|
|Fenêtre Variables locales|Locals|Debug.Locals|
|[Commande Enregistrer la sortie de la fenêtre commande](../../ide/reference/log-command-window-output-command.md)|Journal|Tools.LogCommandWindowOutput|
|Mode Marque de la fenêtre Commande|mark|Tools.CommandWindowMarkMode|
|Mémoire (fenêtre)|Memory1|Debug.Memory1|
|Mémoire 2 (fenêtre)|Memory2|Debug.Memory2|
|Mémoire 3 (fenêtre)|Memory3|Debug.Memory3|
|Mémoire 4 (fenêtre)|Memory4|Debug.Memory4|
|[Définir la base, commande](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|
|[Commande ShowWebBrowser (](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|
|Signet suivant|NextBook|Edit.NextBookmark|
|[Nouveau fichier, commande](../../ide/reference/new-file-command.md)|nf|File.NewFile|
|Nouveau projet|np NewProj|File.NewProject|
|[Ouvrir un fichier (commande)](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|
|[Ouvrir un projet, commande](../../ide/reference/open-project-command.md)|op|File.OpenProject|
|Réduire aux définitions/Arrêter le mode Plan|OutlineDefs StopOutlining|Edit.CollapseToDefinitions|
|Pas à pas principal|p|Debug.StepOver|
|Informations sur les paramètres|ParamInfo|Edit.ParameterInfo|
|Pas à pas sortant|pr|Debug.StepOut|
|Signet précédent|PrevBook|Edit.PreviousBookmark|
|Imprimer le fichier|print|File.Print|
|Fenêtre Propriétés|props|View.PropertiesWindow|
|Arrêter|q|Debug.StopDebugging|
|Rétablir|rétablir|Edit.Redo|
|Registres (fenêtre)|registers|Debug.Registers|
|Exécuter jusqu'au curseur|rtc|Debug.RunToCursor|
|Enregistrer les éléments sélectionnés|Enregistrer|File.SaveSelectedItems|
|Enregistrer tout|SaveAll|File.SaveAll|
|Enregistrer sous|SaveAs|File.SaveSelectedItemsAs|
|[Commande shell](../../ide/reference/shell-command.md)|shell|Tools.Shell|
|Arrêter la recherche dans les fichiers|StopFind|Edit.FindInFiles /stop|
|Permuter l'ancre|SwapAnchor|Edit.SwapAnchor|
|Pas à pas détaillé|t|Debug.StepInto|
|Remplacer la sélection par des tabulations|tabify|Edit.TabifySelection|
|Liste des tâches (fenêtre)|TaskList|View.TaskList|
|Threads (fenêtre)|Threads|Debug.Threads|
|Mosaïque horizontale|TileH|Window.TileHorizontally|
|Mosaïque verticale|TileV|Window.TileVertically|
|Activer/Désactiver le signet|ToggleBook|Edit.ToggleBookmark|
|Fenêtre Boîte à outils|toolbox|View.Toolbox|
|[List code machine, commande](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|
|Mettre en majuscules|Ucase|Edit.MakeUppercase|
|Annuler|phase de restauration|Edit.Undo|
|Remplacer les tabulations par des espaces dans la sélection|Untabify|Edit.UntabifySelection|
|Fenêtre Espion|Espion|Debug.WatchN|
|Activer/Désactiver le retour automatique à la ligne|WordWrap|Edit.ToggleWordWrap|
|Afficher les processus|&#124;|Debug.ListProcesses|
|[Liste des threads, commande](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Fenêtre commande](../../ide/reference/command-window.md)
- [Zone Rechercher/commande](../../ide/find-command-box.md)
