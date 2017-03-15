---
title: "&lt;type1&gt; &#39;&lt;nom_membre&gt;&#39; est en conflit avec &lt;type2&gt; &#39;&lt;nom_membre&gt;&#39; sur la classe de base &lt;type3&gt; &#39;&lt;nom_classe&gt;&#39; et doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39; | Microsoft Docs"
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
  - "bc40004"
  - "vbc40004"
helpviewer_keywords: 
  - "BC40004"
ms.assetid: 24d10f31-3b3d-448c-b928-fc937e1f4a92
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;type1&gt; &#39;&lt;nom_membre&gt;&#39; est en conflit avec &lt;type2&gt; &#39;&lt;nom_membre&gt;&#39; sur la classe de base &lt;type3&gt; &#39;&lt;nom_classe&gt;&#39; et doit &#234;tre d&#233;clar&#233; &#39;Shadows&#39;
Un élément de programmation est déclaré avec le même nom qu’un élément défini dans la classe de base. Dans ce cas, l’élément de cette classe doit masquer l’élément de la classe de base.  
  
 Ce message est un avertissement.`Shadows` est supposé par défaut. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC40004  
  
### Pour corriger cette erreur  
  
-   Ajoutez le mot clé `Shadows` à la déclaration ou modifiez le nom de l’élément déclaré.  
  
## Voir aussi  
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Shadowing in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/shadowing)