---
title: "&#39;nom_proc&#233;dure1&#39; ne peut pas se substituer &#224; &#39;nom_proc&#233;dure2&#39;, car les param&#232;tres d&#233;clar&#233;s &#39;ParamArray&#39; les diff&#233;rencient | Microsoft Docs"
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
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;nom_proc&#233;dure1&#39; ne peut pas se substituer &#224; &#39;nom_proc&#233;dure2&#39;, car les param&#232;tres d&#233;clar&#233;s &#39;ParamArray&#39; les diff&#233;rencient
Une procédure dans une classe dérivée substitue une procédure de même nom dans la classe de base, mais les listes de paramètres sont différentes.  
  
 Pour substituer une procédure dans une classe héritée, il faut que la procédure de substitution corresponde à sa liste de paramètres, à son niveau d’accès et à son type de retour \(le cas échéant\). En particulier, elle doit correspondre à toute déclaration [Optional](/dotnet/visual-basic/language-reference/modifiers/optional) ou [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray).  
  
 **ID d’erreur :** BC30906  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez substituer la procédure, faites en sorte que la liste des paramètres soit exactement la même que celle de la procédure de classe de base. Si le dernier paramètre est déclaré avec `ParamArray` dans la procédure de classe de base, déclarez\-le avec `ParamArray` dans la procédure de substitution.  
  
-   Si vous souhaitez que la liste des paramètres soit différente de la version de la classe de base, vous ne pouvez pas la substituer. Au lieu de cela, surchargez\-la. Pour plus d'informations, consultez [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading).  
  
## Voir aussi  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)