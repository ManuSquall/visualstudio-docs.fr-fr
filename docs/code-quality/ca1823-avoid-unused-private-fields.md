---
title: "CA1823&#160;: &#201;vitez les champs priv&#233;s inutilis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
helpviewer_keywords: 
  - "AvoidUnusedPrivateFields"
  - "CA1823"
ms.assetid: 614f94f6-0dc7-430f-8124-cb889a4a720f
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA1823&#160;: &#201;vitez les champs priv&#233;s inutilis&#233;s
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnusedPrivateFields|  
|CheckId|CA1823|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Cette règle s'affiche lorsqu'un champ privé de votre code existe, mais n'est pas utilisé par un chemin d'accès de code.  
  
## Description de la règle  
 Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le champ ou ajoutez le code qui l'utilise.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle.  
  
## Règles connexes  
 [CA1812 : Évitez les classes internes non instanciées](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801 : Passez en revue les paramètres inutilisés](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)  
  
 [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md)