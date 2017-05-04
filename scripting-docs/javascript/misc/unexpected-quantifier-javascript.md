---
title: "Quantificateur inattendu (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5018"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Quantificateur inattendu (JavaScript)
Lors de la composition d'un modèle de recherche d'expression régulière, vous avez créé un élément de modèle avec un facteur de répétition non conforme.  Par exemple, le modèle  
  
```  
/^+/  
```  
  
 est non conforme puisque pour l'élément « ^ » \(début de l'entrée\), un facteur de répétition est impossible.  Le tableau suivant répertorie les éléments pour lesquels les facteurs à répétition sont impossibles.  
  
|Élément|Description|  
|-------------|-----------------|  
|^|Début de l'entrée|  
|$|Fin de l'entrée|  
|\\b|Limite d'un mot|  
|\\B|Limite non alphabétique|  
|\*|Zéro, ou plusieurs répétitions|  
|\+|Une, ou plusieurs répétitions|  
|?|Zéro, ou une répétition|  
|{n}|n répétitions|  
|{n,}|n ou plus de répétitions|  
|{n,m}|Entre n et m répétitions, inclus|  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que l'élément de modèle de recherche contient exclusivement des facteurs de répétition conformes.  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)