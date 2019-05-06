---
title: 'CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fd018c927981c4a067e4dd0d52ef699490caa3fc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948773"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un membre dans un assembly qui n’est pas marqué avec le <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou était marquée `RuntimeCompatibility(WrapNonExceptionThrows = false)` contient un bloc catch qui gère <xref:System.Exception?displayProperty=fullName> et ne contient pas de bloc catch général immédiatement après. Cette règle ignore [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] assemblys.

## <a name="rule-description"></a>Description de la règle
 Un bloc catch qui gère <xref:System.Exception> intercepte toutes les exceptions conformes Common Language Specification (CLS). Toutefois, il n’intercepte pas les exceptions non conformes CLS. Non-CLS conformes exceptions peuvent être levées à partir du code natif ou du code managé qui a été généré par le Microsoft intermediate language (MSIL) assembleur. Notez que C# et [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateurs n’autorisent pas non-CLS levée d’exceptions et [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] n’intercepte pas les exceptions non conformes CLS. Si l’intention du bloc catch doit gérer toutes les exceptions, utilisez la syntaxe de bloc catch général suivante.

- C#: `catch {}`

- C++ : `catch(...) {}` ou `catch(Object^) {}`

  Une exception compatible non-CLS non gérée devient un problème de sécurité lorsque les autorisations précédemment accordées sont supprimées dans le bloc catch. Étant donné que les exceptions non conformes CLS ne sont pas interceptées, une méthode malveillante qui lève une non-CLS exception pourrait exécuter avec des autorisations élevées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle lorsque l’objectif est d’intercepter toutes les exceptions, remplacer ou ajouter un bloc catch général ou marquez l’assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)`. Si les autorisations sont supprimées dans le bloc catch, en double la fonctionnalité dans le grand bloc catch. Si elle n’est pas l’intention de gérer toutes les exceptions, remplacez le bloc catch qui gère <xref:System.Exception> avec les blocs catch qui gèrent des types d’exceptions spécifiques.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un avertissement de cette règle si le bloc try ne contient-elle pas toutes les instructions susceptibles de générer une exception non conforme CLS. Étant donné que n’importe quel code natif ou managé peut lever une non-CLS exception conforme, cela nécessite une connaissance du code qui peut être exécuté dans tous les chemins de code dans le bloc try. Notez que les exceptions non conformes CLS ne sont pas levées par le common language runtime.

## <a name="example"></a>Exemple
 L’exemple suivant montre une classe MSIL qui lève une exception non conforme CLS.

```
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

## <a name="example"></a>Exemple
 L’exemple suivant montre une méthode qui contient un bloc catch général qui satisfait la règle.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Compilez les exemples précédents comme suit.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>Règles associées
 [CA1031 : Ne pas intercepter des types d’exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Voir aussi
 [Exceptions et gestion des exceptions](http://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (assembleur IL)](http://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [substitution des vérifications de sécurité](http://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [indépendance du langage et composants indépendants du langage](http://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
