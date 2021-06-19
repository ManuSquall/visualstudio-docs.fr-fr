---
title: Ajouter des propriétés personnalisées à des diagrammes de dépendance
description: Découvrez comment vous pouvez stocker des valeurs avec n’importe quel élément d’un diagramme de dépendances lorsque vous écrivez du code d’extension pour des diagrammes de dépendance.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dependency diagrams, adding custom properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 70588a2d472a1170b58911eece4fa70831064f72
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389850"
---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Ajouter des propriétés personnalisées à des diagrammes de dépendance

Lorsque vous écrivez du code d’extension pour des diagrammes de dépendance, vous pouvez stocker des valeurs avec n’importe quel élément d’un diagramme de dépendance. Les valeurs persisteront lorsque le diagramme est enregistré et rouvert. Vous pouvez également faire en sorte que ces propriétés s’affichent dans la fenêtre **Propriétés** afin que les utilisateurs puissent les afficher et les modifier. Par exemple, vous pouvez permettre aux utilisateurs de spécifier une expression régulière pour chaque couche, et écrire le code de validation pour vérifier que les noms de classes dans chaque couche sont conformes au modèle spécifié par l’utilisateur.

## <a name="non-visible-properties"></a>Propriétés non visibles

Si vous souhaitez simplement que votre code joigne des valeurs à n’importe quel élément d’un diagramme de dépendance, vous n’avez pas besoin de définir un composant MEF. Il existe un dictionnaire nommé `Properties` dans [ILayerElement](/previous-versions/ff644511(v=vs.140)). Ajoutez simplement les valeurs marshalables au dictionnaire d'un élément de couche. Ils seront enregistrés dans le cadre du diagramme de dépendance.

## <a name="editable-properties"></a>Propriétés modifiables

**Préparation initiale**

> [!IMPORTANT]
> Pour afficher les propriétés, apportez les modifications suivantes sur chaque ordinateur sur lequel vous souhaitez que les propriétés de couche soient visibles :
>
> 1. Exécutez le bloc-notes en utilisant **exécuter en tant qu’administrateur**. Ouvrez *%ProgramFiles%\Microsoft Visual Studio [version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest*.
> 2. À l’intérieur de l’élément de **contenu** , ajoutez :
>
>     ```xml
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>
>     ```
>
> 3. Dans la section **Visual Studio Tools** du menu Démarrer de l’application Visual Studio, ouvrez **invite de commandes développeur**. Entrez :
>
>      `devenv /rootSuffix /updateConfiguration`
>
>      `devenv /rootSuffix Exp /updateConfiguration`
> 4. Démarrez Visual Studio.

**Vérifier que votre code se trouve dans un projet VSIX**

Si votre propriété fait partie d’une commande, d’un mouvement ou d’un projet de validation, vous n’avez rien à ajouter. Le code de votre propriété personnalisée doit être défini dans un projet d'extensibilité Visual Studio défini en tant que composant MEF. Pour plus d’informations, consultez [Ajouter des commandes et des mouvements aux diagrammes de dépendances](../modeling/add-commands-and-gestures-to-layer-diagrams.md) ou [Ajouter une validation d’architecture personnalisée aux diagrammes de dépendance](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

**Définir la propriété personnalisée**

Pour créer une propriété personnalisée, définissez une classe comme suit :

```csharp
[Export(typeof(IPropertyExtension))]
public class MyProperty : PropertyExtension<ILayerElement>
{
  // Implement the interface.
}
```

Vous pouvez définir des propriétés sur [ILayerElement](/previous-versions/ff644511(v=vs.140)) ou sur l’une de ses classes dérivées, notamment :

- `ILayerModel` -le modèle

- `ILayer` -chaque couche

- `ILayerDependencyLink` -les liens entre les couches

- `ILayerComment`

- `ILayerCommentLink`

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

- [Étendre des diagrammes de dépendance](../modeling/extend-layer-diagrams.md)
