---
title: Mise à jour des formes et des connecteurs pour refléter le modèle
description: Découvrez que dans un langage spécifique à un domaine dans Visual Studio, vous pouvez faire en sorte que l’apparence d’une forme reflète l’état du modèle sous-jacent.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6439a01de2a02361914ce227c43d903f1b24b405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388566"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Mettre à jour les formes et les connecteurs pour refléter le modèle

Dans un langage spécifique à un domaine dans Visual Studio, vous pouvez faire en sorte que l’apparence d’une forme reflète l’état du modèle sous-jacent.

Les exemples de code de cette rubrique doivent être ajoutés à un `.cs` fichier dans votre `Dsl` projet. Vous avez besoin de ces directives dans chaque fichier :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Définir les propriétés de mappage de forme pour contrôler la visibilité d’un élément décoratif

Vous pouvez contrôler la visibilité d’un élément décoratif sans écrire de code de programme, en configurant le mappage entre la forme et la classe de domaine dans la définition DSL. Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Exposer la couleur et le style d’une forme en tant que propriétés

Dans la définition DSL, cliquez avec le bouton droit sur la classe de forme, pointez sur **Ajouter exposé**, puis cliquez sur l’un des éléments tels que **couleur de remplissage**.

La forme a maintenant une propriété de domaine que vous pouvez définir dans le code de programme ou en tant qu’utilisateur. Par exemple, pour le définir dans le code de programme d’une commande ou d’une règle, vous pouvez écrire :

`shape.FillColor = System.Drawing.Color.Red;`

