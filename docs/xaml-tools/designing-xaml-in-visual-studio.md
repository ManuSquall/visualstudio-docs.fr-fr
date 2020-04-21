---
title: Design XAML en studio visuel et dans Blend for Visual Studio
titleSuffix: ''
ms.date: 02/28/2020
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: eb18a2face5d9f1831bec35379a423f272c3e6ce
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649822"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Concevoir du code XAML dans Visual Studio et Blend pour Visual Studio

Visual Studio et Blend pour Visual Studio fournissent tous deux des outils visuels conçus pour générer des interfaces utilisateur attrayantes et des expériences multimédias élaborées avec XAML pour différents types d’applications. Ces deux environnements de développement intégré (IDE) partagent un ensemble de fonctionnalités, y compris un éditeur XAML visuel (concepteur). Blend pour Visual Studio, qui prend en charge les plateformes WPF et UWP, fournit des outils supplémentaires pour concevoir des états visuels et créer des animations.

Vous pouvez basculer entre Visual Studio et Blend pour Visual Studio, et vous pouvez même ouvrir un même projet simultanément dans les deux environnements IDE. Les modifications qui ont été enregistrées dans les fichiers XAML dans l’un des environnements IDE peuvent être appliquées par le biais d’un rechargement automatique, lorsque vous basculez vers l’autre environnement IDE. Vous pouvez contrôler le comportement de rechargement en naviguant vers **Outils** > **Options** > **Environment** > **Documents** dans l’un ou l’autre IDE.

## <a name="installation"></a>Installation

- Pour créer des applications WPF, installez la charge de travail **Développement .NET Desktop** dans Visual Studio. Blend pour Visual Studio sera également installé.

     ![Capture d’écran de la charge de travail .NET Desktop Development de l’installateur Studio visuel](../xaml-tools/media/dotnet-desktop-dev-workload.png)

- Pour créer des applications UWP, installez la charge de travail **Développement pour la plateforme Windows universelle** dans Visual Studio. Blend pour Visual Studio sera également installé.

     ![Capture d’écran de la charge de travail de développement de la plate-forme Windows universelle de l’installateur visual Studio](../xaml-tools/media/uwp-workload.png)

- Pour créez des applications Xamarin.Forms, installer la charge de travail **Développement mobile en .NET** dans Visual Studio. Blend pour Visual Studio *n’est pas* installé ; Blend ne prend pas en charge les applications Xamarin.Forms.

     ![Capture d’écran du développement mobile avec la charge de travail .NET de l’installateur studio visuel](../xaml-tools/media/mobile-dev-dotnet-workload.png)

## <a name="shared-capabilities"></a>Fonctionnalités partagées

Pour la plupart des tâches de développement de base, Visual Studio et Blend pour Visual Studio partagent le même ensemble de fenêtres et de fonctionnalités, avec quelques légères différences. Les fonctions clés sont notamment les suivantes :

- **IntelliSense:** Les deux IDEs prennent en charge les capacités IntelliSense telles que l’achèvement des relevés.

- **Débogage:** Vous pouvez déboguer dans [Visual Studio](inspect-xaml-properties-while-debugging.md) et [Blend for Visual Studio](../xaml-tools/debug-xaml-in-blend.md), y compris le réglage des points d’arrêt dans le code pour déboguer une application en cours d’exécution et en utilisant Hot [Reload](../xaml-tools/xaml-hot-reload.md) pour modifier votre code XAML pendant que l’application est en cours d’exécution. Pour maintenir une expérience de débogage cohérente avec Visual Studio, Blend pour Visual Studio inclut la plupart des fenêtres de débogage et barres d’outils de Visual Studio.

- **Recharge du fichier :** Vous pouvez modifier vos fichiers XAML dans Visual Studio ou Blend for Visual Studio. Les fichiers modifiés qui ont été enregistrés sont rechargés automatiquement lorsque vous passez d’un IDE à l’autre. Vous pouvez contrôler le comportement de rechargement en naviguant vers **Outils** > **Options** > **Environment** > **Documents** dans l’un ou l’autre IDE.

