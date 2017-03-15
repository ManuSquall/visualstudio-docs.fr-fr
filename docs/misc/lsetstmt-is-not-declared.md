---
title: "&#39;&lt;lsetstmt&gt;&#39; n’est pas d&#233;clar&#233; | Microsoft Docs"
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
  - "bc30820"
  - "vbc30820"
helpviewer_keywords: 
  - "BC30820"
ms.assetid: 8666dd52-58ea-4b84-b59a-8ebd8b2cb23b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;lsetstmt&gt;&#39; n’est pas d&#233;clar&#233;
'\<lsetstmt\>' n’est pas déclaré. Les instructions LSet ne sont plus prises en charge ; utilisez Microsoft.VisualBasic.LSet à la place.  
  
 Plusieurs fonctions qui étaient intrinsèques à [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] dans les versions précédentes ont été déplacées vers l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>. Leurs fonctionnalités sont ainsi plus généralement accessibles à tous les langages de programmation.  
  
 **ID d’erreur :** BC30820  
  
### Pour corriger cette erreur  
  
-   Utilisez plutôt la fonction `LSet` dans l’espace de noms `Microsoft.VisualBasic`.  
  
## Voir aussi  
 [NOT IN BUILD : Fonction LSet](http://msdn.microsoft.com/fr-fr/591d286c-6b7a-4350-ae74-99fee00fd964)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/fr-fr/0483590a-6309-449c-a2fa-effa26a03b95)