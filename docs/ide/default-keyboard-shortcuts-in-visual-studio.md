---
title: Raccourcis clavier par défaut dans Visual Studio
ms.date: 06/26/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- shortcut keys [Visual Studio], keyboard binding schemes
- keyboard binding schemes [Visual Studio]
- Help [Visual Studio], shortcut keys
- keyboard shortcuts [Visual Studio], keyboard binding schemes
- keyboard shortcuts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4efd55fbe297e46fb448bbd2087f36df54a1d56c
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927345"
---
# <a name="default-keyboard-shortcuts-in-visual-studio"></a>Raccourcis clavier par défaut dans Visual Studio

Pour plus d’informations sur l’accessibilité du clavier, consultez [Conseils et astuces d’accessibilité](../ide/reference/accessibility-tips-and-tricks.md) et [Guide pratique pour utiliser uniquement le clavier](../ide/reference/how-to-use-the-keyboard-exclusively.md).

Pour accéder à diverses commandes et fenêtres dans Visual Studio, vous pouvez choisir les raccourcis clavier appropriés. Cette rubrique répertorie les raccourcis par défaut propres au profil de développement général, que vous avez peut-être choisi en installant Visual Studio. Quel que soit le profil que vous avez choisi, vous pouvez identifier le raccourci d’une commande en ouvrant la boîte de dialogue **Options**, en développant le nœud **Environnement**, puis en choisissant **Clavier**. Vous pouvez également personnaliser vos raccourcis en assignant un raccourci différent à toute commande donnée.

Pour obtenir la liste des raccourcis clavier courants et d’autres informations sur la productivité, consultez [Raccourcis clavier par défaut pour les commandes fréquemment utilisées dans Visual Studio](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), [Conseils d’utilisation du clavier](../ide/tips-and-tricks-for-visual-studio.md) et [Conseils de productivité](../ide/productivity-tips-for-visual-studio.md).

Les sections du tableau suivant incluent des commandes globales, au sens où vous pouvez y accéder en tout point de Visual Studio à l'aide des raccourcis clavier indiqués :

|||||
|-|-|-|-|
|[Analyser](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_analyze)|[Edition](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_edit)|[Projet](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_project)|[Test](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_test)|
|[Architecture](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_architecture)|[Menus contextuels de l’éditeur](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_editorContext)|[Menus contextuels Projet et Solution](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_projectContext)|[Explorateur de tests](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL)|
|[Générer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_build)|[Fichier](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_file)|[Refactoriser](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_refactor)|[Outils](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_tools)|
|[Menus contextuels de l’affichage de classes](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_classview)|[Aide](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_help)|[Explorateur de solutions](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL)|[Affichage](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_view)|
|[Déboguer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debug)|[Test de charge](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_loadtest)|[Équipe](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_team)|[Fenêtre](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_window)|
|[Menus contextuels du débogueur](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_debugger)|[Autres menus contextuels](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_otherContext)|[Menus contextuels Team Foundation](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_TFcontext)|[Azure](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_windowsazure)|
|[Hub de diagnostic](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_diagnostics)||||

##  <a name="bkmk_global"></a> Global

###  <a name="bkmk_analyze"></a> Analyser

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Analyze.NavigateBackward|**Maj+Alt+3**|
|Analyze.NavigateForward|**Maj+Alt+4**|

###  <a name="bkmk_architecture"></a> Architecture

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Architecture.NewDiagram|**Ctrl+\\, Ctrl+N**|

###  <a name="bkmk_build"></a> Générer

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Build.BuildSolution|**Ctrl+Maj+B**|
|Build.Cancel|**Ctrl+Attn**|
|Build.Compile|**Ctrl+F7**|
|Build.RunCodeAnalysisonSolution|**Alt+F11**|

###  <a name="bkmk_classview"></a> Menus contextuels de l’affichage des classes

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|ClassViewContextMenus.ClassViewMultiselectProjectreferencesItems.Properties|**Alt+Entrée**|

