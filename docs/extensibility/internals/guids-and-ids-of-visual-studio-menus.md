---
title: "GUID et ID de Menus de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menus de Visual studio"
  - "groupes de Visual studio"
  - "ID"
  - "menus existants"
  - "GUID"
  - "menus"
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# GUID et ID de Menus de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique énumère les valeurs GUID et l'ID des menus et des groupes dans la barre de menus de Visual Studio. Ces valeurs sont définies dans les fichiers .vsct sont installés en tant que partie du SDK Visual Studio. Pour plus d'informations, consultez [Groupes, les Menus et les commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Pour plus d'informations sur l'utilisation des objets de l'environnement \(IDE\) développement intégré qui sont définis dans les fichiers .vsct, consultez la page [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les menus et les groupes dans la barre de menus de Visual Studio utilisent le GUID `guidSHLMainMenu`. Le menu lui\-même a un ID `IDM_VS_TOOL_MAINMENU`.  
  
## Groupes sur la barre de menus de Visual Studio  
 Pour ajouter un menu à la barre de menus, définissez un de ces groupes en tant que son parent.  
  
|Regrouper|ID|  
|---------------|--------|  
|Affichage\/Modifier\/fichier|IDG\_VS\_MM\_FILEEDITVIEW|  
|Refactorisation|IDG\_VS\_MM\_REFACTORING :|  
|Projet|IDG\_VS\_MM\_PROJECT|  
|Build|IDG\_VS\_MM\_BUILDDEBUGRUN|  
|Format\/Tools|IDG\_VS\_MM\_TOOLSADDINS|  
|Fenêtre\/aide\/Communauté|IDG\_VS\_MM\_WINDOWHELP|  
|Compléments|IDG\_VS\_MM\_MACROS|  
|FullScreenBar|IDG\_VS\_MM\_FULLSCREENBAR|  
  
## Menus de la barre de menus de Visual Studio  
 Pour ajouter un groupe à un menu de Visual Studio existant, définissez un des menus suivants comme son parent. Sous\-menus ne sont pas inclus dans cette liste.  
  
|Menu|ID|  
|----------|--------|  
|Fichier|IDM\_VS\_MENU\_FILE|  
|Modifier|IDM\_VS\_MENU\_EDIT|  
|Afficher|IDM\_VS\_MENU\_VIEW|  
|Réorganiser|IDM\_VS\_MENU\_REFACTORING|  
|Projet|IDM\_VS\_MENU\_PROJECT|  
|Build|IDM\_VS\_MENU\_BUILD|  
|Format|IDM\_VS\_MENU\_FORMAT|  
|Outils|IDM\_VS\_MENU\_TOOLS|  
|Fenêtre|IDM\_VS\_MENU\_WINDOW|  
|Compléments|IDM\_VS\_MENU\_ADDINS|  
|Communauté|IDM\_VS\_MENU\_COMMUNITY|  
|Aide|IDM\_VS\_MENU\_HELP|  
  
## Groupes de Menus de Visual Studio  
 Les listes suivantes indiquent les groupes qui descendent directement à partir de menus dans la barre de menus de Visual Studio. Le plus rapide pour ajouter une commande à un menu de Visual Studio consiste à définir un de ces groupes en tant que parent. Groupes qui descendent des sous\-menus n'apparaissent pas dans cette section.  
  
### Menu groupes de fichiers  
  
|Regrouper|ID|  
|---------------|--------|  
|Nouveau\/ouvrir|IDG\_VS\_FILE\_FILE|  
|Ajouter|IDG\_VS\_FILE\_ADD|  
|Solution|IDG\_VS\_FILE\_SOLUTION|  
|Divers|IDG\_VS\_FILE\_MISC|  
|Save|IDG\_VS\_FILE\_SAVE|  
|Renommer|IDG\_VS\_FILE\_RENAME|  
|Visiteur|IDG\_VS\_FILE\_BROWSER|  
|Imprimer|IDG\_VS\_FILE\_PRINT|  
|Utilisés le plus récemment|IDG\_VS\_FILE\_MRU|  
|Déplacement|IDG\_VS\_FILE\_MOVE|  
|Quitter|IDG\_VS\_FILE\_EXIT|  
  
### Modifier les groupes de menus  
  
|Regrouper|ID|  
|---------------|--------|  
|Annuler\/Rétablir|IDG\_VS\_EDIT\_UNDOREDO|  
|Couper\/copier\/coller.|IDG\_VS\_EDIT\_CUTCOPY|  
|Sélectionner|IDG\_VS\_EDIT\_SELECT|  
|GoTo|IDG\_VS\_EDIT\_GOTO|  
|Find|IDG\_VS\_EDIT\_FIND|  
|d'entreprise|IDG\_VS\_EDIT\_OBJECTS|  
|Verbes OLE|IDG\_VS\_EDIT\_OLEVERBS|  
|Commande bien|IDG\_VS\_EDIT\_COMMANDWELL|  
  
