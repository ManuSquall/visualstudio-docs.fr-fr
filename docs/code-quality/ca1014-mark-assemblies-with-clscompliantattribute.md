---
title: 'CA1014 : Marquer les assemblys avec CLSCompliantAttribute'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51e5a43a402bb215a939b37354dd30f24e4d5d14
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31898178"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014 : Marquer les assemblys avec CLSCompliantAttribute
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un assembly n’a pas la <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut appliqué à celui-ci.

## <a name="rule-description"></a>Description de la règle
 La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>. Si l’attribut n’est pas présent sur un assembly, l’assembly n’est pas conforme.

 Il est possible pour un assembly conforme CLS pour contiennent des types ou membres qui ne sont pas conformes.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez l’attribut à l’assembly. Au lieu de marquer l’intégralité de l’assembly comme non conforme, vous devez déterminer l’ou les membres de type ne sont pas conformes et marquer ces éléments comme tel. Si possible, vous devez fournir une alternative conforme CLS pour les membres non conformes afin que l’audience la plus large possible puisse accéder à toutes les fonctionnalités de votre assembly.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Si vous ne souhaitez pas que l’assembly soit conforme, appliquez l’attribut et définissez sa valeur sur `false`.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly qui a le <xref:System.CLSCompliantAttribute?displayProperty=fullName> attribut appliqué qui déclare conformes à CLS.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Voir aussi
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)