---
title: "La r&#233;f&#233;rence d’assembly Friend &lt;r&#233;f&#233;rence&gt; n’est pas valide. Les d&#233;clarations InternalsVisibleTo ne peuvent pas avoir une version, une culture, un jeton de cl&#233; publique ou une architecture de processeur sp&#233;cifi&#233;e. | Microsoft Docs"
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
  - "bc31534"
  - "vbc31534"
helpviewer_keywords: 
  - "BC31534"
ms.assetid: ae1e470e-3105-48f2-87b1-466e395a7d44
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La r&#233;f&#233;rence d’assembly Friend &lt;r&#233;f&#233;rence&gt; n’est pas valide. Les d&#233;clarations InternalsVisibleTo ne peuvent pas avoir une version, une culture, un jeton de cl&#233; publique ou une architecture de processeur sp&#233;cifi&#233;e.
Le nom d’assembly passé au constructeur d’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contient un attribut `Version`, `Culture`, `PublicKeyToken` ou `processorArchitecture`.  
  
 **ID d’erreur :** BC31534  
  
### Pour corriger cette erreur  
  
1.  Supprimez l’attribut `Version`, `Culture`, `PublicKeyToken` ou `processorArchitecture` du nom d’assembly passé au constructeur d’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.  
  
## Voir aussi  
 <xref:System.Reflection.AssemblyName>   
 [NOT IN BUILD : Assemblys Friend \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/80e7a33a-ca91-450b-a00e-c5a7986e228c)