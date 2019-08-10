---
title: 'CA1414 : Marquer les arguments P-Invoke booléens comme MarshalAs'
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
ms.openlocfilehash: 8e8d47b73009e0bd742c989ddc0311644453e5d9
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921867"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Catégorie|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une déclaration de méthode d’appel de <xref:System.Boolean?displayProperty=fullName> code non managé comprend un paramètre <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> ou une valeur de retour, mais l’attribut n’est pas appliqué au paramètre ou à la valeur de retour.

## <a name="rule-description"></a>Description de la règle
Une méthode d’appel de plateforme accède au code non managé et est définie à l' `Declare` aide du [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mot clé <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>dans ou. <xref:System.Runtime.InteropServices.MarshalAsAttribute>Spécifie le comportement de marshaling utilisé pour convertir les types de données entre du code managé et du code non managé. De nombreux types de données simples, <xref:System.Byte?displayProperty=fullName> tels <xref:System.Int32?displayProperty=fullName>que et, ont une représentation unique dans du code non managé et ne nécessitent pas de spécification de leur comportement de marshaling; le Common Language Runtime fournit automatiquement le comportement correct.

Le <xref:System.Boolean> type de données a plusieurs représentations dans du code non managé. Lorsque n’est pas spécifié, le comportement de marshaling par défaut <xref:System.Boolean> pour le type de données est. <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> <xref:System.Runtime.InteropServices.MarshalAsAttribute> Il s’agit d’un entier 32 bits, qui n’est pas approprié dans toutes les circonstances. La représentation booléenne requise par la méthode non managée doit être déterminée et mise en correspondance avec le approprié <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool est le type booléen Win32, qui est toujours de 4 octets. UnmanagedType. U1 doit être utilisé pour C++ `bool` ou d’autres types de 1 octet.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, appliquez <xref:System.Runtime.InteropServices.MarshalAsAttribute> au paramètre <xref:System.Boolean> ou à la valeur de retour. Affectez la valeur appropriée <xref:System.Runtime.InteropServices.UnmanagedType>à l’attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. Même si le comportement de marshaling par défaut est approprié, le code est plus facile à gérer lorsque le comportement est spécifié explicitement.

## <a name="example"></a>Exemples

L’exemple suivant montre des méthodes d’appel de code non managé marquées avec les attributs appropriés <xref:System.Runtime.InteropServices.MarshalAsAttribute> .

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Règles associées
[CA1901 Les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101 Spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interopération avec du code non managé](/dotnet/framework/interop/index)