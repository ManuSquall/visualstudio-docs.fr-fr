---
title: "Les param&#232;tres de type ou les types construits avec des param&#232;tres de type ne sont pas autoris&#233;s dans les arguments d’attribut | Microsoft Docs"
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
  - "BC32079"
  - "vbc32079"
helpviewer_keywords: 
  - "BC32079"
ms.assetid: 93eb59bd-e7db-4f73-a37f-405a83df48c1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les param&#232;tres de type ou les types construits avec des param&#232;tres de type ne sont pas autoris&#233;s dans les arguments d’attribut
Un attribut est appliqué à l’aide d’un argument qui est soit un paramètre de type, soit construit avec un paramètre de type.  
  
 Visual Basic et le .NET Framework ne prennent pas actuellement en charge les combinaisons d’attributs et de types génériques. Cela signifie que les limitations suivantes s’appliquent :  
  
-   Un attribut ne peut ni être un type générique, ni être déclaré dans un type générique.  
  
-   Un attribut ne peut pas hériter d’une classe générique, et une classe générique ne peut pas non plus hériter d’un attribut.  
  
-   Quand vous appliquez un attribut, vous ne pouvez pas fournir un argument qui correspond à l’un des éléments suivants :  
  
    -   Type générique  
  
    -   Type construit à partir d’un type générique  
  
    -   Paramètre de type d’un type conteneur  
  
    -   Type construit à partir d’un paramètre de type d’un type conteneur  
  
 **ID d’erreur :** BC32079  
  
### Pour corriger cette erreur  
  
-   Reconstruisez les arguments fournis à l’attribut de manière à ce qu’ils n’incluent pas de paramètres de type ni de type construit à partir d’un paramètre de type.  
  
## Voir aussi  
 <xref:System.Attribute>   
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [Types génériques Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)