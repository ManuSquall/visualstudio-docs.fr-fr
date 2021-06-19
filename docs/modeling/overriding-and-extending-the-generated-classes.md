---
title: Substitution et extension des classes générées
description: Découvrez comment votre définition DSL est une plateforme sur laquelle vous pouvez créer un ensemble puissant d’outils basés sur un langage spécifique à un domaine.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 07c44e7ff7a603f339ec268b06bd78cc84cd6be2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390943"
---
# <a name="override-and-extend-the-generated-classes"></a>Remplacer et étendre les classes générées

Votre définition DSL est une plateforme sur laquelle vous pouvez créer un ensemble puissant d’outils basés sur un langage spécifique à un domaine. De nombreuses extensions et adaptations peuvent être effectuées en remplaçant et en étendant les classes générées à partir de la définition DSL. Ces classes incluent non seulement les classes de domaine que vous avez définies explicitement dans le diagramme de définition DSL, mais également d’autres classes qui définissent la boîte à outils, l’Explorateur, la sérialisation, etc.

## <a name="extensibility-mechanisms"></a>Mécanismes d’extensibilité

Plusieurs mécanismes sont fournis pour vous permettre d’étendre le code généré.

### <a name="override-methods-in-a-partial-class"></a>Substituer les méthodes dans une classe partielle

Les définitions de classes partielles permettent de définir une classe dans plusieurs emplacements. Cela vous permet de séparer le code généré du code que vous écrivez vous-même. Dans votre code écrit manuellement, vous pouvez remplacer les classes héritées par le code généré.

Par exemple, si dans votre définition DSL vous définissez une classe de domaine nommée `Book` , vous pouvez écrire du code personnalisé qui ajoute des méthodes override :

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Pour substituer les méthodes dans une classe générée, écrivez toujours votre code dans un fichier séparé des fichiers générés. En règle générale, le fichier est contenu dans un dossier nommé CustomCode. Si vous apportez des modifications au code généré, elles seront perdues quand vous régénérez le code à partir de la définition DSL.

Pour découvrir les méthodes que vous pouvez substituer, tapez **override** dans la classe, suivi d’un espace. L’info-bulle IntelliSense vous indique les méthodes qui peuvent être substituées.

### <a name="double-derived-classes"></a>Classes Double-Derived

La plupart des méthodes des classes générées sont héritées d’un ensemble fixe de classes dans les espaces de noms de modélisation. Toutefois, certaines méthodes sont définies dans le code généré. En règle générale, cela signifie que vous ne pouvez pas les remplacer ; vous ne pouvez pas substituer dans une classe partielle les méthodes qui sont définies dans une autre définition partielle de la même classe.

Toutefois, vous pouvez substituer ces méthodes en définissant le paramètre génère un indicateur de **double dérivé** pour la classe de domaine. Deux classes sont alors générées, l’une étant une classe de base abstraite de l’autre. Toutes les définitions de méthode et de propriété se trouvent dans la classe de base, et seul le constructeur est dans la classe dérivée.

Par exemple, dans l’exemple de bibliothèque. DSL, la propriété de la `CirculationBook` classe de domaine a la `Generates``Double Derived` valeur `true` . Le code généré pour cette classe de domaine contient deux classes :

- `CirculationBookBase`, qui est un abstrait et qui contient toutes les méthodes et propriétés.

- `CirculationBook`, qui est dérivé de `CirculationBookBase` . Elle est vide, à l’exception de ses constructeurs.

Pour substituer n’importe quelle méthode, vous créez une définition partielle de la classe dérivée telle que `CirculationBook` . Vous pouvez substituer les méthodes générées et les méthodes héritées de l’infrastructure de modélisation.

Vous pouvez utiliser cette méthode avec tous les types d’élément, y compris les éléments de modèle, les relations, les formes, les diagrammes et les connecteurs. Vous pouvez également substituer des méthodes d’autres classes générées. Certaines classes générées, telles que ToolboxHelper, sont toujours doubles dérivées.

### <a name="custom-constructors"></a>Constructeurs personnalisés

Vous ne pouvez pas substituer un constructeur. Même dans les classes dérivées de double, le constructeur doit être dans la classe dérivée.

Si vous souhaitez fournir votre propre constructeur, vous pouvez le faire en définissant `Has Custom Constructor` pour la classe de domaine dans la définition DSL. Lorsque vous cliquez sur **transformer tous les modèles**, le code généré n’inclut pas de constructeur pour cette classe. Elle inclura un appel au constructeur manquant. Cela provoque un rapport d’Erreurs lorsque vous générez la solution. Double-cliquez sur le rapport d’erreurs pour afficher un commentaire dans le code généré qui explique ce que vous devez fournir.

Écrivez une définition de classe partielle dans un fichier distinct des fichiers générés et fournissez le constructeur.

### <a name="flagged-extension-points"></a>Points d’extension avec indicateur

Un point d’extension avec indicateur est un emplacement dans la définition DSL où vous pouvez définir une propriété ou une case à cocher pour indiquer que vous allez fournir une méthode personnalisée. Les constructeurs personnalisés en sont un exemple. D’autres exemples incluent la définition `Kind` d’une propriété de domaine sur un stockage calculé ou personnalisé ou la définition de l’indicateur **is Custom** dans un générateur de connexions.

Dans chaque cas, lorsque vous définissez l’indicateur et régénérez le code, une erreur de génération se produit. Double-cliquez sur l’erreur pour afficher un commentaire qui explique ce que vous devez fournir.

### <a name="rules"></a>Règles

Le gestionnaire de transactions vous permet de définir des règles qui s’exécutent avant la fin d’une transaction dans laquelle un événement désigné s’est produit, tel qu’une modification d’une propriété. Les règles sont généralement utilisées pour maintenir la synchronisation entre les différents éléments du magasin. Par exemple, les règles sont utilisées pour s’assurer que le diagramme affiche l’état actuel du modèle.

Les règles sont définies pour chaque classe, ce qui vous permet de ne pas avoir de code qui enregistre la règle pour chaque objet. Pour plus d’informations, consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Stocker les événements

Le magasin de modélisation fournit un mécanisme d’événement que vous pouvez utiliser pour écouter des types spécifiques de modification dans le magasin, y compris l’ajout et la suppression d’éléments, les modifications apportées aux valeurs de propriété, etc. Les gestionnaires d’événements sont appelés après la fermeture de la transaction dans laquelle les modifications ont été apportées. En général, ces événements sont utilisés pour mettre à jour les ressources en dehors du magasin.

### <a name="net-events"></a>Événements .NET

Vous pouvez vous abonner à certains événements sur les formes. Par exemple, vous pouvez écouter les clics de souris sur une forme. Vous devez écrire du code qui s’abonne à l’événement pour chaque objet. Ce code peut être écrit dans une substitution de InitializeInstanceResources ().

Certains événements sont générés sur ShapeFields, qui sont utilisés pour dessiner des éléments décoratifs sur une forme. Pour obtenir un exemple, consultez [Comment : intercepter un clic sur une forme ou un Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Ces événements ne se produisent généralement pas dans une transaction. Vous devez créer une transaction si vous souhaitez apporter des modifications au magasin.
