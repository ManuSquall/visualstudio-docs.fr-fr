---
title: "VBArray est attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5013"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: f2998d7d-13a4-4bbe-b872-3ff3316551e4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# VBArray est attendu
Vous avez fourni un objet autre qu'un safeArray Visual Basic, qui correspond à l'élément attendu.  
  
```  
new VBArray(safeArray);  
```  
  
 Les objets VBArray sont en lecture seule et ne peuvent pas être créés directement.  L'argument safeArray est une valeur VBArray qui doit avoir obtenu une valeur VBArray avant d'être passé au constructeur `VBArray`.  Cela ne peut être effectué qu'en récupérant la valeur d'un objet ActiveX existant ou d'un autre objet.  
  
### Pour corriger cette erreur  
  
-   Vérifiez que seuls les objets **VBArray** sont passés au constructeur **VBArray**.  
  
## Voir aussi  
 [Objet VBArray](../../javascript/reference/vbarray-object-javascript.md)   
 [Utilisation de tableaux](../../javascript/advanced/using-arrays-javascript.md)