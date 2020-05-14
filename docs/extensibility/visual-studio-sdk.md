---
title: Studio visuel SDK - France Microsoft Docs
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
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698077"
---
# <a name="visual-studio-sdk"></a>Kit de développement logiciel Visual Studio
Le Visual Studio SDK vous aide à étendre les fonctionnalités visual Studio ou à intégrer de nouvelles fonctionnalités dans Visual Studio. Vous pouvez distribuer vos extensions à d’autres utilisateurs, ainsi qu’au Visual Studio Marketplace. Voici quelques-unes des façons dont vous pouvez étendre Visual Studio :

- Ajoutez des commandes, des boutons, des menus et d’autres éléments d’interface utilisateur à l’IDE

- Ajouter des fenêtres d’outils pour de nouvelles fonctionnalités

- Étendre IntelliSense pour une langue donnée, ou fournir IntelliSense pour les nouveaux langages de programmation

- Utilisez des ampoules pour fournir des conseils et des suggestions qui aident les développeurs à écrire un meilleur code

- Permettre le soutien d’une nouvelle langue

- Ajouter un type de projet personnalisé

- Atteindre des millions de développeurs via le Visual Studio Marketplace

  Si vous n’avez jamais écrit une extension Visual Studio avant, vous devriez trouver plus d’informations sur ces fonctionnalités et à [commencer à développer des extensions Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="install-the-visual-studio-sdk"></a>Installer le SDK Visual Studio
 Le Visual Studio SDK est une fonctionnalité facultative dans la configuration Visual Studio. Vous pouvez également installer le VS SDK plus tard. Pour plus d’informations, voir [Installer le Studio Visuel SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>Quoi de neuf dans le Visual Studio 2017 SDK
 Le Visual Studio SDK a quelques nouvelles fonctionnalités telles que le format VSIX v3 ainsi que des changements de rupture, ce qui peut vous obliger à mettre à jour votre extension. Pour plus d’informations, voir [Ce qui est nouveau dans le Visual Studio 2017 SDK](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md).

## <a name="visual-studio-user-experience-guidelines"></a>Directives d’expérience utilisateur Visual Studio
 Obtenez d’excellents conseils pour concevoir l’interface utilisateur pour votre extension dans [visual Studio directives d’expérience utilisateur](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

 Vous pouvez également apprendre à rendre votre extension fière sur les appareils DPI élevés avec [l’article Address DPI questions.](../extensibility/addressing-dpi-issues2.md)

 Profitez du [service Image et](../extensibility/image-service-and-catalog.md) du catalogue pour une excellente gestion de l’image et un support pour un DPI et un thème élevés.

## <a name="find-and-install-existing-visual-studio-extensions"></a>Trouver et installer les extensions Visual Studio existantes
 Vous pouvez trouver des extensions Visual Studio dans le dialogue **Extensions et Mises à jour** sur le menu **Tools.** Pour plus d’informations, voir [Localiser et utiliser Visual Studio Extensions](../ide/finding-and-using-visual-studio-extensions.md). Vous pouvez également trouver des extensions dans le [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

## <a name="visual-studio-sdk-reference"></a>Référence Visual Studio SDK
 Vous pouvez trouver la référence Visual Studio SDK API à [Visual Studio SDK Reference](../extensibility/visual-studio-sdk-reference.md).

## <a name="visual-studio-sdk-samples"></a>Échantillons de Studio SDK visuel
 Vous pouvez trouver des exemples open source d’extensions VS SDK sur GitHub à [Visual Studio Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples). Ce repo GitHub contient des échantillons qui illustrent diverses caractéristiques extensibles dans Visual Studio.

## <a name="other-visual-studio-sdk-resources"></a>Autres ressources SDK Visual Studio
 Si vous avez des questions sur le VSSDK ou si vous souhaitez partager vos expériences de développement d’extensions, vous pouvez utiliser le [Visual Studio Extensibility Forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) ou le [Chatroom ExtendVS Gitter](https://gitter.im/Microsoft/extendvs).

 Vous pouvez trouver plus d’informations dans le [blog VSX Arcana](https://blogs.msdn.microsoft.com/vsx/) et un certain nombre de blogs écrits par microsoft MVP:

- [Extensions préférées de Visual Studio](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [Extéabilité Visual Studio](http://www.visualstudioextensibility.com/overview/vs/)

- [Extension du studio visuel](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>Voir aussi

- [Créer une extension avec une commande de menu](../extensibility/creating-an-extension-with-a-menu-command.md)
- [Comment : Migrer les projets d’extensibility au Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [FAQ : Conversion des add-ins aux extensions VSPackage](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [Gérer plusieurs threads dans le code géré](../extensibility/managing-multiple-threads-in-managed-code.md)
- [Étendre les menus et les commandes](../extensibility/extending-menus-and-commands.md)
- [Ajouter des commandes aux barres d’outils](../extensibility/adding-commands-to-toolbars.md)
- [Étendre et personnaliser les fenêtres d’outils](../extensibility/extending-and-customizing-tool-windows.md)
- [Extensions de service d’éditeur et de langue](../extensibility/editor-and-language-service-extensions.md)
- [Étendre les projets](../extensibility/extending-projects.md)
- [Étendre les paramètres et les options de l’utilisateur](../extensibility/extending-user-settings-and-options.md)
- [Créez des modèles de projets et d’objets personnalisés](../extensibility/creating-custom-project-and-item-templates.md)
- [Étendre les propriétés et la fenêtre de la propriété](../extensibility/extending-properties-and-the-property-window.md)
- [Étendre d’autres parties de Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)
- [Utilisation et prestation de services](../extensibility/using-and-providing-services.md)
- [Gérer VSPackages](../extensibility/managing-vspackages.md)
- [Coquille isolée Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [Extensions Ship Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Dans le kit SDK Visual Studio](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Prise en charge du SDK Visual Studio](../extensibility/support-for-the-visual-studio-sdk.md)
- [Référence Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)
