---
title: "CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2133
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f191c9f67fd09e72d4cb57ded2fa88135c388611
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2133-delegates-must-bind-to-methods-with-consistent-transparency"></a>CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente
|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
> [!NOTE]
>  Cet avertissement est appliqué uniquement au code qui est en cours d’exécution (la version du CLR qui est spécifique aux applications Silverlight Web) CoreCLR.  
  
## <a name="cause"></a>Cause  
 Cet avertissement se déclenche sur une méthode qui lie un délégué qui est marquée avec la <xref:System.Security.SecurityCriticalAttribute> à une méthode qui est transparente ou marquée avec le <xref:System.Security.SecuritySafeCriticalAttribute>. L'avertissement déclenche également une méthode qui lie un délégué transparent ou critique sécurisé à une méthode critique.  
  
## <a name="rule-description"></a>Description de la règle  
 Les types délégués et les méthodes auxquelles elles se lient doivent avoir une transparence cohérente. Les délégués transparents et critique sécurisé ne peuvent lier à d’autres méthodes transparents ou critique sécurisé. De même, les délégués critiques peuvent être liés uniquement aux méthodes critiques. Ces règles de liaison vérifient que le seul code que vous pouvez appeler une méthode via un délégué aurait également pu appeler la même méthode directement. Par exemple, règles de liaison d’empêchent le code transparent d’appeler du code critique directement via un délégué transparent.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cet avertissement, modifiez la transparence du délégué ou de la méthode qu’il lie afin que la transparence des deux sont équivalentes.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]