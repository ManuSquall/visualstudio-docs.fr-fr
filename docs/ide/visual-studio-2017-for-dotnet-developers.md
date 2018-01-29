---
title: "Visual Studio 2017 pour développeurs .NET | Microsoft Docs"
description: "Présentation des fonctionnalités de Visual Studio 2017 qui permettent d’écrire du meilleur code .NET plus rapidement."
author: kuhlenh
ms.author: kaseyu
manager: ghogen
ms.technology: vs-ide-general
ms.date: 01/16/2018
ms.topic: article
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: db1e944f3ce12369b096c75a7fc12648a2d7e91d
ms.sourcegitcommit: 49aa031cbebdd9c7ec070c713afb1a97d1ecb701
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2018
---
# <a name="visual-studio-2017-for-net-developers"></a>Visual Studio 2017 pour développeurs .NET

## <a name="smart-code-editor"></a>Éditeur de code intelligent

[Documentation : Utilisation d’IntelliSense](using-intellisense.md)  
[Documentation : Fonctionnalités de l’Éditeur Intelligent](writing-code-in-the-code-and-text-editor.md)

Visual Studio propose une compréhension approfondie de votre code via le compilateur Roslyn, qui fournit des fonctionnalités d’édition intelligentes, telles que la coloration syntaxique, la complétion de code, la vérification des variables mal orthographiées, la résolution des types non importés, le mode Plan, les visualiseurs de structure, [CodeLens](find-code-changes-and-other-history-with-codelens.md), la hiérarchie des appels, les info-bulles Info express, l’aide sur les paramètres, ainsi que les outils de refactorisation, l’application des actions rapides et la génération de code.

