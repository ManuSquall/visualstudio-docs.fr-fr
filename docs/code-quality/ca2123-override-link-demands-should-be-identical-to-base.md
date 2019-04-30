---
title: 'CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52959279bca5aa0f86722050f6118f64997a901d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545046"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée dans un type public substitue une méthode ou implémente une interface et n’a pas le même [demandes de liaison](/dotnet/framework/misc/link-demands) que l’interface ou une méthode virtuelle.

## <a name="rule-description"></a>Description de la règle
 Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune. Une violation est signalée si la méthode ou la méthode de base a une demande de liaison et l’autre n’est pas le cas.

 Si cette règle est violée, un appelant malveillant peut contourner la demande de liaison simplement en appelant la méthode non sécurisée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appliquez la même demande de liaison à la méthode de substitution ou l’implémentation. Si ce n’est pas possible, marquez la méthode avec une demande complète ou supprimer complètement de l’attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre différentes violations de cette règle.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](/dotnet/standard/security/secure-coding-guidelines)
- [Demandes de liaison](/dotnet/framework/misc/link-demands)