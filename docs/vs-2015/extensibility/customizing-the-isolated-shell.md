---
title: Personnalisation de l’interpréteur de commandes isolé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555966"
---
# <a name="customizing-the-isolated-shell"></a>Personnalisation du Shell isolé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez personnaliser votre application Visual Studio isolated Shell en modifiant différents aspects de l’interface utilisateur de Visual Studio et en restreignant les commandes et les fonctionnalités incluses dans votre application spécialisée.  
  
## <a name="using-the-applicationpkgdef-file"></a>Utilisation du fichier. pkgdef de l’application  
 La solution de modèle d’interpréteur de commandes isolé comprend un *SolutionName*. Fichier application. pkgdef qui vous permet de modifier les fonctionnalités suivantes :  
  
##### <a name="the-application-title"></a>Le titre de l’application  
 Vous pouvez personnaliser le titre de l’application, qui est le nom affiché dans la barre de titre de l’application, en modifiant la valeur de la ligne « AppName » dans le *NomSolution*. Fichier application. pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
 Si vous ne souhaitez pas que le titre de l’application affiche le projet actuellement chargé, modifiez la valeur de la ligne « ShowHierarchyRootInTitle » dans le *NomSolution*. Fichier application. pkgdef de DWORD : 00000001 à DWORD : 00000000.  
  
##### <a name="the-application-icon"></a>Icône d’application  
 Vous pouvez personnaliser l’icône de l’application, qui est l’icône qui est affichée par le nom de l’application dans la barre de titre de l’application. Copiez une icône différente dans le répertoire de l’icône. Dans **Explorateur de solutions**, ajoutez l’icône au dossier fichiers de ressources. Ouvrez ensuite le fichier VSShellStub. RC et remplacez la valeur de IDI_STUBPROGRAM par le nom de la nouvelle icône. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-command-line-logo"></a>Le logo de la ligne de commande  
 Vous pouvez personnaliser le logo de la ligne de commande, qui est le texte qui apparaît lorsque l’application est démarrée à partir de la ligne de commande, en modifiant la valeur de la ligne « CommandLineLogo » dans le *NomSolution*. Fichier application. pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>Nom du sous-dossier des fichiers utilisateur  
 Vous pouvez modifier le nom du dossier géré par votre application pour les fichiers utilisateur en modifiant la valeur de la ligne « UserFilesSubFolderName » dans *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>Titre du nœud de l’arborescence de solutions dans la boîte de dialogue Nouveau projet  
 Vous pouvez personnaliser le titre du nœud de la solution dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgSlnTreeNodeTitle » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>En-tête de modèles installés dans la boîte de dialogue Nouveau projet  
 Vous pouvez modifier l’en-tête de modèles installés dans la boîte de dialogue Nouveau projet en modifiant la valeur de la ligne « NewProjDlgInstalledTemplatesHdr » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>Indique s’il faut ou non masquer les fichiers divers par défaut  
 Vous pouvez spécifier s’il faut ou non masquer les fichiers divers par défaut en modifiant la valeur de la ligne « HideMiscellaneousFilesByDefault » dans le *NomSolution*. Fichier application. pkgdef. Pour masquer les fichiers divers, définissez la valeur `dword:00000001` , et pour afficher les fichiers, définissez la valeur `dword:00000000` .  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>Indique si la fenêtre sortie doit être désactivée  
 Vous pouvez spécifier s’il faut ou non désactiver la fenêtre de sortie dans votre application en modifiant la valeur de la ligne « DisableOutputWindow » dans le *NomSolution*. Fichier application. pkgdef. Pour désactiver la fenêtre sortie, définissez la valeur `dword:00000001` et pour afficher la fenêtre sortie, définissez la valeur `dword:00000000` .  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>Indique s’il faut ou non autoriser les fichiers supprimés dans la fenêtre principale  
 Vous pouvez spécifier s’il faut ou non autoriser les fichiers supprimés dans la fenêtre principale de votre application en modifiant la valeur de la ligne « AllowsDroppedFilesOnMainWindow » dans le *NomSolution*. Fichier application. pkgdef. Pour autoriser les fichiers supprimés, définissez la valeur `dword:00000001` et pour interdire les fichiers supprimés, définissez la valeur `dword:00000000` .  
  
##### <a name="the-default-search-page"></a>Page de recherche par défaut  
 Vous pouvez personnaliser la page du navigateur Web, qui est celle qui s’affiche lorsque la fenêtre du navigateur Web est ouverte, en modifiant la valeur de la ligne « DefaultSearchPage » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-default-home-page"></a>Page d’hébergement par défaut  
 Vous pouvez personnaliser la page d’origine en modifiant la valeur de la ligne « DefaultHomePage » dans le *NomSolution*. Fichier application. pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>Indique s’il faut ou non masquer le concept de solution  
 Vous pouvez spécifier s’il faut ou non masquer la solution dans votre application en modifiant la valeur de la ligne « HideSolutionConcept » dans le *NomSolution*. Fichier application. pkgdef. Pour masquer la solution, définissez la valeur `dword:00000001` et pour afficher la solution, définissez la valeur `dword:00000000` .  
  
