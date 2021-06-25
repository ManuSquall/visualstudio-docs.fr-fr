---
title: 'Comment : gérer plusieurs threads dans du code managé | Microsoft Docs'
description: Apprenez à gérer plusieurs threads dans le code si votre extension VSPackage managée appelle des méthodes asynchrones ou a des opérations à partir du thread d’interface utilisateur de Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903084"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Comment : gérer plusieurs threads dans du code managé
Si vous avez une extension de VSPackage managée qui appelle des méthodes asynchrones ou a des opérations qui s’exécutent sur des threads autres que le thread d’interface utilisateur de Visual Studio, vous devez suivre les instructions indiquées ci-dessous. Vous pouvez maintenir la réactivité du thread d’interface utilisateur, car il n’a pas besoin d’attendre la fin du travail sur un autre thread. Vous pouvez rendre votre code plus efficace, car vous n’avez pas de threads supplémentaires qui occupent de l’espace de pile et vous pouvez le rendre plus fiable et plus facile à déboguer, car vous évitez les blocages et le code qui ne répond pas.

 En général, vous pouvez passer du thread d’interface utilisateur à un thread différent, ou vice versa. Lorsque la méthode retourne, le thread actuel est le thread à partir duquel il a été appelé à l’origine.

> [!IMPORTANT]
> Les instructions suivantes utilisent les API de l' <xref:Microsoft.VisualStudio.Threading> espace de noms, en particulier la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. Les API de cet espace de noms sont nouvelles dans [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Vous pouvez obtenir une instance de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> à partir de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propriété `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Basculer du thread d’interface utilisateur vers un thread d’arrière-plan

1. Si vous êtes sur le thread d’interface utilisateur et que vous souhaitez effectuer un travail asynchrone sur un thread d’arrière-plan, utilisez `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Si vous êtes sur le thread d’interface utilisateur et que vous souhaitez bloquer de façon synchrone pendant que vous effectuez un travail sur un thread d’arrière-plan, utilisez la <xref:System.Threading.Tasks.TaskScheduler> propriété `TaskScheduler.Default` à l’intérieur de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Basculer d’un thread d’arrière-plan vers le thread d’interface utilisateur

1. Si vous êtes sur un thread d’arrière-plan et que vous souhaitez effectuer une opération sur le thread d’interface utilisateur, utilisez <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> méthode pour basculer vers le thread d’interface utilisateur. Cette méthode publie un message dans le thread d’interface utilisateur avec la continuation de la méthode asynchrone actuelle, et communique également avec le reste de l’infrastructure de thread pour définir la priorité correcte et éviter les interblocages.

     Si votre méthode de thread d’arrière-plan n’est pas asynchrone et que vous ne pouvez pas la rendre asynchrone, vous pouvez toujours utiliser la `await` syntaxe pour basculer vers le thread d’interface utilisateur en encapsulant votre travail avec <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , comme dans cet exemple :

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
