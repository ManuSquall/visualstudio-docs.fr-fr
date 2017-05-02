---
title: "Objet prototype non valide pour la fonction | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b9e34652-190f-4b57-b253-df2e8c4d09c6
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Objet prototype non valide pour la fonction
Vous avez tenté d'utiliser **instanceof** pour déterminer si un objet est dérivé d'une classe de fonction particulière, mais vous avez redéfini la propriété `prototype` de l'objet avec la valeur `null`, ou avec un type d'objet externe \(l'un et l'autre ne constituant pas des objets [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valides\).  Un objet externe peut être un objet issu du modèle objet hôte \(objet fenêtre ou document dans Internet Explorer, par exemple\) ou un objet COM externe.  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que la propriété `prototype` de la fonction fait référence à un objet [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valide.  
  
## Voir aussi  
 [Objet de function](../../javascript/reference/function-object-javascript.md)   
 [prototype, propriété \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)