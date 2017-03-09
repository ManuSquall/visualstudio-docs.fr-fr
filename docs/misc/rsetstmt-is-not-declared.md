---
title: "&#39;&lt;rsetstmt&gt;&#39; n’est pas d&#233;clar&#233;. | Microsoft Docs"
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
  - "bc30821"
  - "vbc30821"
helpviewer_keywords: 
  - "BC30821"
ms.assetid: 7936e3ef-7ac6-4a71-af55-acc2c5cd8754
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;rsetstmt&gt;&#39; n’est pas d&#233;clar&#233;.
'\<rsetstmt\>' n’est pas déclaré. Les instructions RSet ne sont plus prises en charge ; utilisez Microsoft.VisualBasic.RSet à la place.  
  
 Plusieurs fonctions qui étaient intrinsèques à [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans les versions précédentes ont été déplacées vers l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>. Leurs fonctionnalités sont ainsi plus largement accessibles à tous les langages de programmation.  
  
 **ID d’erreur :** BC30821  
  
### Pour corriger cette erreur  
  
-   Utilisez plutôt la fonction `RSet` dans l’espace de noms `Microsoft.VisualBasic`.  
  
## Voir aussi  
 [NOT IN BUILD : Fonction RSet](http://msdn.microsoft.com/fr-fr/534514e5-dee9-4dfd-993b-da09731eece5)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/fr-fr/0483590a-6309-449c-a2fa-effa26a03b95)