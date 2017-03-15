---
title: "Le type g&#233;n&#233;rique &#39;&lt;nom_type_g&#233;n&#233;rique&gt;&#39; ne peut pas &#234;tre import&#233; plus d’une fois | Microsoft Docs"
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
  - "BC32086"
  - "vbc32086"
helpviewer_keywords: 
  - "BC32086"
ms.assetid: d93bae4b-3224-4a6e-a072-8ce231084519
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le type g&#233;n&#233;rique &#39;&lt;nom_type_g&#233;n&#233;rique&gt;&#39; ne peut pas &#234;tre import&#233; plus d’une fois
Un [Imports Statement \(.NET Namespace and Type\)](/dotnet/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type) spécifie un type générique qui a déjà été importé avec un paramétrage de type différent.  
  
 Vous pouvez déclarer plusieurs types construits à partir d’un type générique, car vous ne redéfinissez pas le type générique en déclarant un type construit. Cependant, si vous importez plusieurs fois un type générique, cela équivaut à plusieurs définitions.  
  
 **ID d’erreur :** BC32086  
  
### Pour corriger cette erreur  
  
1.  Si le fichier source contenant cette instruction `Imports` contient également une autre instruction `Imports` spécifiant le même type générique, supprimez l’une d’elles.  
  
2.  Si vous devez importer le même type générique avec des paramétrages de type différents, utilisez plusieurs fichiers sources.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)