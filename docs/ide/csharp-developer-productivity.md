---
title: Améliorer votre productivité pour le développement .NET
description: Vue d’ensemble de la navigation, de l’analyse du code, des tests unitaires et d’autres fonctionnalités qui vont vous aider à écrire du code .NET plus performant plus rapidement.
author: kuhlenh
ms.author: gewarren
manager: jillfra
ms.date: 04/25/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: bd36b75f3df640df0e1910fb3a7a52d17c37d30f
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328775"
---
# <a name="visual-studio-productivity-guide-for-c-developers"></a>Guide de productivité Visual Studio pour les développeurs C#

Découvrez comment Visual Studio rend les développeurs plus productifs que jamais. Tirez parti de nos améliorations en performance et en productivité, comme l’accès aux assemblys décompilés, les suggestions de noms de variables au fil de la saisie, une vue hiérarchique dans l’**Explorateur de tests**, l’option Atteindre tout (**Ctrl**+**T**) pour accéder aux déclarations de fichiers/types/membres/symboles, une **Assistance sur l’exception** intelligente, la configuration et la mise en conformité du style du code, ainsi qu’un grand nombre de refactorisations et de corrections de code.

## <a name="im-used-to-keyboard-shortcuts-from-a-different-editor"></a>Je suis habitué aux raccourcis clavier d’un autre éditeur

::: moniker range="vs-2017"

**Nouveauté de Visual Studio 2017 version 15.8**

::: moniker-end

Si vous utilisiez un autre IDE ou environnement de codage, vous pouvez basculer votre schéma de clavier vers *Visual Studio Code* ou *ReSharper (Visual Studio)*  :

![Schémas de clavier dans Visual Studio](../ide/media/VS2017Guide-Keyboard.png)

Certaines extensions offrent également des schémas de clavier :

