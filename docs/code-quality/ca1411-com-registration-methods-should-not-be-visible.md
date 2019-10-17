---
title: "CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1411
- ComRegistrationMethodsShouldNotBeVisible
helpviewer_keywords:
- ComRegistrationMethodsShouldNotBeVisible
- CA1411
ms.assetid: a59f96f1-1f38-4596-b656-947df5c55311
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b39e16b2a94a22582b9f369e647676541fa4220d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440170"
---
# <a name="ca1411-com-registration-methods-should-not-be-visible"></a>CA1411 : Les méthodes d'inscription COM ne doivent pas être visibles

|||
|-|-|
|TypeName|ComRegistrationMethodsShouldNotBeVisible|
|CheckId|CA1411|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode marquée avec le <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> ou l’attribut <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> est visible de l’extérieur.

## <a name="rule-description"></a>Description de la règle
Lorsqu’un assembly est inscrit auprès du modèle COM (Component Object Model), les entrées sont ajoutées au registre pour chaque type visible par COM dans l’assembly. Les méthodes marquées avec les attributs <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> et <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute> sont appelées au cours des processus d’inscription et d’annulation de l’inscription, respectivement, pour exécuter le code utilisateur qui est spécifique à l’inscription/annulation de l’inscription de ces types. Ce code ne doit pas être appelé en dehors de ces processus.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, remplacez l’accessibilité de la méthode par `private` ou `internal` (`Friend` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre deux méthodes qui violent la règle.

[!code-csharp[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/CSharp/ca1411-com-registration-methods-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Interoperability.ComRegistration2#1](../code-quality/codesnippet/VisualBasic/ca1411-com-registration-methods-should-not-be-visible_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.RegistrationServices?displayProperty=fullName>
- [Inscription d’assemblys dans COM](/dotnet/framework/interop/registering-assemblies-with-com)
- [Regasm.exe (outil d’inscription d’assemblys)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)
