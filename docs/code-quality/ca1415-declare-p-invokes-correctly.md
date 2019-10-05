---
title: 'CA1415 : Déclarer correctement les méthodes P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99274abee2c05a1bd33e34c9eb02cc928c1b54b0
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234610"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415 : Déclarer correctement les méthodes P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture : si P/Invoke qui déclare le paramètre ne peut pas être affiché à l’extérieur de l’assembly. Avec rupture : si l’appel P/Invoke qui déclare le paramètre peut être affiché à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
Une méthode d’appel de code non managé est déclarée de manière incorrecte.

## <a name="rule-description"></a>Description de la règle
Une méthode d’appel de plateforme accède au code non managé et est définie à l' `Declare` aide du [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mot clé <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>dans ou. Actuellement, cette règle recherche des déclarations de méthode d’appel de code non managé qui ciblent des fonctions Win32 qui ont un pointeur vers un paramètre de structure OVERLAPPED et le paramètre managé correspondant <xref:System.Threading.NativeOverlapped?displayProperty=fullName> n’est pas un pointeur vers une structure.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, déclarez correctement la méthode d’appel de code non managé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
L’exemple suivant montre des méthodes d’appel de code non managé qui violent la règle et satisfont à la règle.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Voir aussi
[Interopération avec du code non managé](/dotnet/framework/interop/index)