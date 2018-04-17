---
title: 'Comment : gérer plusieurs Threads dans le Code managé | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0888a0f65f36d624deffac60ceee032d3f3d13a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-managing-multiple-threads-in-managed-code"></a>Comment : gérer plusieurs Threads dans le Code managé
Si vous avez une extension VSPackage managée qui appelle des méthodes asynchrones ou a des opérations qui s’exécutent sur des threads autres que le thread d’interface utilisateur de Visual Studio, vous devez suivre les instructions ci-dessous. Vous pouvez conserver le thread d’interface utilisateur réactive, car il n’a pas besoin d’attendre pour le travail sur un autre thread pour terminer. Vous pouvez rendre votre code plus efficace, car vous n’avez pas les threads supplémentaires qui occupent de l’espace de pile, et vous pouvez le rendre plus fiable et plus facile à déboguer, car vous évitez les interblocages et les blocages.  
  
 En règle générale, vous pouvez basculer le thread d’interface utilisateur à un autre thread, ou vice versa. Lorsque la méthode est retournée, le thread actuel est le thread à partir duquel il a été initialement appelé.  
  
> [!IMPORTANT]
>  Les instructions suivantes utilisent les API dans le <xref:Microsoft.VisualStudio.Threading> espace de noms, en particulier, la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> classe. Les API dans cet espace de noms sont nouvelles dans [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Vous pouvez obtenir une instance d’un <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> à partir de la <xref:Microsoft.VisualStudio.Shell.ThreadHelper> propriété `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Passage à partir du Thread d’interface utilisateur à un Thread d’arrière-plan  
  
1.  Si vous êtes sur le thread d’interface utilisateur et que vous souhaitez effectuer le travail asynchrone sur un thread d’arrière-plan, utilisez Task.Run() :  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you're on a separate thread.  
    });  
    // Now you're back on the UI thread.  
  
    ```  
  
2.  Si vous êtes sur le thread d’interface utilisateur et que vous souhaitiez bloquer de façon synchrone lorsque vous effectuez un travail sur un thread d’arrière-plan, utilisez la <xref:System.Threading.Tasks.TaskScheduler> propriété `TaskScheduler.Default` dans <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Passage d’un Thread d’arrière-plan pour le Thread d’interface utilisateur  
  
1.  Si vous êtes sur un thread d’arrière-plan et que vous voulez faire quelque chose sur le thread d’interface utilisateur, utilisez <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Vous pouvez utiliser la <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> méthode pour basculer vers le thread d’interface utilisateur. Cette méthode envoie un message au thread d’interface utilisateur avec la continuation de la méthode asynchrone actuelle et également communique avec le reste de l’infrastructure de thread pour définir la priorité correcte et éviter les blocages.  
  
     Si votre méthode de thread d’arrière-plan n’est pas asynchrone, et vous ne pouvez pas rendre asynchrone, vous pouvez toujours utiliser le `await` syntaxe pour basculer vers le thread d’interface utilisateur en encapsulant votre travail avec <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, comme dans cet exemple :  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```