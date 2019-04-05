---
title: 'Procédure : Déboguer la méthode OnStart | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d77d06e720ebe9146f907d8868c46c94addd5d99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950293"
---
# <a name="how-to-debug-the-onstart-method"></a>Procédure : Déboguer la méthode OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez déboguer un service Windows en le démarrant et en attachant le débogueur au processus de service. Pour plus d'informations, voir [Procédure : déboguer les applications de service Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). Toutefois, pour déboguer la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> d’un service Windows, vous devez lancer le débogueur à l’intérieur de la méthode.  
  
1.  Ajoutez un appel à <xref:System.Diagnostics.Debugger.Launch%2A> au début de la méthode `OnStart()`.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Démarrez le service (avec `net start`ou à partir de la fenêtre **Services** ).  
  
     Une boîte de dialogue similaire à celle ci-dessous doit s’afficher :  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Sélectionnez **Oui, déboguer \<nom_service>**.  
  
4.  Dans la fenêtre du débogueur juste-à-temps, sélectionnez la version de Visual Studio à utiliser pour le débogage.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Une nouvelle instance de Visual Studio démarre, mais son exécution s’arrête à la méthode `Debugger.Launch()` .  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)
