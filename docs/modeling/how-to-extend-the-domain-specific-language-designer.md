---
title: 'Comment : étendre le concepteur de langage spécifique à un domaine'
description: Découvrez comment vous pouvez créer des extensions du concepteur que vous utilisez pour modifier les définitions de langage spécifique à un domaine (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9354e3b846f48a79aa5cdd0f39a159bd007cdd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387215"
---
# <a name="how-to-extend-the-domain-specific-language-designer"></a>Comment : étendre le concepteur de langage spécifique à un domaine

Vous pouvez créer des extensions pour le concepteur que vous utilisez pour modifier les définitions DSL. Les types d’extensions que vous pouvez effectuer incluent l’ajout de commandes de menu, l’ajout de gestionnaires pour les gestes par glisser-cliquer et le double-clic, et les règles qui sont déclenchées quand des types particuliers de valeurs ou de relations changent. Les extensions peuvent être empaquetées en tant qu’extension d’intégration Visual Studio (VSIX) et distribuées à d’autres utilisateurs.

Pour obtenir un exemple de code et des informations supplémentaires sur cette fonctionnalité, consultez le [Kit de développement logiciel de visualisation et de modélisation](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)de Visual Studio.

## <a name="set-up-the-solution"></a>Configurer la solution

Configurez un projet qui contient le code de votre extension et un projet VSIX qui exporte le projet. Votre solution peut contenir d’autres projets incorporés dans la même extension VSIX.

### <a name="to-create-a-dsl-designer-extension-solution"></a>Pour créer une solution d’extension Concepteur DSL

1. Créez un nouveau projet à l’aide du modèle de projet **bibliothèque de classes** . Ce projet contiendra le code de vos extensions.

2. Créez un projet de **projet VSIX** .

     Sélectionnez **Ajouter à la solution**.

     *Source. extension. vsixmanifest* s’ouvre dans l’éditeur de manifeste VSIX.

3. Au-dessus du champ contenu, cliquez sur **Ajouter du contenu**.

4. Dans la boîte de dialogue **Ajouter du contenu** , définissez **Sélectionner un type de contenu** sur le **Composant MEF**, puis définissez **projet** sur votre projet de bibliothèque de classes.

5. Cliquez sur **Sélectionner des éditions** et assurez-vous que **Visual Studio Enterprise** est cochée.

6. Assurez-vous que le projet VSIX est le projet de démarrage de la solution.

7. Dans le projet de bibliothèque de classes, ajoutez des références aux assemblys suivants :

     Microsoft. VisualStudio. CoreUtility

     Microsoft. VisualStudio. Modeling. Sdk. 11.0

     Microsoft. VisualStudio. Modeling. Sdk. Diagrams. 11.0

     Microsoft. VisualStudio. Modeling. Sdk. DslDefinition. 11.0

     Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

     System.ComponentModel.Composition

     System.Drawing

     System.Drawing.Design

     System.Windows.Forms

## <a name="test-and-deployment"></a>Test et déploiement

Pour tester l’une des extensions de cette rubrique, générez et exécutez la solution. Une instance expérimentale de Visual Studio s’ouvre. Dans cette instance, ouvrez une solution DSL. Modifiez le diagramme DslDefinition. Le comportement de l’extension est visible.

Pour déployer les extensions sur le Visual Studio principal et sur d’autres ordinateurs, procédez comme suit :

1. Recherchez le fichier d’installation VSIX dans votre projet VSIX dans bin \\ * \\ \* . vsix

2. Copiez ce fichier sur l’ordinateur cible, puis dans l’Explorateur Windows (ou l’Explorateur de fichiers), double-cliquez dessus.

     Le gestionnaire d’extensions Visual Studio s’ouvre pour confirmer que l’extension a été installée.

Pour désinstaller l’extension, procédez comme suit :

1. dans Visual Studio, dans le menu **Outils** , cliquez sur **Gestionnaire d’extensions**.

2. Sélectionnez l’extension et supprimez-la.

## <a name="add-a-shortcut-menu-command"></a>Ajouter une commande de menu contextuel

Pour qu’une commande de menu contextuel s’affiche sur la surface de Concepteur DSL ou dans la fenêtre de l’Explorateur DSL, écrivez une classe ressemblant à ce qui suit.

La classe doit implémenter `ICommandExtension` et doit avoir l’attribut `DslDefinitionModelCommandExtension` .

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDefinition;
using Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.DslDesigner;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Command extending the DslDesigner.
  /// </summary>
  [DslDefinitionModelCommandExtension]
  public class MyDslDesignerCommand : ICommandExtension
  {
    /// <summary>
    /// Selection Context for this command
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Is the command visible and active?
    /// This is called when the user right-clicks.
    /// </summary>
    public void QueryStatus(IMenuCommand command)
    {
      command.Visible = true;
      // Is there any selected DomainClasses in the Dsl explorer?
      command.Enabled =
        SelectionContext.AtLeastOneSelected<DomainClass>();

      // Is there any selected ClassShape on the design surface?
      command.Enabled |=
        (SelectionContext.GetCurrentSelection<ClassShape>()
                .Count() > 0);
    }
    /// <summary>
    /// Executes the command
    /// </summary>
    /// <param name="command">Command initiating this action</param>
    public void Execute(IMenuCommand command)
    {
      ...
    }
    /// <summary>
    /// Label for the command
    /// </summary>
    public string Text
    {
      get { return "My Command"; }
    }
  }
}
```

## <a name="handle-mouse-gestures"></a>Gérer les gestes de souris

Le code est similaire au code de la commande de menu.

```csharp
[DslDefinitionModelGestureExtension]
 class MouseGesturesExtensions : IGestureExtension
 {
  /// <summary>
  /// Double-clicking on a shape representing a Domain model element displays this model element in a dialog box
  /// </summary>
  /// <param name="targetElement">Shape element on which the user has clicked</param>
  /// <param name="diagramPointEventArgs">event args for this double-click</param>
  public void OnDoubleClick(ShapeElement targetElement,
       DiagramPointEventArgs diagramPointEventArgs)
  {
   ModelElement modelElement = PresentationElementHelper.
        GetDslDefinitionModelElement(targetElement);
   if (modelElement != null)
   {
    MessageBox.Show(string.Format(
      "Double clicked on {0}", modelElement.ToString()),
      "Model element double-clicked");
   }
  }

  /// <summary>
  /// Tells if the DslDesigner can consume the to-be-dropped information
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we try to drop</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  /// <returns><c>true</c> if we can consume the to be dropped data, and <c>false</c> otherwise</returns>
  public bool CanDragDrop(ShapeElement targetMergeElement,
        DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    diagramDragEventArgs.Effect = DragDropEffects.Copy;
    return true;
   }
   return false;
  }

  /// <summary>
  /// Processes the drop by displaying the dropped text
  /// </summary>
  /// <param name="targetMergeElement">Shape on which we dropped</param>
  /// <param name="diagramDragEventArgs">Drop event</param>
  public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
  {
   if (diagramDragEventArgs.Data.GetDataPresent(DataFormats.FileDrop))
   {
    string[] droppedFiles =
      diagramDragEventArgs.Data.
               GetData(DataFormats.FileDrop) as string[];
    MessageBox.Show(string.Format("Dropped text {0}",
        string.Join("\r\n", droppedFiles)), "Dropped Text");
   }
  }
 }
