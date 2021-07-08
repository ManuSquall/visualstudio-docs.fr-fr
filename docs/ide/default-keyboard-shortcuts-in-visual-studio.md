---
title: Raccourcis clavier par défaut
description: en savoir plus sur les raccourcis clavier par défaut dans Visual Studio qui vous permettent d’accéder à diverses commandes et fenêtres.
ms.custom: SEO-VS-2020
ms.date: 06/21/2021
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a63dbc1ad3ec544e52974a7ced9a69d4585ab629
ms.sourcegitcommit: b5744be07b7882e30bae67ef2810db56cf68344f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2021
ms.locfileid: "113487716"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Raccourcis clavier par défaut dans Visual Studio

Pour accéder à diverses [commandes](reference/visual-studio-commands.md) et fenêtres dans Visual Studio, vous pouvez choisir les raccourcis clavier appropriés. Cette page répertorie les raccourcis de commande par défaut propres au profil **Général**, que vous avez peut-être choisis en installant Visual Studio. Quel que soit le profil que vous avez choisi, vous pouvez [identifier le raccourci](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) d’une commande en ouvrant la boîte de dialogue **Options**, en développant le nœud **Environnement**, puis en choisissant **Clavier**. Vous pouvez également personnaliser vos raccourcis en assignant un raccourci différent à toute commande donnée.

Pour obtenir la liste des raccourcis clavier courants et d'autres informations sur la productivité, consultez :

- [Conseils d’utilisation du clavier](../ide/productivity-shortcuts.md)
- [Conseils de productivité](../ide/productivity-features.md).

pour plus d’informations sur l’accessibilité dans Visual Studio, consultez [conseils et astuces d’accessibilité](../ide/reference/accessibility-tips-and-tricks.md) et [comment : utiliser le clavier en mode exclusif](../ide/reference/how-to-use-the-keyboard-exclusively.md).

## <a name="most-popular-keyboard-shortcuts"></a>Raccourcis clavier les plus populaires

Tous les raccourcis de cette section s’appliquent globalement sauf indication contraire. Le contexte *Global* signifie que le raccourci s’applique dans n’importe quelle fenêtre Outil dans Visual Studio.

> [!NOTE]
> Vous pouvez [rechercher le raccourci](identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) d’une commande en ouvrant la boîte de dialogue **Options**, en développant le nœud **Environnement**, puis en choisissant **Clavier**.


#### <a name="build-popular-shortcuts"></a>Build : raccourcis populaires

|Commandes|Raccourcis clavier |ID de commande|
|-|-|-|
|Génère la solution|**Ctrl + Maj + B** | Build.BuildSolution |
|Annuler|**CTRL + ATTN** | Build.Cancel |
|Compiler|**Ctrl+F7** | Build.Compile |
|Exécuter l’analyse du code sur la solution|**Alt+F11**| Build.RunCodeAnalysisonSolution |

#### <a name="debug-popular-shortcuts"></a>Débogage : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Arrêter à la fonction|**CTRL + B**| Debug.BreakatFunction |
|Interrompre tout|**Ctrl + Alt + Attn**| Debug.BreakAll |
|Supprimer tous les points d'arrêt|**CTRL + MAJ + F9**| Debug.DeleteAllBreakpoints |
|Exceptions|**Ctrl + Alt + E**| Debug.Exceptions |
|Espion rapide|**Ctrl + Alt + Q**<br /><br />ou **MAJ + F9**| Debug.QuickWatch |
|Redémarrer|**Ctrl+Maj+F5**| Debug.Restart |
|Exécuter jusqu'au curseur|**Ctrl + F10**| Debug.RunToCursor |
|Définir l'instruction suivante|**Ctrl+Maj+F10**| Debug.SetNextStatement |
|Démarrer|**F5**| Debug.Start |
|Exécuter sans débogage|**CTRL + F5**| Debug.StartWithoutDebugging |
|Pas à pas détaillé|**F11**| Debug.StepInto |
|Pas à pas sortant|**Maj + F11**| Debug.StepOut |
|Pas à pas principal|**F10**| Debug.StepOver |
|Arrêter le débogage|**Maj + F5**| Debug.StopDebugging |
|Basculer le point d'arrêt|**F9**| Debug.ToggleBreakpoint |

#### <a name="edit-popular-shortcuts"></a>Modifier : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Saut de ligne|**entrée** [éditeur de texte, Concepteur de rapports, Concepteur Windows Forms]<br /><br />ou **MAJ + entrée** [éditeur de texte]| Edit.BreakLine |
|Réduire aux définitions|**Ctrl + M**, **Ctrl + O** [éditeur de texte]| Edit.CollapseToDefinitions |
|Sélection de commentaire|**CTRL + K**, **Ctrl + C** [éditeur de texte]| Edit.CommentSelection |
|Compléter le mot|**Alt + flèche droite** [éditeur de texte, concepteur de flux de travail]<br /><br />ou **Ctrl + barre d’espace** [éditeur de texte, concepteur de flux de travail]<br /><br />ou **CTRL + K**, **W** [Concepteur de flux de travail]<br /><br />ou **CTRL + K, CTRL + W** [Concepteur de flux de travail]| Edit.CompleteWord |
|Copier|**Ctrl + C**<br /><br />ou **Ctrl + Inser**| Edit.Copy |
|Couper|**Ctrl+X**<br /><br />ou **MAJ + SUPPR**| Edit.Cut |
|Supprimer|**Supprimer** [Team Explorer]<br /><br />ou **MAJ + SUPPR** [diagramme de séquence, diagramme d’activités UML, diagramme de couche]<br /><br />ou **Ctrl + Suppr** [diagramme de classes]| Edit.Delete |
|Rechercher|**Ctrl + F**| Edit.Find |
|Rechercher toutes les références|**Maj + F12**| Edit.FindAllReferences |
|Rechercher dans les fichiers|**Ctrl + Maj + F**| Edit.FindinFiles |
|Suivant|**F3**| Edit.FindNext |
|Rechercher la sélection suivante|**CTRL + F3**| Edit.FindNextSelected |
|Mettre en forme le document|**CTRL + K, Ctrl + D** [éditeur de texte]| Edit.FormatDocument |
|Sélection du format|**CTRL + K, Ctrl + F** [éditeur de texte]| Edit.FormatSelection |
|Accéder à|**CTRL + G**| Edit.GoTo |
|Atteindre la déclaration|**Ctrl + F12**| Edit.GoToDeclaration |
|Atteindre la définition|**F12**| Edit.GoToDefinition |
|Atteindre la liste déroulante de recherche|**Ctrl+D**| Edit.GoToFindCombo |
|Atteindre l’emplacement suivant|**F8**| Edit.GoToNextLocation |
|Insérer un extrait|**CTRL + K**, **CTRL + X**| Edit.InsertSnippet |
|Onglet Insérer|**onglet** [Concepteur de rapports, Concepteur Windows Forms, éditeur de texte]| Edit.InsertTab |
|Couper la ligne|**Ctrl + L** [éditeur de texte]| Edit.LineCut |
|Étendre la colonne d’une ligne vers le PG.|**Maj + Alt + flèche bas** [éditeur de texte]| Edit.LineDownExtendColumn |
|Ligne ouverte au-dessus|**Ctrl + Entrée** [éditeur de texte]| Edit.LineOpenAbove |
|Répertorier les membres|**Ctrl + J** [éditeur de texte, concepteur de flux de travail]<br /><br />ou **CTRL + K, Ctrl + L** [Concepteur de flux de travail]<br /><br />ou **CTRL + K, L** [Concepteur de flux de travail]| Edit.ListMembers |
|Accéder à|**CTRL +,**| Edit.NavigateTo |
|Ouvrir un fichier|**Ctrl + Maj + G**| Edit.OpenFile |
|Mode Refrappe|**Insérer** [éditeur de texte]| Edit.OvertypeMode |
|Informations sur les paramètres|**Ctrl + Maj + barre d’espace** [éditeur de texte, concepteur de flux de travail]<br /><br />ou **CTRL + K, Ctrl + P** [Concepteur de flux de travail]<br /><br />ou **CTRL + K, P** [Concepteur de flux de travail]| Edit.ParameterInfo |
|Coller|**Ctrl+V**<br /><br />ou **Maj + Inser**| Edit.Paste |
|Aperçu de définition|**ALT + F12** [éditeur de texte]| Edit.PeekDefinition |
|Rétablir|**CTRL + Y**<br /><br />ou **Maj + Alt + Retour arrière**<br /><br />ou **Ctrl + Maj + Z**| Edit.Redo |
|Replace|**Ctrl + H**| Edit.Replace |
|Sélectionner tout|**Ctrl + A**| Edit.SelectAll |
|Sélectionner le mot actuel|**CTRL + W** [éditeur de texte]| Edit.SelectCurrentWord |
|Annuler la sélection|**échap** [éditeur de texte, Concepteur de rapports, concepteur de Paramètres, Concepteur Windows Forms, éditeur de ressources managées]| Edit.SelectionCancel |
|Entourer de|**Ctrl + K, CTRL + S**| Edit.SurroundWith |
|Tabulation gauche|**maj + Tab** [éditeur de texte, Concepteur de rapports, éditeur de Windows Forms]| Edit.TabLeft |
|Activer/désactiver tout le mode plan|**Ctrl + M, Ctrl + L** [éditeur de texte]| Edit.ToggleAllOutlining |
|Activer/Désactiver le signet|**CTRL + k, CTRL + k** [éditeur de texte]| Edit.ToggleBookmark |
|Activer/désactiver le mode de saisie semi-automatique|**Ctrl + Alt + espace** [éditeur de texte]| Edit.ToggleCompletionMode |
|Activer/désactiver le développement du mode plan|**CTRL + m, CTRL + m** [éditeur de texte]| Edit.ToggleOutliningExpansion |
|Supprimer les marques de commentaire de la sélection|**CTRL + K, Ctrl + U** [éditeur de texte]| Edit.UncommentSelection |
|Annuler|**Ctrl+Z**<br /><br />ou **Alt + Retour arrière**| Edit.Undo |
|Suppression de mot à la fin|**Ctrl + Suppr** [éditeur de texte]| Edit.WordDeleteToEnd |
|Suppression des mots jusqu’au début|**Ctrl + Retour arrière** [éditeur de texte]| Edit.WordDeleteToStart |

#### <a name="file-popular-shortcuts"></a>Fichier : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Quitter|**ALT + F4**| File.Exit |
|Nouveau fichier|**Ctrl + N**| File.NewFile |
|Nouveau projet|**Ctrl + Maj + N**| File.NewProject |
|Nouveau site Web|**Maj+Alt+N**| File.NewWebSite |
|Ouvrir un fichier|**Ctrl+O**| File.OpenFile |
|Ouvrir le projet|**Ctrl + Maj + O**| File.OpenProject |
|Ouvrir le site Web|**Maj+Alt+O**| File.OpenWebSite |
|Renommer|**F2** [Team Explorer]| File.Rename |
|Enregistrer tout|**Ctrl + Maj + S**| File.SaveAll |
|Enregistrer les éléments sélectionnés|**Ctrl+S**| File.SaveSelectedItems |
|Afficher dans le navigateur|**Ctrl + Maj + W**| File.ViewinBrowser |

#### <a name="project-popular-shortcuts"></a>Project : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Ajouter un élément existant|**Maj + Alt + A**| Project.AddExistingItem |
|Ajouter un nouvel élément|**Ctrl + Maj + A**| Project.AddNewItem |

#### <a name="refactor-popular-shortcuts"></a>Refactoriser : raccourcis populaires

|Commande|Raccourci clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Extraire la méthode|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |

#### <a name="tools-popular-shortcuts"></a>Outils : raccourcis populaires

|Commande|Raccourci clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Attacher au processus|**Ctrl + Alt + P**| Tools.AttachtoProcess |

