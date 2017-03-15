---
title: "&#39;&lt;nom_membre&gt;&#39; est obsol&#232;te&#160;: &#39;&lt;message_erreur&gt;&#39; | Microsoft Docs"
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
  - "bc30668"
  - "vbc30668"
helpviewer_keywords: 
  - "BC30668"
ms.assetid: 25e5606c-2734-4f42-a2bc-1ad28ec1e892
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_membre&gt;&#39; est obsol&#232;te&#160;: &#39;&lt;message_erreur&gt;&#39;
Une instruction tente d’accéder à un membre de classe ou de structure qui a été marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute>. Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`. Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False` ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC30668  
  
### Pour corriger cette erreur  
  
1.  Examinez le message d’erreur et prenez les mesures nécessaires.  
  
2.  Vérifiez que le nom du membre est orthographié correctement dans la référence du code source.  
  
## Voir aussi  
 [NOT IN BUILD : attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)