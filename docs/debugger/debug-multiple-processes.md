---
title: Debug processus multiples Microsoft Docs
ms.date: 11/20/2018
ms.topic: conceptual
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
ms.openlocfilehash: 160e219b6fc2ab314f8d0dd91043c18101f2c3a5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302223"
---
# <a name="debug-multiple-processes-c-visual-basic-c"></a>Débogé de plusieurs processus (C, Visual Basic, CMD)

Visual Studio peut déboiffer une solution qui comporte plusieurs processus. Vous pouvez démarrer et basculer entre les processus, casser, continuer et passer à travers la source, arrêter de débogage, et se terminer ou se détacher des processus individuels.

## <a name="start-debugging-with-multiple-processes"></a>Commencez à débogage avec plusieurs processus

Lorsque plus d’un projet dans une solution Visual Studio peut s’exécuter indépendamment, vous pouvez sélectionner le projet que le débingière commence. Le projet de démarrage actuel apparaît en gras dans **Solution Explorer**.

Pour modifier le projet de démarrage, dans **Solution Explorer**, cliquez à droite sur un projet différent et sélectionnez Set **comme startUp Project**.

Pour commencer à déboguer un projet de **Solution Explorer** sans en faire le projet de démarrage, cliquez à droite sur le projet et sélectionnez **Debug** > **Start nouvelle instance** ou step into new **instance**.

**Définir le projet de démarrage ou plusieurs projets à partir de solutions Propriétés :**

1. Sélectionnez la solution dans **Solution Explorer,** puis sélectionnez l’icône **Propriétés** dans la barre d’outils, ou cliquez à droite sur la solution et sélectionnez **les propriétés**.

1. Sur la page **Propriétés,** sélectionnez **Common Properties** > **Startup Project**.

   ![Modification du type de démarrage pour un projet](../debugger/media/dbg_execution_startmultipleprojects.png "DBG_Execution_StartMultipleProjects")

1. Sélectionnez **la sélection actuelle,** **projet de démarrage unique** et un fichier de projet, ou plusieurs **projets de démarrage**.

   Si vous sélectionnez **plusieurs projets de démarrage,** vous pouvez modifier l’ordre de démarrage et l’action à prendre pour chaque projet: **Démarrer**, Démarrer **sans débogage**, ou **Aucun**.

1. Sélectionnez **Appliquer**, ou **OK** pour appliquer et fermer le dialogue.

### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Joindre à un processus

Le débbugger peut également *s’attacher* aux applications en cours d’exécution dans les processus en dehors de Visual Studio, y compris sur les appareils distants. Après votre attachement à une application, vous pouvez utiliser le debugger Visual Studio. Les caractéristiques de débogage peuvent être limitées. Cela dépend si l’application a été construite avec des informations de débogé, si vous avez accès au code source de l’application, et si le compilateur JIT suit les informations de débogé.