- [Touches d’accès rapide pour Visual Studio (ReSharper/IntelliJ)](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.HotKeys)
- [Émulation Emacs](https://marketplace.visualstudio.com/items?itemName=JustinClareburtMSFT.EmacsEmulation)
- [VSVim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)

Le tableau suivant liste les principaux raccourcis de Visual Studio :

| Raccourci (tous les profils) | Commande | Description |
|-|-|-|
| **Ctrl**+**T** | Atteindre tout | Accéder à n’importe quel fichier, type, membre ou toute déclaration de symbole |
| **F12** (également **Ctrl**+**Clic**) | Atteindre la définition | Accédez à l’emplacement de définition d’un symbole |
| **Ctrl**+**F12** | Accéder à l’implémentation | Accédez à partir d’un type ou membre de base à ses diverses implémentations |
| **Maj**+**F12** | Rechercher toutes les références | Affichez toutes les références de symboles et de littéraux |
| **Ctrl**+ **.** (également **Alt**+**Entrée** dans le profil C#) | Actions rapides et refactorisations | Affichez les correctifs de code, les actions de génération de code, les refactorisations et les autres actions rapides qui sont disponibles au niveau de votre curseur ou de votre sélection de code |
| **Ctrl**+**D** | Dupliquer la ligne | Duplique la ligne de code où se trouve le curseur (disponible dans **Visual Studio 2017 versions 15.6** et ultérieures) |
| **Maj**+**Alt**+ **+** / **-** | Développer/Réduire la sélection | Développe ou réduit la sélection actuelle dans l’éditeur (disponible dans **Visual Studio 2017 version 15.5** et les versions ultérieures) |
| **Maj** + **Alt** +  **.** | Insérer un signe insertion à la prochaine correspondance | Ajoute une sélection et un signe insertion à l’emplacement suivant qui correspond à la sélection actuelle (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |
| **Ctrl**+**Q** | Rechercher | Effectuez une recherche parmi tous les paramètres Visual Studio |
| **F5** | Démarrer le débogage | Démarrez le débogage de votre application |
| **Ctrl**+**F5** | Exécutez sans déboguer | Exécutez votre application localement sans débogage |
| **Ctrl**+**K**,**D** (Profil par défaut) ou **Ctrl**+**E**,**D** (Profil C#) | Mettre le document en forme | Nettoie les violations de mise en forme de votre fichier selon les paramètres de saut de ligne, d’espacement et de mise en retrait définis |
| **Ctrl**+ **\\** ,**Ctrl**+**E** (profil par défaut) ou **Ctrl**+**W**,**E** (profil C#) | Voir la liste des erreurs | Affichez toutes les erreurs de votre document, projet ou solution |
| **Alt** + **Pg. préc/Pg. suiv** | Accéder au problème suivant/précédent | Atteindre l’erreur, avertissement, suggestion précédent/suivant dans votre document (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |
| **Ctrl**+**K**, **/** | Activer/désactiver les marques de commentaire pour une ligne unique | Cette commande ajoute ou supprime un commentaire sur une ligne unique selon que votre sélection est déjà commentée ou non |
| **Ctrl**+**Maj**+ **/** | Activer/désactiver les marques de commentaire pour les blocs | Cette commande ajoute ou retire les commentaires de bloc en fonction de ce que vous avez sélectionné |

> [!NOTE]
> Certaines extensions dissocient les combinaisons de touches de Visual Studio par défaut. Pour utiliser les commandes ci-dessus, restaurez les valeurs par défaut de Visual Studio de vos combinaisons de touches en accédant à **Outils** > **Paramètres d’importation et d’exportation** > **Réinitialiser tous les paramètres** ou à **Outils** > **Options** > **Clavier** > **Réinitialiser**.

Pour plus d’informations sur les raccourcis clavier et les commandes, consultez [Raccourcis de productivité](../ide/productivity-shortcuts.md) et [Raccourcis clavier populaires](default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md).

## <a name="navigate-quickly-to-files-or-types"></a>Accéder rapidement aux fichiers ou aux types

Visual Studio a une fonctionnalité appelée **Atteindre tout** (**Ctrl**+**T**). **Atteindre tout** vous permet de passer rapidement à n’importe quelle déclaration de fichier, type, membre ou symbole.

- Changez l’emplacement de cette barre de recherche ou désactivez l’aperçu de navigation dynamique en utilisant l’icône d’**engrenage**.
- Filtrez les résultats avec une syntaxe comme `t mytype`.
- Limitez votre recherche au document actif.
- Le respect de la casse est pris en charge.

![Accéder à tout dans Visual Studio](../ide/media/VS2017Guide-go-to-all.png)

## <a name="enforce-code-style-rules"></a>Appliquer des règles de style de code

Vous pouvez utiliser un fichier EditorConfig pour codifier les conventions de codage et les faire suivre avec votre source.

![Application du style de code dans Visual Studio](../ide/media/VSGuide_CodeStyle.png)

- Ajoutez le fichier EditorConfig par défaut ou pour le style .NET à votre projet en choisissant **Ajouter** > **Nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément**, recherchez « editorconfig ». Sélectionnez un des modèles d'élément **Fichier editorconfig**, puis choisissez **Ajouter**.

   ![Modèles d’élément EditorConfig dans Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Créez automatiquement un fichier *.editorconfig* à partir de vos paramètres de style de code dans **Outils** > **Options** > **Éditeur de texte**  > **C#** > **Style de code**.

   ![Générer un fichier .editorconfig à partir des paramètres dans VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- La [fonctionnalité d’inférence de code](/visualstudio/intellicode/code-style-inference) d’IntelliCode pour Visual Studio déduit vos styles de code à partir du code existant. Elle crée ensuite un fichier EditorConfig non vide avec vos préférences de style de code déjà définies.

Découvrez la documentation des [options de convention de codage .NET](editorconfig-code-style-settings-reference.md), qui contient également un exemple d’un fichier EditorConfig terminé.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Nettoyage du code

Visual Studio fournit la mise en forme à la demande de votre fichier de code, avec notamment vos préférences de style de code, via la fonctionnalité **Nettoyage du code**. Pour exécuter le nettoyage du code, cliquez sur l’icône de balai en bas de l’éditeur ou appuyez sur **Ctrl**+**K**, **Ctrl**+**E**.

![Bouton de nettoyage du code dans Visual Studio 2019](media/execute-code-cleanup.png)

Vous pouvez également exécuter le nettoyage du code sur l’ensemble de votre projet ou solution. Cliquez avec le bouton droit sur le nom du projet ou de la solution dans **l’Explorateur de solutions**, sélectionnez **Analyser et nettoyer le code**, puis sélectionnez **Exécuter le nettoyage du code**.

![Exécuter le nettoyage du code sur l’ensemble du projet ou de la solution](media/run-code-cleanup-project-solution.png)

En plus de la mise en forme des espaces, des tirets, etc., dans votre fichier, le **Nettoyage du code** s’applique également aux styles de code sélectionnés. Vos préférences pour chaque style de code sont lues à partir du [fichier EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), si vous en avez un pour le projet, ou à partir des [paramètres de style de code](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) dans la boîte de dialogue **Options**.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refactorisations et corrections de code

Visual Studio est fourni avec un grand nombre de refactorisations, d’actions de génération de code et de corrections de code. Les tildes rouges représentent les erreurs, les tildes verts représentent les avertissements et trois points gris représentent les suggestions de code. Vous pouvez accéder aux correctifs de code en cliquant sur l’icône d’ampoule ou de tournevis, ou en appuyant sur **Ctrl**+ **.** ou sur **Alt**+**Entrée**. Chaque correction est accompagnée d’une fenêtre de prévisualisation qui affiche une comparaison dynamique du code pour illustrer la correction.

Les correctifs rapides et refactorisations répandus sont les suivants :

- Renommer
- Extraire la méthode
- Changer la signature de la méthode
- Générer le constructeur
- Générer la méthode
- Déplacer le type vers le fichier
- Ajouter un contrôle de valeur null
- Ajouter un paramètre
- Supprimer les instructions using inutiles
- Boucle foreach vers une requête LINQ ou une méthode LINQ
- Remonter des membres

Pour plus d’informations, consultez [Fonctionnalités de génération de code](code-generation-in-visual-studio.md).

Vous pouvez [installer des analyseurs FxCop](../code-quality/install-fxcop-analyzers.md) pour signaler des problèmes de code. Ou écrivez votre propre correctif de code ou refactorisation avec des [analyseurs Roslyn](https://github.com/dotnet/roslyn/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix).

Plusieurs membres de la communauté ont écrit des extensions gratuites qui ajoutent de nouvelles inspections de code :

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

![Refactorisations dans Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Rechercher des utilisations, accéder à l’implémentation et naviguer vers des assemblys décompilés

Visual Studio contient de nombreuses fonctionnalités qui vous permettent de rechercher et de [parcourir votre code](../ide/navigating-code.md).

| Fonctionnalité | Raccourci | Détails/améliorations |
|- | - | -|
| Rechercher toutes les références | **Maj**+**F12**| Les résultats sont en couleur et peuvent être regroupés par projet, définition et type de référence, par exemple lecture ou écriture. Vous pouvez également « verrouiller » les résultats. |
| Accéder à l’implémentation | **Ctrl**+**F12** | Vous pouvez utiliser Atteindre la définition sur le mot clé `override` pour accéder au membre substitué |
| Atteindre la définition | **F12** ou **Ctrl**+**Clic**| Appuyez sur la touche **Ctrl** et cliquez pour accéder à la définition |
| Aperçu de définition | **Alt**+**F12** | Vue inline d’une définition |
| Visualiseur de structure | Lignes grises en pointillés entre accolades | Placez le curseur pour voir la structure de votre code |
| Navigation vers les assemblys décompilés | **F12** ou **Ctrl**+**Clic** | Accédez à la source externe (décompilée avec ILSpy) en activant la fonctionnalité : **Outils** > **Options** > **Éditeur de texte** > **C#**  > **Avancé** > **Activer la navigation vers les sources décompilées**. |

![Accéder à tout et Rechercher toutes les références](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Améliorations apportées à IntelliSense

Utilisez IntelliCode pour Visual Studio pour obtenir des [complétions de code sensibles au contexte](/visualstudio/intellicode/intellicode-visual-studio) au lieu d’une simple une liste alphabétique. Vous pouvez également entraîner un [modèle IntelliSense personnalisé](/visualstudio/intellicode/custom-model-faq) en vous basant sur vos propres bibliothèques spécifiques à un domaine.

## <a name="unit-testing"></a>Test unitaire

À partir de Visual Studio 2017, les améliorations de l’expérience de test sont nombreuses. Vous pouvez tester avec les frameworks de test MSTest v1, MSTest v2, NUnit ou XUnit.

- **Explorateur de tests** La découverte de test est rapide.

- Organisez vos tests dans l’**Explorateur de tests** avec le *tri hiérarchique*.

   ![Vue de la hiérarchie de l’Explorateur de tests dans Visual Studio](../ide/media/VSGuide_Testing.png)

- [Live Unit Testing](../test/live-unit-testing.md) exécute en continu les tests impactés par vos modifications du code et met à jour les icônes de l’éditeur inline pour vous informer de l’état de vos tests. Incluez ou excluez des tests spécifiques ou des projets de test de votre jeu de tests dynamique. (Visual Studio Enterprise Edition uniquement.)

## <a name="debugging"></a>Débogage

Voici quelques-unes des fonctionnalités de débogage de Visual Studio :

::: moniker range=">=vs-2019"

- La possibilité de rechercher une chaîne dans les fenêtres **Espion**, **Automatique** et **Variables locales**.
- *Cliquer pour exécuter*, qui vous permet de placer le curseur à côté d’une ligne de code, de cliquer sur l’icône verte de « lecture » qui s’affiche et d’exécuter votre programme jusqu’à ce qu’il atteigne cette ligne.
- L’**Assistance sur l’exception**, qui place les informations les plus importantes en haut de la boîte de dialogue, par exemple quelle variable est `null` dans une `NullReferenceException`.
- Le [débogage Revenir en arrière](../debugger/view-historical-application-state.md), qui vous permet de revenir aux étapes ou aux points d’arrêt précédents et de voir l’état de l’application comme elle était avant.
- Le [débogage de capture instantanée](/azure/application-insights/app-insights-snapshot-debugger), qui vous permet d’examiner l’état d’une application web dynamique au moment où une exception a été levée (sur Azure uniquement).

::: moniker-end

::: moniker range="vs-2017"

- *Cliquer pour exécuter*, qui vous permet de placer le curseur à côté d’une ligne de code, de cliquer sur l’icône verte de « lecture » qui s’affiche et d’exécuter votre programme jusqu’à ce qu’il atteigne cette ligne.
- L’**Assistance sur l’exception**, qui place les informations les plus importantes en haut de la boîte de dialogue, par exemple quelle variable est `null` dans une `NullReferenceException`.
- Le [débogage Revenir en arrière](../debugger/view-historical-application-state.md), qui vous permet de revenir aux étapes ou aux points d’arrêt précédents et de voir l’état de l’application comme elle était avant.
- Le [débogage de capture instantanée](/azure/application-insights/app-insights-snapshot-debugger), qui vous permet d’examiner l’état d’une application web dynamique au moment où une exception a été levée (sur Azure uniquement).

::: moniker-end

![Assistance sur l’exception dans Visual Studio](../ide/media/VSGuide_Debugging.png)

## <a name="version-control"></a>Gestion de version

Vous pouvez utiliser git ou TFVC pour stocker et mettre à jour votre code dans Visual Studio.

::: moniker range=">=vs-2019"

- Installez les [demandes de tirage pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=vsideversioncontrolmsft.pr4vs) pour créer, réviser, extraire et exécuter des demandes de tirage sans quitter Visual Studio.

::: moniker-end

- Organisez vos changements locaux dans [Team Explorer](reference/team-explorer-reference.md) et utilisez la barre d’état pour suivre les commits et les changements en attente.

- Configurez l’intégration et la livraison continues pour vos projets ASP.NET dans Visual Studio avec l’extension [Outils de livraison continue pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=VSIDEDevOpsMSFT.ContinuousDeliveryToolsforVisualStudio).

![Contrôle de code source dans Visual Studio](../ide/media/VSIDE_Productivity_SourceControl.png)

## <a name="what-other-features-should-i-know-about"></a>Quelles sont les autres fonctionnalités à connaître ?

Voici une liste de fonctionnalités de l’éditeur liées à la productivité pour rendre l’écriture de code plus efficace. Vous devrez peut-être activer certaines fonctionnalités, car elles sont désactivées par défaut (elles peuvent éventuellement indexer des éléments sur votre machine, être controversées ou être à l’état expérimental).

| Fonctionnalité | Détails | Comment activer |
|-|-|-|
| Rechercher un fichier dans l’Explorateur de solutions | Met en évidence le fichier actif dans **Explorateur de solutions** | **Outils** > **Options** > **Projets et solutions** > **Suivre un élément actif dans l’Explorateur de solutions** |
| Ajouter des instructions using pour les types dans les assemblys de référence et les packages NuGet | Affiche une ampoule d’erreur avec un correctif de code pour installer un package NuGet pour un type non référencé | **Outils** > **Options** > **Éditeur de texte** > **C#**  > **Avancé** > **Suggérer des usings pour les types dans les assemblys de référence** et **Suggérer des usings pour les types dans les packages NuGet** |
| Activer l’analyse complète de la solution | Visualisez toutes les erreurs de votre solution dans la **Liste d’erreurs** | **Outils** > **Options** > **Éditeur de texte** > **C#**  > **Avancé**   > **Activer l’analyse complète de la solution** |
| Activer la navigation vers les sources décompilées | Permet d’activer la fonctionnalité Atteindre la définition sur les types/membres de sources externes et d’utiliser le décompilateur ILSpy pour afficher les corps de méthodes | **Outils** > **Options** > **Éditeur de texte** > **C#**  > **Avancé** > **Activer la navigation vers les sources décompilées** |
| Mode de saisie semi-automatique/suggestion | Change le comportement de complétion dans IntelliSense. Les développeurs qui utilisaient IntelliJ ont tendance à utiliser un paramètre qui n’est pas un paramètre par défaut. | **Menu** > **Modifier** > **IntelliSense** > **Activer/Désactiver le mode de saisie semi-automatique** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Affiche les informations de référence du code et l’historique des modifications dans l’éditeur. (Les indicateurs CodeLens de contrôle de code source ne sont pas disponibles dans l’édition Visual Studio Community.) | **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **CodeLens** |
| [Extraits de code](../ide/visual-csharp-code-snippets.md) | Permet de vous épargner le code réutilisable courant | Tapez un nom d’extrait et appuyez deux fois sur **Tab**. |
