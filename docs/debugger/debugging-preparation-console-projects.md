---
title: "Pr&#233;paration du d&#233;bogage&#160;: projets console | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "applications console, débogage"
  - "déboguer (Visual Studio), applications console"
  - "déboguer les applications console"
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Pr&#233;paration du d&#233;bogage&#160;: projets console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La préparation du débogage d'un projet console est identique à celle d'un projet Windows, avec quelques éléments supplémentaires à prendre en compte.  Pour plus d'informations, consultez [Applications Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md) et [Debugging Preparation: Windows Forms Applications \(.NET\)](http://msdn.microsoft.com/fr-fr/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5).  En raison de la similarité de toutes les applications console, cette rubrique couvre les types de projets suivants :  
  
-   Application console C\#  
  
-   Application console Visual Basic  
  
-   Application console C\+\+ \(.NET\)  
  
-   Application console C\+\+ \(Win32\)  
  
 Vous pouvez être amené à spécifier des arguments de ligne de commande pour votre application console.  Pour plus d'informations, consultez [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Paramètres de projet pour une configuration Debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) ou [Paramètres de projet pour des configurations Debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Comme toutes les propriétés de projet, ces arguments persistent entre les sessions de débogage et celles de Visual Studio.  Par conséquent, si vous avez débogué précédemment l'application console, n'oubliez pas qu'il existe peut\-être des arguments provenant des sessions précédentes dans la boîte de dialogue **Pages de propriétés de \<Projet\>**.  
  
 Une application console utilise la fenêtre de **console** pour accepter les entrées et afficher les messages de sortie.  Pour écrire dans la fenêtre **Console**, votre application doit utiliser l'objet **Console** au lieu de l'objet Debug.  Pour écrire dans la fenêtre **Sortie Visual Studio**, utilisez l'objet Debug, comme d'habitude.  Vérifiez l'emplacement dans lequel écrit votre application, sinon vous risquez de rechercher les messages au mauvais endroit.  Pour plus d'informations, consultez [Console, classe](https://msdn.microsoft.com/en-us/library/system.console.aspx), [Debug, classe](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) et [Sortie, fenêtre](../ide/reference/output-window.md).  
  
## Démarrage de l'application  
 Lorsque certaines applications console démarrent, elles s'exécutent jusqu'à la fin, puis se ferment.  Ce comportement peut ne pas vous fournir suffisamment de temps pour interrompre l'exécution et le débogage.  Pour pouvoir déboguer une application, utilisez l'une des procédures suivantes pour démarrer l'application :  
  
-   Votre application démarre l'exécution et s'exécute jusqu'à ce qu'elle atteigne le point d'arrêt.  
  
-   Votre application démarre et s'arrête immédiatement à la première ligne de code source.  
  
-   Dans une fenêtre de code source, cliquez avec le bouton droit sur une ligne et sélectionnez **Exécuter jusqu'au curseur**.  
  
     Votre application démarre et s'exécute jusqu'à la ligne sélectionnée, ou jusqu'à un point d'arrêt, si le point d'arrêt est atteint avant la ligne.  
  
 Lors du débogage d'une application console, vous pouvez démarrer l'application à partir de l'invite de commandes au lieu de la démarrer à partir de Visual Studio.  Dans ce cas, vous pouvez démarrer l'application à partir de l'invite de commandes, puis l'attacher au débogueur Visual Studio.  Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Lorsque vous démarrez une application console à partir de Visual Studio, la fenêtre **Console** apparaît quelquefois derrière la fenêtre Visual Studio.  Si vous essayez de démarrer votre application console à partir de Visual Studio et que rien ne se produit, essayez de déplacer la fenêtre Visual Studio.  
  
## Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)   
 [Types de projets Visual C\+\+](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Types de projets C\#, F\# et Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)