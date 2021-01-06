---
title: Déboguer la méthode OnStart | Microsoft Docs
description: Découvrez comment déboguer la méthode OnStart d’un service Windows dans Visual Studio, en lançant le débogueur à partir de la méthode.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903140"
---
# <a name="how-to-debug-the-onstart-method"></a>Comment : déboguer la méthode OnStart
Vous pouvez déboguer un service Windows en le démarrant et en attachant le débogueur au processus de service. Pour plus d’informations, consultez [Guide pratique pour déboguer les applications de service Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Toutefois, pour déboguer la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> d’un service Windows, vous devez lancer le débogueur à l’intérieur de la méthode.

1. Ajoutez un appel à <xref:System.Diagnostics.Debugger.Launch%2A> au début de la méthode `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Démarrez le service (avec `net start`ou à partir de la fenêtre **Services** ).

    Une boîte de dialogue similaire à celle ci-dessous doit s’afficher :

    ![Capture d’écran d’une boîte de dialogue du débogueur juste-à-temps Visual Studio qui affiche une exception de .NET Framework non gérée survenue dans WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Sélectionnez **Oui, déboguer \<service name> .**

4. Dans la fenêtre du débogueur juste-à-temps, sélectionnez la version de Visual Studio à utiliser pour le débogage.

    ![Capture d’écran d’une fenêtre du débogueur juste-à-temps Visual Studio avec’nouvelle instance de Microsoft Visual Studio 2015 'sélectionnée dans la liste des débogueurs possibles.](../debugger/media/justintimedebugger.png)

5. Une nouvelle instance de Visual Studio démarre, mais son exécution s’arrête à la méthode `Debugger.Launch()` .

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
