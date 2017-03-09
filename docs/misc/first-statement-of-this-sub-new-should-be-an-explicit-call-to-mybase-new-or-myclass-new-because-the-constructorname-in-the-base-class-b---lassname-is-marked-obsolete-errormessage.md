---
title: "La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel explicite &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; de la classe de base &#39;&lt;nom_classe_base&gt;&#39; de &#39;&lt;nom_classe_d&#233;riv&#233;e&gt;&#39; est marqu&#233; comme obsol&#232;te&#160;: &#39;&lt;message_erreur&gt;&#39; | Microsoft Docs"
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
  - "bc41004"
  - "vbc41004"
helpviewer_keywords: 
  - "BC41004"
ms.assetid: 61185283-d43d-46ae-bfa0-6fe3e1d0982a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La premi&#232;re instruction de ce &#39;Sub New&#39; doit &#234;tre un appel explicite &#224; &#39;MyBase.New&#39; ou &#39;MyClass.New&#39;, car le &#39;&lt;nom_constructeur&gt;&#39; de la classe de base &#39;&lt;nom_classe_base&gt;&#39; de &#39;&lt;nom_classe_d&#233;riv&#233;e&gt;&#39; est marqu&#233; comme obsol&#232;te&#160;: &#39;&lt;message_erreur&gt;&#39;
Un constructeur de classe n’appelle pas explicitement un constructeur de classe de base, et le constructeur de classe de base implicite est marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme un avertissement.  
  
 Quand un constructeur de classe dérivée n’appelle pas de constructeur de classe de base, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] essaie de générer un appel implicite à un constructeur de classe de base sans paramètre. S’il n’existe aucun constructeur accessible dans la classe de base qui peut être appelé sans arguments, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas générer d’appel implicite. Dans ce cas, le constructeur nécessaire est marqué avec l’attribut <xref:System.ObsoleteAttribute>, et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne peut pas l’appeler.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute>. Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`. Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous conservez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 Par défaut, ce message est un avertissement, car la propriété <xref:System.ObsoleteAttribute.IsError%2A> de <xref:System.ObsoleteAttribute> a la valeur `False`. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuration d'avertissements en Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID d’erreur :** BC41004  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d’erreur mentionné et prenez les mesures nécessaires.  
  
2.  Incluez un appel à `MyBase.New()` ou `MyClass.New()` en tant que première instruction de `Sub New` dans la classe dérivée.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)