---
title: Améliorer votre productivité pour le développement .NET
description: Vue d’ensemble de la navigation, de l’analyse du code, des tests unitaires et d’autres fonctionnalités qui vont vous aider à écrire du code .NET plus performant plus rapidement.
author: kuhlenh
ms.author: kaseyu
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.date: 06/14/2018
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: d0f7ffbef8fade3e5723a84ac433ce95679c26c3
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39381092"
---
# <a name="visual-studio-2017-c-productivity-guide"></a>Guide de productivité C# pour Visual Studio 2017

Découvrez comment [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) rend les développeurs plus productifs que jamais. Tirez parti de nos améliorations en performance et en productivité, comme l’accès aux assemblys décompilés, les suggestions de noms de variables au fil de la saisie, une vue hiérarchique dans l’**Explorateur de tests**, l’option Atteindre tout (**Ctrl**+**T**) pour accéder aux déclarations de fichiers/types/membres/symboles, une **Assistance sur l’exception** intelligente, la configuration et la mise en conformité du style du code, ainsi qu’un grand nombre de refactorisations et de corrections de code.

##  <a name="im-used-to-my-keyboard-shortcuts-from-a-different-extensioneditoride"></a>Je suis habitué à mes raccourcis clavier dans une autre extension ou un autre éditeur/IDE.

**Nouveautés de Visual Studio 2017 version 15.8** Si vous utilisiez un autre IDE ou environnement de codage, vous pouvez basculer votre schéma de clavier vers *Visual Studio Code* ou *ReSharper (Visual Studio)*  :

