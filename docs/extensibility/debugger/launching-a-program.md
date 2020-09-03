---
title: Lancement d’un programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf638e0c96c7df1de2650260427a972a07efce23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738480"
---
# <a name="launch-a-program"></a>Lancer un programme
Les utilisateurs qui souhaitent déboguer un programme peuvent appuyer sur **F5** pour exécuter le débogueur à partir de l’IDE. Cela commence une série d’événements qui aboutissent au final à la connexion de l’IDE à un moteur de débogage (DE), qui est à son tour connecté, ou attaché, au programme comme suit :

1. L’IDE appelle d’abord le package de projet pour récupérer les paramètres de débogage de projet actifs de la solution. Les paramètres incluent le répertoire de démarrage, les variables d’environnement, le port dans lequel le programme s’exécute et le DE l’utilisation pour créer le programme, s’il est spécifié. Ces paramètres sont passés au package de débogage.

2. Si un DE est spécifié, le DE appelle le système d’exploitation pour lancer le programme. Suite au lancement du programme, l’environnement d’exécution du programme se charge. Par exemple, si un programme est écrit en MSIL, le common language runtime est appelé pour exécuter le programme.

    - ou -

    Si un DE n’est pas spécifié, le port appelle le système d’exploitation pour lancer le programme, ce qui entraîne le chargement de l’environnement d’exécution du programme.

   > [!NOTE]
   > Si un DE est utilisé pour lancer un programme, il est probable que le même DE sera attaché au programme.

3. Selon que le port DE ou du port a lancé le programme, l’environnement DE ou DE Runtime crée ensuite une description du programme, ou un nœud, et notifie le port que le programme est en cours d’exécution.

   > [!NOTE]
   > Il est recommandé que l’environnement d’exécution crée le nœud de programme, car le nœud de programme est une représentation légère d’un programme pouvant être débogué. Il n’est pas nécessaire de charger un entier uniquement pour créer et inscrire un nœud de programme. Si le DE est conçu pour s’exécuter dans le processus de l’IDE, mais qu’aucun IDE n’est en cours d’exécution, il doit exister un composant qui peut ajouter un nœud de programme au port.

   Le programme nouvellement créé, ainsi que tous les autres programmes, associés ou non associés, lancés ou attachés à à partir du même IDE, composent une session de débogage.

   Par programmation, quand l’utilisateur appuie sur **F5**pour la première fois, le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] package de débogage appelle le package de projet (qui est associé au type de programme en cours de lancement) via la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> méthode, qui à son tour remplit une <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> structure avec les paramètres de débogage de projet actifs de la solution. Cette structure est repassée au package de débogage via un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> méthode. Le package de débogage instancie ensuite le gestionnaire de débogage de session (SDM), qui lance le programme en cours de débogage et tous les moteurs de débogage associés.

   L’un des arguments passés au SDM est le GUID du DE à utiliser pour lancer le programme.

   Si le GUID n’est pas `GUID_NULL` , le SDM co-crée le de, puis appelle sa méthode [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour lancer le programme. Par exemple, si un programme est écrit en code natif, appellera `IDebugEngineLaunch2::LaunchSuspended` probablement `CreateProcess` et `ResumeThread` (fonctions Win32) pour exécuter le programme.

   Suite au lancement du programme, l’environnement d’exécution du programme est chargé. L’environnement DE ou d’exécution crée ensuite une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) pour décrire le programme et transmet cette interface à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) pour notifier le port que le programme est en cours d’exécution.

   Si `GUID_NULL` est passé, le port lance le programme. Une fois que le programme est en cours d’exécution, l’environnement d’exécution crée une `IDebugProgramNode2` interface pour décrire le programme et le passer à `IDebugPortNotify2::AddProgramNode` . Cela indique au port que le programme est en cours d’exécution. Ensuite, le SDM attache le moteur de débogage au programme en cours d’exécution.

## <a name="in-this-section"></a>Contenu de cette section
 [Notification du port](../../extensibility/debugger/notifying-the-port.md) Explique ce qui se produit après le lancement d’un programme et la notification du port.

 [Attacher après un lancement](../../extensibility/debugger/attaching-after-a-launch.md) Documente lorsque la session de débogage est prête à attacher le DE au programme.

## <a name="related-sections"></a>Sections connexes
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.
