---
title: "CA2130&#160;: Les constantes critiques de s&#233;curit&#233; doivent &#234;tre transparentes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2130"
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2130&#160;: Les constantes critiques de s&#233;curit&#233; doivent &#234;tre transparentes
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un champ constant ou un membre d'énumération est marqué avec le <xref:System.Security.SecurityCriticalAttribute>.  
  
## Description de la règle  
 La mise en application de la transparence n'est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu'aucune recherche ne soit requise au moment de l'exécution.  Les champs constants doivent être transparents de sécurité \(security\-transparent\) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, supprimez l'attribut SecurityCritical du champ ou de la valeur.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 Dans les exemples suivants, la valeur enum `EnumWithCriticalValues.CriticalEnumValue` et la constante `CriticalConstant` déclenchent cet avertissement.  Pour résoudre les problèmes, supprimez l'attribut \[`SecurityCritical`\] pour qu'elles soient transparentes de sécurité.  
  
 [!code-cs[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]