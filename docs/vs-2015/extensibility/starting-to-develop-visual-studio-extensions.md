---
title: Début du développement des extensions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- getting started, Visual Studio integration
- Visual Studio, integration
ms.assetid: 8fe5e2ab-a424-4173-9d39-dd082c4d58d0
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d62a4c6cc45681fe6a66ae57df2e1da1d1cc12e0
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850595"
---
# <a name="starting-to-develop-visual-studio-extensions"></a>Lancement du développement d’extensions Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous n’avez jamais écrit une extension Visual Studio, vous avez probablement des questions. Nous avons répertorié quelques-uns des plus courants ici. Si vous ne voyez pas les informations que vous recherchez, utilisez les boutons de commentaires (**cette page vous a-t-elle été utile ?** au bas de l’écran) pour vous demander ce que vous voulez.

## <a name="what-software-do-i-need-to-develop-visual-studio-extensions"></a>De quel logiciel ai-je besoin pour développer des extensions Visual Studio ?
 Vous devez installer le kit de développement logiciel (SDK) Visual Studio 2015 en plus de Visual Studio 2015 pour développer des extensions Visual Studio.   Vous pouvez installer le kit de développement logiciel (SDK) Visual Studio 2015 dans le cadre de la configuration standard, ou vous pouvez l’installer ultérieurement. Pour plus d’informations sur l’installation du kit de développement logiciel (SDK) Visual Studio, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="what-kinds-of-things-can-i-do-with-visual-studio-extensions"></a>Quels sont les types de choses que je peux faire avec les extensions Visual Studio ?
 Le ciel est la limite lorsqu’il s’agit d’imaginer différentes extensions de Visual Studio. Bien entendu, la plupart des extensions ont un effet sur l’écriture de code, mais cela ne doit pas être le cas. Voici quelques exemples des types d’extensions que vous pouvez générer :

- Prise en charge des langues qui ne sont pas incluses dans Visual Studio, avec la coloration de la syntaxe, IntelliSense et le compilateur et la prise en charge du débogage

- Outils de productivité qui étendent l’expérience IDE de base avec des modèles supplémentaires, la refactorisation de code, de nouvelles boîtes de dialogue ou des fenêtres outil

