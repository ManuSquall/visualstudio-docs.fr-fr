---
title: Définir un gestionnaire de mouvements sur un diagramme de modélisation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, double-click
- UML - extending, drag and drop
ms.assetid: e5e1d70a-3539-4321-a3b1-89e86e4d6430
caps.latest.revision: 36
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67946ffb674a7f4a2346229b958ba8316d6ff919
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850494"
---
# <a name="define-a-gesture-handler-on-a-modeling-diagram"></a>Définir un gestionnaire de mouvements sur un diagramme de modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio,vous pouvez définir des commandes qui sont exécutées quand l’utilisateur double-clique sur des éléments ou les fait glisser sur un diagramme UML. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio ([VSIX](https://msdn.microsoft.com/library/dd393694(VS.100).aspx)) et les distribuer à d’autres utilisateurs de Visual Studio.

 Si un comportement intégré existe déjà pour le type de diagramme et le type d’élément que vous souhaitez faire glisser, il se peut que vous ne puissiez pas effectuer d’ajouts à ce comportement ni le substituer.

## <a name="requirements"></a>Configuration requise pour
 Consultez [Spécifications](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="creating-a-gesture-handler"></a>Création d’un gestionnaire de mouvements
 Pour définir un gestionnaire de mouvements pour un concepteur UML, vous devez créer une classe qui définit le comportement du gestionnaire de mouvements, puis incorporer cette classe dans une extension d’intégration Visual Studio (VSIX). Cette dernière joue le rôle d’un conteneur capable d’installer le gestionnaire. Deux autres méthodes permettent de définir un gestionnaire de mouvements :

- **Créer un gestionnaire de mouvements dans son propre VSIX à l’aide d’un modèle de projet.** . Il s’agit de la méthode la plus rapide. Choisissez cette méthode si vous ne souhaitez pas combiner votre gestionnaire avec d’autres types d’extensions, telles que les extensions de validation, les éléments de boîte à outils personnalisés ou les commandes de menu.

- **Créer des gestionnaires de mouvements et des projets VSIX distincts.** Adoptez cette approche si vous souhaitez combiner plusieurs types d’extensions dans la même extension VSIX. Par exemple, si votre gestionnaire de mouvements prévoit que le modèle observe des contraintes spécifiques, vous pouvez l’incorporer au même VSIX en tant que méthode de validation.

#### <a name="to-create-a-gesture-handler-in-its-own-vsix"></a>Pour créer un gestionnaire de mouvements dans son propre VSIX

1. Dans la boîte de dialogue **Nouveau projet** , sous **Projets de modélisation**, cliquez sur **Extension de mouvement**.

2. Ouvrez le fichier **.cs** dans le nouveau projet et modifiez la classe `GestureExtension` pour implémenter votre gestionnaire de mouvements.

    Pour plus d’informations, consultez [Implémentation du gestionnaire de mouvements](#Implementing).

3. Appuyez sur F5 pour tester le gestionnaire de mouvements. Pour plus d’informations, consultez [Exécution du gestionnaire de mouvements](#Executing).

4. Installez le gestionnaire de mouvements sur un autre ordinateur en copiant le fichier **bin\\\*\\\*. vsix** généré par votre projet. Pour plus d’informations, consultez [Installation et désinstallation d’une extension](#Installing).

   Voici une autre procédure :

#### <a name="to-create-a-separate-class-library-dll-project-for-the-gesture-handler"></a>Pour créer un projet distinct de bibliothèque de classes (DLL) pour le gestionnaire de mouvements

1. Créez un projet de bibliothèque de classes dans une nouvelle solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou dans une solution existante.

   1. Dans le menu **Fichier** , choisissez **Nouveau**, **Projet**.

   2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis dans la colonne du milieu, choisissez **Bibliothèque de classes**.

2. Ajoutez les références suivantes à votre projet.

    `Microsoft.VisualStudio.Modeling.Sdk.[version]`

    `Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility`

    `Microsoft.VisualStudio.Uml.Interfaces`

    `System.ComponentModel.Composition`

    `System.Windows.Forms`

    `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer` : cette référence n’est utile que si vous étendez des diagrammes de couche. Pour plus d’informations, consultez [étendre des diagrammes de couche](../modeling/extend-layer-diagrams.md).

3. Ajouter un fichier de classe au projet et affecter le code suivant comme contenu.

   > [!NOTE]
   > Modifiez l’espace de noms et le nom de la classe en fonction de vos besoins.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Modeling.Diagrams;
   using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Modeling;
   using Microsoft.VisualStudio.Uml.Classes;
   // ADD other UML namespaces if required

   namespace MyGestureHandler // CHANGE
   {
     // DELETE any of these attributes if the handler
     // should not work with some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // Gesture handlers must export IGestureExtension:
     [Export(typeof(IGestureExtension))]
     // CHANGE class name
     public class MyGesture1 : IGestureExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       /// <summary>
       /// Called when the user double-clicks on the diagram
       /// </summary>
       /// <param name="targetElement"></param>
       /// <param name="diagramPointEventArgs"></param>
       public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target shape, if any. Null if the target is the diagram.
         IShape targetIShape = targetElement.CreateIShape();

         // Do something...
       }

       /// <summary>
       /// Called repeatedly when the user drags from anywhere on the screen.
       /// Return value should indicate whether a drop here is allowed.
       /// </summary>
       /// <param name="targetMergeElement">References the element to be dropped on.</param>
       /// <param name="diagramDragEventArgs">References the element to be dropped.</param>
       /// <returns></returns>
       public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.

         // Get the target element, if any. Null if the target is the diagram.
         IShape targetIShape = targetMergeElement.CreateIShape();

         // This example allows drag of any UML elements.
         return GetModelElementsFromDragEvent(diagramDragEventArgs).Count() > 0;
       }

       /// <summary>
       /// Execute the action to be performed on the drop.
       /// </summary>
       /// <param name="targetDropElement"></param>
       /// <param name="diagramDragEventArgs"></param>
       public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
       {
         // CHANGE THIS CODE FOR YOUR APPLICATION.
       }

       /// <summary>
       /// Retrieves UML IElements from drag arguments.
       /// Works for drags from UML diagrams.
       /// </summary>
       private IEnumerable<IElement> GetModelElementsFromDragEvent
               (DiagramDragEventArgs dragEvent)
       {
         //ElementGroupPrototype is the container for
         //dragged and copied elements and toolbox items.
         ElementGroupPrototype prototype =
            dragEvent.Data.
            GetData(typeof(ElementGroupPrototype))
                 as ElementGroupPrototype;
         // Locate the originals in the implementation store.
         IElementDirectory implementationDirectory =
            dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

         return prototype.ProtoElements.Select(
           prototypeElement =>
           {
             ModelElement element = implementationDirectory
               .FindElement(prototypeElement.ElementId);
             ShapeElement shapeElement = element as ShapeElement;
             if (shapeElement != null)
             {
               // Dragged from a diagram.
               return shapeElement.ModelElement as IElement;
             }
             else
             {
               // Dragged from UML Model Explorer.
               return element as IElement;
             }
           });
       }

     }
   }

   ```

    Pour plus d’informations sur les éléments à ajouter dans les méthodes, consultez [Implémentation du gestionnaire de mouvements](#Implementing).

   Vous devez ajouter votre commande de menu à un projet VSIX, qui joue le rôle de conteneur pour l’installation de la commande. Si vous le souhaitez, vous pouvez inclure d’autres composants dans le même VSIX.

#### <a name="to-add-a-separate-gesture-handler-to-a-vsix-project"></a>Pour ajouter un gestionnaire de mouvements distinct à un projet VSIX

1. Vous n’avez pas besoin de suivre cette procédure si vous avez créé le gestionnaire de mouvements avec son propre VSIX.

2. Créez un projet VSIX, sauf si votre solution en comporte déjà un.

    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel de la solution, choisissez **Ajouter**, puis **Nouveau projet**.

    2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Extensibilité**. Dans la colonne du milieu, choisissez **Projet VSIX**.

3. Définissez le projet VSIX comme projet de démarrage de la solution.

    - Dans l’Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.

4. Dans **source.extension.vsixmanifest**, ajoutez le projet de bibliothèque de classes du gestionnaire de mouvements en tant que composant MEF :

    1. Sous l’onglet **Métadonnées** , nommez le VSIX.

    2. Sous l’onglet **Cibles d’installation** , définissez les versions de Visual Studio comme cibles.

    3. Sous l’onglet **Composants** , choisissez **Nouveau**puis, dans la boîte de dialogue, définissez :

         **Type** = **Composant MEF**

         **Source** = **Projet dans la solution actuelle**

         **Projet** = *Votre projet de bibliothèque de classes*

## <a name="Executing"></a>Exécution du gestionnaire de mouvements
 À des fins de test, exécutez votre gestionnaire de mouvements en mode débogage.

#### <a name="to-test-the-gesture-handler"></a>Pour tester le gestionnaire de mouvements

1. Appuyez sur **F5**, ou dans le menu **Déboguer** , choisissez **Démarrer le débogage**.

    Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre.

    **Dépannage**: si une nouvelle instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne démarre pas :

   - Si vous avez plusieurs projets, vérifiez que le projet VSIX est défini comme projet de démarrage de la solution.

   - Dans l'Explorateur de solutions, dans le menu contextuel du projet de démarrage ou du projet unique, choisissez Propriétés. Dans l’éditeur de propriétés du projet, choisissez l’onglet **Déboguer** . Assurez-vous que la chaîne dans le champ **Démarrer le programme externe** correspond au chemin d’accès complet de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], généralement :

        `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez ou créez un projet de modélisation, puis ouvrez ou créez un diagramme de modélisation. Utilisez un diagramme qui appartient à l’un des types répertoriés dans les attributs de la classe de votre gestionnaire de mouvements.

3. Double-cliquez sur le diagramme. Votre gestionnaire de double-clic doit être appelé.

4. Faites glisser un élément de l’Explorateur UML sur le diagramme. Votre gestionnaire de glisser-déplacer doit être appelé.

   **Dépannage**: si le gestionnaire de mouvements ne fonctionne pas, vérifiez ce qui suit :

- Le projet de gestionnaire de mouvements est répertorié en tant que composant MEF sous l’onglet **Composants** de **source.extensions.manifest** dans le projet VSIX.

- les paramètres de tous les attributs `Import` et `Export` sont valides.

- La méthode `CanDragDrop` ne retourne pas la valeur `false`.

- Le type de diagramme de modèle que vous utilisez (classe, séquence UML, etc.) est répertorié comme l’un des attributs de la classe du gestionnaire de mouvements [ClassDesignerExtension], [SequenceDesignerExtension], etc.

- Aucune fonctionnalité intégrée n’est déjà définie pour ce type de cible et d’élément déposé.

## <a name="Implementing"></a>Implémentation du gestionnaire de mouvements

### <a name="the-gesture-handler-methods"></a>Méthodes du gestionnaire de mouvements
 La classe du gestionnaire de mouvements implémente et exporte <xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement.IGestureExtension>. Les méthodes que vous devez définir sont les suivantes :

|||
|-|-|
|`bool CanDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Retournez la valeur `true` pour autoriser le déplacement de l’élément source référencé dans `dragEvent` vers cette cible.<br /><br /> Cette méthode ne doit pas apporter de modifications au modèle. Elle doit fonctionner rapidement, car elle permet de déterminer l’état de la flèche à mesure que l’utilisateur déplace la souris.|
|`void OnDragDrop (ShapeElement target, DiagramDragEventArgs dragEvent)`|Mettez à jour le modèle basé sur l’objet source référencé dans `dragEvent`et la cible.<br /><br /> Appelée quand l’utilisateur relâche le bouton de la souris après avoir effectué un glissement.|
|`void OnDoubleClick (ShapeElement target, DiagramPointEventArgs pointEvent)`|`target` est la forme sur laquelle l’utilisateur a double-cliqué.|

 Vous pouvez écrire des gestionnaires qui peuvent accepter non seulement des éléments UML, mais également une vaste gamme d’autres éléments, comme des fichiers, des nœuds dans un affichage de classes .NET, etc. L’utilisateur peut faire glisser l’un de ces éléments dans un diagramme UML, à condition que vous écriviez une méthode `OnDragDrop` capable de décoder la forme sérialisée des éléments. Les méthodes de décodage varient d’un type d’élément à l’autre.

 Les paramètres de ces méthodes sont les suivants :

- `ShapeElement target`. Forme ou diagramme sur lequel l’utilisateur a fait glisser quelque chose.

    `ShapeElement` est une classe dans l’implémentation qui est sous-jacente aux outils de modélisation UML. Pour réduire le risque de mettre le modèle UML et les diagrammes dans un état incohérent, nous vous recommandons de ne pas utiliser directement les méthodes de cette classe. Au lieu de cela, encapsulez l’élément dans un `IShape`, puis utilisez les méthodes décrites dans [afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md).

  - Pour obtenir un `IShape`:

      ```
      IShape targetIShape = target.CreateIShape(target);
      ```

  - Pour obtenir l’élément de modèle ciblé par l’opération de glissement ou de double-clic :

      ```
      IElement target = targetIShape.Element;
      ```

      Vous pouvez le caster en un type d’élément plus spécifique.

  - Pour obtenir le magasin de modèles UML qui contient le modèle UML :

      ```
      IModelStore modelStore =
        targetIShape.Element.GetModelStore(); 
      ```

  - Pour obtenir l’accès à l’hôte et au fournisseur de services :

      ```
      target.Store.GetService(typeof(EnvDTE.DTE)) as EnvDTE.DTE
      ```

- `DiagramDragEventArgs eventArgs`. Ce paramètre achemine la forme sérialisée de l’objet source d’une opération de glissement :

    ```
    System.Windows.Forms.IDataObject data = eventArgs.Data;
    ```

     Vous pouvez faire glisser des éléments de genres différents vers un diagramme, à partir de différentes parties de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ou à partir du Bureau Windows. Différents types d’éléments sont encodés de façons différentes dans `IDataObject`. Pour en extraire les éléments, consultez la documentation correspondant au type d’objet approprié.

     Si votre objet source est un élément UML glissé à partir de l’Explorateur de modèles UML ou d’un autre diagramme UML, reportez-vous à [obtenir des éléments de modèle UML à partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

### <a name="writing-the-code-of-the-methods"></a>Écriture du code des méthodes
 Pour plus d’informations sur l’écriture de code pour lire et mettre à jour le modèle, consultez [Programming with the UML API](../modeling/programming-with-the-uml-api.md).

 Pour plus d’informations sur l’accès aux informations de modèle dans une opération de glissement, consultez [obtenir des éléments de modèle UML à partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

 Si vous travaillez avec un diagramme de séquence, consultez également [modifier des diagrammes de séquence UML à l’aide de l’API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 Outre les paramètres des méthodes, vous pouvez déclarer une propriété importée dans votre classe qui fournit l’accès au diagramme et au modèle actuels.

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 La déclaration de `IDiagramContext` vous permet d’écrire du code dans vos méthodes qui accède au diagramme, à la sélection actuelle et au modèle :

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>)
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IDiagram diagram in modelStore.Diagrams) {...}
foreach (IElement element in modelStore.AllInstances<IUseCase>) {...}
```

 Pour plus d’informations, consultez [naviguer dans le modèle UML](../modeling/navigate-the-uml-model.md).

## <a name="Installing"></a>Installation et désinstallation d’une extension
 Vous pouvez installer une extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sur votre propre ordinateur et sur d’autres ordinateurs.

#### <a name="to-install-an-extension"></a>Pour installer une extension

1. Sur votre ordinateur, recherchez le fichier **.vsix** généré par votre projet VSIX.

    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel du projet VSIX, choisissez **Ouvrir le dossier dans l’Explorateur Windows**.

    2. Recherchez le fichier **bin\\\*\\** _YourProject_ **. vsix**

2. Copiez le fichier **.vsix** sur l’ordinateur cible sur lequel vous souhaitez installer l’extension. Il peut s’agir de votre propre ordinateur ou d’un autre ordinateur.

     L’ordinateur cible doit disposer de l’une des éditions de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que vous avez spécifiées dans **source.extension.vsixmanifest**.

3. Sur l’ordinateur cible, ouvrez le fichier **.vsix** .

     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Pour désinstaller une extension

1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension, puis choisissez **Désinstaller**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *% LocalAppData%* **\Local\Microsoft\VisualStudio\\[version] \Extensions**

## <a name="DragExample"></a> Exemple
 L’exemple suivant montre comment créer des lignes de vie dans un diagramme de séquence, en fonction des parties et des ports d’un composant ayant fait l’objet d’un glissement à partir d’un diagramme de composant.

 Pour le tester, appuyez sur F5. Une instance expérimentale de Visual Studio s’ouvre. Dans cette instance, ouvrez un modèle UML et créez un composant sur un diagramme de composant. Ajoutez à ce composant quelques interfaces et parties internes de composant. Sélectionnez les interfaces et les parties. Faites ensuite glisser les interfaces et les parties sur un diagramme de séquence. (Faites glisser le diagramme de composant vers le haut jusqu’à l’onglet du diagramme de séquence, puis vers le haut dans le diagramme de séquence). Une vie s’affiche pour chaque interface et chaque partie.

 Pour plus d’informations sur la liaison d’interactions à des diagrammes de séquence, consultez [modifier des diagrammes de séquence UML à l’aide de l’API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

```
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Interactions;
using Microsoft.VisualStudio.Uml.CompositeStructures;
using Microsoft.VisualStudio.Uml.Components;

/// <summary>
/// Creates lifelines from component ports and parts.
/// </summary>
[Export(typeof(IGestureExtension))]
[SequenceDesignerExtension]
public class CreateLifelinesFromComponentParts : IGestureExtension
{
  [Import]
  public IDiagramContext Context { get; set; }

  /// <summary>
  /// Called by the modeling framework when
  /// the user drops something on a target.
  /// </summary>
  /// <param name="target">The target shape or diagram </param>
  /// <param name="dragEvent">The item being dragged</param>
  public void OnDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    ISequenceDiagram diagram = Context.CurrentDiagram
            as ISequenceDiagram;
    IInteraction interaction = diagram.Interaction;
    if (interaction == null)
    {
      // Sequence diagram is empty: create an interaction.
      interaction = diagram.ModelStore.Root.CreateInteraction();
      interaction.Name = Context.CurrentDiagram.Name;
      diagram.Bind(interaction);
    }
    foreach (IConnectableElement connectable in
       GetConnectablesFromDrag(dragEvent))
    {
      ILifeline lifeline = interaction.CreateLifeline();
      lifeline.Represents = connectable;
      lifeline.Name = connectable.Name;
    }
  }

  /// <summary>
  /// Called by the modeling framework to determine whether
  /// the user can drop something on a target.
  /// Must not change anything.
  /// </summary>
  /// <param name="target">The target shape or diagram</param>
  /// <param name="dragEvent">The item being dragged</param>
  /// <returns>true if this item can be dropped on this target</returns>
  public bool CanDragDrop(ShapeElement target,
           DiagramDragEventArgs dragEvent)
  {
    IEnumerable<IConnectableElement> connectables = GetConnectablesFromDrag(dragEvent);
    return connectables.Count() > 0;
  }

  ///<summary>
  /// Get dragged parts and ports of an IComponent.
  ///</summary>
  private IEnumerable<IConnectableElement>
    GetConnectablesFromDrag(DiagramDragEventArgs dragEvent)
  {
    foreach (IElement element in
      GetModelElementsFromDragEvent(dragEvent))
    {
      IConnectableElement part = element as IConnectableElement;
      if (part != null)
      {
        yield return part;
      }
    }
  }

  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
          (DiagramDragEventArgs dragEvent)
  {
    //ElementGroupPrototype is the container for
    //dragged and copied elements and toolbox items.
    ElementGroupPrototype prototype =
       dragEvent.Data.
       GetData(typeof(ElementGroupPrototype))
            as ElementGroupPrototype;
    // Locate the originals in the implementation store.
    IElementDirectory implementationDirectory =
       dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

    return prototype.ProtoElements.Select(
      prototypeElement =>
      {
        ModelElement element = implementationDirectory
          .FindElement(prototypeElement.ElementId);
        ShapeElement shapeElement = element as ShapeElement;
        if (shapeElement != null)
        {
          // Dragged from a diagram.
          return shapeElement.ModelElement as IElement;
        }
        else
        {
          // Dragged from UML Model Explorer.
          return element as IElement;
        }
      });
  }

  public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
  {
  }
}

```

 Le code de `GetModelElementsFromDragEvent()` est décrit dans la rubrique [récupérer des éléments de modèle UML à partir de IDataObject](../modeling/get-uml-model-elements-from-idataobject.md).

## <a name="see-also"></a>Voir aussi
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md) [étendre des modèles et des diagrammes UML](../modeling/extend-uml-models-and-diagrams.md) [définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md) [programmation à l’aide de l’API UML](../modeling/programming-with-the-uml-api.md)
