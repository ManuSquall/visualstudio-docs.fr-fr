---
title: 'Comment : ajouter un gestionnaire glisser-déplacer'
description: Découvrez comment ajouter des gestionnaires pour les événements de glisser-déplacer à votre DSL afin que les utilisateurs puissent faire glisser des éléments sur votre diagramme à partir d’autres diagrammes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 79b58ee6ebd4db3ee9727bf59b260f281ba00275
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390409"
---
# <a name="how-to-add-a-drag-and-drop-handler"></a>Comment : ajouter un gestionnaire glisser-déplacer

Vous pouvez ajouter des gestionnaires pour les événements de glisser-déplacer à votre DSL, afin que les utilisateurs puissent faire glisser des éléments sur votre diagramme à partir d’autres diagrammes ou d’autres parties de Visual Studio. Vous pouvez aussi ajouter des gestionnaires pour des événements tels que les doubles clics. Ensemble, les gestionnaires de glisser-déplacer et de double-clic sont appelés *gestionnaires de mouvements*.

Cette rubrique traite des mouvements de type glisser-déplacer dont l'origine se situe sur d'autres diagrammes. Pour déplacer et copier des événements au sein d'un seul diagramme, pensez à l'autre solution qui consiste à définir une sous-classe d'`ElementOperations`. Pour plus d’informations, consultez [Personnalisation du comportement](../modeling/customizing-copy-behavior.md)de la copie. Vous avez aussi la possibilité de personnaliser la définition DSL.

## <a name="defining-gesture-handlers-by-overriding-shapeelement-methods"></a>Définition des gestionnaires de mouvements en remplaçant les méthodes ShapeElement

`OnDragDrop`, `OnDoubleClick` , `OnDragOver` et d’autres méthodes peuvent être substituées.