### Refactoriser des groupes de menus  
  
|Regrouper|ID|  
|---------------|--------|  
|Communes|IDG\_REFACTORING\_COMMON|  
|Avancé|IDG\_REFACTORING\_ADVANCED|  
  
### Afficher les groupes de menus  
  
|Regrouper|ID|  
|---------------|--------|  
|Code du formulaire|IDG\_VS\_VIEW\_FORMCODE|  
|Visiteur|IDG\_VS\_VIEW\_BROWSER|  
|Définir des vues|IDG\_VS\_VIEW\_DEFINEVIEWS|  
|Windows|IDG\_VS\_VIEW\_WINDOWS|  
|Architecte Windows|IDG\_VS\_VIEW\_ARCH\_WINDOWS|  
|Organisation Windows|IDG\_VS\_VIEW\_ORG\_WINDOWS|  
|Explorateur de code|IDG\_VS\_VIEW\_CODEBROWSENAV\_WINDOWS|  
|Développement Windows|IDG\_VS\_VIEW\_DEV\_WINDOWS|  
|Barres d'outils|IDG\_VS\_VIEW\_TOOLBARS|  
|Symboles|IDG\_VS\_VIEW\_SYMBOLNAVIGATE|  
|Accédez|IDG\_VS\_VIEW\_NAVIGATE|  
|Accédez réduite|IDG\_VS\_VIEW\_SMALLNAVIGATE|  
|Explorateur d'objets|IDG\_VS\_VIEW\_OBJBRWSR|  
|Commande bien|IDG\_VS\_VIEW\_COMMANDWELL|  
|Pages de propriétés|IDG\_VS\_VIEW\_PROPPAGES|  
|Actualiser|IDG\_VS\_VIEW\_REFRESH|  
  
### Groupes de menus de projet  
  
|Regrouper|ID|  
|---------------|--------|  
|Divers ajouter|IDG\_VS\_PROJ\_MISCADD|  
|Ajouter|IDG\_VS\_PROJ\_ADD|  
|Dossier|IDG\_VS\_PROJ\_FOLDER|  
|Déchargement\/rechargement|IDG\_VS\_PROJ\_UNLOADRELOAD|  
|Référence|IDG\_VS\_PROJ\_REFERENCE|  
|Options|IDG\_VS\_PROJ\_OPTIONS|  
|Paramètres|IDG\_VS\_PROJ\_SETTINGS|  
  
### Créer des groupes de menus  
  
|Regrouper|ID|  
|---------------|--------|  
|Solution|IDG\_VS\_BUILD\_SOLUTION|  
|Sélection|IDG\_VS\_BUILD\_SELECTION|  
|Optimisation guidée par profil|IDG\_VS\_PGO\_SELECTION|  
|Divers|IDG\_VS\_BUILD\_MISC|  
|Annuler|IDG\_VS\_BUILD\_CANCEL|  
  
### Groupes de menus d'outils  
  
|Regrouper|ID|  
|---------------|--------|  
|Ligne de commande|IDG\_VS\_TOOLS\_CMDLINE|  
|Extraits de code|IDG\_VS\_TOOLS\_SNIPPETS|  
|Sous\-ensemble de l'objet|IDG\_VS\_TOOLS\_OBJSUBSET|  
|Options|IDG\_VS\_TOOLS\_OPTIONS|  
|Autres 2|IDG\_VS\_TOOLS\_OTHER2|  
|Outils externes|IDG\_VS\_TOOLS\_EXT\_TOOLS|  
|Personnalisations externes|IDG\_VS\_TOOLS\_EXT\_CUST|  
  
### Groupes du Menu fenêtre  
  
|Regrouper|ID|  
|---------------|--------|  
|Nouveau|IDG\_VS\_WINDOW\_NEW|  
|Station d'accueil\/de fermeture|IDG\_VS\_DOCKCLOSE|  
|Ancrer\/masquer|IDG\_VS\_DOCKHIDE|  
|Réorganiser|IDG\_VS\_WINDOW\_ARRANGE|  
|Navigation|IDG\_VS\_WINDOW\_NAVIGATION|  
|Liste|IDG\_VS\_WINDOW\_LIST|  
  
### Groupes de menus aide  
  
|Regrouper|ID|  
|---------------|--------|  
|Exemples|IDG\_VS\_HELP\_SAMPLES|  
|Prise en charge|IDG\_VS\_HELP\_SUPPORT|  
|À propos de|IDG\_VS\_HELP\_ABOUT|  
  
