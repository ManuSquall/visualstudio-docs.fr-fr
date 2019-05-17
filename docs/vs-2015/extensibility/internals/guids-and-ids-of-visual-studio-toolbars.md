---
title: GUID et ID des barres d’outils | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6ec717707727b046ecd0d749179ea463ae3a4950
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436274"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID et ID des barres d’outils Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Cette rubrique énumère les valeurs GUID et l’ID de barres d’outils qui sont inclus dans l’environnement de développement intégré (IDE) Visual Studio, et des groupes qu’ils contiennent. Ces valeurs sont définies dans les fichiers .vsct qui sont installés dans le cadre du SDK Visual Studio. Pour plus d’informations, consultez [IDE-Defined commandes, Menus et les groupes](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

> [!NOTE]
> Grand nombre de barres d’outils disponibles pour Visual Studio ne sont pas définis par Visual Studio et leur GUID et les valeurs d’ID ne sont pas publics. Cette rubrique répertorie uniquement les barres d’outils qui sont définis dans les fichiers .vsct de Visual Studio SDK.

 Pour plus d’informations sur l’utilisation des objets d’IDE qui sont définis dans les fichiers .vsct, consultez [extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).

 Les barres d’outils par défaut fournis par l’IDE Visual Studio utilisent le GUID `guidSHLMainMenu`, sauf indication contraire à l’aide de syntaxe de la paire GUID : ID.

## <a name="ide-toolbars"></a>Barres d’outils IDE
 Les barres d’outils suivants sont fournis par l’IDE Visual Studio. Barres d’outils peuvent être affichées en les sélectionnant dans le **barres d’outils** sous-menu de la **outils** menu. Barres d’outils dans les fenêtres Outil ne sont pas inclus dans cette section.

 Seuls les groupes peuvent descendra directement à partir de barres d’outils. Pour ajouter un groupe, la valeur est son parent le GUID et l’ID de la barre d’outils. Pour ajouter un bouton à une barre d’outils, de définir son parent à un groupe dans la barre d’outils.

|ToolBar|Id|
|-------------|--------|
|Standard|IDM_VS_TOOL_STANDARD|
|Build|IDM_VS_TOOL_BUILD|
|Éditeur de texte|IDM_VS_TOOL_TEXTEDITOR|
|Débogage|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|Emplacement de débogage|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>Barres d’outils spéciaux
 Ces barres d’outils sont définies par l’IDE Visual Studio, mais ils remplissent des fonctions spécialisées et n’hébergent pas de groupes de commandes.

|ToolBar|Id|
|-------------|--------|
|Ajouter une commande|IDM_VS_TOOL_ADDCOMMAND|
|Undefined|IDM_VS_TOOL_UNDEFINED|
|Schéma XML|IDM_VS_TOOL_SCHEMA|
|Données XML|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>Groupes sur les barres d’outils IDE
 Pour ajouter un bouton à une barre d’outils standard, définissez un des groupes suivants en tant que son parent. Les groupes sont triés par la barre d’outils parent.

### <a name="standard-toolbar-groups"></a>Groupes de la barre d’outils standard

|Nom|Id|
|----------|--------|
|Enregistrer/Ouvrir|IDG_VS_TOOLSB_SAVEOPEN|
|Couper/copier|IDG_VS_TOOLSB_CUTCOPY|
|Annuler/Rétablir|IDG_VS_TOOLSB_UNDOREDO|
|Exécution/Build|IDG_VS_TOOLSB_RUNBUILD|
|Rechercher|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|Nouveau Windows|IDG_VS_TOOLSB_NEWWINDOWS|
|Charger/enregistrer|IDG_VS_WINDOWUI_LOADSAVE|
|Jauge|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>Créer des groupes de la barre d’outils

|Nom|Id|
|----------|--------|
|Barre de build|IDG_VS_BUILDBAR|
|Annuler|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>Groupes de la barre d’outils Éditeur de texte

|Nom|Id|
|----------|--------|
|Achèvement|IDM_VS_TOOL_TEXTEDITOR|
|Retrait|IDG_VS_EDITTOOLBAR_INDENT|
|Commentaire|IDG_VS_EDITTOOLBAR_COMMENT|
|Signets|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>Groupes de la barre d’outils de débogage

|Nom|Id|
|----------|--------|
|Exécution|IDM_DEBUG_TOOLBAR|
|Exécution pas à pas|IDG_DEBUG_TOOLBAR_STEPPING|
|Watch|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>Groupes de barre d’outils emplacement de débogage

|Nom|Id|
|----------|--------|
|Emplacement de débogage|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>Barres d’outils de la fenêtre outil
 Barres d’outils peuvent apparaître directement dans l’IDE ou dans les fenêtres outil tel que **l’Explorateur de solutions**. Étant donné que les fenêtres Outil ne sont pas définis dans les fichiers .vsct, barres d’outils de la fenêtre outil n’ont pas de parents définis. Au lieu de cela, ils sont placés dans le code. Le tableau suivant présente les barres d’outils qui apparaissent dans les fenêtres Outil dans l’IDE et les groupes de commandes qu’ils contiennent.

> [!NOTE]
> Barres d’outils et les groupes utilisent le GUID `guidSHLMainMenu`, sauf indication contraire à l’aide de syntaxe de la paire GUID : ID. Où un GUID est spécifié pour une barre d’outils, il s’applique également aux groupes qui descendent à partir de cette barre d’outils.

|Fenêtre Outil|ToolBar|Groupes|
|-----------------|-------------|------------|
|Explorateur de solutions|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1..5|
|Explorateur de serveurs|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|Properties|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|Explorateur d'objets|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|Explorateur d'objets|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|Sortie|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|Rechercher et remplacer|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|Résultats 1 de la recherche|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|Rechercher des résultats 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|Extrait de code|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|Signets|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|Liste des tâches|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|Tâches utilisateur|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|Liste d'erreurs|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|Explorateur d'appels|IDM_VS_TOOL_CALLBROWSER1..16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|Points d’arrêt|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|Code Machine|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|Mémoire 1-4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1…4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1..4|
|Processus|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>Voir aussi
 [Ajout d’un contrôleur de Menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md) [Ajout d’une barre d’outils à une fenêtre outil](../../extensibility/adding-a-toolbar-to-a-tool-window.md) [GUID et ID des Menus de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)
