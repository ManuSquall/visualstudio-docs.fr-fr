---
title: "CA1400 : Des points d’entrée P-Invoke doivent exister | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: dd92619a652255f67c1e1558c40ea05840cd0eb5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400 : Des points d'entrée P/Invoke doivent exister
|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|Catégorie|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode publique ou protégée est marquée avec le <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. Si la règle ne peut pas trouver le nom de la méthode exactement tel qu’il est spécifié, il recherche ANSI ou des versions à caractères larges de la méthode en suffixant le nom de la méthode « A » ou « W ». Si aucune correspondance n’est trouvée, la règle essaie de localiser une fonction à l’aide du format de nom __stdcall (_MyMethod@12, où 12 représente la longueur des arguments). Si aucune correspondance n’est trouvée, et le nom de la méthode commence par '#', la règle recherche la fonction en tant que référence ordinale au lieu d’une référence de nom.  
  
## <a name="rule-description"></a>Description de la règle  
 Aucune vérification de la compilation n’est disponible pour vous assurer que les méthodes marquées avec <xref:System.Runtime.InteropServices.DllImportAttribute> se trouvent dans la DLL non managée référencée. Si aucune fonction qui porte le nom spécifié n’est dans la bibliothèque, ou les arguments de la méthode ne correspondent pas les arguments de fonction, le common language runtime lève une exception.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez la méthode qui a le <xref:System.Runtime.InteropServices.DllImportAttribute> attribut. Assurez-vous que la bibliothèque non managée existe et qu’il est dans le même répertoire que l’assembly qui contient la méthode. Si la bibliothèque est présent et correctement référencée, vérifiez que le nom de la méthode, le type de retour et la signature d’argument correspondent à la fonction de bibliothèque.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle lorsque la bibliothèque non managée est dans le même répertoire que l’assembly managé qui y fait référence. Il peut être possible de supprimer un avertissement de cette règle dans le cas où la bibliothèque non managée n’a pas été trouve.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui enfreint la règle. Aucune fonction nommée `DoSomethingUnmanaged` se produit dans kernel32.dll.  
  
 [!code-csharp[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>