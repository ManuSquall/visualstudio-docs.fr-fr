---
title: Lancement d’un programme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c069e082d4bd9a11278a63d33a68822e528db795
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409976"
---
# <a name="launch-a-program"></a>Lancer un programme
Appuyez sur les utilisateurs souhaitant déboguer un programme **F5** d’exécuter le débogueur à partir de l’IDE. Commence une série d’événements qui aboutissent à présent dans l’IDE de la connexion à un moteur de débogage (DE), qui est à son tour connecté, ou attaché, le programme comme suit :

1. L’IDE appelle d’abord le package de projet pour obtenir des paramètres de débogage du projet actif de la solution. Les paramètres incluent le répertoire de démarrage, les variables d’environnement, le port dans lequel le programme s’exécute et l’Allemagne à utiliser pour créer le programme, si spécifié. Ces paramètres sont passés au package de débogage.

2. Si un D’est spécifié, l’Allemagne appelle le système d’exploitation pour lancer le programme. Par conséquent le lancement du programme, l’environnement d’exécution du programme charge. Par exemple, si un programme est écrit dans le langage MSIL, le common language runtime est appelé pour exécuter le programme.

    - ou -

    Si un DE n’est pas spécifié, le port appelle le système d’exploitation pour lancer le programme, ce qui provoque l’environnement d’exécution du programme à charger.

   > [!NOTE]
   > Si un D’est utilisé pour lancer un programme, il est probable que le même DE sera attaché au programme.

3. Selon que l’Allemagne ou le port lancé le programme, l’Allemagne ou l’environnement d’exécution puis crée une description du programme ou un nœud et notifie le port que le programme est en cours d’exécution.

   > [!NOTE]
   > Il est recommandé que l’environnement d’exécution créer le nœud de programme, car le nœud de programme est une représentation simplifiée d’un programme qui peut être débogué. Il est inutile de charger un ensemble DE simplement pour créer et inscrire un nœud de programme. Si le dé est conçue pour exécuter en cours de l’IDE, mais aucun IDE est en cours d’exécution, il doit exister un composant qui peut ajouter un nœud de programme au port.

   Le programme nouvellement créé, ainsi que d’autres programmes, liés ou non liés, lancé ou joints à partir de l’IDE de même, composer une session de débogage.

   Par programmation, lorsque l’utilisateur tout d’abord appuie **F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de déboguer le package appelle le package de projet (qui est associé avec le type de programme lancé) via le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> (méthode), qui à son tour remplit un <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> structure avec des paramètres de débogage du projet actif de la solution. Cette structure est passée dans le package de débogage via un appel à la <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> (méthode). Le package de débogage instancie ensuite le Gestionnaire de session de débogage (SDM), qui lance le programme en cours de moteurs de débogage débogué et tout état associé.

   Un des arguments transmis pour le SDM est le GUID de l’Allemagne à utiliser pour lancer le programme.

   Si le GUID DE n’est pas `GUID_NULL`, le SDM crée le DE, puis appelle son [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) méthode pour lancer le programme. Par exemple, si un programme est écrit en code natif, `IDebugEngineLaunch2::LaunchSuspended` appellera probablement `CreateProcess` et `ResumeThread` (fonctions Win32) pour exécuter le programme.

   Par conséquent le lancement du programme, l’environnement d’exécution du programme est chargé. Le DE ou de l’environnement d’exécution crée ensuite un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) pour décrire le programme d’interface et transmet cette interface à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) pour notifier le port que le programme est en cours d’exécution.

   Si `GUID_NULL` est passée, le port lance le programme. Une fois que le programme est en cours d’exécution, l’environnement d’exécution crée un `IDebugProgramNode2` interface pour décrire le programme et le transmet à `IDebugPortNotify2::AddProgramNode`. Cette procédure avertit le port que le programme est en cours d’exécution. Puis le SDM attache le moteur de débogage pour le programme en cours d’exécution.

## <a name="in-this-section"></a>Dans cette section
 [Notification du port](../../extensibility/debugger/notifying-the-port.md) explique que se passe-t-il après un programme est lancé et le port est notifié.

 [Attachement après un lancement](../../extensibility/debugger/attaching-after-a-launch.md) Documents lors de la session de débogage est prête à attacher le DE au programme.

## <a name="related-sections"></a>Rubriques connexes
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) contient des liens vers diverses tâches de débogage, telles que lancement d’un programme et l’évaluation des expressions.