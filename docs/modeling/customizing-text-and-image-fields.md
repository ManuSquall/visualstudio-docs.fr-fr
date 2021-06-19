---
title: Personnalisation des champs de texte et d'image
description: En savoir plus sur la personnalisation des fichiers texte et image. Sachez également que lorsque vous définissez un élément décoratif de texte dans une forme, il est représenté par un TextField.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f52c4deda5b934a9b55c5ecfeec95ca633edf15e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389265"
---
# <a name="customizing-text-and-image-fields"></a>Personnalisation des champs de texte et d'image
Lorsque vous définissez un élément décoratif de texte dans une forme, il est représenté par un élément TextField. Pour obtenir des exemples d’initialisation de TextFields et d’autres ShapeFields, inspectez Dsl\GeneratedCode\Shapes.cs dans votre solution DSL.

 Un TextField est un objet qui gère une zone dans une forme, telle que l’espace affecté à une étiquette. Une instance TextField est partagée entre de nombreuses formes de la même classe. L’instance TextField ne stocke pas le texte de l’étiquette séparément pour chaque instance : à la place, la `GetDisplayText(ShapeElement)` méthode prend la forme comme paramètre et peut rechercher le texte en fonction de l’état actuel de la forme et de son élément de modèle.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Détermination de l’apparence d’un champ de texte
 La `DoPaint()` méthode est appelée pour afficher le champ à l’écran. Vous pouvez remplacer la valeur par défaut, `DoPaint(),` ou vous pouvez substituer certaines des méthodes qu’elle appelle. La version simplifiée suivante des méthodes par défaut peut vous aider à comprendre comment remplacer le comportement par défaut :

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 Il existe plusieurs autres paires de `Get` méthodes et de `Default` Propriétés, telles que `DefaultMultipleLine/GetMultipleLine()` . Vous pouvez affecter une valeur à la propriété par défaut pour modifier la valeur de toutes les instances du champ de forme. Pour que la valeur varie d’une instance de forme à l’autre, ou dépendante de l’état de la forme ou de son élément de modèle, substituez la `Get` méthode.

## <a name="static-customizations"></a>Personnalisations statiques
 Si vous souhaitez modifier chaque instance de ce champ de forme, déterminez d’abord si vous pouvez définir la propriété dans la définition DSL. Par exemple, vous pouvez définir la taille et le style de la police dans le Fenêtre Propriétés.

 Si ce n’est pas le cas, remplacez la `InitializeShapeFields` méthode de votre classe Shape et assignez une valeur à la `Default...` propriété appropriée du champ de texte.

> [!WARNING]
> Pour remplacer `InitializeShapeFields()` , vous devez affecter à la propriété **génère une double dérivée** de la classe Shape la valeur `true` dans la définition DSL.

 Dans cet exemple, une forme a un champ de texte qui sera utilisé pour les commentaires utilisateur. Nous souhaitons utiliser la police de commentaire standard. Étant donné qu’il s’agit d’une police standard du jeu de styles, nous pouvons définir l’ID de police par défaut :

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>Personnalisations dynamiques
 Pour que l’apparence varie en fonction de l’état d’une forme ou de son élément de modèle, dérivez votre propre sous-classe de `TextField` et substituez une ou plusieurs `Get...` méthodes. Vous devez également substituer la méthode InitializeShapeFields de votre forme et remplacer l’instance de l’TextField par une instance de votre propre classe.

 L’exemple suivant rend la police d’un champ de texte dépendante de l’état d’une propriété de domaine booléenne de l’élément de modèle de la forme.

 Pour exécuter cet exemple de code, créez une solution DSL à l’aide du modèle de langage minimal. Ajoutez une propriété de domaine booléen `AlternateState` à la classe de domaine ExampleElement. Ajoutez un élément décoratif d’icône à la classe ExampleShape et définissez son image sur un fichier bitmap. Cliquez sur **transformer tous les modèles**. Ajoutez un nouveau fichier de code dans le projet DSL et insérez le code suivant.

 Pour tester le code, appuyez sur F5 et, dans la solution de débogage, ouvrez un exemple de diagramme. L’État par défaut de l’icône doit apparaître. Sélectionnez la forme et dans le Fenêtre Propriétés, modifiez la valeur de la propriété **AlternateState** . La police du nom de l’élément doit changer.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>Jeux de styles
 L’exemple précédent montre comment vous pouvez remplacer le champ de texte par une police disponible. Toutefois, une méthode préférable consiste à la remplacer par un ensemble de styles associé à la forme ou à l’application. Pour ce faire, vous devez remplacer <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> ou GetTextBrushId ().

 Vous pouvez également modifier l’ensemble de styles de votre forme en remplaçant <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A> . Cela a pour effet de modifier les polices et les pinceaux pour tous les champs de forme.

