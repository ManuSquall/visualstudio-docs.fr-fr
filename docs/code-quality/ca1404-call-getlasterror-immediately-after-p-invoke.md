---
title: 'CA1404 : Appeler GetLastError immédiatement après P-Invoke'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f29549f6b062a34a8b9e49bc7418b05d2d4e8831
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900309"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404 : Appeler GetLastError immédiatement après P/Invoke
|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un appel est fait à la <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> méthode ou l’équivalent Win32 `GetLastError` (fonction) et l’appel immédiatement avant n’est pas à une plateforme appeler la méthode.

## <a name="rule-description"></a>Description de la règle
 Une plateforme de l’appel de méthode accède à un code non managé et est définie à l’aide de la `Declare` mot clé dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attribut. En règle générale, en cas d’échec, les fonctions non managées appellent Win32 `SetLastError` fonction pour définir un code d’erreur associé à l’échec. L’appelant de la fonction d’échec appelle Win32 `GetLastError` fonction pour récupérer le code d’erreur et de déterminer la cause de l’échec. Le code d’erreur est conservé sur une base par thread et est remplacé par l’appel suivant à `SetLastError`. Après un appel à une plateforme ayant échoué appeler la méthode, le code managé peut récupérer le code d’erreur en appelant le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> (méthode). Comme le code d’erreur peut être remplacé par des appels internes à partir d’autres méthodes de bibliothèque de classes managée, la `GetLastError` ou <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> méthode doit être appelée immédiatement après l’appel de méthode non managé.

 La règle ignore les appels à ce qui suit membres gérés lorsqu’ils se produisent entre l’appel à la plate-forme d’appel de méthode et l’appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Ces membres ne modifient pas l’erreur code et sont utiles pour déterminer la réussite d’une plateforme appellent les appels de méthode.

-   <xref:System.IntPtr.Zero?displayProperty=fullName>

-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, placez l’appel à <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> afin qu’il suive immédiatement l’appel à la plate-forme appeler la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si la méthode d’appel du code entre la plate-forme et le <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> appel de méthode ne peut pas explicitement ou implicitement provoquer le code d’erreur à modifier.

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui enfreint la règle et une méthode qui satisfait la règle.

 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1060 : Déplacer P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400 : Des points d’entrée P/Invoke doivent exister.](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401 : Les P/Invoke ne doivent pas être visible](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205 : Utilisez des équivalents managés de l’API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)