##### <a name="the-default-debug-engine"></a>Moteur de débogage par défaut  
 Vous pouvez modifier le moteur de débogage utilisé par votre application en modifiant la valeur de la ligne « DefaultDebugEngine » dans le *NomSolution*. Fichier application. pkgdef vers le GUID de votre moteur de débogage.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>Extension de fichier du fichier d’options utilisateur  
 Vous pouvez modifier le nom du dossier géré par votre application pour les fichiers utilisateur en modifiant la valeur de la ligne « UserOptsFileExt » dans *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-solution-file-extension"></a>Extension du fichier solution  
 Vous pouvez modifier l’extension utilisée pour vos fichiers solution en modifiant la valeur de la ligne « SolutionFileExt » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-default-user-files-folder-root"></a>Racine du dossier de fichiers utilisateur par défaut  
 Vous pouvez modifier le nom du dossier racine des fichiers utilisateur de votre application en modifiant la valeur de la ligne « UserFilesSubFolderName » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-solution-file-creator-identifier"></a>Identificateur du créateur du fichier solution  
 Vous pouvez modifier l’identificateur utilisé pour vos fichiers solution en modifiant la valeur de la ligne « SolutionFileCreatorIdentifier » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-default-projects-location"></a>L’emplacement des projets par défaut  
 Vous pouvez modifier le nom de l’emplacement des projets par défaut en modifiant la valeur de la ligne « DefaultProjectsLocation » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="the-application-localization-package"></a>Package de localisation d’application  
 Vous pouvez modifier le package de localisation utilisé pour votre application en modifiant la valeur de la ligne « AppLocalizationPackage » dans le *NomSolution*. Fichier application. pkgdef.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>Indique s’il faut ou non afficher la racine de la hiérarchie dans le titre  
 Vous pouvez indiquer s’il faut ou non afficher la racine de la hiérarchie dans la barre de titre de votre application en modifiant la valeur de la ligne « ShowHierarchyRootInTitle » dans le *NomSolution*. Fichier application. pkgdef. Pour afficher la racine de la hiérarchie, définissez la valeur `dword:00000001` , et pour masquer la racine de la hiérarchie, définissez la valeur `dword:00000000` .  
  
##### <a name="specifying-a-start-page"></a>Spécification d’une page de démarrage  
 Pour spécifier une page de démarrage pour votre application personnalisée, dans le *NomSolution*. Fichier application. pkgdef, définissez la valeur « DisableStartPage » sur `dword:00000000` et, sous `[$RootKey$\StartPage\Default]` Définissez l’URI sur l’emplacement du fichier. xaml :  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Dans le fichier ApplicationCommands. vsct dans le projet d’interface utilisateur *NomSolution*, commentez l’entrée « No_ShellPkg_startPageCommand » :  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 Vous devez ajouter le fichier. xaml, ainsi que tous les fichiers graphiques dont vous avez besoin, au projet *NomSolution* . Ces fichiers doivent être copiés dans le répertoire du projet *SolutionName* , pas ajoutés à partir d’un autre annuaire.  
  
 Sur tous les fichiers, définissez la propriété **type d’élément** sur **fichier Shell isolé** pour que les fichiers soient copiés dans le répertoire *$RootFolder $* . (Pour définir la propriété **type d’élément** , cliquez avec le bouton droit sur le fichier et sélectionnez **Propriétés**. Cette propriété se trouve sous **Propriétés de configuration**, **général**.)  
  
 Pour plus d’informations sur la personnalisation des pages de démarrage, consultez [Personnalisation de la page de démarrage](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>Utilisation d’autres éléments de l’interpréteur de commandes isolé  
 Vous pouvez utiliser d’autres fichiers et projets inclus dans le modèle de solution de Shell isolé pour personnaliser davantage votre application.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Activer/désactiver des packages Visual Studio  
 Le fichier *NomSolution*. pkgundef vous permet de désactiver certains genres de fonctionnalités Visual Studio en excluant certains packages. Par exemple, la ligne suivante :  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 supprime le projet fichiers divers du jeu de modèles de projet affiché dans la boîte de dialogue **nouveau projet** . Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="enabledisable-menu-commands"></a>Activer/désactiver les commandes de menu  
 Le fichier UI. vsct de *NomSolution*contient une liste commentée de toutes les commandes de menu disponibles pour l’interpréteur de commandes isolé. Pour désactiver une commande donnée, supprimez les marques de commentaire de la ligne correspondante. Par exemple, pour désactiver le commentaire de fenêtre/fractionnement, supprimez les marques de commentaire de la `<Define name="No_SplitCommand"/>` ligne. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>Bitmap utilisé sur l’écran de démarrage  
 Vous pouvez personnaliser l’image bitmap utilisée sur l’écran de démarrage, qui est la fenêtre qui s’affiche au démarrage de l’application, en modifiant la valeur de la ligne « SplashScreenBitmap » dans le *NomSolution*. Fichier application. pkgdef. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
##### <a name="the-helpabout-window"></a>Fenêtre aide/à propos de  
 Dans le modèle d’interpréteur de commandes isolé, vous pouvez utiliser un projet distinct pour personnaliser la boîte de l’aide/à propos de votre application. Pour plus d’informations, consultez [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).
