---
title: 'Ca1402 : éviter les surcharges dans les interfaces COM visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 258b7ba1444cd990c3ec68ebfd5faccc945439e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661346"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402 : Éviter les surcharges dans les interfaces COM visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une interface visible COM (Component Object Model) déclare des méthodes surchargées.

## <a name="rule-description"></a>Description de la règle
 Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom. Les surcharges suivantes sont renommées de manière unique en ajoutant au nom un caractère de soulignement « _ » et un entier qui correspond à l’ordre de déclaration de la surcharge. Par exemple, considérez les méthodes suivantes.

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

 Visual Basic 6 clients COM ne peuvent pas implémenter de méthodes d’interface à l’aide d’un trait de soulignement dans le nom.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez les méthodes surchargées afin que les noms soient uniques. Vous pouvez également rendre l’interface invisible pour COM en modifiant l’accessibilité en `internal` (`Friend` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) ou en appliquant l’attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> défini sur `false`.

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
 Interopérabilité avec le [type de données long](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516) du [code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
