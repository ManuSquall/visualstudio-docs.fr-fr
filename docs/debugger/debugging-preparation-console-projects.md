---
title: "Préparation du débogage : Projets de la Console | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9e1ade672c3abd81f4f71d1e48a39560e17e1465
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-preparation-console-projects"></a>Préparation du débogage : projets console
La préparation du débogage d'un projet console est identique à celle d'un projet Windows, avec quelques éléments supplémentaires à prendre en compte. Pour plus d’informations, consultez [les Applications Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), et [préparation du débogage : Applications Windows Forms (.NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). En raison de la similarité de toutes les applications console, cette rubrique couvre les types de projets suivants :  
  
-   Application console C#  
  
-   Application console Visual Basic  
  
-   Application console C++ (.NET)  
  
-   Application console C++ (Win32)  
  
 Vous pouvez être amené à spécifier des arguments de ligne de commande pour votre application console. Pour plus d’informations, consultez [paramètres de projet pour une Configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [paramètres de projet pour une Configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), ou [des paramètres de projet pour les Configurations Debug c# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Comme toutes les propriétés de projet, ces arguments persistent entre les sessions de débogage et celles de Visual Studio. Par conséquent, si vous avez débogué précédemment l’application console, n’oubliez pas qu’il existe peut-être des arguments provenant des sessions précédentes dans le  **\<projet > Pages de propriétés** boîte de dialogue.  
  
 Une application console utilise la **Console** fenêtre pour accepter les entrées et afficher les messages de sortie. Pour écrire dans le **Console** fenêtre, votre application doit utiliser le **Console** objet au lieu de l’objet Debug. Pour écrire dans le **sortie de Visual Studio** fenêtre, utilisez l’objet Debug, comme d’habitude. Vérifiez l'emplacement dans lequel écrit votre application, sinon vous risquez de rechercher les messages au mauvais endroit. Pour plus d’informations, consultez [classe Console](/dotnet/api/system.console), [classe Debug](/dotnet/api/system.diagnostics.debug), et [fenêtre sortie](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Démarrage de l'application  
 Lorsque certaines applications console démarrent, elles s'exécutent jusqu'à la fin, puis se ferment. Ce comportement peut ne pas vous fournir suffisamment de temps pour interrompre l'exécution et le débogage. Pour pouvoir déboguer une application, utilisez l'une des procédures suivantes pour démarrer l'application :  
  
-   Votre application commence à s’exécuter et s’exécute jusqu'à ce qu’il atteigne le point d’arrêt.  
  
-   Votre application démarre et s'arrête immédiatement à la première ligne de code source.  
  
-   Dans une fenêtre de code source, cliquez sur une ligne, puis sélectionnez **exécuter jusqu’au curseur**.  
  
     Votre application démarre et s'exécute jusqu'à la ligne sélectionnée, ou jusqu'à un point d'arrêt, si le point d'arrêt est atteint avant la ligne.  
  
 Lors du débogage d'une application console, vous pouvez démarrer l'application à partir de l'invite de commandes au lieu de la démarrer à partir de Visual Studio. Dans ce cas, vous pouvez démarrer l'application à partir de l'invite de commandes, puis l'attacher au débogueur Visual Studio. Pour plus d’informations, consultez [attacher au processus en cours](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Lorsque vous démarrez une application console à partir de Visual Studio, le **Console** fenêtre apparaît quelquefois derrière la fenêtre Visual Studio. Si vous essayez de démarrer votre application console à partir de Visual Studio et que rien ne se produit, essayez de déplacer la fenêtre Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projet Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Types de projets C#, F# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour une Configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)