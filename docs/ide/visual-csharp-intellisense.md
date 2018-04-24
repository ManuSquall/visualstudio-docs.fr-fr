---
title: C# IntelliSense | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1a443258d7f3b71c8f14cb967fc37090f80b5ad5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="c-intellisense"></a>C# IntelliSense

C# IntelliSense est disponible quand vous écrivez du code dans l’éditeur et quand vous déboguez du code dans la fenêtre de commande [Mode Exécution](../ide/reference/immediate-window.md).

## <a name="completion-lists"></a>Listes de saisie semi-automatique

Les listes de saisie semi-automatique IntelliSense en C# contiennent des jetons des fonctionnalités Liste des membres, Compléter le mot, etc. Vous bénéficiez d'un accès rapide aux éléments suivants :

- Membres d’un type ou d’un espace de noms

- Noms de variables, de commandes et de fonctions

- Extraits de code

- Mots clés de langage

- méthodes d’extension.

La liste de saisie semi-automatique en C# est également assez intelligente pour éliminer les jetons inappropriés et présélectionner un jeton selon le contexte. Pour plus d’informations, consultez [Listes de saisie semi-automatique filtrées](#filtered-completion-lists).

## <a name="code-snippets-in-completion-lists"></a>Extraits de code dans les listes de saisie semi-automatique

En C#, la liste de saisie semi-automatique comprend des extraits de code pour vous aider à insérer facilement des entités prédéfinies de code dans votre programme. Dans la liste de saisie semi-automatique, les extraits de code sont affichés sous forme de [raccourci](../ide/code-snippets-schema-reference.md#shortcut) d’extrait de code. Pour plus d'informations sur les extraits de code fournis par défaut en C#, consultez [Liste d'extraits de code C#](../ide/visual-csharp-code-snippets.md).

## <a name="language-keywords-in-completion-lists"></a>Mots clés de langage dans les listes de saisie semi-automatique

En C#, la liste de saisie semi-automatique inclut également des mots clés de langage. Pour plus d’informations sur les mots clés du langage C#, consultez [Mots clés C#](/dotnet/csharp/language-reference/keywords/index).

## <a name="extension-methods-in-completion-lists"></a>Méthodes d’extension dans les listes de saisie semi-automatique

En C#, la liste de saisie semi-automatique inclut les méthodes d’extension qui sont dans la portée.

> [!NOTE]
> La liste de saisie semi-automatique n'affiche pas toutes les méthodes d'extension pour les objets <xref:System.String>.

Les méthodes d’extension utilisent une icône différente de celle des méthodes d’instance. Pour obtenir la liste des icônes de liste, consultez [Icônes de l’Explorateur d’objets et de la fenêtre Affichage de classes](../ide/class-view-and-object-browser-icons.md). Quand une méthode d’instance et une méthode d’extension portant le même nom sont toutes deux dans la portée, la liste de saisie semi-automatique affiche l’icône de la méthode d’extension.

## <a name="filtered-completion-lists"></a>Listes de saisie semi-automatique filtrées

IntelliSense supprime les membres inutiles de la liste de saisie semi-automatique à l'aide de filtres. C# filtre les listes de saisie semi-automatique qui apparaissent pour les éléments suivants :

- **Interfaces et classes de base** : IntelliSense supprime automatiquement les éléments dans les listes de saisie semi-automatique des interfaces et des classes de base, à la fois dans les listes d’interfaces et de classes de base de déclaration, et dans les listes de contraintes. Par exemple, les enums n'apparaissent pas dans la liste de saisie semi-automatique pour les classes de base, car les enums ne peuvent pas être utilisés pour les classes de base. La liste de saisie semi-automatique des classes de base contient uniquement des interfaces et des espaces de noms. Si vous sélectionnez un élément dans la liste et que vous tapiez une virgule, IntelliSense supprime les classes de base de la liste de saisie semi-automatique, car C# ne prend pas en charge l'héritage multiple. Le même comportement se produit également pour les clauses de contrainte.

- **Attributs** : quand vous appliquez un attribut à un type, la liste de saisie semi-automatique est filtrée afin de répertorier uniquement les types qui descendent des espaces de noms qui contiennent ces types, comme <xref:System.Attribute>.

- **Clauses catch**

- **Initialiseurs d’objets** : seuls les membres qui peuvent être initialisés apparaissent dans la liste de saisie semi-automatique.

- **Mot clé new** : quand vous tapez `new` et appuyez sur la barre d’espace, une liste de saisie semi-automatique s’affiche. Un élément est sélectionné automatiquement dans la liste en fonction du contexte de votre code. Par exemple, des éléments sont automatiquement sélectionnés dans la liste de saisie semi-automatique pour les déclarations et pour les instructions return dans les méthodes.

