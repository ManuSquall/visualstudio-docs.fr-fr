---
title: 'CA2007 : N’attendez pas directement une Tâche'
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
ms.openlocfilehash: bf3e13697f39f7d0f531549d4c018b9f42872596
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545226"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007 : N’attendez pas directement une Tâche

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

## <a name="configurability"></a>Possibilités de configuration

Vous pouvez configurer si vous souhaitez exclure des méthodes asynchrones qui ne retournent pas une valeur à partir de cette règle. Pour exclure ces types de méthodes, ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Vous pouvez également configurer de types d’assembly auquel appliquer cette règle de sortie. Par exemple, pour uniquement appliquer cette règle au code qui produit une application console ou une bibliothèque de liens dynamiques (autrement dit, pas une application d’interface utilisateur), ajoutez la paire clé-valeur suivante dans un fichier .editorconfig dans votre projet :

```
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Pour plus d’informations, consultez [analyseurs FxCop configurer](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Voir aussi

- [Dois-je attendre une tâche avec ConfigureAwait (false) ?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installer les analyseurs FxCop dans Visual Studio](install-fxcop-analyzers.md)