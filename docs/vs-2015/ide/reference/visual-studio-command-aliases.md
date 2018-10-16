---
title: Alias de commandes Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- aliases, Visual Studio commands
- Visual Studio, commands
- predefined command aliases
- commands, aliases
- Visual Studio commands
- pre-defined command aliases
- command aliases
ms.assetid: de8bb378-8c1c-4087-a9a5-537fa8314c19
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c2daf9aa4e92ef4a017f36cbcc806abc50d6bde
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240433"
---
# <a name="visual-studio-command-aliases"></a>Alias de commandes Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Les alias constituent un moyen rapide d’entrer une commande dans la zone **Rechercher/Commande** ou la fenêtre **Commande** en abrégeant le texte nécessaire pour exécuter la commande. Par exemple, au lieu d’entrer le texte `>File.OpenFile` pour afficher la boîte de dialogue **Ouvrir un fichier**, vous pouvez utiliser l’alias prédéfini `>of`.  
  
 Tapez `alias` dans la fenêtre **Commande** pour afficher la liste des alias actuels et leurs définitions. Tapez `>cls` pour effacer le contenu de la fenêtre **Commande**. Si vous souhaitez voir l’alias d’une commande spécifique, tapez `alias <command name>`.  
  
 Vous pouvez créer facilement votre propre alias pour l’une des commandes Visual Studio (avec ou sans arguments). Par exemple, la syntaxe permettant de créer un alias pour `File.NewFile MyFile.txt` est `alias MyAlias File.NewFile MyFile.txt`. Pour supprimer l’un de vos alias, utilisez `alias <alias name> /delete`.  
  
 Le tableau ci-dessous contient une liste des alias de commandes Visual Studio prédéfinis. Certains noms de commande possèdent plusieurs alias prédéfinis. Pour afficher des rubriques d’aide détaillées relatives à la syntaxe correcte, aux arguments et aux commutateurs de ces commandes, cliquez sur les liens correspondant à leurs noms dans le tableau suivant.  
  
