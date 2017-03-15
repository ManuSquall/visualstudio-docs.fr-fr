---
title: "&#39;(&#39; inattendu | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc32095"
  - "bc32095"
helpviewer_keywords: 
  - "BC32095"
ms.assetid: a47ad15a-2cfc-4d17-9012-27ba85b7d783
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;(&#39; inattendu
'\(' inattendu. Les tableaux de types génériques non instanciés ne sont pas autorisés.  
  
 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas compiler un tableau s’il ne possède pas un type de données spécifique. Vous ne pouvez pas utiliser un paramètre de type de données d’un type générique comme type de données d’un tableau.  
  
 **ID d’erreur :** BC32095  
  
### Pour corriger cette erreur  
  
-   Si vous avez besoin d’utiliser un tableau, vous devez le déclarer comme étant d’un type de données spécifique. Vous ne pouvez pas utiliser un paramètre de type de données.  
  
-   Si vous avez besoin d’un groupe d’éléments qui soit du type de données qui doit être fourni pour un paramètre de type de données, vous devez utiliser une collection au lieu d’un tableau.  
  
## Voir aussi  
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [NIB Collections en Visual Basic](http://msdn.microsoft.com/fr-fr/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)   
 [Gestion de groupes d’objets \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/50be4910-4732-4d5f-a18a-055a162e9037)