- **Mot clé enum** : quand vous appuyez sur la barre d’espace après un signe égal pour une assignation enum, une liste de saisie semi-automatique apparaît. Un élément est sélectionné automatiquement dans la liste en fonction du contexte de votre code. Par exemple, des éléments sont automatiquement sélectionnés dans la liste de saisie semi-automatique quand vous tapez le mot clé return et quand vous effectuez une déclaration.

- **Opérateurs as et is** : une liste de saisie semi-automatique filtrée s’affiche automatiquement quand vous appuyez sur la barre d’espace après avoir tapé le mot clé `as` ou `is`.

- **Événements** : quand vous tapez le mot clé `event`, la liste de saisie semi-automatique contient uniquement des types délégués.

- **Aide sur les paramètres** : affiche automatiquement la première surcharge de méthode qui correspond aux paramètres que vous entrez. Si plusieurs surcharges de méthode sont disponibles, vous pouvez utilisez les flèches haut et bas pour accéder à la surcharge suivante dans la liste.

## <a name="most-recently-used-members"></a>Membres utilisés récemment

IntelliSense mémorise les membres que vous avez récemment sélectionnés dans la fenêtre contextuelle [Liste des membres](../ide/using-intellisense.md) pour la saisie semi-automatique du nom d’objet. La prochaine fois que vous utilisez la liste des membres, les membres utilisés récemment seront affichés en haut. L'historique des membres utilisés récemment est effacé entre chaque session dans l'IDE.

## <a name="override"></a>override

Lorsque vous tapez [override](/dotnet/csharp/language-reference/keywords/override) et appuyez sur la touche Espace, IntelliSense affiche dans une zone de liste contextuelle tous les membres valides de la classe de base que vous pouvez substituer. La saisie du type de retour de la méthode après `override` indique à IntelliSense d'afficher uniquement les méthodes qui retournent le même type. Quand IntelliSense ne trouve aucune correspondance, il affiche tous les membres de la classe de base.

## <a name="automatic-code-generation"></a>Génération de code automatique

### <a name="add-using"></a>Ajouter using

L’opération IntelliSense **Ajouter using** ajoute automatiquement la directive `using` obligatoire dans votre fichier de code. Avec cette fonctionnalité, vous pouvez conserver le focus dans le code que vous écrivez au lieu de devoir le déplacer vers une autre partie du code.

Pour lancer l'opération Ajouter using, positionnez le curseur sur une référence de type qui ne peut pas être résolue. Par exemple, quand vous créez une application console et que vous ajoutez ensuite `XmlTextReader` dans le corps de la méthode `Main`, une ligne ondulée rouge s’affiche sous cette ligne de code pour signaler que la référence de type ne peut pas être résolue. Vous pouvez ensuite appeler l’opération Ajouter using par le biais d’une action rapide. L’action rapide s’affiche uniquement quand vous placez le curseur sur le type indépendant.

![Ajouter using, image développée de l’action rapide](../ide/media/addusing-quickaction.png "AddUsing-QuickAction")

Cliquez sur l’icône Ampoule, puis choisissez **using System.Xml;** pour ajouter automatiquement la directive using.

### <a name="remove-and-sort-usings"></a>Supprimer et trier les directives using

L’option **Supprimer et trier les directives using** trie et supprime les déclarations `using` et `extern` sans changer le comportement du code source. Au fil du temps, les fichiers sources peuvent devenir trop importants et difficiles à lire à cause de directives `using` inutiles et désorganisées. L’option **Supprimer et trier les directives using** compacte le code source en supprimant les directives `using` inutilisées, et elle trie les directives pour améliorer la lisibilité du code. Dans le menu **Edition**, choisissez **IntelliSense**, puis choisissez **Organiser les instructions Using**.

### <a name="implement-interface"></a>Implémenter l'interface

IntelliSense propose une option pour vous aider à implémenter une [interface](/dotnet/csharp/language-reference/keywords/interface) tout en travaillant dans l’éditeur de code. Normalement, pour implémenter correctement une interface, vous devez créer une déclaration de méthode pour chaque membre de l’interface dans votre classe. Grâce à IntelliSense, quand vous tapez le nom d’une interface dans une déclaration de classe, une ampoule Actions rapides s’affiche. Cette fonctionnalité vous permet d’implémenter l’interface automatiquement, à l’aide d’un nommage explicite ou implicite. Sous l'affectation de noms explicite, les déclarations de méthode comportent le nom de l'interface. Sous l'affectation de noms implicite, les déclarations de méthode n'indiquent pas l'interface à laquelle elles appartiennent. Une méthode d'interface explicitement nommée est accessible uniquement via une instance d'interface et non via une instance de classe. Pour plus d’informations, consultez [Implémentation d’interface explicite](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

