---
title: 'CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bf5bb8320a8876582cc325ecf973c83593777193
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920495"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode transparente requiert un <xref:System.Security.Permissions.SecurityAction> ou une autre demande de sécurité.

## <a name="rule-description"></a>Description de la règle
Cette règle se déclenche sur les méthodes transparentes qui requièrent l’accès de LinkDemands. Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Étant donné que les méthodes transparentes sont supposées être neutres pour la sécurité, elles ne doivent pas prendre de décisions en matière de sécurité. En outre, un code critique sécurisé, qui prend des décisions de sécurité, ne doit pas s’appuyer sur du code transparent pour avoir pris une telle décision.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, supprimez la demande de liaison sur la méthode transparente ou marquez <xref:System.Security.SecuritySafeCriticalAttribute> la méthode avec l’attribut si elle effectue des vérifications de sécurité, telles que des demandes de sécurité.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemples
Dans l’exemple suivant, la règle est déclenchée sur la méthode, car la méthode est transparente et est marquée <xref:System.Security.PermissionSet> avec un LinkDemand <xref:System.Security.Permissions.SecurityAction>qui contient un.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Ne supprimez aucun avertissement de cette règle.