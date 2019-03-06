---
title: 'Comment : déboguer la méthode OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2fc5e8a7e0bbc80fd7fa0aa2d242239a9be6a219
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714970"
---
# <a name="how-to-debug-the-onstart-method"></a>Comment : déboguer la méthode OnStart
Vous pouvez déboguer un service Windows en le démarrant et en attachant le débogueur au processus de service. Pour plus d'informations, consultez [How to: Debug Windows Service Applications](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Toutefois, pour déboguer la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> d’un service Windows, vous devez lancer le débogueur à l’intérieur de la méthode.

1. Ajoutez un appel à <xref:System.Diagnostics.Debugger.Launch%2A> au début de la méthode `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Démarrez le service (avec `net start`ou à partir de la fenêtre **Services** ).

    Une boîte de dialogue similaire à celle ci-dessous doit s’afficher :

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Sélectionnez **Oui, déboguer \<nom_service>**.

4. Dans la fenêtre du débogueur juste-à-temps, sélectionnez la version de Visual Studio à utiliser pour le débogage.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Une nouvelle instance de Visual Studio démarre, mais son exécution s’arrête à la méthode `Debugger.Launch()` .

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
