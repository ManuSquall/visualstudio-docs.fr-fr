---
title: Lancement d’un programme Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738480"
---
# <a name="launch-a-program"></a>Lancer un programme
Les utilisateurs qui veulent déboguer un programme peuvent appuyer sur **F5** pour exécuter le débbugger de l’IDE. Cela commence une série d’événements qui finissent par entraîner la connexion de l’IDE à un moteur de débogé (DE), qui est à son tour connecté, ou attaché, au programme comme suit:

1. L’IDE appelle d’abord le paquet de projet pour obtenir les paramètres de déboiffage du projet actif de la solution. Les paramètres comprennent le répertoire de départ, les variables de l’environnement, le port dans lequel le programme fonctionnera, et le DE à utiliser pour créer le programme, si spécifié. Ces paramètres sont passés à l’emballage de débogé.

2. Si un DE est spécifié, le DE appelle le système d’exploitation pour lancer le programme. À la suite du lancement du programme, l’environnement de l’exécution du programme se charge. Par exemple, si un programme est écrit dans MSIL, l’heure d’exécution de langue commune sera invoquée pour exécuter le programme.

    -ou-

    Si un DE n’est pas spécifié, le port appelle le système d’exploitation pour lancer le programme, ce qui entraîne la charge de l’environnement de temps d’exécution du programme.

   > [!NOTE]
   > Si un DE est utilisé pour lancer un programme, il est probable que le même DE sera attaché au programme.

3. Selon que le DE ou le port ont lancé le programme, le DE ou l’environnement de l’heure d’exécution crée alors une description du programme, ou nœud, et informe le port que le programme est en cours d’exécution.

   > [!NOTE]
   > Il est recommandé que l’environnement de course-temps créer le nœud de programme, parce que le nœud de programme est une représentation légère d’un programme qui peut être débogé. Il n’est pas nécessaire de charger un DE entier juste pour créer et enregistrer un nœud de programme. Si le DE est conçu pour fonctionner dans le processus de l’IDE, mais aucun IDE n’est réellement en cours d’exécution, il doit y avoir un composant qui peut ajouter un nœud de programme au port.

   Le programme nouvellement créé, ainsi que tous les autres programmes, liés ou non, lancés ou attachés à partir du même IDE, composent une session de débogé.

   Sur le plan programmatique, lorsque l’utilisateur appuie pour la première fois **sur F5**, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le paquet <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> de déboignes appelle <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> le paquet de projet (qui est associé au type de programme lancé) à travers la méthode, qui à son tour remplit une structure avec les paramètres de débaillement de projet actif de la solution. Cette structure est transmise à l’emballage de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> débogé par un appel à la méthode. Le paquet de débog instantanément ensuite le gestionnaire de débogé de session (SDM), qui lance le programme étant débogé et tous les moteurs de débogés associés.

   L’un des arguments transmis au SDM est le GUID du DE qui sera utilisé pour lancer le programme.

   Si le DE GUID n’est pas `GUID_NULL`, le SDM co-crée le DE, puis appelle sa méthode [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) pour lancer le programme. Par exemple, si un programme est `IDebugEngineLaunch2::LaunchSuspended` écrit `CreateProcess` en `ResumeThread` code natif, il sera probablement appelé et (fonctions Win32) pour exécuter le programme.

   À la suite du lancement du programme, l’environnement de durée du programme est chargé. Soit le DE ou l’environnement de course-temps crée alors une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) pour décrire le programme et passe cette interface à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) pour informer le port que le programme est en cours d’exécution.

   Si `GUID_NULL` elle est adoptée, alors le port lance le programme. Une fois le programme en cours d’exécution, l’environnement de course-temps crée une `IDebugProgramNode2` interface pour décrire le programme et le transmet à `IDebugPortNotify2::AddProgramNode`. Cela avise le port que le programme est en cours d’exécution. Ensuite, le SDM attache le moteur de débogé au programme de fonctionnement.

## <a name="in-this-section"></a>Contenu de cette section
 [Notifier le port](../../extensibility/debugger/notifying-the-port.md) Explique ce qui se passe après le lancement d’un programme et l’avis du port.

 [Fixation après un lancement](../../extensibility/debugger/attaching-after-a-launch.md) Documents lorsque la session de débogé est prête à joindre le DE au programme.

## <a name="related-sections"></a>Sections connexes
 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
