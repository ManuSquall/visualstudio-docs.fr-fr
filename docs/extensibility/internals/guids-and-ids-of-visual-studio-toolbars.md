---
title: GUID et ID de barres d’outils Visual Studio | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 394e0991d734279879df89422ac23fdd26899eeb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133985"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>GUID et ID de barres d’outils de Visual Studio
Cette rubrique énumère les valeurs GUID et l’ID de barres d’outils qui sont inclus dans l’environnement de développement intégré (IDE) Visual Studio, et des groupes qu’ils contiennent. Ces valeurs sont définies dans les fichiers .vsct qui sont installés dans le cadre du SDK Visual Studio. Pour plus d’informations, consultez [IDE-Defined commandes, Menus et des groupes](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  Nombre de barres d’outils disponibles pour Visual Studio ne sont pas définis par Visual Studio et leur GUID et les valeurs d’ID ne sont pas publics. Cette rubrique répertorie uniquement les barres d’outils qui sont définis dans les fichiers .vsct de kit de développement logiciel Visual Studio.  
  
 Pour plus d’informations sur la façon d’utiliser des objets IDE qui sont définis dans les fichiers .vsct, consultez [étendant les Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les barres d’outils par défaut fournis par l’IDE de Visual Studio utilisent le GUID `guidSHLMainMenu`, sauf indication contraire en utilisant la syntaxe de la paire GUID : ID.  
  
## <a name="ide-toolbars"></a>Barres d’outils de l’IDE  
 Les barres d’outils suivants sont fournis par l’IDE Visual Studio. Barres d’outils peuvent être affichés en les sélectionnant dans le **barres d’outils** sous-menu de la **outils** menu. Barres d’outils dans les fenêtres Outil ne sont pas incluses dans cette section.  
  
 Seuls les groupes peuvent descendre directement à partir de barres d’outils. Pour ajouter un groupe, définissez son parent pour le GUID et l’ID de la barre d’outils. Pour ajouter un bouton à une barre d’outils, définissez son parent à un groupe dans la barre d’outils.  
  
|ToolBar|Id|  
|-------------|--------|  
|Standard|IDM_VS_TOOL_STANDARD|  
|Générer|IDM_VS_TOOL_BUILD|  
|Éditeur de texte|IDM_VS_TOOL_TEXTEDITOR|  
|Débogage|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|  
|Emplacement de débogage|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|  
  
### <a name="special-toolbars"></a>Barres d’outils spéciaux  
 Ces barres d’outils sont définis par l’IDE de Visual Studio, mais elles remplissent des fonctions spécialisées et n’hébergent pas les groupes de commandes.  
  
|ToolBar|Id|  
|-------------|--------|  
|Ajouter une commande|IDM_VS_TOOL_ADDCOMMAND|  
|Undefined|IDM_VS_TOOL_UNDEFINED|  
|Schéma XML|IDM_VS_TOOL_SCHEMA|  
|Données XML|IDM_VS_TOOL_DATA|  
  
## <a name="groups-on-the-ide-toolbars"></a>Groupes sur les barres d’outils de l’IDE  
 Pour ajouter un bouton à une barre d’outils standard, définir l’un des groupes suivants en tant que son parent. Les groupes sont triés par la barre d’outils parente.  
  
### <a name="standard-toolbar-groups"></a>Groupes de la barre d’outils standard  
  
|Name|Id|  
|----------|--------|  
|Enregistrer/Ouvrir|IDG_VS_TOOLSB_SAVEOPEN|  
|Couper/copier|IDG_VS_TOOLSB_CUTCOPY|  
|Annuler/Rétablir|IDG_VS_TOOLSB_UNDOREDO|  
|Exécuter/Build|IDG_VS_TOOLSB_RUNBUILD|  
|Rechercher|IDG_VS_TOOLSB_SEARCH|  
|Windows|IDG_VS_TOOLSB_WINDOWS|  
|Nouvelles fenêtres|IDG_VS_TOOLSB_NEWWINDOWS|  
|Chargement / d’enregistrement|IDG_VS_WINDOWUI_LOADSAVE|  
|jauge|IDG_VS_TOOLSB_GAUGE|  
  
### <a name="build-toolbar-groups"></a>Créez des groupes de la barre d’outils  
  
|Name|Id|  
|----------|--------|  
|Barre de build|IDG_VS_BUILDBAR|  
|Annuler|IDG_VS_BUILD_CANCEL|  
  
### <a name="text-editor-toolbar-groups"></a>Groupes de la barre d’outils Éditeur de texte  
  
|Name|Id|  
|----------|--------|  
|Achèvement|IDM_VS_TOOL_TEXTEDITOR|  
|Retrait|IDG_VS_EDITTOOLBAR_INDENT|  
|Commentaire|IDG_VS_EDITTOOLBAR_COMMENT|  
|Signets|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|  
  
### <a name="debug-toolbar-groups"></a>Groupes de la barre d’outils de débogage  
  
|Name|Id|  
|----------|--------|  
|Exécution|IDM_DEBUG_TOOLBAR|  
|Exécution pas à pas|IDG_DEBUG_TOOLBAR_STEPPING|  
|Watch|IDG_DEBUG_TOOLBAR_WATCH|  
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|  
  
### <a name="debug-location-toolbar-groups"></a>Groupes de barre d’outils emplacement de débogage  
  
|Name|Id|  
|----------|--------|  
|Emplacement de débogage|IDG_DEBUG_CONTEXT_TOOLBAR|  
  
## <a name="tool-window-toolbars"></a>Barres d’outils de la fenêtre outil  
 Barres d’outils peuvent apparaître directement dans l’IDE ou dans les fenêtres Outil comme **l’Explorateur de solutions**. Étant donné que les fenêtres Outil ne sont pas définis dans les fichiers .vsct, barres d’outils de la fenêtre outil n’ont pas de parents définis. Au lieu de cela, ils sont placés dans le code. Le tableau suivant présente les barres d’outils qui s’affichent dans les fenêtres Outil dans l’IDE et les groupes de commandes qu’ils contiennent.  
  
> [!NOTE]
>  Barres d’outils et des groupes d’utiliser le GUID `guidSHLMainMenu`, sauf indication contraire en utilisant la syntaxe de la paire GUID : ID. Où un GUID est spécifié pour une barre d’outils, il s’applique également aux groupes qui descendent à partir de cette barre d’outils.  
  
|Fenêtre Outil|ToolBar|Groupes|  
|-----------------|-------------|------------|  
|Explorateur de solutions|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1... 5|  
|Explorateur de serveurs|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|  
|Propriétés|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|  
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|  
|Affichage de classes|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|  
|Explorateur d'objets|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|  
|Explorateur d'objets|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|  
|Sortie|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|  
|Rechercher et remplacer|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|  
|Rechercher les résultats 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|  
|Rechercher les résultats des 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|  
|Extrait de code|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|  
|Signets|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|  
|Liste des tâches|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|  
|Tâches utilisateur|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|  
|Liste d'erreurs|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|  
|Explorateur d'appels|IDM_VS_TOOL_CALLBROWSER1... 16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|  
|Points d’arrêt|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|  
|Code Machine|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|  
|Mémoire de 1 à 4|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1... 4|IDG_MEMORY_EXPRESSION1... 4<br /><br /> IDG_MEMORY_COLUMNS1... 4|  
|Processus|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un contrôleur de Menu à une barre d’outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Ajout d’une barre d’outils à une fenêtre outil](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID et ID des menus Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)