## <a name="customizing-image-fields"></a>Personnalisation des champs d’image
 Lorsque vous définissez un élément décoratif d’image dans une forme et que vous définissez une forme d’image, la zone dans laquelle la forme est affichée est gérée par un ImageField. Pour obtenir des exemples d’initialisation de ImageFields et d’autres ShapeFields, inspectez Dsl\GeneratedCode\Shapes.cs dans votre solution DSL.

 Un ImageField est un objet qui gère une zone dans une forme, telle que l’espace affecté à un Decorator. Une instance ImageField est partagée entre de nombreuses formes de la même classe Shape. L’instance ImageField ne stocke pas d’image distincte pour chaque forme : à la place, la `GetDisplayImage(ShapeElement)` méthode prend la forme comme paramètre et peut Rechercher l’image dépendante de l’état actuel de la forme et de son élément de modèle.

 Si vous souhaitez un comportement spécial tel qu’une image de variable, vous pouvez créer votre propre classe dérivée de ImageField.

#### <a name="to-create-a-subclass-of-imagefield"></a>Pour créer une sous-classe de ImageField

1. Définissez la propriété **Derived double** de la classe de forme parente dans votre définition DSL.

2. Remplacez la `InitializeShapeFields` méthode de votre classe Shape.

    - Créez un nouveau fichier de code dans le projet DSL et écrivez une définition de classe partielle pour la classe Shape. Remplacez la définition de méthode ici.

3. Inspecter le code de `InitializeShapeFields` dans DSL\GeneratedCode\Shapes.cs.

     Dans votre méthode override, appelez la méthode de base, puis créez une instance de votre propre classe de champ image. Utilisez cette valeur pour remplacer le champ d’image normal dans la `shapeFields` liste.

## <a name="dynamic-icons"></a>Icônes dynamiques
 Cet exemple rend une modification d’icône dépendante de l’état de l’élément de modèle de la forme.

> [!WARNING]
> Cet exemple montre comment créer un élément décoratif d’image dynamique. Toutefois, si vous souhaitez uniquement basculer entre une ou deux images en fonction de l’état d’une variable de modèle, il est plus simple de créer plusieurs éléments décoratifs d’image, de les localiser à la même position sur la forme, puis de définir le filtre de visibilité pour qu’il dépende de valeurs spécifiques de la variable de modèle. Pour définir ce filtre, sélectionnez le mappage de forme dans la définition DSL, ouvrez la fenêtre Détails DSL, puis cliquez sur l’onglet décorateurs.

 Pour exécuter cet exemple de code, créez une solution DSL à l’aide du modèle de langage minimal. Ajoutez une propriété de domaine booléen `AlternateState` à la classe de domaine ExampleElement. Ajoutez un élément décoratif d’icône à la classe ExampleShape et définissez son image sur un fichier bitmap. Cliquez sur **transformer tous les modèles**. Ajoutez un nouveau fichier de code dans le projet DSL et insérez le code suivant.

 Pour tester le code, appuyez sur F5 et, dans la solution de débogage, ouvrez un exemple de diagramme. L’État par défaut de l’icône doit apparaître. Sélectionnez la forme et dans le Fenêtre Propriétés, modifiez la valeur de la propriété **AlternateState** . L’icône doit ensuite être pivotée à 90 degrés, sur cette forme.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>Voir aussi

- [Définition de formes et de connecteurs](../modeling/defining-shapes-and-connectors.md)
- [Définition d’une image d’arrière-plan dans un diagramme](../modeling/setting-a-background-image-on-a-diagram.md)
- [Navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)