Pour plus d’informations, voir [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

**Pour établir un attachement à un processus en cours d’exécution :**

1. Avec l’application en cours d’exécution, sélectionnez **Debug** > **Attach to Process**.

   ![Joindre à la boîte de dialogue Process](../debugger/media/dbg_attachtoprocessdlg.png "Boîte de dialogue Attacher au processus")

1. Dans la boîte de dialogue **Attach to Process,** sélectionnez le processus dans la liste **des processus disponibles,** puis **sélectionnez Attach**.

>[!NOTE]
>Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution. Pour déboquer un processus enfantin, soit attachez au processus de l’enfant après qu’il commence, ou configurez l’éditeur de registre Windows pour commencer le processus d’enfant dans une nouvelle instance de débagé.

### <a name="use-the-registry-editor-to-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Utilisez l’éditeur de registre pour démarrer automatiquement un processus dans le débagé

Parfois, vous devrez peut-être déboiffer le code de démarrage d’une application lancée par un autre processus. C'est le cas des services et des actions d'installation personnalisée. Vous pouvez obtenir le lancement du débbuggeur et vous attacher automatiquement à l’application.

1. Démarrer l’éditeur du registre Windows en exécutant *regedit.exe*.

1. Dans l’éditeur d’enregistrement, naviguez vers **HKEY_LOCAL_MACHINE’Software-Microsoft-Windows NT-CurrentVersion’Image File Option d’exécution**.

1. Sélectionnez le dossier de l’application à démarrer dans le débogueur.

   Si l’application n’est pas répertoriée comme un dossier pour enfants, cliquez à droite **Sur les options d’exécution des fichiers d’images,** sélectionnez **New** > **Key**et tapez le nom de l’application. Ou, cliquez à droite sur la nouvelle clé de l’arbre, sélectionnez **Renommez,** puis entrez le nom de l’application.

1. Cliquez à droite sur la nouvelle clé de l’arbre et sélectionnez **nouvelle** > **valeur de chaîne**.

1. Changer le nom de la nouvelle valeur `debugger`de New Value **#1** à .

1. **Débogéeur à** clic droit et sélectionnez **Modifier**.

   ![Boîte de dialogue Modification de la chaîne](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "Boîte de dialogue Modification de la chaîne")

1. Dans la boîte de dialogue `vsjitdebugger.exe` **Edit String,** tapez la boîte de données De **valeur,** puis sélectionnez **OK**.

   ![Entrée de démarrage du débogueur automatique dans regedit.exe](../debugger/media/dbg_execution_automaticstart_result.png "Entrée de démarrage du débogueur automatique dans regedit.exe")

## <a name="debug-with-multiple-processes"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Debug avec plusieurs processus
<a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>

Lorsque le débogage d’une application avec plusieurs processus, la rupture, le pas et la poursuite des commandes de débbugger affectent tous les processus par défaut. Par exemple, lorsqu’un processus est suspendu à un point d’arrêt, l’exécution de tous les autres processus est également suspendue. Vous pouvez changer ce comportement par défaut pour mieux contrôler les cibles des commandes d’exécution.

**Pour modifier si tous les processus sont suspendus lorsqu’un processus se brise :**

- Sous **Outils** (ou **Debug**) > **Options** > **Debugging** > **General**, sélectionnez ou **effacez la pause tous les processus lorsqu’un processus casse** la case à cocher.

### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Commandes Arrêter, Exécuter pas à pas et Continuer

Le tableau suivant décrit les comportements des commandes de débogage lorsque la **pause tous les processus lorsqu’un processus casse** la case à cocher est sélectionnée ou désélectionnée :

|**Commande**|Volumes sélectionnés|Désélectionné|
|-|-|-|
|**Debug**  > **Break Tous**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|
|**Debug** > **Continuer**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|
|**Debug** > **Step Into**, Step **Over**, ou Step **Out**|Tous les processus s'exécutent pendant les étapes de processus actuelles. <br />Puis, tous les processus s'arrêtent.|Étapes de processus actuel. <br />Les processus suspendus reprennent. <br />Les processus en cours d'exécution se poursuivent.|
|**Debug** > Step Into Current Process , Step Over Current Process , or **Step Out Current Process** Debug Step Into Current**Process**, Step Over **Current Process**|N/A|Étapes de processus actuel.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|Point **de rupture** de fenêtre de source|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|
|Fenêtre source **Courir au curseur**<br />La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br />Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|**Processus de** fenêtre > **Break Process**|N/A|Le processus sélectionné s'interrompt.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|**Processus** fenêtre > **Processus de poursuite**|N/A|Le processus sélectionné reprend.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|

### <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les fichiers sources et de symboles (.pdb)
Pour naviguer dans le code source d’un processus, le débbuggeur a besoin d’accéder à ses fichiers sources et symboles. Pour plus d’informations, consultez [Spécifier les fichiers de symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer en utilisant la fenêtre **démontage.** Pour plus d’informations, voir [Comment : Utilisez la fenêtre de démontage.](../debugger/how-to-use-the-disassembly-window.md)

### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Basculer entre processus

Vous pouvez vous attacher à plusieurs processus lorsque vous débogagez, mais un seul processus est actif dans le débogage à un moment donné. Vous pouvez définir le processus actif ou *actuel* dans la barre d’outils **Emplacement de débogage** ou dans la fenêtre **Processus**. Pour basculer entre les processus, les deux processus doivent être en mode arrêt.

**Pour définir le processus actuel à partir de la barre d’outils Debug Location :**

1. Pour ouvrir la barre **d’outils Debug Location,** sélectionnez **View** > **Toolbars** > **Debug Emplacement**.

1. Lors du débogage, sur la barre **d’outils Debug Location,** sélectionnez le processus que vous souhaitez définir comme processus actuel à partir de **l’abandon du processus.**

   ![Basculer d’un processus à l’autre](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")

**Pour définir le processus actuel à partir de la fenêtre Processus :**

1. Pour ouvrir la fenêtre **Processes,** tout en débogage, sélectionnez **Debug** > **Windows** > **Processes**.

1. Dans la fenêtre **Processes,** le processus actuel est marqué par une flèche jaune. Double-cliquez sur le processus que vous souhaitez définir comme le processus actuel.

   ![Fenêtre de processus](../debugger/media/dbg_processeswindow.png "DBG_ProcessesWindow")

Le passage à un processus le définit comme processus actuel à des fins de débogage. Les fenêtres Debugger montrent l’état pour le processus actuel, et les commandes de pas affectent seulement le processus actuel.

## <a name="stop-debugging-with-multiple-processes"></a>Arrêtez de débogage avec plusieurs processus

Par défaut, lorsque vous sélectionnez **Debug** > **Stop Debugging**, le débogage se termine ou se détache de tous les processus.

- Si le processus actuel a été lancé dans le débbugger, le processus est terminé.

- Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.

Si vous commencez à débogage d’un processus à partir d’une solution Visual Studio, puis joindre à un autre processus qui est déjà en cours d’exécution, puis choisissez **Stop Debugging**, la session de débogage se termine. Le processus qui a été commencé dans Visual Studio se termine, tandis que le processus que vous avez attaché à continue à courir.

Pour contrôler la façon dont **Stop Debugging** affecte un processus individuel, dans la fenêtre **Processes,** cliquez à droite sur un processus, puis sélectionnez ou effacez la **décodeur lorsque le débogage a cessé** la case à cocher.

>[!NOTE]
>La **pause tous les processus lorsqu’un processus casse l’option** de débbugger n’affecte pas l’arrêt, la fin ou le détachement des processus.

### <a name="stop-terminate-and-detach-commands"></a>Commandes Arrêter, Terminer et Détacher

Le tableau suivant décrit les comportements du débbuggeur arrêter, terminer et détacher les commandes avec plusieurs processus:

|**Commande**|**Description**|
|-|-|
|**Debug** > **Stop Debugging**|Sauf si le comportement est modifié dans la fenêtre **Processes,** les processus commencés par le débruceur sont terminés, et les processus attachés sont détachés.|
|**Debug** > **Mettre fin à tous**|Tous les processus sont terminés.|
|**Debug** > **détacher tous**|Le débogueur se détache de tous les processus.|
|**Processus de** > **de** fenêtre de processus de dépôt de processus|Le débogueur se détache du processus sélectionné.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|**Processus de** fenêtre > **processus de fin**|Le processus sélectionné est terminé.<br />D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|
|**Traite la** fenêtre > **détachez lorsque le débogage s’arrête**|S’il est sélectionné, **Debug** > **Stop Debugging** se détache du processus sélectionné. <br />S’il n’est pas sélectionné, **Debug** > **Stop Debugging** met fin au processus sélectionné. |

## <a name="see-also"></a>Voir aussi

- [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)
- [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Applications multithreaded Debug](../debugger/debug-multithreaded-applications-in-visual-studio.md)