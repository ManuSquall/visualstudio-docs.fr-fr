---
title: 'CA1400 : les points d’entrée P-Invoke doivent exister | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548302"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400 : Des points d'entrée P/Invoke doivent exister
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Une méthode publique ou protégée est marquée avec <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. Si la règle ne peut pas trouver le nom de la méthode exactement tel qu’il est spécifié, elle recherche des versions ANSI ou à caractères larges de la méthode en suffixant le nom de la méthode avec « A » ou « W ». Si aucune correspondance n’est trouvée, la règle tente de localiser une fonction en utilisant le format de nom _MyMethod@12 de __stdcall (, où 12 représente la longueur des arguments). Si aucune correspondance n’est trouvée et que le nom de la méthode commence par « # », la règle recherche la fonction en tant que référence ordinale au lieu d’une référence de nom.

## <a name="rule-description"></a>Description de la règle
 Aucun contrôle au moment de la compilation n’est disponible pour s’assurer que les méthodes marquées avec <xref:System.Runtime.InteropServices.DllImportAttribute> sont situées dans la dll non managée référencée. Si aucune fonction portant le nom spécifié n’est dans la bibliothèque, ou si les arguments de la méthode ne correspondent pas aux arguments de la fonction, le common language runtime lève une exception.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez la méthode qui a l' <xref:System.Runtime.InteropServices.DllImportAttribute> attribut. Assurez-vous que la bibliothèque non managée existe et qu’elle se trouve dans le même répertoire que l’assembly qui contient la méthode. Si la bibliothèque est présente et correctement référencée, vérifiez que le nom de la méthode, le type de retour et la signature d’argument correspondent à la fonction de bibliothèque.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle lorsque la bibliothèque non managée se trouve dans le même répertoire que l’assembly managé qui y fait référence. Il peut être possible de supprimer sans risque un avertissement de cette règle dans le cas où la bibliothèque non managée n’a pas pu être localisée.

## <a name="example"></a>Exemple
 L’exemple suivant montre un type qui viole la règle. Aucune fonction nommée ne `DoSomethingUnmanaged` se produit dans kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
