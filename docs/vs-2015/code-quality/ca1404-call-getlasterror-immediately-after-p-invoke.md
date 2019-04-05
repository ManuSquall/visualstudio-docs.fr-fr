---
title: 'CA1404 : Appeler GetLastError immédiatement après P-Invoke | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a7f1f4d036bd035368cce10684899d880481e37b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938240"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404 : Appeler GetLastError immédiatement après P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un appel est effectué pour le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> méthode ou équivalents Win32 `GetLastError` (fonction) et l’appel immédiatement avant n’est pas à une plateforme appeler la méthode.

## <a name="rule-description"></a>Description de la règle
 Une plateforme d’appeler la méthode accède à un code non managé et est définie à l’aide de la `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut. En règle générale, en cas d’échec, les fonctions non managées appellent Win32 `SetLastError` fonction permettant de définir un code d’erreur associé à l’échec. L’appelant de la fonction ayant échouée appelle la fonction Win32 `GetLastError` fonction pour récupérer le code d’erreur et de déterminer la cause de l’échec. Le code d’erreur est conservé sur un thread par thread et est remplacé par l’appel suivant à `SetLastError`. Après un appel à une plateforme ayant échoué appeler la méthode, le code managé peut récupérer le code d’erreur en appelant le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> (méthode). Étant donné que le code d’erreur peut être écrasé par les appels internes à partir d’autres méthodes de bibliothèque de classes managée, la `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> méthode doit être appelée immédiatement après l’appel de méthode non managé.

 La règle ignore les appels à ce qui suit membres gérés lorsqu’ils se produisent entre l’appel à la plateforme d’appel de méthode et l’appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ces membres ne changent pas l’erreur code et s’avèrent utiles pour déterminer la réussite d’une plateforme les appels de méthode d’appel.

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, placez l’appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> afin qu’il suive immédiatement l’appel à la plateforme appeler la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la méthode d’appel du code entre la plateforme et le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> appel de méthode ne peut pas explicitement ou implicitement provoquer le code d’erreur à modifier.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui viole la règle et une méthode qui satisfait la règle.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1060 : Déplacer les P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400 : Points d’entrée P/Invoke doivent exister](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401 : P/Invoke ne doivent pas être visible](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205 : Utilisez des équivalents managés de l’API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
