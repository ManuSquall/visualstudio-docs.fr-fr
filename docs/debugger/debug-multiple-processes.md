---
title: Déboguer plusieurs processus | Microsoft Docs
ms.date: 11/20/2018
ms.topic: how-to
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94a61e0083b17fa095b419a2066a4f8b9c39dfb7
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350600"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Déboguer plusieurs processus (C#, Visual Basic, C++)

Visual Studio peut déboguer une solution qui a plusieurs processus. Vous pouvez démarrer et basculer entre les processus, arrêter, continuer et exécuter pas à pas la source, arrêter le débogage et terminer ou détacher des processus individuels.

## <a name="start-debugging-with-multiple-processes"></a>Démarrer le débogage avec plusieurs processus

Quand plusieurs projets dans une solution Visual Studio peuvent s’exécuter indépendamment, vous pouvez sélectionner le projet que le débogueur démarre. Le projet de démarrage actuel s’affiche en gras dans **Explorateur de solutions**.

Pour modifier le projet de démarrage, dans **Explorateur de solutions**, cliquez avec le bouton droit sur un autre projet et sélectionnez **définir comme projet de démarrage**.

Pour démarrer le débogage d’un projet à partir de **Explorateur de solutions** sans en faire le projet de démarrage, cliquez avec le bouton droit sur le projet, puis sélectionnez **Déboguer**  >  **Démarrer une nouvelle instance** ou **pas à pas détaillé dans la nouvelle instance**.

**Pour définir le projet de démarrage ou plusieurs projets à partir des propriétés de la solution :**

1. Sélectionnez la solution dans **Explorateur de solutions** puis sélectionnez l’icône **Propriétés** dans la barre d’outils, ou cliquez avec le bouton droit sur la solution et sélectionnez **Propriétés**.

