---
title: Personnalisation des champs de texte et Image | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: a7259fc0-5afa-4356-b27e-5641e01628a9
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5069f6d45d72606bce7de2866c6328864fcde21f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433247"
---
# <a name="customizing-text-and-image-fields"></a>Personnalisation des champs de texte et d'image
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous définissez un décorateur de texte dans une forme, il est représenté par un champ de texte. Pour obtenir des exemples de l’initialisation de TextFields et autres dont ShapeFields, inspecter Dsl\GeneratedCode\Shapes.cs dans votre solution DSL.  
  
 Un champ de texte est un objet qui gère une zone dans une forme, telles que l’espace affecté à une étiquette. Une instance de TextField est partagée entre plusieurs formes de la même classe. L’instance TextField ne stocke pas le texte de l’étiquette séparément pour chaque instance : au lieu de cela, le `GetDisplayText(ShapeElement)` méthode prend la forme en tant que paramètre et peut rechercher le texte dépendant de l’état actuel de la forme et son élément de modèle.  
  
## <a name="how-the-appearance-of-a-text-field-is-determined"></a>Détermination de l’apparence d’un champ de texte  
 Le `DoPaint()` méthode est appelée à affiche le champ sur l’écran. Vous pouvez soit remplacer la valeur par défaut `DoPaint(),` ou vous pouvez remplacer certaines des méthodes qu’elle appelle. La version simplifiée suivante de méthodes par défaut peut vous aider à comprendre comment substituer le comportement par défaut :  
  
```  
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
// To change the brush for every field, change the shape’s styleset.   
// To customize to a brush in the style set, override GetTextBrushId.  
// To change the brush to non-standard color, override this.  
// Should take account of whether selected.   
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)  
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }  
  
// Brush ID selects a brush from a StyleSet.  
// Either return a member of DiagramBrushes   
// or add your own brush to the shape or application’s styleset.  
// Override this to change dynamically or per instance.  
// To change statically, just assign to default values.   
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)  
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId  
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;  
}  
  
// Font determines the shape and size of the text.  
// To change the font for every field, change the shape’s styleset.   
// To customize to a font in the style set, override GetFontId.  
// To change the font to a non-standard font, override this.   
public virtual Font GetFont(ShapeElement shape)  
{ return shape.StyleSet.GetFont(GetFontId(shape)); }  
  
// Selects a font from a styleset.  
// Either return a member of DiagramFonts or   
// add your own font to the shape or application’s styleset.  
// To change statically for all instances of this field,   
// assign to DefaultFontId.  
// To change per shape or dynamically, override this.   
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)  
{ return DefaultFontId; }  
  
```  
  
 Il existe plusieurs autres paires de `Get` méthodes et `Default` propriétés, telles que `DefaultMultipleLine/GetMultipleLine()`. Vous pouvez affecter une valeur à la propriété par défaut pour modifier la valeur pour toutes les instances du champ de forme. Pour rendre la valeur varient d’instance d’une forme à un autre ou dépend de l’état de la forme ou son élément de modèle, vous devez remplacer le `Get` (méthode).  
  
## <a name="static-customizations"></a>Personnalisations statiques  
 Si vous souhaitez remplacer toutes les instances de ce champ de forme, déterminez d’abord si vous pouvez définir la propriété dans la définition DSL. Par exemple, vous pouvez définir la taille de police et de style dans la fenêtre Propriétés.  
  
 Dans le cas contraire, puis remplacer le `InitializeShapeFields` méthode de votre classe de forme, puis lui attribuer une valeur appropriés `Default...` propriété du champ de texte.  
  
> [!WARNING]
> Pour remplacer `InitializeShapeFields()`, vous devez définir le **génère une Double dérivée** la propriété de la classe shape `true` dans la définition DSL.  
  
 Dans cet exemple, une forme a un champ de texte qui sera utilisé pour les commentaires de l’utilisateur. Nous souhaitons utiliser la police de commentaire standard. S’agissant d’une police standard à partir du jeu de style, nous pouvons définir l’id de police par défaut :  
  
```  
  
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
 Pour rendre l’apparence varient dépend de l’état d’une forme ou son élément de modèle, dérivez votre propre sous-classe de `TextField` et substituez une ou plusieurs `Get...` méthodes. Vous devez également substituer la méthode de InitializeShapeFields votre forme et remplacez l’instance de l’objet TextField par une instance de votre propre classe.  
  
 L’exemple suivant met la police d’un champ de texte dépendant de l’état d’une propriété de domaine booléenne de la forme élément de modèle.  
  
 Pour exécuter cet exemple de code, créez une solution DSL à l’aide du modèle de langage Minimal. Ajouter une propriété de domaine booléenne `AlternateState` à la classe de domaine ExampleElement. Ajouter un élément décoratif d’icône à la classe ExampleShape et définissez son image dans un fichier bitmap. Cliquez sur **transformer tous les modèles**. Ajoutez un nouveau fichier de code dans le projet DSL et insérez le code suivant.  
  
 Pour tester le code, appuyez sur F5 et, dans la solution de débogage, ouvrez un exemple de diagramme. L’état par défaut de l’icône doit apparaître. Sélectionnez la forme et dans la fenêtre Propriétés, modifiez la valeur de la **AlternateState** propriété. La police du nom de l’élément doit changer.  
  
```  
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
  
