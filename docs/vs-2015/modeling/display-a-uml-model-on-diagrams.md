---
title: Afficher un modèle UML sur des diagrammes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: adf1f1f2-2ad9-4ade-82de-c6a5194ab471
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06a22161068dd7604fe7bb4153e322c0954b89d2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533016"
---
# <a name="display-a-uml-model-on-diagrams"></a>Afficher un modèle UML sur des diagrammes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le code de programme d'une extension de Visual Studio, vous pouvez contrôler comment les éléments de modèle sont affichés dans les diagrammes. Pour connaître les versions de Visual Studio qui prennent en charge les modèles UML, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

Dans cette rubrique :
- [Pour afficher un élément dans un diagramme](#Display)

- [Accès aux formes qui représentent un élément](#GetShapes)

- [Déplacement et redimensionnement des formes](#Moving)

- [Pour supprimer une forme d'un diagramme](#Removing)

- [Ouverture et création de diagrammes](#Opening)

- [Exemple : commande pour aligner des formes](#AlignCommand)

## <a name="to-display-an-element-on-a-diagram"></a><a name="Display"></a>Pour afficher un élément dans un diagramme
 Quand vous créez un élément tel qu'un cas d'usage ou une action, l'utilisateur peut le voir dans l'Explorateur de modèles UML, mais il n'apparaît pas toujours automatiquement dans un diagramme. Dans certains cas, vous devez écrire du code pour l'afficher. Le tableau suivant récapitule les alternatives.

|Type d'élément|Par exemple|Pour l'afficher, votre code doit|
|---------------------|-----------------|-------------------------------------|
|Classifieur|`Class`<br /><br /> `Component`<br /><br /> `Actor`<br /><br /> `Use Case`|Créer des formes associées dans les diagrammes spécifiés. Vous pouvez créer une quantité quelconque de formes pour chaque classifieur.<br /><br /> `diagram.Display<modelElementType>`<br /><br /> `(modelElement, parentShape,`<br /><br /> `xPosition , yPosition);`<br /><br /> Affectez la valeur `parentShape` à `null` pour une forme au niveau supérieur du diagramme.<br /><br /> Pour afficher une forme dans une autre :<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `useCaseDiagram.Display`<br /><br /> `(useCase,`<br /><br /> `subsystemShape,`<br /><br /> `subsystemShape.XPosition + 5,`<br /><br /> `subsystemShape.YPosition + 5);`**Remarque :**  Si vous effectuez l’affichage à l’intérieur d’une transaction **ILinkedUndo** , la méthode retourne parfois non `IShape` . Mais la forme est créée correctement et est accessible à l'aide de `IElement.Shapes().`.|
|Enfant de classifieur|Attribut, Opération,<br /><br /> Partie, Port|Automatique : aucun code nécessaire.<br /><br /> Il est affiché dans le cadre du parent.|
|Comportement|Interaction (séquence),<br /><br /> Activité|Lier le comportement à un diagramme approprié.<br /><br /> Chaque comportement peut être lié au plus à un diagramme à la fois.<br /><br /> Par exemple :<br /><br /> `sequenceDiagram.Bind(interaction);`<br /><br /> `activityDiagram.Bind(activity);`|
|Enfant de comportement|Lignes de vie, messages, actions, nœuds d'objets|Automatique : aucun code nécessaire.<br /><br /> Il est affiché si le parent est lié à un diagramme.|
|Relation|Association, généralisation, flux, dépendance|Automatique : aucun code nécessaire.<br /><br /> Il est affiché dans chaque diagramme où les deux extrémités sont affichées.|

## <a name="accessing-the-shapes-that-represent-an-element"></a><a name="GetShapes"></a>Accès aux formes qui représentent un élément
 La forme qui représente un élément appartient aux types :

 `IShape`

 `IShape<` *ElementType* `>`

 où *ElementType* est un type de l’élément de modèle tel que `IClass` ou `IUseCase` .

|Syntaxe|Description|
|-|-|
|`anElement.Shapes ()`|Tous les `IShapes` qui représentent cet élément dans les diagrammes ouverts.|
|`anElement.Shapes(aDiagram)`|Tous les `IShapes` qui représentent cet élément dans un diagramme particulier.|
|`anIShape.GetElement()`|Le `IElement` que la forme représente. Vous le convertissez normalement en une sous-classe d'IElement.|
|`anIShape.Diagram`|Le `IDiagram` qui contient la forme.|
|`anIShape.ParentShape`|La forme qui contient `anIShape`. Par exemple, une forme de port est contenue dans une forme de composant.|
|`anIShape.ChildShapes`|Formes contenues dans un `IShape` ou `IDiagram`.|
|`anIShape.GetChildShapes<IUseCase>()`|Les formes contenues dans un `IShape` ou `IDiagram` qui représentent des éléments du type spécifié, tels que `IUseCase`.|
|`IShape iShape = ...;`<br /><br /> `IShape<IClass> classShape = iShape.ToIShape<IClass>();`<br /><br /> `IClass aClass = classShape.Element;`|Effectuez un cast d'un `IShape` générique en un `IShape<IElement>` fortement typé.|
|`IShape<IClassifier> classifierShape;`<br /><br /> `IShape<IUseCase> usecaseShape =`<br /><br /> `classifierShape.ToIShape<IUseCase>();`|Effectuez un cast de forme d'un type de forme paramétrable vers un autre.|

## <a name="moving-and-resizing-shapes"></a><a name="Moving"></a>Déplacer et redimensionner des formes

|Syntaxe|Description|
|-|-|
|`anIShape.Move(x, y, [width], [height])`|Déplacez ou redimensionnez une forme.|
|`IDiagram.EnsureVisible( IEnumerable<IShape> shapes, bool zoomToFit = false)`|Activez la fenêtre et faites défiler le diagramme pour que toutes les formes données soient visibles. Les formes doivent toutes être dans le diagramme. Si `zoomToFit` est true, le diagramme est redimensionné si nécessaire pour que toutes les formes soient visibles.|

 Pour obtenir un exemple, consultez [définition d’une commande d’alignement](#AlignCommand).

## <a name="to-remove-a-shape-from-a-diagram"></a><a name="Removing"></a>Pour supprimer une forme d’un diagramme
 Vous pouvez supprimer des formes de certains types d'éléments sans supprimer l'élément.

|Élément de modèle|Pour supprimer la forme|
|-------------------|-------------------------|
|Un classifieur : classe, interface, énumération, acteur, cas d'usage ou composant|`shape.Delete();`|
|Un comportement : interaction ou activité|Vous pouvez supprimer le diagramme du projet. Utilisez `IDiagram.FileName` pour obtenir le chemin d'accès.<br /><br /> Cela ne supprime pas le comportement du modèle.|
|Toute autre forme|Vous ne pouvez pas supprimer explicitement d'autres formes d'un diagramme. La forme disparaît automatiquement si l'élément est supprimé du modèle ou si la forme parente est supprimée du diagramme.|

## <a name="opening-and-creating-diagrams"></a><a name="Opening"></a>Ouverture et création de diagrammes

### <a name="to-access-the-users-current-diagram-from-a-command-or-gesture-extension"></a>Pour accéder au diagramme actuel de l'utilisateur à partir d'une commande ou d'une extension de mouvement
 Déclarez cette propriété importée dans votre classe :

 `[Import]`

 `IDiagramContext Context { get; set; }`

 Dans une méthode, accédez au diagramme :

 `IClassDiagram classDiagram =`

 `Context.CurrentDiagram as IClassDiagram;`

> [!NOTE]
> Une instance de `IDiagram` (et ses sous-types tels que `IClassDiagram`) est valide uniquement dans la commande que vous traitez. Nous vous déconseillons de conserver un objet `IDiagram` dans une variable qui persiste pendant que le contrôle est retourné à l'utilisateur.

 Pour plus d’informations, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

### <a name="to-obtain-a-list-of-open-diagrams"></a>Pour obtenir une liste des diagrammes ouverts
 Une liste des diagrammes qui sont ouverts actuellement dans le projet :

```
Context.CurrentDiagram.ModelStore.Diagrams()
```

## <a name="to-access-the-diagrams-in-a-project"></a>Pour accéder aux diagrammes dans un projet
 Vous pouvez utiliser l'API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pour ouvrir et créer des projets de modélisation et des diagrammes.

 Remarquez le cast de `EnvDTE.ProjectItem` en `IDiagramContext`.

```

      using EnvDTE; // Visual Studio API
...
[Import]
public IServiceProvider ServiceProvider { get; set; }
...
// Get Visual Studio API
DTE dte = ServiceProvider.GetService(typeof(DTE)) as DTE;
// Get current Visual Studio project
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;
// Open and process every diagram in the project.
foreach (ProjectItem item in project.ProjectItems)
{
  // Cast ProjectItem to IDiagramContext
  IDiagramContext context = item as IDiagramContext;
  if (context == null)
  {
     // This is not a diagram file.
     continue;
  }
  // Open the file and give the window the focus.
  if (!item.IsOpen)
  {
      item.Open().Activate();
  }
  // Get the diagram.
  IDiagram diagram = context.CurrentDiagram;
  // Deal with specific diagram types.
  ISequenceDiagram seqDiagram = diagram as ISequenceDiagram;
  if (seqDiagram != null)
  { ... } } }
```

 Les instances de `IDiagram` et ses sous-types ne sont pas valides une fois le contrôle retourné à [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Vous pouvez également obtenir le magasin de modèles à partir d'un projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

```

      Project project = ...;
IModelStore modelStore = (project as IModelingProject).Store;
```

## <a name="example-command-for-aligning-shapes"></a><a name="AlignCommand"></a>Exemple : commande pour aligner des formes
 Le code suivant implémente une commande de menu qui aligne correctement les formes. Vous devez d'abord placer plusieurs formes avec un alignement approximatif, verticalement ou horizontalement. Vous pouvez ensuite utiliser la commande Aligner pour aligner leur centre.

 Pour rendre la commande accessible, ajoutez ce code à un projet de commande de menu, puis déployez l'extension résultante pour vos utilisateurs. Pour plus d’informations, consultez [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace AlignCommand
{
  // Implements a command to align shapes in a UML class diagram.
  // The user first selects shapes that are roughly aligned either vertically or horizontally.
  // This command will straighten them up.

  // Place this file in a menu command extension project.
  // See https://msdn.microsoft.com/library/ee329481.aspx

  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension] // TODO: Add other diagram types if needed
  class CommandExtension : ICommandExtension
  {
    /// <summary>
    /// See https://msdn.microsoft.com/library/ee329481.aspx
    /// </summary>
    [Import]
    IDiagramContext context { get; set; }

    /// <summary>
    /// Transaction context.
    /// See https://msdn.microsoft.com/library/ee330926.aspx
    /// </summary>
    [Import]
    ILinkedUndoContext linkedUndo { get; set; }

    /// <summary>
    /// Called when the user selects the command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      Align(context.CurrentDiagram.SelectedShapes);
    }

    /// <summary>
    /// Called when the user right-clicks on the diagram.
    /// Determines whether the command is enabled.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      IEnumerable<IShape> currentSelection = context.CurrentDiagram.SelectedShapes;
      // Make it visible if there are shapes selected:
      command.Visible = currentSelection.Count() > 0 && !(currentSelection.FirstOrDefault() is IDiagram);

      // Make it enabled if there are two or more shapes that are roughly in line:
      command.Enabled = currentSelection.Count() > 1
        && (HorizontalAlignCenter(currentSelection) > 0.0
        || VerticalAlignCenter(currentSelection) > 0.0);

    }

    /// <summary>
    /// Title of the menu command.
    /// </summary>
    public string Text
    {
      get { return "Align Shapes"; }
    }

    /// <summary>
    /// Find a horizontal line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double HorizontalAlignCenter(IEnumerable<IShape> shapes)
    {
      double Y = -1.0;
      double top = 0.0, bottom = shapes.First().Bottom();
      foreach (IShape shape in shapes)
      {
        top = Math.Max(top, shape.Top());
        bottom = Math.Min(bottom, shape.Bottom());
      }
      if (bottom > top) Y = (bottom + top) / 2.0;
      return Y;
    }

    /// <summary>
    /// Find a vertical line that goes through a list of shapes.
    /// </summary>
    /// <param name="shapes"></param>
    /// <returns></returns>
    private static double VerticalAlignCenter(IEnumerable<IShape> shapes)
    {
      double X = -1.0;
      double left = 0.0, right = shapes.First().Right();
      foreach (IShape shape in shapes)
      {
        left = Math.Max(left, shape.Left());
        right = Math.Min(right, shape.Right());
      }
      if (right > left) X = (right + left) / 2.0;
      return X;
    }

    /// <summary>
    /// Line up those shapes that are roughly aligned.
    /// </summary>
    /// <param name="shapes"></param>
    private void Align(IEnumerable<IShape> shapes)
    {
      if (shapes.Count() > 1)
      {
        // The shapes must all overlap either horizontally or vertically.
        // Find a horizontal line that is covered by all the shapes:
        double Y = HorizontalAlignCenter(shapes);
        if (Y > 0.0) // Negative if they don't overlap.
        {
          // Adjust all the shape positions in one transaction:
          using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
          {
            foreach (IShape shape in shapes)
            {
              shape.AlignYCenter(Y);
            }
            t.Commit();
          }
        }
        else
        {
          // Find a vertical line that is covered by all the shapes:
          double X = VerticalAlignCenter(shapes);
          if (X > 0.0) // Negative if they don't overlap.
          {
            // Adjust all the shape positions in one transaction:
            using (ILinkedUndoTransaction t = linkedUndo.BeginTransaction("align"))
            {
              foreach (IShape shape in shapes)
              {
                shape.AlignXCenter(X);
              }
              t.Commit();
            }
          }
        }
      }
    }
  }

  /// <summary>
  /// Convenience extensions for IShape.
  /// </summary>
  public static class IShapeExtension
  {
    public static double Bottom(this IShape shape)
    {
      return shape.YPosition + shape.Height;
    }

    public static double Top(this IShape shape)
    {
      return shape.YPosition;
    }

    public static double Left(this IShape shape)
    {
      return shape.XPosition;
    }

    public static double Right(this IShape shape)
    {
      return shape.XPosition + shape.Width;
    }

    public static void AlignYCenter(this IShape shape, double Y)
    {
      shape.Move(shape.XPosition, Y - shape.YCenter());
    }

    public static void AlignXCenter(this IShape shape, double X)
    {
      shape.Move(X - shape.XCenter(), shape.YPosition);
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double YCenter(this IShape shape)
    {
        return shape.Height / 2.0;
    }

    /// <summary>
    /// We can adjust what bit of the shape we want to be aligned.
    /// The default is the center of the shape.
    /// </summary>
    /// <param name="shape"></param>
    /// <returns></returns>
    public static double XCenter(this IShape shape)
    {
        return shape.Width / 2.0;
    }
  }
}

```

## <a name="see-also"></a>Voir aussi
 [Étendre des modèles et des diagrammes UML](../modeling/extend-uml-models-and-diagrams.md) [naviguer dans le modèle UML](../modeling/navigate-the-uml-model.md)
 