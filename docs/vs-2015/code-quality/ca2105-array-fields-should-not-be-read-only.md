---
title: 'CA2105 : les champs de tableau ne doivent pas être en lecture seule | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7599359899ca4860913b5bc0dd601fd06d9b8b54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666010"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105 : Les champs de tableau ne doivent pas être en lecture seule
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Catégorie|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un champ public ou protégé qui contient un tableau est déclaré en lecture seule.

## <a name="rule-description"></a>Description de la règle
 Lorsque vous appliquez le modificateur `readonly` (`ReadOnly` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) à un champ qui contient un tableau, le champ ne peut pas être modifié pour faire référence à un tableau différent. Toutefois, les éléments du tableau stockés dans un champ en lecture seule peuvent être modifiés. Le code qui prend des décisions ou effectue des opérations basées sur les éléments d’un tableau en lecture seule qui peut être accessible publiquement peut contenir une faille de sécurité exploitable.

 Notez que le fait d’avoir un champ public ne respecte pas non plus la règle de conception [CA1051 : ne déclarez pas les champs d’instance visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger la faille de sécurité qui est identifiée par cette règle, ne comptez pas sur le contenu d’un tableau en lecture seule qui peut être accessible publiquement. Il est fortement recommandé d’utiliser l’une des procédures suivantes :

- Remplacez le tableau par une collection fortement typée qui ne peut pas être modifiée. Pour plus d'informations, consultez <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Remplacez le champ public par une méthode qui retourne un clone d’un tableau privé. Étant donné que votre code ne repose pas sur le clone, il n’y a aucun danger si les éléments sont modifiés.

  Si vous avez choisi la deuxième approche, ne remplacez pas le champ par une propriété ; les propriétés qui retournent des tableaux ont un impact négatif sur les performances. Pour plus d’informations, consultez [CA1819 : les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 L’exclusion d’un avertissement de cette règle est fortement déconseillée. Presque aucun scénario ne se produit lorsque le contenu d’un champ en lecture seule n’est pas important. Si c’est le cas avec votre scénario, supprimez le modificateur `readonly` au lieu d’exclure le message.

## <a name="example"></a>Exemple
 Cet exemple illustre les dangers liés à la violation de cette règle. La première partie montre un exemple de bibliothèque de type, `MyClassWithReadOnlyArrayField`, qui contient deux champs (`grades` et `privateGrades`) qui ne sont pas sécurisés. Le champ `grades` est public et, par conséquent, vulnérable à n’importe quel appelant. Le champ `privateGrades` est privé mais reste vulnérable, car il est retourné aux appelants par la méthode `GetPrivateGrades`. Le champ `securePrivateGrades` est exposé de manière sécurisée par la méthode `GetSecurePrivateGrades`. Elle est déclarée comme privée pour suivre les bonnes pratiques de conception. La deuxième partie affiche le code qui modifie les valeurs stockées dans les membres `grades` et `privateGrades`.

 L’exemple de bibliothèque de classes s’affiche dans l’exemple suivant.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Exemple
 Le code suivant utilise l’exemple de bibliothèque de classes pour illustrer des problèmes de sécurité de tableau en lecture seule.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 La sortie de cet exemple est la suivante :

 **Avant la falsification : grades : 90, 90, 90 grades privés : 90, 90, 90 Notes sécurisées, 90, 90, 90**
**après falsification : grades : 90, 555, 90 grades privés : 90, 555, 90 Secure grades, 90,** 90, 90
## <a name="see-also"></a>Voir aussi
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
