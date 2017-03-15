---
title: "CA2133&#160;: Les d&#233;l&#233;gu&#233;s doivent lier les m&#233;thodes avec une transparence coh&#233;rente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2133&#160;: Les d&#233;l&#233;gu&#233;s doivent lier les m&#233;thodes avec une transparence coh&#233;rente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
> [!NOTE]
>  Cet avertissement est appliqué uniquement au code exécutant CoreCLR \(version du CLR qui est spécifique aux applications Web Silverlight\).  
  
## Cause  
 Cet avertissement déclenche sur une méthode qui lie un délégué marqué avec l'<xref:System.Security.SecurityCriticalAttribute> à une méthode qui est transparente ou marquée avec l'<xref:System.Security.SecuritySafeCriticalAttribute>.  L'avertissement déclenche également une méthode qui lie un délégué transparent ou critique sécurisé à une méthode critique.  
  
## Description de la règle  
 Les types délégués et les méthodes qu'ils lient doivent avoir une transparence cohérente.  Les délégués transparents et sécurisés \(safe\-critical\) peuvent être liés uniquement à d'autres méthodes transparentes et sécurisées \(safe\-critical\).  De même, les délégués critiques peuvent être liés uniquement à des méthodes critiques.  Ces règles de liaison vérifient que le seul code qui peut appeler une méthode via un délégué aurait également pu appeler directement la même méthode.  Par exemple, la liaison de règles empêche le code transparent d'appeler directement le code critique via un délégué transparent.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cet avertissement, modifiez la transparence du délégué ou de la méthode qu'il lie afin que la transparence des deux soit équivalente.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
### Code  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]