---
title: "MSBuild Best Practices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "best practices, MSBuild"
  - "MSBuild, best practices"
ms.assetid: 90ef8693-e921-410a-a377-fe4d13f58c48
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# MSBuild Best Practices
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nous vous recommandons les meilleures pratiques suivantes pour l'écriture de scripts MSBuild :  
  
-   Les valeurs de propriété par défaut sont mieux gérées en utilisant l'attribut `Condition` plutôt qu'en déclarant une propriété dont la valeur par défaut peut être substituée sur la ligne de commande.  Par exemple, utilisez  
  
     `<MyProperty Condition="$(MyProperty)" == ''>`  
  
     `MyDefaultValue`  
  
     `</MyProperty>`  
  
-   Évitez les caractères génériques quand vous sélectionnez des éléments.  Spécifiez plutôt les fichiers de manière explicite.  Les erreurs susceptibles de se produire quand vous ajoutez ou supprimez des fichiers sont ainsi plus faciles à localiser.  
  
## Voir aussi  
 [Advanced Concepts](../msbuild/msbuild-advanced-concepts.md)