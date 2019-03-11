---
title: 'CA2007 : N’attend pas directement d’une tâche'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699678"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007 : N’attend pas directement d’une tâche

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Category|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directement.

## <a name="rule-description"></a>Description de la règle

Quand une méthode asynchrone attend un <xref:System.Threading.Tasks.Task> directement, la continuation se produit dans le même thread qui a créé la tâche. Ce comportement peut s’avérer coûteux en termes de performances et peut entraîner un blocage sur le thread d’interface utilisateur. Envisagez d’appeler <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> pour signaler votre intention de continuation.

Cette règle a été introduite avec [analyseurs FxCop](install-fxcop-analyzers.md) et n’existe pas dans « legacy » (analyse statique du code) FxCop.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger les violations, appelez <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sur la manière attendue <xref:System.Threading.Tasks.Task>. Vous pouvez passer soit `true` ou `false` pour le `continueOnCapturedContext` paramètre.

- Appel `ConfigureAwait(true)` sur la tâche a le même comportement que ne pas appeler explicitement <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. En appelant explicitement cette méthode, vous indiquez à des lecteurs que vous voulez intentionnellement effectuer la continuation sur le contexte de synchronisation d’origine.

- Appeler `ConfigureAwait(false)` sur la tâche pour planifier les continuations au pool de threads, évitant ainsi un blocage sur le thread d’interface utilisateur. En passant `false` est une bonne option pour les bibliothèques indépendantes de l’application.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer cet avertissement si vous savez que le consommateur n’est pas une application d’interface graphique utilisateur graphique ou si le consommateur n’a pas un <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Exemple

L’extrait de code suivant génère l’avertissement :

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Pour corriger la violation, appelez <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sur la manière attendue <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>Voir aussi

- [Dois-je attendre une tâche avec ConfigureAwait (false) ?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installer les analyseurs FxCop dans Visual Studio](install-fxcop-analyzers.md)