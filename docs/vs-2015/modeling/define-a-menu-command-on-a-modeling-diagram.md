---
title: Définir une commande de menu sur un diagramme de modélisation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, menu commands
ms.assetid: 79c277de-5871-4fc7-9701-55eec5c3cd46
caps.latest.revision: 63
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23ba1a6900559d7ee13639bb1da696127e47e536
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299269"
---
# <a name="define-a-menu-command-on-a-modeling-diagram"></a>Définir une commande de menu sur un diagramme de modélisation
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez définir des éléments de menu supplémentaires dans les menus contextuels d’un diagramme UML. Vous pouvez contrôler si la commande de menu apparaît et est activée dans le menu contextuel d’un élément sur le diagramme, et vous pouvez écrire du code qui s’exécute quand l’utilisateur choisit l’élément de menu. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio ([VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)) et les distribuer à d’autres utilisateurs de Visual Studio.

## <a name="requirements"></a>Configuration requise
 Consultez [Spécifications](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="defining-the-menu-command"></a>Définition de la commande de menu
 Pour créer une commande de menu pour un concepteur UML, vous devez créer une classe qui définit le comportement de la commande et incorporer cette classe dans une Extension d’intégration Visual Studio (VSIX). Cette dernière joue le rôle de conteneur capable d’installer la commande. Deux autres méthodes permettent de définir une commande de menu :

- **Créer une commande de menu dans sa propre extension VSIX à l’aide d’un modèle de projet.** Il s’agit de l’approche la plus rapide. Adoptez-la si vous ne souhaitez pas combiner vos commandes de menu avec d’autres types d’extensions, telles que les extensions de validation, les éléments de boîte à outils personnalisés ou les gestionnaires de mouvements.

- **Créer des projets VSIX et des commandes de menu distincts.** Adoptez cette approche si vous souhaitez combiner plusieurs types d’extensions dans la même extension VSIX. Par exemple, si votre commande de menu prévoit que le modèle observe des contraintes spécifiques, vous pouvez l’incorporer à la même extension VSIX en tant que méthode de validation.

#### <a name="to-create-a-menu-command-in-its-own-vsix"></a>Pour créer une commande de menu dans sa propre extension VSIX

1. Dans la boîte de dialogue **Nouveau projet** , sous **Projets de modélisation**, cliquez sur **Extension de commande**.

2. Ouvrez le fichier **.cs** dans le nouveau projet et modifiez la classe `CommandExtension` pour implémenter votre commande.

    Pour plus d’informations, consultez [Implémentation de la commande de menu](#Implementing).

3. Vous pouvez ajouter des commandes supplémentaires à ce projet en définissant de nouvelles classes.

4. Testez la commande de menu en appuyant sur F5. Pour plus d’informations, consultez [Exécution de la commande de menu](#Executing).

5. Installez la commande de menu sur un autre ordinateur en copiant le fichier **bin\\\*\\\*. vsix** généré par votre projet. Pour plus d’informations, consultez [Installation et désinstallation d’une extension](#Installing).

   Voici une autre procédure :

#### <a name="to-create-a-menu-command-in-a-separate-class-library-dll-project"></a>Pour créer une commande de menu dans un projet de bibliothèque de classes (DLL) distinct

1. Créez un projet de bibliothèque de classes dans une nouvelle solution Visual Studio ou dans une solution existante.

   1. Dans le menu **Fichier**, sélectionnez **Nouveau**, **Projet**.

   2. Sous **Modèles installés**, sélectionnez **Visual C#** ou **Visual Basic**. Dans la colonne du milieu, choisissez **Bibliothèque de classes**.

   3. Définissez **Solution** pour indiquer si vous souhaitez créer une solution ou ajouter un composant à une solution VSIX déjà ouverte.

   4. Définissez le nom et l’emplacement du projet, puis cliquez sur OK.

2. Ajoutez les références suivantes à votre projet.

   |                                                                                                    Référence                                                                                                    |                                                                                                  Ce que cela vous permet de faire                                                                                                  |
   |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |                                                                                        System.ComponentModel.Composition                                                                                        |                                         Définir des composants à l’aide de [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).                                          |
   |                                                                                      Microsoft.VisualStudio.Uml.Interfaces                                                                                      |                                                                                        Lire et modifier des propriétés d’éléments de modèle.                                                                                         |
   |                                                                             Microsoft.VisualStudio.ArchitectureTools.Extensibility                                                                              |                                                                                      Créer des éléments de modèle, modifiez des formes sur des diagrammes.                                                                                       |
   |                                                                                  Microsoft.VisualStudio.Modeling.Sdk.[version]                                                                                  | Définir des gestionnaires d’événements de modèle.<br /><br /> Encapsuler des séries de modifications apportées à votre modèle. Pour plus d’informations, consultez [lier des mises à jour de modèle UML à l’aide de transactions](../modeling/link-uml-model-updates-by-using-transactions.md). |
   |                                                            Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]<br /><br /> (n’est pas toujours obligatoire)                                                             |                                                                                   Accéder à des éléments de diagramme supplémentaires pour les gestionnaires de mouvements.                                                                                   |
   | Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer<br /><br /> Obligatoire uniquement pour les commandes sur des diagrammes de couche. Pour plus d’informations, consultez [étendre des diagrammes de couche](../modeling/extend-layer-diagrams.md). |                                                                                             Définir des commandes sur un diagramme de couche.                                                                                              |

3. Ajouter un fichier de classe au projet et affecter le code suivant comme contenu.

   > [!NOTE]
   > Modifier l’espace de noms, le nom de classe et la valeur retournés par `Text` selon vos préférences.
   >
   >  Si vous définissez plusieurs commandes, elles apparaissent dans le menu par ordre alphabétique des noms de classes.

   ```
   using System.ComponentModel.Composition;
   using System.Linq;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
   using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
   using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
   using Microsoft.VisualStudio.Uml.AuxiliaryConstructs;
   using Microsoft.VisualStudio.Uml.Classes;
       // ADD other UML namespaces if required

   namespace UMLmenu1 // CHANGE
   {
     // DELETE any of these attributes if the command
     // should not appear in some types of diagram.
     [ClassDesignerExtension]
     [ActivityDesignerExtension]
     [ComponentDesignerExtension]
     [SequenceDesignerExtension]
     [UseCaseDesignerExtension]
     // [LayerDesignerExtension]

     // All menu commands must export ICommandExtension:
     [Export (typeof(ICommandExtension))]
     // CHANGE class name – determines order of appearance on menu:
     public class Menu1 : ICommandExtension
     {
       [Import]
       public IDiagramContext DiagramContext { get; set; }

       public void QueryStatus(IMenuCommand command)
       { // Set command.Visible or command.Enabled to false
         // to disable the menu command.
         command.Visible = command.Enabled = true;
       }

       public string Text
       {
         get { return "MENU COMMAND LABEL"; }
       }

       public void Execute(IMenuCommand command)
       {
         // A selection of starting points:
         IDiagram diagram = this.DiagramContext.CurrentDiagram;
         foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
         { IElement element = shape.Element; }
         IModelStore modelStore = diagram.ModelStore;
         IModel model = modelStore.Root;
         foreach (IElement element in modelStore.AllInstances<IClass>())
         { }
       }
     }
   }
   ```

    Pour plus d’informations sur les éléments à ajouter dans les méthodes, consultez [Implémentation de la commande de menu](#Implementing).

   Vous devez ajouter votre commande de menu à un projet VSIX, qui joue le rôle de conteneur pour l’installation de la commande. Si vous le souhaitez, vous pouvez inclure d’autres composants dans le même VSIX.

#### <a name="to-add-a-menu-command-to-a-vsix-project"></a>Pour ajouter une commande de menu à un projet VSIX

1. Il est inutile d’appliquer cette procédure si vous avez créé la commande de menu avec sa propre extension VSIX.

2. Créez un projet VSIX, sauf si votre solution en comporte déjà un.

    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel de la solution, choisissez **Ajouter**, puis **Nouveau projet**.

    2. Sous **Modèles installés**, développez **Visual C#** ou **Visual Basic**, puis sélectionnez **Extensibilité**. Dans la colonne du milieu, choisissez **Projet VSIX**.

3. Dans l’Explorateur de solutions, dans le menu contextuel du projet VSIX, choisissez **Définir comme projet de démarrage**.

4. Ouvrez **source.extension.vsixmanifest**.

    1. Sous l’onglet **Métadonnées** , nommez le VSIX.

    2. Sous l’onglet **Cibles d’installation** , définissez les versions de Visual Studio comme cibles.

    3. Sous l’onglet **Composants** , choisissez **Nouveau**puis, dans la boîte de dialogue, définissez :

         **Type** = **Composant MEF**

         **Source** = **Projet dans la solution actuelle**

         **Projet** = *Votre projet de bibliothèque de classes*

## <a name="Implementing"></a>Implémentation de la commande de menu
 La classe de commande de menu implémente les méthodes nécessaires pour <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension>.

|||
|-|-|
|`string Text { get; }`|Retourne l’étiquette de votre élément de menu.|
|`void QueryStatus(IMenuCommand command);`|Appelée quand l’utilisateur clique avec le bouton droit sur le diagramme.<br /><br /> Cette méthode ne doit pas modifier le modèle.<br /><br /> Utilisez `DiagramContext.CurrentDiagram.SelectedShapes` pour déterminer si vous souhaitez que la commande apparaisse et soit activée.<br /><br /> Définir :<br /><br /> -   `command.Visible` à `true` si la commande doit apparaître dans le menu quand l’utilisateur clique avec le bouton droit dans le diagramme<br />-   `command.Enabled` à `true` si l’utilisateur peut cliquer sur la commande dans le menu<br />-   `command.Text` pour définir l’étiquette de menu de manière dynamique|
|`void Execute (IMenuCommand command);`|Appelée quand l’utilisateur clique sur votre élément de menu, s’il est visible et activé.|

### <a name="accessing-the-model-in-code"></a>Accès au modèle dans le code
 Incluez la déclaration suivante dans votre classe de commande de menu :

```
[Import] public IDiagramContext DiagramContext { get; set; }
```

 ...

 La déclaration de `IDiagramContext` vous permet d’écrire du code dans vos méthodes qui accède au diagramme, à la sélection actuelle et au modèle :

```
IDiagram diagram = this.DiagramContext.CurrentDiagram;
foreach (IShape<IElement> shape in diagram.GetSelectedShapes<IElement>())
{ IElement element = shape.Element; ... }
IModelStore modelStore = diagram.ModelStore;
IModel model = modelStore.Root;
foreach (IElement element in modelStore.AllInstances<IUseCase>()) {...}
```

### <a name="navigating-and-updating-the-model"></a>Navigation et mise à jour du modèle
 Les éléments du modèle UML sont tous disponibles via l’API. À partir de la sélection actuelle ou de la racine du modèle, vous pouvez accéder à tous les autres éléments. Pour plus d’informations, consultez [naviguer dans le modèle UML](../modeling/navigate-the-uml-model.md) et [programmation à l’aide de l’API UML](../modeling/programming-with-the-uml-api.md).

 Si vous travaillez avec un diagramme de séquence, consultez également [modifier des diagrammes de séquence UML à l’aide de l’API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).

 L’API vous permet aussi de modifier les propriétés des éléments, de supprimer des éléments et des relations, et de créer des éléments et des relations.

 Par défaut, chaque modification que vous apportez dans votre méthode Execute est effectuée dans une transaction distincte. L’utilisateur peut annuler chaque modification séparément. Si vous souhaitez regrouper les modifications dans une transaction unique, utilisez une <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoTransaction> comme décrit dans [lier des mises à jour de modèles UML à l’aide de transactions](../modeling/link-uml-model-updates-by-using-transactions.md).

### <a name="use-the-ui-thread-for-updates"></a>Utiliser le thread d’interface utilisateur pour les mises à jour
 Dans certains cas, il peut être utile de mettre à jour le modèle à partir d’un thread d’arrière-plan. Par exemple, si votre commande charge des données à partir d’une ressource lente, vous pouvez effectuer le chargement dans un thread d’arrière-plan pour que l’utilisateur puisse voir les modifications pendant qu’elles sont en cours et annuler l’opération si nécessaire.

 Toutefois, sachez que le magasin de modèles n’est pas thread-safe. Vous devez toujours utiliser le thread d’interface utilisateur pour effectuer des mises à jour et, dans la mesure du possible, empêcher l’utilisateur d’apporter des modifications pendant que l’opération d’arrière-plan est en cours. Pour obtenir un exemple, consultez [mettre à jour un modèle UML à partir d’un thread d’arrière-plan](../modeling/update-a-uml-model-from-a-background-thread.md).

## <a name="Executing"></a>Exécution de la commande de menu
 À des fins de test, exécutez votre commande en mode débogage.

#### <a name="to-test-the-menu-command"></a>Pour tester la commande de menu

1. Appuyez sur **F5**, ou dans le menu **Déboguer** , choisissez **Démarrer le débogage**.

     Une instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] démarre.

     **Dépannage**: si une nouvelle instance de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ne démarre pas :

    - Si vous avez plusieurs projets, vérifiez que le projet VSIX est défini comme projet de démarrage de la solution.

    - Dans l’Explorateur de solutions, dans le menu contextuel du projet de démarrage ou du projet unique, choisissez **Propriétés**. Dans l’éditeur de propriétés du projet, sélectionnez l’onglet **Déboguer** . Assurez-vous que la chaîne dans le champ **Démarrer le programme externe** correspond au chemin d’accès complet de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], généralement :

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Dans l’instance expérimentale de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ouvrez ou créez un projet de modélisation, puis ouvrez ou créez un diagramme de modélisation. Utilisez un diagramme qui appartient à l’un des types répertoriés dans les attributs de votre classe de commande de menu.

3. Ouvrez le menu contextuel n’importe où sur le diagramme. Votre commande doit apparaître dans le menu.

     **Dépannage**: si la commande n’apparaît pas dans le menu, vérifiez que :

    - le projet de commande de menu est répertorié en tant que composant MEF sous l’onglet **Composants** de **source.extensions.manifest** dans le projet VSIX ;

    - les paramètres des attributs `Import` et `Export` sont valides ;

    - La méthode `QueryStatus` ne définit pas la `command`.`Enabled` ou `Visible` ou `false`.

    - le type de diagramme de modèle que vous utilisez (classe UML, séquence, etc.) est répertorié comme l’un des attributs de classe de commande de menu `[ClassDesignerExtension]`, `[SequenceDesignerExtension]` et ainsi de suite.

## <a name="Installing"></a>Installation et désinstallation d’une extension
 Vous pouvez installer une extension [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sur votre propre ordinateur et sur d’autres ordinateurs.

#### <a name="to-install-an-extension"></a>Pour installer une extension

1. Sur votre ordinateur, recherchez le fichier **.vsix** généré par votre projet VSIX.

    1. Dans l’ **Explorateur de solutions**, dans le menu contextuel du projet VSIX, choisissez **Ouvrir le dossier dans l’Explorateur Windows**.

    2. Recherchez le fichier **bin\\\*\\** _YourProject_ **. vsix**

2. Copiez le fichier **.vsix** sur l’ordinateur cible sur lequel vous souhaitez installer l’extension. Il peut s’agir de votre propre ordinateur ou d’un autre ordinateur.

     L’ordinateur cible doit disposer de l’une des éditions de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] que vous avez spécifiées dans **source.extension.vsixmanifest**.

3. Sur l’ordinateur cible, ouvrez le fichier **.vsix** , par exemple en double-cliquant dessus.

     Le**Programme d’installation des extensions Visual Studio** s’ouvre et installe l’extension.

4. Démarrez ou redémarrez [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Pour désinstaller une extension

1. Dans le menu **Outils** , choisissez **Extensions et mises à jour**.

2. Développez **Extensions installées**.

3. Sélectionnez l’extension, puis choisissez **Désinstaller**.

   Exceptionnellement, une extension défaillante ne parvient pas à se charger et crée un rapport dans la fenêtre d’erreur, mais ne s’affiche pas dans le Gestionnaire d’extensions. Dans ce cas, vous pouvez supprimer l’extension en supprimant le fichier de l’emplacement suivant :

   *% LocalAppData%* **\Local\Microsoft\VisualStudio\\[version] \Extensions**

## <a name="MenuExample"></a> Exemple
 L’exemple suivant montre le code pour une commande de menu qui échange les noms de deux éléments sur un diagramme de classes. Ce code doit être intégré à un projet d’Extension [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et installé comme décrit dans les sections précédentes.

```
using System.Collections.Generic; // for IEnumerable
using System.ComponentModel.Composition;
  // for [Import], [Export]
using System.Linq; // for IEnumerable extensions
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
  // for IDiagramContext
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
  // for designer extension attributes
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;
  // for IGestureExtension, ICommandExtension, ILinkedUndoContext
using Microsoft.VisualStudio.Uml.Classes;
  // for class diagrams, packages

/// <summary>
/// Extension to swap names of classes in a class diagram.
/// </summary>
namespace SwapClassNames
{
  // Declare the class as an MEF component:
  [Export(typeof(ICommandExtension))]
  [ClassDesignerExtension]
  // Add more ExportMetadata attributes to make
  // the command appear on diagrams of other types.
  public class NameSwapper : ICommandExtension
  {
  // MEF required interfaces:
  [Import]
  public IDiagramContext Context { get; set; }
  [Import]
  public ILinkedUndoContext LinkedUndoContext { get; set; }

  /// <summary>
  /// Swap the names of the currently selected elements.
  /// </summary>
  /// <param name="command"></param>
  public void Execute(IMenuCommand command)
  {
    // Get selected shapes that are IClassifiers -
    // IClasses, IInterfaces, IEnumerators.
    var selectedShapes = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>();
    if (selectedShapes.Count() < 2) return;

    // Get model elements displayed by shapes.
    IClassifier firstElement = selectedShapes.First().Element;
    IClassifier lastElement = selectedShapes.Last().Element;

    // Do the swap in a transaction so that user
    // cannot undo one change without the other.
    using (ILinkedUndoTransaction transaction =
    LinkedUndoContext.BeginTransaction("Swap names"))
    {
    string firstName = firstElement.Name;
    firstElement.Name = lastElement.Name;
    lastElement.Name = firstName;
    transaction.Commit();
    }
  }

  /// <summary>
  /// Called by Visual Studio to determine whether
  /// menu item should be visible and enabled.
  /// </summary>
  public void QueryStatus(IMenuCommand command)
  {
    int selectedClassifiers = Context.CurrentDiagram
     .GetSelectedShapes<IClassifier>().Count();
    command.Visible = selectedClassifiers > 0;
    command.Enabled = selectedClassifiers == 2;
  }

  /// <summary>
  /// Name of the menu command.
  /// </summary>
  public string Text
  {
    get { return "Swap Names"; }
  }
  }

}
```

## <a name="see-also"></a>Voir aussi
 [Définir et installer une extension de modélisation](../modeling/define-and-install-a-modeling-extension.md) [étendre des modèles et des diagrammes UML](../modeling/extend-uml-models-and-diagrams.md) [définir un gestionnaire de mouvements sur un diagramme de modélisation](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [définir un élément de boîte à outils de modélisation personnalisé](../modeling/define-a-custom-modeling-toolbox-item.md) [définir des contraintes de validation pour les modèles UML](../modeling/define-validation-constraints-for-uml-models.md) [modifier des diagrammes de séquence UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md) à l’aide de la programmation de l’API UML [avec l’exemple d’API UML](../modeling/programming-with-the-uml-api.md) [: commande pour aligner des formes sur un diagramme UML](https://go.microsoft.com/fwlink/?LinkID=213809)
