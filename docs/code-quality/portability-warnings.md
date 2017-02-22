---
title: "Avertissements li&#233;s &#224; la portabilit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "avertissements liés à la portabilité"
  - "avertissements liés à l’analyse du code managé, avertissements liés à la portabilité"
  - "avertissements, portabilité"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# Avertissements li&#233;s &#224; la portabilit&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements de portabilité prennent en charge la portabilité sur différents systèmes d'exploitation.  
  
## Dans cette section  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1900 : Les champs de type valeur doivent être portables](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Cette règle vérifie que les structures déclarées avec un attribut de disposition explicite s'aligneront correctement lorsqu'elles seront marshalées pour le code non managé sur les systèmes d'exploitation 64 bits.|  
|[CA1901 : Les déclarations P\/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Cette règle évalue la taille de chaque paramètre et la valeur de retour d'un P\/Invoke, et vérifie que leur taille est correcte lorsqu'elle est marshalée au code non managé sur les systèmes d'exploitation 32 bits et 64 bits.|  
|[CA1903 : Utiliser uniquement l'API à partir du Framework cible](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet.|