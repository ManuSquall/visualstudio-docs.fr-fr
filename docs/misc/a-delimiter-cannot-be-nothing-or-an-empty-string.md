---
title: "Un d&#233;limiteur ne peut pas &#234;tre Nothing ou un String vide | Microsoft Docs"
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
  - "vbrTextFieldParser_DelimiterNothing"
ms.assetid: 8885fcd1-c201-409d-9a32-6ff2b13c0c13
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Un d&#233;limiteur ne peut pas &#234;tre Nothing ou un String vide
Le `TextFieldParser` ne peut pas lire le fichier, car la propriété `Delimiters` a la valeur `Nothing` ou est un `String` vide \(""\).  
  
### Pour corriger cette erreur  
  
-   Fournissez une valeur valide pour `Delimiters`.  
  
## Voir aussi  
 [TextFieldParser.SetDelimiters, méthode](http://msdn.microsoft.com/fr-fr/21fa40ec-5866-4d0e-9fd9-c708a190dcc9)   
 [TextFieldParser.Delimiters, propriété](http://msdn.microsoft.com/fr-fr/4eb18f4d-3011-40a9-b668-be93eed0444f)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [TextFieldParser Object](/dotnet/visual-basic/language-reference/objects/textfieldparser-object)   
 [Parsing Text Files with the TextFieldParser Object](/dotnet/visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object)