L'option Implémenter l'interface génère le nombre minimal de stubs de méthode requis pour satisfaire l'interface. Si une classe de base implémente des parties de l'interface, ces stubs ne sont pas régénérés.

### <a name="implement-abstract-base-class"></a>Implémenter une classe de base abstraite

IntelliSense fournit une option qui vous aidera à implémenter automatiquement les membres d'une classe de base abstraite pendant que vous travaillez dans l'éditeur de code. Normalement, pour implémenter les membres d'une classe de base abstraite, il est nécessaire de créer une nouvelle définition de méthode pour chaque méthode de la classe de base abstraite dans votre classe dérivée. Grâce à IntelliSense, après avoir tapé le nom d’une classe de base abstraite dans une déclaration de classe, une ampoule Actions rapides s’affiche. Cette fonctionnalité vous permet d’implémenter automatiquement les méthodes de la classe de base.

Les stubs de méthode générés par la fonctionnalité Implémenter une classe de base abstraite sont modélisés par l'extrait de code défini dans le fichier MethodStub.snippet. Les extraits de code sont modifiables. Pour plus d’informations, consultez [Procédure pas à pas : création d’un extrait de code](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Générer à partir de l'utilisation

La fonctionnalité **Générer à partir de l’utilisation** permet d’utiliser des classes et des membres avant de les définir. Vous pouvez générer un stub pour une classe, un constructeur, une méthode, une propriété, un champ ou une énumération quelconque que vous souhaitez utiliser, mais que vous n'avez pas encore défini. Vous pouvez générer de nouveaux types et membres sans quitter votre emplacement actuel dans le code. Cette opération réduit l'interruption de votre flux de travail.

Une ligne ondulée rouge s’affiche sous chaque identificateur non défini. Quand vous placez le pointeur de la souris sur l'identificateur, un message d'erreur s'affiche dans une info-bulle. Pour afficher les options appropriées, vous pouvez utiliser l'une des procédures suivantes :

- Cliquez sur l'identificateur non défini. Une ampoule Actions rapides s’affiche sous l’identificateur. Cliquez sur l’ampoule.

- Cliquez sur l’identificateur non défini, puis appuyez sur **Ctrl** + **.** (Ctrl+point).

- Cliquez avec le bouton droit sur l’identificateur non défini, puis cliquez sur **Actions rapides et refactorisations**.

Les options qui apparaissent peuvent inclure les éléments suivants :

- **Générer la propriété**

- **Générer le champ**

- **Générer la méthode**

- **Générer la classe**

- **Générer un nouveau type...** (pour une classe, un struct, une interface ou un enum)

## <a name="generate-event-handlers"></a>Générer des gestionnaires d'événements

Dans l'éditeur de code, IntelliSense peut vous aider à connecter des méthodes (gestionnaires d'événements) à des champs d'événement.

Quand vous tapez l’opérateur `+=` après un champ d’événement dans un fichier .cs, IntelliSense vous invite à appuyer sur la touche **Tab**. Une nouvelle instance d'un délégué pointant vers la méthode qui gère l'événement est alors insérée.

![Bouton de raccordement automatique](../ide/media/vxautohookup.gif "vxAutoHookUp")

Si vous appuyez sur la touche **Tab**, IntelliSense complète l’instruction automatiquement et affiche la référence du gestionnaire d’événements sous forme de texte sélectionné dans l’éditeur de code. Pour terminer la connexion d’événements automatique, IntelliSense vous invite à appuyer de nouveau sur la touche **Tab** afin de créer un stub vide pour le gestionnaire d’événements.

![Générer un gestionnaire d’événements](../ide/media/vxgenerateeventhandler.gif "vxGenerateEventHandler")

> [!NOTE]
> Si un nouveau délégué créé par IntelliSense fait référence à un gestionnaire d'événements existant, IntelliSense communique cette information dans l'info-bulle. Vous pouvez ensuite modifier cette référence, dans la mesure où le texte est déjà sélectionné dans l'éditeur de code. Sinon, la connexion d'événements automatique se termine à ce stade.

Si vous appuyez sur la touche **Tab**, IntelliSense choisit une méthode avec la signature appropriée et place le curseur dans le corps de votre gestionnaire d’événements.

> [!NOTE]
> Utilisez la commande **Naviguer vers l’arrière** du menu **Affichage** (**Ctrl** + **-**) pour revenir à l’instruction de connexion d’événements.

## <a name="see-also"></a>Voir aussi

[Utilisation de la fonctionnalité IntelliSense](../ide/using-intellisense.md)  
[IDE Visual Studio](../ide/visual-studio-ide.md)