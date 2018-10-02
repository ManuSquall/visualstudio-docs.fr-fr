---
title: 'CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité | Microsoft Docs'
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
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ed55d0645e70303f53bbd0d95021d05bb560fe23
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590017"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2143 : les méthodes transparentes ne doivent pas utiliser de demandes de sécurité](https://docs.microsoft.com/visualstudio/code-quality/ca2143-transparent-methods-should-not-use-security-demands).

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode ou type de transparent est marquée de façon déclarative avec une <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> `.Demand` à la demande ou les appels de méthode le <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> (méthode).

## <a name="rule-description"></a>Description de la règle
 Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Le code transparent de sécurité doit utiliser des demandes complètes pour prendre des décisions de sécurité et le code critique sécurisé ne doit pas dépendre du code transparent pour l'exécution de ces demandes. Tout code qui effectue des vérifications de sécurité, telles que des demandes de sécurité doit être critique de sécurité à la place.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 En règle générale, pour corriger une violation de cette règle, marquez la méthode avec le <xref:System.Security.SecuritySafeCriticalAttribute> attribut. Vous pouvez également supprimer la demande.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 La règle de fichiers sur le code suivant, car une méthode transparente effectue une demande de sécurité déclarative.

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2143.transparentmethodsshouldnotdemand/cs/ca2143 - transparentmethodsshouldnotdemand.cs#1)]

## <a name="see-also"></a>Voir aussi
 [CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)



