---
title: "GUID et ID des barres d&#39;outils de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "groupes de Visual studio"
  - "barres d'outils"
  - "barre d'outils Visual studio"
  - "ID"
  - "groupe de toolgar"
  - "barre d'outils de la fenêtre outil"
  - "GUID"
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# GUID et ID des barres d&#39;outils de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette rubrique énumère GUID et les valeurs d'ID des barres d'outils qui sont incluses dans l'IDE de Visual \(IDE\) Studio, les groupes et ils contiennent.  Ces valeurs sont définies dans les fichiers de .vsct installés dans le cadre de le kit de développement Visual Studio.  Pour plus d'informations, consultez [Groupes, les Menus et les commandes définies par l’IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
> [!NOTE]
>  plusieurs des barres d'outils disponibles à Visual Studio ne sont pas définies par Visual Studio, et leur GUID et valeurs d'ID ne sont pas publics.  Cette rubrique répertorie uniquement les barres d'outils qui sont définies dans les fichiers du kit de développement Visual Studio .vsct.  
  
 Pour plus d'informations sur l'utilisation des objets de l'IDE définis dans les fichiers de .vsct, consultez [Extension des Menus et commandes](../../extensibility/extending-menus-and-commands.md).  
  
 Les barres d'outils par défaut fournies par l'IDE de Visual Studio utilisent un GUID `guidSHLMainMenu`, sauf dans sinon spécifié à l'aide d'un GUID : Syntaxe d'ID.  
  
## Barres d'outils de l'environnement  
 les barres d'outils suivantes sont fournies par l'IDE de Visual Studio.  Les barres d'outils peuvent être affichées en les sélectionnant dans le sous\-menu de **barres d'outils** le menu pour **Outils** .  Les barres d'outils dans des fenêtres Outil ne sont pas incluses dans cette section.  
  
 Seuls les groupes peuvent défiler directement des barres d'outils.  Pour ajouter un groupe, définissez son parent à un GUID et ID de la barre d'outils.  Pour ajouter un bouton à une barre d'outils, définissez son parent à un groupe dans la barre d'outils.  
  
|Barre d'outils|ID|  
|--------------------|--------|  
|Standard|IDM\_VS\_TOOL\_STANDARD|  
|Générer|IDM\_VS\_TOOL\_BUILD|  
|Éditeur de texte|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Débogage|guidVSDebugGroup : IDM\_DEBUG\_TOOLBAR|  
|emplacement de débogage|guidVSDebugGroup : IDM\_DEBUG\_CONTEXT\_TOOLBAR|  
  
### barres d'outils spéciales  
 Ces barres d'outils sont définies par l'IDE de Visual Studio, mais elles exécutent des fonctions spécialisées et n'hébergent pas de groupes de commandes.  
  
|Barre d'outils|ID|  
|--------------------|--------|  
|ajoutez la commande|IDM\_VS\_TOOL\_ADDCOMMAND|  
|Indéfini|IDM\_VS\_TOOL\_UNDEFINED|  
|Schéma XML|IDM\_VS\_TOOL\_SCHEMA|  
|Données XML|IDM\_VS\_TOOL\_DATA|  
  
## Groupes sur les barres d'outils de l'environnement  
 Pour ajouter un bouton à une barre d'outils standard, définissez un des groupes suivants comme son parent.  les groupes sont triés par la barre d'outils parente.  
  
### Groupes standard de barre d'outils  
  
|Nom|ID|  
|---------|--------|  
|Enregistrez\/ouvrez|IDG\_VS\_TOOLSB\_SAVEOPEN|  
|Couper\/copiez|IDG\_VS\_TOOLSB\_CUTCOPY|  
|L'annulation\/rétablir|IDG\_VS\_TOOLSB\_UNDOREDO|  
|Exécuter\/génération|IDG\_VS\_TOOLSB\_RUNBUILD|  
|Rechercher|IDG\_VS\_TOOLSB\_SEARCH|  
|Windows|IDG\_VS\_TOOLSB\_WINDOWS|  
|nouvelles fenêtres|IDG\_VS\_TOOLSB\_NEWWINDOWS|  
|Chargement\/sauvegarde|IDG\_VS\_WINDOWUI\_LOADSAVE|  
|jauge|IDG\_VS\_TOOLSB\_GAUGE|  
  
