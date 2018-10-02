---
title: 'CA2108 : Vérifiez la sécurité déclarative dans les types valeur | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90b294d4eca3cd549b2dfe95583fbf30f8371076
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588155"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108 : Vérifiez la sécurité déclarative dans les types valeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2108 : Vérifiez la sécurité déclarative dans les types valeur](https://docs.microsoft.com/visualstudio/code-quality/ca2108-review-declarative-security-on-value-types).

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type valeur public ou protégé est sécurisé par un [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) ou [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Description de la règle
 Les types valeur sont alloués et initialisés par leurs constructeurs par défaut avant d’exécutent d’autres constructeurs. Si un type valeur est sécurisé par un LinkDemand ou un à la demande, et l’appelant n’a pas d’autorisations qui répondent à la vérification de sécurité, un constructeur autre que la valeur par défaut échoue, et une exception de sécurité est levée. Le type de valeur n’est pas libéré ; Il reste dans l’état défini par son constructeur par défaut. Ne supposez pas que l’appelant qui passe une instance du type valeur est autorisé à créer ou accéder à l’instance.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Vous ne pouvez pas corriger une violation de cette règle, sauf si vous supprimez la vérification de sécurité du type, et utiliser la sécurité au niveau méthode vérifie à la place. Notez que la correction de la violation de cette manière n’empêchera pas les appelants dotés d’autorisations inadéquates d’obtenir des instances du type valeur. Vous devez vous assurer qu’une instance du type valeur, dans son état par défaut, n’expose pas d’informations sensibles et ne peut pas être utilisée de façon préjudiciable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous pouvez supprimer un avertissement de cette règle si un appelant peut obtenir des instances du type valeur dans son état par défaut sans que cela constitue une menace pour la sécurité.

## <a name="example"></a>Exemple
 L’exemple suivant montre une bibliothèque contenant un type valeur qui enfreint cette règle. Notez que le `StructureManager` type suppose qu’un appelant qui passe une instance du type valeur est autorisé à créer ou accéder à l’instance.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante montre la faiblesse de la bibliothèque.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Cet exemple produit la sortie suivante.

 **Constructeur personnalisé de structure : échouée de la requête. ** 
 **Nouvelles valeurs SecuredTypeStructure 100 100**
**nouvelles valeurs SecuredTypeStructure 200 200**
## <a name="see-also"></a>Voir aussi
 [Demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