- Concepteurs spécifiques à un domaine pour des scénarios tels que la conception de données ou le support Cloud

  Pour obtenir des exemples d’extensions, consultez le [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Vous pouvez également jeter un coup d’œil aux [extensions open source de Visual Studio](https://github.com/Microsoft/extendvs/blob/master/CommunityExtensions.md).

## <a name="which-visual-studio-features-can-i-extend"></a>Quelles fonctionnalités Visual Studio puis-je étendre ?
 En théorie, vous pouvez étendre quasiment n’importe quelle partie de Visual Studio : menus, barres d’outils, commandes, fenêtres, solutions, projets, éditeurs, etc.

 Dans la pratique, nous avons découvert que les fonctionnalités que la plupart des gens souhaitent étendre sont des commandes, des menus et des barres d’outils, des fenêtres, des fonctionnalités IntelliSense et des projets. Voici des liens vers les sections appropriées :

- [Extension des menus et des commandes](../extensibility/extending-menus-and-commands.md): ajoutez vos propres éléments aux menus et barres d’outils de Visual Studio. Vous pouvez les utiliser pour lancer de nouvelles fonctionnalités Visual Studio ou vos propres applications d’assistance externe. Vous pouvez également fournir des raccourcis personnalisés pour vos éléments de menu.

- [Extension et personnalisation des fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md): étendre les fenêtres outil existantes ou créer vos propres fenêtres outil. Par exemple, vous pouvez ajouter de nouvelles propriétés aux **Propriétés**, ou vous pouvez créer une nouvelle fenêtre outil pour ajouter des fonctionnalités supplémentaires.

- [Extensions du service de langage et](../extensibility/editor-and-language-service-extensions.md)de l’éditeur : ajoutez vos propres personnalisations IntelliSense fournies pour les langages Visual Studio, ou créez la prise en charge de nouveaux langages de programmation. Vous pouvez créer des saisies semi-automatiques des instructions, des suggestions et de nouvelles info-bulles Info-bulles. Avec les ampoules, vous pouvez ajouter des suggestions de refactorisation et des correctifs de code pour prendre en charge les nouveaux langages de programmation.

- [Extension des projets](../extensibility/extending-projects.md)

- [Extension des options et des paramètres utilisateur](../extensibility/extending-user-settings-and-options.md)

- [Extension des propriétés et la fenêtre Propriétés](../extensibility/extending-properties-and-the-property-window.md)

- [Extension d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)

- [Shell isolé Visual Studio](../extensibility/visual-studio-isolated-shell.md)

## <a name="BKMK_ProjectTemplate"></a>Quels modèles de projet sont fournis par le VSSDK ?
 Les deux principaux types d’extensions sont les VSPackages et les extensions MEF. En général, les extensions VSPackage sont utilisées pour les extensions qui utilisent ou étendent des commandes, des fenêtres outil et des projets. Les extensions MEF permettent d’étendre ou de personnaliser l’éditeur Visual Studio.

 Pour les C# extensions Visual et Visual Basic, le VSSDK fournit un modèle de projet VSIX vide que vous pouvez utiliser avec les nouveaux modèles d’élément qui créent des commandes de menu, des fenêtres outil et des extensions d’éditeur. Pour plus d’informations, consultez [Nouveautés du kit de développement logiciel (SDK) Visual Studio 2015](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md). Vous pouvez également utiliser ce modèle pour empaqueter des modèles de projet, des extraits de code et d’autres artefacts à distribuer à d’autres utilisateurs.

 Pour C++, l’Assistant VSPackage fournit le code permettant d’ajouter des commandes de menu, des fenêtres outil et des éditeurs personnalisés.

 Le modèle d’interpréteur de commandes isolé est utilisé pour empaqueter une extension dans une version de l’interpréteur de commandes Visual Studio que vous pouvez marquer et distribuer comme vous le souhaitez. Les rubriques suivantes vous montrent comment commencer avec chaque type d’extension :

- Commandes de menu : [création d’une extension à l’aide d’une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)

- Fenêtres outil : [création d’une extension avec une fenêtre outil](../extensibility/creating-an-extension-with-a-tool-window.md)

- Extensions [de l’éditeur : création d’une extension avec un modèle d’élément d’éditeur](../extensibility/creating-an-extension-with-an-editor-item-template.md)

- VSPackages de base : [création d’une extension avec un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

- Modèle de projet VSIX : [prise en main avec le modèle de projet VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)

- Shell isolé Visual Studio : [procédure pas à pas : création d’une application Shell isolée de base](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)

## <a name="how-do-i-get-my-extension-to-look-like-visual-studio"></a>Comment faire faire en sorte que mon extension ressemble à Visual Studio ?
 Bénéficiez de conseils utiles pour concevoir l’interface utilisateur de votre extension dans [les instructions d’expérience utilisateur de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="where-can-i-find-examples-of-vssdk-code"></a>Où puis-je trouver des exemples de code VSSDK ?
 Chacun des liens figurant dans la section précédente contient des procédures pas à pas qui vous montrent comment implémenter des fonctionnalités spécifiques. Vous trouverez également des exemples VSSDK Open source sur GitHub dans [exemples Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="how-can-i-distribute-my-extension"></a>Comment distribuer mon extension ?
 Vous pouvez installer votre extension sur un autre ordinateur ou l’envoyer à vos amis sous la forme d’un fichier. vsix, que vous installez en double-cliquant dessus. Vous trouverez plus d’informations sur les packages VSIX dans la publication d' [Extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md).

 Vous pouvez également publier votre extension sur la Galerie Visual Studio, ce qui la rend visible pour un grand nombre de clients Visual Studio. Pour obtenir un exemple d’empaquetage d’une extension pour la Galerie, consultez [procédure pas à pas : publication d’une extension Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md). Pour plus d’informations sur ce que vous devez faire pour publier sur la Galerie, consultez [produits et extensions pour Visual Studio](https://visualstudiogallery.msdn.microsoft.com/).
