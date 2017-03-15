---
title: "CA2131&#160;: Les types critiques de s&#233;curit&#233; ne peuvent pas participer &#224; l&#39;&#233;quivalence des types | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131&#160;: Les types critiques de s&#233;curit&#233; ne peuvent pas participer &#224; l&#39;&#233;quivalence des types
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Un type participe à l'équivalence des types et un type lui\-même, ou un membre ou champ du type, est marqué avec l'attribut <xref:System.Security.SecurityCriticalAttribute>.  
  
## Description de la règle  
 Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l'équivalence de type.  Lorsque le CLR détecte un tel type, il ne peut pas le charger avec une <xref:System.TypeLoadException> au moment de l'exécution.  En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l'équivalence de type manuellement plutôt qu'en comptant sur tlbimp et les compilateurs pour faire l'équivalence de type.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, supprimez l'attribut SecurityCritical.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## Exemple  
 Les exemples suivants présentent une interface, une méthode et un champ qui provoqueront le déclenchement de cette règle.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## Voir aussi  
 [Code transparent de sécurité, niveau 2](../Topic/Security-Transparent%20Code,%20Level%202.md)