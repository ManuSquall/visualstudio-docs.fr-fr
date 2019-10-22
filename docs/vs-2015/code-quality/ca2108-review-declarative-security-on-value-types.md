---
title: 'CA2108 : passez en revue la sécurité déclarative sur les types valeur | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a05b7098d75d368f893b2504f7663675611bc0ce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658720"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108 : Vérifiez la sécurité déclarative dans les types valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type valeur public ou protégé est sécurisé par des demandes de [données et de modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) ou de [liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Description de la règle
 Les types valeur sont alloués et initialisés par leurs constructeurs par défaut avant que d’autres constructeurs ne s’exécutent. Si un type valeur est sécurisé par une demande ou un LinkDemand, et que l’appelant n’a pas les autorisations qui satisfont à la vérification de sécurité, tout constructeur autre que la valeur par défaut échoue et une exception de sécurité est levée. Le type de valeur n’est pas libéré ; elle reste dans l’état défini par son constructeur par défaut. Ne partez pas du principe qu’un appelant qui passe une instance du type valeur a l’autorisation de créer ou d’accéder à l’instance.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Vous ne pouvez pas corriger une violation de cette règle, sauf si vous supprimez la vérification de sécurité du type et utilisez les vérifications de sécurité au niveau de la méthode à la place. Notez que la résolution de la violation de cette manière n’empêchera pas les appelants avec des autorisations inappropriées d’obtenir des instances du type valeur. Vous devez vous assurer qu’une instance du type valeur, dans son état par défaut, n’expose pas d’informations sensibles et qu’elle ne peut pas être utilisée de manière dangereuse.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer un avertissement de cette règle si un appelant peut obtenir des instances du type valeur dans son état par défaut sans compromettre la sécurité.

## <a name="example"></a>Exemple
 L’exemple suivant montre une bibliothèque contenant un type valeur qui ne respecte pas cette règle. Notez que le type `StructureManager` suppose qu’un appelant qui passe une instance du type valeur a l’autorisation de créer ou d’accéder à l’instance.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante illustre la faiblesse de la bibliothèque.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Cet exemple produit la sortie suivante.

 **Constructeur personnalisé de structure : échec de la requête.** 
**nouvelles valeurs SecuredTypeStructure 100 100** 
**nouvelles valeurs SecuredTypeStructure 200 200**
## <a name="see-also"></a>Voir aussi
 [Liaison des demandes](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [de données et de modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
