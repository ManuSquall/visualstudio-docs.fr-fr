---
title: "&#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car leurs types de retour ne sont pas identiques | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;m&#233;thode2&gt;&#39;, car leurs types de retour ne sont pas identiques
Vous avez tenté de substituer une méthode par une autre dont le type de retour est différent. Un type peut se substituer à une méthode substituable héritée en déclarant une méthode avec un nom et une signature identiques et en marquant la déclaration avec le modificateur `Overrides`. La signature des deux méthodes doit correspondre.  
  
 **ID d’erreur :** BC30437  
  
### Pour corriger cette erreur  
  
-   Vérifiez les types de retour des deux méthodes et modifiez\-les si nécessaire pour qu’elles correspondent.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)