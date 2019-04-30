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
ms.openlocfilehash: 2f361720f45a24e561ab2a886537bda02c73c006
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545770"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Un membre dans un assembly qui n’est pas marqué avec le <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou était marquée `RuntimeCompatibility(WrapNonExceptionThrows = false)` contient un bloc catch qui gère <xref:System.Exception?displayProperty=fullName> et ne contient pas de bloc catch général immédiatement après. Cette règle ignore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] assemblys.

## <a name="rule-description"></a>Description de la règle

Un bloc catch qui gère <xref:System.Exception> intercepte toutes les exceptions conformes Common Language Specification (CLS). Toutefois, il n’intercepte pas les exceptions non conformes CLS. Non-CLS conformes exceptions peuvent être levées à partir du code natif ou du code managé qui a été généré par le Microsoft intermediate language (MSIL) assembleur. Notez que c# et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] compilateurs n’autorisent pas non-CLS levée d’exceptions et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n’intercepte pas les exceptions non conformes CLS. Si l’intention du bloc catch doit gérer toutes les exceptions, utilisez la syntaxe de bloc catch général suivante.

- C#: `catch {}`

- C++ : `catch(...) {}` ou `catch(Object^) {}`

Une exception compatible non-CLS non gérée devient un problème de sécurité lorsque les autorisations précédemment accordées sont supprimées dans le bloc catch. Étant donné que les exceptions non conformes CLS ne sont pas interceptées, une méthode malveillante qui lève une non-CLS exception pourrait exécuter avec des autorisations élevées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle lorsque l’objectif est d’intercepter toutes les exceptions, remplacer ou ajouter un bloc catch général ou marquez l’assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Si les autorisations sont supprimées dans le bloc catch, en double la fonctionnalité dans le grand bloc catch. Si elle n’est pas l’intention de gérer toutes les exceptions, remplacez le bloc catch qui gère <xref:System.Exception> avec les blocs catch qui gèrent des types d’exceptions spécifiques.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Il est possible de supprimer un avertissement de cette règle si le bloc try ne contient-elle pas toutes les instructions susceptibles de générer une exception non conforme CLS. Étant donné que n’importe quel code natif ou managé peut lever une non-CLS exception conforme, cela nécessite une connaissance du code qui peut être exécuté dans tous les chemins de code dans le bloc try. Notez que les exceptions non conformes CLS ne sont pas levées par le common language runtime.

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

[CA1031 : Ne pas intercepter des types d’exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Voir aussi

- [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)
- [Ilasm.exe (assembleur IL)](/dotnet/framework/tools/ilasm-exe-il-assembler)
- [Indépendance du langage et composants indépendants du langage](/dotnet/standard/language-independence-and-language-independent-components)