#### <a name="view-popular-shortcuts"></a>Affichage : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Affichage de classes|**Ctrl + Maj + C**| View.ClassView |
|Modifier l’étiquette|**F2**| View.EditLabel |
|Liste d'erreurs|**Ctrl + \\ , Ctrl + E**<br /><br />ou **CTRL + \\ , E**| View.ErrorList |
|Naviguer vers l’arrière|**Ctrl +-**| View.NavigateBackward |
|Naviguer vers l’avant|**Ctrl + Maj +-**| View.NavigateForward |
|Explorateur d’objets|**Ctrl + Alt + J**| View.ObjectBrowser |
|Output|**Ctrl + Alt + O**| View.Output |
|Fenêtre Propriétés|**F4**| View.PropertiesWindow |
|Actualiser|**F5** [Team Explorer]| View.Refresh |
|Explorateur de serveurs|**Ctrl + Alt + S**| View.ServerExplorer |
|Afficher la balise active|**Ctrl +.**<br /><br />ou **Maj + Alt + F10** [mode Design de l’éditeur HTML]| View.ShowSmartTag |
|Explorateur de solutions|**CTRL + ALT + L**| View.SolutionExplorer |
|TFS Team Explorer|**Ctrl + \\ , Ctrl + M**| View.TfsTeamExplorer |
|Boîte à outils|**CTRL + ALT + X**| View.Toolbox |
|Afficher le code|**Entrée** [diagramme de classes]<br /><br />ou **F7** [Paramètres Designer]| View.ViewCode |
|Concepteur de vue|**MAJ + F7** [vue source de l’éditeur HTML]| View.ViewDesigner |

#### <a name="window-popular-shortcuts"></a>Fenêtre : raccourcis populaires

|Commandes|Raccourcis clavier [contextes spéciaux]|ID de commande|
|-|-|-|
|Activer la fenêtre de document|**Échap**| Window.ActivateDocumentWindow |
|Fermer la fenêtre de document|**CTRL + F4**| Window.CloseDocumentWindow |
|Fenêtre de document suivante|**Ctrl + F6**| Window.NextDocumentWindow |
|Document suivant-fenêtre de navigation|**CTRL + TAB**| Window.NextDocumentWindowNav |
|Volet de fractionnement suivant|**F6**| Window.NextSplitPane |


## <a name="global-shortcuts"></a>Raccourcis globaux

Ces raccourcis clavier sont *globaux*, ce qui signifie que vous pouvez les utiliser lors de n’importe quelle fenêtre de Visual Studio est active.

