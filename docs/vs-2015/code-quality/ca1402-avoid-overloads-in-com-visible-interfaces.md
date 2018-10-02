---
title: 'CA1402 : Éviter les surcharges dans les interfaces COM visibles | Microsoft Docs'
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
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ece9a444ac308003c56da1bd4f2ecf4433e2b4a9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588103"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402 : Éviter les surcharges dans les interfaces COM visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1402 : éviter les surcharges dans les interfaces COM visibles](https://docs.microsoft.com/visualstudio/code-quality/ca1402-avoid-overloads-in-com-visible-interfaces).

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un composant COM (Object Model) visible interface déclare les méthodes surchargées.

## <a name="rule-description"></a>Description de la règle
 Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom. Les surcharges suivantes sont renommées de manière unique en ajoutant le nom, un caractère de trait de soulignement « _ » et un entier qui correspond à l’ordre de déclaration de la surcharge. Par exemple, considérez les méthodes suivantes.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Ces méthodes sont exposées aux clients COM comme suit.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Les clients COM Visual Basic 6 ne peut pas implémenter des méthodes d’interface à l’aide d’un trait de soulignement dans le nom.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez les méthodes surchargées afin que les noms sont uniques. Vous pouvez également rendre l’interface invisible à COM en modifiant l’accessibilité à `internal` (`Friend` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ou en appliquant la <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attribut la valeur `false`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre une interface qui enfreint la règle et une interface qui satisfait la règle.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 [Interopérabilité avec du Code non managé](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Type de données Long](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



