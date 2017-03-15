---
title: "D&#233;finition de l&#39;emplacement et de la taille de la forme par la classe BoundsRules | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, événements"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# D&#233;finition de l&#39;emplacement et de la taille de la forme par la classe BoundsRules
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*une règle limites* est une classe qui définit des limites sur la taille et l'emplacement d'une forme.  Il fournit une méthode qui est appelée à plusieurs reprises pendant qu'un utilisateur fait glisser une forme ou les angles ou les côtés d'une forme.  
  
 l'exemple suivant contraint une forme rectangulaire pour être une barre de taille fixe, horizontale ou verticale.  Lorsque l'utilisateur fait glisser les angles ou les côtés, le plan retourne entre les deux configurations autorisées de la hauteur et la largeur.  
  
 la règle limites est une classe dérivée d' <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>.  une instance de la règle est créée dans la forme :  
  
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
  
 Notez que l'emplacement et la taille peuvent être contraints si vous le souhaitez.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md)