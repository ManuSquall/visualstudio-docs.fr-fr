---
title: SDK Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59ef6ae6b042b1616997821febe156ef5cac3b7f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299703"
---
# <a name="visual-studio-sdk"></a>Kit de développement logiciel Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le kit de développement logiciel (SDK) Visual Studio vous aide à étendre les fonctionnalités de Visual Studio ou à intégrer de nouvelles fonctionnalités dans Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’à la Galerie Visual Studio. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :  
  
- Ajouter des commandes, des boutons, des menus et d’autres éléments d’interface utilisateur à l’IDE  
  
- Ajouter des fenêtres outil pour les nouvelles fonctionnalités  
  
- Étendez IntelliSense pour un langage donné ou fournissez IntelliSense pour les nouveaux langages de programmation  
  
- Utilisez des ampoules pour fournir des conseils et des suggestions pour aider les développeurs à écrire du code plus performant  
  
- Activer la prise en charge d’une nouvelle langue  
  
- Ajouter un type de projet personnalisé  
  
- Atteignez des millions de développeurs via le Visual Studio Marketplace  
  
  Si vous n’avez jamais écrit une extension Visual Studio, vous trouverez plus d’informations sur ces fonctionnalités et sur le [développement d’extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installation du Kit de développement logiciel (SDK) Visual Studio  
 À compter de Visual Studio 2015, vous n’installez pas le kit de développement logiciel (SDK) Visual Studio à partir du centre de téléchargement. Il est inclus en tant que fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installation du kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Nouveautés du kit de développement logiciel (SDK) Visual Studio 2015  
 Le kit de développement logiciel (SDK) Visual Studio propose de nouvelles fonctionnalités, notamment des ampoules et de nouveaux éléments de projet qui vous permettent de créer des commandes de menu, des fenêtres outil et des extensions d’éditeur à l’aide d’un package VSIX. Pour plus d’informations, consultez [Nouveautés du kit de développement logiciel (SDK) Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Lignes directrices pour l’expérience utilisateur dans Visual Studio  
 Bénéficiez de conseils utiles pour concevoir l’interface utilisateur de votre extension dans [les instructions d’expérience utilisateur de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Vous pouvez également découvrir comment faire en sorte que votre extension soit intéressante sur les appareils haute résolution avec notre rubrique relative [aux problèmes d’adressage dpi](../extensibility/addressing-dpi-issues2.md) .  
  
 Tirez parti du [service d’images et du catalogue](../extensibility/image-service-and-catalog.md) pour une gestion des images exceptionnelle et la prise en charge de la haute résolution et des thèmes.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Recherche et installation des extensions Visual Studio existantes  
 Vous pouvez rechercher les extensions Visual Studio dans la boîte de dialogue **extensions et mises à jour** du menu **Outils** . Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également trouver des extensions dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Informations de référence sur le SDK Visual Studio  
 Vous trouverez les informations de référence sur l’API du SDK Visual Studio à la [Référence du kit de développement Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Exemples du kit de développement logiciel Visual Studio  
 Vous trouverez des exemples Open source d’extensions VS SDK sur GitHub dans [exemples Visual Studio](https://aka.ms/vs2015sdksamples). Ce référentiel GitHub contient des exemples qui illustrent diverses fonctionnalités extensibles dans Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Autres ressources du kit de développement logiciel (SDK) Visual Studio  
 Si vous avez des questions sur le VSSDK ou que vous souhaitez partager vos expériences en développant des extensions, vous pouvez utiliser le [Forum extensibilité de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou la [conversation de groupe ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Vous trouverez plus d’informations sur le [blog de Arcana VSX](https://blogs.msdn.microsoft.com/vsx/) et sur un certain nombre de blogs écrits par des MVP Microsoft :  
  
- [Extensions Visual Studio favorites](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Extension de Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une extension à l’aide d’une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Comment : migrer des projets d’extensibilité vers Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [FAQ : conversion des compléments en extensions VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gestion de plusieurs threads dans le code managé](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajout de commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)   
 [Extension et personnalisation des fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md)   
 [Extensions du service de langage et de l’éditeur](../extensibility/editor-and-language-service-extensions.md)   
 [Extension des projets](../extensibility/extending-projects.md)   
 [Extension des paramètres et options de l’utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Création de modèles de projet et d’élément personnalisés](../extensibility/creating-custom-project-and-item-templates.md)   
 [Extension des propriétés et de la fenêtre des propriétés](../extensibility/extending-properties-and-the-property-window.md)   
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Utilisation et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Extension de Services connectés](../extensibility/extending-connected-services.md)   
 [Gestion des VSPackages](../extensibility/managing-vspackages.md)   
   de [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
 [Expédition des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dans le kit de développement logiciel Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Prise en charge du kit de développement logiciel Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
   d' [Archive](../extensibility/archive.md)  
 [Référence du Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk-reference.md)
