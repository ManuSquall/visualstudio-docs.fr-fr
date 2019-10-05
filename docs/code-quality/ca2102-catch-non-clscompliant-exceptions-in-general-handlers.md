---
title: 'CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f62ad97bbb96f49a7263edd29f0f8a7c263bec4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233009"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un membre d’un assembly qui n’est pas marqué <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> avec ou est `RuntimeCompatibility(WrapNonExceptionThrows = false)` marqué comme contient un bloc Catch <xref:System.Exception?displayProperty=fullName> qui gère et ne contient pas de bloc catch général immédiatement après. Cette règle ignore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] les assemblys.

## <a name="rule-description"></a>Description de la règle

Un bloc catch qui gère <xref:System.Exception> intercepte toutes les exceptions conformes à Common Language Specification (CLS). Toutefois, il n’intercepte pas les exceptions non conformes à CLS. Les exceptions non conformes à CLS peuvent être levées à partir du code natif ou du code managé qui a été généré par l’assembleur MSIL (Microsoft Intermediate Language). Notez que les C# compilateurs et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n’autorisent pas la levée d’exceptions non conformes CLS et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n’interceptent pas les exceptions non conformes à CLS. Si l’objectif du bloc catch est de gérer toutes les exceptions, utilisez la syntaxe de bloc catch générale suivante.

- C#: `catch {}`

- C++: `catch(...) {}` ou`catch(Object^) {}`

Une exception non gérée non conforme CLS devient un problème de sécurité lorsque des autorisations précédemment autorisées sont supprimées dans le bloc catch. Étant donné que les exceptions non conformes à CLS ne sont pas interceptées, une méthode malveillante qui lève une exception non conforme CLS peut s’exécuter avec des autorisations élevées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle lorsque l’intention est d’intercepter toutes les exceptions, remplacez ou ajoutez un bloc catch général ou marquez l’assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Si des autorisations sont supprimées dans le bloc catch, dupliquez les fonctionnalités dans le bloc catch général. Si vous n’avez pas l’intention de gérer toutes les exceptions, remplacez le bloc Catch <xref:System.Exception> qui gère les blocs catch qui gèrent des types d’exception spécifiques.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer sans risque un avertissement de cette règle si le bloc try ne contient aucune instruction susceptible de générer une exception non conforme CLS. Étant donné que tout code natif ou managé peut lever une exception non conforme CLS, cela nécessite une connaissance de tout le code qui peut être exécuté dans tous les chemins de code à l’intérieur du bloc try. Notez que les exceptions non conformes à CLS ne sont pas levées par la common language runtime.

## <a name="example-1"></a>Exemple 1

L’exemple suivant montre une classe MSIL qui lève une exception non conforme CLS.

```cpp
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example-2"></a>Exemple 2

L’exemple suivant montre une méthode qui contient un bloc catch général qui satisfait la règle.

[!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]

Compilez les exemples précédents comme suit.

```cpp
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Règles associées

[CA1031 Ne pas intercepter les types d’exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Voir aussi

- [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (assembleur IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)