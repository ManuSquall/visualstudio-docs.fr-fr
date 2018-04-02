---
title: Visual Studio 2017 pour développeurs .NET | Microsoft Docs
description: Présentation des fonctionnalités de Visual Studio 2017 qui permettent d’écrire du meilleur code .NET plus rapidement.
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
ms.openlocfilehash: 7e910c50682d45d209d993cb883ca01d1ea436f2
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2018
---
# <a name="visual-studio-2017-productivity-guide-for-net-developers"></a>Guide de productivité Visual Studio 2017 pour les développeurs .NET

- [Guide de productivité](#guide)
- [Vue d’ensemble de Visual Studio 2017](#overview)

## <a name="a-idguide-productivity-guide"></a><a id="guide"/> Guide de productivité
Avec [Visual Studio 2017](https://www.visualstudio.com/downloads/), les développeurs sont plus productifs que jamais ! Nous avons amélioré les performances et la fiabilité du démarrage et du chargement des solutions, de la découverte de tests et de la latence de la saisie. Nous avons également ajouté et amélioré des fonctionnalités pour vous aider à écrire du code plus rapidement. Ces fonctionnalités incluent notamment la navigation vers les assemblys décompilés, les suggestions de noms de variables au cours de la saisie, un affichage hiérarchique dans l’Explorateur de tests, l’option Atteindre tout (**Ctrl+T**) pour accéder aux déclarations de fichiers/types/membres/symboles, un programme intelligent d’assistance pour les exceptions, la configuration et la mise en conformité du style du code, ainsi qu’un grand nombre de refactorisations et de corrections de code. 

Suivez ce guide pour optimiser votre productivité.

###  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Je suis habitué à mes raccourcis clavier dans une autre extension ou un autre éditeur/IDE.

Si vous avez un autre environnement de développement intégré ou environnement de codage, les extensions suivantes peuvent vous être utiles :

- [Émulation Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [Touches d’accès rapide pour Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Le tableau suivant liste les principaux raccourcis Visual Studio. 

> [!NOTE]
> Dans la mesure où certaines extensions dissocient les combinaisons de touches Visual Studio par défaut, vous devez les restaurer pour pouvoir utiliser les commandes suivantes. Restaurez les valeurs par défaut de vos combinaisons de touches Visual Studio en accédant à : **Outils > Importation et exportation de paramètres > Réinitialiser tous les paramètres** ou **Outils > Options > Clavier > Réinitialiser**.

| Raccourci (tous les profils) | Commande | Description |
|-|-|-|
| **Ctrl + T** | Atteindre tout | Accédez à n’importe quel fichier, type, membre ou toute déclaration de symbole |
| **F12** (également **Ctrl + clic**) | Atteindre la définition | Accédez à l’emplacement de définition d’un symbole |
| **Ctrl + F12** | Accéder à l’implémentation | Accédez à partir d’un type ou membre de base à ses diverses implémentations |
| **Maj + F12** | Rechercher toutes les références | Affichez toutes les références de symboles et de littéraux |
| **Ctrl**+**.** (également **Alt + Entrée** dans le profil C#) | Actions rapides et refactorisations | Affichez les correctifs de code, les actions de génération de code, les refactorisations et les autres actions rapides qui sont disponibles au niveau de votre curseur ou de votre sélection de code |
| **Ctrl**+**D** | Dupliquer la ligne | Duplique la ligne de code où se trouve le curseur (disponible dans **Visual Studio 2017 versions 15.6** et ultérieures) |
| **Maj**+**Alt**+**+**/**-** | Développer/Réduire la sélection | Développe ou réduit la sélection actuelle dans l’éditeur (disponible dans **Visual Studio 2017 version 15.5** et les versions ultérieures) |
| **Ctrl + Q** | Lancement rapide | Effectuez une recherche parmi tous les paramètres Visual Studio |
| **F5** | Démarrer le débogage | Démarrez le débogage de votre application |
| **Ctrl + F5** | Exécutez sans déboguer | Exécutez votre application localement sans débogage |
| **CTRL + K, D** (profil par défaut) ou **Ctrl + E, D** (profil C#) | Mettre le document en forme | Nettoie les violations de mise en forme de votre fichier selon les paramètres de saut de ligne, d’espacement et de mise en retrait définis |
| **Ctrl+\\,E** (profil par défaut) ou **Ctrl+W,E** (profil C#) | Voir la liste des erreurs | Affichez toutes les erreurs de votre document, projet ou solution |

### <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>J’ai besoin d’accéder rapidement à des fichiers ou des types.
Visual Studio 2017 a une fonctionnalité appelée _Atteindre tout_ (**Ctrl+T**). Atteindre tout vous permet de passer rapidement à n’importe quelle déclaration de fichier, type, membre ou symbole.
- Changez l’emplacement de cette barre de recherche, ou désactivez l’aperçu de navigation dynamique à l’aide de l’icône d’**engrenage**
- Filtrez les résultats à l’aide de notre syntaxe de requête (par exemple « t mytype »). Vous pouvez également limiter la portée de votre recherche au document actif.
- Le respect de la casse est pris en charge !

![Atteindre tout dans Visual Studio](../ide/media/VS2017Guide-go-to-all.png "VS2017Guide-go-to-all")

### <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mon équipe applique des règles de style de code à notre base de code.
Vous pouvez utiliser un fichier .editorconfig pour codifier les conventions de codage. Nous vous recommandons d’installer l’[extension des services de langage EditorConfig](https://aka.ms/editorconfig) pour ajouter et modifier un fichier .editorconfig. Nous vous recommandons de consulter la [documentation](https://aka.ms/editorconfigDocs) pour toutes les options de convention de codage .NET.

Consultez cet [extrait gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) pour obtenir un exemple de fichier .editorconfig.

![Mise en conformité du style de code dans Visual Studio](../ide/media/VS2017Guide-code-style.png "VS2017Guide-code-style")

### <a name="i-need-more-refactorings-and-code-fixes"></a>J’ai besoin de refactorisations et de corrections de code supplémentaires.
Visual Studio 2017 est fourni avec un grand nombre de refactorisations, d’actions de génération de code et de corrections de code, que vous pouvez consulter dans notre [documentation](https://aka.ms/refactorings). Les tildes rouges représentent les erreurs, les tildes verts représentent les avertissements et trois points gris représentent les suggestions de code.

Vous pouvez accéder aux corrections de code en cliquant sur l’icône d’ampoule/de tournevis, ou en appuyant sur **Ctrl+.** ou sur **Alt+Entrée**. Chaque correction est accompagnée d’une fenêtre de prévisualisation qui affiche une comparaison dynamique du code pour illustrer la correction.

Voici quelques refactorisations et corrections rapides populaires : Renommer, Extraire la méthode, Modifier la signature de la méthode, Générer le constructeur, Générer une méthode, Déplacer le type vers le fichier, Ajouter un contrôle de valeur null, Ajouter un paramètre, Supprimer les Using inutiles.

Vous pouvez facilement écrire des refactorisations et des corrections de code à l’aide d’[analyseurs Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix). Plusieurs membres de la communauté ont écrit des *extensions* gratuites qui ajoutent des inspections de code supplémentaires : Roslynator et SonarLint pour Visual Studio. 

![Refactorisations dans Visual Studio](../ide/media/VS2017Guide-refactoring.png "VS2017Guide-refactoring")

### <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>J’ai besoin de rechercher des utilisations, d’accéder à l’implémentation, de naviguer vers des assemblys décompilés
Visual Studio 2017 comporte de nombreuses fonctionnalités pour vous aider à effectuer des recherches et à naviguer dans votre base de code, notamment Rechercher toutes les références (**Maj+F12**), Accéder à l’implémentation (**Ctrl+F12**), Atteindre la définition (**F12** ou **Ctrl+Clic**). La fonctionnalité de navigation vers les assemblys décompilés a été ajoutée à la version 15.6. Pour activer cette fonctionnalité, accédez à **Outils > Options > Éditeur de texte > C# > Avancé > Activer la navigation vers les sources décompilées**.

![Naviguer vers les sources décompilées dans Visual Studio](../ide/media/VS2017Guide-navigate-to-source.png "VS2017Guide-navigate-to-source")

### <a name="i-want-to-run-and-see-my-unit-tests"></a>Je souhaite exécuter et afficher mes tests unitaires.
Nous proposons deux solutions pour accéder aux tests unitaires dans Visual Studio 2017 : l’Explorateur de tests et _Live Unit Testing_. Nous avons considérablement amélioré la vitesse de découverte de tests dans l’Explorateur de tests de la version 15.6. Nous avons également repensé l’IU pour permettre le tri hiérarchique.

Visual Studio comporte également une fonctionnalité de test unitaire appelée [Live Unit Testing](/test/live-unit-testing). Live Unit Testing s’exécute en permanence en arrière-plan, exécute les tests impactés par vos modifications du code et met à jour les icônes de l’éditeur inline pour vous informer sur l’état de vos tests.

![Affichage hiérarchique de l’Explorateur de tests dans Visual Studio](../ide/media/VS2017Guide-hiearchy-test-explorer.png "VS2017Guide-hiearchy-test-explorer")

### <a name="what-other-features-do-i-need-to-know-about"></a>Quelles sont les autres fonctionnalités à connaître ?
Voici une liste de fonctionnalités de l’éditeur liées à la productivité pour rendre l’écriture de code plus efficace. Vous devrez peut-être activer certaines fonctionnalités, car elles sont désactivées par défaut (elles peuvent éventuellement indexer des éléments sur votre machine, être controversées ou être à l’état expérimental).
- La fonctionnalité de *localisation de fichier dans l’Explorateur de solutions* met en évidence le fichier actif dans l’Explorateur de solutions.
  - **Outils > Options > Projets et solutions > Suivre un élément actif dans l’Explorateur de solutions**
- Si vous *ajoutez des using pour les types dans les assemblys de référence et les packages NuGet*, une ampoule s’affiche avec une correction de code afin de permettre l’installation d’un package NuGet pour un type non référencé.
  - **Outils > Options > Éditeur de texte > C# > Avancé > Suggérer des usings pour les types dans les assemblys de référence** et **Suggérer des usings pour les types dans les packages NuGet**
- *Activez l’analyse complète de la solution* pour afficher toutes les erreurs de votre solution dans la fenêtre Liste d’erreurs.
  - **Outils > Options > Éditeur de texte > C# > Avancé > Activer l’analyse complète de la solution**
- *Activez la navigation vers les sources décompilées* pour activer la fonctionnalité Atteindre la définition sur les types/membres de sources externes, et utilisez le décompilateur ILSpy pour afficher les corps de méthodes.
  - **Outils > Options > Éditeur de texte > C# > Avancé > Activer la navigation vers les sources décompilées**
- Le *mode Complétion/Suggestion* d’IntelliSense change le comportement de complétion. Les développeurs ayant utilisé IntelliJ ont tendance à changer le paramètre par défaut.
  - **Menu > Edition > IntelliSense -> Activer/Désactiver le mode de saisie semi-automatique**
- Nous avons des *extraits de code* pour vous aider à remplacer le texte réutilisable usuel (appuyez deux fois sur la touche Tab). Consultez la [liste complète](/ide/visual-csharp-code-snippets).

![Extraits de code dans Visual Studio](../ide/media/VS2017Guide-code-snippet.png "VS2017Guide-code-snippet")

### <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Est-ce qu’il vous manque une fonctionnalité qui améliore votre productivité, ou est-ce que vous trouvez le niveau de performance médiocre ?
Il existe plusieurs façons de nous laisser des commentaires :
- Vous pouvez soumettre des demandes de fonctionnalités .NET dans notre [dépôt GitHub](https://github.com/dotnet/roslyn/issues).
- Vous pouvez soumettre des demandes de fonctionnalités Visual Studio, des bogues et des problèmes de performances à l’aide de l’icône **Envoyer des commentaires** située en haut de la fenêtre Visual Studio.


## <a name="a-idoverview-overview-of-visual-studio-2017-for-net-developers"></a><a id="overview"/> Vue d’ensemble de Visual Studio 2017 pour les développeurs .NET

### <a name="smart-code-editor"></a>Éditeur de code intelligent

- [Documentation : Utilisation d’IntelliSense](using-intellisense.md)
- [Documentation : Fonctionnalités de l’Éditeur Intelligent](writing-code-in-the-code-and-text-editor.md)

Visual Studio propose une compréhension approfondie de votre code par le biais du compilateur .NET (« Roslyn »), qui fournit des fonctionnalités d’édition intelligentes, telles que la coloration syntaxique, la complétion de code, la vérification des variables mal orthographiées, la résolution des types non importés, le mode Plan, les visualiseurs de structure, [CodeLens](find-code-changes-and-other-history-with-codelens.md), la hiérarchie des appels, les info-bulles Info express, l’aide sur les paramètres, ainsi que des outils de refactorisation, d’application d’actions rapides et de génération de code.

![Éditeur de code intelligent Visual Studio](../ide/media/VSIDE_Productivity_SmartCodeEditor.png "VSIDE_Productivity_SmartCodeEditor")

### <a name="navigate-and-search-your-codebase"></a>Parcourir et effectuer des recherches dans votre base de code

[Documentation : Naviguer dans le code](navigating-code.md)

Naviguez rapidement dans votre code .NET en accédant à n’importe quel fichier, type, membre ou à toute déclaration de symbole, grâce au raccourci *Accéder à tout* (**Ctrl + T**). Recherchez toutes les références d’un littéral ou d’un symbole dans votre code, y compris les références entre langages .NET (**MAJ + F12**). Utilisez nos commandes de navigation ciblée pour accéder directement aux définitions de symbole (**F12**) et aux implémentations de symbole (**Ctrl + F12**).

![Accéder à tout et Rechercher toutes les références](../ide/media/VSIDE_Productivity_Navigation.png "VSIDE_Productivity_Navigation")

### <a name="live-code-analysis-for-code-quality"></a>Analyse du code en temps réel pour la qualité du code

[Documentation : Refactorisation et actions rapides](refactoring-code-generation-quick-actions.md)

Visual Studio propose des diagnostics de code en temps réel pour vous aider à améliorer la qualité de votre code en détectant les erreurs et le code potentiellement problématique. Des actions rapides (**Ctrl**+**.**) sont disponibles pour résoudre les problèmes détectés dans votre document, votre projet ou votre solution. Activez *l’analyse complète de la solution* pour rechercher les problèmes dans l’ensemble de votre solution, même si les fichiers ne sont pas ouverts dans l’éditeur.

En outre, utilisez les suggestions de code pour en savoir plus sur les bonnes pratiques, les stubs, la génération de code et la refactorisation de code, et découvrez de nouvelles fonctionnalités de langage avec le raccourci **Ctrl**+**.** .

![Appliquer des correctifs rapides et des refactorisations à l’aide du menu Ampoule](../ide/media/VSIDE_Productivity_CodeAnalysis.png "VSIDE_Productivity_CodeAnalysis")

### <a name="unit-testing"></a>Test unitaire

[Documentation : Tests unitaires dans Visual Studio](../test/improve-code-quality.md)

Exécutez et déboguez vos tests unitaires basés sur les frameworks de test MSTest, NUnit ou XUnit pour les applications qui ciblent .NET Framework, .NET Standard ou .NET Core. Explorez et examinez vos tests dans *l’Explorateur de tests* ou voyez immédiatement l’impact des modifications du code sur vos tests unitaires dans l’éditeur avec *Live Unit Testing* (version Enterprise uniquement).

![Live Unit Testing dans Visual Studio](../ide/media/VSIDE_Productivity_LiveUnitTesting.png "VSIDE_Productivity_LiveUnitTesting")

### <a name="code-consistency-and-style"></a>Style et cohérence du code

- [Documentation : Options d’éditeur personnalisées et portables](create-portable-custom-editor-options.md)
- [Documentation : Paramètres de style de code EditorConfig pour .NET](editorconfig-code-style-settings-reference.md)

Visual Studio permet la configuration de conventions de codage, détecte les violations de style de codage et fournit des correctifs rapides pour résoudre les problèmes de style avec le raccourci **Ctrl**+**.** . Configurez et appliquez les conventions de mise en forme, de nommage et de style de code de votre équipe dans un référentiel, pour substituer les valeurs au niveau du projet et du fichier, avec *EditorConfig*.

![Configurer et appliquer des conventions de codage avec EditorConfig](../ide/media/VSIDE_Productivity_CodeStyle.png "VSIDE_Productivity_CodeStyle")

### <a name="debugging"></a>Débogage

[Documentation : Débogage dans Visual Studio](../debugger/index.md)

Visual Studio comprend un débogueur ultraperformant qui vous permet de déboguer vos applications .NET qui ciblent .NET Framework, .NET Standard et .NET Core. Activez/désactivez et définissez des points d’arrêt conditionnels (**F9**), effectuez un pas à pas détaillé des appels de méthode, évaluez les expressions LINQ et lambda, définissez des espions de variable, effectuez des rattachements aux processus, examinez votre pile des appels ou apportez des modifications de code en temps réel pendant le débogage avec *Modifier et Continuer*.

Si votre service s’exécute dans Azure, utilisez le *débogage d’instantané* pour diagnostiquer les problèmes des applications cloud en production déployées dans Visual Studio 2017 Enterprise.

![Débogage dans Visual Studio](../ide/media/VSIDE_Productivity_Debugging.png "VSIDE_Productivity_Debugging")

### <a name="version-control"></a>Gestion de version

[Documentation : Gestion de version dans Visual Studio](/vsts/index)

Utilisez git ou TFVC pour stocker et mettre à jour votre code dans Visual Studio. Dans l’éditeur, organisez les modifications locales avec Team Explorer et utilisez la barre d’état pour suivre les validations et les modifications en attente. Configurez l’intégration et la livraison continues dans Visual Studio avec l’extension [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) pour adopter le flux de travail de développement agile.

![Contrôle de code source dans Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png "VSIDE_Productivity_SourceControl")

### <a name="extensibility"></a>Extensibilité

[Documentation : Étendre Visual Studio](../extensibility/index.md)

Visual Studio propose un écosystème complet d’extensions que vous pouvez installer ou créer au fur et à mesure de vos besoins. Installez des extensions à partir de la *Galerie des extensions* ou de *Visual Studio Marketplace*, générez votre propre plug-in d’éditeur avec le *SDK VS*, ou créez votre propre analyseur de code en direct ou votre propre refactorisation à l’aide du *SDK de la plateforme du compilateur .NET* . Pour obtenir des suggestions et d’autres corrections de code, téléchargez l’extension [Analyse du code Microsoft](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.MicrosoftCodeAnalysis2017).

![Galerie des extensions Visual Studio](../ide/media/VSIDE_Productivity_Extensibility.png "VSIDE_Productivity_Extensibility")
