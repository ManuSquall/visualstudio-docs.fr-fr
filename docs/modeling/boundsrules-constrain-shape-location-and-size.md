---
title: Définition de l'emplacement et de la taille de la forme par la classe BoundsRules
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 449fb0c12b11163ba0ceca981e66a7da0c399e1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950197"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Définition de l'emplacement et de la taille de la forme par la classe BoundsRules

Un *règle de limites* est une classe qui définit les limites de la taille et l’emplacement d’une forme. Il fournit une méthode qui est appelée à plusieurs reprises pendant que l’utilisateur fait glisser une forme ou angles ou sur les côtés d’une forme.

L’exemple suivant force une forme rectangulaire à une barre de taille fixe, horizontale ou verticale. Lorsque l’utilisateur fait glisser les angles ou sur les côtés, le contour renverse entre les deux configurations autorisées de hauteur et largeur.

Les limites de règle est une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Une instance de la règle est créée dans la forme :

```csharp
using Microsoft.VisualStudio.Modeling.Diagrams; ...

public partial class BarShape
{
  /// <summary>
  /// Rule invoked when the user is resizing a shape.
  /// </summary>
  public override BoundsRules BoundsRules
  { get { return new BarBoundsRule(); } }
}

/// <summary>
/// Rule invoked when the user is changing a shape's outline.
/// Provides real-time mouse rubber-band feedback, so must work fast.
/// </summary>
public class BarBoundsRule: BoundsRules
{
  public override RectangleD GetCompliantBounds
     (ShapeElement shape, RectangleD proposedBounds)
  {
    double thickness = 0.1;
    if (proposedBounds.Height > proposedBounds.Width)
    {
      // There is a minimum width for a shape; the width
      // will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
            new SizeD(thickness, proposedBounds.Height));
    }
    else
    {
      // There is a minimum height for a shape; the
      // height will actually be set to the lesser of
      // thickness and that minimum.
      return new RectangleD(proposedBounds.Location,
         new SizeD(proposedBounds.Width, thickness));
} } }
```

Notez que l’emplacement et la taille peuvent être contraint si vous le souhaitez.

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>
- [Répondre aux changements et les propager](../modeling/responding-to-and-propagating-changes.md)