1. Sur la page **Propriétés** , sélectionnez **Propriétés communes**  >  **projet de démarrage**.

   ![Modification du type de démarrage pour un projet](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Sélectionnez **sélection actuelle**, **projet de démarrage unique** et fichier projet ou **plusieurs projets de démarrage**.

   Si vous sélectionnez **plusieurs projets de démarrage**, vous pouvez modifier l’ordre de démarrage et l’action à entreprendre pour chaque projet : **Démarrer**, **exécuter sans débogage**ou **aucun**.

1. Sélectionnez **appliquer**ou **OK** pour appliquer et fermer la boîte de dialogue.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Attacher à un processus

Le débogueur peut également *être attaché* à des applications qui s’exécutent dans des processus en dehors de Visual Studio, y compris sur des appareils distants. Après l’attachement à une application, vous pouvez utiliser le débogueur Visual Studio. Les fonctionnalités de débogage peuvent être limitées. Cela dépend du fait que l’application a été générée avec les informations de débogage, que vous ayez accès au code source de l’application et que le compilateur JIT effectue le suivi des informations de débogage.

Pour plus d’informations, consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Pour établir un attachement à un processus en cours d’exécution :**

1. Une fois l’application en cours d’exécution, sélectionnez **Déboguer**  >  **attacher au processus**.

   ![Boîte de dialogue Attacher au processus](../debugger/media/dbg_attachtoprocessdlg.png "Boîte de dialogue Attacher au processus")

1. Dans la boîte de dialogue **attacher au processus** , sélectionnez le processus dans la liste **processus disponibles** , puis cliquez sur **attacher**.

>[!NOTE]
>Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution. Pour déboguer un processus enfant, joignez-le au processus enfant après son démarrage, ou configurez l’éditeur du Registre Windows pour démarrer le processus enfant dans une nouvelle instance du débogueur.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Utiliser l’éditeur du Registre pour démarrer automatiquement un processus dans le débogueur

Parfois, vous devrez peut-être déboguer le code de démarrage d’une application qui est lancée par un autre processus. C'est le cas des services et des actions d'installation personnalisée. Vous pouvez lancer le débogueur et l’attacher automatiquement à l’application.

1. Démarrez l’éditeur du Registre Windows en exécutant *regedit.exe*.

1. Dans l’éditeur du Registre, accédez à **HKEY_LOCAL_MACHINE options d’exécution de fichier \Software\microsoft\windows NT\CurrentVersion\Image File Execution**.

1. Sélectionnez le dossier de l’application à démarrer dans le débogueur.

   Si l’application n’est pas listée en tant que dossier enfant, cliquez avec le bouton droit sur **options d’exécution de fichier image**, sélectionnez **nouvelle**  >  **clé**, puis tapez le nom de l’application. Ou cliquez avec le bouton droit sur la nouvelle clé dans l’arborescence, sélectionnez **Renommer**, puis entrez le nom de l’application.

1. Cliquez avec le bouton droit sur la nouvelle clé dans l’arborescence et sélectionnez **nouvelle**  >  **valeur de chaîne**.

1. Remplacez le nom de la nouvelle valeur **#1** par `debugger` .

1. Cliquez avec le bouton droit sur **débogueur** et sélectionnez **modifier**.

   ![Boîte de dialogue Modification de la chaîne](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Boîte de dialogue Modification de la chaîne")

1. Dans la boîte de dialogue modification de la **chaîne** , tapez `vsjitdebugger.exe` dans la zone **données** de la valeur, puis sélectionnez **OK**.

   ![Entrée de démarrage du débogueur automatique dans regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Entrée de démarrage du débogueur automatique dans regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Déboguer avec plusieurs processus
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Lors du débogage d’une application à l’aide de plusieurs processus, les commandes de rupture, d’exécution pas à pas et de poursuite du débogueur affectent tous les processus par défaut. Par exemple, lorsqu’un processus est interrompu à un point d’arrêt, l’exécution de tous les autres processus est également interrompue. Vous pouvez changer ce comportement par défaut pour mieux contrôler les cibles des commandes d’exécution.

**Pour modifier l’interruption de tous les processus lorsqu’un processus s’arrête :**

- Sous **Outils** (ou **débogage**) > **options**  >  **débogage**  >  **général**, activez ou désactivez la case à cocher **arrêter tous les processus lorsqu’un processus s’arrête** .

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Commandes Arrêter, Exécuter pas à pas et Continuer

Le tableau suivant décrit les comportements des commandes de débogage lorsque la case à cocher **arrêter tous les processus lorsqu’un processus s’arrête** est activée ou désactivée :

|**Commande**|Volumes sélectionnés|Désélectionné|
|-|-|-|
|**Débogage**   >  **Arrêter tout**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|
|**Débogage**  >  **Continuer**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|
|**Débogage**  >  **Pas à**pas détaillé, **pas à pas principal**ou **pas à pas sortant**|Tous les processus s'exécutent pendant les étapes de processus actuelles. <br />Puis, tous les processus s'arrêtent.|Étapes de processus actuel. <br />Les processus suspendus reprennent. <br />Les processus en cours d'exécution se poursuivent.|
|**Débogage**  >  **Pas à pas détaillé du processus en cours**, **pas à pas principal du processus actuel**ou **pas à pas sortant du processus actuel**|N/A|Étapes de processus actuel.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|Point d' **arrêt** de la fenêtre source|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|
|Fenêtre source **exécutée jusqu’au curseur**<br />La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br />Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|Fenêtre **processus** > **arrêt du processus**|N/A|Le processus sélectionné s'interrompt.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|Fenêtre **processus** > **continuer le processus**|N/A|Le processus sélectionné reprend.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les fichiers sources et de symboles (.pdb)
Pour naviguer dans le code source d’un processus, le débogueur doit accéder à ses fichiers sources et fichiers de symboles. Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer à l’aide de la fenêtre **code machine** . Pour plus d’informations, consultez [Comment : utiliser la fenêtre Code machine](../debugger/how-to-use-the-disassembly-window.md).

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Basculer entre processus

Vous pouvez attacher plusieurs processus lors du débogage, mais un seul processus est actif dans le débogueur à un moment donné. Vous pouvez définir le processus actif ou *actuel* dans la barre d’outils **Emplacement de débogage** ou dans la fenêtre **Processus**. Pour basculer entre les processus, les deux processus doivent être en mode arrêt.

**Pour définir le processus en cours à partir de la barre d’outils emplacement de débogage :**

1. Pour ouvrir la barre d’outils **emplacement de débogage** , sélectionnez **Afficher**les  >  **barres d’outils**  >  **emplacement de débogage**.

1. Pendant le débogage, dans la barre d’outils **emplacement de débogage** , sélectionnez le processus que vous souhaitez définir comme processus actuel dans la liste déroulante **traiter** .

   ![Basculer entre les processus](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Pour définir le processus en cours à partir de la fenêtre processus :**

1. Pour ouvrir la fenêtre **processus** , pendant le débogage, sélectionnez **Déboguer**les  >  **Windows**  >  **processus**Windows.

1. Dans la fenêtre **processus** , le processus actuel est marqué par une flèche jaune. Double-cliquez sur le processus que vous souhaitez définir comme processus actuel.

   ![Fenêtre processus](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Le passage à un processus le définit en tant que processus actuel à des fins de débogage. Les fenêtres du débogueur affichent l’état du processus en cours et les commandes pas à pas affectent uniquement le processus actuel.

## <a name="stop-debugging-with-multiple-processes"></a>Arrêter le débogage avec plusieurs processus

Par défaut, lorsque vous sélectionnez **Déboguer**  >  **arrêter le débogage**, le débogueur se termine ou se détache de tous les processus.

- Si le processus en cours a été lancé dans le débogueur, le processus est terminé.

- Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.

Si vous démarrez le débogage d’un processus à partir d’une solution Visual Studio, puis attachez à un autre processus qui est déjà en cours d’exécution, puis choisissez **arrêter le débogage**, la session de débogage se termine. Le processus qui a été démarré dans Visual Studio se termine, tandis que le processus que vous avez attaché continue à s’exécuter.

Pour contrôler la façon dont l' **arrêt du débogage** affecte un processus individuel, dans la fenêtre **processus** , cliquez avec le bouton droit sur un processus, puis activez ou désactivez la case à cocher **détacher lorsque le débogage est arrêté** .

>[!NOTE]
>L’option **arrêter tous les processus lorsqu’un processus interrompt** le débogueur n’affecte pas l’arrêt, l’arrêt ou le détachement des processus.

### <a name="stop-terminate-and-detach-commands"></a>Commandes Arrêter, Terminer et Détacher

Le tableau suivant décrit les comportements des commandes arrêter, terminer et détacher du débogueur avec plusieurs processus :

|**Commande**|**Description**|
|-|-|
|**Débogage**  >  **Arrêter le débogage**|Sauf si le comportement est modifié dans la fenêtre **processus** , les processus démarrés par le débogueur sont terminés et les processus attachés sont détachés.|
|**Débogage**  >  **Arrêter tout**|Tous les processus sont terminés.|
|**Débogage**  >  **Détacher tout**|Le débogueur se détache de tous les processus.|
|Fenêtre **processus** > **détacher le processus**|Le débogueur se détache du processus sélectionné.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|Fenêtre **processus** > **terminer le processus**|Le processus sélectionné est terminé.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|La fenêtre **processus** > **détacher lorsque le débogage s’arrête**|Si cette option est sélectionnée, le **débogage**  >  **arrêter le débogage** se détache du processus sélectionné. <br />Si cette option n’est pas **sélectionnée, le débogage**  >  **arrêter le débogage** met fin au processus sélectionné. |

## <a name="see-also"></a>Voir aussi

- [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Navigation dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)
- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Déboguer des applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)