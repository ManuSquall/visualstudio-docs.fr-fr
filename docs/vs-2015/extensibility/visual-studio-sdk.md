---
title: SDK Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7554bf39960a55a566b366abc328f54199bd4367
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47496203"
---
# <a name="visual-studio-sdk"></a>SDK Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Visual Studio SDK](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-sdk).  
  
Le SDK Visual Studio vous permet d’étendre les fonctionnalités de Visual Studio ou d’intégrer de nouvelles fonctionnalités à Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’à la galerie Visual Studio. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :  
  
-   Ajouter des commandes, des boutons, des menus et autres éléments d’interface utilisateur à l’IDE  
  
-   Ajouter des fenêtres Outil pour les nouvelles fonctionnalités  
  
-   Étendre IntelliSense pour une langue donnée, ou fournir IntelliSense pour les nouveaux langages de programmation  
  
-   Utiliser des ampoules pour fournir des indicateurs et des suggestions pour aider les développeurs à écrivent du code de meilleure qualité  
  
-   Activer la prise en charge d’un nouveau langage  
  
-   Ajouter un type de projet personnalisé  
  
-   Atteindre des millions de développeurs par le biais de la galerie Visual Studio  
  
 Si vous n’avez jamais rédigé une extension de Visual Studio avant, vous devriez trouver plus d’informations sur ces fonctionnalités et à [commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installer le SDK Visual Studio  
 À partir de Visual Studio 2015, vous n’installez pas le Kit de développement logiciel Visual Studio à partir du centre de téléchargement. Il est inclus comme fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2015  
 Le SDK Visual Studio a certaines nouvelles fonctionnalités, y compris des ampoules et nouveaux éléments de projet qui vous permettent de créer des commandes de menu, les fenêtres Outil et les extensions de l’éditeur à l’aide d’un package VSIX. Pour plus d’informations, consultez [What ' s New in Visual Studio 2015 SDK](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Lignes directrices pour l’expérience utilisateur dans Visual Studio  
 Obtenir des conseils pour la conception de l’interface utilisateur pour votre extension dans [recommandations pour l’expérience utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Vous pouvez également apprendre à rendre votre extension de l’aspect souhaité sur les appareils à résolution élevée avec notre [traite des problèmes de PPP](../extensibility/addressing-dpi-issues2.md) rubrique.  
  
 Tirer parti de la [Service d’images et de catalogue](../extensibility/image-service-and-catalog.md) pour la gestion des images exceptionnelles et la prise en charge des thèmes et des résolutions élevées.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Recherche et l’installation des Extensions Visual Studio existants  
 Vous pouvez trouver des extensions Visual Studio dans le **Extensions et mises à jour** boîte de dialogue sur le **outils** menu. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également trouver des extensions dans le [galerie Visual Studio](https://visualstudiogallery.msdn.microsoft.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Informations de référence sur le SDK Visual Studio  
 Vous pouvez trouver la référence d’API du Kit de développement logiciel Visual Studio sur [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Exemples du Kit de développement logiciel Visual Studio  
 Vous trouverez des exemples d’open source d’extensions du Kit de développement logiciel Visual Studio sur GitHub à l’adresse [exemples Visual Studio](https://aka.ms/vs2015sdksamples). Ce référentiel GitHub contient des exemples qui illustrent différentes fonctionnalités extensibles dans Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Autres ressources du Kit de développement logiciel Visual Studio  
 Si vous avez des questions sur l’extensibilité de Visual Studio ou que vous souhaitez partager vos expériences de développement d’extensions, vous pouvez utiliser la [Forum Visual Studio Extensibility](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [ExtendVS groupe Chat](https://gitter.im/Microsoft/extendvs).  
  
 Vous trouverez plus d’informations dans le [VSX aventurer blog](http://blogs.msdn.com/b/vsx/) et un nombre de blogs écrits par des Microsoft MVPs :  
  
-   [Extensions Visual Studio favoris](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extension de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Comment : migrer des projets d’extensibilité vers Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [Forum aux questions : Conversion des compléments en extensions VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [La gestion de plusieurs Threads en Code managé](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajout de commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)   
 [Extension et personnalisation de Windows de l’outil](../extensibility/extending-and-customizing-tool-windows.md)   
 [Éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md)   
 [Extension des projets](../extensibility/extending-projects.md)   
 [Options et paramètres d’extension utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Création de modèles de projets et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md)   
 [Étendre les propriétés et la fenêtre des propriétés](../extensibility/extending-properties-and-the-property-window.md)   
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [À l’aide et fourniture de Services](../extensibility/using-and-providing-services.md)   
 [Extension des Services connectés](../extensibility/extending-connected-services.md)   
 [Gestion de VSPackages](../extensibility/managing-vspackages.md)   
 [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Proposent des Extensions de Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dans le Kit de développement logiciel de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Prise en charge pour le SDK Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Référence du Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk-reference.md)

