---
title: Extension de votre DSL à l'aide de MEF
description: Découvrez comment vous pouvez étendre votre langage spécifique à un domaine (DSL) à l’aide de la Managed Extensibility Framework (MEF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3a4572a7210203d6c7525a278430210c954c3405
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388878"
---
# <a name="extend-your-dsl-by-using-mef"></a>Extension de votre DSL à l'aide de MEF

Vous pouvez étendre votre langage spécifique à un domaine (DSL) à l’aide de Managed Extensibility Framework (MEF). Vous ou d’autres développeurs serez en mesure d’écrire des extensions pour le DSL sans modifier la définition DSL et le code du programme. Ces extensions incluent les commandes de menu, les gestionnaires de glisser-déplacer et la validation. Les utilisateurs peuvent installer votre DSL, puis installer éventuellement des extensions pour celui-ci.

En outre, lorsque vous activez MEF dans votre DSL, il peut être plus facile d’écrire certaines des fonctionnalités de votre DSL, même si elles sont toutes générées avec le DSL.

Pour plus d’informations sur MEF, consultez [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-enable-your-dsl-to-be-extended-by-mef"></a>Pour permettre l’extension de votre DSL par MEF

1. Créez un dossier nommé **MefExtension** dans le projet **DslPackage** . Ajoutez-y les fichiers suivants :

     Nom du fichier : `CommandExtensionVSCT.tt`

    > [!IMPORTANT]
    > Définissez le GUID dans ce fichier pour qu’il soit identique au GUID CommandSetId défini dans DslPackage\GeneratedCode\Constants.tt

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#
    // CmdSet Guid must be defined before master template is included
    // This Guid must be kept synchronized with the CommandSetId Guid in Constants.tt
    Guid guidCmdSet = new Guid ("00000000-0000-0000-0000-000000000000");
    string menuidCommandsExtensionBaseId="0x4000";
    #>
    <#@ include file="DslPackage\CommandExtensionVSCT.tt" #>
    ```

    Nom du fichier : `CommandExtensionRegistrar.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\CommandExtensionRegistrar.tt" #>
    ```

    Nom du fichier : `ValidationExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionEnablement.tt" #>
    ```

    Nom du fichier : `ValidationExtensionRegistrar.tt`

    Si vous ajoutez ce fichier, vous devez activer la validation dans votre DSL en utilisant au moins l’un des commutateurs dans **EditorValidation** dans l’Explorateur DSL.

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\ValidationExtensionRegistrar.tt" #>
    ```

    Nom du fichier : `PackageExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="DslPackage\PackageExtensionEnablement.tt" #>
    ```

2. Créez un dossier nommé **MefExtension** dans le projet **DSL** . Ajoutez-y les fichiers suivants :

     Nom du fichier : `DesignerExtensionMetaDataAttribute.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\DesignerExtensionMetadataAttribute.tt" #>
    ```

    Nom du fichier : `GestureExtensionEnablement.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionEnablement.tt" #>
    ```

    Nom du fichier : `GestureExtensionController.tt`

    ```
    <#@ Dsl processor="DslDirectiveProcessor" requires="fileName='..\..\Dsl\DslDefinition.dsl'" #>
    <#@ include file="Dsl\GestureExtensionController.tt" #>
    ```

3. Ajoutez la ligne suivante au fichier existant nommé **DslPackage\Commands.vsct**:

    ```xml
    <Include href="MefExtension\CommandExtensionVSCT.vsct"/>
    ```

    Insérez la ligne après la `<Include>` directive existante.

4. Ouvrez *DslDefinition. DSL*.

5. Dans l’Explorateur DSL, sélectionnez **Editor\Validation**.

6. Dans le Fenêtre Propriétés, assurez-vous qu’au moins une des propriétés nommées **utilise** est `true` .

7. Dans la barre d’outils **Explorateur de solutions** , cliquez sur **transformer tous les modèles**.

     Les fichiers des filiales s’affichent sous chacun des fichiers que vous avez ajoutés.

8. Générez et exécutez la solution pour vérifier qu’elle fonctionne toujours.

Votre DSL est désormais compatible MEF. Vous pouvez écrire des commandes de menu, des gestionnaires de mouvements et des contraintes de validation en tant qu’extensions MEF. Vous pouvez écrire ces extensions dans votre solution DSL avec un autre code personnalisé. En outre, vous ou d’autres développeurs pouvez écrire des extensions Visual Studio distinctes qui étendent votre DSL.

## <a name="create-an-extension-for-a-mef-enabled-dsl"></a>Créer une extension pour un DSL compatible MEF

Si vous avez accès à un DSL compatible MEF créé par vous-même ou quelqu’un d’autre, vous pouvez écrire des extensions pour celui-ci. Les extensions peuvent être utilisées pour ajouter des commandes de menu, des gestionnaires de mouvements ou des contraintes de validation. Pour créer ces extensions, vous utilisez une solution d’extension Visual Studio (VSIX). La solution se compose de deux parties : un projet de bibliothèque de classes qui génère l’assembly de code et un projet VSIX qui empaquette l’assembly.

### <a name="to-create-a-dsl-extension-vsix"></a>Pour créer une extension DSL VSIX

1. Créez un projet de **Bibliothèque de classes**.

2. Dans le nouveau projet, ajoutez une référence à l’assembly du DSL.

   - Cet assembly a généralement un nom qui se termine par « .Dsl.dll ».

   - Si vous avez accès au projet DSL, vous pouvez trouver le fichier d’assembly sous le **répertoire \\ DSL \\ \* bin** .

   - Si vous avez accès au fichier VSIX DSL, vous pouvez trouver l’assembly en remplaçant l’extension de nom de fichier du fichier VSIX par « .zip ». Décompressez le fichier .zip.

3. Ajoutez des références aux assemblys .NET suivants :

   - Microsoft.VisualStudio.Modeling.Sdk.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0.dll

   - Microsoft.VisualStudio.Modeling.Sdk.Shell.11.0.dll

   - System.ComponentModel.Composition.dll

   - System.Windows.Forms.dll

4. Créez un projet de **projet VSIX** .

5. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet VSIX, puis choisissez **définir comme projet de démarrage**.

6. Dans le nouveau projet, ouvrez **source. extension. vsixmanifest**.

7. Cliquez sur **Ajouter du contenu**. Dans la boîte de dialogue, définissez **type de contenu** sur **Composant MEF** et **projet source** sur votre projet de bibliothèque de classes.

8. Ajoutez une référence VSIX au DSL.

   1. Dans **source. extension. vsixmanifest**, cliquez sur **Ajouter une référence** .

   2. Dans la boîte de dialogue, cliquez sur **Ajouter une charge utile** , puis recherchez le fichier VSIX du DSL. Le fichier VSIX est créé dans la solution DSL, dans **DslPackage \\ bin \\ \***.

       Cela permet aux utilisateurs d’installer le DSL et votre extension en même temps. Si l’utilisateur a déjà installé le DSL, seule votre extension sera installée.

9. Passez en revue et mettez à jour les autres champs de **source. extension. vsixmanifest**. Cliquez sur **Sélectionner des éditions** et vérifiez que les éditions de Visual Studio appropriées sont définies.

10. Ajoutez du code au projet de bibliothèque de classes. Utilisez les exemples de la section suivante comme guide.

     Vous pouvez ajouter n’importe quel nombre de classes de commande, de mouvement et de validation.

11. Pour tester l’extension, appuyez sur **F5**. Dans l’instance expérimentale de Visual Studio, créez ou ouvrez un exemple de fichier DSL.

## <a name="writing-mef-extensions-for-dsls"></a>Écriture d’extensions MEF pour DSL

Vous pouvez écrire des extensions dans le projet de code de l’assembly d’une solution d’extension DSL distincte. Vous pouvez également utiliser MEF dans votre projet DslPackage, comme un moyen pratique d’écrire des commandes, des mouvements et du code de validation dans le cadre de la DSL.

### <a name="menu-commands"></a>Commandes de menu

Pour écrire une commande de menu, définissez une classe qui implémente <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ICommandExtension> et préfixe la classe avec l’attribut défini dans votre DSL, nommé *YourDsl* `CommandExtension` . Vous pouvez écrire plusieurs classes de commandes de menu.

`QueryStatus()` est appelé chaque fois que l’utilisateur clique avec le bouton droit sur le diagramme. Il doit inspecter la sélection actuelle et définir `command.Enabled` pour indiquer quand la commande est applicable.

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl; // My DSL
using Company.MyDsl.ExtensionEnablement; // My DSL
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement; // IVsSelectionContext
using Microsoft.VisualStudio.Modeling.ExtensionEnablement; // ICommandExtension

namespace MyMefExtension
{
  // Defined in Dsl\MefExtension\DesignerExtensionMetaDataAttribute.cs:
  [MyDslCommandExtension]
  public class MyCommandClass : ICommandExtension
  {
    /// <summary>
    /// Provides access to current document and selection.
    /// </summary>
    [Import]
    IVsSelectionContext SelectionContext { get; set; }

    /// <summary>
    /// Called when the user selects this command.
    /// </summary>
    /// <param name="command"></param>
    public void Execute(IMenuCommand command)
    {
      // Transaction is required if you want to update elements.
      using (Transaction t = SelectionContext.CurrentStore
              .TransactionManager.BeginTransaction("fix names"))
      {
        foreach (ExampleShape shape in SelectionContext.CurrentSelection)
        {
          ExampleElement element = shape.ModelElement as ExampleElement;
          element.Name = element.Name + " !";
        }
        t.Commit();
      }
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines whether the command should appear.
    /// This method should set command.Enabled and command.Visible.
    /// </summary>
    /// <param name="command"></param>
    public void QueryStatus(IMenuCommand command)
    {
      command.Enabled =
        command.Visible = (SelectionContext.CurrentSelection.OfType<ExampleShape>().Count() > 0);
    }

    /// <summary>
    /// Called when the user right-clicks the diagram.
    /// Determines the text of the command in the menu.
    /// </summary>
    public string Text
    {
      get { return "My menu command"; }
    }
  }
}
```

### <a name="gesture-handlers"></a>Gestionnaires de mouvements

Un gestionnaire de mouvements peut gérer des objets glissés sur le diagramme depuis n’importe quel endroit, à l’intérieur ou à l’extérieur de Visual Studio. L’exemple suivant permet à l’utilisateur de faire glisser des fichiers de l’Explorateur Windows vers le diagramme. Il crée des éléments qui contiennent les noms de fichiers.

Vous pouvez écrire des gestionnaires pour gérer les opérations de déplacement à partir d’autres modèles DSL et de modèles UML. Pour plus d’informations, consultez [Comment : ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md).

```csharp
using System.ComponentModel.Composition;
using System.Linq;
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling; // Transactions
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;

namespace MefExtension
{
  [MyDslGestureExtension]
  class MyGestureExtension : IGestureExtension
  {
    public void OnDoubleClick(ShapeElement targetElement, DiagramPointEventArgs diagramPointEventArgs)
    {
      System.Windows.Forms.MessageBox.Show("double click!");
    }

    /// <summary>
    /// Called when the user drags anything over the diagram.
    /// Return true if the dragged object can be dropped on the current target.
    /// </summary>
    /// <param name="targetMergeElement">The shape or diagram that the mouse is currently over</param>
    /// <param name="diagramDragEventArgs">Data about the dragged element.</param>
    /// <returns></returns>
    public bool CanDragDrop(ShapeElement targetMergeElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      // This handler only allows items to be dropped onto the diagram:
      return targetMergeElement is MefDsl2Diagram &&
      // And only accepts files dragged from Windows Explorer:
        diagramDragEventArgs.Data.GetFormats().Contains("FileNameW");
    }

    /// <summary>
    /// Called when the user drops an item onto the diagram.
    /// </summary>
    /// <param name="targetDropElement"></param>
    /// <param name="diagramDragEventArgs"></param>
    public void OnDragDrop(ShapeElement targetDropElement, DiagramDragEventArgs diagramDragEventArgs)
    {
      MefDsl2Diagram diagram = targetDropElement as MefDsl2Diagram;
      if (diagram == null) return;

      // This handler only accepts files dragged from Windows Explorer:
      string[] draggedFileNames = diagramDragEventArgs.Data.GetData("FileNameW") as string[];
      if (draggedFileNames == null || draggedFileNames.Length == 0) return;

      using (Transaction t = diagram.Store.TransactionManager.BeginTransaction("file names"))
      {
        // Create an element to represent each file:
        foreach (string fileName in draggedFileNames)
        {
          ExampleElement element = new ExampleElement(diagram.ModelElement.Partition);
          element.Name = fileName;

          // This method of adding the new element allows the position
          // of the shape to be specified:
          ElementGroup group = new ElementGroup(element);
          diagram.ElementOperations.MergeElementGroupPrototype(
            diagram, group.CreatePrototype(), PointD.ToPointF(diagramDragEventArgs.MousePosition));
        }
        t.Commit();
      }
    }
  }
}
```

### <a name="validation-constraints"></a>Contraintes de validation

Les méthodes de validation sont marquées par l' `ValidationExtension` attribut généré par le DSL, ainsi que par <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> . La méthode peut apparaître dans toute classe qui n’est pas marquée par un attribut.

Pour plus d’informations, consultez [validation dans un langage de Domain-Specific](../modeling/validation-in-a-domain-specific-language.md).

```csharp
using Company.MyDsl;
using Company.MyDsl.ExtensionEnablement;
using Microsoft.VisualStudio.Modeling.Validation;

namespace MefExtension
{
  class MyValidationExtension // Can be any class.
  {
    // SAMPLE VALIDATION METHOD.
    // All validation methods have the following attributes.

    // Specific to the extended DSL:
    [MyDslValidationExtension]

    // Determines when validation is applied:
    [ValidationMethod(
       ValidationCategories.Save
     | ValidationCategories.Open
     | ValidationCategories.Menu)]

    /// <summary>
    /// When validation is executed, this method is invoked
    /// for every element in the model that is an instance
    /// of the second parameter type.
    /// </summary>
    /// <param name="context">For reporting errors</param>
    /// <param name="elementToValidate"></param>
    private void ValidateClassNames
      (ValidationContext context,
       // Type determines to what elements this will be applied:
       ExampleElement elementToValidate)
    {
      // Write code here to test values and links.
      if (elementToValidate.Name.IndexOf(' ') >= 0)
      {
        // Log any unacceptable values:
        context.LogError(
          // Description:
          "Name must not contain spaces"
          // Error code unique to this type of error:
          , "MyDsl001"
          // Element to highlight when user double-clicks error:
          , elementToValidate);
} } } }
```

## <a name="see-also"></a>Voir aussi

- [Publication d’extensions Visual Studio](../extensibility/shipping-visual-studio-extensions.md)
- [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index)
- [Guide pratique pour ajouter un gestionnaire de glisser-déplacer](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Validation dans un langage spécifique à un domaine](../modeling/validation-in-a-domain-specific-language.md)
