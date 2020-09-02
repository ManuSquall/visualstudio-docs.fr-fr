---
title: 'CA1407 : éviter les membres statiques dans les types visibles par COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 436a8614c18c296c072d91116143306d898f0436
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538851"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407 : Éviter les membres statiques dans les types visibles par COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un type qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) contient une `public``static` méthode.

## <a name="rule-description"></a>Description de la règle
 COM ne prend pas en charge les `static` méthodes.

 Cette règle ignore les accesseurs de propriété et d’événement, les méthodes de surcharge d’opérateur ou les méthodes qui sont marquées à l’aide de l' <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut ou de l' <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics.

 Pour que cette règle se produise, un au niveau de l’assembly <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit avoir `false` la valeur et la classe <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit avoir la valeur `true` , comme le montre le code suivant.

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
 Pour corriger une violation de cette règle, modifiez la conception pour utiliser une méthode d’instance qui fournit les mêmes fonctionnalités que la `static` méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si un client COM n’a pas besoin d’accéder aux fonctionnalités fournies par la `static` méthode.

## <a name="example-violation"></a>Exemple de violation

### <a name="description"></a>Description
 L’exemple suivant montre une `static` méthode qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>Commentaires
 Dans cet exemple, la méthode **book. FromPages** ne peut pas être appelée à partir de com.

## <a name="example-fix"></a>Exemple de correction

### <a name="description"></a>Description
 Pour corriger la violation dans l’exemple précédent, vous pouvez remplacer la méthode par une méthode d’instance, mais cela n’a pas de sens dans cette instance. Une meilleure solution consiste à s’appliquer explicitement `ComVisible(false)` à la méthode pour indiquer clairement aux autres développeurs que la méthode ne peut pas être vue à partir de com.

 L’exemple suivant s’applique <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> à la méthode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>Règles associées
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413 : Éviter les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Voir aussi
 [Interopération avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