###  <a name="bkmk_debug"></a> Déboguer

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Debug.ApplyCodeChanges|**Alt+F10**|
|Debug.Autos|**Ctrl+Alt+V, A**|
|Debug.BreakAll|**Ctrl+Alt+Attn**|
|Debug.BreakatFunction|**Ctrl+B**|
|Debug.Breakpoints|**Ctrl+Alt+B**|
|Debug.CallStack|**Ctrl+Alt+C**|
|Debug.DeleteAllBreakpoints|**Ctrl+Maj+F9**|
|Debug.DiagnosticsHub.Launch|**Alt+F2**|
|Debug.Disassembly|**Ctrl+Alt+D**|
|Debug.DOMExplorer|**Ctrl+Alt+V, D**|
|Debug.EnableBreakpoint|**Ctrl+F9**|
|Debug.Exceptions|**Ctrl+Alt+E**|
|Debug.GoToPreviousCallorIntelliTraceEvent|**Ctrl+Maj+F11**|
|Debug.Graphics.StartDiagnostics|**Alt+F5**|
|Debug.Immediate|**Ctrl+Alt+I**|
|Debug.IntelliTraceCalls|**Ctrl+Alt+Y, T**|
|Debug.IntelliTraceEvents|**Ctrl+Alt+Y, F**|
|Debug.JavaScriptConsole|**Ctrl+Alt+V, C**|
|Debug.Locals|**Ctrl+Alt+V, L**|
|Debug.LocationToolbar.ProcessCombo|**Ctrl+5**|
|Debug.LocationToolbar.StackFrameCombo|**Ctrl+7**|
|Debug.LocationToolbar.ThreadCombo|**Ctrl+6**|
|Debug.LocationToolbar.ToggleCurrentThreadFlaggedState|**Ctrl+8**|
|Debug.LocationToolbar.ToggleFlaggedThreads|**Ctrl+9**|
|Debug.Memory1|**Ctrl+Alt+M, 1**|
|Debug.Memory2|**Ctrl+Alt+M, 2**|
|Debug.Memory3|**Ctrl+Alt+M, 3**|
|Debug.Memory4|**Ctrl+Alt+M, 4**|
|Debug.Modules|**Ctrl+Alt+U**|
|Debug.ParallelStacks|**Ctrl+Maj+D, S**|
|Debug.ParallelWatch1|**Ctrl+Maj+D, 1**|
|Debug.ParallelWatch2|**Ctrl+Maj+D, 2**|
|Debug.ParallelWatch3|**Ctrl+Maj+D, 3**|
|Debug.ParallelWatch4|**Ctrl+Maj+D, 4**|
|Debug.Processes|**Ctrl+Alt+Z**|
|Debug.QuickWatch|**Maj+F9**<br /><br /> ou<br /><br /> **Ctrl+Alt+Q**|
|Debug.RefreshWindowsapp|**Ctrl+Maj+R**|
|Debug.Registers|**Ctrl+Alt+G**|
|Debug.Restart|**Ctrl+Maj+F5**|
|Debug.RunToCursor|**Ctrl+F10**|
|Debug.SetNextStatement|**Ctrl+Maj+F10**|
|Debug.ShowCallStackonCodeMap|**Ctrl+Maj+`**|
|Debug.ShowNextStatement|**Alt+Num** *|
|Debug.Start|**F5**|
|Debug.StartWindowsPhoneApplicationAnalysis|**Alt+F1**|
|Debug.StartWithoutDebugging|**Ctrl + F5**|
|Debug.StepInto|**F11**|
|Debug.StepIntoCurrentProcess|**Ctrl+Alt+F11**|
|Debug.StepIntoSpecific|**Maj+Alt+F11**|
|Debug.StepOut|**Maj+F11**|
|Debug.StepOutCurrentProcess|**Ctrl+Maj+Alt+F11**|
|Debug.StepOver|**F10**|
|Debug.StepOverCurrentProcess|**Ctrl+Alt+F10**|
|Debug.StopDebugging|**Maj+F5**|
|Debug.StopPerformanceAnalysis|**Maj+Alt+F2**|
|Debug.Tasks|**Ctrl+Maj+D, K**|
|Debug.Threads|**Ctrl+Alt+H**|
|Debug.ToggleBreakpoint|**F9**|
|Debug.ToggleDisassembly|**Ctrl+F11**|
|Debug.Watch1|**Ctrl+Alt+W, 1**|
|Debug.Watch2|**Ctrl+Alt+W, 2**|
|Debug.Watch3|**Ctrl+Alt+W, 3**|
|Debug.Watch4|**Ctrl+Alt+W, 4**|

###  <a name="bkmk_debugger"></a> Menus contextuels du débogueur

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|DebuggerContextMenus.BreakpointsWindow.Delete|**Alt+F9, D**|
|DebuggerContextMenus.BreakpointsWindow.GoToDisassembly|**Alt+F9, A**|
|DebuggerContextMenus.BreakpointsWindow.GoToSourceCode|**Alt+F9, S**|

###  <a name="bkmk_diagnostics"></a> Hub de diagnostic

|Commande|Raccourci clavier|
|-------------|-----------------------|
|DiagnosticsHub.StopCollection|**Ctrl+Alt+F2**|

###  <a name="bkmk_edit"></a> Edition

|Commandes|Raccourcis clavier|
|--------------|-|
|Edit.Copy|**Ctrl+C**<br /><br /> ou<br /><br /> **Ctrl+Inser**|
|Edit.Cut|**Ctrl+X**<br /><br /> ou<br /><br /> **Maj+Suppr**|
|Edit.CycleClipboardRing|**Ctrl+Maj+V**<br /><br /> ou<br /><br /> **Ctrl+Maj+Inser**|
|Edit.Delete|**Supprimer**|
|Edit.Find|**Ctrl+F**|
|Edit.FindAllReferences|**Maj + F12**|
|Edit.FindinFiles|**Ctrl+Maj+F**|
|Edit.FindNext|**F3**|
|Edit.FindNextSelected|**Ctrl+F3**|
|Edit.FindPrevious|**Maj+F3**|
|Edit.FindPreviousSelected|**Ctrl+Maj+F3**|
|Edit.GenerateMethod|**Ctrl+K, Ctrl+M**|
|Edit.GoTo|**Ctrl+G**|
|Edit.GoToDeclaration|**Ctrl + F12**|
|Edit.GoToDefinition|**F12**|
|Edit.GoToFindCombo|**Ctrl+D**|
|Edit.GoToNextLocation|**F8**|
|Edit.GoToPrevLocation|**Maj+F8**|
|Edit.InsertSnippet|**Ctrl+K, Ctrl+X**|
|Edit.MoveControlDown|**Ctrl+Bas**|
|Edit.MoveControlDownGrid|**Bas**|
|Edit.MoveControlLeft|**Ctrl+Gauche**|
|Edit.MoveControlLeftGrid|**Gauche**|
|Edit.MoveControlRight|**Ctrl+Droite**|
|Edit.MoveControlRightGrid|**Droite**|
|Edit.MoveControlUp|**Ctrl+Haut**|
|Edit.MoveControlUpGrid|**Haut**|
|Edit.NavigateTo|**Ctrl+,**|
|Edit.NextBookmark|**Ctrl+K, Ctrl+N**|
|Edit.NextBookmarkInFolder|**Ctrl+Maj+K, Ctrl+Maj+N**|
|Edit.OpenFile|**Ctrl+Maj+G**|
|Edit.Paste|**Ctrl+V**<br /><br /> ou<br /><br /> **Maj+Inser**|
|Edit.PreviousBookmark|**Ctrl+K, Ctrl+P**|
|Edit.PreviousBookmarkInFolder|**Ctrl+Maj+K, Ctrl+Maj+P**|
|Edit.QuickFindSymbol|**Maj+Alt+F12**|
|Edit.Redo|**Ctrl+Y**<br /><br /> ou<br /><br /> **Ctrl+Maj+Z**<br /><br /> ou<br /><br /> **Maj+Alt+Retour arrière**|
|Edit.RefreshRemoteReferences|**Ctrl+Maj+J**|
|Edit.Replace|**Ctrl+H**|
|Edit.ReplaceinFiles|**Ctrl+Maj+H**|
|Edit.SelectAll|**Ctrl+A**|
|Edit.SelectNextControl|**Tab**|
|Edit.SelectPreviousControl|**Maj+Tab**|
|Edit.ShowTileGrid|**Entrée**|
|Edit.SizeControlDown|**Ctrl+Maj+Bas**|
|Edit.SizeControlDownGrid|**Maj+Bas**|
|Edit.SizeControlLeft|**Ctrl+Maj+Gauche**|
|Edit.SizeControlLeftGrid|**Maj+Gauche**|
|Edit.SizeControlRight|**Ctrl+Maj+Droite**|
|Edit.SizeControlRightGrid|**Maj+Droite**|
|Edit.SizeControlUp|**Ctrl+Maj+Haut**|
|Edit.SizeControlUpGrid|**Maj+Haut**|
|Edit.StopSearch|**Alt+F3, S**|
|Edit.SurroundWith|**Ctrl+K, Ctrl+S**|
|Edit.Undo|**Ctrl+Z**<br /><br /> ou<br /><br /> **Alt+Retour arrière**|

###  <a name="bkmk_editorContext"></a> Menus contextuels de l’éditeur

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|EditorContextMenus.CodeWindow.Breakpoint.BreakpointEditlabels|**Alt+F9, L**|
|EditorContextMenus.CodeWindow.CodeMap.ShowItem|**Ctrl+`**|
|EditorContextMenus.CodeWindow.Execute|**Ctrl+Alt+F5**|
|EditorContextMenus.CodeWindow.GoToView|**Ctrl+M, Ctrl+G**|
|EditorContextMenus.CodeWindow.ToggleHeaderCodeFile|**Ctrl+K, Ctrl+O**|
|EditorContextMenus.CodeWindow.ViewCallHierarchy|**Ctrl+K, Ctrl+T**<br /><br /> ou<br /><br /> **Ctrl+K, T**|

###  <a name="bkmk_file"></a> Fichier

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|File.Exit|**Alt+F4**|
|File.NewFile|**Ctrl+N**|
|File.NewProject|**Ctrl+Maj+N**|
|File.NewWebSite|**Maj+Alt+N**|
|File.OpenFile|**Ctrl+O**|
|File.OpenProject|**Ctrl+Maj+O**|
|File.OpenWebSite|**Maj+Alt+O**|
|File.Print|**Ctrl+P**|
|File.SaveAll|**Ctrl+Maj+S**|
|File.SaveSelectedItems|**Ctrl+S**|
|File.ViewinBrowser|**Ctrl+Maj+W**|

###  <a name="bkmk_help"></a> Aide

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Help.AddandRemoveHelpContent|**Ctrl+Alt+F1**|
|Help.F1Help|**F1**|
|Help.ViewHelp|**Ctrl+F1**|
|Help.WindowHelp|**Maj+F1**|

###  <a name="bkmk_loadtest"></a> Test de charge

|Commande|Raccourci clavier|
|-------------|-----------------------|
|LoadTest.JumpToCounterPane|**Ctrl+R, Q**|

###  <a name="bkmk_otherContext"></a> Autres menus contextuels

|Commande|Raccourci clavier|
|-------------|-----------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.AddNewDiagram|**Insert**|

###  <a name="bkmk_project"></a> Projet

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Project.AddExistingItem|**Maj+Alt+A**|
|Project.AddNewItem|**Ctrl+Maj+A**|
|Project.ClassWizard|**Ctrl+Maj+X**|
|Project.Override|**Ctrl+Alt+Inser**|
|Project.Previewchanges|**Alt+;, Alt+C**|
|Project.Publishselectedfiles|**Alt+;, Alt+P**|
|Project.Replaceselectedfilesfromserver|**Alt+;, Alt+R**|

###  <a name="bkmk_projectContext"></a> Menus contextuels Projet et Solution

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|ProjectandSolutionContextMenus.Item.MoveDown|**Alt+Bas**|
|ProjectandSolutionContextMenus.Item.MoveUp|**Alt+Haut**|

