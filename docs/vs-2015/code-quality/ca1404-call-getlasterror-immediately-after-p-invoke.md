---
title: 'CA1404 : appeler GetLastError immédiatement après P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661324"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404 : Appeler GetLastError immédiatement après P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un appel est passé à la méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> ou à la fonction Win32 équivalente `GetLastError`, et l’appel qui vient immédiatement avant n’est pas une méthode d’appel de code non managé.

## <a name="rule-description"></a>Description de la règle
 Une méthode d’appel de plate-forme accède au code non managé et est définie à l’aide du mot clé `Declare` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou de l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. En général, en cas d’échec, les fonctions non managées appellent la fonction Win32 `SetLastError` pour définir un code d’erreur associé à l’échec. L’appelant de la fonction failed appelle la fonction Win32 `GetLastError` pour récupérer le code d’erreur et déterminer la cause de l’échec. Le code d’erreur est conservé par thread et remplacé par l’appel suivant à `SetLastError`. Après un appel à une méthode d’appel de plateforme qui a échoué, le code managé peut récupérer le code d’erreur en appelant la méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Étant donné que le code d’erreur peut être remplacé par des appels internes d’autres méthodes de la bibliothèque de classes managées, la méthode `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> doit être appelée immédiatement après l’appel de la méthode d’appel de code non managé.

 La règle ignore les appels aux membres managés suivants lorsqu’ils se produisent entre l’appel à la méthode d’appel de code non managé et l’appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ces membres ne modifient pas le code d’erreur et sont utiles pour déterminer la réussite de certains appels de méthode d’appel de code non managé.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, déplacez l’appel vers <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> afin qu’il suive immédiatement l’appel à la méthode d’appel de code non managé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le code entre l’appel de la méthode d’appel de code non managé et l’appel de méthode <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> ne peut pas explicitement ou implicitement entraîner la modification du code d’erreur.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui enfreint la règle et une méthode qui satisfait la règle.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1060 : Déplacer les P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400 : Des points d’entrée P/Invoke doivent exister](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401 : Les P/Invoke ne doivent pas être visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 : Spécifier le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205 : Utilisez des équivalents managés de l’API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
