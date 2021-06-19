---
title: 'Comment : intercepter un événement Click sur une forme ou un décorateur'
description: Découvrez comment intercepter un clic sur une forme ou un élément décoratif d’icône, et comment intercepter des clics, double-cliquer, faire glisser des éléments et d’autres gestes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, programming domain models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d2bcc16a6f2be70ae9ba0bfec0f3a24c94213dcf
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387162"
---
# <a name="how-to-intercept-a-click-on-a-shape-or-decorator"></a>Comment : intercepter un événement Click sur une forme ou un décorateur
Les procédures suivantes montrent comment intercepter un clic sur une forme ou un élément décoratif d’icône. Vous pouvez intercepter les clics, les double-clics, les glissements et autres gestes, et faire en sorte que l’élément réponde.

## <a name="to-intercept-clicks-on-shapes"></a>Pour intercepter des clics sur des formes
 Dans le projet DSL, dans un fichier de code distinct des fichiers de code générés, écrivez une définition de classe partielle pour la classe Shape. Remplacez `OnDoubleClick()` ou l’une des autres méthodes dont le nom commence par `On...` . Exemple :

```csharp
public partial class MyShape // change
  {
    public override void OnDoubleClick(DiagramPointEventArgs e)
    {
      base.OnDoubleClick(e);
      System.Windows.Forms.MessageBox.Show("Click");
      e.Handled = true;
  }  }
```

> [!NOTE]
> Affectez à la valeur `e.Handled` `true` , sauf si vous souhaitez que l’événement soit passé à la forme ou au diagramme conteneur.

## <a name="to-intercept-clicks-on-decorators"></a>Pour intercepter des clics sur des décorateurs
 Les éléments décoratifs d’image sont transportés sur une instance de la classe ImageField, qui a une méthode OnDoubleClick. Vous pouvez intercepter les clics si vous écrivez une sous-classe ImageField. Les champs sont configurés dans la méthode InitializeShapeFields. Par conséquent, vous devez modifier cette méthode pour instancier votre sous-classe au lieu du ImageField normal. La méthode InitializeShapeFields se trouve dans le code généré de la classe Shape. Vous pouvez substituer la classe Shape si vous définissez sa `Generates Double Derived` propriété comme décrit dans la procédure suivante.

 Bien que InitializeShapeFields soit une méthode d’instance, il est appelé une seule fois pour chaque classe. Par conséquent, il existe une seule instance de ClickableImageField pour chaque champ de chaque classe, et non une instance pour chaque forme dans le diagramme. Lorsque l’utilisateur double-clique sur une instance, vous devez identifier l’instance qui a été atteinte, comme le montre le code de l’exemple.

#### <a name="to-intercept-a-click-on-an-icon-decorator"></a>Pour intercepter un clic sur un élément décoratif d’icône

1. Ouvrez ou créez une solution DSL.

2. Choisissez ou créez une forme qui possède un élément décoratif d’icône et mappez-la à une classe de domaine.

