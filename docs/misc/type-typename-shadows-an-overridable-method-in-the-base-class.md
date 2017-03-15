---
title: "&lt;type&gt; &#39;&lt;nom_type&gt;&#39; masque une m&#233;thode substituable dans la classe de base | Microsoft Docs"
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
  - "vbc40005"
  - "bc40005"
helpviewer_keywords: 
  - "BC40005"
ms.assetid: 1dadda7f-1d26-4ae8-a668-9f69d55ceb50
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type&gt; &#39;&lt;nom_type&gt;&#39; masque une m&#233;thode substituable dans la classe de base
\<type\> '\<nom\_type\>' masque une méthode substituable dans la classe de base. Pour substituer la méthode de base, vous devez déclarer cette méthode 'Overrides'.  
  
 Un élément de programmation est déclaré avec le même nom qu’une procédure ou propriété substituable définie dans la classe de base. Dans ce cas, l’élément de cette classe doit masquer l’élément de la classe de base.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40005  
  
### Pour corriger cette erreur  
  
-   Si vous souhaitez substituer la procédure de base, ajoutez le mot clé `Overrides` à la déclaration.  
  
-   Si vous souhaitez masquer la procédure de base, ajoutez le mot clé `Shadows` à la déclaration.  
  
-   Si vous ne souhaitez ni substituer ni masquer la procédure de base, changez le nom de l’élément déclaré.  
  
## Voir aussi  
 [NOT IN BUILD : Substitution de propriétés et de méthodes](http://msdn.microsoft.com/fr-fr/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)   
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)