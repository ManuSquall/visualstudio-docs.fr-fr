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
ms.openlocfilehash: 0d3ab899ad660c637492a4c3d229779481184e95
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547012"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007 : N’attendez pas directement une Tâche

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Catégorie|Microsoft.Reliability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause

Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) directement un <xref:System.Threading.Tasks.Task> .

## <a name="rule-description"></a>Description de la règle

Lorsqu’une méthode asynchrone attend directement une <xref:System.Threading.Tasks.Task> , une continuation se produit dans le thread qui a créé la tâche. Ce comportement peut être coûteux en termes de performances et peut entraîner un blocage sur le thread d’interface utilisateur. Envisagez d’appeler <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> pour signaler votre intention de continuation.

Cette règle a été introduite avec les [analyseurs FxCop](install-fxcop-analyzers.md) et n’existe pas dans l’analyse FxCop héritée.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger les violations, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> appelez sur le <xref:System.Threading.Tasks.Task>attendu. Vous pouvez passer soit `true` ou `false` pour le `continueOnCapturedContext` paramètre.

- L' `ConfigureAwait(true)` appel de sur la tâche a le même comportement que l' <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>appel de manière explicite. En appelant explicitement cette méthode, vous permettez aux lecteurs de savoir que vous souhaitez intentionnellement effectuer la continuation sur le contexte de synchronisation d’origine.

- Appelez `ConfigureAwait(false)` sur la tâche pour planifier les continuations vers le pool de threads, évitant ainsi un blocage sur le thread d’interface utilisateur. Le `false` passage à est une bonne option pour les bibliothèques indépendantes des applications.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Vous pouvez supprimer cet avertissement si vous savez que le consommateur n’est pas une application GUI (Graphical User Interface) ou si le consommateur n’a <xref:System.Threading.SynchronizationContext>pas de.

## <a name="example"></a>Exemples

L’extrait de code suivant génère l’avertissement:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Pour corriger la violation, appelez <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> sur le <xref:System.Threading.Tasks.Task>attendu:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Configurabilité

Vous pouvez configurer si vous souhaitez exclure des méthodes asynchrones qui ne retournent pas de valeur à partir de cette règle. Pour exclure ces genres de méthodes, ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Vous pouvez également configurer les types d’assembly de sortie auxquels appliquer cette règle. Par exemple, pour appliquer cette règle uniquement au code qui produit une application console ou une bibliothèque liée de manière dynamique (autrement dit, pas une application d’interface utilisateur), ajoutez la paire clé-valeur suivante à un fichier. editorconfig dans votre projet:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Pour plus d’informations, consultez [configurer les analyseurs FxCop](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Voir aussi

- [Dois-je attendre une tâche avec ConfigureAwait (false)?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installer les analyseurs FxCop dans Visual Studio](install-fxcop-analyzers.md)