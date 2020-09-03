---
title: BoundsRules contraindre l’emplacement et la taille de la forme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7d660189ede0848216eb44d6ef49fe9c93a06ec8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672728"
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Définition de l'emplacement et de la taille de la forme par la classe BoundsRules
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Une *règle de limites* est une classe qui définit des limites sur la taille et l’emplacement d’une forme. Il fournit une méthode appelée à plusieurs reprises lorsqu’un utilisateur fait glisser une forme ou les angles ou les côtés d’une forme.

 L’exemple suivant limite la taille d’une forme rectangulaire à une barre de taille fixe, horizontale ou verticale. Lorsque l’utilisateur fait glisser les angles ou les côtés, le contour s’incline entre les deux configurations autorisées de hauteur et de largeur.

 La règle de limites est une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> . Une instance de la règle est créée dans la forme :

```
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

 Notez que l’emplacement et la taille peuvent être limités si vous le souhaitez.

## <a name="see-also"></a>Voir aussi
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules> [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md)
