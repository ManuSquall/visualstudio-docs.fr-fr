---
title: SDK Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aceed2833d0083beccf197c4c681f92270a1f9a4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583656"
---
# <a name="visual-studio-sdk"></a>Kit de développement logiciel Visual Studio
Le kit de développement logiciel (SDK) Visual Studio vous aide à étendre les fonctionnalités de Visual Studio ou à intégrer de nouvelles fonctionnalités dans Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’à la Visual Studio Marketplace. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :

- Ajouter des commandes, des boutons, des menus et d’autres éléments d’interface utilisateur à l’IDE

- Ajouter des fenêtres outil pour les nouvelles fonctionnalités

- Étendez IntelliSense pour un langage donné ou fournissez IntelliSense pour les nouveaux langages de programmation

- Utilisez des ampoules pour fournir des conseils et des suggestions pour aider les développeurs à écrire du code plus performant

- Activer la prise en charge d’une nouvelle langue

- Ajouter un type de projet personnalisé

- Atteignez des millions de développeurs via le Visual Studio Marketplace

  Si vous n’avez jamais écrit une extension Visual Studio, vous trouverez plus d’informations sur ces fonctionnalités et sur le [développement d’extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio
 Le kit de développement logiciel (SDK) Visual Studio est une fonctionnalité facultative dans le programme d’installation de Visual Studio. Vous pouvez également installer le kit de développement logiciel (SDK) Visual Studio plus tard. Pour plus d’informations, consultez [installer le kit de développement logiciel (SDK) Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-sdk"></a>Nouveautés du kit de développement logiciel (SDK) Visual Studio
 Le kit de développement logiciel (SDK) Visual Studio dispose de nouvelles fonctionnalités, telles que l’avertissement des extensions chargées de façon synchrone et le format VSIX v3, ainsi que des modifications avec rupture, qui peuvent vous obliger à mettre à jour votre extension. Pour plus d’informations, consultez [Nouveautés du kit de développement logiciel (SDK) Visual studio 2019](../extensibility/whats-new-visual-studio-2019-sdk.md) et [Nouveautés du kit de développement logiciel (SDK) Visual Studio 2017](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Instructions pour l’expérience utilisateur de Visual Studio
 Bénéficiez de conseils utiles pour concevoir l’interface utilisateur de votre extension dans [les instructions d’expérience utilisateur de Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Vous pouvez également découvrir comment faire en sorte que votre extension soit intéressante sur les appareils haute résolution avec l’article [problèmes dpi d’adresse](../extensibility/addressing-dpi-issues2.md) .

 Tirez parti du [service d’images et du catalogue](../extensibility/image-service-and-catalog.md) pour une gestion des images exceptionnelle et la prise en charge de la haute résolution et des thèmes.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Rechercher et installer des extensions Visual Studio existantes
 Vous pouvez rechercher les extensions Visual Studio dans la boîte de dialogue **extensions et mises à jour** du menu **Outils** . Pour plus d’informations, consultez [Rechercher et utiliser des extensions Visual Studio](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également trouver des extensions dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Référence du kit de développement logiciel Visual Studio
 Vous trouverez les informations de référence sur l’API du SDK Visual Studio à la [Référence du kit de développement Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Exemples du kit de développement logiciel Visual Studio
 Vous trouverez des exemples Open source d’extensions VS SDK sur GitHub dans [exemples Visual Studio](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Ce référentiel GitHub contient des exemples qui illustrent diverses fonctionnalités extensibles dans Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Autres ressources du kit de développement logiciel (SDK) Visual Studio
 Si vous avez des questions sur le VSSDK ou que vous souhaitez partager vos expériences en développant des extensions, vous pouvez utiliser le [Forum extensibilité de Visual Studio](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou le [Gitter de Gitter ExtendVS](https://gitter.im/Microsoft/extendvs).

 Vous trouverez plus d’informations sur le [blog de Arcana VSX](/archive/blogs/vsx/) et sur un certain nombre de blogs écrits par des MVP Microsoft :

- [Extensions Visual Studio favorites](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Extensibilité de Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Extension de Visual Studio](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Voir aussi

- [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Comment : migrer des projets d’extensibilité vers Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [FAQ : conversion des compléments en extensions VSPackage](../vs-2015/extensibility/faq-converting-add-ins-to-vspackage-extensions.md?view=vs-2015&preserve-view=true)
- [Gérer plusieurs threads dans du code managé](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Étendre des menus et des commandes](../extensibility/extending-menus-and-commands.md)
- [Ajouter des commandes à des barres d’outils](../extensibility/adding-commands-to-toolbars.md)
- [Étendre et personnaliser les fenêtres outil](../extensibility/extending-and-customizing-tool-windows.md)
- [Extensions du service de langage et de l’éditeur](../extensibility/editor-and-language-service-extensions.md)
- [Étendre des projets](../extensibility/extending-projects.md)
- [Étendre les paramètres et les options utilisateur](../extensibility/extending-user-settings-and-options.md)
- [Créer des modèles de projet et d’élément personnalisés](../extensibility/creating-custom-project-and-item-templates.md)
- [Étendre les propriétés et la fenêtre de propriétés](../extensibility/extending-properties-and-the-property-window.md)
- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Utilisation et fourniture de services](../extensibility/using-and-providing-services.md)
- [Gérer VSPackages](../extensibility/managing-vspackages.md)
- [Shell isolé Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Envoyer des extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Dans le kit SDK Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Prise en charge du SDK Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Référence du kit de développement logiciel Visual Studio](../extensibility/visual-studio-sdk-reference.md)