- **Mises en page et réglages synchronisés :** Les mises en page des fenêtres et les paramètres de l’outil de personnalisation de conception pour Visual Studio ou Blend for Visual Studio sont synchronisés sur vos appareils et versions lorsque vous vous connectez avec le même compte de personnalisation. Consultez [Synchroniser les paramètres sur plusieurs ordinateurs](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Fonctionnalités avancées dans Blend pour Visual Studio

Pour accroître votre productivité, utilisez Blend pour Visual Studio pour les tâches suivantes. Pour ces tâches, Blend pour Visual Studio s’avère plus rapide et plus riche en fonctionnalités que le concepteur Visual Studio ou le code seul.

| Tâche | Visual Studio | Blend pour Visual Studio | Informations complémentaires |
| - | - | - | - |
| **Concevoir des états visuels** | Il n’existe pas d’outil permettant de concevoir des états visuels. Vous devez les créer par programmation. | Utilisez les outils de conception pour modifier l’apparence d’un contrôle en fonction de son état. | [États visuels](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Créer des animations** |Il n'existe aucun outil de conception d'animations ; vous devez les créer par programmation. Cela nécessite une bonne connaissance du système d'animation et de minutage de WPF, ainsi que des compétences étendues en matière de codage.|Vous créez les animations de manière visuelle et pouvez en afficher un aperçu dans Blend pour Visual Studio. Il s'agit d'une méthode plus rapide et plus précise que celle qui consiste à créer des animations dans le code. Vous pouvez ajouter des déclencheurs pour gérer l'interaction des utilisateurs et basculer vers le code pour ajouter des gestionnaires d'événements et d'autres fonctionnalités.|[Animer des objets](../xaml-tools/animate-objects-in-xaml-designer.md)|
|**Transformer des formes et du texte en tracés pour une manipulation plus facile**|Non pris en charge.|Vous pouvez modifier les formes (telles que des rectangles et des ellipses) de manière subtile ou radicale en les convertissant en tracés, ce qui confère un meilleur contrôle d'édition. Vous pouvez remodeler ou combiner des tracés et créer des tracés composites à partir de plusieurs formes.<br /><br />Vous pouvez aussi convertir des blocs de texte en tracés pour les manipuler en tant qu'images vectorielles.|[Dessiner des formes et des tracés](../xaml-tools/draw-shapes-and-paths.md)|
|**Modifier des contrôles, des modèles et des styles**|Nécessite du codage et une connaissance des styles et modèles WPF.|Transformez une image en contrôle.<br /><br />Utilisez les outils d'édition de modèle pour apporter des modifications à des contrôles, styles et modèles en quelques clics de souris.<br /><br />Par exemple, vous pouvez utiliser les ressources de style Blend pour Visual Studio pour implémenter des contrôles WPF courants (tels que des boutons, zones de liste, barres de défilement, menus, etc.) et modifier leur couleur, style ou modèle sous-jacent directement dans Blend pour Visual Studio. Vous pouvez ensuite basculer vers le code pour apporter des touches finales, le cas échéant.|[Modifier le style des objets](modify-the-style-of-objects-in-blend.md)|
|**Connecter votre interface utilisateur à des données**|Vous pouvez créer une source de données à partir de ressources, telles que des bases de données SQL Server, des services WCF ou web, des objets ou des listes SharePoint, et lier la source de données aux contrôles de votre interface utilisateur.<br /><br />Des données doivent être créées manuellement au moment de la conception pour une expérience de conception interactive.|Pour les applications .NET Framework, créez des exemples de données en toute simplicité à des fins de prototypage et de test. Passez à des données en direct dès que vous êtes prêt.<br /><br />Les capacités de génération de données de Blend pour Visual Studio sont remarquables (vous pouvez facilement ajouter noms, nombres, URL et photos à la volée) et peuvent vous faire gagner beaucoup de temps.<br /><br />Pour les données en direct, vous pouvez lier les contrôles de votre interface utilisateur à un fichier XML ou à une source de données CLR.|[Afficher des données](display-data-in-blend.md)|

Pour plus d’informations sur la conception XAML avancée, consultez [Créer une interface utilisateur à l’aide de Blend pour Visual Studio](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML](xaml-overview.md)
- [Vue d’ensemble de Blend for Visual Studio](creating-a-ui-by-using-blend-for-visual-studio.md)
