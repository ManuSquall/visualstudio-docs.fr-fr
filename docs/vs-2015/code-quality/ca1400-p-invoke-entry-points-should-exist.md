---
title: 'CA1400 : Des points d’entrée P-Invoke doivent exister | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0544fb21533e3f114ab1efdc315d844b4cad0acb
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47590294"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400 : Des points d'entrée P/Invoke doivent exister
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1400 : points d’entrée P-Invoke doivent exister](https://docs.microsoft.com/visualstudio/code-quality/ca1400-p-invoke-entry-points-should-exist).

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode publique ou protégée est marquée avec le <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. Si la règle ne peut pas trouver le nom de la méthode exactement tel qu’il est spécifié, il recherche ANSI ou des versions à caractères larges de la méthode ajoutant le nom de la méthode avec « A » ou « W ». Si aucune correspondance n’est trouvée, la règle essaie de localiser une fonction en utilisant le format de nom __stdcall (_MyMethod@12, où 12 représente la longueur des arguments). Si aucune correspondance n’est trouvée, et le nom de la méthode commence par '#', la règle recherche pour la fonction comme une référence d’ordinal au lieu d’une référence de nom.

## <a name="rule-description"></a>Description de la règle
 Aucune vérification de la compilation est disponible pour vous assurer que les méthodes marquées avec <xref:System.Runtime.InteropServices.DllImportAttribute> se trouvent dans la DLL non managée référencée. Si aucune fonction qui porte le nom spécifié se trouve dans la bibliothèque, ou les arguments de la méthode ne correspondent pas les arguments de fonction, le common language runtime lève une exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez la méthode qui a le <xref:System.Runtime.InteropServices.DllImportAttribute> attribut. Assurez-vous que la bibliothèque non managée existe et qu’il est dans le même répertoire que l’assembly qui contient la méthode. Si la bibliothèque est présent et correctement référencée, vérifiez que le nom de la méthode, le type de retour et la signature de l’argument correspond à la fonction de bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle lorsque la bibliothèque non managée est dans le même répertoire que l’assembly managé qui y fait référence. Il est possible de supprimer un avertissement de cette règle dans le cas où la bibliothèque non managée ne pourrait pas être localisée.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle. Aucune fonction nommée `DoSomethingUnmanaged` se produit dans kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>



