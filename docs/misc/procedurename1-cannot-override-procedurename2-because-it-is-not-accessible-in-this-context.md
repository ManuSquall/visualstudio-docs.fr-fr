---
title: "&#39;&lt;nom_proc&#233;dure1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;nom_proc&#233;dure2&gt;&#39;, car il n’est pas accessible dans ce contexte | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31417"
  - "vbc31417"
helpviewer_keywords: 
  - "BC31417"
ms.assetid: 1a36acbf-cead-43a0-b12f-f52f94d09124
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_proc&#233;dure1&gt;&#39; ne peut pas se substituer &#224; &#39;&lt;nom_proc&#233;dure2&gt;&#39;, car il n’est pas accessible dans ce contexte
Une procédure ou une propriété se substitue à une procédure ou une propriété avec un niveau d’accès qui empêche l’accès à la procédure ou propriété de substitution.  
  
 Par exemple, si une procédure est déclarée en tant que `Friend` dans un assembly, elle est inaccessible en dehors de cet assembly. Si une procédure au sein d’un autre assembly du même projet essaie de se substituer à la procédure `Friend`, elle ne peut pas y accéder pour la remplacer.  
  
 **ID d’erreur :** BC31417  
  
### Pour corriger cette erreur  
  
-   Déplacez la procédure ou la propriété de substitution dans l’assembly où se trouve la procédure ou la propriété à remplacer.  
  
     ou  
  
-   Supprimez le mot clé `Overrides`.  
  
## Voir aussi  
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)