```

## <a name="respond-to-value-changes"></a>Répondre aux modifications de valeur

Ce gestionnaire a besoin d’un modèle de domaine pour fonctionner correctement. Nous fournissons un modèle de domaine simple.

```csharp
using System.Diagnostics;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
  /// <summary>
  /// Rule firing when the type of a domain model property is changed. The change is displayed
  /// in the debugger (Output window of the Visual Studio instance debugging this extension)
  /// </summary>
  [RuleOn(typeof(PropertyHasType))]
  public class DomainPropertyTypeChangedRule : RolePlayerChangeRule
  {
    /// <summary>
    /// Method called when the Type of a Domain Property
    /// is changed by the user in a DslDefinition
    /// </summary>
    /// <param name="e"></param>
    public override void RolePlayerChanged(RolePlayerChangedEventArgs e)
    {
      // We are only interested in the type
      if (e.DomainRole.Id == PropertyHasType.TypeDomainRoleId)
      {
        PropertyHasType relationship =
           e.ElementLink as PropertyHasType;
        DomainType newType = e.NewRolePlayer as DomainType;
        DomainType oldType = e.OldRolePlayer as DomainType;
        DomainProperty property = relationship.Property;

         // We write about the Type change in the debugguer
        Debug.WriteLine(string.Format("The type of the Domain property '{0}' of domain class '{1}' changed from '{2}' to '{3}'",
          property.Name,
          property.Class.Name,
          oldType.GetFullName(false),
          newType.GetFullName(false))
} }  }  );
```

Le code suivant implémente un modèle simple. Créez un nouveau GUID pour remplacer l’espace réservé.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.DslDefinition;
namespace Fabrikam.SimpleDslDesignerExtension
{
    /// <summary>
    /// Simplest possible domain model
    /// needed only for extension rules.
    /// </summary>
    [DomainObjectId(SimpleDomainModelExtension.DomainModelId)]
    public class SimpleDomainModelExtension : DomainModel
    {
        // Id of this domain model extension
        // Please replace this with a new GUID:
        public const string DomainModelId =
                  "00000000-0000-0000-0000-000000000000";

        /// <summary>
        /// Constructor for the domain model extension
        /// </summary>
        /// <param name="store">Store in which the domain model will be loaded</param>
        public SimpleDomainModelExtension(Store store)
            : base(store, new Guid(SimpleDomainModelExtension.DomainModelId))
        {

        }

        /// <summary>
        /// Rules brought by this domain model extension
        /// </summary>
        /// <returns></returns>
        protected override System.Type[] GetCustomDomainModelTypes()
        {
            return new Type[] {
                     typeof(DomainPropertyTypeChangedRule)
                              };
        }
    }

    /// <summary>
    /// Provider for the DomainModelExtension
    /// </summary>
    [Export(typeof(DomainModelExtensionProvider))]    [ProvidesExtensionToDomainModel(typeof(DslDefinitionModelDomainModel))]
    public class SimpleDomainModelExtensionProvider
          : DomainModelExtensionProvider
    {
        /// <summary>
        /// Extension model type
        /// </summary>
        public override Type DomainModelType
        {
            get
            {
                return typeof(SimpleDomainModelExtension);
            }
        }

    }
}
```