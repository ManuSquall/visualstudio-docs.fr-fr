---
title: 'CA2105 : Les champs de tableau ne doivent pas être en lecture seule'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeadbd977b8c7d97af611a2054692a6071f21a36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808300"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105 : Les champs de tableau ne doivent pas être en lecture seule

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Un champ public ou protégé qui contient un tableau est déclaré en lecture seule.

## <a name="rule-description"></a>Description de la règle

Lorsque vous appliquez le `readonly` (`ReadOnly` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) modificateur à un champ qui contient un tableau, le champ ne peut pas être modifié pour faire référence à un tableau différent. Toutefois, les éléments du tableau stockés dans un champ en lecture seule peuvent être modifiés. Code qui prend des décisions ou exécute des opérations qui reposent sur les éléments d’un tableau en lecture seule qui est publiquement accessible peut contenir une faille de sécurité exploitable.

Notez que la présence d’un champ public également viole la règle de conception [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger la vulnérabilité de sécurité qui est identifiée par cette règle, ne comptez pas sur le contenu d’un tableau en lecture seule qui est accessible publiquement. Il est fortement recommandé d’utiliser l’une des procédures suivantes :

- Remplacez le tableau par une collection fortement typée qui ne peut pas être modifiée. Pour plus d'informations, consultez <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Remplacez le champ public avec une méthode qui retourne un clone d’un tableau privé. Étant donné que votre code ne repose pas sur le clone, il n’existe aucun risque si les éléments sont modifiés.

Si vous avez choisi la deuxième approche, ne remplacez pas le champ par une propriété ; propriétés qui retournent des tableaux de manière négative affectent les performances. Pour plus d’informations, consultez [CA1819 : Propriétés ne doivent pas retourner de tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Exclusion d’un avertissement de cette règle est fortement déconseillée. Presque aucun scénarios se produisent dans lequel le contenu d’un champ en lecture seule est sans important. Si c’est le cas dans votre scénario, supprimez le `readonly` modificateur au lieu d’exclure le message.

## <a name="example-1"></a>Exemple 1

Cet exemple montre les dangers de violation de cette règle. La première partie montre un exemple de bibliothèque qui a un type, `MyClassWithReadOnlyArrayField`, qui contient deux champs (`grades` et `privateGrades`) qui ne sont pas sécurisés. Le champ `grades` est public et par conséquent vulnérable pour tout appelant. Le champ `privateGrades` est privé, mais est toujours vulnérable, car il est retourné aux appelants par le `GetPrivateGrades` (méthode). Le `securePrivateGrades` champ est exposé de manière sécurisée par le `GetSecurePrivateGrades` (méthode). Il est déclaré comme privés pour suivre les pratiques d’une bonne conception. La deuxième partie montre le code qui modifie des valeurs stockées dans le `grades` et `privateGrades` membres.

La bibliothèque de classes d’exemple apparaît dans l’exemple suivant.

[!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_1.cs)]

## <a name="example-2"></a>Exemple 2

Le code suivant utilise la bibliothèque de classes d’exemple pour illustrer les problèmes de sécurité de tableau en lecture seule.

[!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../code-quality/codesnippet/CSharp/ca2105-array-fields-should-not-be-read-only_2.cs)]

La sortie de cet exemple est :

```text
Before tampering: Grades: 90, 90, 90 Private Grades: 90, 90, 90  Secure Grades, 90, 90, 90
After tampering: Grades: 90, 555, 90 Private Grades: 90, 555, 90  Secure Grades, 90, 90, 90
```

## <a name="see-also"></a>Voir aussi

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>