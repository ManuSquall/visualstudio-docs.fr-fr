---
title: Ajouter des propriétés personnalisées à des diagrammes de dépendance
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 9a3d16fda5b6a4a21ea60aaf2af3d35678e998e4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54979476"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Ajouter des propriétés personnalisées à des diagrammes de dépendance

Lorsque vous écrivez le code d’extension pour des diagrammes de dépendance, vous pouvez stocker des valeurs avec n’importe quel élément sur un diagramme de dépendances. Les valeurs persisteront lorsque le diagramme est enregistré et rouvert. Vous pouvez également faire apparaître ces propriétés dans le **propriétés** fenêtre afin que les utilisateurs peuvent voir et les modifier. Par exemple, vous pouvez permettre aux utilisateurs de spécifier une expression régulière pour chaque couche, et écrire le code de validation pour vérifier que les noms de classes dans chaque couche sont conformes au modèle spécifié par l’utilisateur.

## <a name="non-visible-properties"></a>Propriétés non visibles

Si vous souhaitez simplement votre code associe des valeurs pour n’importe quel élément dans un diagramme de dépendances, vous n’avez pas besoin de définir un composant MEF. Il existe un dictionnaire nommé `Properties` dans <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>. Ajoutez simplement les valeurs marshalables au dictionnaire d’un élément de couche. Elles seront enregistrées en tant que partie du diagramme de dépendance. Pour plus d’informations, consultez [Parcourir et mise à jour des modèles dans le code de programme de couche](../modeling/navigate-and-update-layer-models-in-program-code.md).

## <a name="editable-properties"></a>Propriétés modifiables

**Préparation initiale**

> [!IMPORTANT]
> Pour faire apparaître les propriétés, apportez la modification suivante sur chaque ordinateur où vous souhaitez que les propriétés de couche soient visibles :
>
> 1. Exécutez le bloc-notes à l’aide de **exécuter en tant qu’administrateur**. Ouvrez *%ProgramFiles%\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. À l’intérieur de la **contenu** élément, ajoutez :
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
> 3. Sous le **Visual Studio Tools** section du Visual Studio application menu Démarrer, ouvrez **invite de commandes développeur**. Entrez :
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Redémarrez Visual Studio.

**Assurez-vous que votre code se trouve dans un projet VSIX**

Si votre propriété fait partie d’une commande, de mouvement ou projet de validation, vous ne devez rien à ajouter. Le code de votre propriété personnalisée doit être défini dans un projet d'extensibilité Visual Studio défini en tant que composant MEF. Pour plus d’informations, consultez [ajouter des commandes et des mouvements aux diagrammes de dépendance](../modeling/add-commands-and-gestures-to-layer-diagrams.md) ou [ajouter la validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Définir la propriété personnalisée**

Pour créer une propriété personnalisée, définissez une classe comme suit :

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Vous pouvez définir des propriétés sur <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> ou l'une de ses classes dérivées, notamment :

-   `ILayerModel` : le modèle

-   `ILayer` : chaque couche

-   `ILayerDependencyLink` : les liens entre les couches

-   `ILayerComment`

-   `ILayerCommentLink`

## <a name="example"></a>Exemple

Le code suivant est un descripteur de propriété personnalisé classique. Il définit une propriété booléenne sur le modèle de couche (`ILayerModel`) qui permet à l'utilisateur de fournir des valeurs pour une méthode de validation personnalisée.

```csharp
using System;
using System.ComponentModel.Composition;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;

namespace MyNamespace
{
  /// <summary>
  /// Custom properties are added to the Layer Designer via a custom
  /// Property Descriptor. We have to export this Property Descriptor
  /// using MEF to make it available in the Layer Designer.
  /// </summary>
  [Export(typeof(IPropertyExtension))]
  public class AllTypesMustBeReferencedProperty
      : PropertyExtension<ILayerModel>
  {
    /// <summary>
    /// Each custom property must have a unique name.
    /// Usually we use the full name of this class.
    /// </summary>
    public static readonly string FullName =
      typeof(AllTypesMustBeReferencedProperty).FullName;

    /// <summary>
    /// Construct the property. Notice the use of FullName.
    /// </summary>
    public AllTypesMustBeReferencedProperty()
            : base(FullName)
    {  }

    /// <summary>
    /// The display name is shown in the Properties window.
    /// We therefore use a localizable resource.
    /// </summary>
    public override string DisplayName
    {
      get { return Strings.AllTypesMustBeReferencedDisplayName; }
    }

    /// <summary>
    /// Description shown at the bottom of the Properties window.
    /// We use a resource string for easier localization.
    /// </summary>
    public override string Description
    {
      get { return Strings.AllTypesMustBeReferencedDescription; }
    }

    /// <summary>
    /// This is called to set a new value for this property. We must
    /// throw an exception if the value is invalid.
    /// </summary>
    /// <param name="component">The target ILayerElement</param>
    /// <param name="value">The new value</param>
    public override void SetValue(object component, object value)
    {
      ValidateValue(value);
      base.SetValue(component, value);
    }
    /// <summary>
    /// Helper to validate the value.
    /// </summary>
    /// <param name="value">The value to validate</param>
    private static void ValidateValue(object value)
    {  }

    public override Type PropertyType
    { get { return typeof(bool); } }

    /// <summary>
    /// The segment label of the properties window.
    /// </summary>
    public override string Category
    {
      get
      {
        return Strings.AllTypesMustBeReferencedCategory;
      }
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

- [Extension des diagrammes de dépendance](../modeling/extend-layer-diagrams.md)
