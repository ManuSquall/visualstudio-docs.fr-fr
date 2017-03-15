---
title: "Toutes les largeurs de champs, &#224; l’exception de celle du dernier &#233;l&#233;ment, doivent &#234;tre sup&#233;rieures &#224; z&#233;ro | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrTextFieldParser_FieldWidthsMustPositive"
ms.assetid: 41d8c661-a749-4c89-be56-905c6e7c3c9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Toutes les largeurs de champs, &#224; l’exception de celle du dernier &#233;l&#233;ment, doivent &#234;tre sup&#233;rieures &#224; z&#233;ro
Toutes les largeurs de champs, à l’exception de celle du dernier élément, doivent être supérieures à zéro. Une largeur de champ inférieure ou égale à zéro dans le dernier élément indique que le dernier champ a une longueur variable.  
  
 L’opération a échoué car une largeur de champ autre que celle du dernier élément a une valeur inférieure ou égale à zéro. Une largeur de champ inférieure ou égale à zéro peut être utilisée comme dernier élément pour indiquer que le dernier champ est de longueur variable, mais elle ne peut pas être utilisée comme autre élément.  
  
### Pour corriger cette erreur  
  
-   Affectez la longueur correcte à la largeur de champ.  
  
## Voir aussi  
 [TextFieldParser.SetFieldWidths, méthode](http://msdn.microsoft.com/fr-fr/958fed9f-e0f3-4fc5-83b4-386156bdf036)   
 [TextFieldParser.FieldWidths, propriété](http://msdn.microsoft.com/fr-fr/c6985360-60c6-494e-89e7-43b6b73f2597)   
 [How to: Read From Fixed\-width Text Files](../Topic/How%20to:%20Read%20From%20Fixed-width%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)