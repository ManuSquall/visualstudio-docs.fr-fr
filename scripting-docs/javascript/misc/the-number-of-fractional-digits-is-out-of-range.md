---
title: "Le nombre de chiffres fractionnaires est hors limites | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5026"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: dbe05d7d-fcf6-4823-9c61-4b814d1ad3c4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Le nombre de chiffres fractionnaires est hors limites
Vous avez tenté de passer un argument non valide à la fonction **Number.prototype.toExponential**.  L'argument de la fonction **toExponential\(\)** doit être compris entre 0 et 20 \(inclus\).  
  
### Pour corriger cette erreur  
  
-   Assurez\-vous que l'argument de **toExponential\(\)** n'est ni trop bas, ni trop élevé.  
  
## Voir aussi  
 [toExponential, méthode \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)