---
title: 'CA1414 : marquer les arguments P-Invoke booléens avec MarshalAs | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548380"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une déclaration de méthode d’appel de code non managé comprend un <xref:System.Boolean?displayProperty=fullName> paramètre ou une valeur de retour, mais l' <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attribut n’est pas appliqué au paramètre ou à la valeur de retour.

## <a name="rule-description"></a>Description de la règle
 Une méthode d’appel de plateforme accède au code non managé et est définie à l’aide du `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute>Spécifie le comportement de marshaling utilisé pour convertir les types de données entre du code managé et du code non managé. De nombreux types de données simples, tels que <xref:System.Byte?displayProperty=fullName> et <xref:System.Int32?displayProperty=fullName> , ont une représentation unique dans du code non managé et ne nécessitent pas de spécification de leur comportement de marshaling ; le Common Language Runtime fournit automatiquement le comportement correct.

 Le <xref:System.Boolean> type de données a plusieurs représentations dans du code non managé. Lorsque <xref:System.Runtime.InteropServices.MarshalAsAttribute> n’est pas spécifié, le comportement de marshaling par défaut pour le <xref:System.Boolean> type de données est <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Il s’agit d’un entier 32 bits, qui n’est pas approprié dans toutes les circonstances. La représentation booléenne requise par la méthode non managée doit être déterminée et mise en correspondance avec le approprié <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool est le type booléen Win32, qui est toujours de 4 octets. UnmanagedType. U1 doit être utilisé pour C++ `bool` ou d’autres types de 1 octet. Pour plus d’informations, consultez [marshaling par défaut pour les types booléens](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, appliquez <xref:System.Runtime.InteropServices.MarshalAsAttribute> au <xref:System.Boolean> paramètre ou à la valeur de retour. Affectez la valeur appropriée à l’attribut <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Même si le comportement de marshaling par défaut est approprié, le code est plus facile à gérer lorsque le comportement est spécifié explicitement.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux méthodes d’appel de code non managé marquées avec les <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributs appropriés.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1901 : les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101 : spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Marshaling par défaut pour les types booléens](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interopérants avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
