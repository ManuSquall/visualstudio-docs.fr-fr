---
title: 'Préparation du débogage : projets console | Microsoft Docs'
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
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691215"
---
# <a name="debugging-preparation-console-projects"></a>Préparation du débogage : projets console
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La préparation du débogage d'un projet console est identique à celle d'un projet Windows, avec quelques éléments supplémentaires à prendre en compte. Pour plus d’informations, consultez [les Applications Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), et [préparation du débogage : applications Windows Forms (.NET)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5) En raison de la similarité de toutes les applications console, cette rubrique couvre les types de projets suivants :  
  
- Application console C#  
  
- Application console Visual Basic  
  
- Application console C++ (.NET)  
  
- Application console C++ (Win32)  
  
  Vous pouvez être amené à spécifier des arguments de ligne de commande pour votre application console. Pour plus d’informations, consultez [paramètres de projet pour une configuration de débogage C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [paramètres de projet pour une configuration de débogage Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ou [paramètres de projet pour les configurations de débogage C#](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Comme toutes les propriétés de projet, ces arguments persistent entre les sessions de débogage et celles de Visual Studio. Par conséquent, si vous avez débogué précédemment l’application console, n’oubliez pas qu’il existe peut-être des arguments provenant des sessions précédentes dans la boîte de dialogue ** \<Project> pages de propriétés** .  
  
  Une application console utilise la fenêtre **Console** pour accepter les entrées et afficher les messages de sortie. Pour écrire dans la fenêtre de **console** , votre application doit utiliser l’objet **console** au lieu de l’objet Debug. Pour écrire dans la fenêtre **Sortie Visual Studio**, utilisez l’objet Debug, comme d’habitude. Vérifiez l'emplacement dans lequel écrit votre application, sinon vous risquez de rechercher les messages au mauvais endroit. Pour plus d’informations, consultez [Console, classe](https://msdn.microsoft.com/library/system.console.aspx), [Debug, classe](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) et [Sortie, fenêtre](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Démarrage de l'application  
 Lorsque certaines applications console démarrent, elles s'exécutent jusqu'à la fin, puis se ferment. Ce comportement peut ne pas vous fournir suffisamment de temps pour interrompre l'exécution et le débogage. Pour pouvoir déboguer une application, utilisez l'une des procédures suivantes pour démarrer l'application :  
  
- Votre application démarre l'exécution et s'exécute jusqu'à ce qu'elle atteigne le point d'arrêt.  
  
- Votre application démarre et s'arrête immédiatement à la première ligne de code source.  
  
- Dans une fenêtre de code source, cliquez avec le bouton droit sur une ligne et sélectionnez **Exécuter jusqu’au curseur**.  
  
   Votre application démarre et s'exécute jusqu'à la ligne sélectionnée, ou jusqu'à un point d'arrêt, si le point d'arrêt est atteint avant la ligne.  
  
  Lors du débogage d'une application console, vous pouvez démarrer l'application à partir de l'invite de commandes au lieu de la démarrer à partir de Visual Studio. Dans ce cas, vous pouvez démarrer l'application à partir de l'invite de commandes, puis l'attacher au débogueur Visual Studio. Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Quand vous démarrez une application console à partir de Visual Studio, la fenêtre **Console** apparaît parfois derrière la fenêtre Visual Studio. Si vous essayez de démarrer votre application console à partir de Visual Studio et que rien ne se produit, essayez de déplacer la fenêtre Visual Studio.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de code natif](../debugger/debugging-native-code.md)   
 [Débogage de code managé](../debugger/debugging-managed-code.md)   
 [Types de projet Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Types de projets C#, F # et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)
