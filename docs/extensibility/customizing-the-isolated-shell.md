---
title: "Personnalisation de l’interpréteur de commandes isolé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f36bfb81f311db0f49d399f86007f10d618b7ba3
ms.lasthandoff: 02/22/2017

---
# <a name="customizing-the-isolated-shell"></a>Personnalisation de l’interpréteur de commandes isolé
Vous pouvez personnaliser votre application de shell isolé de Visual Studio en modifiant les différents aspects de l’interface utilisateur de Visual Studio et en limitant les commandes et les fonctionnalités incluses dans votre application spécialisée.  
  
## <a name="using-the-applicationpkgdef-file"></a>À l’aide du fichier Application.pkgdef  
 Le modèle de solution shell isolé inclut un *SolutionName*. Fichier application.pkgdef qui vous permet de modifier les fonctionnalités suivantes :  
  
##### <a name="the-application-title"></a>Le titre de l’application  
 Vous pouvez personnaliser le titre de l’application, qui est le nom qui s’affiche dans la barre de titre de l’application, en modifiant la valeur de la ligne « AppName » dans le *SolutionName*. Fichier application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si vous ne souhaitez pas le titre de l’application pour afficher le projet actuellement chargé, modifiez la valeur de la ligne « ShowHierarchyRootInTitle » dans le *SolutionName*. Fichier de application.pkgdef de DWORD :&00000;001 à DWORD :&00000;000.  
  