## <a name="style-sets"></a>Jeux de style  
 L’exemple précédent montre comment vous pouvez modifier le champ de texte pour toute police qui n’est disponible. Toutefois, une méthode préférable consiste à remplacer par un ensemble de styles qui est associé à la forme ou à l’application. Pour ce faire, vous substituez <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> ou GetTextBrushId().  
  
 Vous pouvez également envisager de modifier le jeu de styles de la forme en substituant <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>. Cela a pour effet de modifier les polices et les pinceaux pour tous les champs de forme.  
  
## <a name="customizing-image-fields"></a>Personnalisation des champs d’Image  
 Lorsque vous définissez un élément décoratif d’image dans une forme, et lorsque vous définissez une forme d’image, la zone dans laquelle la forme est affichée est gérée par un ImageField. Pour obtenir des exemples de l’initialisation de ImageFields et autres dont ShapeFields, inspecter Dsl\GeneratedCode\Shapes.cs dans votre solution DSL.  
  
 Un ImageField est un objet qui gère une zone dans une forme, telles que l’espace affecté à un élément décoratif. Une instance de l’ImageField est partagée entre plusieurs formes de la même classe de forme. L’instance de l’ImageField ne stocke pas d’une image distincte pour chaque forme : au lieu de cela, le `GetDisplayImage(ShapeElement)` méthode prend la forme en tant que paramètre et peut rechercher l’image dépend de l’état actuel de la forme et son élément de modèle.  
  
 Si vous souhaitez un comportement spécial tel qu’une image de variable, vous pouvez créer votre propre classe dérivée de ImageField.  
  
#### <a name="to-create-a-subclass-of-imagefield"></a>Pour créer une sous-classe de ImageField  
  
1. Définir le **génère une Double dérivée** propriété de la classe de forme parent dans votre définition DSL.  
  
2. Remplacer le `InitializeShapeFields` méthode de votre classe de forme.  
  
    - Créer un nouveau fichier de code dans le projet DSL et écrire une définition de classe partielle pour la classe shape. Remplacer la définition de la méthode.  
  
3. Inspecter le code de `InitializeShapeFields` dans DSL\GeneratedCode\Shapes.cs.  
  
     Dans votre méthode de substitution, appelez la méthode de base, puis créez une instance de votre propre classe de champ d’image. Utilisez-le pour remplacer le champ d’image standard dans le `shapeFields` liste.  
  
## <a name="dynamic-icons"></a>Icônes dynamiques  
 Cet exemple montre une icône Modifier dépend de l’état de la forme élément de modèle.  
  
> [!WARNING]
> Cet exemple montre comment rendre un élément décoratif d’image dynamique. Mais si vous souhaitez uniquement basculer entre une ou deux images selon l’état d’une variable de modèle, il est plus simple créer plusieurs décorateurs d’image, les localise dans la même position sur la forme et puis définissez le filtre de visibilité à dépendre des valeurs spécifiques du modèle variable. Pour définir ce filtre, sélectionnez le mappage de forme dans la définition DSL, ouvrez la fenêtre Détails DSL, cliquez sur l’onglet éléments décoratifs.  
  
 Pour exécuter cet exemple de code, créez une solution DSL à l’aide du modèle de langage Minimal. Ajouter une propriété de domaine booléenne `AlternateState` à la classe de domaine ExampleElement. Ajouter un élément décoratif d’icône à la classe ExampleShape et définissez son image dans un fichier bitmap. Cliquez sur **transformer tous les modèles**. Ajoutez un nouveau fichier de code dans le projet DSL et insérez le code suivant.  
  
 Pour tester le code, appuyez sur F5 et, dans la solution de débogage, ouvrez un exemple de diagramme. L’état par défaut de l’icône doit apparaître. Sélectionnez la forme et dans la fenêtre Propriétés, modifiez la valeur de la **AlternateState** propriété. L’icône doit alors apparaître pivotée à 90 degrés, cette forme.  
  
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
 [Définition de formes et connecteurs](../modeling/defining-shapes-and-connectors.md)   
 [Définition d’une Image d’arrière-plan sur un diagramme](../modeling/setting-a-background-image-on-a-diagram.md)   
 [Navigation et mise à jour d’un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Écriture de code pour personnaliser un langage spécifique à un domaine](../modeling/writing-code-to-customise-a-domain-specific-language.md)
