---
title: "CA1400 : Des points d'entrée P-Invoke doivent exister"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5503f00995a4720207ea0ea9c29201d379e70adb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234903"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400 : Des points d'entrée P/Invoke doivent exister

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode publique ou protégée est marquée avec <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. Si la règle ne peut pas trouver le nom de la méthode exactement tel qu’il est spécifié, elle recherche des versions ANSI ou à caractères larges de la méthode en suffixant le nom de la méthode avec « A » ou « W ». Si aucune correspondance n’est trouvée, la règle tente de localiser une fonction en utilisant le format de nom_MyMethod@12_ _ stdcall (, où 12 représente la longueur des arguments). Si aucune correspondance n’est trouvée et que le nom de la méthode commence par « # », la règle recherche la fonction en tant que référence ordinale au lieu d’une référence de nom.

## <a name="rule-description"></a>Description de la règle
Aucun contrôle au moment de la compilation n’est disponible pour s’assurer que les méthodes <xref:System.Runtime.InteropServices.DllImportAttribute> marquées avec sont situées dans la dll non managée référencée. Si aucune fonction portant le nom spécifié n’est dans la bibliothèque, ou si les arguments de la méthode ne correspondent pas aux arguments de la fonction, le common language runtime lève une exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, corrigez la méthode qui a <xref:System.Runtime.InteropServices.DllImportAttribute> l’attribut. Assurez-vous que la bibliothèque non managée existe et qu’elle se trouve dans le même répertoire que l’assembly qui contient la méthode. Si la bibliothèque est présente et correctement référencée, vérifiez que le nom de la méthode, le type de retour et la signature d’argument correspondent à la fonction de bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez pas un avertissement de cette règle lorsque la bibliothèque non managée se trouve dans le même répertoire que l’assembly managé qui y fait référence. Il peut être possible de supprimer sans risque un avertissement de cette règle dans le cas où la bibliothèque non managée n’a pas pu être localisée.

## <a name="example"></a>Exemple
L’exemple suivant montre un type qui viole la règle. Aucune fonction nommée `DoSomethingUnmanaged` ne se produit dans kernel32. dll.

[!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>