### groupes de barre d'outils de génération  
  
|Nom|ID|  
|---------|--------|  
|barre de génération|IDG\_VS\_BUILDBAR|  
|Cancel|IDG\_VS\_BUILD\_CANCEL|  
  
### Groupes de barre d'outils éditeur de texte  
  
|Nom|ID|  
|---------|--------|  
|Achèvement|IDM\_VS\_TOOL\_TEXTEDITOR|  
|Retrait|IDG\_VS\_EDITTOOLBAR\_INDENT|  
|Commentaire|IDG\_VS\_EDITTOOLBAR\_COMMENT|  
|Signets|IDG\_VS\_EDITTOOLBAR\_TEMPBOOKMARKS|  
  
### groupes de barre d'outils de débogage  
  
|Nom|ID|  
|---------|--------|  
|Exécution|IDM\_DEBUG\_TOOLBAR|  
|Pas à pas|IDG\_DEBUG\_TOOLBAR\_STEPPING|  
|Watch|IDG\_DEBUG\_TOOLBAR\_WATCH|  
|Windows|IDG\_DEBUG\_TOOLBAR\_WINDOWS|  
  
### Groupes de barre d'outils emplacement de débogage  
  
|Nom|ID|  
|---------|--------|  
|déboguez l'emplacement|IDG\_DEBUG\_CONTEXT\_TOOLBAR|  
  
## Barres d'outils de la fenêtre Outil  
 Les barres d'outils peuvent apparaître directement dans l'IDE ou dans des fenêtres Outil telles que **Explorateur de solutions**.  Étant donné que les fenêtres Outil ne sont pas définies dans les fichiers de .vsct, les barres d'outils de la fenêtre Outil n'ont pas défini des parents.  En revanche, ils sont placés dans le code.  Le tableau suivant affiche les barres d'outils qui apparaissent sur les fenêtres Outil de l'IDE, et les groupes de commandes qu'ils contiennent.  
  
> [!NOTE]
>  Les barres d'outils et les groupes utilisent un GUID `guidSHLMainMenu`, sauf dans sinon spécifié à l'aide d'un GUID : Syntaxe d'ID.  Où le GUID est spécifié pour une barre d'outils, il s'applique également aux groupes qui descendent de cette barre d'outils.  
  
