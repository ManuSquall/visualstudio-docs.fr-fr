---
title: "CA2126 : Liaison de types nécessitent des demandes d’héritage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 20ce42e001bcb0fe60f563cb4cfbee913315df27
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126 : Les demandes de liaison de types nécessitent des demandes d'héritage
|||  
|-|-|  
|TypeName|TypeLinkDemandsRequireInheritanceDemands|  
|CheckId|CA2126|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type unsealed public est protégé avec une demande de liaison, a une méthode substituable, et ni le type ni la méthode est protégée par une demande d’héritage.  
  
## <a name="rule-description"></a>Description de la règle  
 Une demande de liaison sur une méthode ou son type déclarant requiert que l’appelant immédiat de la méthode avoir l’autorisation spécifiée. Une demande d’héritage sur une méthode requiert une méthode de substitution pour avoir l’autorisation spécifiée. Une demande d’héritage sur un type requiert une classe dérivée a l’autorisation spécifiée.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, sécurisez le type ou la méthode avec une demande d’héritage pour la même autorisation que la demande de liaison.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle.  
  
 [!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
 [!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
 [!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2108 : Vérifiez la sécurité déclarative dans les types de valeurs](../code-quality/ca2108-review-declarative-security-on-value-types.md)  
  
 [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md)  
  
 [CA2122 : N’exposez pas indirectement des méthodes avec des demandes de liaison](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)  
  
 [CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)   
 [Demandes de liaison](/dotnet/framework/misc/link-demands)   