![Éditeur de code intelligent Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

## <a name="navigate-and-search-your-codebase"></a>Parcourir et effectuer des recherches dans votre base de code

[Documentation : Naviguer dans le code](navigating-code.md)

Naviguez rapidement dans votre code .NET en accédant à n’importe quel fichier, type, membre ou à toute déclaration de symbole, grâce au raccourci *Accéder à tout* (**Ctrl + T**). Recherchez toutes les références d’un littéral ou d’un symbole dans votre code, y compris les références entre langages .NET (**MAJ + F12**). Utilisez nos commandes de navigation ciblée pour accéder directement aux définitions de symbole (**F12**) et aux implémentations de symbole (**Ctrl + F12**).

![Accéder à tout et Rechercher toutes les références](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

## <a name="live-code-analysis-for-code-quality"></a>Analyse du code en temps réel pour la qualité du code

[Documentation : Refactorisation et actions rapides](refactoring-code-generation-quick-actions.md)

Visual Studio propose des diagnostics de code en temps réel pour vous aider à améliorer la qualité de votre code en détectant les erreurs et le code potentiellement problématique. Des actions rapides (**Ctrl +.**) sont disponibles pour résoudre les problèmes détectés dans votre document, projet ou solution. Activez *l’analyse complète de la solution* pour rechercher les problèmes dans l’ensemble de votre solution, même si les fichiers ne sont pas ouverts dans l’éditeur.

En outre, utilisez les suggestions de code pour en savoir plus sur les bonnes pratiques, les stubs, la génération de code et la refactorisation de code, et découvrez de nouvelles fonctionnalités de langage avec le raccourci **Ctrl +.** .

![Appliquer des correctifs rapides et des refactorisations à l’aide du menu Ampoule](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

## <a name="unit-testing"></a>Test unitaire

[Documentation : Tests unitaires dans Visual Studio](../test/improve-code-quality.md)

Exécutez et déboguez vos tests unitaires basés sur les frameworks de test MSTest, NUnit ou XUnit pour les applications qui ciblent .NET Framework, .NET Standard ou .NET Core. Explorez et examinez vos tests dans *l’Explorateur de tests* ou voyez immédiatement l’impact des modifications du code sur vos tests unitaires dans l’éditeur avec *Live Unit Testing* (version Enterprise uniquement). 

![Live Unit Testing dans Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

## <a name="code-consistency-and-style"></a>Style et cohérence du code

[Documentation : Options d’éditeur personnalisées et portables](create-portable-custom-editor-options.md)  
[Documentation : Paramètres de style de code EditorConfig pour .NET](editorconfig-code-style-settings-reference.md)

Visual Studio permet la configuration de conventions de codage, détecte les violations de style de codage et fournit des correctifs rapides pour résoudre les problèmes de style grâce au raccourci **Ctrl +.** . Configurez et appliquez les conventions de mise en forme, de nommage et de style de code de votre équipe dans un référentiel, pour substituer les valeurs au niveau du projet et du fichier, avec *EditorConfig*.

![Configurer et appliquer des conventions de codage avec EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

## <a name="debugging"></a>Débogage

[Documentation : Débogage dans Visual Studio](../debugger/index.md)

Visual Studio comprend un débogueur ultraperformant qui vous permet de déboguer vos applications .NET qui ciblent .NET Framework, .NET Standard et .NET Core. Activez/désactivez et définissez des points d’arrêt conditionnels (**F9**), effectuez un pas à pas détaillé des appels de méthode, évaluez les expressions LINQ et lambda, définissez des espions de variable, effectuez des rattachements aux processus, examinez votre pile des appels ou apportez des modifications de code en temps réel pendant le débogage avec *Modifier et Continuer*.

Si votre service s’exécute dans Azure, utilisez le *débogage d’instantané* pour diagnostiquer les problèmes des applications cloud en production déployées dans Visual Studio 2017 Enterprise.

![Débogage dans Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

## <a name="version-control"></a>Gestion de version

[Documentation : Gestion de version dans Visual Studio](/vsts/index)

Utilisez git ou TFVC pour stocker et mettre à jour votre code dans Visual Studio. Dans l’éditeur, organisez les modifications locales avec Team Explorer et utilisez la barre d’état pour suivre les validations et les modifications en attente. Configurez l’intégration et la livraison continues dans Visual Studio avec l’extension [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) pour adopter le flux de travail de développement agile.

![Contrôle de code source dans Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

## <a name="extensibility"></a>Extensibilité

[Documentation : Étendre Visual Studio](../extensibility/index.md)

Visual Studio propose un écosystème complet d’extensions que vous pouvez installer ou créer au fur et à mesure de vos besoins. Installez des extensions à partir de la *Galerie des extensions* ou de *Visual Studio Marketplace*, générez votre propre plug-in d’éditeur avec le *SDK VS*, ou créez votre propre analyseur de code en direct ou votre propre refactorisation à l’aide du *SDK de la plateforme du compilateur .NET* . Pour obtenir des suggestions et d’autres corrections de code, téléchargez l’extension [Analyse du code Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Galerie des extensions Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")

## <a name="popular-extensions--shortcuts"></a>Extensions et raccourcis populaires

Si vous avez un autre environnement de développement intégré ou environnement de codage, les extensions suivantes peuvent vous être utiles :

- [Émulation Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation )
- [Touches d’accès rapide pour Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Le tableau suivant liste les principaux raccourcis Visual Studio. Notez que certaines extensions annulent l’association des combinaisons de touches par défaut de Visual Studio. Vous devez alors restaurer ces combinaisons de touches pour pouvoir utiliser les commandes ci-dessous. Pour restaurer vos combinaisons de touches aux valeurs par défaut de Visual Studio, accédez à **Outils > Importation et exportation de paramètres... > Réinitialiser tous les paramètres**.

| Raccourci (tous les profils) | Commande | Description |
|-|-|-|
| **Ctrl + T** | Atteindre tout | Accédez à n’importe quel fichier, type, membre ou toute déclaration de symbole |
| **F12** (également **Ctrl + clic**) | Atteindre la définition | Accédez à l’emplacement de définition d’un symbole |
| **Ctrl + F12** | Accéder à l’implémentation | Accédez à partir d’un type ou membre de base à ses diverses implémentations |
| **Maj + F12** | Rechercher toutes les références | Affichez toutes les références de symboles et de littéraux |
| **Ctrl + .** (également **Alt + Entrée** dans le profil C#) | Actions rapides et refactorisations | Affichez les correctifs de code, les actions de génération de code, les refactorisations et les autres actions rapides qui sont disponibles au niveau de votre curseur ou de votre sélection de code |
| **Ctrl**+**E**,**V** | Dupliquer la ligne | Duplique la ligne de code où se trouve le curseur (disponible dans **Visual Studio 2017 version 15.6 préversion 2** et ultérieures) |
| **Ctrl**+**W** | Développer la sélection | Étend la sélection actuelle d’une unité structurelle (disponible dans **Visual Studio 2017 version 15.5**) |
| **Ctrl**+**Maj**+**W** | Diminuer la sélection | Diminue (réduit) la sélection actuelle d’une unité structurelle (disponible dans **Visual Studio 2017 version 15.5**) |
| **Ctrl + Q** | Lancement rapide | Effectuez une recherche parmi tous les paramètres Visual Studio |
| **F5** | Démarrer le débogage | Démarrez le débogage de votre application |
| **Ctrl + F5** | Exécutez sans déboguer | Exécutez votre application localement sans débogage |
| **CTRL + K, D** (profil par défaut) ou **Ctrl + E, D** (profil C#) | Mettre le document en forme | Nettoie les violations de mise en forme de votre fichier selon les paramètres de saut de ligne, d’espacement et de mise en retrait définis |
| **Ctrl+\\,E** (profil par défaut) ou **Ctrl+W,E** (profil C#) | Voir la liste des erreurs | Affichez toutes les erreurs de votre document, projet ou solution |