---
title: Concevoir en XAML dans Visual Studio et Blend
titleSuffix: ''
ms.date: 08/05/2019
ms.topic: conceptual
ms.assetid: 288e2415-9fcf-408e-bc35-9848315e14fd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd0ff12b141a50872d586764d2b33bd68f3224fb
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821868"
---
# <a name="design-xaml-in-visual-studio-and-blend-for-visual-studio"></a>Concevoir du code XAML dans Visual Studio et Blend pour Visual Studio

Visual Studio et Blend pour Visual Studio fournissent tous deux des outils visuels conçus pour générer des interfaces utilisateur attrayantes et des expériences multimédias élaborées avec XAML pour différents types d’applications. Ces deux environnements de développement intégré (IDE) partagent un ensemble de fonctionnalités, y compris un éditeur XAML visuel (concepteur). Blend pour Visual Studio, qui prend en charge les plateformes WPF et UWP, fournit des outils supplémentaires pour concevoir des états visuels et créer des animations.

Vous pouvez basculer entre Visual Studio et Blend pour Visual Studio, et vous pouvez même ouvrir un même projet simultanément dans les deux environnements IDE. Les modifications qui ont été enregistrées dans les fichiers XAML dans l’un des environnements IDE peuvent être appliquées par le biais d’un rechargement automatique, lorsque vous basculez vers l’autre environnement IDE. Vous pouvez contrôler le comportement de rechargement en accédant à **Outils** > **Options** > **Environnement** > **Documents**, dans l’un des environnements IDE.

## <a name="installation"></a>Installation

- Pour créer des applications WPF, installez la charge de travail **Développement .NET Desktop** dans Visual Studio. Blend pour Visual Studio sera également installé.
- Pour créer des applications UWP, installez la charge de travail **Développement pour la plateforme Windows universelle** dans Visual Studio. Blend pour Visual Studio sera également installé.
- Pour créez des applications Xamarin.Forms, installer la charge de travail **Développement mobile en .NET** dans Visual Studio. Blend pour Visual Studio *n’est pas* installé ; Blend ne prend pas en charge les applications Xamarin.Forms.

## <a name="shared-capabilities"></a>Fonctionnalités partagées

Pour la plupart des tâches de développement de base, Visual Studio et Blend pour Visual Studio partagent le même ensemble de fenêtres et de fonctionnalités, avec quelques légères différences. Voici quelques points clés :

- **IntelliSense :** les deux IDE prennent en charge les fonctionnalités IntelliSense comme la saisie semi-automatique des instructions.

- **Débogage :** Vous pouvez déboguer du code dans [Visual Studio](../debugger/inspect-xaml-properties-while-debugging.md) et [Blend pour Visual Studio](../debugger/debug-xaml-in-blend.md), y compris définir des points d’arrêt dans le code pour déboguer une application en cours d’exécution et utiliser le [rechargement à chaud](../debugger/xaml-hot-reload.md) pour modifier votre code XAML pendant que l’application s’exécute. Pour maintenir une expérience de débogage cohérente avec Visual Studio, Blend pour Visual Studio inclut la plupart des fenêtres de débogage et barres d’outils de Visual Studio.

- **Rechargement des fichiers :** Vous pouvez modifier vos fichiers XAML dans Visual Studio ou Blend pour Visual Studio. Les fichiers modifiés qui ont été enregistrés sont rechargés automatiquement lorsque vous passez d’un IDE à l’autre. Vous pouvez contrôler le comportement de rechargement en accédant à **Outils** > **Options** > **Environnement** > **Documents**, dans l’un des environnements IDE.

- **Dispositions et paramètres synchronisés :** Dans Visual Studio ou Blend pour Visual Studio, les préférences concernant les dispositions et les paramètres des fenêtres Outil personnalisées sont synchronisées entre vos appareils et vos versions lorsque vous vous connectez avec un même compte de personnalisation. Consultez [Synchroniser les paramètres sur plusieurs ordinateurs](../ide/synchronized-settings-in-visual-studio.md).

