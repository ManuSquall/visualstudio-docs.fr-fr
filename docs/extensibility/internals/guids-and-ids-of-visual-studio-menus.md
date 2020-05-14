---
title: GUIDs et IDs de Visual Studio Menus (fr) Microsoft Docs
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a656d5cb9a126a9dc3988d70a290fceb3e56439e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708241"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>GUIDs et IDs des menus Visual Studio
Cet article énumère les valeurs GUID et ID des menus et des groupes sur le menu Visual Studio bar. Ces valeurs sont définies dans des fichiers *.vsct* qui sont installés dans le cadre du Visual Studio SDK. Pour plus d’informations, consultez les [commandes, les menus et les groupes définis par l’IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Pour plus d’informations sur la façon de travailler avec des objets intégrés de l’environnement de développement (IDE) qui sont définis dans des fichiers *.vsct,* voir [Les menus et les commandes Extend](../../extensibility/extending-menus-and-commands.md).

 Les menus et les groupes du menu `guidSHLMainMenu`Visual Studio utilisent le GUID . Le menu bar lui-même a une carte d’identité de `IDM_VS_TOOL_MAINMENU`.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Groupes sur le menu Visual Studio bar
 Pour ajouter un menu à la barre de menu, placez l’un de ces groupes comme parent.

|Groupe|id|
|-----------|--------|
|Fichier/Edit/View|IDG_VS_MM_FILEEDITVIEW|
|Refactorisation|IDG_VS_MM_REFACTORING:|
|Projet|IDG_VS_MM_PROJECT|
|Générer|IDG_VS_MM_BUILDDEBUGRUN|
|Format/Outils|IDG_VS_MM_TOOLSADDINS|
|Fenêtre/Aide/Communauté|IDG_VS_MM_WINDOWHELP|
|Logiciels enfichables|IDG_VS_MM_MACROS|
|FullScreenBar (fullScreenBar)|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Menus au menu Visual Studio bar
 Pour ajouter un groupe à un menu Visual Studio existant, définissez l’un des menus suivants comme parent. Submenus ne sont pas inclus dans cette liste.

|Menu|id|
|----------|--------|
|Fichier|IDM_VS_MENU_FILE|
|Modifier|IDM_VS_MENU_EDIT|
|Vue|IDM_VS_MENU_VIEW|
|Refactorisation|IDM_VS_MENU_REFACTORING|
|Projet|IDM_VS_MENU_PROJECT|
|Générer|IDM_VS_MENU_BUILD|
|Format|IDM_VS_MENU_FORMAT|
|Outils|IDM_VS_MENU_TOOLS|
|Extensions|IDM_VS_MENU_EXTENSIONS|
|Fenêtre|IDM_VS_MENU_WINDOW|
|Logiciels enfichables|IDM_VS_MENU_ADDINS|
|Communauté|IDM_VS_MENU_COMMUNITY|
|Aide|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Groupes sur les menus Visual Studio
 Les listes suivantes montrent les groupes qui descendent directement des menus du menu Visual Studio bar. La façon la plus rapide d’ajouter une commande à un menu Visual Studio est de définir l’un de ces groupes comme le parent. Les groupes qui descendent de sous-genre n’apparaissent pas dans cette section.

### <a name="file-menu-groups"></a>Groupes de menu de fichiers

|Groupe|id|
|-----------|--------|
|Nouveau/Ouvert|IDG_VS_FILE_FILE|
|Ajouter|IDG_VS_FILE_ADD|
|Solution|IDG_VS_FILE_SOLUTION|
|Divers|IDG_VS_FILE_MISC|
|Enregistrer|IDG_VS_FILE_SAVE|
|Renommer|IDG_VS_FILE_RENAME|
|Browser|IDG_VS_FILE_BROWSER|
|Print|IDG_VS_FILE_PRINT|
|Plus récemment utilisé|IDG_VS_FILE_MRU|
|Déplacer|IDG_VS_FILE_MOVE|
|Quitter|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>Modifier les groupes de menu

|Groupe|id|
|-----------|--------|
|Annuler/Rétablir|IDG_VS_EDIT_UNDOREDO|
|Coupe/Copie/Pâte|IDG_VS_EDIT_CUTCOPY|
|Sélectionnez|IDG_VS_EDIT_SELECT|
|Goto|IDG_VS_EDIT_GOTO|
|Rechercher|IDG_VS_EDIT_FIND|
|Objets|IDG_VS_EDIT_OBJECTS|
|Verbes OLE|IDG_VS_EDIT_OLEVERBS|
|Commandez bien|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>Groupes de menu Refactor

|Groupe|id|
|-----------|--------|
|Courant|IDG_REFACTORING_COMMON|
|Avancé|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>Afficher les groupes de menu

|Groupe|id|
|-----------|--------|
|Code de formulaire|IDG_VS_VIEW_FORMCODE|
|Browser|IDG_VS_VIEW_BROWSER|
|Définir Vues|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Architecte Windows|IDG_VS_VIEW_ARCH_WINDOWS|
|Fenêtres de l’organisation|IDG_VS_VIEW_ORG_WINDOWS|
|Navigateur de code|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|Barres d'outils|IDG_VS_VIEW_TOOLBARS|
|Symboles|IDG_VS_VIEW_SYMBOLNAVIGATE|
|Naviguer|IDG_VS_VIEW_NAVIGATE|
|Petite navigation|IDG_VS_VIEW_SMALLNAVIGATE|
|Explorateur d'objets|IDG_VS_VIEW_OBJBRWSR|
|Commandez bien|IDG_VS_VIEW_COMMANDWELL|
|Pages de propriétés|IDG_VS_VIEW_PROPPAGES|
|Actualiser|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>Groupes de menu de projets

|Groupe|id|
|-----------|--------|
|Divers Ajouter|IDG_VS_PROJ_MISCADD|
|Ajouter|IDG_VS_PROJ_ADD|
|Dossier|IDG_VS_PROJ_FOLDER|
|Déchargement/rechargement|IDG_VS_PROJ_UNLOADRELOAD|
|Informations de référence|IDG_VS_PROJ_REFERENCE|
|Options|IDG_VS_PROJ_OPTIONS|
|Paramètres|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>Construire des groupes de menu

|Groupe|id|
|-----------|--------|
|Solution|IDG_VS_BUILD_SOLUTION|
|Sélection|IDG_VS_BUILD_SELECTION|
|Optimisation guidée par profil|IDG_VS_PGO_SELECTION|
|Divers|IDG_VS_BUILD_MISC|
|Annuler|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>Groupes de menu d’outils

|Groupe|id|
|-----------|--------|
|Ligne de commande|IDG_VS_TOOLS_CMDLINE|
|Extraits de code|IDG_VS_TOOLS_SNIPPETS|
|Sous-ensemble d’objets|IDG_VS_TOOLS_OBJSUBSET|
|Options|IDG_VS_TOOLS_OPTIONS|
|Autres 2|IDG_VS_TOOLS_OTHER2|
|Outils externes|IDG_VS_TOOLS_EXT_TOOLS|
|Personnalisations externes|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>Groupes de menu de fenêtre

|Groupe|id|
|-----------|--------|
|Nouveau|IDG_VS_WINDOW_NEW|
|Dock/Fermer|IDG_VS_DOCKCLOSE|
|Dock/Hide|IDG_VS_DOCKHIDE|
|Réorganiser|IDG_VS_WINDOW_ARRANGE|
|Navigation|IDG_VS_WINDOW_NAVIGATION|
|List|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>Aide aux groupes de menu

|Groupe|id|
|-----------|--------|
|Exemples|IDG_VS_HELP_SAMPLES|
|Support|IDG_VS_HELP_SUPPORT|
|À propos|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Sous-présage des menus Visual Studio
 La hiérarchie suivante montre le sous-genre qui sont associés aux menus du menu Visual Studio bar. Parce que seul un groupe peut avoir un menu en tant que parent, chaque sous-mois doit descendre d’un groupe sur un menu, au lieu de directement à partir du menu. Pour plus d’informations sur la relation entre les menus, les groupes et les sous-hommes, voir [Ajouter un sous-mois à un menu](../../extensibility/adding-a-submenu-to-a-menu.md).

> [!NOTE]
> Les noms des menus de la barre de menu Visual Studio ne sont pas indiqués séparément dans cette hiérarchie car ils peuvent être déduits de la convention de nommage pour les groupes de l’IDE, comme suit: *\<IDG_VS_ Nom\>du menu -\<Nom\>de groupe*.

|Groupe parent|Sous-menu|Groupes d’enfants|
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
- [GUIDs et IDs des barres d’outils Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [GUIDs et IDs des commandes Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Fichiers visualister de table de commande de studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