Si vous souhaitez que la variable de propriété soit uniquement sous contrôle du programme, et non par l’utilisateur, sélectionnez la nouvelle propriété de domaine comme **couleur de remplissage** dans le diagramme de définition DSL. Ensuite, dans la Fenêtre Propriétés, Set **peut être exploré** `false` ou défini comme **UI ReadOnly** to `true` .

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Définir des règles de modification pour définir la couleur, le style ou l’emplacement en fonction des propriétés de l’élément de modèle
 Vous pouvez définir des règles qui mettent à jour l’apparence de la forme en fonction des autres parties du modèle. Par exemple, vous pouvez définir une règle de modification sur un élément de modèle qui met à jour la couleur de sa forme en fonction des propriétés de l’élément de modèle. Pour plus d’informations sur les règles de modification, consultez [règles de propagation des modifications dans le modèle](../modeling/rules-propagate-changes-within-the-model.md).

 Vous devez utiliser des règles uniquement pour mettre à jour les propriétés qui sont conservées dans le magasin, car les règles ne sont pas appelées lors de l’exécution de la commande Annuler. Cela n’inclut pas certaines fonctionnalités graphiques telles que la taille et la visibilité d’une forme. Pour mettre à jour ces fonctionnalités d’une forme, consultez [mise à jour des fonctionnalités graphiques de non-stockage](#OnAssociatedProperty).

 L’exemple suivant suppose que vous avez exposé `FillColor` en tant que propriété de domaine comme décrit dans la section précédente.

```csharp
[RuleOn(typeof(ExampleElement))]
  class ExampleElementPropertyRule : ChangeRule
  {
    public override void ElementPropertyChanged(ElementPropertyChangedEventArgs e)
    {
      base.ElementPropertyChanged(e);
      ExampleElement element = e.ModelElement as ExampleElement;
      // The rule is called for every property that is updated.
      // Therefore, verify which property changed:
      if (e.DomainProperty.Id == ExampleElement.NameDomainPropertyId)
      {
        // There is usually only one shape:
        foreach (PresentationElement pel in PresentationViewsSubject.GetPresentation(element))
        {
          ExampleShape shape = pel as ExampleShape;
          // Replace this with a useful condition:
          shape.FillColor = element.Name.EndsWith("3")
                     ? System.Drawing.Color.Red : System.Drawing.Color.Green;
        }
      }
    }
  }
  // The rule must be registered:
  public partial class OnAssociatedPropertyExptDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(ExampleElementPropertyRule));
      // If you add more rules, list them here.
      return types.ToArray();
    }
  }
```

## <a name="use-onchildconfigured-to-initialize-a-shapes-properties"></a>Utiliser OnChildConfigured pour initialiser les propriétés d’une forme

Pour définir les propriétés d’une forme lorsqu’elle est créée pour la première fois, remplacez `OnChildConfigured()` dans une définition partielle de la classe Diagram. La classe Diagram est spécifiée dans votre définition DSL et le code généré se trouve dans **Dsl\Generated Code\Diagram.cs**. Exemple :

```csharp
partial class MyLanguageDiagram
{
  protected override void OnChildConfigured(ShapeElement child, bool childWasPlaced, bool createdDuringViewFixup)
  {
    base.OnChildConfigured(child, childWasPlaced, createdDuringViewFixup);
    ExampleShape shape = child as ExampleShape;
    if (shape != null)
    {
      if (!createdDuringViewFixup) return; // Ignore load from file.
      ExampleElement element = shape.ModelElement as ExampleElement;
      // Replace with a useful condition:
      shape.FillColor = element.Name.EndsWith("3")
          ? System.Drawing.Color.Red : System.Drawing.Color.Green;
    }
    // else deal with other types of shapes and connectors.
  }
}
```

Cette méthode peut être utilisée à la fois pour les propriétés de domaine et les fonctionnalités de non-stockage, telles que la taille de la forme.

## <a name="use-associatevaluewith-to-update-other-features-of-a-shape"></a><a name="OnAssociatedProperty"></a> Utiliser AssociateValueWith () pour mettre à jour d’autres fonctionnalités d’une forme

Pour certaines fonctionnalités d’une forme, par exemple si elle a une ombre, ou le style de flèche d’un connecteur, il n’existe aucune méthode intégrée pour exposer la fonctionnalité en tant que propriété de domaine.  Les modifications apportées à ces fonctionnalités ne sont pas sous le contrôle du système de transactions. Par conséquent, il n’est pas approprié de les mettre à jour à l’aide de règles, car les règles ne sont pas appelées lorsque l’utilisateur exécute la commande Annuler.

Au lieu de cela, vous pouvez mettre à jour ces fonctionnalités à l’aide de <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A> . Dans l’exemple suivant, le style de flèche d’un connecteur est contrôlé par la valeur d’une propriété de domaine dans la relation que le connecteur affiche :

```csharp
public partial class ArrowConnector // My connector class.
{
    /// <summary>
    /// Called whenever a registered property changes in the associated model element.
    /// </summary>
    /// <param name="e"></param>
    protected override void OnAssociatedPropertyChanged(VisualStudio.Modeling.Diagrams.PropertyChangedEventArgs e)
    {
      base.OnAssociatedPropertyChanged(e);
      // Can be called for any property change. Therefore,
      // Verify that this is the property we're interested in:
      if ("IsDirected".Equals(e.PropertyName))
      {
        if (e.NewValue.Equals(true))
        { // Update the shape's built-in Decorator feature:
          this.DecoratorTo = LinkDecorator.DecoratorEmptyArrow;
        }
        else
        {
          this.DecoratorTo = null; // No arrowhead.
        }
      }
    }

    // OnAssociatedPropertyChanged is called only for properties
    // that have been registered using AssociateValueWith().
    // InitializeResources is a convenient place to call this.
    // This method is invoked only once per class, even though
    // it is an instance method.
    protected override void InitializeResources(StyleSet classStyleSet)
    {
      base.InitializeResources(classStyleSet);
      AssociateValueWith(this.Store, Wire.IsDirectedDomainPropertyId);
      // Add other properties here.
    }
}
```

`AssociateValueWith()` doit être appelée une fois pour chaque propriété de domaine que vous souhaitez inscrire. Une fois appelé, toute modification apportée à la propriété spécifiée appellera `OnAssociatedPropertyChanged()` dans toutes les formes qui présentent l’élément de modèle de la propriété.

Il n’est pas nécessaire d’appeler `AssociateValueWith()` pour chaque instance. Bien que InitializeResources soit une méthode d’instance, il n’est appelé qu’une seule fois pour chaque classe Shape.
