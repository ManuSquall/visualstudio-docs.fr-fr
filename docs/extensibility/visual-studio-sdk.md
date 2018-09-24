---
title: SDK Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 794d1bae562bf107d9986a132a44d4fa95aec20d
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495815"
---
# <a name="visual-studio-sdk"></a>SDK Visual Studio
Le SDK Visual Studio vous permet d’étendre les fonctionnalités de Visual Studio ou d’intégrer de nouvelles fonctionnalités à Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’à la place de marché Visual Studio. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :  
  
-   Ajouter des commandes, des boutons, des menus et autres éléments d’interface utilisateur à l’IDE  
  
-   Ajouter des fenêtres Outil pour les nouvelles fonctionnalités  
  
-   Étendre IntelliSense pour une langue donnée, ou fournir IntelliSense pour les nouveaux langages de programmation  
  
-   Utiliser des ampoules pour fournir des indicateurs et des suggestions pour aider les développeurs à écrivent du code de meilleure qualité  
  
-   Activer la prise en charge d’un nouveau langage  
  
-   Ajouter un type de projet personnalisé  
  
-   Atteindre des millions de développeurs via Visual Studio Marketplace  
  
 Si vous n’avez jamais rédigé une extension de Visual Studio avant, vous devriez trouver plus d’informations sur ces fonctionnalités et à [commencer à développer des extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio  
 Le SDK Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit SDK VS par la suite. Pour plus d’informations, consultez [installer le SDK Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017  
 Le SDK Visual Studio a certaines nouvelles fonctionnalités comme le format de v3 VSIX ainsi que les dernières modifications, ce qui peuvent vous obliger à mettre à jour votre extension. Pour plus d’informations, consultez [quelles sont les nouveautés dans le Kit de développement logiciel Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).  
  
## <a name="visual-studio-user-experience-guidelines"></a>Recommandations pour l’expérience utilisateur Visual Studio  
 Obtenir des conseils pour la conception de l’interface utilisateur pour votre extension dans [recommandations pour l’expérience utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
 Vous pouvez également apprendre à rendre votre extension de l’aspect souhaité sur les appareils à résolution élevée avec la [adresse PPP émet](../extensibility/addressing-dpi-issues2.md) article.  
  
 Tirer parti de la [service et le catalogue de l’Image](../extensibility/image-service-and-catalog.md) pour la gestion des images exceptionnelles et la prise en charge des thèmes et des résolutions élevées.  
  
## <a name="find-and-install-existing-visual-studio-extensions"></a>Rechercher et installer des extensions Visual Studio existantes  
 Vous pouvez trouver des extensions Visual Studio dans le **Extensions et mises à jour** boîte de dialogue sur le **outils** menu. Pour plus d’informations, consultez [rechercher et utiliser les Extensions de Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également trouver des extensions dans le [Visual Studio marketplace](https://marketplace.visualstudio.com/)  
  
## <a name="visual-studio-sdk-reference"></a>Référence de Visual Studio SDK  
 Vous pouvez trouver la référence d’API du Kit de développement logiciel Visual Studio sur [référence du Kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md).  
  
## <a name="visual-studio-sdk-samples"></a>Exemples pour Visual Studio SDK  
 Vous trouverez des exemples d’open source d’extensions du Kit de développement logiciel Visual Studio sur GitHub à l’adresse [exemples Visual Studio](https://aka.ms/vs2015sdksamples). Ce référentiel GitHub contient des exemples qui illustrent différentes fonctionnalités extensibles dans Visual Studio.  
  
## <a name="other-visual-studio-sdk-resources"></a>Autres ressources Visual Studio SDK  
 Si vous avez des questions sur l’extensibilité de Visual Studio ou que vous souhaitez partager vos expériences de développement d’extensions, vous pouvez utiliser la [Forum Visual Studio Extensibility](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou [salon de conversation Gitter ExtendVS](https://gitter.im/Microsoft/extendvs).  
  
 Vous trouverez plus d’informations dans le [VSX aventurer blog](https://blogs.msdn.microsoft.com/vsx/) et un nombre de blogs écrits par des Microsoft MVPs :  
  
-   [Extensions Visual Studio préférées](http://geekswithblogs.net/sdorman/archive/2014/10/05/favorite-visual-studio-extensions.aspx)  
  
-   [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)  
  
-   [Extension de Visual Studio](http://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>Voir aussi  
 [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [Comment : migrer des projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)   
 [Forum aux questions : Conversion des compléments en extensions VSPackage](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [Gérer plusieurs threads en code managé](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [Étendre des menus et commandes](../extensibility/extending-menus-and-commands.md)   
 [Ajouter des commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)   
 [Étendre et personnaliser des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md)   
 [Extensions de service d’éditeur et la langue](../extensibility/editor-and-language-service-extensions.md)   
 [Étendre des projets](../extensibility/extending-projects.md)   
 [Étendre les options et paramètres utilisateur](../extensibility/extending-user-settings-and-options.md)   
 [Créer des modèles de projet et d’élément personnalisés](../extensibility/creating-custom-project-and-item-templates.md)   
 [Étendre les propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)   
 [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)   
 [Utilisation et la fourniture de services](../extensibility/using-and-providing-services.md)   
 [Gérer les packages VS](../extensibility/managing-vspackages.md)   
 [Shell Visual Studio isolé](../extensibility/visual-studio-isolated-shell.md)   
 [Expédier les extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)   
 [Dans le Kit de développement logiciel de Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Prise en charge pour le SDK Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)   
 [Archive](../extensibility/archive.md)   
 [Référence de Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
