---
title: "&#39;&lt;nom_&#233;l&#233;ment&gt;&#39; est obsol&#232;te (erreur Visual Basic) | Microsoft Docs"
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
  - "vbc31075"
  - "bc31075"
helpviewer_keywords: 
  - "BC31075"
ms.assetid: 614d36a1-2fba-4d03-963c-1565e88b08a6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;nom_&#233;l&#233;ment&gt;&#39; est obsol&#232;te (erreur Visual Basic)
Une instruction tente d’accéder à un élément de programmation qui a été marqué avec l’attribut <xref:System.ObsoleteAttribute> et la directive pour le traiter comme une erreur.  
  
 Vous pouvez marquer un élément de programmation comme n’étant plus utilisé en lui appliquant <xref:System.ObsoleteAttribute>. Dans ce cas, vous pouvez affecter à la propriété <xref:System.ObsoleteAttribute.IsError%2A> de l’attribut la valeur `True` ou `False`. Si vous lui affectez la valeur `True`, le compilateur traite une tentative d’utilisation de l’élément comme une erreur. Si vous lui affectez la valeur `False`, ou si vous laissez la valeur par défaut `False`, le compilateur émet un avertissement en cas de tentative d’utilisation de l’élément.  
  
 **ID d’erreur :** BC31075  
  
### Pour corriger cette erreur  
  
-   Vérifiez que le nom de l’élément est orthographié correctement dans la référence du code source.  
  
## Voir aussi  
 [NOT IN BUILD : Attributs utilisés en Visual Basic](http://msdn.microsoft.com/fr-fr/22231318-8a40-49af-9245-e0aab723563b)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)