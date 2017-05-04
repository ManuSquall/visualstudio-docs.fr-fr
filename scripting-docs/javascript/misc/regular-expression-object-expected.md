---
title: "Objet Regular expression attendu | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Objet Regular expression attendu
Vous avez tenté d'appeler la méthode **RegExp.prototype.toString** ou **RegExp.prototype.valueOf** sur un objet d'un type autre que `RegExp`.  L'objet de ce type d'appel doit être de type `RegExp`.  
  
### Pour corriger cette erreur  
  
-   Appelez uniquement les méthodes **RegExp.prototype.toString** ou **RegExp.prototype.valueOf** sur les objets de type `RegExp`.  
  
## Voir aussi  
 [Objet Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/fr-fr/ab0766e1-7037-45ed-aa23-706f58358c0e)