## Sous\-menus des Menus de Visual Studio  
 La hiérarchie suivante montre les sous\-menus associés avec les menus de la barre de menus de Visual Studio. Comme un groupe peut avoir un menu parent, chaque sous\-menu doit aboutissent à partir d'un groupe dans un menu, au lieu de directement à partir du menu. Pour plus d'informations sur la relation entre les menus, les groupes et les sous\-menus, consultez [Ajout d'un sous\-menu à un Menu](../../extensibility/adding-a-submenu-to-a-menu.md).  
  
> [!NOTE]
>  Les noms des menus dans la barre de menus de Visual Studio ne sont pas affichés séparément dans cette hiérarchie, car ils peuvent être déduits à partir de la convention d'affectation de noms pour les groupes dans l'IDE, comme suit : IDG\_VS\_*nom de Menu*\_*nom de groupe*.  
  
|Groupe parent|Sous\-menu|Groupes enfants|  
|-------------------|----------------|---------------------|  
|IDG\_VS\_FILE\_FILE|IDM\_VS\_CSCD\_NEW|IDG\_VS\_FILE\_NEW\_CASCADE|  
||IDM\_VS\_CSCD\_OPEN|IDG\_VS\_FILE\_OPENP\_CASCADE|  
|||IDG\_VS\_FILE\_OPENF\_CASCADE|  
|IDG\_VS\_FILE\_ADD|IDM\_VS\_CSCD\_ADD|IDG\_VS\_FILE\_ADD\_PROJECT\_NEW|  
|||IDG\_VS\_FILE\_ADD\_PROJECT\_EXI|  
|IDG\_VS\_FILE\_MRU|IDM\_VS\_CSCD\_FILEMRU|IDG\_VS\_FILE\_FMRU\_CASCADE|  
||IDM\_VS\_CSCD\_PROJMRU|IDG\_VS\_FILE\_PMRU\_CASCADE|  
|IDG\_VS\_FILE\_MOVE|IDM\_VS\_CSCD\_MOVETOPRJ|IDG\_VS\_FILE\_MOVE\_CASCADE|  
|||IDG\_VS\_FILE\_MOVE\_PICKER|  
|IDG\_VS\_VIEW\_DEV\_WINDOWS|IDM\_VS\_CSCD\_FINDRESULTS|IDG\_VS\_WNDO\_FINDRESULTS|  
||IDM\_VS\_CSCD\_WINDOWS|IDG\_VS\_VIEW\_CALLBROWSER|  
|||IDG\_VS\_WNDO\_OTRWNDWS1... 6|  
|||IDG\_VS\_WNDO\_WINDOWS2|  
|IDG\_VS\_VIEW\_TOOLBARS|IDM\_VS\_CSCD\_COMMANDBARS||  
|IDG\_VS\_EDIT\_GOTO|IDM\_VS\_EDITOR\_FIND\_MENU||  
|IDG\_VS\_EDIT\_OBJECTS|IDM\_VS\_CSCD\_MNUDES|IDG\_VS\_MNUDES\_INSERT|  
|||IDG\_VS\_MNUDES\_EDITNAMES|  
||IDM\_VS\_CSCD\_OLEVERBS|IDG\_VS\_EDIT\_OLEVERBS|  
|IDG\_VS\_BUILD\_SELECTION|IDM\_VS\_CSCD\_BUILD|IDG\_VS\_BUILD\_CASCADE|  
|||IDG\_VS\_BUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_REBUILD|IDG\_VS\_REBUILD\_CASCADE|  
|||IDG\_VS\_REBUILD\_PROJPICKER|  
||IDM\_VS\_CSCD\_PROJONLY|IDG\_VS\_PROJONLY\_CASCADE|  
||IDM\_VS\_CSCD\_CLEAN|IDG\_VS\_CLEAN\_CASCADE|  
|||IDG\_VS\_CLEAN\_PROJPICKER|  
||IDM\_VS\_CSCD\_DEPLOY|IDG\_VS\_DEPLOY\_CASCADE|  
|||IDG\_VS\_DEPLOY\_PROJPICKER|  
|IDG\_VS\_PGO\_SELECTION|IDM\_VS\_CSCD\_PGO\_BUILD|IDG\_VS\_PGO\_BUILD\_CASCADE\_BUILD|  
|||IDG\_VS\_PGO\_BUILD\_CASCADE\_RUN|  
  
## Voir aussi  
 [GUID et ID des barres d'outils de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)   
 [GUID et ID de commandes de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)   
 [Table de commandes de Visual Studio \(. Fichiers VSCT\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)