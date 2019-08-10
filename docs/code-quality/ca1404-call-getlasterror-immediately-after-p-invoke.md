---
title: 'CA1404 : Appeler GetLastError immédiatement après P-Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 03add1625c4d59bb180f9f0f08692e67bee8047b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922076"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404 : Appeler GetLastError immédiatement après P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Catégorie|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un appel est fait à la <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> méthode ou à la fonction `GetLastError` Win32 équivalente, et l’appel qui vient juste avant n’est pas une méthode d’appel de code non managé.

## <a name="rule-description"></a>Description de la règle
Une méthode d’appel de plateforme accède au code non managé et est définie à l' `Declare` aide du [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mot clé <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> dans ou de l’attribut. En général, en cas d’échec, les fonctions non managées appellent la fonction Win32 `SetLastError` pour définir un code d’erreur associé à l’échec. L’appelant de la fonction failed appelle la `GetLastError` fonction Win32 pour récupérer le code d’erreur et déterminer la cause de l’échec. Le code d’erreur est conservé par thread et remplacé par l’appel suivant à `SetLastError`. Après un appel à une méthode d’appel de plateforme qui a échoué, le code managé peut récupérer le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> code d’erreur en appelant la méthode. Étant donné que le code d’erreur peut être remplacé par des appels internes d’autres méthodes de la `GetLastError` bibliothèque <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> de classes managée, la méthode ou doit être appelée immédiatement après l’appel de la méthode d’appel de code non managé.

La règle ignore les appels aux membres managés suivants lorsqu’ils se produisent entre l’appel à la méthode d’appel de code <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>non managé et l’appel à. Ces membres ne modifient pas le code d’erreur et sont utiles pour déterminer la réussite de certains appels de méthode d’appel de code non managé.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, déplacez l’appel vers <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> afin qu’il suive immédiatement l’appel à la méthode d’appel de code non managé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le code entre l’appel de la méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> d’appel de code non managé et l’appel de la méthode ne peut pas explicitement ou implicitement entraîner la modification du code d’erreur.

## <a name="example"></a>Exemple
L’exemple suivant montre une méthode qui enfreint la règle et une méthode qui satisfait la règle.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Règles associées
[CA1060 Déplacer les P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400 Des points d’entrée P/Invoke doivent exister](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401 Les P/Invoke ne doivent pas être visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101 Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205 Utiliser des équivalents managés de l’API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)