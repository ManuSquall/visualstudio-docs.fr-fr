---
title: "Les classes &#39;NotInheritable&#39; ne peuvent pas avoir de membres d&#233;clar&#233;s &#39;&lt;nom_sp&#233;cificateur&gt;&#39; | Microsoft Docs"
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
  - "vbc30607"
  - "bc30607"
helpviewer_keywords: 
  - "BC30607"
ms.assetid: c800e24e-d055-402f-b378-6d2f4041ff16
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les classes &#39;NotInheritable&#39; ne peuvent pas avoir de membres d&#233;clar&#233;s &#39;&lt;nom_sp&#233;cificateur&gt;&#39;
Il n’est pas possible d’utiliser les modificateurs override les classes `NotInheritable` car leurs membres ne peuvent pas être substitués.  
  
 **ID d’erreur :** BC30607  
  
### Pour corriger cette erreur  
  
-   Supprimez les modificateurs override, tels que `Overridable`, `NotOverridable` ou `MustOverride`, de la définition de classe.  
  
## Voir aussi  
 [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable)   
 [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable)   
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)