###  <a name="bkmk_refactor"></a> Refactoriser

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Refactor.EncapsulateField|s**Ctrl+R, Ctrl+E**|
|Refactor.ExtractInterface|**Ctrl+R, Ctrl+I**|
|Refactor.ExtractMethod|**Ctrl+R, Ctrl+M**|
|Refactor.RemoveParameters|**Ctrl+R, Ctrl+V**|
|Refactor.Rename|**Ctrl+R, Ctrl+R**|
|Refactor.ReorderParameters|**Ctrl+R, Ctrl+O**|

###  <a name="bkmk_solutionexplorerGLOBAL"></a> Explorateur de solutions

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|SolutionExplorer.OpenFilesFilter|**Ctrl+[, O**<br /><br /> ou<br /><br /> **Ctrl+[, Ctrl+O**|
|SolutionExplorer.PendingChangesFilter|**Ctrl+[, P**<br /><br /> ou<br /><br /> **Ctrl+[, Ctrl+P**|
|SolutionExplorer.SyncWithActiveDocument|**Ctrl+[, S**<br /><br /> ou<br /><br /> **Ctrl+[, Ctrl+S**|

###  <a name="bkmk_team"></a> Équipe

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Team.Git.GoToGitBranches|**Ctrl+0, Ctrl+N**<br /><br /> ou<br /><br /> **Ctrl+0, N**|
|Team.Git.GoToGitChanges|**Ctrl+0, Ctrl+G**<br /><br /> ou<br /><br /> **Ctrl+0, G**|
|Team.Git.GoToGitCommits|**Ctrl+0, Ctrl+O**<br /><br /> ou<br /><br /> **Ctrl+0, O**|
|Team.TeamExplorerSearch|**Ctrl+’**|

###  <a name="bkmk_TFcontext"></a> Menus contextuels Team Foundation

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|TeamFoundationContextMenus.Commands.GoToBuilds|**Ctrl+0, Ctrl+B**<br /><br /> ou<br /><br /> **Ctrl+0, B**|
|TeamFoundationContextMenus.Commands.GoToConnect|**Ctrl+0, Ctrl+C**<br /><br /> ou<br /><br /> **Ctrl+0, C**|
|TeamFoundationContextMenus.Commands.GoToDocuments|**Ctrl+0, Ctrl+D**<br /><br /> ou<br /><br /> **Ctrl+0, D**|
|TeamFoundationContextMenus.Commands.GoToHome|**Ctrl+0, Ctrl+H**<br /><br /> ou<br /><br /> **Ctrl+0, H**|
|TeamFoundationContextMenus.Commands.GoToMyWork|**Ctrl+0, Ctrl+M**<br /><br /> ou<br /><br /> **Ctrl+0, M**|
|TeamFoundationContextMenus.Commands.GoToPendingChanges|**Ctrl+0, Ctrl+P**<br /><br /> ou<br /><br /> **Ctrl+0, P**|
|TeamFoundationContextMenus.Commands.GoToReports|**Ctrl+0, Ctrl+R**<br /><br /> ou<br /><br /> **Ctrl+0, R**|
|TeamFoundationContextMenus.Commands.GoToSettings|**Ctrl+0, Ctrl+S**<br /><br /> ou<br /><br /> **Ctrl+0, S**|
|TeamFoundationContextMenus.Commands.GoToWebAccess|**Ctrl+0, Ctrl+A**<br /><br /> ou<br /><br /> **Ctrl+0, A**|
|TeamFoundationContextMenus.Commands.GoToWorkItems|**Ctrl+0, Ctrl+W**<br /><br /> ou<br /><br /> **Ctrl+0, W**|

###  <a name="bkmk_test"></a> Tester

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Test.UseCodedUITestBuilder|**Ctrl+\\, Ctrl+C**|
|Test.UseExistingActionRecording|**Ctrl+\\, Ctrl+A**|

###  <a name="bkmk_testexplorerGLOBAL"></a> Explorateur de tests

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|TestExplorer.DebugAllTests|**Ctrl+R, Ctrl+A**|
|TestExplorer.DebugAllTestsInContext|**Ctrl+R, Ctrl+T**|
|TestExplorer.RepeatLastRun|**Ctrl+R, L**|
|TestExplorer.RunAllTests|**Ctrl+R, A**|
|TestExplorer.RunAllTestsInContext|**Ctrl+R, T**|

###  <a name="bkmk_tools"></a> Outils

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Tools.AttachtoProcess|**Ctrl+Alt+P**|
|Tools.CodeSnippetsManager|**Ctrl+K, Ctrl+B**|
|Tools.ForceGC|**Ctrl+Maj+Alt+F12, Ctrl+Maj+Alt+F12**|
|Tools.GoToCommandLine|**Ctrl+/**|

###  <a name="bkmk_view"></a> Affichage

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|View.AllWindows|**Maj+Alt+M**|
|View.ArchitectureExplorer|**Ctrl+\\, Ctrl+R**|
|View.Backward|**Alt+Gauche**|
|View.BookmarkWindow|**Ctrl+K, Ctrl+W**|
|View.BrowseNext|**Ctrl+Maj+1**|
|View.BrowsePrevious|**Ctrl+Maj+2**|
|View.CallHierarchy|**Ctrl+Alt+K**|
|View.ClassView|**Ctrl+Maj+C**|
|View.ClassViewGoToSearchCombo|**Ctrl+K, Ctrl+V**|
|View.CodeDefinitionWindow|**Ctrl+\\, D**<br /><br /> ou<br /><br /> **Ctrl+\\, Ctrl+D**|
|View.CommandWindow|**Ctrl+Alt+A**|
|View.DataSources|**Maj+Alt+D**|
|View.DocumentOutline|**Ctrl+Alt+T**|
|View.EditLabel|**F2**|
|View.ErrorList|**Ctrl+\\, E**<br /><br /> ou<br /><br /> **Ctrl+\\, Ctrl+E**|
|View.F#Interactive|**Ctrl+Alt+F**|
|View.FindSymbolResults|**Ctrl+Alt+F12**|
|View.Forward|**Alt+Droite**|
|View.ForwardBrowseContext|**Ctrl+Maj+7**|
|View.FullScreen|**Maj+Alt+Entrée**|
|View.NavigateBackward|**Ctrl+-**|
|View.NavigateForward|**Ctrl+Maj+-**|
|View.NextError|**Ctrl+Maj+F12**|
|View.Notifications|**Ctrl+W, N**<br /><br /> ou<br /><br /> **Ctrl+W, Ctrl+N**|
|View.ObjectBrowser|**Ctrl+Alt+J**|
|View.ObjectBrowserGoToSearchCombo|**Ctrl+K, Ctrl+R**|
|View.Output|**Ctrl+Alt+O**|
|View.PopBrowseContex|**Ctrl+Maj+8**|
|View.PropertiesWindow|**F4**|
|View.PropertyPages|**Maj+F4**|
|View.ResourceView|**Ctrl+Maj+E**|
|View.ServerExplorer|**Ctrl+Alt+S**|
|View.ShowSmartTag|**Maj+Alt+F10**<br /><br /> ou<br /><br /> **Ctrl + .**|
|View.SolutionExplorer|**Ctrl+Alt+L**|
|View.SQLServerObjectExplorer|**Ctrl+\\, Ctrl+S**|
|View.TaskList|**Ctrl+\\, T**<br /><br /> ou<br /><br /> **Ctrl+\\, Ctrl+T**|
|View.TfsTeamExplorer|**Ctrl+\\, Ctrl+M**|
|View.Toolbox|**Ctrl+Alt+X**|
|View.UMLModelExplorer|**Ctrl+\\, Ctrl+U**|
|View.ViewCode|**F7**|
|View.ViewDesigner|**Maj+F7**|
|View.WebBrowser|**Ctrl+Alt+R**|
|View.ZoomIn|**Ctrl+Maj+.**|
|View.ZoomOut|**Ctrl+Maj+,**|

###  <a name="bkmk_window"></a> Fenêtre

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Window.ActivateDocumentWindow|**Échap**|
|Window.AddTabtoSelection|**Ctrl+Maj+Alt+Espace**|
|Window.CloseDocumentWindow|**Ctrl+F4**|
|Window.CloseToolWindow|**Maj+Échap**|
|Window.KeepTabOpen|**Ctrl+Alt+Origine**|
|Window.MovetoNavigationBar|**Ctrl+F2**|
|Window.NextDocumentWindow|**Ctrl+F6**|
|Window.NextDocumentWindowNav|**Ctrl+Tab**|
|Window.NextPane|**Alt+F6**|
|Window.NextSplitPane|**F6**|
|Window.NextTab|**Ctrl+Alt+Pg suiv**<br /><br /> ou<br /><br /> **Ctrl+Pg Suiv**|
|Window.NextTabandAddtoSelection|**Ctrl+Maj+Alt+Pg suiv**|
|Window.NextToolWindowNav|**Alt+F7**|
|Window.PreviousDocumentWindow|**Ctrl+Maj+F6**|
|Window.PreviousDocumentWindowNav|**Ctrl+Maj+Tab**|
|Window.PreviousPane|**Maj+Alt+F6**|
|Window.PreviousSplitPane|**Maj+F6**|
|Window.PreviousTab|**Ctrl+Alt+Pg préc**<br /><br /> ou<br /><br /> **Ctrl+Pg préc**|
|Window.PreviousTabandAddtoSelection|**Ctrl+Maj+Alt+Pg préc**|
|Window.PreviousToolWindowNav|**Maj+Alt+F7**|
|Window.QuickLaunch|**Ctrl + Q**|
|Window.QuickLaunchPreviousCategory|**Ctrl+Maj+Q**|
|Window.ShowDockMenu|**Alt+-**|
|Window.ShowEzMDIFileList|**Ctrl+Alt+Bas**|
|Window.SolutionExplorerSearch|**Ctrl+;**|
|Window.WindowSearch|**Alt+`**|

###  <a name="bkmk_windowsazure"></a> Azure

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|WindowsAzure.RetryMobileServiceScriptOperation|**Ctrl+Num \*, Ctrl+R**|
|WindowsAzure.ShowMobileServiceScriptErrorDetails|**Ctrl+Num \*, Ctrl+D**|

##  <a name="adonet-entity-data-model-designer"></a>ADO.NET Entity Data Model Designer

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down|**Alt+Bas**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Down5|**Alt+Pg suiv**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToBottom|**Alt+Fin**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.ToTop|**Alt+Origine**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up|**Alt+Haut**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.MoveProperties.Up5|**Alt+Pg préc**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.Refactor.Rename|**Ctrl+R, R**|
|OtherContextMenus.MicrosoftDataEntityDesignContext.RemovefromDiagram|**Maj+Suppr**|
|View.EntityDataModelBrowser|**Ctrl+1**|
|View.EntityDataModelMappingDetails|**Ctrl+2**|

##  <a name="class-diagram"></a>Diagramme de classes

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|ClassDiagram.Collapse|**Num -**|
|ClassDiagram.Expand|**Num +**|
|Edit.Delete|**Ctrl+Suppr**|
|Edit.ExpandCollapseBaseTypeList|**Maj+Alt+B**|
|Edit.NavigateToLollipop|**Maj+Alt+L**|
|Edit.RemovefromDiagram|**Supprimer**|
|View.ViewCode|**Entrée**|

##  <a name="coded-ui-test-editor"></a>Éditeur de test codé de l'interface utilisateur

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|OtherContextMenus.UITestEditorContextMenu.CopyReferencetoClipboard|**Ctrl+C**|
|OtherContextMenus.UITestEditorContextMenu.InsertDelayBefore|**Ctrl+Alt+D**|
|OtherContextMenus.UITestEditorContextMenu.LocateAll|**Maj+Alt+L**|
|OtherContextMenus.UITestEditorContextMenu.LocatetheUIControl|**Ctrl+Maj+L**|
|OtherContextMenus.UITestEditorContextMenu.Movecode|**Ctrl+Alt+C**|
|OtherContextMenus.UITestEditorContextMenu.Splitintoanewmethod|**Ctrl+Maj+T**|

##  <a name="dataset-editor"></a>Éditeur DataSet

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|OtherContextMenus.ColumnContext.InsertColumn|**Insert**|
|OtherContextMenus.DbTableContext.Add.Column|**Ctrl+L**|

##  <a name="difference-viewer"></a>Visionneuse de différences

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Diff.IgnoreTrimWhitespace|**Ctrl+\\, Ctrl+Barre d’espace**|
|Diff.InlineView|**Ctrl+\\, Ctrl+1**|
|Diff.LeftOnlyView|**Ctrl+\\, Ctrl+3**|
|Diff.NextDifference|**F8**|
|Diff.PreviousDifference|**Maj+F8**|
|Diff.RightOnlyView|**Ctrl+\\, Ctrl+4**|
|Diff.SideBySideView|**Ctrl+\\, Ctrl+2**|
|Diff.SwitchBetweenLeftAndRight|**Ctrl+\\, Ctrl+Tab**|
|Diff.SynchronizeViewToggle|**Ctrl+\\, Ctrl+Bas**|
|EditorContextMenus.CodeWindow.AddComment|**Ctrl+Maj+K**|
|EditorContextMenus.CodeWindow.EditLocalFile|**Ctrl+Maj+P**|

##  <a name="dom-explorer"></a>Explorateur DOM

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|DOMExplorer.Refresh|**F5**|
|DOMExplorer.SelectElement|**Ctrl+B**|
|DOMExplorer.ShowLayout|**Ctrl+Maj+I**|

##  <a name="f-interactive"></a>F# interactif

|Commande|Raccourci clavier|
|-------------|-----------------------|
|OtherContextMenus.FSIConsoleContext.CancelInteractiveEvaluation|**Ctrl+Attn**|

##  <a name="graph-document-editor"></a>Éditeur de document de graphique

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Add.AddNode|**Insert**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.BothDependencies|**B**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.IncomingDependencies|**I**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Advanced.Select.OutgoingDependencies|**O**|
|ArchitectureContextMenus.DirectedGraphContextMenu.NewComment|**Ctrl+Maj+K**<br /><br /> ou<br /><br /> **Ctrl+E, C**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Remove|**Supprimer**|
|ArchitectureContextMenus.DirectedGraphContextMenu.Rename|**F2**|

##  <a name="graphics-diagnostics"></a>Graphics Diagnostics

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Debug.Graphics.CaptureFrame|Aucun.|
|Graphics.MovePixelSelectionDown|**Maj+Alt+Bas**|
|Graphics.MovePixelSelectionLeft|**Maj+Alt+Gauche**|
|Graphics.MovePixelSelectionRight|**Maj+Alt+Droite**|
|Graphics.MovePixelSelectionUp|**Maj+Alt+Haut**|
|Graphics.ResetZoom|**Maj+Alt+0**|
|Graphics.ZoomToFitInWindow|**Maj+Alt+9**|
|Graphics.ZoomIn|**Maj+Alt+=**|
|Graphics.ZoomOut|**Maj+Alt+-**|

##  <a name="html-editor"></a>Éditeur HTML

|Commande|Raccourci clavier|
|-------------|-----------------------|
|OtherContextMenus.HTMLContext.GoToController|**Ctrl+M, Ctrl+G**|

##  <a name="html-editor-design-view"></a>Éditeur HTML en mode Design

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.MoveControlDown|**Ctrl+Bas**|
|Edit.MoveControlUp|**Ctrl+Haut**|
|Format.Bold|**Ctrl+B**|
|Format.ConverttoHyperlink|**Ctrl+L**|
|Format.InsertBookmark|**Ctrl+Maj+L**|
|Format.Italic|**Ctrl+I**|
|Format.Underline|**Ctrl+U**|
|Project.AddContentPage|**Ctrl+M, Ctrl+C**|
|Table.ColumntotheLeft|**Ctrl+Alt+Gauche**|
|Table.ColumntotheRight|**Ctrl+Alt+Droite**|
|Table.RowAbove|**Ctrl+Alt+Haut**|
|Table.RowBelow|**Ctrl+Alt+Bas**|
|View.ASP.NETNonvisualControls|**Ctrl+Maj+N**|
|View.EditMaster|**Ctrl+M, Ctrl+M**|
|View.NextView|**Ctrl+Pg Suiv**|
|View.ShowSmartTag|**Maj+Alt+F10**|
|View.ViewMarkup|**Maj+F7**|
|Window.PreviousTab|**Ctrl+Pg préc**|

##  <a name="html-editor-source-view"></a>Éditeur HTML en mode Source

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|OtherContextMenus.HTMLContext.GoToController|**Ctrl+M, Ctrl+G**|
|View.NextView|**Ctrl+Pg Suiv**|
|View.SynchronizeViews|**Ctrl+Maj+Y**|
|View.ViewDesigner|**Maj+F7**|
|Window.PreviousTab|**Ctrl+Pg préc**|

##  <a name="layer-diagram"></a>Diagramme de couche

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.Delete|**Maj+Suppr**|

##  <a name="managed-resources-editor"></a>Éditeur de ressources managées

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.EditCell|**F2**|
|Edit.Remove|**Supprimer**|
|Edit.RemoveRow|**Ctrl+Suppr**|
|Edit.SelectionCancel|**Échap**|
|Resources.Audio|**Ctrl+4**|
|Resources.Files|**Ctrl+5**|
|Resources.Icons|**Ctrl+3**|
|Resources.Images|**Ctrl+2**|
|Resources.Other|**Ctrl+6**|
|Resources.Strings|**Ctrl+1**|

##  <a name="merge-editor-window"></a>Fenêtre de l’éditeur de fusion

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonLeftWindow|**Alt+1**|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonResultWindow|**Alt+2**|
|TeamFoundationContextMenus.MergeContextMenu.SetFocusonRightWindow|**Alt+3**|

##  <a name="microsoft-sql-server-data-tools-schema-compare"></a>Microsoft SQL Server Data Tools, Comparaison de schémas

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|SQL.SSDTSchemaCompareCompare|**Maj+Alt+C**|
|SQL.SSDTSchemaCompareGenerateScript|**Maj+Alt+G**|
|SQL.SSDTSchemaCompareNextChange|**Maj+Alt+.**|
|SQL.SSDTSchemaComparePreviousChange|**Maj+Alt+,**|
|SQL.SSDTSchemaCompareStop|**Alt+Attn**|
|SQL.SSDTSchemaCompareWriteUpdates|**Maj+Alt+U**|

##  <a name="microsoft-sql-server-data-tools-table-designer"></a>Microsoft SQL Server Data Tools, Concepteur de tables

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|CommitAllEdits|**Maj+Alt+U**|
|SQL.ExpandWildcards|**Ctrl+R, E**<br /><br /> ou<br /><br /> s**Ctrl+R, Ctrl+E**|
|SQL.FullyqualifyNames|**Ctrl+R, Q**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+Q**|
|SQL.MovetoSchema|**Ctrl+R, M**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+M**|
|SQL.Rename|**F2**<br /><br /> ou<br /><br /> **Ctrl+R, R**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+R**|
|ViewFileInScriptPanel|**Maj+Alt+Pg suiv**|

##  <a name="microsoft-sql-server-data-tools-t-sql-editor"></a>Microsoft SQL Server Data Tools, Éditeur T-SQL

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|CommitAllEdits|**Maj+Alt+U**|
|SQL.ExecuteWithDebugger|**Alt+F5**|
|SQL.ExpandWildcards|**Ctrl+R, E**<br /><br /> ou<br /><br /> s**Ctrl+R, Ctrl+E**|
|SQL.FullyqualifyNames|**Ctrl+R, Q**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+Q**|
|SQL.MovetoSchema|**Ctrl+R, M**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+M**|
|SQL.Rename|**F2**<br /><br /> ou<br /><br /> **Ctrl+R, R**<br /><br /> ou<br /><br /> **Ctrl+R, Ctrl+R**|
|SQL.TSqlEditorCancelQuery|**Alt+Attn**|
|SQL.TSqlEditorExecuteQuery|**Ctrl+Maj+E**|
|SQL.TSqlEditorResultsAsFile|**Ctrl+D, F**|
|SQL.TSqlEditorResultsAsGrid|**Ctrl+D, G**|
|SQL.TSqlEditorResultsAsText|**Ctrl+D, T**|
|SQL.TSqlEditorShowEstimatedPlan|**Ctrl+D, E**|
|SQL.TSqlEditorToggleExecutionPlan|**Ctrl+D, A**|
|SQL.TSqlEditorToggleResultsPane|**Ctrl+D, R**|
|TSqlEditorCloneQuery|**Ctrl+Alt+N**|
|TSqlEditorDatabaseCombo|**Maj+Alt+Pg suiv**|

##  <a name="microsoft-sql-server-data-tools-t-sql-pdw-editor"></a>Microsoft SQL Server Data Tools, Éditeur T-SQL PDW

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|SQL.TSqlEditorCancelQuery|**Alt+Attn**|
|SQL.TSqlEditorExecuteQuery|**Ctrl+Maj+E**|
|SQL.TSqlEditorResultsAsFile|**Ctrl+D, F**|
|SQL.TSqlEditorResultsAsGrid|**Ctrl+D, G**|
|SQL.TSqlEditorResultsAsText|**Ctrl+D, T**|
|SQL.TSqlEditorShowEstimatedPlan|**Ctrl+D, E**|
|SQL.TSqlEditorToggleExecutionPlan|**Ctrl+D, A**|
|SQL.TSqlEditorToggleResultsPane|**Ctrl+D, R**|
|TSqlEditorCloneQuery|**Ctrl+Alt+N**|
|TSqlEditorDatabaseCombo|**Maj+Alt+Pg suiv**|

##  <a name="page-inspector"></a>Inspecteur de page

|Commande|Raccourci clavier|
|-------------|-----------------------|
|PageInspector.Minimize|**F12**|

##  <a name="query-designer"></a>Concepteur de requêtes

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|**Ctrl + T**|
|QueryDesigner.Criteria|**Ctrl+2**|
|QueryDesigner.Diagram|**Ctrl+1**|
|QueryDesigner.ExecuteSQL|**Ctrl+R**|
|QueryDesigner.GotoRow|**Ctrl+G**|
|QueryDesigner.JoinMode|**Ctrl+Maj+J**|
|QueryDesigner.Results|**Ctrl+4**|
|QueryDesigner.SQL|**Ctrl+3**|

##  <a name="query-results"></a>Résultats des requêtes

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|SQL.QueryResultsNewRow|**Alt+Fin**|
|SQL.QueryResultsRefresh|**Maj+Alt+R**|
|SQL.QueryResultsStop|**Alt+Attn**|

##  <a name="report-designer"></a>Concepteur de rapports

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.BreakLine|**Entrée**|
|Edit.CharLeft|**Gauche**|
|Edit.CharLeftExtend|**Maj+Gauche**|
|Edit.CharRight|**Droite**|
|Edit.CharRightExtend|**Maj+Droite**|
|Edit.InsertTab|**Tab**|
|Edit.LineDown|**Bas**|
|Edit.LineDownExtend|**Maj+Bas**|
|Edit.LineUp|**Haut**|
|Edit.LineUpExtend|**Maj+Haut**|
|Edit.MoveControlDown|**Ctrl+Bas**|
|Edit.MoveControlLeft|**Ctrl+Gauche**|
|Edit.MoveControlRight|**Ctrl+Droite**|
|Edit.MoveControlUp|**Ctrl+Haut**|
|Edit.SelectionCancel|**Échap**|
|Edit.SizeControlDown|**Ctrl+Maj+Bas**|
|Edit.SizeControlLeft|**Ctrl+Maj+Gauche**|
|Edit.SizeControlRight|**Ctrl+Maj+Droite**|
|Edit.SizeControlUp|**Ctrl+Maj+Haut**|
|Edit.TabLeft|**Maj+Tab**|
|View.ReportData|**Ctrl+Alt+D**|

##  <a name="sequence-diagram"></a>Diagramme de séquence

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|ArchitectureDesigner.Sequence.NavigateToCode|**F12**|
|Edit.Delete|**Maj+Suppr**|

##  <a name="settings-designer"></a>Concepteur de paramètres

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.EditCell|**F2**|
|Edit.RemoveRow|**Ctrl+Suppr**|
|Edit.SelectionCancel|**Échap**|
|View.ViewCode|**F7**|

##  <a name="solution-explorer"></a>Explorateur de solutions

|Commande|Raccourci clavier|
|-------------|-----------------------|
|ClassViewContextMenus.ClassViewProject.View.ViewinPageInspector|**Ctrl+K, Ctrl+G**|

##  <a name="team-explorer"></a>Team Explorer

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.Delete|**Supprimer**|
|File.Rename|**F2**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNavigation|**Alt+Origine**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerNextSectionContent|**Alt+Bas**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPageContent|**Alt+0**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerPreviousSectionContent|**Alt+Haut**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection1Content|**Alt+1**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection2Content|**Alt+2**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection3Content|**Alt+3**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection4Content|**Alt+4**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection5Content|**Alt+5**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection6Content|**Alt+6**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection7Content|**Alt+7**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection8Content|**Alt+8**|
|TeamFoundationContextMenus.Commands.GoToTeamExplorerSection9Content|**Alt+9**|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateBackward|**Alt+Gauche**|
|TeamFoundationContextMenus.Commands.TeamExplorerNavigateForward|**Alt+Droite**|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageCreateCopyWI|**Maj+Alt+C**|
|TeamFoundationContextMenus.MyWorkPageInProgress.TfsContextMyWorkPageNewLinkedWI|**Maj+Alt+L**|
|View.Refresh|**F5**|

##  <a name="team-foundation-build-detail-editor"></a>Éditeur des détails Team Foundation Build

|Commande|Raccourci clavier|
|-------------|-----------------------|
|View.Refresh|**F5**|

##  <a name="test-explorer"></a>Explorateur de tests

|Commande|Raccourci clavier|
|-------------|-----------------------|
|TestExplorer.OpenTest|**F12**|

##  <a name="text-editor"></a>Éditeur de texte

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.BreakLine|**Entrée**<br /><br /> ou<br /><br /> **Maj+Entrée**|
|Edit.CharLeft|**Gauche**|
|Edit.CharLeftExtend|**Maj+Gauche**|
|Edit.CharLeftExtendColumn|**Maj+Alt+Gauche**|
|Edit.CharRight|**Droite**|
|Edit.CharRightExtend|**Maj+Droite**|
|Edit.CharRightExtendColumn|**Maj+Alt+Droite**|
|Edit.CharTranspose|**Ctrl + T**|
|Edit.ClearBookmarks|**Ctrl+K, Ctrl+L**|
|Edit.CollapseAllOutlining|**Ctrl+M, Ctrl+A**|
|Edit.CollapseCurrentRegion|**Ctrl+M, Ctrl+S**|
|Edit.CollapseTag|**Ctrl+M, Ctrl+T**|
|Edit.CollapsetoDefinitions|**Ctrl+M, Ctrl+O**|
|Edit.CommentSelection|**Ctrl+K, Ctrl+C**|
|Edit.CompleteWord|**Ctrl+Barre d’espace**<br /><br /> ou<br /><br /> **Alt+Droite**|
|Edit.CopyParameterTip|**Ctrl+Maj+Alt+C**|
|Edit.DecreaseFilterLevel|**Alt+,**|
|Edit.DeleteBackwards|**Retour arrière**<br /><br /> ou<br /><br /> **Maj+Retour arrière**|
|Edit.DeleteHorizontalWhiteSpace|**Ctrl+K, Ctrl+\**|
|Edit.DocumentEnd|**Ctrl+Fin**|
|Edit.DocumentEndExtend|**Ctrl+Maj+Fin**|
|Edit.DocumentStart|**Ctrl+Origine**|
|Edit.DocumentStartExtend|**Ctrl+Maj+Origine**|
|Edit.ExpandAllOutlining|**Ctrl+M, Ctrl+X**|
|Edit.ExpandCurrentRegion|**Ctrl+M, Ctrl+E**|
|Edit.FormatDocument|**Ctrl+K, Ctrl+D**|
|Edit.FormatSelection|**Ctrl+K, Ctrl+F**|
|Edit.GotoBrace|**Ctrl+]**|
|Edit.GotoBraceExtend|**Ctrl+Shift+]**|
|Edit.HideSelection|**Ctrl+M, Ctrl+H**|
|Edit.IncreaseFilterLevel|**Alt+.**|
|Edit.IncrementalSearch|**Ctrl+I**|
|Edit.InsertTab|**Tab**|
|Edit.LineCut|**Ctrl+L**|
|Edit.LineDelete|**Ctrl+Maj+L**|
|Edit.LineDown|**Bas**|
|Edit.LineDownExtend|**Maj+Bas**|
|Edit.LineDownExtendColumn|**Maj+Alt+Bas**|
|Edit.LineEnd|**Fin**|
|Edit.LineEndExtend|**Maj+Fin**|
|Edit.LineEndExtendColumn|**Maj+Alt+Fin**|
|Edit.LineOpenAbove|**Ctrl+Entrée**|
|Edit.LineOpenBelow|**Ctrl+Maj+Entrée**|
|Edit.LineStart|**Accueil**|
|Edit.LineStartExtend|**Maj+Origine**|
|Edit.LineStartExtendColumn|**Maj+Alt+Origine**|
|Edit.LineTranspose|**Maj+Alt+T**|
|Edit.LineUp|**Haut**|
|Edit.LineUpExtend|**Maj+Haut**|
|Edit.LineUpExtendColumn|**Maj+Alt+Haut**|
|Edit.ListMembers|**Ctrl+J**|
|Edit.MakeLowercase|**Ctrl+U**|
|Edit.MakeUppercase|**Ctrl+Maj+U**|
|Edit.MoveSelectedLinesDown|**Alt+Bas**|
|Edit.MoveSelectedLinesUp|**Alt+Haut**|
|Edit.NextHighlightedReference|**Ctrl+Maj+Bas**|
|Edit.OvertypeMode|**Insert**|
|Edit.PageDown|**Pg suiv**|
|Edit.PageDownExtend|**Maj+Pg suiv**|
|Edit.PageUp|**Pg préc**|
|Edit.PageUpExtend|**Maj+Pg préc**|
|Edit.ParameterInfo|**Ctrl+Maj+Barre d’espace**|
|Edit.PasteParameterTip|**Ctrl+Maj+Alt+P**|
|Edit.PeekBackward|**Ctrl+Alt+-**|
|Edit.PeekDefinition|**Alt + F12**|
|Edit.PeekForward|**Ctrl+Alt+=**|
|Edit.PreviousHighlightedReference|**Ctrl+Maj+Haut**|
|Edit.QuickInfo|**Ctrl+K, Ctrl+I**|
|Edit.ReverseIncrementalSearch|**Ctrl+Maj+I**|
|Edit.ScrollLineDown|**Ctrl+Bas**|
|Edit.ScrollLineUp|**Ctrl+Haut**|
|Edit.SelectCurrentWord|**Ctrl+W**|
|Edit.SelectionCancel|**Échap**|
|Edit.SelectToLastGoBack|**Ctrl+=**|
|Edit.ShowCodeLensMenu|**Alt+`**|
|Edit.StopHidingCurrent|**Ctrl+M, Ctrl+U**|
|Edit.StopOutlining|**Ctrl+M, Ctrl+P**|
|Edit.SwapAnchor|**Ctrl+K, Ctrl+A**|
|Edit.TabLeft|**Maj+Tab**|
|Edit.ToggleAllOutlining|**Ctrl+M, Ctrl+L**|
|Edit.ToggleBookmark|**Ctrl+K, Ctrl+K**|
|Edit.ToggleCompletionMode|**Ctrl+Alt+Barre d’espace**|
|Edit.ToggleOutliningExpansion|**Ctrl+M, Ctrl+M**|
|Edit.ToggleTaskListShortcut|**Ctrl+K, Ctrl+H**|
|Edit.ToggleWordWrap|**Ctrl+E, Ctrl+W**|
|Edit.UncommentSelection|**Ctrl+K, Ctrl+U**|
|Edit.ViewBottom|**Ctrl+Pg Suiv**|
|Edit.ViewBottomExtend|**Ctrl+Maj+Pg suiv**|
|Edit.ViewTop|**Ctrl+Pg préc**|
|Edit.ViewTopExtend|**Ctrl+Maj+Pg préc**|
|Edit.ViewWhiteSpace|**Ctrl+R, Ctrl+W**|
|Edit.WordDeleteToEnd|**Ctrl+Suppr**|
|Edit.WordDeleteToStart|**Ctrl+Retour arrière**|
|Edit.WordNext|**Ctrl+Droite**|
|Edit.WordNextExtend|**Ctrl+Maj+Droite**|
|Edit.WordNextExtendColumn|**Ctrl+Maj+Alt+Droite**|
|Edit.WordPrevious|**Ctrl+Gauche**|
|Edit.WordPreviousExtend|**Ctrl+Maj+Gauche**|
|Edit.WordPreviousExtendColumn|**Ctrl+Maj+Alt+Gauche**|
|Edit.WordTranspose|**Ctrl+Maj+T**|
|EditorContextMenus.CodeWindow.ExecuteInInteractive|**Alt+Entrée**|
|EditorContextMenus.CodeWindow.ExecuteLineInInteractive|**Alt+’**|
|OtherContextMenus.HTMLContext.ViewinPageInspector|**Ctrl+K, Ctrl+G**|
|TeamFoundationContextMenus.Annotate.TfsAnnotateMoveNextRegion|**Alt+Pg suiv**|
|TeamFoundationContextMenus.Annotate.TfsAnnotateMovePreviousRegion|**Alt+Pg préc**|

##  <a name="uml-activity-diagram"></a>Diagramme d'activités UML

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.Delete|**Maj+Suppr**|

##  <a name="uml-class-diagram"></a>Diagramme de classes UML

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.DeleteFromModel|**Maj+Suppr**|

##  <a name="uml-component-diagram"></a>Diagramme de composant UML

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.DeleteFromModel|**Maj+Suppr**|

##  <a name="uml-use-case-diagram"></a>Diagramme de cas d'usage UML

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.DeleteFromModel|**Maj+Suppr**|

##  <a name="vc-accelerator-editor"></a>Éditeur d'accélérateurs VC

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.NewAccelerator|**Insert**|
|Edit.NextKeyTyped|**Ctrl+W**|

##  <a name="vc-dialog-editor"></a>Éditeur de boîtes de dialogue VC

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.MoveControlDown|**Bas**|
|Edit.MoveControlLeft|**Gauche**|
|Edit.MoveControlRight|**Droite**|
|Edit.MoveControlUp|**Haut**|
|Edit.ScrollColumnLeft|**Ctrl+Gauche**|
|Edit.ScrollColumnRight|**Ctrl+Droite**|
|Edit.ScrollLineDown|**Ctrl+Bas**|
|Edit.ScrollLineUp|**Ctrl+Haut**|
|Edit.SizeControlDown|**Maj+Bas**|
|Edit.SizeControlLeft|**Maj+Gauche**|
|Edit.SizeControlRight|**Maj+Droite**|
|Edit.SizeControlUp|**Maj+Haut**|
|Format.AlignBottoms|**Ctrl+Maj+Bas**|
|Format.AlignCenters|**Maj+F9**|
|Format.AlignLefts|**Ctrl+Maj+Gauche**|
|Format.AlignMiddles|**F9**|
|Format.AlignRights|**Ctrl+Maj+Droite**|
|Format.AlignTops|**Ctrl+Maj+Haut**|
|Format.ButtonBottom|**Ctrl+B**|
|Format.ButtonRight|**Ctrl+R**|
|Format.CenterHorizontal|**Ctrl+Maj+F9**|
|Format.CenterVertical|**Ctrl+F9**|
|Format.CheckMnemonics|**Ctrl+M**|
|Format.SizetoContent|**Maj+F7**|
|Format.SpaceAcross|**Alt+Droite**<br /><br /> ou<br /><br /> **Alt+Gauche**|
|Format.SpaceDown|**Alt+Haut**<br /><br /> ou<br /><br /> **Alt+Bas**|
|Format.TabOrder|**Ctrl+D**|
|Format.TestDialog|**Ctrl + T**|
|Format.ToggleGuides|**Ctrl+G**|

##  <a name="vc-image-editor"></a>Éditeur d'images VC

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Image.AirbrushTool|**Ctrl+A**|
|Image.BrushTool|**Ctrl+B**|
|Image.CopyandOutlineSelection|**Ctrl+Maj+U**|
|Image.DrawOpaque|**Ctrl+J**|
|Image.EllipseTool|**Alt+P**|
|Image.EraseTool|**Ctrl+Maj+I**|
|Image.FilledEllipseTool|**Ctrl+Maj+Alt+P**|
|Image.FilledRectangleTool|**Ctrl+Maj+Alt+R**|
|Image.FilledRoundedRectangleTool|**Ctrl+Maj+Alt+W**|
|Image.FillTool|**Ctrl+F**|
|Image.FlipHorizontal|**Ctrl+H**|
|Image.FlipVertical|**Maj+Alt+H**|
|Image.LargerBrush|**Ctrl+=**|
|Image.LineTool|**Ctrl+L**|
|Image.MagnificationTool|**Ctrl+M**|
|Image.Magnify|**Ctrl+Maj+M**|
|Image.NewImageType|**Insert**|
|Image.NextColor|**Ctrl+]**<br /><br /> ou<br /><br /> **Ctrl+Droite**|
|Image.NextRightColor|**Ctrl+Shift+]**<br /><br /> ou<br /><br /> **Ctrl+Maj+Droite**|
|Image.OutlinedEllipseTool|**Maj+Alt+P**|
|Image.OutlinedRectangleTool|**Maj+Alt+R**|
|Image.OutlinedRoundedRectangleTool|**Maj+Alt+W**|
|Image.PencilTool|**Ctrl+I**|
|Image.PreviousColor|**Ctrl+[**<br /><br /> ou<br /><br /> **Ctrl+Gauche**|
|Image.PreviousRightColor|**Ctrl+Maj+[**<br /><br /> ou<br /><br /> **Ctrl+Maj+Gauche**|
|Image.RectangleSelectionTool|**Maj+Alt+S**|
|Image.RectangleTool|**Alt+R**|
|Image.Rotate90Degrees|**Ctrl+Maj+H**|
|Image.RoundedRectangleTool|**Alt+W**|
|Image.ShowGrid|**Ctrl+Alt+S**|
|Image.ShowTileGrid|**Ctrl+Maj+Alt+S**|
|Image.SmallBrush|**Ctrl + .**|
|Image.SmallerBrush|**Ctrl+-**|
|Image.TextTool|**Ctrl + T**|
|Image.UseSelectionasBrush|**Ctrl+U**|
|Image.ZoomIn|**Ctrl+Maj+.**<br /><br /> ou<br /><br /> **Ctrl+Haut**|
|Image.ZoomOut|**Ctrl+Maj+,**<br /><br /> ou<br /><br /> **Ctrl+Bas**|

##  <a name="vc-string-editor"></a>Éditeur de chaînes VC

|Commande|Raccourci clavier|
|-------------|-----------------------|
|Edit.NewString|**Insert**|

##  <a name="view-designer"></a>Concepteur de vues

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|QueryDesigner.CancelRetrievingData|**Ctrl + T**|
|QueryDesigner.Criteria|**Ctrl+2**|
|QueryDesigner.Diagram|**Ctrl+1**|
|QueryDesigner.ExecuteSQL|**Ctrl+R**|
|QueryDesigner.GotoRow|**Ctrl+G**|
|QueryDesigner.JoinMode|**Ctrl+Maj+J**|
|QueryDesigner.Results|**Ctrl+4**|
|QueryDesigner.SQL|**Ctrl+3**|

##  <a name="visual-studio"></a>Visual Studio

|Commande|Raccourci clavier|
|-------------|-----------------------|
|OtherContextMenus.ORDesignerContext.HideMethodsPane|**Ctrl+1**|

##  <a name="windows-forms-designer"></a>Concepteur Windows Forms

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.BreakLine|**Entrée**|
|Edit.CharLeft|**Gauche**|
|Edit.CharLeftExtend|**Maj+Gauche**|
|Edit.CharRight|**Droite**|
|Edit.CharRightExtend|**Maj+Droite**|
|Edit.DocumentEnd|**Fin**|
|Edit.DocumentEndExtend|**Maj+Fin**|
|Edit.DocumentStart|**Accueil**|
|Edit.DocumentStartExtend|**Maj+Origine**|
|Edit.InsertTab|**Tab**|
|Edit.LineDown|**Bas**|
|Edit.LineDownExtend|**Maj+Haut**|
|Edit.LineUp|**Haut**|
|Edit.LineUpExtend|**Maj+Bas**|
|Edit.MoveControlDown|**Ctrl+Bas**|
|Edit.MoveControlLeft|**Ctrl+Gauche**|
|Edit.MoveControlRight|**Ctrl+Droite**|
|Edit.MoveControlUp|**Ctrl+Haut**|
|Edit.SelectionCancel|**Échap**|
|Edit.SizeControlDown|**Ctrl+Maj+Bas**|
|Edit.SizeControlLeft|**Ctrl+Maj+Gauche**|
|Edit.SizeControlRight|**Ctrl+Maj+Droite**|
|Edit.SizeControlUp|**Ctrl+Maj+Haut**|
|Edit.TabLeft|**Maj+Tab**|

##  <a name="work-item-editor"></a>Éditeur d’élément de travail

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|**Maj+Alt+C**|
|Edit.RefreshWorkItem|**F5**|
|Team.NewLinkedWorkItem|**Maj+Alt+L**|

##  <a name="work-item-query-view"></a>Affichage des requêtes d’élément de travail

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|**Maj+Alt+C**|
|Edit.Indent|**Maj+Alt+Droite**|
|Edit.Outdent|**Maj+Alt+Gauche**|
|Team.NewLinkedWorkItem|**Maj+Alt+L**|
|Team.Refresh|**F5**|
|Window.Toggle|**Maj+Alt+V**|

##  <a name="work-item-results-view"></a>Affichage des résultats des éléments de travail

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.CreateCopyofWorkItem|**Maj+Alt+C**|
|Edit.Indent|**Maj+Alt+Droite**|
|Edit.Outdent|**Maj+Alt+Gauche**|
|Team.GotoNextWorkItem|**Maj+Alt+N**|
|Team.GotoPreviousWorkItem|**Maj+Alt+P**|
|Team.NewLinkedWorkItem|**Maj+Alt+L**|
|Team.Refresh|**F5**|
|Window.Toggle|**Maj+Alt+V**|

##  <a name="workflow-designer"></a>Concepteur de flux de travail

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Edit.CompleteWord|**Ctrl+K, W**<br /><br /> ou<br /><br /> **Ctrl+K, Ctrl+W**<br /><br /> ou<br /><br /> **Ctrl+Barre d’espace**<br /><br /> ou<br /><br /> **Alt+Droite**|
|Edit.DecreaseFilterLevel|**Alt+,**|
|Edit.IncreaseFilterLevel|**Alt+.**|
|Edit.ListMembers|**Ctrl+K, L**<br /><br /> ou<br /><br /> **Ctrl+K, Ctrl+L**<br /><br /> ou<br /><br /> **Ctrl+J**|
|Edit.ParameterInfo|**Ctrl+K, P**<br /><br /> ou<br /><br /> **Ctrl+K, Ctrl+P**<br /><br /> ou<br /><br /> **Ctrl+Maj+Barre d’espace**|
|Edit.QuickInfo|**Ctrl+K, I**<br /><br /> ou<br /><br /> **Ctrl+K, Ctrl+I**|
|WorkflowDesigner.Collapse|**Ctrl+E, Ctrl+C**<br /><br /> ou<br /><br /> **Ctrl+E, C**|
|WorkflowDesigner.CollapseAll|ou|
|WorkflowDesigner.ConnectNodes|**Ctrl+E, Ctrl+F**<br /><br /> ou<br /><br /> **Ctrl+E, F**|
|WorkflowDesigner.CreateVariable|**Ctrl+E, Ctrl+N**<br /><br /> ou<br /><br /> **Ctrl+E, N**|
|WorkflowDesigner.ExpandAll|**Ctrl+E, Ctrl+X**<br /><br /> ou<br /><br /> **Ctrl+E, X**|
|WorkflowDesigner.ExpandInPlace|**Ctrl+E, Ctrl+E**<br /><br /> ou<br /><br /> **Ctrl+E, E**|
|WorkflowDesigner.GoToParent|**Ctrl+E, Ctrl+P**<br /><br /> ou<br /><br /> **Ctrl+E, P**|
|WorkflowDesigner.MoveFocus|**Ctrl+E, Ctrl+M**<br /><br /> ou<br /><br /> **Ctrl+E, M**|
|WorkflowDesigner.NavigateThroughDesigner|**Ctrl+Alt+F6**|
|WorkflowDesigner.Restore|**Ctrl+E, Ctrl+R**<br /><br /> ou<br /><br /> **Ctrl+E, R**|
|WorkflowDesigner.ShowHideArgumentDesigner|**Ctrl+E, Ctrl+A**<br /><br /> ou<br /><br /> **Ctrl+E, A**|
|WorkflowDesigner.ShowHideImportsDesigner|**Ctrl+E, Ctrl+I**<br /><br /> ou<br /><br /> **Ctrl+E, I**|
|WorkflowDesigner.ShowHideOverviewMap|**Ctrl+E, Ctrl+O**<br /><br /> ou<br /><br /> **Ctrl+E, O**|
|WorkflowDesigner.ShowHideVariableDesigner|**Ctrl+E, Ctrl+V**<br /><br /> ou<br /><br /> **Ctrl+E, V**|
|WorkflowDesigner.ToggleSelection|**Ctrl+E, Ctrl+S**<br /><br /> ou<br /><br /> **Ctrl+E, S**|
|WorkflowDesigner.ZoomIn|**Ctrl+Num +**|
|WorkflowDesigner.ZoomOut|**Ctrl+Num -**|

##  <a name="xaml-ui-designer"></a>Concepteur XAML

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|Design.FitAll|**Ctrl+0**|
|Design.ShowHandles|**F9**|
|Design.ZoomIn|**Ctrl+Alt+=**|
|Design.ZoomOut|**Ctrl+Alt+-**|
|Options du concepteur|**Ctrl+Maj+;**|
|Format.EditText|**F2**|
|Format.ResetLayout.All|**Ctrl+Maj+R**|
|Exécuter le code de projet|**Ctrl+F9**|
|Timeline.Hide (Blend uniquement)|**Ctrl+H**|
|Timeline.Lock (Blend uniquement)|**Ctrl+L**|
|Timeline.Show (Blend uniquement)|**Ctrl+Maj+H**|
|Timeline.Unlock (Blend uniquement)|**Ctrl+Maj+L**|
|View.EdgeLeftMoveLeft|**Ctrl+Maj+,**|
|View.EdgeLeftMoveRight|**Ctrl+Maj+.**|
|View.EdgeRightMoveLeft|**Ctrl+Maj+Alt+,**|
|View.EdgeRightMoveRight|**Ctrl+Maj+Alt+.**|
|View.ShowPropertyMarkerMenu|**Ctrl+Barre d’espace**|

##  <a name="xml-text-editor"></a>Éditeur XML (Texte)

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|XML.StartXSLTDebugging|**Alt+F5**|
|XML.StartXSLTWithoutDebugging|**Ctrl+Alt+F5**|

##  <a name="xml-schema-designer"></a>Concepteur de schémas XML

|Commandes|Raccourcis clavier|
|--------------|------------------------|
|GraphView.BottomtoTop|**Alt+Haut**|
|GraphView.LefttoRight|**Alt+Droite**|
|GraphView.RighttoLeft|**Alt+Gauche**|
|GraphView.ToptoBottom|**Alt+Bas**|
|OtherContextMenus.GraphView.RemovefromWorkspace|**Supprimer**|
|XsdDesigner.ShowContentModelView|**Ctrl+2**|
|XsdDesigner.ShowGraphView|**Ctrl+3**|
|XsdDesigner.ShowStartView|**Ctrl+1**|

## <a name="see-also"></a>Voir aussi

- [Éditeur d’images pour les icônes](/cpp/windows/image-editor-for-icons)
- [Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)