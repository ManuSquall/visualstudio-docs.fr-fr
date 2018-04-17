---
title: 'CA2146 : Les Types doivent être au moins aussi critiques que leurs types de base et les interfaces | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2146
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b956397818c171091e4ad982d92adc5e62370a39
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces"></a>CA2146 : Les types doivent être au moins aussi critiques que les types de base et les interfaces
|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type transparent est dérivé d’un type qui est marqué avec la <xref:System.Security.SecuritySafeCriticalAttribute> ou <xref:System.Security.SecurityCriticalAttribute>, ou un type qui est marqué avec la <xref:System.Security.SecuritySafeCriticalAttribute> attribut est dérivé d’un type qui est marqué avec la <xref:System.Security.SecurityCriticalAttribute> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle se déclenche lorsqu’un type dérivé a un attribut de transparence de sécurité qui n’est pas aussi critique que son type de base ou l’interface implémentée. Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées. Les violations de cette règle de transparence de niveau 2 provoquent un <xref:System.TypeLoadException> pour le type dérivé.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour résoudre cette violation, marquez le type dérivé ou d’implémentation avec un attribut de transparence est au moins aussi critique que le type de base ou interface.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]