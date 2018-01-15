---
title: "Ajouter des commandes et des mouvements aux diagrammes de dépendance | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom commands
- dependency diagrams, adding custom gestures
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f580c81d63adb2ca474f8ea9f250f48a61da928a
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2018
---
# <a name="add-commands-and-gestures-to-dependency-diagrams"></a>Ajouter des commandes et des mouvements aux diagrammes de dépendance
Vous pouvez définir des commandes de menu contextuel et gestionnaires de mouvements dans des diagrammes de dépendance dans Visual Studio. Vous pouvez empaqueter ces extensions dans une extension d’intégration Visual Studio (VSIX) et les distribuer à d’autres utilisateurs de Visual Studio.  
  
 Si vous le souhaitez, vous pouvez définir plusieurs commandes et gestionnaires de mouvements dans le même projet Visual Studio. Vous pouvez également combiner plusieurs de ces projets dans une extension VSIX. Par exemple, vous pouvez définir une extension VSIX qui comprend des commandes de couche et un langage spécifique à un domaine.  
  
> [!NOTE]
>  Vous pouvez également personnaliser la validation de l’architecture, dans source quels utilisateurs code est comparé aux diagrammes de dépendance. Vous devez définir la validation de l’architecture dans un projet Visual Studio distinct. Vous pouvez l’ajouter à la même extension VSIX que d’autres extensions. Pour plus d’informations, consultez [ajouter la validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
## <a name="requirements"></a>Configuration requise  
 Consultez [Spécifications](../modeling/extend-layer-diagrams.md#prereqs).  
  
## <a name="defining-a-command-or-gesture-in-a-new-vsix"></a>Définition d’une commande ou d’un mouvement dans une nouvelle extension VSIX  
 Pour créer une extension, la méthode la plus rapide consiste à utiliser le modèle de projet. Le code et le manifeste VSIX sont alors placés dans le même projet.  
  
#### <a name="to-define-an-extension-by-using-a-project-template"></a>Pour définir une extension à l’aide d’un modèle de projet  
  
1.  Créez un projet dans une nouvelle solution en sélectionnant la commande **Nouveau projet** dans le menu **Fichier** .  
  
2.  Dans la boîte de dialogue **Nouveau projet** , sous **Projets de modélisation**, sélectionnez **Concepteur de couche - Extension de commande** ou **Concepteur de couche - Extension de mouvement**.  
  
     Le modèle crée un projet qui contient un petit exemple fonctionnel.  
  
3.  Pour tester l’extension, appuyez sur **Ctrl+F5** ou **F5**.  
  
     Démarrage d’une instance expérimentale de Visual Studio. Dans cette instance, créez un diagramme de dépendances. Votre extension de commande ou de mouvement doit fonctionner dans ce diagramme.  
  
4.  Fermez l’instance expérimentale et modifiez l’exemple de code. Pour plus d’informations, consultez [naviguer et mise à jour des modèles dans le code de programme de couche](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
5.  Vous pouvez ajouter plusieurs gestionnaires de mouvements ou de commandes au même projet. Pour plus d’informations, consultez l’une des sections suivantes :  
  
     [Définition d’une commande de menu](#command)  
  
     [Définition d’un gestionnaire de mouvements](#gesture)  
  
6.  Pour installer l’extension dans l’instance principale de Visual Studio ou sur un autre ordinateur, recherchez le **.vsix** fichier **bin\\\***. Copiez-le sur l’ordinateur sur lequel vous souhaitez l’installer, puis double-cliquez dessus. Pour le désinstaller, utilisez **Extensions et mises à jour** dans le menu **Outils** .  
  
## <a name="adding-a-command-or-gesture-to-a-separate-vsix"></a>Ajout d’une commande ou d’un mouvement à une extension VSIX distincte  
 Si vous souhaitez créer une extension VSIX qui contient des commandes, des validateurs de couche et d’autres extensions, nous vous recommandons de créer un projet pour définir l’extension VSIX et des projets distincts pour les gestionnaires.
  
#### <a name="to-add-layer-extensions-to-a-separate-vsix"></a>Pour ajouter des extensions de couche à une extension VSIX distincte  
  
1.  Créez un projet de bibliothèque de classes dans une solution Visual Studio nouvelle ou existante. Dans la boîte de dialogue **Nouveau projet** , cliquez sur **Visual C#** , puis sur **Bibliothèque de classes**. Ce projet contiendra les classes des commandes ou des gestionnaires de mouvements.  
  
    > [!NOTE]
    >  Vous pouvez définir plusieurs classes de gestionnaires de mouvements ou de commandes dans une bibliothèque de classes, mais vous devez définir les classes de validation de couche dans une bibliothèque de classes distincte.  
  
2.  Identifiez ou créez un projet VSIX dans votre solution. Un projet VSIX contient un fichier nommé **source.extension.vsixmanifest**. Pour ajouter un projet VSIX :  
  
    1.  Dans la boîte de dialogue **Nouveau projet** , développez **Visual C#**, cliquez sur **Extensibilité**, puis sur **Projet VSIX**.  
  
    2.  Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le projet VSIX, puis cliquez sur **Définir comme projet de démarrage**.  
  
    3.  Cliquez sur **Sélectionner des éditions** et assurez-vous que **Visual Studio** est sélectionné.  
  
3.  Dans **source.extension.vsixmanifest**, sous **Composants**, ajoutez le projet de commande ou de gestionnaire de mouvements en tant que composant MEF.  
  
    1.  Sous l’onglet **Composants**, choisissez **Nouveau**.  
  
    2.  Pour **Type**, sélectionnez **Microsoft.VisualStudio.MefComponent**.  
  
    3.  Pour **Source**, sélectionnez **Projet dans la solution actuelle** et sélectionnez le nom de votre projet de gestionnaire de mouvements ou de commande.  
  
    4.  Enregistrez le fichier.  
  
4.  Revenez au projet de gestionnaire de mouvements ou de commande et ajoutez les références de projet suivantes.  
  
|**Référence**|**Ce que cela vous permet de faire**|  
|-------------------|------------------------------------|  
|Program Files\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Créer et modifier des couches|  
|Microsoft.VisualStudio.Uml.Interfaces|Créer et modifier des couches|  
|Microsoft.VisualStudio.ArchitectureTools.Extensibility|Modifier des formes dans les diagrammes|  
|System.ComponentModel.Composition|Définir des composants à l’aide de Managed Extensibility Framework (MEF)|  
|Microsoft.VisualStudio.Modeling.Sdk.[version]|Définir des extensions de modélisation|  
|Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]|Mettre à jour des formes et des diagrammes|  
  
1.  Modifiez le fichier de classe dans le projet de bibliothèque de classes C# pour contenir le code de votre extension. Pour plus d’informations, consultez l’une des sections suivantes :  
  
     [Définition d’une commande de menu](#command)  
  
     [Définition d’un gestionnaire de mouvements](#gesture)  
  
     Voir aussi [naviguer et mise à jour des modèles dans le code de programme de couche](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
2.  Pour tester la fonctionnalité, appuyez sur Ctrl+F5 ou F5. Une instance expérimentale de Visual Studio s’ouvre. Dans cette instance, créez ou ouvrez un diagramme de dépendance.  
  
3.  Pour installer l’extension VSIX dans l’instance principale de Visual Studio ou sur un autre ordinateur, recherchez le **.vsix** de fichiers dans le **bin** répertoire du projet VSIX. Copiez-le sur l’ordinateur sur lequel vous souhaitez installer l’extension VSIX. Double-cliquez sur le fichier VSIX dans l’Explorateur Windows.  
  
     Pour le désinstaller, utilisez **Extensions et mises à jour** dans le menu **Outils** .  
  
##  <a name="command"></a> Définition d’une commande de menu  
 Vous pouvez ajouter plusieurs définitions de commandes de menu à un projet de commande ou de mouvement existant. Chaque commande est définie par une classe dont les caractéristiques sont les suivantes :  
  
-   La classe est déclarée comme suit :  
  
     `[LayerDesignerExtension]`  
  
     `[Export(typeof(ICommandExtension))]`  
  
     `public class`  *MyLayerCommand*  `: ICommandExtension { ... }`  
  
-   L’espace de noms et le nom de la classe sont sans importance.  
  
-   Les méthodes qui implémentent `ICommandExtension` sont les suivantes :  
  
    -   `string Text {get;}` : l’étiquette qui apparaît dans le menu.  
  
    -   `void QueryStatus(IMenuCommand command)` : appelée quand l’utilisateur clique avec le bouton droit sur le diagramme et détermine si la commande doit être visible et activée pour la sélection actuelle de l’utilisateur.  
  
    -   `void Execute(IMenuCommand command)` : appelée quand l’utilisateur sélectionne la commande.  
  
-   Pour déterminer la sélection actuelle, vous pouvez importer `IDiagramContext`:  
  
     `[Import]`  
  
     `public IDiagramContext DiagramContext { get; set; }`  
  
     `...`  
  
     `DiagramContext.CurrentDiagram.SelectedShapes.Count()...`  
  
 Pour plus d’informations, consultez [naviguer et mise à jour des modèles dans le code de programme de couche](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
 Pour ajouter une nouvelle commande, créez un fichier de code qui contient l’exemple suivant. Ensuite, testez-le et modifiez-le.  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
  
namespace MyLayerExtension // Change to your preference.  
{  
  // This is a feature for dependency diagrams:  
  [LayerDesignerExtension]  
  // This feature is a menu command:  
  [Export(typeof(ICommandExtension))]  
  // Change the class name to your preference:  
  public class MyLayerCommand : ICommandExtension  
  {  
    [Import]  
    public IDiagramContext DiagramContext { get; set; }  
  
    [Import]  
    public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
    // Menu command label:  
    public string Text  
    {  
      get { return "Duplicate layers"; }  
    }  
  
    // Called when the user right-clicks the diagram.  
    // Defines whether the command is visible and enabled.  
    public void QueryStatus(IMenuCommand command)  
    {   
      command.Visible =   
      command.Enabled = DiagramContext.CurrentDiagram  
        .SelectedShapes.Count() > 0;  
    }  
  
    // Called when the user selects the command.  
    public void Execute(IMenuCommand command)  
    {  
      // A selection of starting points:  
      IDiagram diagram = this.DiagramContext.CurrentDiagram;  
      ILayerModel lmodel = diagram.GetLayerModel();  
      foreach (ILayer layer in lmodel.Layers)  
      { // All layers in model.  
      }  
      // Updates should be performed in a transaction:  
      using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("copy selection"))  
      {  
        foreach (ILayer layer in   
          diagram.SelectedShapes  
            .Select(shape=>shape.GetLayerElement())  
            .Where(element => element is ILayer))  
        {  
          ILayer copy = lmodel.CreateLayer(layer.Name + "+");  
          // Position the shapes:  
          IShape originalShape = layer.GetShape();  
          copy.GetShape().Move(  
            originalShape.XPosition + originalShape.Width * 1.2,  
            originalShape.YPosition);  
        }  
        t.Commit();  
      }  
    }  
  }  
}  
```  
  
##  <a name="gesture"></a> Définition d’un gestionnaire de mouvements  
 Un gestionnaire de mouvements réagit quand l’utilisateur fait glisser des éléments sur le diagramme de dépendances, et lorsque l’utilisateur double-clique n’importe où dans le diagramme.  
  
 Vous pouvez ajouter un fichier de code qui définit un gestionnaire de mouvements à votre projet VSIX de commande ou de gestionnaire de mouvements existant :  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
using System.ComponentModel.Composition;  
using System.Linq;  
namespace MyLayerExtensions // change to your preference  
{  
  [LayerDesignerExtension]  
  [Export(typeof(IGestureExtension))]  
  public class MyLayerGestureHandler : IGestureExtension  
  {  
  }  
}  
```  
  
 Notez les points suivants concernant les gestionnaires de mouvements :  
  
-   Les membres de `IGestureExtension` sont les suivants :  
  
     **OnDoubleClick** : appelée quand l’utilisateur double-clique n’importe où sur le diagramme.  
  
     **CanDragDrop** : appelée à plusieurs reprises quand l’utilisateur déplace la souris tout en faisant glisser un élément sur le diagramme. Doit fonctionner rapidement.  
  
     **OnDragDrop** : appelée quand l’utilisateur dépose un élément sur le diagramme.  
  
-   Le premier argument de chaque méthode est un `IShape`, à partir duquel vous pouvez obtenir l’élément de couche. Exemple :  
  
    ```  
    public void OnDragDrop(IShape target, IDataObject data)  
    {  
        ILayerElement element = target.GetLayerElement();  
        if (element is ILayer)  
        {  
            // ...  
        }  
    }  
    ```  
  
-   Les gestionnaires pour certains types d’éléments déplacés sont déjà définis. Par exemple, l’utilisateur peut déplacer les éléments à partir de l’Explorateur de solutions vers un diagramme de dépendances. Vous ne pouvez pas définir un gestionnaire de glissement pour ces types d’éléments. Dans ces cas-là, vos méthodes `DragDrop` ne seront pas appelées.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder et mettre à jour des modèles de couche dans le code de programme](../modeling/navigate-and-update-layer-models-in-program-code.md)   
 [Ajout d’une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
