---
title: Visual Studio SDK | Documents Microsoft
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
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: bf8c558d01538d477aee3670b3c119d72a83878d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-sdk"></a>SDK Visual Studio
Le Kit de développement logiciel Visual Studio vous permet d’étendre les fonctionnalités de Visual Studio ou d’intégrer de nouvelles fonctionnalités à Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi que pour Visual Studio Marketplace. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :  
  
-   Ajouter des commandes, des boutons, des menus et autres éléments d’interface utilisateur à l’IDE  
  
-   Ajouter des fenêtres Outil de nouvelles fonctionnalités  
  
-   Étendre IntelliSense pour une langue donnée, ou fournir IntelliSense pour les nouveaux langages de programmation  
  
-   Utiliser les ampoules pour fournir des indicateurs et des suggestions pour aider les développeurs à écrivent du code mieux  
  
-   Activer la prise en charge d’un nouveau langage  
  
-   Ajouter un type de projet personnalisés  
  
-   Atteindre des millions de développeurs via Visual Studio Marketplace  
  
 Si vous n’avez jamais écrit une extension de Visual Studio avant, vous devez rechercher plus d’informations sur ces fonctionnalités et [commencer à développer des Extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="installing-the-visual-studio-sdk"></a>Installer le Kit de développement logiciel de Visual Studio  
 Le Kit de développement logiciel Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS ultérieurement. Pour plus d’informations, consultez [l’installation de Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017  
 Le Kit de développement logiciel Visual Studio a certaines nouvelles fonctionnalités, notamment le format v3 VSIX ainsi que les dernières modifications qui peuvent vous amener à mettre à jour votre extension. Pour plus d’informations, consultez [Nouveautés dans le Kit de développement logiciel Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Recommandations pour l’expérience utilisateur Visual Studio  
 Obtenir des conseils pour la conception de l’interface utilisateur pour votre extension dans [recommandations expérience utilisateur de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Vous pouvez également apprendre comment rendre votre extension superbes sur les appareils PPP élevés avec notre [traite des problèmes de PPP](../extensibility/addressing-dpi-issues2.md) rubrique.  
  
 Tirer parti de la [Service d’images et de catalogue](../extensibility/image-service-and-catalog.md) pour la gestion de l’image de grande et de prise en charge des thèmes et la haute résolution.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>Rechercher et installer des Extensions Visual Studio existants  
 Vous pouvez rechercher des extensions Visual Studio dans le **Extensions et mises à jour** boîte de dialogue sur le **outils** menu. Pour plus d’informations, consultez [Recherche et utilisation des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également rechercher des extensions dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Référence du Kit de développement logiciel Visual Studio  
 Vous pouvez trouver la référence d’API du Kit de développement logiciel Visual Studio à [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Exemples du Kit de développement logiciel Visual Studio  
 Vous trouverez des exemples d’open source d’extensions du Kit de développement logiciel Visual Studio sur GitHub à l’adresse [exemples Visual Studio](https://aka.ms/vs2015sdksamples). Ce référentiel GitHub contient des exemples qui illustrent différentes fonctionnalités extensibles dans Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Autres ressources du Kit de développement logiciel Visual Studio  
 Si vous avez des questions sur l’extensibilité de Visual Studio ou que vous souhaitez partager vos expériences de développement d’extensions, vous pouvez utiliser la [Forum d’extensibilité de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [un accroissement ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).  
  
 Vous trouverez plus d’informations dans le [VSX aventurer blog](http://blogs.msdn.com/b/vsx/) et un nombre de blogs écrite par MVPs Microsoft :  
  
-   [Extensions préférées Visual Studio](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extension de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Comment : migrer des projets d’extensibilité pour Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Forum aux questions : Convertir des compléments Extensions VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [La gestion de plusieurs Threads en Code managé](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajouter des commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)   
 [Étendre et personnaliser des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md)   
 [L’éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md)   
 [Étendre des projets](../extensibility/extending-projects.md)   
 [Options et paramètres d’extension utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Création de projets et modèles d’élément](../extensibility/creating-custom-project-and-item-templates.md)   
 [Étendre les propriétés et la fenêtre des propriétés](../extensibility/extending-properties-and-the-property-window.md)   
 [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [À l’aide et fournir des Services](../extensibility/using-and-providing-services.md)   
 [Gestion des VSPackages](../extensibility/managing-vspackages.md)   
 [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)   
 [Envoi des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dans le Kit de développement logiciel de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Prise en charge pour le SDK de Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Référence du Kit de développement logiciel (SDK) Visual Studio](../extensibility/visual-studio-sdk-reference.md)