3. Dans un fichier de code distinct des fichiers contenus dans le `GeneratedCode` dossier, créez la nouvelle sous-classe de ImageField :

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using System.Collections.Generic;
    using System.Linq;

    namespace Fabrikam.MyDsl { // Change to your namespace
    internal class ClickableImageField : ImageField
    {
      // You can also override OnClick and so on.
      public override void OnDoubleClick(DiagramPointEventArgs e)
      {
        base.OnDoubleClick(e);
        // Work out which instance was hit.
        MyShape shapeHit = e.HitDiagramItem.Shape as MyShape;
        if (shapeHit != null)
        {
          MyDomainClass element =
              shapeHit.ModelElement as MyDomainClass;
          System.Windows.Forms.MessageBox.Show(
             "Double click on shape for " + element.Name);
          // If we do not set Handled, the event will
          // be passed to the containing shape:
          e.Handled = true;
        }
      }

       public ClickableImageField(string fieldName)
         : base(fieldName)
       { }
    }
    ```

     Vous devez affecter la valeur true à Handled si vous ne souhaitez pas que l’événement soit passé à la forme conteneur.

4. Substituez la méthode InitializeShapeFields dans votre classe Shape en ajoutant la définition de classe partielle suivante.

    ```csharp
    public partial class MyShape // change
    {
     protected override void InitializeShapeFields
          (IList<ShapeField> shapeFields)
     {
      base.InitializeShapeFields(shapeFields);
      // You can see the above method in MyShapeBase
      // in the generated Shapes.cs
      // It has already added fields for the Icons.
      // So you will have to retrieve them and replace with your own.
      ShapeField unwantedField = shapeFields.First
          (field => field.Name == "IconDecorator1");
      shapeFields.Remove(unwantedField);

      // Now replicate the generated code from the base class
      // in Shape.cs, but with your own image constructor.
      ImageField field2 = new ClickableImageField("IconDecorator1");
      field2.DefaultImage = ImageHelper.GetImage(
        MyDslDomainModel.SingletonResourceManager
        .GetObject("MyShapeIconDecorator1DefaultImage"));
          shapeFields.Add(field2);
    }
    ```

1. Créez et exécutez la solution.

2. Double-cliquez sur l’icône d’une instance de la forme. Votre message de test doit s’afficher.

## <a name="intercepting-clicks-and-drags-on-compartmentshape-lists"></a>Interception des clics et des glissements sur des listes CompartmentShape
 L’exemple suivant permet aux utilisateurs de réorganiser les éléments dans une forme de compartiment en les faisant glisser. Pour exécuter ce code :

1. Créez une solution DSL à l’aide du modèle de solution **diagrammes de classes** .

    Vous pouvez également utiliser une solution de votre choix qui contient des formes de compartiments. Ce code part du principe qu’il existe une relation d’incorporation entre les éléments du modèle représenté par la forme et les éléments représentés dans les éléments de la liste des compartiments.

2. Définissez la propriété **générée double dérivée** de la forme de compartiment.

3. Ajoutez ce code dans un fichier dans le projet **DSL** .

4. Ajustez les noms de classe de domaine et de forme dans ce code pour qu’ils correspondent à votre propre DSL.

   En résumé, le code fonctionne comme suit. Dans cet exemple, `ClassShape` est le nom de la forme de compartiment.

- Un ensemble de gestionnaires d’événements de souris est attaché à chaque instance de compartiment lors de sa création.

- L' `ClassShape.MouseDown` événement stocke l’élément actuel.

- Lorsque la souris quitte l’élément actuel, une instance de MouseAction est créée, ce qui définit le curseur et capture la souris jusqu’à ce qu’elle soit libérée.

     Pour éviter toute interférence avec d’autres actions de la souris, telles que la sélection du texte d’un élément, le MouseAction n’est pas créé tant que la souris n’a pas quitté l’élément d’origine.

     Une alternative à la création d’un MouseAction serait simplement d’écouter MouseUp. Toutefois, cela ne fonctionnerait pas correctement si l’utilisateur relâche la souris après l’avoir glissée en dehors du compartiment. Le MouseAction est en mesure d’effectuer l’action appropriée, quel que soit l’endroit où la souris est relâchée.

- Lorsque la souris est relâchée, MouseAction. MouseUp réorganise l’ordre des liens entre les éléments de modèle.

- La modification de l’ordre des rôles déclenche une règle qui met à jour l’affichage. Ce comportement est déjà défini et aucun code supplémentaire n’est nécessaire.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Design;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Collections.Generic;
using System.Linq;

// This sample allows users to re-order items in a compartment shape by dragging.

// This example is built on the "Class Diagrams" solution template of VMSDK (DSL Tools).
// You will need to change the following domain class names to your own:
// ClassShape = a compartment shape
// ClassModelElement = the domain class displayed using a ClassShape
// This code assumes that the embedding relationships
// displayed in the compartments don't use inheritance
// (don't have base or derived domain relationships).

namespace Company.CompartmentDrag
{
 /// <summary>
 /// Manage the mouse while dragging a compartment item.
 /// </summary>
 public class CompartmentDragMouseAction : MouseAction
 {
  private ModelElement sourceChild;
  private ClassShape sourceShape;
  private RectangleD sourceCompartmentBounds;

  public CompartmentDragMouseAction(ModelElement sourceChildElement, ClassShape sourceParentShape, RectangleD bounds)
   : base (sourceParentShape.Diagram)
  {
   sourceChild = sourceChildElement;
   sourceShape = sourceParentShape;
   sourceCompartmentBounds = bounds; // For cursor.
  }

  /// <summary>
  /// Call back to the source shape to drop the dragged item.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   sourceShape.DoMouseUp(sourceChild, e);
   this.Cancel(e.DiagramClientView);
   e.Handled = true;
  }

  /// <summary>
  /// Ideally, this shouldn't happen. This action should only be active
  /// while the mouse is still pressed. However, it can happen if you
  /// move the mouse rapidly out of the source shape, let go, and then
  /// click somewhere else in the source shape.
  /// </summary>
  /// <param name="e"></param>
  protected override void OnMouseDown(DiagramMouseEventArgs e)
  {
   base.OnMouseDown(e);
   this.Cancel(e.DiagramClientView);
   e.Handled = false;
  }

  /// <summary>
  /// Display an appropriate cursor while the drag is in progress:
  /// Up-down arrow if we are inside the original compartment.
  /// No entry if we are elsewhere.
  /// </summary>
  /// <param name="currentCursor"></param>
  /// <param name="diagramClientView"></param>
  /// <param name="mousePosition"></param>
  /// <returns></returns>
  public override System.Windows.Forms.Cursor GetCursor(System.Windows.Forms.Cursor currentCursor, DiagramClientView diagramClientView, PointD mousePosition)
  {
   // If the cursor is inside the original compartment, show up-down cursor.
   return sourceCompartmentBounds.Contains(mousePosition)
    ? System.Windows.Forms.Cursors.SizeNS // Up-down arrow.
    : System.Windows.Forms.Cursors.No;
  }
 }

 /// <summary>
 /// Override some methods of the compartment shape.
 /// *** GenerateDoubleDerived must be set for this shape in DslDefinition.dsl. ****
 /// </summary>
 public partial class ClassShape
 {
  /// <summary>
  /// Model element that is being dragged.
  /// </summary>
  private static ClassModelElement dragStartElement = null;
  /// <summary>
  /// Absolute bounds of the compartment, used to set the cursor.
  /// </summary>
  private static RectangleD compartmentBounds;

  /// <summary>
  /// Attach mouse listeners to the compartments for the shape.
  /// This is called once per compartment shape.
  /// The base method creates the compartments for this shape.
  /// </summary>
  public override void EnsureCompartments()
  {
   base.EnsureCompartments();
   foreach (Compartment compartment in this.NestedChildShapes.OfType<Compartment>())
   {
    compartment.MouseDown += new DiagramMouseEventHandler(compartment_MouseDown);
    compartment.MouseUp += new DiagramMouseEventHandler(compartment_MouseUp);
    compartment.MouseMove += new DiagramMouseEventHandler(compartment_MouseMove);
   }
  }

  /// <summary>
  /// Remember which item the mouse was dragged from.
  /// We don't create an Action immediately, as this would inhibit the
  /// inline text editing feature. Instead, we just remember the details
  /// and will create an Action when/if the mouse moves off this list item.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseDown(object sender, DiagramMouseEventArgs e)
  {
   dragStartElement = e.HitDiagramItem.RepresentedElements
     .OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item,
  /// but still inside the compartment, create an Action
  /// to supervise the cursor and handle subsequent mouse events.
  /// Transfer the details of the initial mouse position to the Action.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseMove(object sender, DiagramMouseEventArgs e)
  {
   if (dragStartElement != null)
   {
    if (dragStartElement != e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault())
    {
     e.DiagramClientView.ActiveMouseAction = new CompartmentDragMouseAction(dragStartElement, this, compartmentBounds);
     dragStartElement = null;
    }
   }
  }

  /// <summary>
  /// User has released the mouse button.
  /// </summary>
  /// <param name="sender"></param>
  /// <param name="e"></param>
  void compartment_MouseUp(object sender, DiagramMouseEventArgs e)
  {
    dragStartElement = null;
  }

  /// <summary>
  /// Forget the source item if mouse up occurs outside the
  /// compartment.
  /// </summary>
  /// <param name="e"></param>
  public override void OnMouseUp(DiagramMouseEventArgs e)
  {
   base.OnMouseUp(e);
   dragStartElement = null;
  }

  /// <summary>
  /// Called by the Action when the user releases the mouse.
  /// If we are still on the same compartment but in a different list item,
  /// move the starting item to the position of the current one.
  /// </summary>
  /// <param name="dragFrom"></param>
  /// <param name="e"></param>
  public void DoMouseUp(ModelElement dragFrom, DiagramMouseEventArgs e)
  {
   // Original or "from" item:
   ClassModelElement dragFromElement = dragFrom as ClassModelElement;
   // Current or "to" item:
   ClassModelElement dragToElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   if (dragFromElement != null && dragToElement != null)
   {
    // Find the common parent model element, and the relationship links:
    ElementLink parentToLink = GetEmbeddingLink(dragToElement);
    ElementLink parentFromLink = GetEmbeddingLink(dragFromElement);
    if (parentToLink != parentFromLink && parentFromLink != null && parentToLink != null)
    {
     // Get the static relationship and role (= end of relationship):
     DomainRelationshipInfo relationshipFrom = parentFromLink.GetDomainRelationship();
     DomainRoleInfo parentFromRole = relationshipFrom.DomainRoles[0];
     // Get the node in which the element is embedded, usually the element displayed in the shape:
     ModelElement parentFrom = parentFromLink.LinkedElements[0];

     // Same again for the target:
     DomainRelationshipInfo relationshipTo = parentToLink.GetDomainRelationship();
     DomainRoleInfo parentToRole = relationshipTo.DomainRoles[0];
     ModelElement parentTo = parentToLink.LinkedElements[0];

     // Mouse went down and up in same parent and same compartment:
     if (parentTo == parentFrom && relationshipTo == relationshipFrom)
     {
      // Find index of target position:
      int newIndex = 0;
      var elementLinks = parentToRole.GetElementLinks(parentTo);
      foreach (ElementLink link in elementLinks)
      {
       if (link == parentToLink) { break; }
       newIndex++;
      }

      if (newIndex < elementLinks.Count)
      {
       using (Transaction t = parentFrom.Store.TransactionManager.BeginTransaction("Move list item"))
       {
        parentFromLink.MoveToIndex(parentFromRole, newIndex);
        t.Commit();
       }
      }
     }
    }
   }
  }

  /// <summary>
  /// Get the embedding link to this element.
  /// Assumes there is no inheritance between embedding relationships.
  /// (If there is, you need to make sure you've got the relationship
  /// that is represented in the shape compartment.)
  /// </summary>
  /// <param name="child"></param>
  /// <returns></returns>
  ElementLink GetEmbeddingLink(ClassModelElement child)
  {
   foreach (DomainRoleInfo role in child.GetDomainClass().AllEmbeddedByDomainRoles)
   {
    foreach (ElementLink link in role.OppositeDomainRole.GetElementLinks(child))
    {
     // Just the assume the first embedding link is the only one.
     // Not a valid assumption if one relationship is derived from another.
     return link;
    }
   }
   return null;
  }
 }
}
```

## <a name="see-also"></a>Voir aussi

- [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md)
- [Propriétés des décorateurs](../modeling/properties-of-decorators.md)
