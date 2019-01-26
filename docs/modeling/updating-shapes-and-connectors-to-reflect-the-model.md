---
title: Mise à jour des formes et des connecteurs pour refléter le modèle
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 5fa9861d081fba318805170163d9287ac113fbd0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54997583"
---
# <a name="update-shapes-and-connectors-to-reflect-the-model"></a>Mettre à jour les formes et les connecteurs pour refléter le modèle

Dans un langage spécifique à un domaine dans Visual Studio, vous pouvez rendre l’apparence d’une forme reflètent l’état du modèle sous-jacent.

Les exemples de code dans cette rubrique doivent être ajoutés à un `.cs` de fichiers dans votre `Dsl` projet. Vous avez besoin de ces instructions dans chaque fichier :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
```

## <a name="set-shape-map-properties-to-control-the-visibility-of-a-decorator"></a>Définir les propriétés de mappage de forme pour contrôler la visibilité d’un décorateur

Vous pouvez contrôler la visibilité d’un décorateur sans écrire de code de programme, en configurant le mappage entre la forme et de la classe de domaine dans la définition DSL. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).

## <a name="expose-the-color-and-style-of-a-shape-as-properties"></a>Exposer la couleur et le style d’une forme en tant que propriétés

Dans la définition DSL, la classe de forme avec le bouton droit, pointez sur **ajouter les objets exposés**, puis cliquez sur l’un des éléments tels que **couleur de remplissage**.

La forme a maintenant une propriété de domaine que vous pouvez définir dans le code de programme ou en tant qu’utilisateur. Par exemple, pour la définir dans le code de programme d’une commande ou une règle, vous pouvez écrire :

`shape.FillColor = System.Drawing.Color.Red;`

Si vous souhaitez rendre la variable de propriété uniquement sous le contrôle du programme et non par l’utilisateur, sélectionnez la nouvelle propriété de domaine comme **couleur de remplissage** dans le diagramme de définition DSL. Ensuite, dans la fenêtre Propriétés, définissez **Is Browsable** à `false` ou définir **en lecture seule de l’interface utilisateur est** à `true`.

## <a name="define-change-rules-to-make-color-style-or-location-depend-on-model-element-properties"></a>Définir des règles de modification pour rendre la couleur, style ou emplacement dépendent des propriétés d’élément de modèle
 Vous pouvez définir des règles qui mettent à jour l’apparence de la forme dépend des autres parties du modèle. Par exemple, vous pouvez définir une règle de modification sur un élément de modèle qui met à jour de la couleur de sa forme dépendante sur les propriétés de l’élément de modèle. Pour plus d’informations sur les règles de modification, consultez [propager les modifications dans le modèle de règles](../modeling/rules-propagate-changes-within-the-model.md).

 Vous devez utiliser des règles uniquement pour mettre à jour les propriétés qui sont conservées dans le Store, étant donné que les règles ne sont pas appelés lorsque la commande d’annulation est effectuée. Cela n’inclut pas certaines fonctionnalités graphiques telles que la taille et la visibilité d’une forme. Pour mettre à jour de ces fonctionnalités d’une forme, consultez [fonctionnalités de la mise à jour le graphique de Non-Store](#OnAssociatedProperty).

 L’exemple suivant suppose que vous avez exposé `FillColor` comme une propriété de domaine comme décrit dans la section précédente.

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

Pour définir les propriétés d’une forme lors de sa création, le remplacement `OnChildConfigured()` dans une définition partielle de votre classe de diagramme. La classe de schéma est spécifiée dans votre définition DSL, et le code généré se trouve dans **Dsl\Generated Code\Diagram.cs**. Exemple :

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

Cette méthode peut être utilisée à la fois pour les propriétés de domaine et non-magasin de fonctionnalités, telles que la taille de la forme.

## <a name="OnAssociatedProperty"></a> Utiliser AssociateValueWith() pour mettre à jour d’autres fonctionnalités d’une forme

Pour certaines fonctionnalités d’une forme, telles que s’il a une ombre, ou le style de flèche d’un connecteur, il n’existe aucune méthode intégrée d’exposer la fonctionnalité comme une propriété de domaine.  Modifications apportées à ces fonctionnalités ne sont pas sous le contrôle du système de transaction. Par conséquent, il n’est pas approprié de les mettre à jour à l’aide de règles, étant donné que les règles ne sont pas appelés lorsque l’utilisateur exécute la commande Annuler.

Au lieu de cela, vous pouvez mettre à jour des fonctionnalités à l’aide de <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnAssociatedPropertyChanged%2A>. Dans l’exemple suivant, le style de flèche d’un connecteur est contrôlé par une valeur d’une propriété de domaine dans la relation qui affiche le connecteur :

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

`AssociateValueWith()` doit être appelée une fois pour chaque propriété de domaine que vous souhaitez inscrire. Une fois qu’il a été appelée, toutes les modifications à la propriété spécifiée appellera `OnAssociatedPropertyChanged()` dans toutes les formes qui présentent l’élément de modèle de la propriété.

Il n’est pas nécessaire d’appeler `AssociateValueWith()` pour chaque instance. Bien que InitializeResources est une méthode d’instance, elle est appelée qu’une seule fois pour chaque classe de forme.
