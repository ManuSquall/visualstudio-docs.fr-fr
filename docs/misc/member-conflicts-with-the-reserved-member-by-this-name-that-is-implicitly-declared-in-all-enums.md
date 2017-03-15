---
title: "&#39;&lt;membre&gt;&#39; est en conflit avec le membre r&#233;serv&#233; par ce nom qui est implicitement d&#233;clar&#233; dans tous les enums | Microsoft Docs"
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
  - "bc31420"
  - "vbc31420"
helpviewer_keywords: 
  - "BC31420"
ms.assetid: f2ea5a8b-f63c-4c93-bfac-418ae5a150a5
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membre&gt;&#39; est en conflit avec le membre r&#233;serv&#233; par ce nom qui est implicitement d&#233;clar&#233; dans tous les enums
Le nom d’un membre de type est en conflit avec le nom d’un membre implicitement déclaré dans toutes les énumérations.  
  
 Le compilateur [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] crée des membres implicites correspondant à certains éléments de programmation que vous déclarez. Les énumérations déclarent implicitement le membre `value__member`.  
  
 **ID d’erreur :** BC31420  
  
### Pour corriger cette erreur  
  
-   Modifiez le nom du membre.  
  
## Voir aussi  
 [NotInBuild : Instructions de déclaration en Visual Basic](http://msdn.microsoft.com/fr-fr/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)   
 [Enumerations Overview](/dotnet/visual-basic/programming-guide/language-features/constants-enums/enumerations-overview)   
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)