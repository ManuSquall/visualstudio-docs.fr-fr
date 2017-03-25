---
title: "Commencer à développer des Extensions Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 29
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: dc5416fe979ed3e52ef2df77e5b495cb98038dcd
ms.lasthandoff: 03/07/2017

---
# <a name="starting-to-develop-visual-studio-extensions"></a>Commencer à développer des Extensions Visual Studio
Si vous n’avez jamais rédigé une extension Visual Studio avant, vous avez probablement quelques questions. Nous avons répertorié parmi les plus courants ici. Si vous ne voyez pas les informations que vous recherchez, utilisez les boutons de commentaires (**cette page ont-elles été utiles ?** en bas de l’écran) pour demander ce que vous souhaitez.  
  
## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Quel logiciel ai-je besoin développer des extensions Visual Studio ?  
 Vous devez installer le SDK de Visual Studio en plus de Visual Studio pour développer des extensions Visual Studio. Vous pouvez installer le Kit de développement logiciel Visual Studio dans le cadre du programme d’installation standard, ou vous pouvez l’installer plus tard. Pour plus d’informations sur l’installation de Visual Studio SDK, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quels types d’éléments puis-je faire avec les extensions Visual Studio ?  
 Votre imagination sera la limite lorsqu’il faut imaginer différentes extensions de Visual Studio. Bien entendu, la plupart des extensions avoir quelque chose à faire avec l’écriture de code, mais qui n’a pas le cas. Voici quelques exemples de types d’extensions, que vous pouvez créer :  
  
-   Prise en charge des langues qui ne sont pas inclus dans Visual Studio, avec la coloration de syntaxe, IntelliSense et prise en charge du compilateur et de débogage  
  
-   Outils de productivité qui s’étendent du noyau IDE expérience avec les autres modèles, boîtes de dialogue refactorisation, le nouveau code ou les fenêtres Outil  
  
-   Concepteurs spécifique à un domaine pour des scénarios tels que la prise en charge conception ou cloud des données  
  
 Pour obtenir des exemples d’extensions, consultez le [la galerie Visual Studio](https://visualstudiogallery.msdn.microsoft.com/). Vous pouvez également jeter un œil [Open Source d’Extensions Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).  
  
## <a name="which-visual-studio-features-can-i-extend"></a>Les fonctionnalités de Visual Studio puis-je étendre ?  
 En théorie, vous pouvez étendre n’importe quelle partie de Visual Studio : menus, barres d’outils, commandes, windows, solutions, projets, éditeurs et ainsi de suite.  
  
 Dans la pratique, nous avons découvert que les fonctionnalités de la plupart des personnes veulent étendre sont des commandes, menus et barres d’outils, windows, IntelliSense et projets. Voici des liens vers les sections pertinentes :  
  
-   [Extension des Menus et des commandes](../extensibility/extending-menus-and-commands.md): ajouter vos propres éléments de menus de Visual Studio et les barres d’outils. Vous pouvez les utiliser pour lancer de nouvelles fonctionnalités de Visual Studio ou de vos propres applications d’assistance externe. Vous pouvez également fournir des raccourcis personnalisés pour vos éléments de menu.  
  
-   [Extension et personnalisation des fenêtres Outil](../extensibility/extending-and-customizing-tool-windows.md): étendre des fenêtres Outil existantes ou créer vos propres fenêtres Outil. Par exemple, vous pouvez ajouter de nouvelles propriétés à la **propriétés**, ou vous pouvez créer une nouvelle fenêtre outil pour ajouter des fonctionnalités supplémentaires.  
  
-   [Éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md): ajoutez vos propres personnalisations IntelliSense fourni pour les langages de Visual Studio, ou créer de prise en charge de nouveaux langages de programmation. Vous pouvez créer de nouveaux semi-automatique, des suggestions et nouvelle info-bulles Info Express. Avec des ampoules, vous pouvez ajouter des suggestions de refactorisation et les correctifs de code pour prendre en charge de nouveaux langages de programmation.  
  
-   [Extension des projets](../extensibility/extending-projects.md)  
  
-   [Extension des options et des paramètres utilisateur](../extensibility/extending-user-settings-and-options.md)  
  
-   [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)  
  
-   [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
  
-   [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)  
  
##  <a name="BKMK_ProjectTemplate"></a>Les modèles de projet fournis par VSSDK ?  
 Les deux principaux types d’extensions sont des extensions VSPackages et MEF. En règle générale, extensions VSPackage sont utilisées pour les extensions qui utilisent ou étendent les projets, les fenêtres Outil et les commandes. Extensions MEF sont utilisées pour étendre ou personnaliser l’éditeur Visual Studio.  
  
 Pour les extensions de Visual c# et Visual Basic, VSSDK fournit un modèle de projet VSIX vide que vous pouvez utiliser avec les nouveaux modèles d’élément qui créent des commandes de menu, fenêtres d’outils et extensions de l’éditeur. Vous pouvez également utiliser ce modèle pour les modèles de projet de package, les extraits de code et les autres artefacts pour la distribution à d’autres utilisateurs.  
  
 Pour C++, l’Assistant VSPackage fournit le code pour ajouter des commandes de menu, les fenêtres Outil et les éditeurs personnalisés.  
  
 Le modèle de Shell isolé est utilisé pour empaqueter une extension dans une version de l’interface de Visual Studio que vous pouvez personnaliser et distribuer vos propres. Les rubriques suivantes vous montrent comment démarrer avec chaque type d’extension :  
  
-   Commandes de menu : [création d’une Extension avec une commande de Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   Fenêtres Outil : [création d’une Extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   Extensions de l’éditeur : [avec un éditeur de modèle d’élément pour créer une Extension](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   Les packages VS de base : [création d’une Extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
-   Modèle de projet VSIX : [mise en route avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)  
  
-   Isolé du shell Visual Studio : [procédure pas à pas : création d’une Application Shell isolé](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Comment obtenir mon extension ressemble à Visual Studio ?  
 Obtenez des conseils pour la conception de l’interface utilisateur de votre extension dans [recommandations pour l’environnement utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="where-can-i-find-examples-of-vssdk-code"></a>Où puis-je trouver des exemples de code VSSDK ?  
 Les liens répertoriés dans la section précédente ont des procédures pas à pas qui vous montrent comment implémenter des fonctionnalités spécifiques. Vous pouvez également trouver open source exemples VSSDK sur GitHub à l’adresse [exemples Visual Studio](https://aka.ms/vs2015sdksamples).  
  
## <a name="how-can-i-distribute-my-extension"></a>Comment puis-je distribuer mon extension ?  
 Vous pouvez installer votre extension sur un autre ordinateur ou l’envoyer à vos amis en tant qu’un fichier .vsix, vous installez en double-cliquant dessus. Vous trouverez plus d’informations sur les packages VSIX sur [de livraison d’Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Vous pouvez également publier votre extension dans la galerie Visual Studio, ce qui le rend visible à un grand nombre de clients de Visual Studio. Pour obtenir un exemple d’empaquetage d’une extension de la galerie, consultez la page [procédure pas à pas : publication d’une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Pour plus d’informations sur ce que vous devez faire pour publier dans la galerie, consultez la page [produits et Extensions pour Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
