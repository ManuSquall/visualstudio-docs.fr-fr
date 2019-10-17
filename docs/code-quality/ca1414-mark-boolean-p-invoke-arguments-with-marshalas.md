---
title: 'CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0f8140e78d1ee3340e9ee5441e183b55d4c5111c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444175"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une déclaration de méthode d’appel de code non managé comprend un paramètre <xref:System.Boolean?displayProperty=fullName> ou une valeur de retour, mais l’attribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> n’est pas appliqué au paramètre ou à la valeur de retour.

## <a name="rule-description"></a>Description de la règle
Une méthode d’appel de code non managé accède au code non managé et est définie à l’aide du mot clé `Declare` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ou le <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> spécifie le comportement de marshaling utilisé pour convertir les types de données entre du code managé et du code non managé. De nombreux types de données simples, tels que <xref:System.Byte?displayProperty=fullName> et <xref:System.Int32?displayProperty=fullName>, ont une représentation unique dans du code non managé et ne nécessitent pas de spécification de leur comportement de marshaling. le common language runtime fournit automatiquement le comportement correct.

Le type de données <xref:System.Boolean> a plusieurs représentations dans du code non managé. Lorsque le <xref:System.Runtime.InteropServices.MarshalAsAttribute> n’est pas spécifié, le comportement de marshaling par défaut pour le type de données <xref:System.Boolean> est <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Il s’agit d’un entier 32 bits, qui n’est pas approprié dans toutes les circonstances. La représentation booléenne requise par la méthode non managée doit être déterminée et mise en correspondance avec le @no__t approprié. UnmanagedType. bool est le type booléen Win32, qui est toujours de 4 octets. UnmanagedType. U1 doit être utilisé pour C++ `bool` ou d’autres types de 1 octet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, appliquez <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre <xref:System.Boolean> ou à la valeur de retour. Définissez la valeur de l’attribut sur le @no__t approprié.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. Même si le comportement de marshaling par défaut est approprié, le code est plus facile à gérer lorsque le comportement est spécifié explicitement.

## <a name="example"></a>Exemple

L’exemple suivant montre des méthodes d’appel de code non managé marquées avec les attributs <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriés.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Règles associées
[CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901.md)

[CA2101 : Spécifier le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interopération avec du code non managé](/dotnet/framework/interop/index)
