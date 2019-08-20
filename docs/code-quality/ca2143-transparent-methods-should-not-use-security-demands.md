---
title: 'CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2143
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 532a10740b0617f32e4f970da8dc2a7e2807f792
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920468"
---
# <a name="ca2143-transparent-methods-should-not-use-security-demands"></a>CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité

|||
|-|-|
|TypeName|TransparentMethodsShouldNotDemand|
|CheckId|CA2143|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode ou un type tranparent est marqué de manière <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> déclarative avec une `.Demand` demande ou la <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> méthode appelle la méthode.

## <a name="rule-description"></a>Description de la règle
Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Le code transparent de sécurité doit utiliser des demandes complètes pour prendre des décisions de sécurité et le code critique sécurisé ne doit pas dépendre du code transparent pour l’exécution de ces demandes. Tout code qui effectue des vérifications de sécurité, comme les demandes de sécurité, doit plutôt être critique sécurisé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
En général, pour corriger une violation de cette règle, marquez la méthode avec <xref:System.Security.SecuritySafeCriticalAttribute> l’attribut. Vous pouvez également supprimer la demande.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
Les fichiers de règles sur le code suivant, car une méthode transparente effectue une demande de sécurité déclarative.

[!code-csharp[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]

## <a name="see-also"></a>Voir aussi
[CA2142 Le code transparent ne doit pas être protégé avec LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)