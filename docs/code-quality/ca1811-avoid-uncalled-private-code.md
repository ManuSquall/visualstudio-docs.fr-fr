---
title: "CA1811&#160;: &#201;vitez le recours &#224; du code priv&#233; non appel&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidUncalledPrivateCode"
  - "CA1811"
helpviewer_keywords: 
  - "CA1811"
  - "AvoidUncalledPrivateCode"
ms.assetid: aadbba74-7821-475f-8980-34d17c0a0a8b
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1811&#160;: &#201;vitez le recours &#224; du code priv&#233; non appel&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUncalledPrivateCode|  
|CheckId|CA1811|  
|Catégorie|Microsoft.Performance|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un membre privé ou interne \(de niveau assembly\) n'a pas d'appelants dans l'assembly, et n'est appelé ni par le Common Language Runtime, ni par un délégué.  Les membres suivants ne sont pas vérifiés par cette règle :  
  
-   Membres d'interface explicites.  
  
-   Constructeurs statiques.  
  
-   Constructeurs de sérialisation.  
  
-   Méthodes marquées avec <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>.  
  
-   Membres qui constituent des substitutions.  
  
## Description de la règle  
 Cette règle peut rapporter des faux positifs en présence de points d'entrée qui ne sont actuellement pas identifiés par la logique de la règle.  En outre, un compilateur peut émettre un code ne pouvant être appelé dans un assembly.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le code ne pouvant être appelé ou ajoutez un code qui l'appelle.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle.  
  
## Règles connexes  
 [CA1812 : Évitez les classes internes non instanciées](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)  
  
 [CA1801 : Passez en revue les paramètres inutilisés](../Topic/CA1801:%20Review%20unused%20parameters.md)  
  
 [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md)