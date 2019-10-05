---
title: 'CA1407 : Éviter les membres statiques dans les types visibles par COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57450f80a8c630e2186de8804f8bb88974564e46
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234881"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407 : Éviter les membres statiques dans les types visibles par COM

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Un type qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) `public``static` contient une méthode.

## <a name="rule-description"></a>Description de la règle
COM ne prend pas `static` en charge les méthodes.

Cette règle ignore les accesseurs de propriété et d’événement, les méthodes de surcharge d’opérateur ou les méthodes qui sont marquées à l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> aide de l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut ou de l’attribut.

Par défaut, les éléments suivants sont visibles par COM : assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics.

Pour que cette règle se produise, un au <xref:System.Runtime.InteropServices.ComVisibleAttribute> niveau de l’assembly doit avoir la <xref:System.Runtime.InteropServices.ComVisibleAttribute> `false` valeur et la classe `true`doit avoir la valeur, comme le montre le code suivant.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, modifiez la conception pour utiliser une méthode d’instance qui fournit les mêmes fonctionnalités que `static` la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si un client com n’a pas besoin d’accéder aux fonctionnalités fournies par `static` la méthode.

## <a name="example-violation"></a>Exemple de violation

### <a name="description"></a>Description
L’exemple suivant montre une `static` méthode qui enfreint cette règle.

### <a name="code"></a>Code
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Commentaires
Dans cet exemple, la méthode **book. FromPages** ne peut pas être appelée à partir de com.

## <a name="example-fix"></a>Exemple de correction

### <a name="description"></a>Description
Pour corriger la violation dans l’exemple précédent, vous pouvez remplacer la méthode par une méthode d’instance, mais cela n’a pas de sens dans cette instance. Une meilleure solution consiste à s’appliquer `ComVisible(false)` explicitement à la méthode pour indiquer clairement aux autres développeurs que la méthode ne peut pas être vue à partir de com.

L’exemple suivant s' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> applique à la méthode.

### <a name="code"></a>Code
[!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Règles associées
[CA1017 Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

[CA1406 Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

[CA1413 Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Voir aussi
[Interopération avec du code non managé](/dotnet/framework/interop/index)