---
title: "Kit de développement logiciel de Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 56
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
ms.sourcegitcommit: 477f57bbca9c49e7d7d13155fc1f6e55ee4667a8
ms.openlocfilehash: efc5a2722757229057a91f5e3a6c2ad3681f5a89
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-sdk"></a>Kit de développement logiciel Visual Studio
Le Kit de développement logiciel Visual Studio vous permet d’étendre les fonctionnalités de Visual Studio ou d’intégrer de nouvelles fonctionnalités dans Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’à la galerie Visual Studio. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :  
  
-   Ajouter des commandes, des boutons, des menus et autres éléments d’interface utilisateur de l’IDE  
  
-   Ajouter des fenêtres Outil de nouvelles fonctionnalités  
  
-   Étendre IntelliSense pour une langue donnée, ou fournir IntelliSense pour les nouveaux langages de programmation  
  
-   Utiliser les ampoules pour fournir des indicateurs et des suggestions pour aider les développeurs à écrivent du code de meilleure qualité  
  
-   Activer la prise en charge d’un nouveau langage  
  
-   Ajouter un type de projet personnalisé  
  
-   Atteindre des millions de développeurs via la galerie Visual Studio  
  
 Si vous n’avez jamais rédigé une extension Visual Studio avant, vous devriez trouver plus d’informations sur ces fonctionnalités et à [début du développement d’Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>L’installation du Kit de développement logiciel de Visual Studio  
 À partir de Visual Studio 2015, vous n’installez pas Visual Studio SDK à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le Kit de développement logiciel Visual Studio plus tard. Pour plus d’informations, consultez [l’installation du Kit de développement logiciel Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015  
 Le Kit de développement logiciel Visual Studio comporte quelques nouvelles fonctionnalités, y compris les ampoules et les nouveaux éléments de projet qui vous permettent de créer des commandes de menu, fenêtres d’outils et extensions de l’éditeur à l’aide d’un package VSIX. Pour plus d’informations, consultez [Nouveautés dans le Kit de développement logiciel Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Consignes d’environnement utilisateur Visual Studio  
 Obtenez des conseils pour la conception de l’interface utilisateur de votre extension dans [recommandations pour l’environnement utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Vous pouvez également découvrir comment rendre votre extension superbes sur des périphériques PPP élevées avec notre [traite des problèmes de PPP](../extensibility/addressing-dpi-issues2.md) rubrique.  
  
 Tirer parti de la [Service d’images et de catalogue](../extensibility/image-service-and-catalog.md) pour la gestion des images exceptionnelles et la prise en charge des résolutions élevées et des thèmes.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Recherche et installation des Extensions Visual Studio existants  
 Vous pouvez trouver des extensions Visual Studio dans le **Extensions et mises à jour** boîte de dialogue sur la **outils** menu. Pour plus d’informations, consultez [recherche et utilisation d’Extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également rechercher des extensions dans le [la galerie Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Référence du Kit de développement logiciel Visual Studio  
 Vous pouvez trouver la référence de l’API du Kit de développement logiciel Visual Studio à [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Exemples du Kit de développement logiciel Visual Studio  
 Vous trouverez des exemples d’open source d’extensions du Kit de développement logiciel Visual Studio sur GitHub à l’adresse [exemples Visual Studio](https://aka.ms/vs2015sdksamples). Ce référentiel GitHub contient des exemples qui illustrent différentes fonctionnalités extensibles dans Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Autres ressources du Kit de développement logiciel Visual Studio  
 Si vous avez des questions sur VSSDK ou que vous souhaitez partager vos expériences de développement d’extensions, vous pouvez utiliser la [Forum Visual Studio Extensibility](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [ExtendVS groupe Chat](https://gitter.im/Microsoft/extendvs).  
  
 Vous trouverez plus d’informations dans les [blog de VSX aventurer](http://blogs.msdn.com/b/vsx/) et un nombre de blogs écrits par des Microsoft MVPs :  
  
-   [Extensions Visual Studio favori](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extension de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Comment : migrer les projets d’extensibilité Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Forum aux questions : Conversion des compléments en extensions VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [La gestion de plusieurs Threads en Code managé](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajouter des commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)   
 [Extension et personnalisation des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md)   
 [Éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md)   
 [Étendre des projets](../extensibility/extending-projects.md)   
 [Options et paramètres d’extension utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Création de projet personnalisés et les modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md)   
 [Étendre les propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)   
 [Extension des autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [La gestion de packages VS](../extensibility/managing-vspackages.md)   
 [Isolé du Shell Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dans le Kit de développement logiciel de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Prise en charge pour le Kit de développement logiciel de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md)
