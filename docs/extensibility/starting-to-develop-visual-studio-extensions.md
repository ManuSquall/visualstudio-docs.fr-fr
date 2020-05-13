---
title: Commencer à développer des extensions de studio visuel (fr) Microsoft Docs
ms.date: 09/18/2017
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 744475e61458f7b91ce08fba4d17046df36f5558
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699743"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Lancement du développement d’extensions Visual Studio

Si vous n’avez jamais écrit une extension Visual Studio avant, vous avez probablement quelques questions. Nous avons énuméré quelques-uns des plus communs ici. Si vous ne voyez pas les informations que vous recherchez, utilisez les boutons de rétroaction **(cette page était-elle utile?** au bas de l’écran) pour demander ce que vous voulez.

> [!NOTE]
> Cet article s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, voir [Extending Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac). Pour Visual Studio Code, voir [Visual Studio Code Extension API](https://code.visualstudio.com/api).

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>De quel logiciel ai-je besoin pour développer des extensions Visual Studio ?

Vous devez installer le Visual Studio SDK en plus de Visual Studio afin de développer des extensions Visual Studio. Vous pouvez installer le Studio Visuel SDK dans le cadre d’une configuration régulière, ou vous pouvez l’installer plus tard. Pour plus d’informations sur l’installation du Studio Visuel SDK, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quels types de choses puis-je faire avec les extensions Visual Studio?

Le ciel est la limite quand il s’agit d’imaginer différentes extensions Visual Studio. Bien sûr, la plupart des extensions ont quelque chose à voir avec la rédaction de code, mais cela n’a pas à être le cas. Voici quelques exemples des types d’extensions que vous pouvez construire :

- Prise en charge des langues qui ne sont pas incluses dans Visual Studio, avec coloration syntaxe, IntelliSense, et compilateur et support de déboise

- Outils de productivité qui prolongent l’expérience IDE de base avec des modèles supplémentaires, le refactoring de code, les nouveaux dialogues ou les fenêtres d’outils

- Concepteurs spécifiques au domaine pour des scénarios comme la conception de données ou le support cloud

Pour des exemples d’extensions, consultez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). De nombreuses extensions sont open source, et le Marketplace comprend des liens vers leur pension GitHub.

## <a name="which-visual-studio-features-can-i-extend"></a>Quelles fonctionnalités Visual Studio puis-je étendre ?

En théorie, vous pouvez étendre à peu près n’importe quelle partie de Visual Studio: menus, barres d’outils, commandes, fenêtres, solutions, projets, éditeurs, et ainsi de suite.

Dans la pratique, nous avons constaté que les caractéristiques que la plupart des gens veulent étendre sont des commandes, des menus et des barres d’outils, des fenêtres, IntelliSense, et des projets. Voici des liens vers les sections pertinentes :

- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md): ajoutez vos propres articles aux menus Visual Studio et aux barres d’outils. Vous pouvez les utiliser pour lancer de nouvelles fonctionnalités Visual Studio ou vos propres applications d’aide externes. Vous pouvez également fournir des raccourcis personnalisés pour vos éléments de menu.

- [Extension et personnalisation de Windows outil](../extensibility/extending-and-customizing-tool-windows.md): étendre les fenêtres d’outils existantes ou créer vos propres fenêtres d’outils. Par exemple, vous pouvez ajouter de nouvelles propriétés aux **propriétés,** ou vous pouvez créer une nouvelle fenêtre d’outil pour ajouter des fonctionnalités supplémentaires.

- [Extensions de service d’éditeur et de langue](../extensibility/editor-and-language-service-extensions.md): ajoutez vos propres personnalisations à l’IntelliSense fournie pour les langages Visual Studio, ou créez un support pour de nouveaux langages de programmation. Vous pouvez créer de nouvelles finitions de déclaration, suggestions et nouvelles outils QuickInfo. Avec les ampoules, vous pouvez ajouter des suggestions de refactoring et des correctifs de code pour prendre en charge de nouveaux langages de programmation.

- [Extension des projets](../extensibility/extending-projects.md)

- [Extension des options et des paramètres utilisateur](../extensibility/extending-user-settings-and-options.md)

- [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)

- [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell isolé Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

## <a name="what-project-templates-are-provided-by-the-vssdk"></a><a name="BKMK_ProjectTemplate"></a>Quels modèles de projet sont fournis par le VSSDK ?
 Les deux principaux types d’extensions sont les extensions VSPackages et MEF. En général, les extensions VSPackage sont utilisées pour les extensions qui utilisent ou étendent les commandes, les fenêtres d’outils et les projets. Les extensions MEF sont utilisées pour étendre ou personnaliser l’éditeur Visual Studio.

 Pour les extensions Visual C et Visual Basic, le VSSDK fournit un modèle de projet VSIX vide que vous pouvez utiliser avec les nouveaux modèles d’éléments qui créent des commandes de menu, des fenêtres d’outils et des extensions d’éditeur. Vous pouvez également utiliser ce modèle pour emballer les modèles de projet, les extraits de code et d’autres artefacts pour la distribution à d’autres utilisateurs.

 Pour le C, l’assistant VSPackage fournit le code pour ajouter des commandes de menu, des fenêtres d’outils et des éditeurs personnalisés.

 Le modèle Isolated Shell est utilisé pour emballer une extension dans une version de la coque Visual Studio que vous pouvez marquer et distribuer comme la vôtre. Les sujets suivants vous montrent comment commencer avec chaque type d’extension:

- Commandes de menu : [Création d’une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Fenêtres d’outils : [Création d’une extension avec une fenêtre d’outil](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensions de [l’éditeur : Création d’une extension avec un modèle d’article d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- VSPackages de base : [Création d’une extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modèle de projet VSIX : [Démarrer avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Comment puis-je obtenir mon extension pour ressembler à Visual Studio?
 Obtenez d’excellents conseils pour concevoir l’interface utilisateur pour votre extension dans [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Où puis-je trouver des exemples de code VSSDK ?
 Chacun des liens énumérés dans la section précédente ont étape par étape des procédures pas à pas qui vous montrent comment implémenter des fonctionnalités spécifiques. Vous pouvez également trouver des échantillons open source VSSDK sur GitHub à [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Comment puis-je distribuer mon extension ?
 Vous pouvez installer votre extension sur un autre ordinateur ou l’envoyer à vos amis comme un fichier .vsix, que vous installez en le cliquant en deux clics. Vous pouvez en savoir plus sur les forfaits VSIX à [Shipping Visual Studio Extensions](../extensibility/shipping-visual-studio-extensions.md).

 Vous pouvez également publier votre extension sur le Visual Studio Marketplace, ce qui le rend visible par un grand nombre de clients visual Studio. Par exemple d’emballage d’une extension du marché, voir Procédure pas à [pas: Publier une extension studio visuel](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Pour plus d’informations sur ce que vous devez faire pour publier sur le marché, voir [Produits et extensions pour Visual Studio](/azure/devops/extend/overview?view=vsts).

## <a name="see-also"></a>Voir aussi

- [Extension de Visual Studio pour Mac](/visualstudio/mac/extending-visual-studio-mac)
- [Extension du code visual des studios](https://code.visualstudio.com/api)
