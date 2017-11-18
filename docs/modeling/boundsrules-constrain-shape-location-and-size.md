---
title: Emplacement de la forme et la taille de la classe BoundsRules | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, events
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 8a611bd18cb06b712f671d370bfc26d4dc8cf4f3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="boundsrules-constrain-shape-location-and-size"></a>Définition de l'emplacement et de la taille de la forme par la classe BoundsRules
A *limites règle* est une classe qui définit les limites de la taille et l’emplacement de la forme. Il fournit une méthode qui est appelée à plusieurs reprises pendant que l’utilisateur fait glisser une forme ou angles ou sur les côtés de la forme.  
  
 L’exemple suivant force une forme rectangulaire à une barre de taille fixe, horizontale ou verticale. Lorsque l’utilisateur fait glisser les angles ou sur les côtés, la structure du renverse entre les deux configurations autorisées de hauteur et la largeur.  
  
 Les limites de règle est une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>. Une instance de la règle est créée dans la forme :  
  
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
  
 Notez que l’emplacement et la taille peuvent être contraint si vous le souhaitez.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Propagation et réponse aux modifications](../modeling/responding-to-and-propagating-changes.md)