|Nom de la commande|Alias|Nom complet|  
|------------------|-----------|-------------------|  
|[Imprimer, commande](../../ide/reference/print-command.md)|?|Debug.Print|  
|[Espion express, commande](../../ide/reference/quick-watch-command.md)|??|Debug.Quickwatch|  
|Ajouter un nouveau projet|AddProj|File.AddNewProject|  
|[Alias, commande](../../ide/reference/alias-command.md)|Alias|Tools.Alias|  
|Automatique (fenêtre)|Autos|Debug.Autos|  
|Points d'arrêt (fenêtre)|bl|Debug.Breakpoints|  
|Point d'arrêt|bp|Debug.ToggleBreakPoint|  
|Fenêtre Pile des appels|CallStack|Debug.CallStack|  
|Effacer les signets|ClearBook|Edit.ClearBookmarks|  
|Fermer|Close|File.Close|  
|Fermer tous les documents|CloseAll|Window.CloseAllDocuments|  
|Effacer tout|cls|Edit.ClearAll|  
|Mode Commande|cmd|View.CommandWindow|  
|Afficher le code|code|View.ViewCode|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md)|d|Debug.ListMemory|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères ANSI|da|Debug.ListMemory /Ansi|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Un octet)|db|Debug.ListMemory /Format:OneByte|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères ANSI (format Quatre octets)|dc|Debug.ListMemory /Format:FourBytes /Ansi|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Quatre octets)|dd|Debug.ListMemory /Format:FourBytes|  
|Supprimer jusqu'au début de la ligne|DelBOL|Edit.DeleteToBOL|  
|Supprimer jusqu'à la fin de la ligne|DelEOL|Edit.DeleteToEOL|  
|Supprimer l’espace horizontal|DelHSp|Edit.DeleteHorizontalWhitespace|  
|Concepteur de vues|concepteur|View.ViewDesigner|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Float)|df|Debug.ListMemory/Format:Float|  
|Code Machine (fenêtre)|disasm|Debug.Disassembly|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) (format Huit octets)|dq|Debug.ListMemory /Format:EightBytes|  
|[Afficher la mémoire, commande](../../ide/reference/list-memory-command.md) sous la forme de caractères Unicode|du|Debug.ListMemory /Unicode|  
|[Évaluer l’instruction, commande](../../ide/reference/evaluate-statement-command.md)|eval|Debug.EvaluateStatement|  
|Exit|Exit|File.Exit|  
|Mettre la sélection en forme|format|Edit.FormatSelection|  
|Plein écran|FullScreen|View.FullScreen|  
|[Démarrer, commande](../../ide/reference/start-command.md)|g|Debug.Start|  
|[Atteindre, commande](../../ide/reference/go-to-command.md)|GotoLn|Edit.GoTo|  
|Atteindre l'accolade|GotoBrace|Edit.GotoBrace|  
|F1 Aide|Help|Help.F1Help|  
|Mode Exécution|immed|Tools.ImmediateMode|  
|Insérer le fichier comme texte|InsertFile|Edit.InsertFileAsText|  
|[Afficher la pile des appels, commande](../../ide/reference/list-call-stack-command.md)|kb|Debug.ListCallStack|  
|Mettre en minuscules|Lcase|Edit.MakeLowercase|  
|Couper la ligne|LineCut|Edit.LineCut|  
|Supprimer la ligne|LineDel|Edit.LineDelete|  
|Liste des membres|ListMembers|Edit.ListMembers|  
|Fenêtre Variables locales|Locals|Debug.Locals|  
|[Enregistrer la sortie de la fenêtre de commande, commande](../../ide/reference/log-command-window-output-command.md)|Log|Tools.LogCommandWindowOutput|  
|Mode Marque de la fenêtre Commande|mark|Tools.CommandWindowMarkMode|  
|Mémoire (fenêtre)|Memory1|Debug.Memory1|  
|Mémoire 2 (fenêtre)|Memory2|Debug.Memory2|  
|Mémoire 3 (fenêtre)|Memory3|Debug.Memory3|  
|Mémoire 4 (fenêtre)|Memory4|Debug.Memory4|  
|[Définir la base, commande](../../ide/reference/set-radix-command.md)|n|Debug.SetRadix|  
|[Afficher le navigateur Web, commande](../../ide/reference/showwebbrowser-command.md)|nav navigate|View.ShowWebBrowser|  
|Signet suivant|NextBook|Edit.NextBookmark|  
|[Nouveau fichier, commande](../../ide/reference/new-file-command.md)|nf|File.NewFile|  
|Nouveau projet|np NewProj|File.NewProject|  
|[Ouvrir un fichier, commande](../../ide/reference/open-file-command.md)|of Open|File.OpenFile|  
|[Ouvrir un projet, commande](../../ide/reference/open-project-command.md)|op|File.OpenProject|  
|Réduire aux définitions/Arrêter le mode Plan|OutlineDefs StopOutlining|Edit.CollapsetoDefinitions|  
|Pas à pas principal|p|Debug.StepOver|  
|Informations sur les paramètres|ParamInfo|Edit.ParameterInfo|  
|Pas à pas sortant|pr|Debug.StepOut|  
|Signet précédent|PrevBook|Edit.PreviousBookmark|  
|Imprimer le fichier|print|File.Print|  
|Fenêtre Propriétés|props|View.PropertiesWindow|  
|Arrêter|q|Debug.StopDebugging|  
|Rétablir|redo|Edit.Redo|  
|Registres (fenêtre)|registers|Debug.Registers|  
|Exécuter jusqu'au curseur|rtc|Debug.RunToCursor|  
|Enregistrer les éléments sélectionnés|save|File.SaveSelectedItems|  
|Enregistrer tout|SaveAll|File.SaveAll|  
|Enregistrer sous|SaveAs|File.SaveSelectedItemsAs|  
|[Shell, commande](../../ide/reference/shell-command.md)|shell|Tools.Shell|  
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
|[Afficher le code machine, commande](../../ide/reference/list-disassembly-command.md)|u|Debug.ListDisassembly|  
|Mettre en majuscules|Ucase|Edit.MakeUppercase|  
|Annuler|undo|Edit.Undo|  
|Remplacer les tabulations par des espaces dans la sélection|Untabify|Edit.UntabifySelection|  
|Fenêtre Espion|Watch|Debug.WatchN|  
|Activer/Désactiver le retour automatique à la ligne|WordWrap|Edit.ToggleWordWrap|  
|Afficher les processus|&#124;|Debug.ListProcesses|  
|[Répertorier les threads, commande](../../ide/reference/list-threads-command.md)|~ ~*k ~\*kb|Debug.ListThreads Debug.ListTheads /AllThreads|  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Rechercher/Commande, zone](../../ide/find-command-box.md)



