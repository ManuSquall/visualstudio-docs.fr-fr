---
title: "CA2130 : Les constantes critiques de sécurité doivent être transparentes | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2130
ms.assetid: 344c7f7b-9130-4675-ae7f-9fa260cc9789
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9975acd53976b1668e158fd3e906c669a0f5ed49
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2130-security-critical-constants-should-be-transparent"></a>CA2130 : Les constantes critiques de sécurité doivent être transparentes
|||  
|-|-|  
|TypeName|ConstantsShouldBeTransparent|  
|CheckId|CA2130|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un champ constant ou un membre d’énumération est marqué avec le <xref:System.Security.SecurityCriticalAttribute>.  
  
## <a name="rule-description"></a>Description de la règle  
 La mise en application de la transparence n'est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu'aucune recherche ne soit requise au moment de l'exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez l’attribut SecurityCritical à partir du champ ou une valeur.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans les exemples suivants, la valeur enum `EnumWithCriticalValues.CriticalEnumValue` et la constante `CriticalConstant` génère cet avertissement. Pour résoudre les problèmes, supprimez le [`SecurityCritical`] attribut pour qu’elles soient transparentes de sécurité.  
  
 [!code-csharp[FxCop.Security.CA2130.ConstantsShouldBeTransparent#1](../code-quality/codesnippet/CSharp/ca2130-security-critical-constants-should-be-transparent_1.cs)]