## <a name="advanced-capabilities-in-blend-for-visual-studio"></a>Fonctionnalités avancées dans Blend pour Visual Studio

Pour accroître votre productivité, utilisez Blend pour Visual Studio pour les tâches suivantes. Pour ces tâches, Blend pour Visual Studio s’avère plus rapide et plus riche en fonctionnalités que le concepteur Visual Studio ou le code seul.

| Tâche | Visual Studio | Blend pour Visual Studio | Complément d'information |
| - | - | - | - |
| **Concevoir des états visuels** | Il n’existe pas d’outil permettant de concevoir des états visuels. Vous devez les créer par programmation. | Utilisez les outils de conception pour modifier l’apparence d’un contrôle en fonction de son état. | [États visuels](modify-the-style-of-objects-in-blend.md#visual-states) |
| **Créer des animations** |Il n'existe aucun outil de conception d'animations ; vous devez les créer par programmation. Cela nécessite une bonne connaissance du système d'animation et de minutage de WPF, ainsi que des compétences étendues en matière de codage.|Vous créez les animations de manière visuelle et pouvez en afficher un aperçu dans Blend pour Visual Studio. Il s'agit d'une méthode plus rapide et plus précise que celle qui consiste à créer des animations dans le code. Vous pouvez ajouter des déclencheurs pour gérer l'interaction des utilisateurs et basculer vers le code pour ajouter des gestionnaires d'événements et d'autres fonctionnalités.|[Animer des objets](../designers/animate-objects-in-xaml-designer.md)|
|**Transformer des formes et du texte en tracés pour une manipulation plus facile**|Non pris en charge.|Vous pouvez modifier les formes (telles que des rectangles et des ellipses) de manière subtile ou radicale en les convertissant en tracés, ce qui confère un meilleur contrôle d'édition. Vous pouvez remodeler ou combiner des tracés et créer des tracés composites à partir de plusieurs formes.<br /><br />Vous pouvez aussi convertir des blocs de texte en tracés pour les manipuler en tant qu'images vectorielles.|[Dessiner des formes et des tracés](../designers/draw-shapes-and-paths.md)|
|**Modifier des contrôles, des modèles et des styles**|Nécessite du codage et une connaissance des styles et modèles WPF.|Transformez une image en contrôle.<br /><br />Utilisez les outils d'édition de modèle pour apporter des modifications à des contrôles, styles et modèles en quelques clics de souris.<br /><br />Par exemple, vous pouvez utiliser les ressources de style Blend pour Visual Studio pour implémenter des contrôles WPF courants (tels que des boutons, zones de liste, barres de défilement, menus, etc.) et modifier leur couleur, style ou modèle sous-jacent directement dans Blend pour Visual Studio. Vous pouvez ensuite basculer vers le code pour apporter des touches finales, le cas échéant.|[Modifier le style des objets](../designers/modify-the-style-of-objects-in-blend.md)|
|**Connecter votre interface utilisateur à des données**|Vous pouvez créer une source de données à partir de ressources, telles que des bases de données SQL Server, des services WCF ou web, des objets ou des listes SharePoint, et lier la source de données aux contrôles de votre interface utilisateur.<br /><br />Des données doivent être créées manuellement au moment de la conception pour une expérience de conception interactive.|Pour les applications .NET Framework, créez des exemples de données en toute simplicité à des fins de prototypage et de test. Passez à des données en direct dès que vous êtes prêt.<br /><br />Les capacités de génération de données de Blend pour Visual Studio sont remarquables (vous pouvez facilement ajouter noms, nombres, URL et photos à la volée) et peuvent vous faire gagner beaucoup de temps.<br /><br />Pour les données en direct, vous pouvez lier les contrôles de votre interface utilisateur à un fichier XML ou à une source de données CLR.|[Afficher des données](../designers/display-data-in-blend.md)|

Pour plus d’informations sur la conception XAML avancée, consultez [Créer une interface utilisateur à l’aide de Blend pour Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).
