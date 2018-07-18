---
title: Lancement d’un programme | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 714d751e9855b5567bf76ccd902fada727e14ba1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31103862"
---
# <a name="launching-a-program"></a>Lancement d’un programme
Les utilisateurs qui souhaitent déboguer un programme peuvent appuyer sur F5 pour exécuter le débogueur à partir de l’IDE. Commence une série d’événements d’aboutir à l’IDE se connecter à un moteur de débogage (DE), qui est à son tour connecté ou attaché, le programme comme suit :  
  
1.  L’IDE appelle d’abord le package du projet pour obtenir des paramètres de débogage du projet actif de la solution. Les paramètres incluent le répertoire de démarrage, les variables d’environnement, le port dans lequel le programme sera exécuté et le DE à utiliser pour créer le programme, si spécifié. Ces paramètres sont passés pour le package de débogage.  
  
2.  Si un D’est spécifié, le D’appelle le système d’exploitation pour lancer le programme. Par conséquent le lancement du programme, l’environnement d’exécution du programme est chargé. Par exemple, si un programme est écrit dans le langage MSIL, le common language runtime sera appelé pour exécuter le programme.  
  
     - ou -  
  
     Si un DE n’est pas spécifié, le port appelle le système d’exploitation pour lancer le programme, ce qui entraîne l’environnement d’exécution du programme doit être chargé.  
  
    > [!NOTE]
    >  Si un D’est utilisé pour lancer un programme, il est probable que le même DE sera attaché au programme.  
  
3.  Selon si le DE ou le port a lancé le programme, le DE ou de l’environnement d’exécution crée une description du programme, ou nœud, puis notifie le port que le programme est en cours d’exécution.  
  
    > [!NOTE]
    >  Il est recommandé que l’environnement d’exécution créer le nœud de programme, car le nœud de programme est une représentation simplifiée d’un programme qui peut être débogué. Il n’est pas nécessaire de charger un ensemble DE simplement pour créer et inscrire un nœud du programme. Si le D’est conçu pour s’exécuter le processus de l’IDE, mais aucune IDE est en cours d’exécution, il doit exister un composant que vous pouvez ajouter un nœud de programme pour le port.  
  
 Le programme qui vient d’être créé, ainsi que d’autres programmes, liés ou non liés, lancé ou attachés à partir de l’IDE de même, composer une session de débogage.  
  
 Par programme, lorsque l’utilisateur tout d’abord appuie **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]du package de débogage appelle le package de projet (qui est associé avec le type de programme lancé) via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (méthode), qui à son tour remplit un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> structure avec les paramètres de débogage de la solution projet actif. Cette structure est passée dans le package de débogage via un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> (méthode). Le package de débogage instancie ensuite le Gestionnaire de session de débogage (SDM), qui lance le programme en cours de moteurs de débogage débogué et tout état associé.  
  
 Un des arguments passés à la SDM est le GUID de la DE à utiliser pour lancer le programme.  
  
 Si le GUID DE n’est pas `GUID_NULL`, le SDM crée le DE, puis appelle sa [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) méthode pour lancer le programme. Par exemple, si un programme est écrit en code natif, puis `IDebugEngineLaunch2::LaunchSuspended` appellera probablement `CreateProcess` et `ResumeThread` (fonctions Win32) pour exécuter le programme.  
  
 Par conséquent le lancement du programme, l’environnement d’exécution du programme est chargé. Le DE ou de l’environnement d’exécution crée ensuite un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) de l’interface pour décrire le programme et passe cette interface pour [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) pour notifier le port que le programme en cours d’exécution.  
  
 Si `GUID_NULL` est passée, le port lance le programme. Une fois que le programme est en cours d’exécution, l’environnement d’exécution crée un `IDebugProgramNode2` de l’interface pour décrire le programme et le transmet à `IDebugPortNotify2::AddProgramNode`. Cela informe le port que le programme est en cours d’exécution. Puis le SDM attache le moteur de débogage pour le programme en cours d’exécution.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Notification du port](../../extensibility/debugger/notifying-the-port.md)  
 Explique que se passe-t-il après un programme est lancé et le port est notifié.  
  
 [Attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md)  
 Documents lors de la session de débogage est prête à attacher le DE au programme.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md)  
 Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.