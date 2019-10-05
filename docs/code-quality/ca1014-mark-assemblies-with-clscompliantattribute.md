---
title: 'CA1014 : Marquer les assemblys avec CLSCompliantAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 387eb464959fba522e31f9586998335cb306d844
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236323"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014 : Marquer les assemblys avec CLSCompliantAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Aucun <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut n’est appliqué à un assembly.

## <a name="rule-description"></a>Description de la règle
La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Une bonne conception impose que tous les assemblys indiquent explicitement la conformité <xref:System.CLSCompliantAttribute>CLS avec. Si l’attribut n’est pas présent dans un assembly, l’assembly n’est pas conforme.

Un assembly conforme CLS peut contenir des types ou des membres de type qui ne sont pas conformes.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Au lieu de marquer l’intégralité de l’assembly comme non conforme, vous devez déterminer quels types ou membres de type ne sont pas conformes et marquer ces éléments comme tels. Si possible, vous devez fournir une alternative conforme à CLS pour les membres non conformes afin que le plus grand public possible puisse accéder à toutes les fonctionnalités de votre assembly.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle. Si vous ne souhaitez pas que l’assembly soit conforme, appliquez l’attribut et affectez-lui `false`la valeur.

## <a name="example"></a>Exemple
L’exemple suivant montre un assembly dont l' <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut est appliqué et qui déclare qu’il est conforme à la spécification CLS.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Voir aussi

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)