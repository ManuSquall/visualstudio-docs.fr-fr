---
title: 'CA2102 : interceptez les exceptions non CLSCompliant dans les gestionnaires généraux | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521301"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102 : Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un membre d’un assembly qui n’est pas marqué avec <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou est marqué comme `RuntimeCompatibility(WrapNonExceptionThrows = false)` contient un bloc catch qui gère <xref:System.Exception?displayProperty=fullName> et ne contient pas de bloc catch général immédiatement après. Cette règle ignore les [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] assemblys.

## <a name="rule-description"></a>Description de la règle
 Un bloc catch qui gère <xref:System.Exception> intercepte toutes les exceptions conformes à Common Language Specification (CLS). Toutefois, il n’intercepte pas les exceptions non conformes à CLS. Les exceptions non conformes à CLS peuvent être levées à partir du code natif ou du code managé qui a été généré par l’assembleur MSIL (Microsoft Intermediate Language). Notez que les [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilateurs et C# n’autorisent pas la levée d’exceptions non conformes CLS et [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] n’interceptent pas les exceptions non conformes à CLS. Si l’objectif du bloc catch est de gérer toutes les exceptions, utilisez la syntaxe de bloc catch générale suivante.

- C#: `catch {}`

- C++ : `catch(...) {}` ou `catch(Object^) {}`

  Une exception non gérée non conforme CLS devient un problème de sécurité lorsque des autorisations précédemment autorisées sont supprimées dans le bloc catch. Étant donné que les exceptions non conformes à CLS ne sont pas interceptées, une méthode malveillante qui lève une exception non conforme CLS peut s’exécuter avec des autorisations élevées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle lorsque l’intention est d’intercepter toutes les exceptions, remplacez ou ajoutez un bloc catch général ou marquez l’assembly `RuntimeCompatibility(WrapNonExceptionThrows = true)` . Si des autorisations sont supprimées dans le bloc catch, dupliquez les fonctionnalités dans le bloc catch général. Si vous n’avez pas l’intention de gérer toutes les exceptions, remplacez le bloc catch qui gère les <xref:System.Exception> blocs catch qui gèrent des types d’exception spécifiques.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le bloc try ne contient aucune instruction susceptible de générer une exception non conforme CLS. Étant donné que tout code natif ou managé peut lever une exception non conforme CLS, cela nécessite une connaissance de tout le code qui peut être exécuté dans tous les chemins de code à l’intérieur du bloc try. Notez que les exceptions non conformes à CLS ne sont pas levées par la common language runtime.

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
 [CA1031 : Ne pas intercepter des types d'exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Voir aussi
 [Exceptions et gestion des exceptions](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (assembleur il)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [remplacement des vérifications de sécurité](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
