---
title: "CA1809&#160;: &#201;vitez le surplus de variables locales | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1809"
  - "AvoidExcessiveLocals"
helpviewer_keywords: 
  - "AvoidExcessiveLocals"
  - "CA1809"
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1809&#160;: &#201;vitez le surplus de variables locales
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un membre contient plus de 64 variables locales, dont certaines peuvent être générées par le compilateur.  
  
## Description de la règle  
 Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée *enregistrement* de la valeur.  Le Common Language Runtime prend en charge 64 variables locales au maximum pour l'enregistrement.  Les variables qui ne sont pas enregistrées sont placées sur la pile et doivent être déplacées dans un registre avant toute manipulation.  Pour permettre l'enregistrement de toutes les variables locales, limitez le nombre de variables locales à 64.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, refactorisez l'implémentation afin d'utiliser 64 variables locales au maximum.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle, voire de désactiver la règle, si les performances ne sont pas un problème.  
  
## Règles connexes  
 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)