- [Analyser](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)
- [Modifier](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)
- [Projet](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)
- [Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)
- [Architecture](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)
- [Menus contextuels de l'éditeur](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)
- [Menus contextuels Projet et Solution](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)
- [Explorateur de tests](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)
- [Créer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)
- [File](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)
- [Refactorisation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)
- [outils](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)
- [Menus contextuels de l’affichage de classes](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)
- [Aide](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)
- [Explorateur de solutions](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)
- [Afficher](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)
- [Déboguer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)
- [Test de charge](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)
- [Team](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)
- [Window](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)
- [Menus contextuels du débogueur](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)
- [Autres menus contextuels](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)
- [Menus contextuels Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)
- [Microsoft Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)
- [Concentrateur de diagnostic](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)

### <a name="analyze"></a><a name="bkmk_analyze"></a> Analyse

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Naviguer vers l’arrière|**Maj+Alt+3**| Analyze.NavigateBackward |
|Naviguer vers l’avant|**Maj+Alt+4**| Analyze.NavigateForward |

### <a name="architecture"></a><a name="bkmk_architecture"></a> Architecture

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Nouveau diagramme|**Ctrl + \\ , CTRL + N**| Architecture.NewDiagram |

### <a name="build"></a><a name="bkmk_build"></a> Build

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Génère la sélection|**Ctrl+B** (Visual Studio 2019)| Build.BuildSelection |
|Génère la solution|**Ctrl + Maj + B**| Build.BuildSolution |
|Annuler|**CTRL + ATTN**| Build.Cancel |
|Compiler|**Ctrl+F7**| Build.Compile |
|Exécuter l’analyse du code sur la solution|**Alt+F11**| Build.RunCodeAnalysisonSolution |

### <a name="class-view-context-menus"></a><a name="bkmk_classview"></a> Affichage de classes les menus contextuels

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Propriétés|**Alt + Entrée**| ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties |

### <a name="debug"></a><a name="bkmk_debug"></a> Debug

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Appliquer les modifications du code|**Alt+F10**| Debug.ApplyCodeChanges |
|Attacher au processus|**Ctrl + Alt + P**| Debug.AttachtoProcess |
|Autos|**Ctrl + Alt + V, A**| Debug.Autos |
|Interrompre tout|**Ctrl + Alt + Attn**| Debug.BreakAll |
|Points d’arrêt|**Ctrl + Alt + B**| Debug.Breakpoints |
|Pile des appels|**Ctrl + Alt + C**| Debug.CallStack |
|Supprimer tous les points d'arrêt|**CTRL + MAJ + F9**| Debug.DeleteAllBreakpoints |
|Lancer|**Alt+F2**| Debug.DiagnosticsHub.Launch |
|Code Machine|**CTRL + ALT + D**| Debug.Disassembly |
|Explorateur DOM|**Ctrl + Alt + V, D**| Debug.DOMExplorer |
|Activer le point d'arrêt|**Ctrl + F9**| Debug.EnableBreakpoint |
|Exceptions|**Ctrl + Alt + E**| Debug.Exceptions |
|Point d’arrêt sur fonction|**Ctrl+K, B** (Visual Studio 2019)<br />**CTRL** + **B** (Visual Studio 2017)| Debug.FunctionBreakpoint |
|Aller à l’appel ou l’événement IntelliTrace précédent|**Ctrl+Maj+F11**| Debug.GoToPreviousCallorIntelliTraceEvent |
|Démarrer les Diagnostics|**Alt + F5**| Debug.Graphics.StartDiagnostics |
|Immédiat|**Ctrl + Alt + I**| Debug.Immediate |
|Appels IntelliTrace|**Ctrl+Alt+Y, T**| Debug.IntelliTraceCalls |
|Événements IntelliTrace|**Ctrl+Alt+Y, F**| Debug.IntelliTraceEvents |
|Console JavaScript|**Ctrl + Alt + V, C**| Debug.JavaScriptConsole |
|Locals|**Ctrl + Alt + V, L**| Debug.Locals |
|Traiter la liste déroulante|**Ctrl + 5**| Debug.LocationToolbar.ProcessCombo |
|Combo de frame de pile|**CTRL + 7**| Debug.LocationToolbar.StackFrameCombo |
|Thread combo|**Ctrl + 6**| Debug.LocationToolbar.ThreadCombo |
|Activer/désactiver l’état de l’indicateur de thread actuel|**Ctrl + 8**| Debug.LocationToolbar.ToggleCurrentThreadFlaggedState |
|Activer/désactiver les threads avec indicateur|**Ctrl + 9**| Debug.LocationToolbar.ToggleFlaggedThreads |
|Mémoire 1|**Ctrl+Alt+M, 1**| Debug.Memory1 |
|Mémoire 2|**Ctrl+Alt+M, 2**| Debug.Memory2 |
|Mémoire 3|**Ctrl+Alt+M, 3**| Debug.Memory3 |
|Mémoire 4|**Ctrl+Alt+M, 4**| Debug.Memory4 |
|Modules|**Ctrl+Alt+U**| Debug.Modules |
|Piles parallèles|**Ctrl + Maj + D, S**| Debug.ParallelStacks |
|Espion parallèle 1|**Ctrl+Maj+D, 1**| Debug.ParallelWatch1 |
|Espion parallèle 2|**Ctrl+Maj+D, 2**| Debug.ParallelWatch2 |
|Espion parallèle 3|**Ctrl+Maj+D, 3**| Debug.ParallelWatch3 |
|Espion parallèle 4|**Ctrl+Maj+D, 4**| Debug.ParallelWatch4 |
|Processus|**CTRL + ALT + Z**| Debug.Processes |
|Espion rapide|**Maj+F9** ou **Ctrl+Alt+Q**| Debug.QuickWatch |
|Rattacher au processus|**Maj+Alt+P**| Débogage. ReattachtoProcess |
|Actualiser windowsapp|**Ctrl + Maj + R**| Debug.RefreshWindowsapp |
|Registres|**Ctrl + Alt + G**| Debug.Registers |
|Redémarrer|**Ctrl+Maj+F5**| Debug.Restart |
|Exécuter jusqu'au curseur|**Ctrl + F10**| Debug.RunToCursor |
|Définir l'instruction suivante|**Ctrl+Maj+F10**| Debug.SetNextStatement |
|Afficher la pile d’appels sur la carte du code|**Ctrl + Maj + '**| Debug.ShowCallStackonCodeMap |
|Afficher l'instruction suivante|**ALT + NUM** *| Debug.ShowNextStatement |
|Démarrer|**F5**| Debug.Start |
|Démarrer l’analyse des applications Windows Phone|**Alt + F1**| Debug.StartWindowsPhoneApplicationAnalysis |
|Exécuter sans débogage|**CTRL + F5**| Debug.StartWithoutDebugging |
|Pas à pas détaillé|**F11**| Debug.StepInto |
|Pas à pas détaillé du processus actuel|**Ctrl+Alt+F11**| Debug.StepIntoCurrentProcess |
|Pas à pas détaillé spécifique|**Maj + Alt + F11**| Debug.StepIntoSpecific |
|Pas à pas sortant|**Maj + F11**| Debug.StepOut |
|Pas à pas sortant du processus actuel|**Ctrl+Maj+Alt+F11**| Debug.StepOutCurrentProcess |
|Pas à pas principal|**F10** (lors du débogage : effectue une action de pas à pas principal)| Debug.StepOver |
|Pas à pas principal|**F10** (lorsque vous ne déboguez pas : démarre le débogage et s’arrête sur la première ligne du code utilisateur)| Debug.StepOver |
|Pas à pas principal dans le processus actuel|**Ctrl+Alt+F10**| Debug.StepOverCurrentProcess |
|Arrêter le débogage|**Maj + F5**| Debug.StopDebugging |
|Arrêter l’analyse des performances|**Maj+Alt+F2**| Debug.StopPerformanceAnalysis |
|Tâches|**Ctrl + Maj + D, K**| Debug.Tasks |
|Threads|**Ctrl + Alt + H**| Debug.Threads |
|Basculer le point d'arrêt|**F9**| Debug.ToggleBreakpoint |
|Basculer le code machine|**Ctrl + F11**| Debug.ToggleDisassembly |
|Espion 1|**Ctrl + Alt + W, 1**| Debug.Watch1 |
|Espion 2|**Ctrl + Alt + W, 2**| Debug.Watch2 |
|Espion 3|**Ctrl + Alt + W, 3**| Debug.Watch3 |
|Espion 4|**Ctrl + Alt + W, 4**| Debug.Watch4 |

### <a name="debugger-context-menus"></a><a name="bkmk_debugger"></a> Menus contextuels du débogueur

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Supprimer|**Alt + F9, D**| DebuggerContextMenus.BreakpointsWindow.Delete |
|Atteindre le code machine|**Alt+F9, A**| DebuggerContextMenus.BreakpointsWindow.GoToDisassembly |
|Atteindre le code source|**Alt+F9, S**| DebuggerContextMenus.BreakpointsWindow.GoToSourceCode |

### <a name="diagnostics-hub"></a><a name="bkmk_diagnostics"></a> Hub de diagnostic

|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Arrêter la collecte|**Ctrl + Alt + F2**| DiagnosticsHub.StopCollection |

### <a name="edit"></a><a name="bkmk_edit"></a> Modifier

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Copier|**Ctrl + C**<br /><br /> ou<br /><br /> **CTRL + INS**| Edit.Copy |
|Couper|**Ctrl + X**<br /><br /> ou<br /><br /> **Maj + Suppr**| Edit.Cut |
|Cycle presse-papiers circulaire|**Ctrl + Maj + V**<br /><br /> ou<br /><br /> **Ctrl+Maj+Insert**| Edit.CycleClipboardRing |
|Supprimer|**Supprimer**| Edit.Delete |
|Dupliquer|**Ctrl+D**| Edit.Duplicate |
|Rechercher|**Ctrl + F**| Edit.Find |
|Rechercher toutes les références|**Maj + F12**| Edit.FindAllReferences |
|Rechercher dans les fichiers|**Ctrl + Maj + F**| Edit.FindinFiles |
|Suivant|**F3**| Edit.FindNext |
|Rechercher la sélection suivante|**CTRL + F3**| Edit.FindNextSelected |
|Précédent|**Maj + F3**| Edit.FindPrevious |
|Rechercher la sélection précédente|**Ctrl + Maj + F3**| Edit.FindPreviousSelected |
|Générer la méthode|**Ctrl+K, Ctrl+M**| Edit.GenerateMethod |
|Accéder à|**CTRL + G**| Edit.GoTo |
|Atteindre tout|**Ctrl+,** ou **Ctrl+T**| Edit.GotoAll |
|Atteindre la déclaration|**Ctrl + F12**| Edit.GoToDeclaration |
|Atteindre la définition|**F12**| Edit.GoToDefinition |
|Atteindre le membre|**CTRL+1, Ctrl+M** ou **Ctrl+1, M** ou **Alt+\\**| Edit.GoToMember |
|Atteindre l’emplacement suivant|**F8** (erreur suivante dans la Liste d’erreurs ou une fenêtre de production)| Edit.GoToNextLocation |
|Atteindre l’emplacement précédent|**Maj+F8** (erreur précédente dans la Liste d’erreurs ou une fenêtre de production)| Edit.GoToPrevLocation |
|Insérer un extrait|**Ctrl + K, CTRL + X**| Edit.InsertSnippet |
|Déplacer le contrôle vers le dessous|**Ctrl + flèche bas**| Edit.MoveControlDown |
|Déplacer le contrôle vers le dessous|**Flèche bas**| Edit.MoveControlDownGrid |
|Déplacer le contrôle vers la gauche|**Ctrl + flèche gauche**| Edit.MoveControlLeft |
|Déplacer la grille de gauche du contrôle|**Flèche gauche**| Edit.MoveControlLeftGrid |
|Déplacer le contrôle vers la droite|**Ctrl + flèche droite**| Edit.MoveControlRight |
|Déplacer la grille de droite du contrôle|**Flèche droite**| Edit.MoveControlRightGrid |
|Déplacer le contrôle vers le haut|**Ctrl + flèche haut**| Edit.MoveControlUp |
|Déplacer la grille de contrôle vers le haut|**Flèche haut**| Edit.MoveControlUpGrid |
|Signet suivant|**Ctrl + K, CTRL + N**| Edit.NextBookmark |
|Signet suivant dans le dossier|**Ctrl + Maj + K, Ctrl + Maj + N**| Edit.NextBookmarkInFolder |
|Ouvrir un fichier|**CTRL+MAJ+G** (ouvre le nom du fichier sous le curseur)| Edit.OpenFile |
|Coller|**Ctrl + V**<br /><br /> ou<br /><br /> **Maj + ins**| Edit.Paste |
|Signet précédent|**Ctrl + K, Ctrl + P**| Edit.PreviousBookmark |
|Signet précédent dans le dossier|**Ctrl + Maj + K, Ctrl + Maj + P**| Edit.PreviousBookmarkInFolder |
|Recherche rapide (symbole)|**Maj+Alt+F12**| Edit.QuickFindSymbol |
|Rétablir|**CTRL + Y**<br /><br /> ou<br /><br /> **Ctrl + Maj + Z**<br /><br /> ou<br /><br /> **Maj+Alt+Retour arrière**| Edit.Redo |
|Actualiser les références distantes|**Ctrl + Maj + J**| Edit.RefreshRemoteReferences |
|Replace|**Ctrl + H**| Edit.Replace |
|Remplacer dans les fichiers|**Ctrl + Maj + H**| Edit.ReplaceinFiles |
|Sélectionner tout|**Ctrl + A**| Edit.SelectAll |
|Sélectionner le contrôle suivant|**Tab**| Edit.SelectNextControl |
|Sélectionner le contrôle précédent|**Maj + Tab**| Edit.SelectPreviousControl |
|Afficher la grille de mosaïques|**Entrée**| Edit.ShowTileGrid |
|Contrôle de la taille en dessous|**Ctrl+Maj+Bas**| Edit.SizeControlDown |
|Grille de contrôle en baisse de la taille|**Maj + Flèche bas**| Edit.SizeControlDownGrid |
|Contrôle de la taille à gauche|**Ctrl+Maj+Gauche**| Edit.SizeControlLeft |
|Grille gauche du contrôle de taille|**Maj + Flèche gauche**| Edit.SizeControlLeftGrid |
|Redimensionner le contrôle vers la droite|**Ctrl + Maj + droite**| Edit.SizeControlRight |
|Grille droite du contrôle de taille|**Maj + Flèche droite**| Edit.SizeControlRightGrid |
|Contrôle de la taille|**Ctrl + Maj + haut**| Edit.SizeControlUp |
|Grille de contrôle de la taille|**Maj + haut**| Edit.SizeControlUpGrid |
|Arrêter la recherche|**Alt + F3, S**| Edit.StopSearch |
|Entourer de|**Ctrl + K, CTRL + S**| Edit.SurroundWith |
|Annuler|**Ctrl + Z**<br /><br /> ou<br /><br /> **Alt + Retour arrière**| Edit.Undo |

### <a name="editor-context-menus"></a><a name="bkmk_editorContext"></a> Menus contextuels de l’éditeur

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Conditions de point d’arrêt|**Alt + F9, C**| EditorContextMenus. CodeWindow. Breakpoint. BreakpointConditions |
|Point d’arrêt-modifier les étiquettes|**Alt + F9, L**| EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels |
|Afficher l’élément|**Ctrl + «**| EditorContextMenus.CodeWindow.CodeMap.ShowItem |
|Execute|**Ctrl+Alt+F5**| EditorContextMenus.CodeWindow.Execute |
|Accéder à la vue|**Ctrl+M, Ctrl+G**| EditorContextMenus.CodeWindow.GoToView |
|Basculer le fichier de code d’en-tête|**Ctrl+K, Ctrl+O** (lettre « O »)| EditorContextMenus.CodeWindow.ToggleHeaderCodeFile |
|Afficher la hiérarchie d'appels|**Ctrl+K, Ctrl+T**<br /><br /> ou<br /><br /> **Ctrl+K, T**| EditorContextMenus.CodeWindow.ViewCallHierarchy |

### <a name="file"></a><a name="bkmk_file"></a> Txt

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Quitter|**ALT + F4**| File.Exit |
|Nouveau fichier|**Ctrl + N**| File.NewFile |
|Nouveau projet|**Ctrl + Maj + N**| File.NewProject |
|Nouveau site Web|**Maj+Alt+N**| File.NewWebSite |
|Ouvrir un fichier|**Ctrl+O** (lettre « O »)| File.OpenFile |
|Ouvrir le projet|**Ctrl+Maj+O** (lettre « O »)| File.OpenProject |
|Ouvrir le site Web|**Maj+Alt+O** (lettre « O »)| File.OpenWebSite |
|Impression|**Ctrl + P**| File.Print |
|Enregistrer tout|**Ctrl + Maj + S**| File.SaveAll |
|Enregistrer les éléments sélectionnés|**Ctrl+S**| File.SaveSelectedItems |
|Afficher dans le navigateur|**Ctrl + Maj + W**| File.ViewinBrowser |

### <a name="help"></a><a name="bkmk_help"></a> Aide

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Ajouter et supprimer le contenu d’aide|**Ctrl + Alt + F1**| Help.AddandRemoveHelpContent |
|Aide (F1)|**F1**| Help.F1Help |
|Afficher l’aide|**Ctrl + F1**| Help.ViewHelp |
|Aide sur la fenêtre|**MAJ + F1**| Help.WindowHelp |

### <a name="load-test"></a><a name="bkmk_loadtest"></a> Test de charge

|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Accéder au volet compteur|**Ctrl+R, Q**| LoadTest.JumpToCounterPane |

### <a name="other-context-menus"></a><a name="bkmk_otherContext"></a> Autres menus contextuels

|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Ajouter un nouveau diagramme|**Insérer**| OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram |

### <a name="project"></a><a name="bkmk_project"></a> Projet

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Ajouter un élément existant|**Maj + Alt + A**| Project.AddExistingItem |
|Ajouter un nouvel élément|**Ctrl + Maj + A**| Project.AddNewItem |
|Assistant classe|**Ctrl + Maj + X**| Project.ClassWizard |
|Écraser|**Ctrl+Alt+Insert**| Project.Override |
|Prévisualiser les modifications|**Alt+;**, puis **Alt+C**| Project.Previewchanges |
|Publier les fichiers sélectionnés|**Alt+;**, puis **Alt+P**| Project.Publishselectedfiles |
|Remplacer les fichiers sélectionnés sur le serveur|**Alt+;**, puis **Alt+R**| Project.Replaceselectedfilesfromserver |

### <a name="project-and-solution-context-menus"></a><a name="bkmk_projectContext"></a>Project et menus contextuels de solution

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Descendre|**Alt + flèche bas**| ProjectandSolutionContextMenus.Item.MoveDown |
|Monter|**Alt + Flèche haut**| ProjectandSolutionContextMenus.Item.MoveUp |

### <a name="refactor"></a><a name="bkmk_refactor"></a> Refactoriser

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Encapsuler le champ|**Ctrl+R, Ctrl+E**| Refactor.EncapsulateField |
|Extraire l’interface|**Ctrl+R, Ctrl+I**| Refactor.ExtractInterface |
|Extraire la méthode|**Ctrl+R, Ctrl+M**| Refactor.ExtractMethod |
|Supprimer les paramètres|**Ctrl+R, Ctrl+V**| Refactor.RemoveParameters |
|Renommer|**Ctrl+R, Ctrl+R**| Refactor.Rename |
|Réorganiser les paramètres|**Ctrl+R, Ctrl+O** (lettre « O »)| Refactor.ReorderParameters |

### <a name="solution-explorer"></a><a name="bkmk_solutionexplorerGLOBAL"></a> Explorateur de solutions

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Filtre des fichiers ouverts|**Ctrl+[**, **O** (lettre « O »)<br /><br /> ou<br /><br /> **Ctrl+[**, **Ctrl+O** (lettre « O »)| SolutionExplorer.OpenFilesFilter |
|Filtre des modifications en attente|**CTRL + [**, **P**<br /><br /> ou<br /><br /> **CTRL + [**, **Ctrl + P**| SolutionExplorer.PendingChangesFilter |
|Synchroniser avec le document actif|**CTRL + [**, **S**<br /><br /> ou<br /><br /> **CTRL + [**, **CTRL + S**| SolutionExplorer.SyncWithActiveDocument |

### <a name="team"></a><a name="bkmk_team"></a> Travail

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Accéder aux branches git|**Ctrl+0** (zéro), **Ctrl+N**<br /><br /> ou<br /><br /> **Ctrl+0, N**| Team.Git.GoToGitBranches |
|Accéder aux modifications git|**Ctrl+0** (zéro), **Ctrl+G**<br /><br /> ou<br /><br /> **Ctrl+0, G**| Team.Git.GoToGitChanges |
|Accéder aux validations git|**Ctrl+0** (zéro), **Ctrl+O** (lettre « O »)<br /><br /> ou<br /><br /> **Ctrl+0, O**| Team.Git.GoToGitCommits |
|Recherche dans Team Explorer|**Ctrl + «**| Team.TeamExplorerSearch |

### <a name="team-foundation-context-menus"></a><a name="bkmk_TFcontext"></a> Menus contextuels Team Foundation

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Accéder aux builds|**Ctrl+0** (zéro), **Ctrl+B**<br /><br /> ou<br /><br /> **Ctrl+0, B**| TeamFoundationContextMenus.Commands.GoToBuilds |
|Accéder à la connexion|**Ctrl+0** (zéro), **Ctrl+C**<br /><br /> ou<br /><br /> **Ctrl+0, C**| TeamFoundationContextMenus.Commands.GoToConnect |
|Accéder aux documents|**Ctrl+0** (zéro), **Ctrl+D**<br /><br /> ou<br /><br /> **Ctrl+0, D**| TeamFoundationContextMenus.Commands.GoToDocuments |
|Accéder à la page d’hébergement|**Ctrl+0** (zéro), **Ctrl+H**<br /><br /> ou<br /><br /> **Ctrl+0, H**| TeamFoundationContextMenus.Commands.GoToHome |
|Accéder à mon travail|**Ctrl+0** (zéro), **Ctrl+M**<br /><br /> ou<br /><br /> **Ctrl+0, M**| TeamFoundationContextMenus.Commands.GoToMyWork |
|Atteindre les modifications en attente|**Ctrl+0** (zéro), **Ctrl+P**<br /><br /> ou<br /><br /> **Ctrl+0, P**| TeamFoundationContextMenus.Commands.GoToPendingChanges |
|Accéder aux rapports|**Ctrl+0** (zéro), **Ctrl+R**<br /><br /> ou<br /><br /> **Ctrl+0, R**| TeamFoundationContextMenus.Commands.GoToReports |
|Accéder aux paramètres|**Ctrl+0** (zéro), **Ctrl+S**<br /><br /> ou<br /><br /> **Ctrl+0, S**| TeamFoundationContextMenus.Commands.GoToSettings |
|Accéder à l’accès Web|**Ctrl+0** (zéro), **Ctrl+A**<br /><br /> ou<br /><br /> **Ctrl+0, A**| TeamFoundationContextMenus.Commands.GoToWebAccess |
|Atteindre les éléments de travail|**Ctrl+0** (zéro), **Ctrl+W**<br /><br /> ou<br /><br /> **Ctrl+0, W**| TeamFoundationContextMenus.Commands.GoToWorkItems |

### <a name="test"></a><a name="bkmk_test"></a> Test

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Utiliser le générateur de test codé de l’interface utilisateur|**Ctrl + \\ , Ctrl + C**| Test.UseCodedUITestBuilder |
|Utiliser l’enregistrement des actions existant|**Ctrl + \\ , Ctrl + A**| Test.UseExistingActionRecording |

### <a name="test-explorer"></a><a name="bkmk_testexplorerGLOBAL"></a> Explorateur de tests

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Déboguer tous les tests|**Ctrl+R, Ctrl+A**| TestExplorer.DebugAllTests |
|Déboguer tous les tests en contexte|**Ctrl + R, Ctrl + T**| TestExplorer.DebugAllTestsInContext |
|Déboguer la dernière exécution|**Ctrl + R, D**| TestExplorer.DebugLastRun |
|Répéter la dernière exécution|**Ctrl + R, L**| TestExplorer.RepeatLastRun |
|Exécuter tous les tests|**Ctrl + R, A**| TestExplorer.RunAllTests |
|Exécuter tous les tests en contexte|**Ctrl + R, T**| TestExplorer.RunAllTestsInContext |
|Afficher l’Explorateur de tests|**Ctrl + E, T**| TestExplorer.ShowTestExplorer |
|Ouvrir l’onglet|**Ctrl + E, L**| LiveUnitTesting.OpenTab |
|Résultats de la couverture du code|**Ctrl+E, C**| Test. CodeCoverageResults |

### <a name="tools"></a><a name="bkmk_tools"></a> Outils

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Attacher au processus|**Ctrl + Alt + P**| Tools.AttachtoProcess |
|Gestionnaire des extraits de code|**Ctrl + K, CTRL + B**| Tools.CodeSnippetsManager |
|Forcer le gc|**Ctrl+Maj+Alt+F12, Ctrl+Maj+Alt+F12**| Tools.ForceGC |

### <a name="view"></a><a name="bkmk_view"></a> Affichage

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Toutes les fenêtres|**Maj+Alt+M**| View.AllWindows |
|Navigateur de l'architecture|**Ctrl + \\ , Ctrl + R**| View.ArchitectureExplorer |
|d’un plan|**ALT+flèche gauche** (fonctions différentes de View.NavigateBackward dans l’éditeur de texte)| View.Backward |
|Fenêtre signet|**Ctrl + K, CTRL + W**| View.BookmarkWindow |
|Navigue jusqu'au suivant|**CTRL + MAJ + 1**| View.BrowseNext |
|Navigue jusqu'au précédent|**Ctrl + Maj + 2**| View.BrowsePrevious |
|Hiérarchie d'appels|**Ctrl + Alt + K**| View.CallHierarchy |
|Affichage de classes|**Ctrl + Maj + C**| View.ClassView |
|Affichage de classes-aller à rechercher|**Ctrl+K, Ctrl+V**| View.ClassViewGoToSearchCombo |
|Fenêtre définition de code|**Ctrl + \\ , D**<br /><br /> ou<br /><br /> **Ctrl + \\ , Ctrl + D**| View.CodeDefinitionWindow |
|Fenêtre Commande|**Ctrl + Alt + A**| View.CommandWindow |
|Sources de données|**Maj+Alt+D**| View.DataSources |
|Structure du document|**Ctrl + Alt + T**| View.DocumentOutline |
|Modifier l’étiquette|**F2**| View.EditLabel |
|Liste d'erreurs|**Ctrl + \\ , E**<br /><br /> ou<br /><br /> **Ctrl + \\ , Ctrl + E**| View.ErrorList |
|F# interactif|**Ctrl + Alt + F**| View.F#Interactive |
|Résultats de la recherche de symbole|**Ctrl+Alt+F12**| View.FindSymbolResults |
|Transférer|**ALT+flèche droite** (fonctions différentes de View.NavigateForward dans l’éditeur de texte)| View.Forward |
|Parcourir le contexte en aval|**Ctrl + Maj + 7**| View.ForwardBrowseContext |
|Plein écran|**Maj + Alt + Entrée**| View.FullScreen |
|Naviguer vers l’arrière|**Ctrl +-**| View.NavigateBackward |
|Naviguer vers l’avant|**Ctrl + Maj +-**| View.NavigateForward |
|Erreur suivante|**Ctrl + Maj + F12**| View.NextError |
|Notifications|**Ctrl+W, N**<br /><br /> ou<br /><br /> **Ctrl+W, Ctrl+N**| View.Notifications |
|Explorateur d’objets|**Ctrl + Alt + J**| View.ObjectBrowser |
|Explorateur d’objets-accéder à la zone de recherche|**Ctrl+K, Ctrl+R**| View.ObjectBrowserGoToSearchCombo |
|Output|**Ctrl+Alt+O** (lettre « O »)| View.Output |
|Contexte de navigation dans le menu déroulant|**CTRL+MAJ+8** (C++ uniquement)| View.PopBrowseContext |
|Fenêtre Propriétés|**F4**| View.PropertiesWindow |
|pages de propriétés|**Maj+F4**| View.PropertyPages |
|Affichage des ressources|**CTRL + MAJ + E**| View.ResourceView |
|Explorateur de serveurs|**Ctrl + Alt + S**| View.ServerExplorer |
|Afficher la balise active|**Maj + Alt + F10**<br /><br /> ou<br /><br /> **Ctrl +.**| View.ShowSmartTag |
|Explorateur de solutions|**CTRL + ALT + L**| View.SolutionExplorer |
|explorateur d’objets de serveur SQL|**Ctrl + \\ , CTRL + S**| View.SQLServerObjectExplorer |
|Liste des tâches|**Ctrl + \\ , T**<br /><br /> ou<br /><br /> **Ctrl + \\ , Ctrl + T**| View.TaskList |
|TFS Team Explorer|**Ctrl + \\ , Ctrl + M**| View.TfsTeamExplorer |
|Boîte à outils|**CTRL + ALT + X**| View.Toolbox |
|Explorateur de modèles UML|**Ctrl + \\ , Ctrl + U**| View.UMLModelExplorer |
|Afficher le code|**F7**| View.ViewCode |
|Concepteur de vue|**Maj+F7**| View.ViewDesigner |
|un navigateur Web|**Ctrl + Alt + R**| View.WebBrowser |
|Faire un zoom avant|**Ctrl + Maj +.**| View.ZoomIn |
|Faire un zoom arrière|**Ctrl + Maj +,**| View.ZoomOut |
|Afficher l’Explorateur de tests|**Ctrl + E, T**| TestExplorer.ShowTestExplorer |

### <a name="window"></a><a name="bkmk_window"></a> Fenetre

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Activer la fenêtre de document|**Échap**| Window.ActivateDocumentWindow |
|Ajouter l’onglet à la sélection|**Ctrl+Maj+Alt+Espace**| Window.AddTabtoSelection |
|Fermer la fenêtre de document|**CTRL + F4**| Window.CloseDocumentWindow |
|Fermer la fenêtre outil|**MAJ + ÉCHAP**| Window.CloseToolWindow |
|Garder l’onglet ouvert|**Ctrl+Alt+Début**| Window.KeepTabOpen |
|Déplacer vers la barre de navigation|**Ctrl + F2**| Window.MovetoNavigationBar |
|Fenêtre de document suivante|**Ctrl + F6**| Window.NextDocumentWindow |
|Document suivant-fenêtre de navigation|**CTRL + TAB**| Window.NextDocumentWindowNav |
|Volet suivant|**ALT + F6**| Window.NextPane |
|Volet de fractionnement suivant|**F6**| Window.NextSplitPane |
|Onglet suivant|**Ctrl+Alt+Pg suiv**<br /><br /> ou<br /><br /> **Ctrl+PgDn**| Window.NextTab |
|Onglet suivant et ajouter à la sélection|**Ctrl+Maj+Alt+Pg suiv**| Window.NextTabandAddtoSelection |
|Navigation dans la fenêtre outil suivante|**Alt + F7**| Window.NextToolWindowNav |
|Fenêtre de document précédente|**CTRL + MAJ + F6**| Window.PreviousDocumentWindow |
|Document précédent, fenêtre NAV|**Ctrl + Maj + Tab**| Window.PreviousDocumentWindowNav |
|Volet précédent|**MAJ + ALT + F6**| Window.PreviousPane |
|Volet de fractionnement précédent|**Maj + F6**| Window.PreviousSplitPane |
|Onglet précédent|**Ctrl+Alt+Pg préc**<br /><br /> ou<br /><br /> **Ctrl+Pg préc**| Window.PreviousTab |
|Onglet précédent et ajouter à la sélection|**Ctrl+Maj+Alt+Pg préc**| Window.PreviousTabandAddtoSelection |
|Navigation dans la fenêtre outil précédente|**Maj + Alt + F7**| Window.PreviousToolWindowNav |
|Lancement rapide|**Ctrl + Q**| Window.QuickLaunch |
|Lancement rapide de la catégorie précédente|**Ctrl + Maj + Q**| Window.QuickLaunchPreviousCategory |
|Afficher le menu ancrer|**Alt +-**| Window.ShowDockMenu |
|Afficher la liste des fichiers MDI ex.|**Ctrl + Alt + flèche bas**| Window.ShowEzMDIFileList |
|Recherche dans l’Explorateur de solutions|**Ctrl +;**| Window.SolutionExplorerSearch |
|Recherche de fenêtres|**Alt + '**| Window.WindowSearch |

### <a name="azure"></a><a name="bkmk_windowsazure"></a> Bleu

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Nouvelle tentative d’exécution du script de service mobile|**Ctrl + num \* , Ctrl + R**| WindowsAzure.RetryMobileServiceScriptOperation |
|Afficher les détails de l’erreur de script du service mobile|**Ctrl + num \* , Ctrl + D**| WindowsAzure.ShowMobileServiceScriptErrorDetails |

## <a name="context-specific-shortcuts"></a>Raccourcis spécifiques au contexte


### <a name="adonet-entity-data-model-designer"></a>ADO.NET Entity Data Model Designer

Les raccourcis spécifiques à ce contexte sont les suivants :

|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Descendre|**Alt + flèche bas**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down |
|Inférieure à 5|**Alt+PgDn**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5 |
|Vers le bas|**Alt+Fin**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom |
|Vers le haut|**Alt + début**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop |
|Haut|**Alt + Flèche haut**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up |
|Jusqu’à 5|**Alt+Pg préc**| OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5 |
|Renommer|**Ctrl+R, R**| OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename |
|Supprimer du diagramme|**Maj+Suppr**| OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram |
|Explorateur de modèle de données d’entité|**CTRL + 1**| View.EntityDataModelBrowser |
|Détails de mappage du modèle EDM (Entity Data Model)|**CTRL + 2**| View.EntityDataModelMappingDetails |

### <a name="class-diagram"></a>Diagramme de classes

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Réduire|**Num -**| ClassDiagram.Collapse |
|Développez|**Num +**| ClassDiagram.Expand |
|Supprimer|**Ctrl+Suppr**| Edit.Delete |
|Développer la liste réduire le type de base|**Maj+Alt+B**| Edit.ExpandCollapseBaseTypeList |
|Accéder à l’interface Lollipop|**Maj+Alt+L**| Edit.NavigateToLollipop |
|Supprimer du diagramme|**Supprimer**| Edit.RemovefromDiagram |
|Afficher le code|**Entrée**| View.ViewCode |

### <a name="coded-ui-test-editor"></a>Éditeur de test codé de l'interface utilisateur

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Copier la référence dans le presse-papiers|**Ctrl + C**| OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard |
|Insérer un délai avant|**CTRL + ALT + D**| OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore |
|Localiser tout|**Maj+Alt+L**| OtherContextMenus.UITestEditorContextMenu.LocateAll |
|Localiser le contrôle d’interface utilisateur|**Ctrl+Maj+L**| OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl |
|Déplacer du code|**Ctrl + Alt + C**| OtherContextMenus.UITestEditorContextMenu.Movecode |
|Fractionner en une nouvelle méthode|**Ctrl + Maj + T**| OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod |

### <a name="dataset-editor"></a>Éditeur DataSet

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Insérer une colonne|**Insérer**| OtherContextMenus.ColumnContext.InsertColumn |
|Colonne|**Ctrl + L**| OtherContextMenus.DbTableContext.Add.Column |

### <a name="difference-viewer"></a>Visionneuse de différences

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Ignorer l’espace blanc de découpage|**Ctrl + \\ , Ctrl + barre d’espace**| Diff.IgnoreTrimWhitespace |
|Vue Inline|**Ctrl + \\ , CTRL + 1**| Diff.InlineView |
|Affichage gauche uniquement|**Ctrl + \\ , Ctrl + 3**| Diff.LeftOnlyView |
|Différence suivante|**F8**| Diff.NextDifference |
|Différence précédente|**Maj + F8**| Diff.PreviousDifference |
|Affichage droit uniquement|**Ctrl + \\ , CTRL + 4**| Diff.RightOnlyView |
|Vue côte à côte|**Ctrl + \\ , CTRL + 2**| Diff.SideBySideView |
|Basculer entre gauche et droite|**Ctrl + \\ , CTRL + TAB**| Diff.SwitchBetweenLeftAndRight |
|Bouton de synchronisation de la vue synchroniser|**Ctrl + \\ , Ctrl + flèche bas**| Diff.SynchronizeViewToggle |
|Ajouter un commentaire|**CTRL+Maj+K**| EditorContextMenus.CodeWindow.AddComment |
|Modifier le fichier local|**Ctrl + Maj + P**| EditorContextMenus.CodeWindow.EditLocalFile |

### <a name="dom-explorer"></a>Explorateur DOM

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Actualiser|**F5**| DOMExplorer.Refresh |
|Sélection d'un élément|**CTRL + B**| DOMExplorer.SelectElement |
|Afficher la disposition|**Ctrl + Maj + I**| DOMExplorer.ShowLayout |

### <a name="f-interactive"></a>F# interactif

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Annuler l’évaluation interactive|**CTRL + ATTN**| OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation |

### <a name="graph-document-editor"></a>Éditeur de document de graphique

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Ajouter un nœud|**Insérer**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode |
|Les deux dépendances|**B**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies |
|Dépendances entrantes|**Cliqu**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies |
|Dépendances sortantes|**Sorties**| ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies |
|Nouveau commentaire|**CTRL+Maj+K**<br /><br /> ou<br /><br /> **Ctrl+E, C**| ArchitectureContextMenus.DirectedGraphContextMenu.NewComment |
|Supprimer|**Supprimer**| ArchitectureContextMenus.DirectedGraphContextMenu.Remove |
|Renommer|**F2**| ArchitectureContextMenus.DirectedGraphContextMenu.Rename |

### <a name="graphics-diagnostics"></a>Graphics Diagnostics

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Capturer le frame|Aucun| Debug.Graphics.CaptureFrame |
|Déplacer la sélection des pixels vers le dessous|**Maj+Alt+Bas**| Graphics.MovePixelSelectionDown |
|Déplacer la sélection de pixels vers la gauche|**Maj + Alt + flèche gauche**| Graphics.MovePixelSelectionLeft |
|Déplacer la sélection des pixels vers la droite|**Maj + Alt + flèche droite**| Graphics.MovePixelSelectionRight |
|Déplacer la sélection des pixels vers le haut|**Maj+Alt+Haut**| Graphics.MovePixelSelectionUp |
|Zoom sur la taille réelle|**Maj+Alt+0** (zéro)| Graphics.ResetZoom |
|Zoom pour ajuster à la fenêtre|**Maj+Alt+9**| Graphics.ZoomToFitInWindow |
|Faire un zoom avant|**Maj + Alt + =**| Graphics.ZoomIn |
|Faire un zoom arrière|**Maj + Alt +-**| Graphics.ZoomOut |

### <a name="html-editor"></a>Éditeur HTML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Accéder au contrôleur|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |

### <a name="html-editor-design-view"></a>Éditeur HTML en mode Design

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Déplacer le contrôle vers le dessous|**Ctrl + flèche bas**| Edit.MoveControlDown |
|Déplacer le contrôle vers le haut|**Ctrl + flèche haut**| Edit.MoveControlUp |
|Gras|**CTRL + B**| Format.Bold |
|Convertir en lien hypertexte|**Ctrl + L**| Format.ConverttoHyperlink |
|Insérer un signet|**Ctrl+Maj+L**| Format.InsertBookmark |
|Italique|**Ctrl+I**| Format.Italic |
|Souligner|**Ctrl+U**| Format.Underline |
|Ajouter une page de contenu|**Ctrl+M, Ctrl+C**| Project.AddContentPage |
|Colonne à gauche|**Ctrl + Alt + flèche gauche**| Table.ColumntotheLeft |
|Colonne à droite|**Ctrl+Alt+Droite**| Table.ColumntotheRight |
|Ligne au-dessus|**Ctrl + Alt + flèche haut**| Table.RowAbove |
|Ligne ci-dessous|**Ctrl + Alt + flèche bas**| Table.RowBelow |
|Contrôles .net invisuels|**Ctrl + Maj + N**| View.ASP.NETNonvisualControls |
|Modifier le maître|**Ctrl + M, Ctrl + M**| View.EditMaster |
|Vue suivante|**Ctrl+PgDn**| View.NextView |
|Afficher la balise active|**Maj + Alt + F10**| View.ShowSmartTag |
|Afficher le balisage|**Maj+F7**| View.ViewMarkup |
|Onglet précédent|**Ctrl+Pg préc**| Window.PreviousTab |

### <a name="html-editor-source-view"></a>Éditeur HTML en mode Source

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Accéder au contrôleur|**Ctrl+M, Ctrl+G**| OtherContextMenus.HTMLContext.GoToController |
|Vue suivante|**Ctrl+PgDn**| View.NextView |
|Synchroniser les vues|**Ctrl+Maj+Y**| View.SynchronizeViews |
|Concepteur de vue|**Maj+F7**| View.ViewDesigner |
|Onglet précédent|**Ctrl+Pg préc**| Window.PreviousTab |

### <a name="layer-diagram"></a>Diagramme de couche

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer|**Maj + Suppr**| Edit.Delete |

### <a name="managed-resources-editor"></a>Éditeur de ressources managées

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Modifier la cellule|**F2**| Edit.EditCell |
|Supprimer|**Supprimer**| Edit.Remove |
|Supprimer la ligne|**Ctrl + Suppr**| Edit.RemoveRow |
|Annuler la sélection|**Caractère d'échappement**| Edit.SelectionCancel |
|Audio|**CTRL + 4**| Resources.Audio |
|Fichiers|**Ctrl + 5**| Resources.Files |
|Icônes|**Ctrl + 3**| Resources.Icons |
|Images|**CTRL + 2**| Resources.Images |
|Autre|**Ctrl + 6**| Resources.Other |
|Chaînes|**CTRL + 1**| Resources.Strings |

### <a name="merge-editor-window"></a>Fenêtre de l’éditeur de fusion

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Définir le focus sur la fenêtre de gauche|**Alt+1**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow |
|Définir le focus sur la fenêtre de résultats|**Alt+2**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow |
|Définir le focus sur la fenêtre de droite|**Alt+3**| TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow |

### <a name="microsoft-sql-server-data-tools-schema-compare"></a>Microsoft SQL Server Data Tools, Comparaison de schémas

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Comparaison de comparaison de schémas SSDT|**Maj+Alt+C**| SQL.SSDTSchemaCompareCompare |
|Script de génération de comparaison de schémas SSDT|**Maj+Alt+G**| SQL.SSDTSchemaCompareGenerateScript |
|SSDT le changement suivant de comparaison de schémas|**Maj + Alt +.**| SQL.SSDTSchemaCompareNextChange |
|Comparaison du changement de schéma SSDT|**Maj + Alt +,**| SQL.SSDTSchemaComparePreviousChange |
|Arrêt de comparaison de schémas SSDT|**Alt + Attn**| SQL.SSDTSchemaCompareStop |
|Mises à jour d’écriture de comparaison de schémas SSDT|**Maj+Alt+U**| SQL.SSDTSchemaCompareWriteUpdates |

### <a name="microsoft-sql-server-data-tools-table-designer"></a>Microsoft SQL Server Data Tools, Concepteur de tables

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|CommitAllEdits|**Maj+Alt+U**|
|Développer les caractères génériques|**Ctrl+R, E**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Noms qualifiés complets|**Ctrl+R, Q**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Déplacer vers le schéma|**Ctrl+R, M**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Renommer|**F2**<br /><br /> ou<br /><br /> **Ctrl+R, R**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|ViewFileInScriptPanel|**Maj+Alt+Pg suiv**| |

### <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Microsoft SQL Server Data Tools, Éditeur T-SQL

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|CommitAllEdits|**Maj+Alt+U**|
|Exécuter avec le débogueur|**Alt + F5**| SQL.ExecuteWithDebugger |
|Développer les caractères génériques|**Ctrl+R, E**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+E**| SQL.ExpandWildcards |
|Noms qualifiés complets|**Ctrl+R, Q**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+Q**| SQL.FullyqualifyNames |
|Déplacer vers le schéma|**Ctrl+R, M**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+M**| SQL.MovetoSchema |
|Renommer|**F2**<br /><br /> ou<br /><br /> **Ctrl+R, R**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+R**| SQL.Rename |
|annuler la requête de l’éditeur de SQL|**Alt + Attn**| SQL.TSqlEditorCancelQuery |
|exécuter la requête de l’éditeur de SQL|**CTRL + MAJ + E**| SQL.TSqlEditorExecuteQuery |
|résultats de l’éditeur T SQL sous forme de fichier|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|résultats de l’éditeur T SQL sous forme de grille|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|résultats de l’éditeur T SQL sous forme de texte|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL éditeur afficher le plan estimé|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|basculer le plan d’exécution de l’éditeur T SQL|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|basculer le volet de résultats dans l’éditeur de SQL T|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|requête clone de l’éditeur T SQL|**Ctrl + Alt + N**|SQL. TSqlEditorCloneQuery |
|liste de bases de données d’éditeur T SQL|**Maj+Alt+Pg suiv**|SQL. TSqlEditorDatabaseCombo |

### <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Microsoft SQL Server Data Tools, Éditeur T-SQL PDW

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|annuler la requête de l’éditeur de SQL|**Alt + Attn**| SQL.TSqlEditorCancelQuery |
|exécuter la requête de l’éditeur de SQL|**CTRL + MAJ + E**| SQL.TSqlEditorExecuteQuery |
|résultats de l’éditeur T SQL sous forme de fichier|**Ctrl+D, F**| SQL.TSqlEditorResultsAsFile |
|résultats de l’éditeur T SQL sous forme de grille|**Ctrl+D, G**| SQL.TSqlEditorResultsAsGrid |
|résultats de l’éditeur T SQL sous forme de texte|**Ctrl+D, T**| SQL.TSqlEditorResultsAsText |
|T SQL éditeur afficher le plan estimé|**Ctrl+D, E**| SQL.TSqlEditorShowEstimatedPlan |
|basculer le plan d’exécution de l’éditeur T SQL|**Ctrl+D, A**| SQL.TSqlEditorToggleExecutionPlan |
|basculer le volet de résultats dans l’éditeur de SQL T|**Ctrl+D, R**| SQL.TSqlEditorToggleResultsPane |
|requête clone de l’éditeur T SQL|**Ctrl + Alt + N**|SQL. TSqlEditorCloneQuery |
|requête clone de l’éditeur T SQL|**Maj+Alt+Pg suiv**|SQL. TSqlEditorCloneQuery |

### <a name="page-inspector"></a>Inspecteur de page

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Réduire|**F12**| PageInspector.Minimize |

### <a name="query-designer"></a>Concepteur de requêtes

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Annuler la récupération des données|**Ctrl + T**| QueryDesigner.CancelRetrievingData |
|Critères|**CTRL + 2**| QueryDesigner.Criteria |
|Diagramme|**CTRL + 1**| QueryDesigner.Diagram |
|Exécuter SQL|**Ctrl + R**| QueryDesigner.ExecuteSQL |
|Aller à la ligne|**CTRL + G**| QueryDesigner.GotoRow |
|Mode de jointure|**Ctrl + Maj + J**| QueryDesigner.JoinMode |
|Résultats|**CTRL + 4**| QueryDesigner.Results |
|SQL|**Ctrl + 3**| QueryDesigner.SQL |

### <a name="query-results"></a>Résultats de la requête

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Nouvelle ligne des résultats de la requête|**Alt+Fin**| SQL.QueryResultsNewRow |
|Actualisation des résultats de la requête|**Maj+Alt+R**| SQL.QueryResultsRefresh |
|Arrêt des résultats de la requête|**Alt + Attn**| SQL.QueryResultsStop |

### <a name="report-designer"></a>Concepteur de rapports

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Saut de ligne|**Entrée**| Edit.BreakLine |
|Caractère vers la gauche|**Flèche gauche**| Edit.CharLeft |
|Étendre le caractère vers la gauche|**Maj + Flèche gauche**| Edit.CharLeftExtend |
|Caractère à droite|**Flèche droite**| Edit.CharRight |
|Étendre le caractère à droite|**Maj + Flèche droite**| Edit.CharRightExtend |
|Onglet Insérer|**Tab**| Edit.InsertTab |
|Ligne suivante|**Flèche bas**| Edit.LineDown |
|Étendre la ligne vers le dessous|**Maj + Flèche bas**| Edit.LineDownExtend |
|Ligne précédente|**Flèche haut**| Edit.LineUp |
|Étendre la ligne vers le haut|**Maj + haut**| Edit.LineUpExtend |
|Déplacer le contrôle vers le dessous|**Ctrl + flèche bas**| Edit.MoveControlDown |
|Déplacer le contrôle vers la gauche|**Ctrl + flèche gauche**| Edit.MoveControlLeft |
|Déplacer le contrôle vers la droite|**Ctrl + flèche droite**| Edit.MoveControlRight |
|Déplacer le contrôle vers le haut|**Ctrl + flèche haut**| Edit.MoveControlUp |
|Annuler la sélection|**Échap**| Edit.SelectionCancel |
|Contrôle de la taille en dessous|**Ctrl+Maj+Bas**| Edit.SizeControlDown |
|Contrôle de la taille à gauche|**Ctrl+Maj+Gauche**| Edit.SizeControlLeft |
|Redimensionner le contrôle vers la droite|**Ctrl + Maj + droite**| Edit.SizeControlRight |
|Contrôle de la taille|**Ctrl + Maj + haut**| Edit.SizeControlUp |
|Tabulation gauche|**Maj + Tab**| Edit.TabLeft |
|données de rapport|**CTRL + ALT + D**| View.ReportData |

### <a name="sequence-diagram"></a>Diagramme de séquence

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Accéder au code|**F12**| ArchitectureDesigner.Sequence.NavigateToCode |
|Supprimer|**Maj+Suppr**| Edit.Delete |

### <a name="settings-designer"></a>Concepteur de paramètres

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Modifier la cellule|**F2**| Edit.EditCell |
|Supprimer la ligne|**Ctrl + Suppr**| Edit.RemoveRow |
|Annuler la sélection|**Échap**| Edit.SelectionCancel |
|Afficher le code|**F7**| View.ViewCode |

### <a name="solution-explorer"></a>Explorateur de solutions

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Afficher dans l’inspecteur de page|**Ctrl+K, Ctrl+G**| ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector |

### <a name="team-explorer"></a>Team Explorer

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer|**Supprimer**| Edit.Delete |
|Renommer|**F2**| File.Rename |
|Accéder à la navigation dans Team Explorer|**Alt + début**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation |
|Accéder au contenu de la section suivante Team Explorer|**Alt + flèche bas**| TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent |
|Accéder au contenu de la page Team Explorer|**Alt+0** (zéro)| TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent |
|Accéder au contenu de la section précédente Team Explorer|**Alt + Flèche haut**| TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent |
|Accéder au contenu de la section 1 Team Explorer|**Alt+1**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content |
|Accéder au contenu de la section 2 Team Explorer|**Alt+2**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content |
|Accéder au contenu de la section 3 Team Explorer|**Alt+3**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content |
|Accéder au contenu de la section 4 Team Explorer|**Alt+4**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content |
|Accéder au contenu de la section 5 Team Explorer|**Alt+5**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content |
|Accéder au contenu de la section 6 Team Explorer|**Alt+6**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content |
|Atteindre le contenu de la section 7 Team Explorer|**Alt+7**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content |
|Atteindre le contenu de la section 8 Team Explorer|**Alt+8**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content |
|Accéder au contenu de la section 9 Team Explorer|**Alt+9**| TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content |
|Naviguer vers l’arrière dans Team Explorer|**Alt + Flèche gauche**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward |
|Naviguer vers l’avant dans Team Explorer|**Alt + Flèche droite**| TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward |
|Page mon travail contexte TFS créer un réseau de copie|**Maj+Alt+C**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI |
|Contexte TFS, page mon travail, nouveau Wi lié|**Maj+Alt+L**| TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI |
|Actualiser|**F5**| View.Refresh |

### <a name="test-explorer"></a>Explorateur de tests

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Ouvrir le test|**F12**| TestExplorer.OpenTest |

### <a name="text-editor"></a>Éditeur de texte

Les raccourcis spécifiques à ce contexte sont les suivants :


| Commandes | Raccourcis clavier |ID de commande|
|-|-|-|
|Saut de ligne| **Entrée**<br /><br /> ou<br /><br /> **Maj + Entrée** | Edit.BreakLine |
|Caractère vers la gauche| **Flèche gauche** | Edit.CharLeft |
|Étendre le caractère vers la gauche| **Maj + Flèche gauche** | Edit.CharLeftExtend |
|Étendre la colonne vers la gauche des caractères| **Maj + Alt + flèche gauche** | Edit.CharLeftExtendColumn |
|Caractère à droite| **Flèche droite** | Edit.CharRight |
|Étendre le caractère à droite| **Maj + Flèche droite** | Edit.CharRightExtend |
|Étendre la colonne à droite du caractère| **Maj + Alt + flèche droite** | Edit.CharRightExtendColumn |
|Effacer les signets| **Ctrl + K, Ctrl + L** | Edit.ClearBookmarks |
|Réduire tout le mode plan| **Ctrl + M, Ctrl + A** | Edit.CollapseAllOutlining |
|Réduire la zone active| **Ctrl + M, CTRL + S** | Edit.CollapseCurrentRegion |
|Réduire la balise| **Ctrl+M, Ctrl+T** | Edit.CollapseTag |
|Réduire aux définitions| **Ctrl+M, Ctrl+O** (lettre « O ») | Edit.CollapseToDefinitions |
|Diminuer la sélection| **Maj + Alt +-** | Edit.ContractSelection |
|Sélection de commentaire| **Ctrl + K, Ctrl + C** | Edit.CommentSelection |
|Compléter le mot| **Ctrl + Espace**<br /><br /> ou<br /><br /> **Alt + Flèche droite** | Edit.CompleteWord |
|Copier le paramètre conseillé| **Ctrl + Maj + Alt + C** | Edit.CopyParameterTip |
|Réduire le niveau de filtre| **Alt +,** | Edit.DecreaseFilterLevel |
|Supprimer vers l’arrière| **Retour arrière**<br /><br /> ou<br /><br /> **Maj+Retour arrière** | Edit.DeleteBackwards |
|Supprimer l’espace blanc horizontal| **Ctrl + K, Ctrl +\\** | Edit.DeleteHorizontalWhiteSpace |
|Fin du document| **Ctrl+Fin** | Edit.DocumentEnd |
|Étendre à la fin du document| **Ctrl + Maj + fin** | Edit.DocumentEndExtend |
|Début du document| **Ctrl+Origine** | Edit.DocumentStart |
|Extension de début de document| **Ctrl + Maj + début** | Edit.DocumentStartExtend |
|Développer tout en mode plan| **Ctrl + M, CTRL + X** | Edit.ExpandAllOutlining |
|Développer la région actuelle| **Ctrl + M, Ctrl + E** | Edit.ExpandCurrentRegion |
|Développer la sélection| **Maj + Alt + =** | Edit.ExpandSelection |
|Étendre la sélection au bloc conteneur| **Maj + Alt +]** | Edit.ExpandSelectiontoContainingBlock |
|Mettre en forme le document| **Ctrl + K, Ctrl + D** | Edit.FormatDocument |
|Sélection du format| **Ctrl + K, Ctrl + F** | Edit.FormatSelection |
|Atteindre tout| **Ctrl + T**<br /><br /> ou<br /><br /> **CTRL +,** | Edit.GotoAll |
|Accolade Goto| **Ctrl +]** | Edit.GotoBrace |
|Etendre l’accolade Goto| **Ctrl + Maj +]** | Edit.GotoBraceExtend |
|Goto récent| **Ctrl+T,R** | Edit.GotoRecent |
|Aller au problème suivant dans le fichier| **Alt+PgDn** | Edit.GotoNextIssueinFile |
|Atteindre le problème précédent dans le fichier| **Alt+Pg préc** | Edit.GotoPreviousIssueinFile |
|Masquer la sélection| **Ctrl + M, Ctrl + H** | Edit.HideSelection |
|Augmenter le niveau de filtre| **Alt +.** | Edit.IncreaseFilterLevel |
|Recherche incrémentielle| **Ctrl+I** | Edit.IncrementalSearch |
|Insérer des signes d’insertion à la correspondance| **Maj + Alt +;** | Edit.InsertCaretsatAllMatching |
|Insérer le signe insertion correspondant suivant| **Maj + Alt +.** | Edit.InsertNextMatchingCaret |
|Onglet Insérer| **Tab** | Edit.InsertTab |
|Couper la ligne| **Ctrl + L** | Edit.LineCut |
|Suppression de ligne| **Ctrl+Maj+L** | Edit.LineDelete |
|Ligne suivante| **Flèche bas** | Edit.LineDown |
|Étendre la ligne vers le dessous| **Maj + Flèche bas** | Edit.LineDownExtend |
|Étendre la colonne d’une ligne vers le PG.| **Maj+Alt+Bas** | Edit.LineDownExtendColumn |
|Fin de ligne| **Effet** | Edit.LineEnd |
|Étendre à la fin de la ligne| **Maj + fin** | Edit.LineEndExtend |
|Étendre la colonne de fin de ligne| **Maj + Alt + fin** | Edit.LineEndExtendColumn |
|Ligne ouverte au-dessus| **CTRL+ Enter** | Edit.LineOpenAbove |
|Ligne ouverte en dessous| **Ctrl+Shift+Enter** | Edit.LineOpenBelow |
|Début de ligne| **Page d'accueil** | Edit.LineStart |
|Étendre au début de la ligne| **Maj + début** | Edit.LineStartExtend |
|Étendre la colonne de début de ligne| **Maj + Alt + début** | Edit.LineStartExtendColumn |
|Transposer la ligne| **Maj + Alt + T** | Edit.LineTranspose |
|Ligne précédente| **Flèche haut** | Edit.LineUp |
|Étendre la ligne vers le haut| **Maj + haut** | Edit.LineUpExtend |
|Étendre la colonne de ligne vers le haut| **Maj+Alt+Haut** | Edit.LineUpExtendColumn |
|Répertorier les membres| **Ctrl + J** | Edit.ListMembers |
|Mettre en minuscules| **Ctrl+U** | Edit.MakeLowercase |
|Mettre en majuscules| **CTRL + MAJ + U** | Edit.MakeUppercase |
|Déplacer les lignes sélectionnées vers le dessous| **Alt + flèche bas** | Edit.MoveSelectedLinesDown |
|Déplacer les lignes sélectionnées vers le haut| **Alt + Flèche haut** | Edit.MoveSelectedLinesUp |
|Référence en surbrillance suivante| **Ctrl+Maj+Bas** | Edit.NextHighlightedReference |
|Mode Refrappe| **Insérer** | Edit.OvertypeMode |
|Page suivante| **Pg suiv** | Edit.PageDown |
|Étendre la page vers le PG.| **Maj+PgDn** | Edit.PageDownExtend |
|Page précédente| **Pg préc** | Edit.PageUp |
|Étendre la page vers le haut| **Maj+Pg préc** | Edit.PageUpExtend |
|Informations sur les paramètres| **Ctrl+Maj+Barre d'espace** | Edit.ParameterInfo |
|Coller le paramètre conseillé| **Ctrl + Maj + Alt + P** | Edit.PasteParameterTip |
|Aperçu arrière| **Ctrl + Alt +-** | Edit.PeekBackward |
|Aperçu de définition| **Alt + F12** | Edit.PeekDefinition |
|Aperçu avant| **Ctrl + Alt + =** | Edit.PeekForward |
|Référence en surbrillance précédente| **Ctrl + Maj + haut** | Edit.PreviousHighlightedReference |
|Info express| **Ctrl + K, Ctrl + I** | Edit.QuickInfo |
|Inverser la recherche incrémentielle| **Ctrl + Maj + I** | Edit.ReverseIncrementalSearch |
|Faire défiler la ligne vers le dessous| **Ctrl + flèche bas** | Edit.ScrollLineDown |
|Faire défiler la ligne vers le haut| **Ctrl + flèche haut** | Edit.ScrollLineUp |
|Sélectionner le mot actuel| **CTRL + W** | Edit.SelectCurrentWord |
|Annuler la sélection| **Caractère d'échappement** | Edit.SelectionCancel |
|Sélectionner jusqu’au dernier retour| **Ctrl + =** | Edit.SelectToLastGoBack |
|Afficher le menu de la lentille du code| **Ctrl + K, Ctrl +\`** | Edit.ShowCodeLensMenu |
|Afficher le menu naviguer| **Alt +\`** | Edit.ShowNavigateMenu |
|Arrêter le masquage actuel| **Ctrl + M, Ctrl + U** | Edit.StopHidingCurrent |
|Arrêter le mode plan| **Ctrl + M, Ctrl + P** | Edit.StopOutlining |
|Permuter l’ancre| **Ctrl + K, Ctrl + A** | Edit.SwapAnchor |
|Tabulation gauche| **Maj + Tab** | Edit.TabLeft |
|Activer/désactiver tout le mode plan| **Ctrl + M, Ctrl + L** | Edit.ToggleAllOutlining |
|Activer/Désactiver le signet| **Ctrl + K, CTRL + K** | Edit.ToggleBookmark |
|Activer/désactiver le mode de saisie semi-automatique| **Ctrl+Alt+Espace** | Edit.ToggleCompletionMode |
|Activer/désactiver le développement du mode plan| **Ctrl + M, Ctrl + M** | Edit.ToggleOutliningExpansion |
|Activer/désactiver le raccourci vers la liste des tâches| **Ctrl + K, Ctrl + H** | Edit.ToggleTaskListShortcut |
|Activer/désactiver le retour automatique à la ligne| **Ctrl+E, Ctrl+W** | Edit.ToggleWordWrap |
|Supprimer les marques de commentaire de la sélection| **Ctrl + K, Ctrl + U** | Edit.UncommentSelection |
|Afficher le bas| **Ctrl+PgDn** | Edit.ViewBottom |
|Afficher l’extension inférieure| **Ctrl+Maj+PgDn** | Edit.ViewBottomExtend |
|Afficher le haut| **Ctrl+Pg préc** | Edit.ViewTop |
|Afficher l’extension supérieure| **Ctrl+Maj+Pg préc** | Edit.ViewTopExtend |
|Afficher les espaces blancs| **Ctrl + R, CTRL + W** | Edit.ViewWhiteSpace |
|Suppression de mot à la fin| **Ctrl + Suppr** | Edit.WordDeleteToEnd |
|Suppression des mots jusqu’au début| **Ctrl + Retour arrière** | Edit.WordDeleteToStart |
|Mot suivant| **Ctrl + flèche droite** | Edit.WordNext |
|Étendre le mot suivant| **Ctrl + Maj + droite** | Edit.WordNextExtend |
|Étendre la colonne par le mot suivant| **Ctrl+Maj+Alt+Droite** | Edit.WordNextExtendColumn |
|Mot précédent| **Ctrl + flèche gauche** | Edit.WordPrevious |
|Étendre le mot précédent| **Ctrl+Maj+Gauche** | Edit.WordPreviousExtend |
|Étendre la colonne jusqu’au mot précédent| **Ctrl+Maj+Alt+Gauche** | Edit.WordPreviousExtendColumn |
|Transposer un mot| **Ctrl + Maj + T** | Edit.WordTranspose |
|Exécuter en mode interactif| **Alt + Entrée** | EditorContextMenus.CodeWindow.ExecuteInInteractive |
|Exécuter la ligne en mode interactif| **Alt + '** | EditorContextMenus.CodeWindow.ExecuteLineInInteractive |
|Afficher dans l’inspecteur de page| **Ctrl+K, Ctrl+G** | OtherContextMenus.HTMLContext.ViewinPageInspector |
|Annotation TFS-déplacer la région suivante| **Alt+PgDn** | TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion |
|Annotation TFS-déplacer la région précédente| **Alt+Pg préc** | TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion |

### <a name="uml-activity-diagram"></a>Diagramme d'activités UML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer|**Maj+Suppr**| Edit.Delete |

### <a name="uml-class-diagram"></a>Diagramme de classes UML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer du modèle|**Maj+Suppr**| Edit.DeleteFromModel |

### <a name="uml-component-diagram"></a>Diagramme de composant UML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer du modèle|**Maj+Suppr**| Edit.DeleteFromModel |

### <a name="uml-use-case-diagram"></a>Diagramme de cas d'usage UML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Supprimer du modèle|**Maj+Suppr**| Edit.DeleteFromModel |

### <a name="vc-accelerator-editor"></a>Éditeur d'accélérateurs VC

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Nouvel accélérateur|**Insérer**| Edit.NewAccelerator |
|Clé suivante typée|**CTRL + W**| Edit.NextKeyTyped |

### <a name="vc-dialog-editor"></a>Éditeur de boîtes de dialogue VC

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Déplacer le contrôle vers le dessous|**Flèche bas**| Edit.MoveControlDown |
|Déplacer le contrôle vers la gauche|**Flèche gauche**| Edit.MoveControlLeft |
|Déplacer le contrôle vers la droite|**Flèche droite**| Edit.MoveControlRight |
|Déplacer le contrôle vers le haut|**Flèche haut**| Edit.MoveControlUp |
|Faire défiler la colonne vers la gauche|**Ctrl + flèche gauche**| Edit.ScrollColumnLeft |
|Déplacer la colonne vers la droite|**Ctrl + flèche droite**| Edit.ScrollColumnRight |
|Faire défiler la ligne vers le dessous|**Ctrl + flèche bas**| Edit.ScrollLineDown |
|Faire défiler la ligne vers le haut|**Ctrl + flèche haut**| Edit.ScrollLineUp |
|Contrôle de la taille en dessous|**Maj + Flèche bas**| Edit.SizeControlDown |
|Contrôle de la taille à gauche|**Maj + Flèche gauche**| Edit.SizeControlLeft |
|Redimensionner le contrôle vers la droite|**Maj + Flèche droite**| Edit.SizeControlRight |
|Contrôle de la taille|**Maj + haut**| Edit.SizeControlUp |
|Aligner les bases|**Ctrl+Maj+Bas**| Format.AlignBottoms |
|Aligner les centres|**Maj + F9**| Format.AlignCenters |
|Aligner les gauches|**Ctrl+Maj+Gauche**| Format.AlignLefts |
|Aligner les milieux|**F9**| Format.AlignMiddles |
|Aligner les droits|**Ctrl + Maj + droite**| Format.AlignRights |
|Aligner les sommets|**Ctrl + Maj + haut**| Format.AlignTops |
|Bouton en bas|**CTRL + B**| Format.ButtonBottom |
|Bouton droit|**Ctrl + R**| Format.ButtonRight |
|Centrer horizontalement|**CTRL + MAJ + F9**| Format.CenterHorizontal |
|Centrer verticalement|**Ctrl + F9**| Format.CenterVertical |
|Vérifie les mnémoniques|**Ctrl+M**| Format.CheckMnemonics |
|Taille du contenu|**Maj+F7**| Format.SizetoContent |
|Espacer horizontalement|**Alt + Flèche droite**<br /><br /> ou<br /><br /> **Alt + Flèche gauche**| Format.SpaceAcross |
|Espacer vers le dessous|**Alt + Flèche haut**<br /><br /> ou<br /><br /> **Alt + flèche bas**| Format.SpaceDown |
|Ordre de tabulation|**Ctrl+D**| Format.TabOrder |
|Tester la boîte de dialogue|**Ctrl + T**| Format.TestDialog |
|Activer/désactiver les repères|**CTRL + G**| Format.ToggleGuides |

### <a name="vc-image-editor"></a>Éditeur d'images VC

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Outil Aérographe|**Ctrl+A**| Image.AirbrushTool |
|Outil Pinceau|**CTRL + B**| Image.BrushTool |
|Copier et détourer la sélection|**CTRL + MAJ + U**| Image.CopyandOutlineSelection |
|Dessin opaque|**Ctrl + J**| Image.DrawOpaque |
|Outil Ellipse|**Alt + P**| Image.EllipseTool |
|Outil d’effacement|**Ctrl + Maj + I**| Image.EraseTool |
|Outil Ellipse remplie|**Ctrl + Maj + Alt + P**| Image.FilledEllipseTool |
|Outil Rectangle rempli|**Ctrl + Maj + Alt + R**| Image.FilledRectangleTool |
|Outil Rectangle arrondi rempli|**Ctrl+Maj+Alt+W**| Image.FilledRoundedRectangleTool |
|Outil Remplir avec une couleur|**Ctrl + F**| Image.FillTool |
|Retourner horizontalement|**Ctrl + H**| Image.FlipHorizontal |
|Retourner verticalement|**Maj+Alt+H**| Image.FlipVertical |
|Pinceau plus grand|**Ctrl + =**| Image.LargerBrush |
|Outil ligne|**Ctrl + L**| Image.LineTool |
|Outil d’agrandissement|**Ctrl+M**| Image.MagnificationTool |
|Grossi|**Ctrl + Maj + M**| Image.Magnify |
|Nouveau type d’image|**Insérer**| Image.NewImageType |
|Couleur suivante|**Ctrl +]**<br /><br /> ou<br /><br /> **Ctrl + flèche droite**| Image.NextColor |
|Couleur droite suivante|**Ctrl + Maj +]**<br /><br /> ou<br /><br /> **Ctrl + Maj + droite**| Image.NextRightColor |
|Outil ellipse avec contour|**Maj+Alt+P**| Image.OutlinedEllipseTool |
|Outil Rectangle avec contour|**Maj+Alt+R**| Image.OutlinedRectangleTool |
|Outil Rectangle arrondi avec contour|**Maj+Alt+W**| Image.OutlinedRoundedRectangleTool |
|Outil crayon|**Ctrl+I**| Image.PencilTool |
|Couleur précédente|**Ctrl + [**<br /><br /> ou<br /><br /> **Ctrl + flèche gauche**| Image.PreviousColor |
|Couleur droite précédente|**Ctrl + Maj + [**<br /><br /> ou<br /><br /> **Ctrl+Maj+Gauche**| Image.PreviousRightColor |
|Outil Sélection d’un rectangle|**Maj+Alt+S**| Image.RectangleSelectionTool |
|Outil Rectangle|**Alt + R**| Image.RectangleTool |
|Faire pivoter de 90 degrés|**Ctrl + Maj + H**| Image.Rotate90Degrees |
|Outil Rectangle arrondi|**Alt + W**| Image.RoundedRectangleTool |
|Afficher la grille|**Ctrl + Alt + S**| Image.ShowGrid |
|Afficher la grille de mosaïques|**Ctrl+Maj+Alt+S**| Image.ShowTileGrid |
|Petit pinceau|**Ctrl +.**| Image.SmallBrush |
|Pinceau plus petit|**Ctrl +-**| Image.SmallerBrush |
|Outil texte|**Ctrl + T**| Image.TextTool |
|Utiliser la sélection comme pinceau|**Ctrl+U**| Image.UseSelectionasBrush |
|Faire un zoom avant|**Ctrl + Maj +.**<br /><br /> ou<br /><br /> **Ctrl + flèche haut**| Image.ZoomIn |
|Faire un zoom arrière|**Ctrl + Maj +,**<br /><br /> ou<br /><br /> **Ctrl + flèche bas**| Image.ZoomOut |

### <a name="vc-string-editor"></a>Éditeur de chaînes VC

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Nouvelle chaîne|**Insérer**| Edit.NewString |

### <a name="view-designer"></a>Concepteur de vue

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Annuler la récupération des données|**Ctrl + T**| QueryDesigner.CancelRetrievingData |
|Critères|**CTRL + 2**| QueryDesigner.Criteria |
|Diagramme|**CTRL + 1**| QueryDesigner.Diagram |
|Exécuter SQL|**Ctrl + R**| QueryDesigner.ExecuteSQL |
|Aller à la ligne|**CTRL + G**| QueryDesigner.GotoRow |
|Mode de jointure|**Ctrl + Maj + J**| QueryDesigner.JoinMode |
|Résultats|**CTRL + 4**| QueryDesigner.Results |
|SQL|**Ctrl + 3**| QueryDesigner.SQL |

### <a name="visual-studio"></a>Visual Studio

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commande|Raccourci clavier|ID de commande|
|-|-|-|
|Masquer le volet méthodes|**CTRL + 1**| OtherContextMenus.ORDesignerContext.HideMethodsPane |

### <a name="windows-forms-designer"></a>Concepteur Windows Forms

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Saut de ligne|**Entrée**| Edit.BreakLine |
|Caractère vers la gauche|**Flèche gauche**| Edit.CharLeft |
|Étendre le caractère vers la gauche|**Maj + Flèche gauche**| Edit.CharLeftExtend |
|Caractère à droite|**Flèche droite**| Edit.CharRight |
|Étendre le caractère à droite|**Maj + Flèche droite**| Edit.CharRightExtend |
|Fin du document|**Effet**| Edit.DocumentEnd |
|Étendre à la fin du document|**Maj + fin**| Edit.DocumentEndExtend |
|Début du document|**Page d'accueil**| Edit.DocumentStart |
|Extension de début de document|**Maj + début**| Edit.DocumentStartExtend |
|Onglet Insérer|**Tab**| Edit.InsertTab |
|Ligne suivante|**Flèche bas**| Edit.LineDown |
|Étendre la ligne vers le dessous|**Maj + haut**| Edit.LineDownExtend |
|Ligne précédente|**Flèche haut**| Edit.LineUp |
|Étendre la ligne vers le haut|**Maj + Flèche bas**| Edit.LineUpExtend |
|Déplacer le contrôle vers le dessous|**Ctrl + flèche bas**| Edit.MoveControlDown |
|Déplacer le contrôle vers la gauche|**Ctrl + flèche gauche**| Edit.MoveControlLeft |
|Déplacer le contrôle vers la droite|**Ctrl + flèche droite**| Edit.MoveControlRight |
|Déplacer le contrôle vers le haut|**Ctrl + flèche haut**| Edit.MoveControlUp |
|Annuler la sélection|**Caractère d'échappement**| Edit.SelectionCancel |
|Contrôle de la taille en dessous|**Ctrl+Maj+Bas**| Edit.SizeControlDown |
|Contrôle de la taille à gauche|**Ctrl+Maj+Gauche**| Edit.SizeControlLeft |
|Redimensionner le contrôle vers la droite|**Ctrl + Maj + droite**| Edit.SizeControlRight |
|Contrôle de la taille|**Ctrl + Maj + haut**| Edit.SizeControlUp |
|Tabulation gauche|**Maj + Tab**| Edit.TabLeft |

### <a name="work-item-editor"></a>Éditeur d'élément de travail

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Créer une copie de l’élément de travail|**Maj+Alt+C**| Edit.CreateCopyofWorkItem |
|Actualiser l’élément de travail|**F5**| Edit.RefreshWorkItem |
|Nouvel élément de travail lié|**Maj+Alt+L**| Team.NewLinkedWorkItem |

### <a name="work-item-query-view"></a>Affichage des requêtes d'élément de travail

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Créer une copie de l’élément de travail|**Maj+Alt+C**| Edit.CreateCopyofWorkItem |
|Retrait|**Maj + Alt + flèche droite**| Edit.Indent |
|Retrait négatif|**Maj + Alt + flèche gauche**| Edit.Outdent |
|Nouvel élément de travail lié|**Maj+Alt+L**| Team.NewLinkedWorkItem |
|Actualiser|**F5**| Team.Refresh |
|Bascule|**Maj+Alt+V**| Window.Toggle |

### <a name="work-item-results-view"></a>Affichage des résultats des éléments de travail

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Créer une copie de l’élément de travail|**Maj+Alt+C**| Edit.CreateCopyofWorkItem |
|Retrait|**Maj + Alt + flèche droite**| Edit.Indent |
|Retrait négatif|**Maj + Alt + flèche gauche**| Edit.Outdent |
|Atteindre l’élément de travail suivant|**Maj+Alt+N**| Team.GotoNextWorkItem |
|Aller à l’élément de travail précédent|**Maj+Alt+P**| Team.GotoPreviousWorkItem |
|Nouvel élément de travail lié|**Maj+Alt+L**| Team.NewLinkedWorkItem |
|Actualiser|**F5**| Team.Refresh |
|Bascule|**Maj+Alt+V**| Window.Toggle |

### <a name="workflow-designer"></a>Concepteur de flux de travail

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Compléter le mot|**Ctrl+K, W**<br /><br /> ou<br /><br /> **Ctrl + K, CTRL + W**<br /><br /> ou<br /><br /> **Ctrl + barre d’espace**<br /><br /> ou<br /><br /> **Alt + Flèche droite**| Edit.CompleteWord |
|Réduire le niveau de filtre|**Alt +,**| Edit.DecreaseFilterLevel |
|Augmenter le niveau de filtre|**Alt +.**| Edit.IncreaseFilterLevel |
|Répertorier les membres|**Ctrl+K, L**<br /><br /> ou<br /><br /> **Ctrl + K, Ctrl + L**<br /><br /> ou<br /><br /> **Ctrl + J**| Edit.ListMembers |
|Informations sur les paramètres|**Ctrl+K, P**<br /><br /> ou<br /><br /> **Ctrl + K, Ctrl + P**<br /><br /> ou<br /><br /> **Ctrl+Maj+Barre d'espace**| Edit.ParameterInfo |
|Info express|**Ctrl+K, I**<br /><br /> ou<br /><br /> **Ctrl + K, Ctrl + I**| Edit.QuickInfo |
|Réduire|**Ctrl+E, Ctrl+C**<br /><br /> ou<br /><br /> **Ctrl+E, C**| WorkflowDesigner.Collapse |
|Réduire tout|ou| WorkflowDesigner.CollapseAll |
|nœuds de Connecter|**Ctrl+E, Ctrl+F**<br /><br /> ou<br /><br /> **Ctrl+E, F**| WorkflowDesigner.ConnectNodes |
|Créer une variable|**Ctrl+E, Ctrl+N**<br /><br /> ou<br /><br /> **Ctrl+E, N**| WorkflowDesigner.CreateVariable |
|Tout développer|**Ctrl+E, Ctrl+X**<br /><br /> ou<br /><br /> **Ctrl+E, X**| WorkflowDesigner.ExpandAll |
|Développer sur place|**Ctrl+E, Ctrl+E**<br /><br /> ou<br /><br /> **Ctrl+E, E**| WorkflowDesigner.ExpandInPlace |
|Atteindre le parent|**Ctrl+E, Ctrl+P**<br /><br /> ou<br /><br /> **Ctrl+E, P**| WorkflowDesigner.GoToParent |
|Déplacer le focus|**Ctrl+E, Ctrl+M**<br /><br /> ou<br /><br /> **Ctrl + E, M**| WorkflowDesigner.MoveFocus |
|Naviguer dans le concepteur|**CTRL + ALT + F6**| WorkflowDesigner.NavigateThroughDesigner |
|Restaurer|**Ctrl+E, Ctrl+R**<br /><br /> ou<br /><br /> **Ctrl+E, R**| WorkflowDesigner.Restore |
|Afficher le concepteur d’arguments de masquage|**Ctrl+E, Ctrl+A**<br /><br /> ou<br /><br /> **Ctrl+E, A**| WorkflowDesigner.ShowHideArgumentDesigner |
|Afficher le concepteur d’importations masqué|**Ctrl+E, Ctrl+I**<br /><br /> ou<br /><br /> **Ctrl+E, I**| WorkflowDesigner.ShowHideImportsDesigner |
|Afficher le plan vue d’ensemble masquer|**Ctrl+E, Ctrl+O** (lettre « O »)<br /><br /> ou<br /><br /> **Ctrl+E, O**| WorkflowDesigner.ShowHideOverviewMap |
|Afficher le concepteur de variables masqué|**Ctrl+E, Ctrl+V**<br /><br /> ou<br /><br /> **Ctrl+E, V**| WorkflowDesigner.ShowHideVariableDesigner |
|Activer/désactiver la sélection|**Ctrl+E, Ctrl+S**<br /><br /> ou<br /><br /> **Ctrl+E, S**| WorkflowDesigner.ToggleSelection |
|Faire un zoom avant|**Ctrl+Num +**| WorkflowDesigner.ZoomIn |
|Faire un zoom arrière|**Ctrl + num-**| WorkflowDesigner.ZoomOut |

### <a name="xaml-ui-designer"></a>Concepteur XAML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Ajuster tout|**Ctrl + 0** (zéro)| Design.FitAll |
|Afficher les descripteurs|**F9**| Design.ShowHandles |
|Faire un zoom avant|**Ctrl + Alt + =**| Design.ZoomIn |
|Faire un zoom arrière|**Ctrl + Alt +-**| Design.ZoomOut |
|Options du concepteur|**Ctrl + Maj +;**|
|Modifier le texte|**F2**| Format.EditText |
|Tous|**Ctrl + Maj + R**| Format.ResetLayout.All |
|Exécuter le code de projet|**Ctrl + F9**|
|Masquer (fusion uniquement)|**Ctrl + H**| Timeline.Hide (Blend uniquement) |
|Verrou (fusion uniquement)|**Ctrl + L**| Timeline.Lock (Blend uniquement) |
|Afficher (fusion uniquement)|**Ctrl + Maj + H**| Timeline.Show (Blend uniquement) |
|Déverrouiller (fusion uniquement)|**Ctrl+Maj+L**| Timeline.Unlock (Blend uniquement) |
|Bord gauche déplacer vers la gauche|**Ctrl + Maj +,**| View.EdgeLeftMoveLeft |
|Bord gauche déplacer vers la droite|**Ctrl + Maj +.**| View.EdgeLeftMoveRight |
|Bord droit déplacer vers la gauche|**Ctrl+Maj+Alt+,**| View.EdgeRightMoveLeft |
|Bord droit déplacer vers la droite|**Ctrl + Maj + Alt +.**| View.EdgeRightMoveRight |
|Afficher le menu marqueur de propriété|**Ctrl + barre d’espace**| View.ShowPropertyMarkerMenu |

### <a name="xml-text-editor"></a>Éditeur XML (Texte)

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|Démarrer le débogage XSLT|**Alt + F5**| XML.StartXSLTDebugging |
|Démarrer XSLT sans débogage|**Ctrl+Alt+F5**| XML.StartXSLTWithoutDebugging |

### <a name="xml-schema-designer"></a>Concepteur de schémas XML

Les raccourcis spécifiques à ce contexte sont les suivants :


|Commandes|Raccourcis clavier|ID de commande|
|-|-|-|
|De bas en haut|**Alt + Flèche haut**| GraphView.BottomtoTop |
|De gauche à droite|**Alt + Flèche droite**| GraphView.LefttoRight |
|De droite à gauche|**Alt + Flèche gauche**| GraphView.RighttoLeft |
|De haut en bas|**Alt + flèche bas**| GraphView.ToptoBottom |
|Supprimer de l’espace de travail|**Supprimer**| OtherContextMenus.GraphView.RemovefromWorkspace |
|Afficher la vue de modèle de contenu|**CTRL + 2**| XsdDesigner.ShowContentModelView |
|Afficher la vue du graphique|**Ctrl + 3**| XsdDesigner.ShowGraphView |
|Afficher la vue de départ|**CTRL + 1**| XsdDesigner.ShowStartView |

## <a name="see-also"></a>Voir aussi

- [Commandes Visual Studio](reference/visual-studio-commands.md)
