---
title: 'CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7abb977d69f6221e396a5aea8c2268d505b4ab21
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870456"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité

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

 [!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Voir aussi
 [CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)