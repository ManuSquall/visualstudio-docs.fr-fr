---
title: "Assignation impossible &#224; &#39;this&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Assignation impossible &#224; &#39;this&#39;
Vous avez tenté d'assigner une valeur à **this**.  **this** est un mot clé de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] qui fait référence à l'un ou l'autre des objets suivants :  
  
-   l'objet exécutant actuellement une méthode ;  
  
-   l'objet global si aucune méthode n'est en cours \(ou si la méthode n'appartient à aucun autre objet\).  
  
 Une méthode est une fonction [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] appelée via un objet.  Au sein d'une méthode, le mot clé **this** fait référence à l'objet utilisé pour appeler la méthode \(lequel est l'objet créé en appelant le constructeur de classe avec l'opérateur **new**\).  
  
 Dans une méthode, utilisez **this** pour faire référence à l'objet actif, sans toutefois pouvoir lui assigner une nouvelle valeur.  
  
### Pour corriger cette erreur  
  
-   Ne tentez pas d'assigner une valeur à **this**.  Pour accéder à une méthode ou à une propriété d'un objet instancié, utilisez l'opérateur point \(.\) \(par exemple, cercle**.**rayon\).  
  
    > [!NOTE]
    >  Le nom **this** ne peut être donné à une variable créée par l'utilisateur ; il s'agit d'un mot clé réservé de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Voir aussi  
 [this, instruction](../../javascript/reference/this-statement-javascript.md)   
 [Dépannage de vos scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)