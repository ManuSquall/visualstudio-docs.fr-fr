---
title: Améliorer votre productivité pour le développement .NET
description: Vue d’ensemble de la navigation, de l’analyse du code, des tests unitaires et d’autres fonctionnalités qui vont vous aider à écrire du code .NET plus performant plus rapidement.
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- editor
ms.workload:
- dotnet
ms.openlocfilehash: 09a33db9df8e1309792cd6a3722bb82333348d84
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038653"
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
| **CTRL** + **T** | Atteindre tout | Accéder à n’importe quel fichier, type, membre ou toute déclaration de symbole |
| **F12** (également **CTRL +** + **clic**) | Atteindre la définition | Accédez à l’emplacement de définition d’un symbole |
| **CTRL** + **F12** | Accéder à l’implémentation | Accédez à partir d’un type ou membre de base à ses diverses implémentations |
| **MAJ** + **F12** | Rechercher toutes les références | Affichez toutes les références de symboles et de littéraux |
| **ALT** + **Page d’hébergement** | Accéder à la base | Naviguer vers le haut de la chaîne d’héritage |
| **CTRL** + **.** (également **ALT** + **Entrer** dans le profil C#) | Actions rapides et refactorisations | Affichez les correctifs de code, les actions de génération de code, les refactorisations et les autres actions rapides qui sont disponibles au niveau de votre curseur ou de votre sélection de code |
| **CTRL** + **D** | Dupliquer la ligne | Duplique la ligne de code où se trouve le curseur (disponible dans **Visual Studio 2017 versions 15.6** et ultérieures) |
| **MAJ** + **ALT**+**+**/**-** | Développer/Réduire la sélection | Développe ou réduit la sélection actuelle dans l’éditeur (disponible dans **Visual Studio 2017 version 15.5** et les versions ultérieures) |
| **MAJ**  +  **ALT**  +  **.** | Insérer un signe insertion à la prochaine correspondance | Ajoute une sélection et un signe insertion à l’emplacement suivant qui correspond à la sélection actuelle (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |
| **CTRL** + **Q** | Recherche | Effectuez une recherche parmi tous les paramètres Visual Studio |
| **F5** | Démarrer le débogage | Démarrez le débogage de votre application |
| **CTRL** + **F5** | Exécutez sans déboguer | Exécutez votre application localement sans débogage |
| **CTRL** + **K**,**d** (profil par défaut) ou **CTRL** + **E**,**d** (profil C#) | Mettre le document en forme | Nettoie les violations de mise en forme de votre fichier selon les paramètres de saut de ligne, d’espacement et de mise en retrait définis |
| **CTRL** + **\\** ,**CTRL** + **e** (profil par défaut) ou **CTRL** + **W**,**e** (profil C#) | Voir la liste des erreurs | Affichez toutes les erreurs de votre document, projet ou solution |
| **ALT**  +  **PG PRÉC/PG SUIV** | Accéder au problème suivant/précédent | Atteindre l’erreur, avertissement, suggestion précédent/suivant dans votre document (disponible dans **Visual Studio 2017 version 15.8** et ultérieures) |
| **CTRL** + **K**,**/** | Activer/désactiver les marques de commentaire pour une ligne unique | Cette commande ajoute ou supprime un commentaire sur une ligne unique selon que votre sélection est déjà commentée ou non |
| **CTRL** + **MAJ**+**/** | Activer/désactiver les marques de commentaire pour les blocs | Cette commande ajoute ou retire les commentaires de bloc en fonction de ce que vous avez sélectionné |

> [!NOTE]
> Certaines extensions dissocient les combinaisons de touches de Visual Studio par défaut. Pour utiliser les commandes ci-dessus, restaurez vos combinaisons de touches aux valeurs par défaut de Visual Studio en accédant à **Outils**  >  **importation et exportation de paramètres**  >  **Réinitialiser tous les paramètres** ou **Outils**  >  **options**  >    >  **Réinitialiser** le clavier.

Pour plus d’informations sur les raccourcis clavier et les commandes, consultez [Raccourcis de productivité](../ide/productivity-shortcuts.md) et [Raccourcis clavier populaires](default-keyboard-shortcuts-in-visual-studio.md).

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

- Ajoutez une valeur par défaut ou. Fichier EditorConfig de style net à votre projet en sélectionnant **Ajouter**  >  **un nouvel élément**. Dans la boîte de dialogue **Ajouter un nouvel élément**, recherchez « editorconfig ». Sélectionnez un des modèles d'élément **Fichier editorconfig**, puis choisissez **Ajouter**.

   ![Modèles d’élément EditorConfig dans Visual Studio](media/editorconfig-item-templates.png)

::: moniker range=">=vs-2019"

- Créez automatiquement un fichier *. editorconfig* basé sur vos paramètres de style de code dans **Outils** > **options** > **éditeur de texte** > style de  > **code** C#.

   ![Générer un fichier .editorconfig à partir des paramètres dans VS 2019](media/vs-2019/generate-editorconfig-file.png)

::: moniker-end

- La [fonctionnalité d’inférence de code](/visualstudio/intellicode/code-style-inference) d’IntelliCode pour Visual Studio déduit vos styles de code à partir du code existant. Elle crée ensuite un fichier EditorConfig non vide avec vos préférences de style de code déjà définies.

- Configurez le niveau de gravité d’une règle de style de code directement par le biais de l’éditeur. Si vous n’avez pas de fichier. editorconfig, un fichier est généré pour vous. Placez le curseur sur l’erreur, l’avertissement ou la suggestion, puis tapez **CTRL** + **.** pour ouvrir le menu Actions rapides et refactorisations. Sélectionnez **configurer ou supprimer les problèmes**. Sélectionnez ensuite la règle, et choisissez le niveau de gravité que vous souhaitez configurer pour celle-ci. Cette opération met à jour votre configuration EditorConfig existante avec la nouvelle gravité de la règle.

   ![Configurer le niveau de gravité d’une règle de style de code directement dans l’éditeur](../ide/media/configure-severity-level.png)

Découvrez la documentation des [options de convention de codage .NET](/dotnet/fundamentals/code-analysis/code-style-rule-options), qui contient également un exemple d’un fichier EditorConfig terminé.

::: moniker range=">=vs-2019"

## <a name="code-cleanup"></a>Nettoyage du code

Visual Studio fournit la mise en forme à la demande de votre fichier de code, avec notamment vos préférences de style de code, via la fonctionnalité **Nettoyage du code**. Pour exécuter le nettoyage du code, cliquez sur l’icône du balai en bas de l’éditeur ou appuyez sur **CTRL** + **K**, **CTRL** + **E**.

![Bouton de nettoyage du code dans Visual Studio 2019](media/execute-code-cleanup.png)

Vous pouvez également exécuter le nettoyage du code sur l’ensemble de votre projet ou solution. Cliquez avec le bouton droit sur le nom du projet ou de la solution dans **l’Explorateur de solutions**, sélectionnez **Analyser et nettoyer le code**, puis sélectionnez **Exécuter le nettoyage du code**.

![Exécuter le nettoyage du code sur l’ensemble du projet ou de la solution](media/run-code-cleanup-project-solution.png)

En plus de la mise en forme des espaces, des tirets, etc., dans votre fichier, le **Nettoyage du code** s’applique également aux styles de code sélectionnés. Vos préférences pour chaque style de code sont lues à partir du [fichier EditorConfig](code-styles-and-code-cleanup.md#code-styles-in-editorconfig-files), si vous en avez un pour le projet, ou à partir des [paramètres de style de code](code-styles-and-code-cleanup.md#code-styles-in-the-options-dialog-box) dans la boîte de dialogue **Options**.

::: moniker-end

## <a name="refactorings-and-code-fixes"></a>Refactorisations et corrections de code

Visual Studio est fourni avec un grand nombre de refactorisations, d’actions de génération de code et de corrections de code. Les tildes rouges représentent les erreurs, les tildes verts représentent les avertissements et trois points gris représentent les suggestions de code. Vous pouvez accéder aux corrections de code en cliquant sur l’icône de l’ampoule ou du tournevis, ou en appuyant sur **CTRL** + **.** ou **ALT** + **entrée**. Chaque correction est accompagnée d’une fenêtre de prévisualisation qui affiche une comparaison dynamique du code pour illustrer la correction.

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

Pour plus d’informations, consultez [fonctionnalités de génération de code](code-generation-in-visual-studio.md).

Vous pouvez [installer des analyseurs FxCop](../code-quality/install-fxcop-analyzers.md) pour signaler des problèmes de code. Ou écrivez votre propre correctif de code ou refactorisation avec des [analyseurs Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Getting-Started-Writing-a-Custom-Analyzer-&-Code-Fix.md).

Plusieurs membres de la communauté ont écrit des extensions gratuites qui ajoutent de nouvelles inspections de code :

::: moniker range="vs-2017"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2017)
- [SonarLint pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2017)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

::: moniker range=">=vs-2019"

- [Roslynator](https://marketplace.visualstudio.com/items?itemName=josefpihrt.Roslynator2019)
- [SonarLint pour Visual Studio](https://marketplace.visualstudio.com/items?itemName=SonarSource.SonarLintforVisualStudio2019)
- [StyleCopAnalyzers](https://www.nuget.org/packages/stylecop.analyzers/)
- [CodeCracker](https://www.nuget.org/packages/codecracker.CSharp/)

::: moniker-end

![Refactorisations dans Visual Studio](../ide/media/VSGuide_CodeAnalysis.png)

## <a name="find-usages-go-to-implementation-and-navigate-to-decompiled-assemblies"></a>Rechercher des utilisations, accéder à l’implémentation et naviguer vers des assemblys décompilés

Visual Studio contient de nombreuses fonctionnalités qui vous permettent de rechercher et de [parcourir votre code](../ide/navigating-code.md).

| Fonctionnalité | Raccourci | Détails/améliorations |
|- | - | -|
| Rechercher toutes les références | **MAJ** + **F12**| Les résultats sont en couleur et peuvent être regroupés par projet, définition et type de référence, par exemple lecture ou écriture. Vous pouvez également « verrouiller » les résultats. |
| Accéder à l’implémentation | **CTRL** + **F12** | Vous pouvez utiliser Atteindre la définition sur le mot clé `override` pour accéder au membre substitué |
| Atteindre la définition | **F12** ou **CTRL +** + **clic**| Appuyez sur la touche **Ctrl** et cliquez pour accéder à la définition |
| Aperçu de la définition | **ALT** + **F12** | Vue inline d’une définition |
| Visualiseur de structure | Lignes grises en pointillés entre accolades | Placez le curseur pour voir la structure de votre code |
| Navigation vers les assemblys décompilés | **F12** ou **CTRL +** + **clic** | Accédez à source externe (décompilée avec ILSpy) en activant la fonctionnalité : **Outils**  >  **options**  >  **éditeur de texte**  >  **C#**  >  **avancé**  >  **activer la navigation vers les sources décompilées**. |

![Accéder à tout et Rechercher toutes les références](../ide/media/VSIDE_Productivity_Navigation.png)

## <a name="improved-intellisense"></a>Améliorations apportées à IntelliSense

Utilisez IntelliCode pour Visual Studio pour obtenir des [complétions de code sensibles au contexte](/visualstudio/intellicode/intellicode-visual-studio) au lieu d’une simple une liste alphabétique. Vous pouvez également entraîner un [modèle IntelliSense personnalisé](/visualstudio/intellicode/custom-model-faq) en vous basant sur vos propres bibliothèques spécifiques à un domaine.

## <a name="unit-testing"></a>Effectuer des tests unitaires

À partir de Visual Studio 2017, les améliorations de l’expérience de test sont nombreuses. Vous pouvez tester avec les frameworks de test MSTest v1, MSTest v2, NUnit ou XUnit.

- **Explorateur de tests** La découverte de test est rapide.

- Organisez vos tests dans l’**Explorateur de tests** avec le *tri hiérarchique*.

   ![Vue de la hiérarchie de l’Explorateur de tests dans Visual Studio](../ide/media/VSGuide_Testing.png)

- [Live Unit testing](../test/live-unit-testing.md) exécute en permanence les tests affectés par les modifications de votre code et met à jour les icônes de l’éditeur inline pour vous informer de l’état de vos tests. Incluez ou excluez des tests spécifiques ou des projets de test de votre jeu de tests dynamique. (Visual Studio Enterprise Edition uniquement.)

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

## <a name="version-control"></a>Gestion de versions

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
| Rechercher un fichier dans l’Explorateur de solutions | Met en évidence le fichier actif dans **Explorateur de solutions** | **Outils**  >  **Options**  >  **Projets et solutions**  >  **Suivre un élément actif dans Explorateur de solutions** |
| Ajouter des instructions using pour les types dans les assemblys de référence et les packages NuGet | Affiche une ampoule d’erreur avec un correctif de code pour installer un package NuGet pour un type non référencé | **Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Paramètres avancés**  >  **Suggérer des usings pour les types dans les assemblys de référence** et **suggérer des using pour les types dans les packages NuGet** |
| Activer l’analyse complète de la solution | Voir toutes les erreurs dans votre solution dans le **liste d’erreurs** | **Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Paramètres avancés**  >  **Activer l’analyse complète** de la solution |
| Activer la navigation vers les sources décompilées | Permet d’activer la fonctionnalité Atteindre la définition sur les types/membres de sources externes et d’utiliser le décompilateur ILSpy pour afficher les corps de méthodes | **Outils**  >  **Options**  >  **Éditeur**  >  de texte **C#**  >  **Paramètres avancés**  >  **Activer la navigation vers les sources décompilées** |
| Mode de saisie semi-automatique/suggestion | Change le comportement de complétion dans IntelliSense. Les développeurs qui utilisaient IntelliJ ont tendance à utiliser un paramètre qui n’est pas un paramètre par défaut. | **Menu**  >  **Modifier**  >  **IntelliSense**  >  **Activer/désactiver le mode de saisie semi-automatique** |
| [CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md) | Affiche les informations de référence du code et l’historique des modifications dans l’éditeur. (Les indicateurs CodeLens de contrôle de code source ne sont pas disponibles dans l’édition Visual Studio Community.) | **Outils**  >  **Options**  >  **Éditeur**  >  de texte **Toutes les langues**  >  **CodeLens** |
| [Extraits de code](../ide/visual-csharp-code-snippets.md) | Permet de vous épargner le code réutilisable courant | Tapez un nom d’extrait de code, puis appuyez deux fois sur la **touche Tab** . |