##### <a name="the-application-icon"></a>L’icône d’application  
 Vous pouvez personnaliser l’icône d’application, l’icône qui est affichée par le nom de l’application dans la barre de titre d’application. Copiez une autre icône dans le répertoire de l’icône. Dans **l’Explorateur de solutions**, ajoutez l’icône dans le dossier de fichiers de ressources. Ensuite, ouvrez le fichier VSShellStub.rc et remplacez la valeur de IDI_STUBPROGRAM par le nom de la nouvelle icône. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Le logo de ligne de commande  
 Vous pouvez personnaliser le logo de ligne de commande, qui correspond au texte qui apparaît lorsque l’application est démarrée à partir de la ligne de commande, en modifiant la valeur de la ligne « CommandLineLogo » dans le *SolutionName*. Fichier application.pkgdef. Pour plus d’informations, consultez la page [procédure pas à pas : création d’une Application Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Le nom du sous-dossier fichiers utilisateur  
 Vous pouvez modifier le nom de votre application tient à jour pour les fichiers utilisateur en modifiant la valeur de la ligne « UserFilesSubFolderName » dans le dossier de *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Le titre du nœud d’arbre de solution dans la boîte de dialogue Nouveau projet  
 Vous pouvez personnaliser le titre du nœud de solution dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgSlnTreeNodeTitle » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>L’en-tête de modèles installés dans la boîte de dialogue Nouveau projet  
 Vous pouvez modifier l’en-tête de modèles installés dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgInstalledTemplatesHdr » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>S’il faut masquer les divers fichiers par défaut  
 Vous pouvez spécifier s’il faut masquer les divers fichiers par défaut en modifiant la valeur de la ligne « HideMiscellaneousFilesByDefault » dans le *SolutionName*. Fichier application.pkgdef. Pour masquer les fichiers divers, définissez la valeur `dword:00000001`et pour afficher les fichiers, affectez la valeur `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>S’il faut désactiver la fenêtre Sortie  
 Vous pouvez spécifier s’il faut désactiver la fenêtre Sortie dans votre application en modifiant la valeur de la ligne « DisableOutputWindow » dans le *SolutionName*. Fichier application.pkgdef. Pour désactiver la fenêtre Sortie, définissez la valeur `dword:00000001`et pour afficher la fenêtre Sortie, définissez la valeur `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>S’il faut autoriser les fichiers supprimés de la fenêtre principale  
 Vous pouvez spécifier s’il faut autoriser les fichiers supprimés de la fenêtre principale de votre application en modifiant la valeur de la ligne « AllowsDroppedFilesOnMainWindow » dans le *SolutionName*. Fichier application.pkgdef. Pour autoriser les fichiers supprimés, définissez la valeur `dword:00000001`et pour interdire les fichiers supprimés, affectez la valeur `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>La page de recherche par défaut  
 Vous pouvez personnaliser la page du navigateur web, qui est la page qui s’affiche lorsque la fenêtre du navigateur web est ouvert, en modifiant la valeur de la ligne « DefaultSearchPage » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-default-home-page"></a>La page d’accueil par défaut  
 Vous pouvez personnaliser la page d’accueil en modifiant la valeur de la ligne « DefaultHomePage » dans le *SolutionName*. Fichier application.pkgdef. Pour plus d’informations, consultez la page [procédure pas à pas : création d’une Application Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>S’il faut masquer le concept de solution  
 Vous pouvez spécifier s’il faut masquer la solution dans votre application en modifiant la valeur de la ligne « HideSolutionConcept » dans le *SolutionName*. Fichier application.pkgdef. Pour masquer la solution, affectez la valeur `dword:00000001`et pour afficher la solution, affectez la valeur `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Le moteur de débogage par défaut  
 Vous pouvez modifier le moteur de débogage que votre application utilise en modifiant la valeur de la ligne « DefaultDebugEngine » dans le *SolutionName*. Fichier application.pkgdef le GUID de votre moteur de débogage.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>L’extension de fichier des options utilisateur  
 Vous pouvez modifier le nom de votre application tient à jour pour les fichiers utilisateur en modifiant la valeur de la ligne « UserOptsFileExt » dans le dossier de *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>L’extension de fichier de solution  
 Vous pouvez modifier l’extension utilisée pour les fichiers de votre solution en modifiant la valeur de la ligne « SolutionFileExt » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La racine par défaut du dossier de fichiers utilisateur  
 Vous pouvez modifier le nom du dossier racine des fichiers de l’utilisateur pour votre application en modifiant la valeur de la ligne « UserFilesSubFolderName » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>L’identificateur de créateur de fichier solution  
 Vous pouvez modifier l’identificateur utilisé pour les fichiers de votre solution en modifiant la valeur de la ligne « SolutionFileCreatorIdentifier » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>L’emplacement par défaut des projets  
 Vous pouvez modifier le nom de l’emplacement par défaut des projets en modifiant la valeur de la ligne « DefaultProjectsLocation » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Le package de localisation d’applications  
 Vous pouvez modifier le package de localisation utilisé pour votre application en modifiant la valeur de la ligne « AppLocalizationPackage » dans le *SolutionName*. Fichier application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>S’il faut afficher la racine de la hiérarchie dans le titre  
 Vous pouvez spécifier s’il faut afficher la racine de la hiérarchie dans la barre de titre de votre application en modifiant la valeur de la ligne « ShowHierarchyRootInTitle » dans le *SolutionName*. Fichier application.pkgdef. Pour afficher la racine de la hiérarchie, affectez la valeur `dword:00000001`et pour masquer la racine de la hiérarchie, définissez la valeur `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Spécification d’une page de démarrage  
 Pour spécifier une page de démarrage pour votre application personnalisée, dans le *SolutionName*. Fichier application.pkgdef, affectez la valeur « DisableStartPage » `dword:00000000`et sous `[$RootKey$\StartPage\Default]` définir l’URI à l’emplacement du fichier .xaml :  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Dans le fichier Applicationcommands.vsct dans le *SolutionName*l’interface utilisateur de projet, commentez l’entrée « No_ShellPkg_startPageCommand » :  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Vous devez ajouter le fichier .xaml et tous les fichiers graphiques que vous avez besoin, à la *SolutionName* projet. Ces fichiers doivent effectivement être copiés sur le *SolutionName* répertoire de projet, ne pas ajoutée à partir d’un autre annuaire.  
  
 Sur tous les fichiers, définissez les **Type d’élément** propriété **fichiers Shell isolé** afin que les fichiers à copier sur le *$RootFolder$* active. (Pour définir la **Type d’élément** propriété, cliquez sur le fichier et sélectionnez **propriétés**. Cette propriété se trouve sous **propriétés de Configuration**, **général**.)  
  
 Pour plus d’informations sur la personnalisation des pages de démarrage, consultez [personnalisation de la Page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>À l’aide d’autres éléments du shell isolé  
 Vous pouvez utiliser d’autres fichiers et des projets qui sont inclus dans le modèle de solution shell isolé afin de personnaliser davantage votre application.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Activer/désactiver les packages de Visual Studio  
 Le *SolutionName*.pkgundef fichier vous permet de désactiver certains types de fonctionnalités de Visual Studio en excluant certains packages. Par exemple, la ligne suivante :  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Supprime le projet fichiers divers de l’ensemble des modèles de projet affiché dans la **nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Activer ou désactiver les commandes de menu  
 Le *SolutionName*UI.vsct fichier inclut une liste de commentaire de toutes les commandes de menu disponibles à l’environnement isolé. Pour désactiver une commande donnée, supprimez la ligne correspondante. Par exemple, pour désactiver le commentaire de la fenêtre/fractionnement, supprimez le `<Define name="No_SplitCommand"/>` ligne. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Bitmap utilisé sur l’écran de démarrage  
 Vous pouvez personnaliser l’image utilisée sur l’écran de démarrage, qui est la fenêtre qui s’affiche lorsque l’application est démarrée, en modifiant la valeur de la ligne « SplashScreenBitmap » dans le *SolutionName*. Fichier application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>L’aide/à propos de la fenêtre  
 Dans le modèle de shell isolé, il existe un projet séparé, vous pouvez utiliser pour personnaliser l’aide/à propos de la boîte de votre application. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
