---
title: "&#39;&lt;nom_type&gt;&#39; ne peut pas masquer une m&#233;thode &#39;MustOverride&#39; d&#233;clar&#233;e implicitement pour la propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39; | Microsoft Docs"
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
  - "bc31416"
  - "vbc31416"
helpviewer_keywords: 
  - "BC31416"
ms.assetid: a52aee3c-a19e-412d-bb91-ef1b79e8675f
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_type&gt;&#39; ne peut pas masquer une m&#233;thode &#39;MustOverride&#39; d&#233;clar&#233;e implicitement pour la propri&#233;t&#233; &#39;&lt;nom_propri&#233;t&#233;&gt;&#39; dans &lt;type&gt; &#39;&lt;nom_type&gt;&#39;
Le nom de méthode spécifié est en conflit avec une méthode `MustOverride` générée implicitement par une propriété de la classe de base. Par exemple, si vous déclarez une propriété nommée `Prop1`, le compilateur génère les procédures implicites `get_Prop1` et `set_Prop1`.  
  
 **ID d’erreur :** BC31416  
  
### Pour corriger cette erreur  
  
1.  Donnez un nom unique à la méthode.  
  
2.  Supprimez le modificateur `MustOverride`de la propriété de la classe de base.  
  
## Voir aussi  
 [MustOverride](/dotnet/visual-basic/language-reference/modifiers/mustoverride)   
 [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)   
 [Procédures de propriété](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)