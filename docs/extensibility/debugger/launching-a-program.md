---
title: "Lancement d&#39;un programme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, lancement"
  - "programmes, lancement"
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Lancement d&#39;un programme
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Les utilisateurs qui veulent déboguer un programme peuvent appuyer sur F5 pour exécuter le débogueur de l'IDE.  Cette opération lance une série d'événements qui portent résultat l'IDE se connecter à un moteur de \(DE\) débogage, qui est ensuite connecté, ou attaché, au programme comme suit :  
  
1.  IDE appelle d'abord le package de projet pour obtenir les paramètres de débogage du projet actif de la solution.  Les paramètres sont le répertoire de démarrage, les variables d'environnement, le port dans lesquels le programme s'exécute, et De pour créer le programme, si cela est spécifié.  Ces paramètres sont passés au package de débogage.  
  
2.  Si un De est spécifié, le De appelle le système d'exploitation pour exécuter le programme.  Devant être de exécuter le programme, l'environnement d'exécution du programme est chargé.  Par exemple, si un programme est écrit dans le langage MSIL, le common langage runtime sera appelé pour exécuter le programme.  
  
     ou  
  
     Si un De n'est pas spécifié, le port appelle le système d'exploitation pour exécuter le programme, ce qui provoque l'environnement d'exécution du programme à charger.  
  
    > [!NOTE]
    >  Si un De est utilisé pour exécuter un programme, il est probable que le même De est joint au programme.  
  
3.  Selon que le De ou le port a lancé le programme, le De ou l'environnement d'exécution crée ensuite une description du programme, le nœud ou, et notifie le port que le programme s'exécute.  
  
    > [!NOTE]
    >  Il est recommandé que l'environnement d'exécution créent le nœud de programme, car le nœud du programme est une représentation légère d'un programme qui peut être débogué.  Il n'est pas nécessaire de charger un entier De simplement pour créer et enregistrer un nœud de programme.  Si le De est conçu pour fonctionner en cours de l'IDE, mais aucun l'IDE n'est en fait, il faut un composant qui peut ajouter un nœud de programme au port.  
  
 Le programme nouvellement créé, ainsi que tous les autres programmes, lié ou non lié, lancé ou attaché à même de l'IDE, composent une session de débogage.  
  
 Par programme, lorsque l'utilisateur appuie sur tout d'abord **F5**, le package du débogage des vsprvs appelle le package de projet \(associé au type du projet qui est lancé\) via la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> , qui complète à son tour une structure d'<xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> avec les paramètres de débogage du projet actif de la solution.  Cette structure est retournée au package de débogage via un appel à la méthode d' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> .  Le package de débogage instancie le gestionnaire de débogage de session \(SDM\), qui lance le programme débogué et tous les moteurs de débogage associés.  
  
 Un des arguments passés au SDM est un GUID du De à utiliser pour exécuter le programme.  
  
 Si LE GUID n'est pas `GUID_NULL`, le SDM crée le De, puis appelle sa méthode d' [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour exécuter le programme.  Par exemple, si un programme est écrit en code natif, puis `IDebugEngineLaunch2::LaunchSuspended` appelle éventuellement `CreateProcess` et `ResumeThread` \(fonctions Win32\) pour exécuter le programme.  
  
 Devant être de exécuter le programme, l'environnement d'exécution du programme est chargé.  Le De ou l'environnement d'exécution crée une interface d' [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) pour décrire le programme et passe cette interface à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) pour informer le port que le programme s'exécute.  
  
 Si `GUID_NULL` est passé, le port lance le programme.  Une fois le programme est exécuté, celui\-ci crée une interface d' `IDebugProgramNode2` pour décrire le programme et la passe à `IDebugPortNotify2::AddProgramNode`.  Cela permet d'informer le port que le programme s'exécute.  Le SDM joint le moteur de débogage au programme en cours de exécution.  
  
## Dans cette section  
 [Notifier le Port](../../extensibility/debugger/notifying-the-port.md)  
 Explique ce qui se produit après un programme est exécuté et le port est notifié.  
  
 [Attachement d'après le lancement d'un](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documents lorsque la session de débogage est prête à joindre le De au programme.  
  
## Rubriques connexes  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers différentes tâches de débogage, telles que exécuter un programme et évaluer des expressions.