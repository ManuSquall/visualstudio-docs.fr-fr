---
title: "L’attribut &#39;NonSerialized&#39; n’aura pas d’effet sur ce membre, car sa classe conteneur n’est pas expos&#233;e comme &#39;Serializable&#39; | Microsoft Docs"
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
  - "vbc30772"
  - "bc30772"
helpviewer_keywords: 
  - "BC30772"
ms.assetid: 1014e944-40c1-4078-8a38-139736ef89da
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;NonSerialized&#39; n’aura pas d’effet sur ce membre, car sa classe conteneur n’est pas expos&#233;e comme &#39;Serializable&#39;
Par défaut, les classes et leurs membres sont non sérialisables. L’attribut <xref:System.NonSerializedAttribute> est nécessaire uniquement si un membre d’une classe sérialisable ne doit pas être sérialisé.  
  
 **ID d’erreur :** BC30772  
  
### Pour corriger cette erreur  
  
-   Appliquez l’attribut <xref:System.SerializableAttribute> à la classe.  
  
     \- ou \-  
  
-   Supprimez l’attribut <xref:System.NonSerializedAttribute> du membre.  
  
## Voir aussi  
 <xref:System.NonSerializedAttribute>   
 <xref:System.SerializableAttribute>   
 [NOT IN BUILD : Attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)