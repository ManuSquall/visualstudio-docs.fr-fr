---
title: "&#39;&lt;m&#233;thode&gt;&#39; n’est pas accessible dans ce contexte, car il est &#39;&lt;modificateur&gt;&#39; | Microsoft Docs"
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
  - "vbc30389"
  - "bc30389"
helpviewer_keywords: 
  - "BC30389"
ms.assetid: fae58a68-df91-4741-a8c9-f1bb10e166e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;m&#233;thode&gt;&#39; n’est pas accessible dans ce contexte, car il est &#39;&lt;modificateur&gt;&#39;
Vous avez tenté d’accéder à une méthode qui n’est pas accessible dans ce contexte, car elle a été déclarée `Private`. Cette erreur peut s’expliquer par le fait que le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] importe tous les membres d’une classe sans respecter la casse, d’où un éventuel conflit entre les noms uniquement différenciés par la casse.  
  
 **ID d’erreur :** BC30389  
  
### Pour corriger cette erreur  
  
-   Songez à déclarer la méthode `Public`.  
  
-   Si l’erreur est due à un conflit de noms, veillez à ce que les noms en conflit ne diffèrent pas uniquement par leur casse.  
  
## Voir aussi  
 [Private](/dotnet/visual-basic/language-reference/modifiers/private)