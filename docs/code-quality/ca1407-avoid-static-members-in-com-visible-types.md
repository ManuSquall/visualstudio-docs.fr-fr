---
title: 'CA1407 : Éviter les membres statiques dans les types visibles par COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1ba8ef8cc0b75ed70ea6e98be2a4bac3e041e1d8
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45552014"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407 : Éviter les membres statiques dans les types visibles par COM
|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|Category|Microsoft.Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type qui est marqué spécifiquement comme visible pour COM Component Object Model () contient un `public``static` (méthode).

## <a name="rule-description"></a>Description de la règle
 COM ne prend pas en charge `static` méthodes.

 Cette règle ignore la propriété et les accesseurs d’événement, les méthodes ou des méthodes qui sont marqués à l’aide de la surcharge d’opérateur la <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> attribut ou le <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> attribut.

 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans les types publics et tous les membres de types valeur publics.

 Pour cette règle se produisent, un niveau de l’assembly <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit être définie sur `false` et la classe - <xref:System.Runtime.InteropServices.ComVisibleAttribute> doit être définie sur `true`, comme illustré dans le code suivant.

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
 Pour corriger une violation de cette règle, modifiez le design pour utiliser une méthode d’instance qui fournit les mêmes fonctionnalités que le `static` (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si un client COM ne nécessite pas d’accès à la fonctionnalité fournie par le `static` (méthode).

## <a name="example-violation"></a>Exemple de Violation

### <a name="description"></a>Description
 L’exemple suivant montre un `static` méthode qui enfreint cette règle.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]

### <a name="comments"></a>Commentaires
 Dans cet exemple, le **Book.FromPages** méthode ne peut pas être appelée à partir de COM.

## <a name="example-fix"></a>Exemple de correctif

### <a name="description"></a>Description
 Pour corriger la violation dans l’exemple précédent, vous pouvez modifier la méthode à une méthode d’instance, mais qui n’est pas pertinent dans cette instance. Une meilleure solution consiste à appliquer explicitement `ComVisible(false)` à la méthode pour indiquer clairement à d’autres développeurs que la méthode ne peut pas être visible à partir de COM.

 L’exemple suivant applique <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> à la méthode.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]

## <a name="related-rules"></a>Règles associées
 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>Voir aussi
 [Interopération avec du code non managé](/dotnet/framework/interop/index)