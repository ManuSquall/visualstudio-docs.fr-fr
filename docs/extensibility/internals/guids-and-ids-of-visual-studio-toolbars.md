---
title: GUID et ID des barres d’outils de Visual Studio | Microsoft Docs
description: Affichez une liste de valeurs GUID et ID pour les barres d’outils et les groupes qu’ils contiennent, qui sont inclus dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3d2ba6c92a2913ec63a59751a4181454aa67fa67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898108"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID et ID des barres d’outils de Visual Studio
Cette rubrique énumère les valeurs GUID et ID des barres d’outils incluses dans l’environnement de développement intégré (IDE) de Visual Studio et des groupes qu’ils contiennent. Ces valeurs sont définies dans les fichiers *. vsct* installés dans le cadre du kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> La plupart des barres d’outils disponibles pour Visual Studio ne sont pas définies par Visual Studio, et leurs valeurs GUID et ID ne sont pas publiques. Cette rubrique répertorie uniquement les barres d’outils qui sont définies dans les fichiers *. vsct* du SDK Visual Studio.

 Pour plus d’informations sur l’utilisation des objets IDE définis dans des fichiers *. vsct* , consultez [étendre des menus et des commandes](../../extensibility/extending-menus-and-commands.md).

 Les barres d’outils par défaut fournies par l’IDE de Visual Studio utilisent le GUID `guidSHLMainMenu` , sauf spécification contraire à l’aide de la `GUID:ID` syntaxe.

## <a name="ide-toolbars"></a>Barres d’outils IDE
 Les barres d’outils suivantes sont fournies par l’IDE de Visual Studio. Vous pouvez afficher les barres d’outils en les sélectionnant dans le sous-menu **barres** d’outils du menu **Outils** . Les barres d’outils des fenêtres outil ne sont pas incluses dans cette section.

 Seuls les groupes peuvent être directement issus des barres d’outils. Pour ajouter un groupe, affectez à son parent le GUID et l’ID de la barre d’outils. Pour ajouter un bouton à une barre d’outils, définissez son parent sur un groupe dans la barre d’outils.

|Barre d’outils|id|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Build|IDM_VS_TOOL_BUILD|
|Éditeur de texte|IDM_VS_TOOL_TEXTEDITOR|
|Débogage|guidVSDebugGroup : IDM_DEBUG_TOOLBAR|
|Emplacement de débogage|guidVSDebugGroup : IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Barres d’outils spéciales
 Ces barres d’outils sont définies par l’IDE de Visual Studio, mais elles servent des fonctions spécialisées et n’hébergent pas de groupes de commandes.

|Barre d’outils|id|
|-------------|--------|
|Add, commande|IDM_VS_TOOL_ADDCOMMAND|
|Indéfini|IDM_VS_TOOL_UNDEFINED|
|schéma XML|IDM_VS_TOOL_SCHEMA|
|données XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Groupes sur les barres d’outils de l’IDE
 Pour ajouter un bouton à une barre d’outils standard, définissez l’un des groupes suivants en tant que parent. Les groupes sont triés par barre d’outils parente.

### <a name="standard-toolbar-groups"></a>Groupes de barres d’outils standard

|Nom|id|
|----------|--------|
|Enregistrer/ouvrir|IDG_VS_TOOLSB_SAVEOPEN|
|Couper/copier|IDG_VS_TOOLSB_CUTCOPY|
|Annuler/Rétablir|IDG_VS_TOOLSB_UNDOREDO|
|Exécuter/générer|IDG_VS_TOOLSB_RUNBUILD|
|Recherche|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nouvelles fenêtres|IDG_VS_TOOLSB_NEWWINDOWS|
|Charger/enregistrer|IDG_VS_WINDOWUI_LOADSAVE|
|Jauge|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Créer des groupes de barres d’outils

|Nom|id|
|----------|--------|
|Barre de génération|IDG_VS_BUILDBAR|
|Annuler|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Groupes de barres d’outils de l’éditeur de texte

|Nom|id|
|----------|--------|
|Completion|IDM_VS_TOOL_TEXTEDITOR|
|Retrait|IDG_VS_EDITTOOLBAR_INDENT|
|Commentaire|IDG_VS_EDITTOOLBAR_COMMENT|
|Signets|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Déboguer les groupes de barres d’outils

|Nom|id|
|----------|--------|
|Exécution|IDM_DEBUG_TOOLBAR|
|Exécution pas à pas|IDG_DEBUG_TOOLBAR_STEPPING|
|Espion|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Groupes de barres d’outils d’emplacement de débogage

|Nom|id|
|----------|--------|
|Emplacement de débogage|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Barres d’outils des fenêtres Outil
 Les barres d’outils peuvent apparaître directement dans l’IDE ou dans les fenêtres outil, telles que **Explorateur de solutions**. Étant donné que les fenêtres outil ne sont pas définies dans les fichiers *. vsct* , les barres d’outils de fenêtre outil n’ont pas de parents définis. Au lieu de cela, ils sont placés dans le code. Le tableau suivant répertorie les barres d’outils qui s’affichent sur les fenêtres outil dans l’IDE et les groupes de commandes qu’elles contiennent.

> [!NOTE]
> Les barres d’outils et les groupes utilisent le GUID `guidSHLMainMenu` , sauf spécification contraire à l’aide de la syntaxe GUID : ID. Lorsqu’un GUID est spécifié pour une barre d’outils, il s’applique également aux groupes qui descendent de cette barre d’outils.

|Fenêtre outil|Barre d’outils|Groupes|
|-----------------|-------------|------------|
|Explorateur de solutions|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1.. 5,5|
|Explorateur de serveurs|guid_SE_MenuGroup : IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Propriétés|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Explorateur d'objets|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Explorateur d'objets|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Sortie|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Rechercher et remplacer|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Résultats de la recherche 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Résultats de la recherche 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Extrait|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Signets|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Liste des tâches|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Tâches utilisateur|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Liste d'erreurs|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Explorateur d'appels|IDM_VS_TOOL_CALLBROWSER1.. 16bits|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Points d’arrêt|guidVSDebugGroup : IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Code Machine|guidVSDebugGroup : IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Mémoire 1-4|guidVSDebugGroup : IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1.. 4<br /><br /> IDG_MEMORY_COLUMNS1.. 4|
|Processus|guidVSDebugGroup : IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Voir aussi
- [Ajouter un contrôleur de menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [Ajouter une barre d’outils à une fenêtre outil](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
