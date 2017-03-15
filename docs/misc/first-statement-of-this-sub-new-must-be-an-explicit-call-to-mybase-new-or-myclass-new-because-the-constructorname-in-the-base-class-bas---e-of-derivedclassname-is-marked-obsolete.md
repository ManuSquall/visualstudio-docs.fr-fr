---
title: "La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel explicite &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; de la classe de base &#39;&lt;nom_classe_base&gt;&#39; de &#39;&lt;nom_classe_d&#233;riv&#233;e&gt;&#39; est marqu&#233; comme obsol&#232;te. | Microsoft Docs"
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
  - "vbc30919"
  - "bc30919"
helpviewer_keywords: 
  - "BC30919"
ms.assetid: 437e3204-8ddc-45d3-b9b4-c66d53a61a6d
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel explicite &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; de la classe de base &#39;&lt;nom_classe_base&gt;&#39; de &#39;&lt;nom_classe_d&#233;riv&#233;e&gt;&#39; est marqu&#233; comme obsol&#232;te.
Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base et le constructeur de classe de base implicite est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.  
  
 Quand un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] essaie de générer un appel implicite à un constructeur de classe de base sans paramètre. S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas générer d’appel implicite. Dans ce cas, le constructeur nécessaire est marqué avec l’attribut <xref:System.ObsoleteAttribute>, et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas l’appeler.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute>. Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`. Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC30919  
  
### Pour corriger cette erreur  
  
-   Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)