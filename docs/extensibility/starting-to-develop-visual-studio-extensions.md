---
title: Commencer à développer des Extensions Visual Studio | Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4a3978ba229dff5f5888a50bf67d263cc2c614e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331756"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Lancement du développement d’extensions Visual Studio

Si vous n’avez jamais rédigé une extension de Visual Studio avant, vous avez probablement quelques questions. Nous avons répertorié parmi les plus fréquents ici. Si vous ne voyez pas les informations que vous recherchez, utilisez les boutons de commentaires (**cette page est-elle utile ?** en bas de l’écran) pour demander ce que vous voulez.

> [!NOTE]
> Cet article s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [extension Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>Quel logiciel besoin développer des extensions Visual Studio ?

Vous devez installer le SDK Visual Studio en plus de Visual Studio pour développer des extensions Visual Studio. Vous pouvez installer le SDK Visual Studio en tant que partie du programme d’installation standard, ou vous pouvez l’installer plus tard. Pour plus d’informations sur l’installation de Visual Studio SDK, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quels types d’éléments puis-je faire avec les extensions Visual Studio ?

Le ciel 's la limite le moment venu à imaginer différentes extensions de Visual Studio. Bien entendu, la plupart des extensions avoir quelque chose à faire avec l’écriture de code, mais qui n’a pas été le cas. Voici quelques exemples de types d’extensions, que vous pouvez créer :

- Prise en charge des langues qui ne sont pas inclus dans Visual Studio, avec la coloration syntaxique, IntelliSense et prise en charge du compilateur et de débogage

- Outils de productivité qui étendent le cœur IDE expérience avec des modèles supplémentaires, les boîtes de dialogue refactorisation, nouveau code ou les fenêtres Outil

- Concepteurs de spécifique à un domaine pour les scénarios tels que la prise en charge la conception ou cloud des données

Pour obtenir des exemples d’extensions, consultez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). De nombreuses extensions sont open source, et la place de marché inclut des liens vers leur référentiel GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Les fonctionnalités de Visual Studio puis-je étendre ?

En théorie, vous pouvez étendre n’importe quelle partie de Visual Studio : menus, barres d’outils, commandes, windows, solutions, projets, éditeurs et ainsi de suite.

Dans la pratique, nous avons découvert que les fonctionnalités que la plupart des gens souhaitent étendre sont des commandes, menus et barres d’outils, windows, IntelliSense et projets. Voici des liens vers les sections correspondantes :

- [Extension des Menus et commandes](../extensibility/extending-menus-and-commands.md): ajouter vos propres éléments de menus de Visual Studio et les barres d’outils. Vous pouvez les utiliser pour lancer de nouvelles fonctionnalités de Visual Studio ou de vos propres applications d’assistance externe. Vous pouvez également fournir des raccourcis personnalisés pour vos éléments de menu.

- [Extension et personnalisation de Windows d’outil](../extensibility/extending-and-customizing-tool-windows.md): étendre des fenêtres Outil existantes ou créer vos propres fenêtres Outil. Par exemple, vous pouvez ajouter de nouvelles propriétés à la **propriétés**, ou vous pouvez créer une nouvelle fenêtre d’outil pour ajouter des fonctionnalités supplémentaires.

- [Éditeur et les Extensions de Service de langage](../extensibility/editor-and-language-service-extensions.md): ajouter vos propres personnalisations les IntelliSense fournis pour les langages de Visual Studio, ou créer de prise en charge de nouveaux langages de programmation. Vous pouvez créer le nouveau complément automatique des instructions, des suggestions et nouvelle info-bulles Info Express. Avec des ampoules, vous pouvez ajouter des suggestions de refactorisation et correctifs de code pour prendre en charge de nouveaux langages de programmation.

- [Extension des projets](../extensibility/extending-projects.md)

- [Extension des options et des paramètres utilisateur](../extensibility/extending-user-settings-and-options.md)

- [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)

- [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell isolé Visual Studio](/visualstudio/extensibility/shell/visual-studio-isolated-shell)

## <a name="BKMK_ProjectTemplate"></a> Les modèles de projet sont fournies par l’extensibilité Visual Studio ?
 Les deux principaux types d’extensions sont des VSPackages et des extensions MEF. En règle générale, les extensions VSPackage sont utilisées pour les extensions qui utilisent ou étendent des commandes, les fenêtres Outil et les projets. Extensions MEF sont utilisées pour étendre ou personnaliser l’éditeur Visual Studio.

 Pour les extensions de Visual c# et Visual Basic, l’extensibilité Visual Studio fournit un modèle de projet VSIX vide que vous pouvez utiliser avec les nouveaux modèles d’élément qui créent des commandes de menu, les fenêtres Outil et les extensions de l’éditeur. Vous pouvez également utiliser ce modèle pour les modèles de projet de package, les extraits de code et les autres artefacts pour la distribution à d’autres utilisateurs.

 Pour C++, l’Assistant package Visual Studio fournit le code pour ajouter des commandes de menu, les fenêtres Outil et les éditeurs personnalisés.

 Le modèle de Shell isolé est utilisé pour un package d’extension dans une version de l’interpréteur de commandes de Visual Studio que vous pouvez personnaliser et distribuer en tant que les vôtres. Les rubriques suivantes vous montrent comment bien démarrer avec chaque type d’extension :

- Commandes de menu : [Création d’une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Fenêtres d’outil : [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensions de l’éditeur : [Création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- Packages VS de base : [Création d’une extension avec un package VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modèle de projet VSIX : [Bien démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Comment obtenir mon extension ressemble à Visual Studio ?
 Obtenir des conseils pour la conception de l’interface utilisateur pour votre extension dans [recommandations pour l’expérience utilisateur Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Où puis-je trouver des exemples de code d’extensibilité Visual Studio ?
 Les liens répertoriés dans la section précédente ont des procédures pas à pas qui vous montrent comment implémenter des fonctionnalités spécifiques. Vous trouverez également open source exemples d’extensibilité Visual Studio sur GitHub à l’adresse [exemples Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Comment puis-je distribuer mon extension ?
 Vous pouvez installer votre extension sur un autre ordinateur ou l’envoyer à vos amis en tant qu’un fichier .vsix, que vous installez en double-cliquant dessus. Vous trouverez plus d’informations sur les packages VSIX à [de livraison des Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Vous pouvez également publier votre extension dans Visual Studio Marketplace, ce qui le rend visible à un grand nombre de clients de Visual Studio. Pour obtenir un exemple d’empaquetage d’une extension à la place de marché, consultez [procédure pas à pas : Publication d’une Extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Pour plus d’informations sur ce que vous devez faire pour publier sur la place de marché, consultez [produits et Extensions pour Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Voir aussi

- [Extension de Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac)