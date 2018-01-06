---
title: "Personnalisation de l’interpréteur de commandes isolé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9f5a6059d36493c93ceae249879530e49182acf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-the-isolated-shell"></a>Personnalisation du Shell isolé
Vous pouvez personnaliser votre application de shell isolé Visual Studio en modifiant les différents aspects de l’interface utilisateur de Visual Studio et en limitant les commandes et les fonctionnalités incluses dans votre application spécialisée.  
  
## <a name="using-the-applicationpkgdef-file"></a>À l’aide du fichier Application.pkgdef  
 La solution de modèle de shell isolé inclut un *SolutionName*. Fichier application.pkgdef qui vous permet de modifier les fonctionnalités suivantes :  
  
##### <a name="the-application-title"></a>Le titre de l’application  
 Vous pouvez personnaliser le titre de l’application, qui est le nom qui s’affiche dans la barre de titre de l’application, en modifiant la valeur de la ligne « AppName » dans le *SolutionName*. Fichier de application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si vous ne souhaitez pas que le titre de l’application pour afficher le projet qui est actuellement chargé, modifiez la valeur de la ligne « Valeur » dans le *SolutionName*. Fichier de application.pkgdef de DWORD : 00000001 à DWORD : 00000000.  
  
##### <a name="the-application-icon"></a>L’icône de l’application  
 Vous pouvez personnaliser l’icône de l’application, qui est l’icône qui est affichée par le nom de l’application dans la barre de titre d’application. Copiez une autre icône dans le répertoire de l’icône. Dans **l’Explorateur de solutions**, ajoutez l’icône dans le dossier de fichiers de ressources. Ensuite, ouvrez le fichier VSShellStub.rc et remplacez la valeur de IDI_STUBPROGRAM par le nom de la nouvelle icône. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Le logo de ligne de commande  
 Vous pouvez personnaliser le logo de ligne de commande, qui est le texte qui apparaît lorsque l’application est démarrée à partir de la ligne de commande, en modifiant la valeur de la ligne « CommandLineLogo » dans le *SolutionName*. Fichier de application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application Shell isolée de base](walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Le nom du sous-dossier de fichiers utilisateur  
 Vous pouvez modifier le nom du dossier de votre application gère pour les fichiers utilisateur en modifiant la valeur de la ligne « UserFilesSubFolderName » dans *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Le titre du nœud d’arbre de solution dans la boîte de dialogue Nouveau projet  
 Vous pouvez personnaliser le titre du nœud de solution dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgSlnTreeNodeTitle » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>L’en-tête de modèles installés dans la boîte de dialogue Nouveau projet  
 Vous pouvez modifier l’en-tête de modèles installés dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgInstalledTemplatesHdr » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Masquer les fichiers divers par défaut ou non  
 Vous pouvez spécifier s’il faut ou non masquer les fichiers divers par défaut en modifiant la valeur de la ligne « HideMiscellaneousFilesByDefault » dans le *SolutionName*. Fichier de application.pkgdef. Pour masquer les fichiers divers, définissez la valeur `dword:00000001`et pour afficher les fichiers, affectez la valeur `dword:00000000`.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>S’il faut ou non désactiver la fenêtre Sortie  
 Vous pouvez spécifier s’il faut ou non désactiver la fenêtre de sortie dans votre application en modifiant la valeur de la ligne « DisableOutputWindow » dans le *SolutionName*. Fichier de application.pkgdef. Pour désactiver la fenêtre Sortie, définissez la valeur `dword:00000001`et pour afficher la fenêtre Sortie, affectez la valeur `dword:00000000`.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Autoriser les fichiers déplacés dans la fenêtre principale ou non  
 Vous pouvez spécifier ou non autoriser les fichiers déplacés dans la fenêtre principale de votre application en modifiant la valeur de la ligne « AllowsDroppedFilesOnMainWindow » dans le *SolutionName*. Fichier de application.pkgdef. Pour autoriser les fichiers déplacés, définissez la valeur `dword:00000001`et pour interdire les fichiers supprimés, définissez la valeur `dword:00000000`.  
  
##### <a name="the-default-search-page"></a>La page de recherche par défaut  
 Vous pouvez personnaliser la page de navigateur web, qui est la page qui s’affiche lorsque la fenêtre du navigateur web est ouvert, en modifiant la valeur de la ligne « DefaultSearchPage » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-default-home-page"></a>La page d’accueil par défaut  
 Vous pouvez personnaliser la page d’accueil en modifiant la valeur de la ligne « DefaultHomePage » dans le *SolutionName*. Fichier de application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application Shell isolée de base](walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>S’il faut ou non masquer le concept de solution  
 Vous pouvez spécifier ou non masquer la solution dans votre application en modifiant la valeur de la ligne « HideSolutionConcept » dans le *SolutionName*. Fichier de application.pkgdef. Pour masquer la solution, affectez la valeur `dword:00000001`et pour afficher la solution, affectez la valeur `dword:00000000`.  
  
##### <a name="the-default-debug-engine"></a>Le moteur de débogage par défaut  
 Vous pouvez modifier le moteur de débogage que votre application utilise en modifiant la valeur de la ligne « DefaultDebugEngine » dans le *SolutionName*. Fichier application.pkgdef le GUID de votre moteur de débogage.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>L’extension de fichier du fichier des options utilisateur  
 Vous pouvez modifier le nom du dossier de votre application gère pour les fichiers utilisateur en modifiant la valeur de la ligne « UserOptsFileExt » dans *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-solution-file-extension"></a>L’extension de fichier de solution  
 Vous pouvez modifier l’extension utilisée pour les fichiers de votre solution en modifiant la valeur de la ligne « SolutionFileExt » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>La racine de dossier de fichiers utilisateur par défaut  
 Vous pouvez modifier le nom du dossier racine des fichiers utilisateur pour votre application en modifiant la valeur de la ligne « UserFilesSubFolderName » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>L’identificateur de créateur de fichier de solution  
 Vous pouvez modifier l’identificateur utilisé pour les fichiers de votre solution en modifiant la valeur de la ligne « SolutionFileCreatorIdentifier » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-default-projects-location"></a>L’emplacement par défaut des projets  
 Vous pouvez modifier le nom de l’emplacement par défaut des projets en modifiant la valeur de la ligne « DefaultProjectsLocation » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="the-application-localization-package"></a>Le package d’application localisation  
 Vous pouvez modifier le package de localisation utilisé pour votre application en modifiant la valeur de la ligne « AppLocalizationPackage » dans le *SolutionName*. Fichier de application.pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Afficher la racine de la hiérarchie dans le titre ou non  
 Vous pouvez spécifier ou non afficher la racine de la hiérarchie dans la barre de titre de votre application en modifiant la valeur de la ligne « Valeur » dans le *SolutionName*. Fichier de application.pkgdef. Pour afficher la racine de la hiérarchie, affectez la valeur `dword:00000001`et pour masquer la racine de la hiérarchie, définissez la valeur `dword:00000000`.  
  
##### <a name="specifying-a-start-page"></a>Spécification d’une page de démarrage  
 Pour spécifier une page de démarrage pour votre application personnalisée, dans le *SolutionName*. Fichier de application.pkgdef, affectez la valeur « DisableStartPage » `dword:00000000`et sous `[$RootKey$\StartPage\Default]` définir l’URI à l’emplacement du fichier .xaml :  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Dans le fichier Applicationcommands.vsct dans le *SolutionName*l’interface utilisateur de projet, commentez l’entrée « No_ShellPkg_startPageCommand » :  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Vous devez ajouter le fichier .xaml et tous les fichiers graphiques que vous avez besoin, à la *SolutionName* projet. Ces fichiers doivent effectivement être copiés sur le *SolutionName* répertoire du projet, ne pas ajoutée à partir d’un autre annuaire.  
  
 Sur tous les fichiers, définissez le **Type d’élément** propriété **Shell isolé de fichiers** afin que les fichiers à copier sur le *$RootFolder$* active. (Pour définir le **Type d’élément** propriété, cliquez sur le fichier et sélectionnez **propriétés**. Cette propriété se trouve sous **propriétés de Configuration**, **général**.)  
  
 Pour plus d’informations sur la personnalisation des pages de démarrage, consultez [personnalisation de la Page de démarrage](../../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>À l’aide d’autres éléments du shell isolé  
 Vous pouvez utiliser d’autres fichiers et les projets qui sont inclus dans le modèle de solution de shell isolé pour personnaliser davantage votre application.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Activer ou désactiver les packages Visual Studio  
 Le *SolutionName*.pkgundef fichier vous permet de désactiver certains types de fonctionnalités de Visual Studio en excluant certains packages. Par exemple, la ligne suivante :  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 Supprime le projet fichiers divers de l’ensemble des modèles de projet affichés dans le **nouveau projet** boîte de dialogue. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Activer ou désactiver les commandes de menu  
 Le *SolutionName*UI.vsct fichier inclut la liste de toutes les commandes de menu disponibles pour le shell isolé commenté. Pour désactiver une commande donnée, supprimez les commentaires de la ligne correspondante. Par exemple, pour désactiver le commentaire de la fenêtre/Fractionner, supprimez le `<Define name="No_SplitCommand"/>` ligne. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Bitmap utilisé sur l’écran de démarrage  
 Vous pouvez personnaliser l’image bitmap utilisée sur l’écran de démarrage, qui est la fenêtre qui s’affiche lorsque l’application est démarrée, en modifiant la valeur de la ligne « SplashScreenBitmap » dans le *SolutionName*. Fichier de application.pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>L’aide/à propos de la fenêtre  
 Dans le modèle de shell isolé est un projet séparé, vous pouvez utiliser pour personnaliser l’aide/à propos de la boîte de votre application. Pour plus d’informations, consultez [procédure pas à pas : création d’une Application de Shell isolé base](walkthrough-creating-a-basic-isolated-shell-application.md).