---
title: 'CA1414 : Marquer les arguments P-Invoke booléens comme MarshalAs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e444519c5a6d6d1547b782006d063e90d4a3b976
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58952755"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un appel de méthode déclaration inclut un <xref:System.Boolean?displayProperty=fullName> paramètre ou valeur de retour, mais le <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attribut n’est pas appliqué à la valeur de paramètre ou de retour.

## <a name="rule-description"></a>Description de la règle
 Une plateforme d’appeler la méthode accède à un code non managé et est définie à l’aide de la `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Spécifie le comportement de marshaling est utilisé pour convertir les types de données entre code managé et non managé. Types de nombreuses données simples, tels que <xref:System.Byte?displayProperty=fullName> et <xref:System.Int32?displayProperty=fullName>, ont une représentation unique dans le code non managé et ne nécessitent pas de spécification de leur comportement de marshaling ; le common language runtime fournit automatiquement le comportement correct.

 Le <xref:System.Boolean> type de données a plusieurs représentations en code non managé. Lorsque le <xref:System.Runtime.InteropServices.MarshalAsAttribute> n’est pas spécifié, la valeur par défaut de marshaling de comportement pour le <xref:System.Boolean> est de type de données <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Il s’agit d’un entier 32 bits, ce qui n’est pas approprié dans toutes les circonstances. La représentation booléenne qui est requis par la méthode non managée doit être déterminée et mis en correspondance avec le texte approprié <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType.Bool est du type BOOL Win32, qui est toujours 4 octets. UnmanagedType.U1 doit être utilisé pour C++ `bool` ou d’autres types de 1 octet. Pour plus d’informations, consultez [Marshaling par défaut pour les Types booléens](http://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appliquez <xref:System.Runtime.InteropServices.MarshalAsAttribute> à la <xref:System.Boolean> paramètre ou valeur de retour. Définissez la valeur de l’attribut approprié <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Même si le comportement de marshaling par défaut est approprié, le code est plus faciles à gérer lorsque le comportement est spécifié explicitement.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes qui sont marqués avec le bon d’appel de code <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributs.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Marshaling par défaut pour les Types booléens](http://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interopération avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
