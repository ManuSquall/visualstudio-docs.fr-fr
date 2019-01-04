---
title: GUID et ID des Menus de Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3c2990e7002a75dfb5868a4079d889c08e49c3c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906941"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Menus de GUID et ID de Visual Studio
Cet article énumère les valeurs GUID et l’ID des menus et des groupes dans la barre de menus de Visual Studio. Ces valeurs sont définies dans *.vsct* fichiers qui sont installés dans le cadre du SDK Visual Studio. Pour plus d’informations, consultez [commandes définies par l’IDE, les menus et les groupes](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Pour plus d’informations sur la façon de travailler avec des objets d’environnement (IDE) de développement intégré qui sont définies dans *.vsct* de fichiers, consultez [étendre des menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les menus et les groupes dans la barre de menus de Visual Studio utilisent le GUID `guidSHLMainMenu`. Le menu de barre lui-même a un ID de `IDM_VS_TOOL_MAINMENU`.  
  
## <a name="groups-on-the-visual-studio-menu-bar"></a>Groupes dans la barre de menus de Visual Studio  
 Pour ajouter un menu à la barre de menus, définissez un de ces groupes comme son parent.  
  
|Regrouper|Id|  
|-----------|--------|  
|Fichier/Modifier/afficher|IDG_VS_MM_FILEEDITVIEW|  
|Refactorisation|IDG_VS_MM_REFACTORING :|  
|Projet|IDG_VS_MM_PROJECT|  
|Build|IDG_VS_MM_BUILDDEBUGRUN|  
|Format/Tools|IDG_VS_MM_TOOLSADDINS|  
|Fenêtre/Help/Community|IDG_VS_MM_WINDOWHELP|  
|Compléments|IDG_VS_MM_MACROS|  
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|  
  
## <a name="menus-on-the-visual-studio-menu-bar"></a>Menus dans la barre de menus de Visual Studio  
 Pour ajouter un groupe à un menu de Visual Studio existant, définissez un des menus suivants en tant que son parent. Sous-menus ne sont pas inclus dans cette liste.  
  
|Menu|Id|  
|----------|--------|  
|Fichier|IDM_VS_MENU_FILE|  
|Modifier|IDM_VS_MENU_EDIT|  
|Vue|IDM_VS_MENU_VIEW|  
|Réorganiser|IDM_VS_MENU_REFACTORING|  
|Projet|IDM_VS_MENU_PROJECT|  
|Build|IDM_VS_MENU_BUILD|  
|Format|IDM_VS_MENU_FORMAT|  
|Outils|IDM_VS_MENU_TOOLS|  
|Fenêtre|IDM_VS_MENU_WINDOW|  
|Compléments|IDM_VS_MENU_ADDINS|  
|Communauté|IDM_VS_MENU_COMMUNITY|  
|Help|IDM_VS_MENU_HELP|  
  
## <a name="groups-on-visual-studio-menus"></a>Groupes dans les menus de Visual Studio  
 Les listes suivantes présentent les groupes qui descendent directement à partir des menus dans la barre de menus de Visual Studio. Le moyen le plus rapide pour ajouter une commande à un menu de Visual Studio consiste à définir un de ces groupes en tant que parent. Les groupes qui descendent des sous-menus n’apparaissent pas dans cette section.  
  
### <a name="file-menu-groups"></a>Groupes de menus de fichier  
  
|Regrouper|Id|  
|-----------|--------|  
|Nouveau ouvert /|IDG_VS_FILE_FILE|  
|Ajouter|IDG_VS_FILE_ADD|  
|Solution|IDG_VS_FILE_SOLUTION|  
|Divers|IDG_VS_FILE_MISC|  
|Enregistrer|IDG_VS_FILE_SAVE|  
|Renommer|IDG_VS_FILE_RENAME|  
|Visiteur|IDG_VS_FILE_BROWSER|  
|Imprimer|IDG_VS_FILE_PRINT|  
|Utilisés le plus récemment|IDG_VS_FILE_MRU|  
|Déplacement|IDG_VS_FILE_MOVE|  
|Exit|IDG_VS_FILE_EXIT|  
  
### <a name="edit-menu-groups"></a>Modifier les groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Annuler/Rétablir|IDG_VS_EDIT_UNDOREDO|  
|Couper/copier/coller|IDG_VS_EDIT_CUTCOPY|  
|Sélectionner|IDG_VS_EDIT_SELECT|  
|GoTo|IDG_VS_EDIT_GOTO|  
|Find|IDG_VS_EDIT_FIND|  
|Objets|IDG_VS_EDIT_OBJECTS|  
|Verbes OLE|IDG_VS_EDIT_OLEVERBS|  
|Commande bien|IDG_VS_EDIT_COMMANDWELL|  
  
### <a name="refactor-menu-groups"></a>Refactoriser les groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Communes|IDG_REFACTORING_COMMON|  
|Avancé|IDG_REFACTORING_ADVANCED|  
  
### <a name="view-menu-groups"></a>Afficher les groupes de menu  
  
|Regrouper|Id|  
|-----------|--------|  
|Code du formulaire|IDG_VS_VIEW_FORMCODE|  
|Visiteur|IDG_VS_VIEW_BROWSER|  
|Définir des vues|IDG_VS_VIEW_DEFINEVIEWS|  
|Windows|IDG_VS_VIEW_WINDOWS|  
|L’architecture de Windows|IDG_VS_VIEW_ARCH_WINDOWS|  
|Organisation Windows|IDG_VS_VIEW_ORG_WINDOWS|  
|Explorateur de code|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|  
|Développement Windows|IDG_VS_VIEW_DEV_WINDOWS|  
|Barres d'outils|IDG_VS_VIEW_TOOLBARS|  
|Symbols|IDG_VS_VIEW_SYMBOLNAVIGATE|  
|Accédez|IDG_VS_VIEW_NAVIGATE|  
|Accédez petit|IDG_VS_VIEW_SMALLNAVIGATE|  
|Explorateur d'objets|IDG_VS_VIEW_OBJBRWSR|  
|Commande bien|IDG_VS_VIEW_COMMANDWELL|  
|Pages de propriétés|IDG_VS_VIEW_PROPPAGES|  
|Actualisation|IDG_VS_VIEW_REFRESH|  
  
### <a name="project-menu-groups"></a>Groupes de menus de projet  
  
|Regrouper|Id|  
|-----------|--------|  
|Divers ajouter|IDG_VS_PROJ_MISCADD|  
|Ajouter|IDG_VS_PROJ_ADD|  
|Dossier|IDG_VS_PROJ_FOLDER|  
|Déchargement/rechargement|IDG_VS_PROJ_UNLOADRELOAD|  
|Référence|IDG_VS_PROJ_REFERENCE|  
|Options|IDG_VS_PROJ_OPTIONS|  
|Paramètres|IDG_VS_PROJ_SETTINGS|  
  
### <a name="build-menu-groups"></a>Créer des groupes de menus  
  
|Regrouper|Id|  
|-----------|--------|  
|Solution|IDG_VS_BUILD_SOLUTION|  
|Sélection|IDG_VS_BUILD_SELECTION|  
|Optimisation guidée par profil|IDG_VS_PGO_SELECTION|  
|Divers|IDG_VS_BUILD_MISC|  
|Annuler|IDG_VS_BUILD_CANCEL|  
  
### <a name="tools-menu-groups"></a>Groupes de menus d’outils  
  
|Regrouper|Id|  
|-----------|--------|  
|Ligne de commande|IDG_VS_TOOLS_CMDLINE|  
|Extraits de code|IDG_VS_TOOLS_SNIPPETS|  
|Sous-ensemble de l’objet|IDG_VS_TOOLS_OBJSUBSET|  
|Options|IDG_VS_TOOLS_OPTIONS|  
|Autres 2|IDG_VS_TOOLS_OTHER2|  
|Outils externes|IDG_VS_TOOLS_EXT_TOOLS|  
|Personnalisations externes|IDG_VS_TOOLS_EXT_CUST|  
  
### <a name="window-menu-groups"></a>Groupes de menus de fenêtre  
  
|Regrouper|Id|  
|-----------|--------|  
|Nouveau|IDG_VS_WINDOW_NEW|  
|Ancrage/de fermeture|IDG_VS_DOCKCLOSE|  
|Ancrage/masquer|IDG_VS_DOCKHIDE|  
|Organiser|IDG_VS_WINDOW_ARRANGE|  
|Navigation|IDG_VS_WINDOW_NAVIGATION|  
|Liste|IDG_VS_WINDOW_LIST|  
  
### <a name="help-menu-groups"></a>Groupes de menus aide  
  
|Regrouper|Id|  
|-----------|--------|  
|Exemples|IDG_VS_HELP_SAMPLES|  
|Assistance|IDG_VS_HELP_SUPPORT|  
|À propos de|IDG_VS_HELP_ABOUT|  
  
## <a name="submenus-of-visual-studio-menus"></a>Sous-menus des menus de Visual Studio  
 La hiérarchie suivante montre les sous-menus qui sont associés les menus dans la barre de menus de Visual Studio. Comme un seul groupe peut avoir un menu en tant que son parent, chaque sous-menu doit descendent d’un groupe dans un menu, au lieu de directement à partir du menu. Pour plus d’informations sur la relation entre les menus, des groupes et des sous-menus, consultez [ajouter un sous-menu à un menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Les noms des menus dans la barre de menus de Visual Studio séparément ne figurent pas dans cette hiérarchie, car ils peuvent être déduits à partir de la convention d’affectation de noms pour les groupes dans l’IDE, comme suit : *IDG_VS_\<nom de Menu\>_\<nom du groupe\>*.  
  
|Groupe parent|Sous-menu|Groupes enfants|  
|------------------|-------------|------------------|  
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|  
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|  
|||IDG_VS_FILE_OPENF_CASCADE|  
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|  
|||IDG_VS_FILE_ADD_PROJECT_EXI|  
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|  
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|  
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|  
|||IDG_VS_FILE_MOVE_PICKER|  
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|  
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|  
|||IDG_VS_WNDO_OTRWNDWS1... 6|  
|||IDG_VS_WNDO_WINDOWS2|  
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||  
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||  
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|  
|||IDG_VS_MNUDES_EDITNAMES|  
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|  
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|  
|||IDG_VS_BUILD_PROJPICKER|  
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|  
|||IDG_VS_REBUILD_PROJPICKER|  
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|  
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|  
|||IDG_VS_CLEAN_PROJPICKER|  
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|  
|||IDG_VS_DEPLOY_PROJPICKER|  
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|  
|||IDG_VS_PGO_BUILD_CASCADE_RUN|  
  
## <a name="see-also"></a>Voir aussi  
 [Barres d’outils de GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [Commandes de GUID et ID de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Visual Studio fichiers command table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)