Ajoutez un nouveau fichier de code à votre projet DSL. Pour un gestionnaire de mouvements, vous devez généralement disposer au moins des `using` directives suivantes :

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using System.Linq;
```

Dans le nouveau fichier, définissez une classe partielle pour la forme ou la classe de diagramme qui doit répondre à l'opération de déplacement. Remplacez les méthodes suivantes :

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragOver%2A>-Cette méthode est appelée lorsque le pointeur de la souris entre dans la forme pendant une opération glisser. Votre méthode doit examiner l'élément que l'utilisateur déplace et définir la propriété Effect pour indiquer si l'utilisateur peut déposer l'élément sur cette forme. La propriété Effect détermine l'aspect du curseur pendant qu'il est sur la forme, ainsi que le fait de savoir si `OnDragDrop()` est appelé quand l'utilisateur relâche le bouton de la souris.

    ```csharp
    partial class MyShape // MyShape generated from DSL Definition.
    {
        public override void OnDragOver(DiagramDragEventArgs e)
        {
          base.OnDragOver(e);
          if (e.Effect == System.Windows.Forms.DragDropEffects.None
               && IsAcceptableDropItem(e)) // To be defined
          {
            e.Effect = System.Windows.Forms.DragDropEffects.Copy;
          }
        }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDragDrop%2A> -Cette méthode est appelée si l’utilisateur relâche le bouton de la souris alors que le pointeur de la souris se trouve sur cette forme ou ce diagramme, s’il a `OnDragOver(DiagramDragEventArgs e)` précédemment défini `e.Effect` sur une valeur autre que `None` .

    ```csharp
    public override void OnDragDrop(DiagramDragEventArgs e)
    {
          if (!IsAcceptableDropItem(e))
          {
            base.OnDragDrop(e);
          }
          else
          { // Process the dragged item, for example merging a copy into the diagram
            ProcessDragDropItem(e); // To be defined
          }
    }
    ```

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.OnDoubleClick%2A> -Cette méthode est appelée lorsque l’utilisateur double-clique sur la forme ou le diagramme.

     Pour plus d’informations, consultez [Comment : intercepter un clic sur une forme ou un Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Définissez `IsAcceptableDropItem(e)` pour déterminer si l'élément déplacé est acceptable et ProcessDragDropItem(e) pour mettre à jour votre modèle quand l'élément est déposé. Ces méthodes doivent d'abord extraire l'élément des arguments de l'événement. Pour plus d’informations sur la façon de procéder, consultez [Comment obtenir une référence à l’élément déplacé](#to-send-an-object-from-a-source-dsl).

## <a name="define-gesture-handlers-by-using-mef"></a>Définir des gestionnaires de mouvements à l’aide de MEF

Utilisez cette méthode si vous souhaitez que les développeurs tiers puissent définir leurs propres gestionnaires sur votre DSL. Les utilisateurs peuvent choisir d'installer les extensions tierces après avoir installé votre DSL.

MEF (Managed Extensibility Framework) vous permet de définir des composants qui peuvent être installés avec une configuration minimale. Pour plus d’informations, consultez [Vue d’ensemble de Managed Extensibility Framework](/dotnet/framework/mef/index).

### <a name="to-define-a-mef-gesture-handler"></a>Pour définir un gestionnaire d'événements MEF

1. Ajoutez à vos projets **DSL** et **DslPackage** les fichiers **MEFEXTENSION** décrits dans [étendre votre DSL à l’aide de MEF](../modeling/extend-your-dsl-by-using-mef.md).

2. Vous pouvez désormais définir un gestionnaire d'événements comme composant MEF :

    ```csharp
    // This attribute is defined in the generated file
    // DslPackage\MefExtension\DesignerExtensionMetaDataAttribute.cs:
    [MyDslGestureExtension]
    public class MyGestureHandlerClassName : IGestureExtension
    {
      /// <summary>
      /// Called to determine whether a drag onto the diagram can be accepted.
      /// </summary>
      /// <param name="diagramDragEventArgs">Contains a link to the item that is being dragged</param>
      /// <param name="targetMergeElement">The shape or connector that the mouse is over</param>
      /// <returns>True if the item can be accepted on the targetMergeElement.</returns>
      public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null) return false;
        if (target.IsAcceptableDropItem(diagramDragEventArgs)) return true;
        return false;
      }
      public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
      {
        MyShape target = targetMergeElement as MyShape;
        if (target == null || ! target.IsAcceptableDropItem(diagramDragEventArgs)) return;
        // Process the dragged item, for example merging a copy into the diagram:
        target.ProcessDragDropItem(diagramDragEventArgs);
     }
    ```

     Vous pouvez créer plusieurs composants de gestionnaire de mouvements, comme lorsque vous avez différents types d'objets déplacés.

3. Ajoutez les définitions de classe partielle pour la forme cible, les classes de connecteurs ou de diagrammes, et définissez les méthodes `IsAcceptableDropItem()` et `ProcessDragDropItem()`. Ces méthodes doivent commencer par extraire l'élément déplacé des arguments de l'événement. Pour plus d’informations, consultez [Comment obtenir une référence à l’élément déplacé](#to-send-an-object-from-a-source-dsl).

## <a name="how-to-decode-the-dragged-item"></a>Comment décoder l'élément déplacé

Les éléments peuvent être déplacés à partir de n'importe quelle fenêtre, du Bureau ou d'un DSL.

Lorsque l'utilisateur déplace un élément sur votre diagramme, ou d'une partie de votre diagramme vers une autre, les informations sur l'élément déplacé sont disponibles dans `DiagramDragEventArgs`. Comme l'opération de déplacement peut avoir démarré sur n'importe quel objet de l'écran, les données peuvent être disponibles dans l'un des nombreux formats existants. Votre code doit identifier les formats qu'il est capable de gérer.

Pour connaître les formats dans lesquels vos informations sur la source du déplacement sont disponibles, exécutez votre code en mode débogage, en définissant un point d'arrêt à l'entrée de `OnDragOver()` ou `CanDragDrop()`. Examinez les valeurs du paramètre `DiagramDragEventArgs`. Les informations sont fournies sous deux formes :

- <xref:System.Windows.Forms.IDataObject>  `Data` -Cette propriété comporte des versions sérialisées des objets source, généralement dans plusieurs formats. Ses fonctions les plus utiles sont les suivantes :

  - diagramEventArgs. Data. GetDataFormats ()-répertorie les formats dans lesquels vous pouvez décoder l’objet déplacé. Par exemple, si l'utilisateur déplace un fichier à partir du Bureau, les formats disponibles incluent le nom de fichier (« `FileNameW` »).

  - `diagramEventArgs.Data.GetData(format)` : Décode l’objet déplacé dans le format spécifié. Effectuez une conversion de type de l'objet dans le type approprié. Exemple :

    `string fileName = diagramEventArgs.Data.GetData("FileNameW") as string;`

    Vous pouvez aussi transmettre des objets tels que les références de bus de modèles à partir de la source et dans votre propre format personnalisé. Pour plus d’informations, consultez [Comment envoyer des références de bus de modèles dans un glisser-déplacer](#to-send-an-object-from-a-source-dsl).

- <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>`Prototype`-Utilisez cette propriété si vous souhaitez que les utilisateurs fassent glisser des éléments à partir d’un modèle DSL ou UML. Un prototype de groupe d'éléments contient un ou plusieurs objets, les liens et les valeurs de leurs propriétés. Il est également utilisé dans les opérations de collage et lorsque vous ajoutez un élément à partir de la boîte à outils. Dans un prototype, les objets et leurs types sont identifiés par un GUID. Par exemple, ce code permet à l'utilisateur de déplacer les éléments de classe à partir d'un diagramme UML ou de l'Explorateur de modèles UML :

    ```csharp
    private bool IsAcceptableDropItem(DiagramDragEventArgs e)
    {
      return e.Prototype != null && e.Prototype.RootProtoElements.Any(element =>
            element.DomainClassId.ToString()
            == "3866d10c-cc4e-438b-b46f-bb24380e1678"); // Accept UML class shapes.
     // Or, from another DSL: SourceNamespace.SourceShapeClass.DomainClassId
    }
    ```

     Pour accepter des formes UML, déterminez les GUID des classes de formes UML par expérimentation. N'oubliez qu'il existe généralement plusieurs types d'éléments sur un diagramme. Souvenez-vous aussi qu'un objet déplacé à partir d'un diagramme DSL ou UML est la forme, et non l'élément de modèle.

`DiagramDragEventArgs` possède également des propriétés qui indiquent la position actuelle du pointeur de la souris et si l’utilisateur appuie sur les touches CTRL, ALT ou Maj.

## <a name="how-to-get-the-original-of-a-dragged-element"></a>Comment obtenir l'original d'un élément déplacé

Si l'élément déplacé est un élément DSL, vous pouvez ouvrir le modèle source et accéder à l'élément.

Les propriétés `Data` et `Prototype` des arguments de l'événement contiennent uniquement une référence à la forme déplacée. Généralement, si vous voulez créer un objet dans le DSL cible dérivé du prototype d'une quelconque façon, vous devez obtenir l'accès à l'original, par exemple en lisant le contenu du fichier ou en accédant à l'élément de modèle représenté par une forme. Vous pouvez à cette fin utiliser l'extension Visual Studio Model Bus.

### <a name="to-prepare-a-dsl-project-for-model-bus"></a>Pour préparer un projet DSL pour le bus de modèles

Rendre le DSL source accessible par Visual Studio Model bus :

1. Ouvrez le fichier de définition DSL du DSL source dans le concepteur DSL. Cliquez avec le bouton droit sur l’aire de conception, puis cliquez sur **activer ModelBus**. Dans la boîte de dialogue, choisissez l'une ou l'autre des options.  Cliquez sur **OK**. Un nouveau projet « ModelBus » vient s'ajouter à la solution DSL.

2. Cliquez sur **transformer tous les modèles** et reconstruisez la solution.

### <a name="to-send-an-object-from-a-source-dsl"></a>Pour envoyer un objet à partir d'un DSL source

1. Dans votre sous-classe ElementOperations, remplacez `Copy()` de telle sorte qu'elle encode une MBR (Model Bus Reference) en IDataObject. Cette méthode est appelée quand l'utilisateur commence à exécuter un déplacement depuis le diagramme source. La MBR encodée est alors disponible dans l'IDataObject quand l'utilisateur dépose l'élément dans le diagramme cible.

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Shell;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Integration;
    using Microsoft.VisualStudio.Modeling.Integration.Shell;
    using System.Drawing; // PointF
    using  System.Collections.Generic; // ICollection
    using System.Windows.Forms; // for IDataObject
    ...
    public class MyElementOperations : DesignSurfaceElementOperations
    {
        public override void Copy(System.Windows.Forms.IDataObject data, System.Collections.Generic.ICollection<ModelElement> elements, ClosureType closureType, System.Drawing.PointF sourcePosition)
        {
          base.Copy(data, elements, closureType, sourcePosition);

          // Get the ModelBus service:
          IModelBus modelBus =
              this.Store.GetService(typeof(SModelBus)) as IModelBus;
          DocData docData = ((VSDiagramView)this.Diagram.ActiveDiagramView).DocData;
          string modelFile = docData.FileName;
          // Get an adapterManager for the target DSL:
          ModelBusAdapterManager manager =
              (modelBus.FindAdapterManagers(modelFile).First());
          ModelBusReference modelReference = manager.CreateReference(modelFile);
          ModelBusReference elementReference = null;
          using (ModelBusAdapter adapter = modelBus.CreateAdapter(modelReference))
          {
            elementReference = adapter.GetElementReference(elements.First());
          }

          data.SetData("ModelBusReference", elementReference);
        }
    ...}
    ```

### <a name="to-receive-a-model-bus-reference-from-a-dsl-in-a-target-dsl-or-uml-project"></a>Pour recevoir une MBR à partir d'un DSL dans un projet DSL ou UML cible

1. Dans le projet DSL cible, ajoutez les références de projet aux projets suivants :

    - Le projet DSL source.

    - Le projet ModelBus source.

2. Dans le fichier de code du gestionnaire de mouvements, ajoutez les références d'espaces de noms suivantes :

    ```csharp
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Modeling.Integration;
    using SourceDslNamespace;
    using SourceDslNamespace.ModelBusAdapters;
    ```

3. L'exemple suivant illustre comment accéder à l'élément de modèle source :

    ```csharp
    partial class MyTargetShape // or diagram or connector
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
        // Verify that we're being passed an Object Shape.
        ElementGroupPrototype prototype = diagramDragEventArgs.Prototype;
        if (prototype == null) return;
        if (Company.InstanceDiagrams.ObjectShape.DomainClassId
          != prototype.RootProtoElements.First().DomainClassId)
          return;
        // - This is an ObjectShape.
        // - We need to access the originating Store, find the shape, and get its object.

        IModelBus modelBus = targetDropElement.Store.GetService(typeof(SModelBus)) as IModelBus;

        // Unpack the MBR that was packed in Copy:
        ModelBusReference reference = diagramDragEventArgs.Data.GetData("ModelBusReference") as ModelBusReference;
        using (SourceDslAdapter adapter = modelBus.CreateAdapter(reference) as SourceDslAdapter)
        {
          using (ILinkedUndoTransaction t = LinkedUndoContext.BeginTransaction("doing things"))
          {
            // Quickest way to get the shape from the MBR:
            ObjectShape firstShape = adapter.ResolveElementReference<ObjectShape>(reference);

            // But actually there might be several shapes - so get them from the prototype instead:
            IElementDirectory remoteDirectory = adapter.Store.ElementDirectory;
            foreach (Guid shapeGuid in prototype.SourceRootElementIds)
            {
              PresentationElement pe = remoteDirectory.FindElement(shapeGuid) as PresentationElement;
              if (pe == null) continue;
              SourceElement instance = pe.ModelElement as SourceElement;
              if (instance == null) continue;

              // Do something with the object:
          instance...
            }
            t.Commit();
          }
        }
    }
    ```

### <a name="to-accept-an-element-sourced-from-a-uml-model"></a>Pour accepter un élément dont la source est un modèle UML

- L'exemple de code suivant accepte un objet déposé à partir d'un diagramme UML.

    ```csharp
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Diagrams;
    using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
    using Microsoft.VisualStudio.Uml.Classes;
    using System;
    using System.ComponentModel.Composition;
    using System.Linq;
    ...
    partial class TargetShape
    {
      internal void ProcessDragDropItem(DiagramDragEventArgs diagramDragEventArgs)
      {
            EnvDTE.DTE dte = this.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
            // Find the UML project
            foreach (EnvDTE.Project project in dte.Solution.Projects)
            {
              IModelingProject modelingProject = project as IModelingProject;
              if (modelingProject == null) continue; // not a modeling project
              IModelStore store = modelingProject.Store;
              if (store == null) return;

              foreach (IDiagram dd in store.Diagrams())
              {
                  // Get Modeling.Diagram that implements UML.IDiagram:
                  Diagram diagram = dd.GetObject<Diagram>();

                  foreach (Guid elementId in e.Prototype.SourceRootElementIds)
                  {
                    ShapeElement shape = diagram.Partition.ElementDirectory.FindElement(elementId) as ShapeElement;
                    if (shape == null) continue;
                    // This example assumes the shape is a UML class:
                    IClass classElement = shape.ModelElement as IClass;
                    if (classElement == null) continue;

                    // Now do something with the UML class element ...
                  }
            }
          break; // don't try any more projects
    }  }  }
    ```

## <a name="using-mouse-actions-dragging-compartment-items"></a>Utilisation d'actions de la souris : faire glisser des éléments de compartiment

Vous pouvez écrire un gestionnaire qui intercepte les actions de la souris sur les champs d’une forme. L’exemple suivant permet à l’utilisateur de réorganiser les éléments dans un compartiment en les faisant glisser avec la souris.

Pour générer cet exemple, créez une solution à l’aide du modèle de solution **diagrammes de classes** . Ajoutez un fichier de code et ajoutez le code suivant. Adaptez l'espace de noms pour qu'il soit identique au vôtre.

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
// This code assumes that the embedding relationships displayed in the compartments
// don't use inheritance (don't have base or derived domain relationships).

namespace Company.CompartmentDrag  // EDIT.
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
  /// click somewhere else in the source shape. Yuk.
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
   dragStartElement = e.HitDiagramItem.RepresentedElements.OfType<ClassModelElement>().FirstOrDefault();
   compartmentBounds = e.HitDiagramItem.Shape.AbsoluteBoundingBox;
  }

  /// <summary>
  /// When the mouse moves away from the initial list item, but still inside the compartment,
  /// create an Action to supervise the cursor and handle subsequent mouse events.
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

- [Personnalisation du comportement de la copie](../modeling/customizing-copy-behavior.md)
- [Déploiement de solutions de langage spécifique à un domaine](msi-and-vsix-deployment-of-a-dsl.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