![Schémas de clavier dans Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Certaines extensions offrent également des schémas de clavier :
- [Touches d’accès rapide pour Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Émulation Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Le tableau suivant liste les principaux raccourcis de Visual Studio :

| Raccourci (tous les profils) | Commande | Description |
|-|-|-|
| **Ctrl**+**T** | Atteindre tout | Accédez à n’importe quel fichier, type, membre ou toute déclaration de symbole |
| **F12** (également **Ctrl**+**Clic**) | Atteindre la définition | Accédez à l’emplacement de définition d’un symbole |
| **Ctrl**+**F12** | Accéder à l’implémentation | Accédez à partir d’un type ou membre de base à ses diverses implémentations |
| **Maj**+**F12** | Rechercher toutes les références | Affichez toutes les références de symboles et de littéraux |
| **Ctrl**+**.** (également **Alt**+**Entrée** dans le profil C#) | Actions rapides et refactorisations | Affichez les correctifs de code, les actions de génération de code, les refactorisations et les autres actions rapides qui sont disponibles au niveau de votre curseur ou de votre sélection de code |
| **Ctrl**+**D** | Dupliquer la ligne | Duplique la ligne de code où se trouve le curseur (disponible dans **Visual Studio 2017 versions 15.6** et ultérieures) |
| **Maj**+**Alt**+**+**/**-** | Développer/Réduire la sélection | Développe ou réduit la sélection actuelle dans l’éditeur (disponible dans **Visual Studio 2017 version 15.5** et les versions ultérieures) |
| **Maj** + **Alt** + **Ins** | Insérer un signe insertion à la prochaine correspondance | Ajoute une sélection et un signe insertion à l’emplacement suivant qui correspond à la sélection actuelle (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |
| **Ctrl**+**Q** | Lancement rapide | Effectuez une recherche parmi tous les paramètres Visual Studio |
| **F5** | Démarrer le débogage | Démarrez le débogage de votre application |
| **Ctrl**+**F5** | Exécutez sans déboguer | Exécutez votre application localement sans débogage |
| **Ctrl**+**K**,**D** (Profil par défaut) ou **Ctrl**+**E**,**D** (Profil C#) | Mettre le document en forme | Nettoie les violations de mise en forme de votre fichier selon les paramètres de saut de ligne, d’espacement et de mise en retrait définis |
| **Ctrl**+**\\**,**E** (Profil par défaut) ou **Ctrl**+**W**,**E** (Profil C#) | Voir la liste des erreurs | Affichez toutes les erreurs de votre document, projet ou solution |
| **Alt** + **Pg. préc/Pg. suiv** | Accéder au problème suivant/précédent | Atteindre l’erreur, avertissement, suggestion précédent/suivant dans votre document (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |

> [!NOTE]
> Certaines extensions dissocient les combinaisons de touches de Visual Studio par défaut. Pour utiliser les commandes ci-dessus, restaurez les valeurs par défaut de Visual Studio de vos combinaisons de touches en accédant à **Outils** > **Paramètres d’importation et d’exportation** > **Réinitialiser tous les paramètres** ou à **Outils** > **Options** > **Clavier** > **Réinitialiser**.

Pour en savoir plus sur les raccourcis clavier et les commandes dans Visual Studio, consultez [notre documentation](..\ide\tips-and-tricks-for-visual-studio.md).

## <a name="i-need-a-way-to-quickly-navigate-to-files-or-types"></a>J’ai besoin d’accéder rapidement à des fichiers ou des types.
Visual Studio 2017 a une fonctionnalité appelée **Atteindre tout** (**Ctrl**+**T**). Atteindre tout vous permet de passer rapidement à n’importe quelle déclaration de fichier, type, membre ou symbole.
- Changez l’emplacement de cette barre de recherche, ou désactivez l’aperçu de navigation dynamique à l’aide de l’icône d’**engrenage**
- Filtrez les résultats à l’aide de notre syntaxe de requête (par exemple « t mytype »). Vous pouvez également limiter la portée de votre recherche au document actif.
- Le respect de la casse est pris en charge !

![Accéder à tout dans Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="my-team-enforces-code-style-rules-on-our-codebase"></a>Mon équipe applique des règles de style de code à notre base de code.
Vous pouvez utiliser un fichier *.editorconfig* pour codifier les conventions de codage et les faire suivre avec votre source.
- Nous vous recommandons d’installer [l’extension des services de langage EditorConfig](https://aka.ms/editorconfig) pour ajouter et modifier un fichier *.editorconfig* dans Visual Studio.
- Consultez la [documentation](https://aka.ms/editorconfigDocs) de toutes les options de convention de codage .NET.
- Consultez cet [extrait gist](https://gist.github.com/kuhlenh/5471666a7a2c57fea427e81cf0a41da8) pour obtenir un exemple de fichier *.editorconfig*.

![Application du style de code dans Visual Studio](../ide/media/VSGuide_CodeStyle.png)

## <a name="i-need-more-refactorings-and-code-fixes"></a>J’ai besoin de refactorisations et de corrections de code supplémentaires.
Visual Studio 2017 est fourni avec un grand nombre de refactorisations, d’actions de génération de code et de corrections de code. Les tildes rouges représentent les erreurs, les tildes verts représentent les avertissements et trois points gris représentent les suggestions de code. Vous pouvez accéder aux corrections de code en cliquant sur l’icône d’ampoule/tournevis, ou en appuyant sur **Ctrl**+**.** ou sur **Alt**+**Entrée**. Chaque correction est accompagnée d’une fenêtre de prévisualisation qui affiche une comparaison dynamique du code pour illustrer la correction.

- Les correctifs rapides et refactorisations répandus sont les suivants :
  - *Renommer*
  - *Extraire la méthode*
  - *Modifier la signature de la méthode*
  - *Générer le constructeur*
  - *Générer la méthode*
  - *Déplacer le type vers le fichier*
  - *Ajouter un contrôle de valeur null*
  - *Ajouter un paramètre*
  - *Supprimer les instructions using inutiles*
  - Découvrez-en d’autres dans notre [documentation](https://aka.ms/refactorings)
- Écrivez votre propre correctif de code ou refactorisation avec des [analyseurs Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).
- Plusieurs membres de la communauté ont écrit des extensions gratuites qui ajoutent des inspections de code supplémentaires :
  - [Analyseurs FXCop](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/)
  - [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
  - [SonarLint pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
  - [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)

![Refactorisations dans Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="i-need-find-usages-go-to-implementation-navigate-to-decompiled-assemblies"></a>J’ai besoin de rechercher des utilisations, d’accéder à l’implémentation, de naviguer vers des assemblys décompilés
Visual Studio 2017 contient de nombreuses fonctionnalités qui vous permettent de rechercher et de parcourir votre code base. Découvrez plus d’informations sur les [fonctionnalités de navigation dans le code](../ide/navigating-code.md)

| Fonctionnalité | Raccourci | Détails/améliorations |
|- | - | -|
| Rechercher toutes les références | **Maj**+**F12**| Les résultats sont en couleur et peuvent être regroupés par projet, définition, etc. Vous pouvez également « verrouiller » les résultats. |
| Accéder à l’implémentation | **Ctrl**+**F12** | Vous pouvez utiliser Atteindre la définition sur le mot clé `override` pour accéder au membre substitué |
| Atteindre la définition | **F12** ou **Ctrl**+**Clic**| Vous pouvez maintenir la touche **Ctrl** enfoncée et cliquer pour accéder à la définition |
| Aperçu de définition | **Alt**+**F12** | Vue inline d’une définition |
| Visualiseur de structure | Lignes grises en pointillés entre accolades | Placez le curseur pour voir la structure de votre code |
| Navigation vers les assemblys décompilés | **F12** ou **Ctrl**+**Clic** | Accédez à une source externe (décompilée avec ILSpy) en activant la fonctionnalité : **Outils** > **Options** > **Éditeur de texte** > **C#** > **Avancé** > **Activer la navigation vers les sources décompilées**. |

![Accéder à tout et Rechercher toutes les références](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="i-want-to-run-and-see-my-unit-tests"></a>Je souhaite exécuter et afficher mes tests unitaires.
Nous avons apporté de nombreuses améliorations à l’expérience de test dans Visual Studio 2017. Utilisez l’une de nos expériences de test unitaire avec les frameworks de test MSTest v1, MSTest v2, NUnit ou XUnit.
- La découverte de tests de l’**Explorateur de tests** est rapide dans la version 15.6 (pour de meilleurs résultats, passez à la dernière version de votre adaptateur de test).
- Organisez vos tests dans l’Explorateur de tests avec notre nouveau *tri hiérarchique* dans la version 15.6.
- [Live Unit Testing](../test/live-unit-testing.md) exécute en continu les tests impactés par vos modifications du code et met à jour les icônes de l’éditeur inline pour vous informer de l’état de vos tests. Incluez ou excluez des tests spécifiques ou des projets de test de votre *jeu de tests dynamique*.

![Vue de la hiérarchie de l’Explorateur de tests dans Visual Studio](../ide/media/VSGuide_Testing.png)

## <a name="i-want-to-debug-my-code"></a>Je souhaite déboguer mon code.
Nous avons ajouté une multitude de nouvelles fonctionnalités de débogage dans Visual Studio 2017.
- *Cliquer pour exécuter* vous permet de placer le curseur à côté d’une ligne de code, de cliquer sur l’icône verte de « lecture » qui s’affiche et d’exécuter votre programme jusqu’à ce qu’il atteigne cette ligne.
- La nouvelle **Assistance sur l’exception** place les informations les plus importantes, comme la variable 'null' d’une NullReferenceException, en haut de la boîte de dialogue.
- Le débogage [Revenir en arrière](../debugger/how-to-use-intellitrace-step-back.md) vous permet de revenir aux étapes ou aux points d’arrêt précédents et de voir l’état de l’application comme elle était avant.
- Le [débogage d’instantané](/azure/application-insights/app-insights-snapshot-debugger) vous permet d’examiner l’état d’une application web dynamique au moment où une exception a été levée (sur Azure uniquement).

![Nouvelle assistance sur l’exception dans Visual Studio 2017](../ide/media/VSGuide_Debugging.png)

## <a name="i-want-to-use-version-control-with-my-projects"></a>Je veux utiliser la gestion de versions avec mes projets.
Vous pouvez utiliser git ou TFVC pour stocker et mettre à jour votre code dans Visual Studio.
- Organisez vos changements locaux avec **Team Explorer** et utilisez la barre d’état pour suivre les validations et les changements en attente.
- Configurez l’intégration et la livraison continues pour vos projets dans Visual Studio avec l’extension [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio) et adoptez le flux de travail de développement agile.

![Contrôle de code source dans Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-do-i-need-to-know-about"></a>Quelles sont les autres fonctionnalités à connaître ?
Voici une liste de fonctionnalités de l’éditeur liées à la productivité pour rendre l’écriture de code plus efficace. Vous devrez peut-être activer certaines fonctionnalités, car elles sont désactivées par défaut (elles peuvent éventuellement indexer des éléments sur votre machine, être controversées ou être à l’état expérimental).

| Fonctionnalité | Détails | Comment activer |
|-|-|-|
| Rechercher un fichier dans l’Explorateur de solutions | Met en évidence le fichier actif dans **Explorateur de solutions** | **Outils** > **Options** > **Projets et solutions** > **Suivre un élément actif dans l’Explorateur de solutions** |
| Ajouter des instructions using pour les types dans les assemblys de référence et les packages NuGet | Affiche une ampoule avec un correctif de code pour installer un package NuGet pour un type non référencé | **Outils** > **Options** > **Éditeur de texte** > **C#** > **Avancé** > **Suggérer des usings pour les types dans les assemblys de référence** et **Suggérer des usings pour les types dans les packages NuGet** |
| Activer l’analyse complète de la solution | Visualisez toutes les erreurs de votre solution dans la **Liste d’erreurs** | **Outils** > **Options** > **Éditeur de texte** > **C#** > **Avancé**   > **Activer l’analyse complète de la solution** |
| Activer la navigation vers les sources décompilées | Permet d’activer la fonctionnalité Atteindre la définition sur les types/membres de sources externes et d’utiliser le décompilateur ILSpy pour afficher les corps de méthodes | **Outils** > **Options** > **Éditeur de texte** > **C#** > **Avancé** > **Activer la navigation vers les sources décompilées** |
| Mode de saisie semi-automatique/suggestion | Change le comportement de saisie semi-automatique dans IntelliSense - Les développeurs qui connaissent IntelliJ ont tendance à changer le paramètre par défaut | **Menu** > **Modifier** > **IntelliSense** > **Activer/Désactiver le mode de saisie semi-automatique** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Affiche les informations de référence du code et l’historique des modifications dans l’éditeur | **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **CodeLens** |
| [Extraits de code](../ide/visual-csharp-code-snippets.md) | Permet de vous épargner le texte réutilisable courant |  Tapez un nom d’extrait et appuyez deux fois sur **Tab**. |

## <a name="missing-a-feature-that-makes-you-productive-or-experiencing-poor-performance"></a>Est-ce qu’il vous manque une fonctionnalité qui améliore votre productivité, ou est-ce que vous trouvez le niveau de performance médiocre ?
Il existe plusieurs façons de nous laisser des commentaires :
- Vous pouvez soumettre des demandes de fonctionnalités .NET dans notre [dépôt GitHub](https://github.com/dotnet/roslyn/issues).
- Vous pouvez soumettre des demandes de fonctionnalités Visual Studio, des bogues et des problèmes de performances en utilisant l’icône **Envoyer des commentaires** en haut à droite de la fenêtre Visual Studio.
