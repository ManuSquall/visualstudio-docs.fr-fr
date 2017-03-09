---
title: "Impossible de lire les champs d&#233;limit&#233;s, car un guillemet double ne constitue pas un d&#233;limiteur conforme lorsque EscapeQuotes a la valeur True | Microsoft Docs"
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
  - "vbrTextFieldParser_IllegalDelimiter"
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de lire les champs d&#233;limit&#233;s, car un guillemet double ne constitue pas un d&#233;limiteur conforme lorsque EscapeQuotes a la valeur True
Le `TextFieldParser` ne peut pas lire le fichier, car un guillemet \("\) a été fourni comme délimiteur et `EscapeQuotes` a la valeur `True`.  
  
### Pour corriger cette erreur  
  
-   Affectez la valeur `False` à `EscapeQuotes`.  
  
## Voir aussi  
 [TextFieldParser.SetDelimiters, méthode](http://msdn.microsoft.com/fr-fr/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters, propriété](http://msdn.microsoft.com/fr-fr/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)