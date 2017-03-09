---
title: "&#39;&lt;nom_type&gt;&#39; dans l’assembly &#39;&lt;nom_assembly&gt;&#39; a &#233;t&#233; transf&#233;r&#233; &#224; lui-m&#234;me et est donc un type non pris en charge | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31425"
  - "vbc31425"
helpviewer_keywords: 
  - "BC31425"
  - "transfert de type"
ms.assetid: e3275d55-3f4c-4bbc-9c8f-f55c4e973063
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; dans l’assembly &#39;&lt;nom_assembly&gt;&#39; a &#233;t&#233; transf&#233;r&#233; &#224; lui-m&#234;me et est donc un type non pris en charge
Un assembly utilise <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour transférer un de ses types à un autre assembly, mais spécifie le même type dans le même assembly.  
  
 Le *transfert de type* consiste à réassigner la définition d’une classe, d’une structure, d’une interface, d’un délégué ou d’une énumération à un autre assembly que celui dans lequel il ou elle a été initialement défini\(e\). On l’utilise souvent conjointement avec la *refactorisation de code*, qui consiste à fractionner un assembly en plusieurs assemblys ou à déplacer du code d’un assembly vers un autre.  
  
 Le transfert d’un type à lui\-même occasionne un transfert circulaire. Si un autre assembly a tenté d’accéder au type transféré, il entre dans un transfert sans fin sans jamais parvenir à un type qui n’avait pas été transféré.  
  
 **ID d’erreur :** BC31425  
  
### Pour corriger cette erreur  
  
-   Transférez le type vers un type dans un autre assembly ou ne le transférez pas du tout.  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)   
 [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/fr-fr/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)