|fenêtre Outil|Barre d'outils|Groups|  
|-------------------|--------------------|------------|  
|Explorateur de solutions|IDM\_VS\_TOOL\_PROJWIN|IDG\_VS\_PROJ\_TOOLBAR1..5|  
|Explorateur de serveurs|guid\_SE\_MenuGroup : IDM\_SE\_TOOLBAR\_SERVEREXPLORER|IDG\_SE\_TOOLBAR\_REFRESH|  
|Propriétés|IDM\_VS\_TOOL\_PROPERTIES|IDG\_VS\_PROPERTIES\_SORT<br /><br /> IDG\_VS\_PROPERTIES\_PAGES|  
|Affichage de classes|IDM\_VS\_TOOL\_CLASSVIEW|IDG\_VS\_CLASSVIEW\_FOLDERS<br /><br /> IDG\_VS\_CLASSVIEW\_SEARCH<br /><br /> IDG\_VS\_CLASSVIEW\_SETTINGS|  
|Affichage de classes|IDM\_VS\_TOOL\_CLASSVIEW\_GO|IDG\_VS\_CLASSVIEW\_SEAR CH2|  
|Explorateur d'objets|IDM\_VS\_TOOL\_OBJBROWSER|IDG\_VS\_OBJBROWSER\_SUBSETS<br /><br /> IDG\_VS\_OBJBROWSER\_SEARCH<br /><br /> IDG\_VS\_OBJBROWSER\_ADDREFERENCE<br /><br /> IDG\_VS\_OBJBROWSER\_BROWSERSETTINGS|  
|Explorateur d'objets|IDM\_VS\_TOOL\_OBJECT\_BROWSER\_GO|IDG\_VS\_OBJBROWSER\_SEAR CH2|  
|Sortie|IDM\_VS\_TOOL\_OUTPUTWINDOW|IDG\_VS\_OUTPUTWINDOW\_SELECT<br /><br /> IDG\_VS\_OUTPUTWINDOW\_GOTO<br /><br /> IDG\_VS\_OUTPUTWINDOW\_NEXTPREV<br /><br /> IDG\_VS\_OUTPUTWINDOW\_CLEAR<br /><br /> IDG\_VS\_OUTPUTWINDOW\_WORDWRAP|  
|Rechercher et remplacer|IDM\_VS\_TOOL\_UNIFIEDFIND|IDG\_VS\_FINDTAB<br /><br /> IDG\_VS\_REPLACETAB|  
|recherchez les résultats 1|IDM\_VS\_TOOL\_FINDRESULTS1|IDG\_VS\_FINDRESULTS1\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS1\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS1\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS1\_STOPFIND|  
|résultats 2 de recherche|IDM\_VS\_TOOL\_FINDRESULTS2|IDG\_VS\_FINDRESULTS2\_GOTO<br /><br /> IDG\_VS\_FINDRESULTS2\_NEXTPREV<br /><br /> IDG\_VS\_FINDRESULTS2\_CLEAR<br /><br /> IDG\_VS\_FINDRESULTS2\_STOPFIND|  
|Snippet|IDM\_VS\_TOOL\_SNIPPETMENUS|IDG\_VS\_SNIPPET\_REPL<br /><br /> IDG\_VS\_SNIPPET\_REF<br /><br /> IDG\_VS\_SNIPPET\_PROP|  
|Signets|IDM\_VS\_TOOL\_BOOKMARKWIND|IDG\_VS\_BWNEWFOLDER<br /><br /> IDG\_VS\_BWNEXTBM<br /><br /> IDG\_VS\_BWNEXTBMF<br /><br /> IDG\_VS\_BWENABLE<br /><br /> IDG\_VS\_BWDELETE|  
|Liste des tâches|IDM\_VS\_TOOL\_TASKLIST|IDG\_VS\_TASKLIST\_PROVIDERLIST|  
|tâches d'utilisateur|IDM\_VS\_TOOL\_USERTASKS|IDG\_VS\_TASKLIST\_PROVIDERLIST<br /><br /> IDG\_VS\_USERTASKS\_EDIT|  
|Liste d'erreurs|IDM\_VS\_TOOL\_ERRORLIST|IDG\_VS\_ERRORLIST\_ERRORGROUP<br /><br /> IDG\_VS\_ERRORLIST\_WARNINGGROUP<br /><br /> IDG\_VS\_ERRORLIST\_MESSAGEGROUP|  
|navigateur d'appel|IDM\_VS\_TOOL\_ CALLBROWSER1. .16|\_ACTIONS D'IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_TYPE D'IDG\_VS\_TOOLBAR\_ CALLBROWSER1<br /><br /> \_CBSETTINGS D'IDG\_VS\_TOOLBAR\_ CALLBROWSER1|  
|Points d'arrêt|guidVSDebugGroup : IDM\_BREAKPOINTS\_WINDOW\_TOOLBAR|IDG\_BREAKPOINTS\_WINDOW\_NEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_DELETE<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_ALL<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_VIEW<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_EDIT<br /><br /> IDG\_BREAKPOINTS\_WINDOW\_COLUMNS|  
|Le code machine|guidVSDebugGroup : IDM\_DISASM\_WINDOW\_TOOLBAR|IDG\_DISASM\_WINDOW\_TOOLBAR|  
|mémoire 1\-4|guidVSDebugGroup : IDM\_MEMORY\_WINDOW\_TOOLBAR1… 4|IDG\_MEMORY\_EXPRESSION1..4<br /><br /> IDG\_MEMORY\_ COLUMNS1. .4|  
|Processus|guidVSDebugGroup : IDM\_ATTACHED\_PROCS\_TOOLBAR|IDG\_ATTACHED\_PROCS\_EXECCNTRL IDG\_ATTACHED\_PROCS\_STEPPING<br /><br /> IDG\_ATTACHED\_PROCS\_EXE CCNTRL2<br /><br /> IDG\_ATTACHED\_PROCS\_ATTACH<br /><br /> IDG\_ATTACHED\_PROCS\_COLUMNS|  
  
## Voir aussi  
 [Ajout d'un contrôleur de Menu à une barre d'outils](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)   
 [Ajout d'une barre d'outils à une fenêtre outil](../../extensibility/adding-a-toolbar-to-a-tool-window.md)   
 [GUID et ID de Menus de Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)