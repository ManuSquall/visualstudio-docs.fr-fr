---
title: "Une d&#233;claration d’espace de noms doit commencer par &#39;xmlns&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31187"
  - "vbc31187"
helpviewer_keywords: 
  - "BC31187"
ms.assetid: 64c6a033-7cdc-48a0-bff0-bdd045cb13ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Une d&#233;claration d’espace de noms doit commencer par &#39;xmlns&#39;
Un espace de noms XML a été spécifié sans l’identificateur `xmlns` obligatoire. L’identificateur `xmlns` doit contenir uniquement des caractères en minuscules.  
  
 **ID d’erreur :** BC31187  
  
### Pour corriger cette erreur  
  
-   Utilisez l’identificateur `xmlns` quand vous déclarez un espace de noms XML. Voici un exemple :  
  
    ```vb#  
    Imports <xmlns:ns="http://SampleNamespace">  
    ```  
  
## Voir aussi  
 [Imports Statement \(XML Namespace\)](/dotnet/visual-basic/language-reference/statements/imports-statement-xml-namespace)   
 [XML Literals](/dotnet/visual-basic/language-reference/xml-literals/index)   
 [XML](/dotnet/visual-basic/programming-guide/language-features/xml/index)