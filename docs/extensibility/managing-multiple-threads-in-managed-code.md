---
title: 'Comment : Gérer plusieurs threads dans le code géré (fr) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702779"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Comment : Gérer plusieurs threads dans le code géré
Si vous disposez d’une extension VSPackage gérée qui appelle des méthodes asynchrones ou a des opérations qui exécutent sur des threads autres que le thread d’interface utilisateur Visual Studio, vous devez suivre les lignes directrices données ci-dessous. Vous pouvez garder le thread d’interface utilisateur réactif parce qu’il n’a pas besoin d’attendre le travail sur un autre thread pour terminer. Vous pouvez rendre votre code plus efficace, parce que vous n’avez pas de threads supplémentaires qui prennent de l’espace pile, et vous pouvez le rendre plus fiable et plus facile à débocher parce que vous évitez les impasses et les pendaisons.

 En général, vous pouvez passer du thread d’interface utilisateur à un thread différent, ou vice versa. Lorsque la méthode revient, le thread actuel est le fil à partir duquel il a été appelé à l’origine.

> [!IMPORTANT]
> Les lignes directrices suivantes <xref:Microsoft.VisualStudio.Threading> utilisent les API <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> dans l’espace nom, en particulier la classe. Les API dans cet espace [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]de nom sont nouveaux dans . Vous pouvez obtenir une <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> instance <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory`d’un de la propriété .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Passer du fil d’interface utilisateur à un thread d’arrière-plan

1. Si vous êtes sur le fil d’interface utilisateur et que vous souhaitez `Task.Run()`effectuer un travail asynchrone sur un fil de fond, utilisez :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Si vous êtes sur le fil d’interface utilisateur et que vous souhaitez bloquer <xref:System.Threading.Tasks.TaskScheduler> en `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>synchronité pendant que vous effectuez des travaux sur un thread de fond, utilisez la propriété à l’intérieur :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Passer d’un fil d’arrière-plan au thread d’interface utilisateur

1. Si vous êtes sur un fil de fond et que vous <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>voulez faire quelque chose sur le thread d’interface utilisateur, utilisez :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Vous pouvez <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> utiliser la méthode pour passer au thread d’interface utilisateur. Cette méthode affiche un message au thread d’interface utilisateur avec la poursuite de la méthode asynchrone actuelle, et communique également avec le reste du cadre de filetage pour définir la priorité correcte et éviter les impasses.

     Si votre méthode de fil de fond n’est pas asynchrone et vous ne `await` pouvez pas le rendre asynchrone, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>vous pouvez toujours utiliser la syntaxe pour passer au fil d’interface utilisateur en enveloppant votre travail avec , comme dans cet exemple:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
