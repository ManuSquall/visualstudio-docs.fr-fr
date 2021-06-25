---
title: GUID et ID des menus Visual Studio | Microsoft Docs
description: Affichez la liste des valeurs GUID et ID des menus et des groupes dans la barre de menus de Visual Studio incluse dans l’environnement de développement intégré (IDE) de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bceee5fce8a77ad5169020bd3d21896bdbc71443
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898069"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUID et ID des menus Visual Studio
Cet article énumère les valeurs GUID et ID des menus et des groupes dans la barre de menus de Visual Studio. Ces valeurs sont définies dans les fichiers *. vsct* installés dans le cadre du kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [commandes, menus et groupes définis par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Pour plus d’informations sur l’utilisation des objets de l’environnement de développement intégré (IDE) définis dans les fichiers *. vsct* , consultez [étendre des menus et des commandes](../../extensibility/extending-menus-and-commands.md).

 Les menus et les groupes de la barre de menus de Visual Studio utilisent le GUID `guidSHLMainMenu` . La barre de menus elle-même a un ID de `IDM_VS_TOOL_MAINMENU` .

## <a name="groups-on-the-visual-studio-menu-bar"></a>Groupes dans la barre de menus de Visual Studio
 Pour ajouter un menu à la barre de menus, définissez l’un de ces groupes comme parent.

|Group|id|
|-----------|--------|
|Fichier/Modifier/afficher|IDG_VS_MM_FILEEDITVIEW|
|Refactorisation|IDG_VS_MM_REFACTORING :|
|Project|IDG_VS_MM_PROJECT|
|Build|IDG_VS_MM_BUILDDEBUGRUN|
|Format/outils|IDG_VS_MM_TOOLSADDINS|
|Fenêtre/aide/communauté|IDG_VS_MM_WINDOWHELP|
|Logiciels enfichables|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menus de la barre de menus de Visual Studio
 Pour ajouter un groupe à un menu Visual Studio existant, définissez l’un des menus suivants comme parent. Les sous-menus ne sont pas inclus dans cette liste.

|Menu|id|
|----------|--------|
|Fichier|IDM_VS_MENU_FILE|
|Modifier|IDM_VS_MENU_EDIT|
|Affichage|IDM_VS_MENU_VIEW|
|Refactorisation|IDM_VS_MENU_REFACTORING|
|Project|IDM_VS_MENU_PROJECT|
|Build|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Outils|IDM_VS_MENU_TOOLS|
|Extensions|IDM_VS_MENU_EXTENSIONS|
|Fenêtre|IDM_VS_MENU_WINDOW|
|Logiciels enfichables|IDM_VS_MENU_ADDINS|
|Communauté|IDM_VS_MENU_COMMUNITY|
|Aide|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Groupes dans les menus Visual Studio
 Les listes suivantes affichent les groupes qui descendent directement des menus de la barre de menus de Visual Studio. La façon la plus rapide d’ajouter une commande à un menu Visual Studio consiste à définir l’un de ces groupes comme parent. Les groupes qui descendent des sous-menus n’apparaissent pas dans cette section.

### <a name="file-menu-groups"></a>Groupes de menus de fichiers

|Group|id|
|-----------|--------|
|Nouveau/ouvrir|IDG_VS_FILE_FILE|
|Ajouter|IDG_VS_FILE_ADD|
|Solution|IDG_VS_FILE_SOLUTION|
|Divers|IDG_VS_FILE_MISC|
|Enregistrer|IDG_VS_FILE_SAVE|
|Renommer|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Impression|IDG_VS_FILE_PRINT|
|Utilisé le plus récemment|IDG_VS_FILE_MRU|
|Déplacer|IDG_VS_FILE_MOVE|
|Quitter|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modifier les groupes de menus

|Group|id|
|-----------|--------|
|Annuler/Rétablir|IDG_VS_EDIT_UNDOREDO|
|Couper/copier/coller|IDG_VS_EDIT_CUTCOPY|
|Sélectionnez|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Rechercher|IDG_VS_EDIT_FIND|
|Objets|IDG_VS_EDIT_OBJECTS|
|Verbes OLE|IDG_VS_EDIT_OLEVERBS|
|Commande|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Refactoriser les groupes de menus

|Group|id|
|-----------|--------|
|Courant|IDG_REFACTORING_COMMON|
|Avancé|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Afficher les groupes de menus

|Group|id|
|-----------|--------|
|Code du formulaire|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Définir des vues|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architecture des fenêtres|IDG_VS_VIEW_ARCH_WINDOWS|
|Fenêtres de l’Organisation|IDG_VS_VIEW_ORG_WINDOWS|
|Explorateur de code|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Fenêtres de développement|IDG_VS_VIEW_DEV_WINDOWS|
|Barres d'outils|IDG_VS_VIEW_TOOLBARS|
|symboles|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Naviguer|IDG_VS_VIEW_NAVIGATE|
|Navigation réduite|IDG_VS_VIEW_SMALLNAVIGATE|
|Explorateur d'objets|IDG_VS_VIEW_OBJBRWSR|
|Commande|IDG_VS_VIEW_COMMANDWELL|
|Pages de propriétés|IDG_VS_VIEW_PROPPAGES|
|Actualiser|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Groupes de menus de projet

|Group|id|
|-----------|--------|
|Ajouter divers|IDG_VS_PROJ_MISCADD|
|Ajouter|IDG_VS_PROJ_ADD|
|Dossier|IDG_VS_PROJ_FOLDER|
|Déchargement/rechargement|IDG_VS_PROJ_UNLOADRELOAD|
|Informations de référence|IDG_VS_PROJ_REFERENCE|
|Options|IDG_VS_PROJ_OPTIONS|
|Paramètres|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Groupes de menus de génération

|Group|id|
|-----------|--------|
|Solution|IDG_VS_BUILD_SOLUTION|
|Sélection|IDG_VS_BUILD_SELECTION|
|Optimisation guidée par profil|IDG_VS_PGO_SELECTION|
|Divers|IDG_VS_BUILD_MISC|
|Annuler|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Groupes de menus outils

|Group|id|
|-----------|--------|
|Ligne de commande|IDG_VS_TOOLS_CMDLINE|
|Extraits de code|IDG_VS_TOOLS_SNIPPETS|
|Sous-ensemble d’objets|IDG_VS_TOOLS_OBJSUBSET|
|Options|IDG_VS_TOOLS_OPTIONS|
|Autre 2|IDG_VS_TOOLS_OTHER2|
|Outils externes|IDG_VS_TOOLS_EXT_TOOLS|
|Personnalisations externes|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Groupes de menus de la fenêtre

|Group|id|
|-----------|--------|
|Nouveau|IDG_VS_WINDOW_NEW|
|Ancrer/fermer|IDG_VS_DOCKCLOSE|
|Ancrer/masquer|IDG_VS_DOCKHIDE|
|Réorganiser|IDG_VS_WINDOW_ARRANGE|
|Navigation|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Groupes du menu aide

|Group|id|
|-----------|--------|
|Exemples|IDG_VS_HELP_SAMPLES|
|Support|IDG_VS_HELP_SUPPORT|
|À propos de|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sous-menus des menus de Visual Studio
 La hiérarchie suivante montre les sous-menus associés aux menus de la barre de menus de Visual Studio. Étant donné que seul un groupe peut avoir un menu comme parent, chaque sous-menu doit être décroisé d’un groupe sur un menu, plutôt que directement à partir du menu. Pour plus d’informations sur la relation entre les menus, les groupes et les sous-menus, consultez [Ajouter un sous-menu à un menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Les noms des menus de la barre de menus de Visual Studio ne sont pas affichés séparément dans cette hiérarchie, car ils peuvent être déduits de la Convention d’affectation de noms pour les groupes dans l’IDE, comme suit : *IDG_VS_ \<Menu Name\> _ \<Group Name\>*.

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
|||IDG_VS_WNDO_OTRWNDWS1... 6,3|
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
- [GUID et ID des barres d’outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUID et ID des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Fichiers de table de commandes Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
