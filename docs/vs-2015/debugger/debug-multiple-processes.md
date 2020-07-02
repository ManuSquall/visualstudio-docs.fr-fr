---
title: Déboguer plusieurs processus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.programs
- vs.debug.processes.attaching
- vs.debug.activeprogram
- vs.debug.attaching
- vs.debug.attachedprocesses
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97d98522e011023cb3a021a69c9a82e8bb34cef3
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533274"
---
# <a name="debug-multiple-processes"></a>Déboguer plusieurs processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici comment démarrer les processus de débogage, basculer d'un processus à un autre, arrêter et continuer l'exécution, parcourir la source, arrêter le débogage et mettre fin ou se détacher d'un processus.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Matières  
 [Configurer le comportement d'exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Rechercher les fichiers sources et de symboles (. pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Basculer les processus, arrêter et continuer l’exécution, parcourir la source](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Arrêter le débogage, le terminer ou le détacher des processus](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurer le comportement d’exécution de plusieurs processus  
 Par défaut, lorsque plusieurs processus s'exécutent dans le débogueur, les commandes de saut, de progression et d'arrêt du débogueur affectent généralement tous les processus. Par exemple, lorsqu'un processus est interrompu à un point d'arrêt, l'exécution de tous les autres processus est également interrompu. Vous pouvez modifier ce comportement par défaut pour mieux contrôler les cibles des commandes d'exécution.  
  
1. Dans le menu **Déboguer** , choisissez **Options et paramètres**.  
  
2. Dans la page **débogage**, **général** , désactivez la case à cocher **arrêter tous les processus lorsqu’un processus s’arrête** .  
  
   ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les fichiers sources et de symboles (.pdb)  
 Pour parcourir le code source d'un processus, le débogueur doit accéder aux fichiers sources et aux fichiers de symboles du processus. Consultez [spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer en utilisant la fenêtre Code Machine. Consultez [Comment : utiliser la fenêtre Code machine](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Démarrer plusieurs processus dans une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur  
  
- [Démarrer le débogage de plusieurs processus dans une solution Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [modifier le projet de démarrage](#BKMK_Change_the_startup_project) • [Démarrer un projet spécifique dans une solution](#BKMK_Start_a_specific_project_in_a_solution) • [Démarrer plusieurs projets dans une solution](#BKMK_Start_multiple_projects_in_a_solution) • [attacher à un processus](#BKMK_Attach_to_a_process) • [Démarrer automatiquement un processus dans le débogueur](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution. Pour déboguer un processus enfant :  
> 
> - Effectuez un attachement au processus enfant après son démarrage.  
> 
>   -ou-  
>   - Configurez Windows pour démarrer automatiquement le processus enfant dans une nouvelle instance du débogueur.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Démarrer le débogage de plusieurs processus dans une solution Visual Studio  
 Lorsque vous disposez de plusieurs projets dans une solution Visual Studio qui peuvent s'exécuter indépendamment (projets qui s'exécutent dans des processus distincts), vous pouvez sélectionner les projets que le débogueur démarre.  
  
 ![Modification du type de démarrage pour un projet](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Modifier le projet de démarrage  
 Pour modifier le projet de démarrage d’une solution, sélectionnez le projet dans Explorateur de solutions puis choisissez **définir comme projet de démarrage** dans le menu contextuel.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Démarrer un projet spécifique dans une solution  
 Pour démarrer un projet pour une solution sans modifier le projet de démarrage par défaut, sélectionnez le projet dans Explorateur de solutions puis choisissez **Déboguer** dans le menu contextuel. Vous pouvez ensuite choisir **Démarrer une nouvelle instance** ou **pas à pas détaillé dans la nouvelle instance**.  
  
 ![Retour au](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [début démarrer plusieurs processus dans une solution vs, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Démarrer plusieurs projets dans une solution  
  
1. Sélectionnez la solution dans Explorateur de solutions puis choisissez **Propriétés** dans le menu contextuel.  
  
2. Sélectionnez **Propriétés communes**, **projet de démarrage** dans la boîte de dialogue **Propriétés** .  
  
3. Pour chaque projet que vous souhaitez modifier, choisissez **Démarrer**, **exécuter sans débogage**ou **aucun**.  
  
   ![Retour au](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [début démarrer plusieurs processus dans une solution vs, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Attacher à un processus  
 Le débogueur peut également s' *attacher* aux programmes qui s’exécutent dans des processus en dehors de Visual Studio, y compris les programmes qui s’exécutent sur un périphérique distant. Une fois l'attachement au programme effectué, vous pouvez utiliser les commandes d'exécution du débogueur, inspecter l'état du programme, et ainsi de suite. Les possibilités d'inspection peuvent dépendre de la présence d'informations de débogage dans le programme, de vos droits d'accès au code source de ce dernier et du suivi des informations de débogage par le compilateur JIT Common Language Runtime.  
  
 Pour plus d’informations, consultez [attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) .  
  
 **Attacher à un processus qui s'exécute sur votre ordinateur local**  
  
 Choisissez **Déboguer**, **attacher au processus**. Dans la boîte de dialogue **attacher au processus** , sélectionnez le processus dans la liste **processus disponibles** , puis choisissez **attacher**.  
  
 ![Boîte de dialogue Attacher au processus](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Démarrer automatiquement un processus dans le débogueur  
 Il peut être utile de déboguer le code de démarrage d'un programme lancé par un autre processus. C'est le cas des services et des actions d'installation personnalisée. Dans ces scénarios, il est possible de demander un lancement du débogueur et sa connexion automatique au démarrage de l'application.  
  
1. Démarrez l’éditeur du Registre (**regedit.exe**).  
  
2. Accédez au dossier **HKEY_LOCAL_MACHINE \Software\microsoft\windows Nt\currentversion\image File Execution Options d’exécution de fichier** .  
  
3. Sélectionnez le dossier de l’application à démarrer dans le débogueur.  
  
    Si le nom de l’application n’est pas listé comme dossier enfant, sélectionnez **options d’exécution de fichier image** , puis choisissez **nouveau**, **clé** dans le menu contextuel. Sélectionnez la nouvelle clé, choisissez **Renommer** dans le menu contextuel, puis entrez le nom de l’application.  
  
4. Dans le menu contextuel du dossier d’application, choisissez **nouveau**, valeur de **chaîne**.  
  
5. Remplacez le nom de **la nouvelle valeur par** `debugger` .  
  
6. Dans le menu contextuel de l’entrée du débogueur, choisissez **modifier**.  
  
7. Dans la boîte de dialogue modification de la chaîne, tapez `vsjitdebugger.exe` dans la zone **données** de la valeur.  
  
    ![Boîte de dialogue Modification de la chaîne](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrée de démarrage du débogueur automatique dans regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Basculer les processus, arrêter et continuer l’exécution, parcourir la source  
  
- [Basculer entre les processus](#BKMK_Switch_between_processes) • [commandes arrêter, exécuter pas à pas et continuer](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Basculer entre processus  
 Pendant un débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir le processus actif ou *actuel* dans la barre d’outils emplacement de débogage ou dans la fenêtre **processus** . Pour basculer entre les processus, les deux processus doivent être en mode arrêt.  
  
 **Pour définir le processus en cours**  
  
- Dans la barre d’outils emplacement de débogage, choisissez **traiter** pour afficher la zone de liste **processus** . Sélectionnez le processus que vous souhaitez désigner comme processus actuel.  
  
   ![Basculer entre les processus](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Si la barre d’outils **emplacement de débogage** n’est pas visible, choisissez **Outils**, **personnaliser**. Sous l’onglet **barres d’outils** , choisissez **emplacement de débogage**.  
  
- Ouvrez la fenêtre **processus** (raccourci **CTRL + ALT + Z**), recherchez le processus que vous souhaitez définir comme processus actuel et double-cliquez dessus.  
  
   ![Fenêtre processus](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Le processus actuel est marqué par une flèche jaune.  
  
  Basculer vers un projet en fait le processus en cours du débogage. La fenêtre de débogueur que vous voyez affiche l'état du processus actuel, et toutes les commandes de progression n'affectent que le processus actuel.  
  
  ![Retour aux principaux](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [processus de commutateur, interrompre et continuer l’exécution,](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source) parcourir la source  
  
  ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Commandes Arrêter, Exécuter pas à pas et Continuer  
  
> [!NOTE]
> Par défaut, les commandes de débogage break, continue et step affectent tous les processus en cours de débogage. Pour modifier ce comportement, consultez [configurer le comportement d’exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
|**Commande**|**Arrêter tous les processus lorsqu’un processus s’arrête**<br /><br /> Activé (valeur par défaut)|**Arrêter tous les processus lorsqu’un processus s’arrête**<br /><br /> Désactivé|  
|-|-|-|
|Menu **Déboguer** :<br /><br /> -   **Arrêter tout**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|  
|Menu **Déboguer** :<br /><br /> -   **Pouvoir**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|  
|Menu **Déboguer** :<br /><br /> -   **Pas à pas détaillé**<br />-   **Pas à pas principal**<br />-   **Pas à pas sortant**|Tous les processus s'exécutent pendant les étapes de processus actuelles.<br /><br /> Puis, tous les processus s'arrêtent.|Étapes de processus actuel.<br /><br /> Les processus suspendus reprennent.<br /><br /> Les processus en cours d'exécution se poursuivent.|  
|Menu **Déboguer** :<br /><br /> -   **Pas à pas détaillé du processus actuel**<br />-   **Pas à pas principal dans le processus actuel**<br />-   **Pas à pas sortant du processus actuel**|N/A|Étapes de processus actuel.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Fenêtre source<br /><br /> -   **D'**|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|  
|Menu contextuel de la fenêtre source :<br /><br /> -   **Exécuter jusqu’au curseur**<br /><br /> La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br /><br /> Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Menu contextuel de la fenêtre **processus** :<br /><br /> -   **Arrêter le processus**|N/A|Le processus sélectionné s'interrompt.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Menu contextuel de la fenêtre **processus** :<br /><br /> -   **Continuer le processus**|N/A|Le processus sélectionné reprend.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
  
 ![Retour aux principaux](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [processus de commutateur, interrompre et continuer l’exécution,](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source) parcourir la source  
  
 ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Arrêter le débogage, le terminer ou le détacher des processus  
  
- [Commandes Arrêter, Terminer et Détacher](#BKMK_Stop__terminate__and_detach_commands)  
  
  Par défaut, lorsque vous choisissez **Déboguer**, **arrêter le débogage** lorsque plusieurs processus sont ouverts dans le débogueur, le débogueur se termine ou se détache de tous les processus selon la façon dont le processus a été ouvert dans le débogueur :  
  
- Si le processus actuel a été lancé dans le débogueur, ce processus serait terminé.  
  
- Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.  
  
  Par exemple, si vous démarrez le débogage d’un processus à partir d’une solution Visual Studio, attachez à un autre processus qui est déjà en cours d’exécution, puis choisissez **arrêter le débogage**, la session de débogage se termine, le processus qui a été démarré dans Visual Studio est terminé, tandis que le processus que vous avez attaché reste en cours d’exécution. Vous pouvez utiliser les procédures suivantes pour contrôler la façon dont vous arrêtez le débogage.  
  
> [!NOTE]
> L’option **arrêter tous les processus lorsqu’un processus s’arrête** n’affecte pas l’arrêt du débogage ou l’arrêt et le détachement des processus.  
  
 **Pour modifier la façon dont l'arrêt du débogage affecte un processus individuel**  
  
- Ouvrez la fenêtre **processus** (raccourci **CTRL + ALT + Z**). Sélectionnez un processus, puis activez ou désactivez la case à cocher **détacher lorsque le débogage est arrêté** .  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Commandes arrêter, terminer et détacher  
  
|**Commande**|**Description**|  
|-|-|  
|Menu **Déboguer** :<br /><br /> -   **Arrêter le débogage**|Sauf si le comportement est modifié par l’option **détacher** la fenêtre **processus** lorsque le débogage est arrêté :<br /><br /> 1. les processus démarrés par le débogueur sont terminés.<br />2. les processus attachés sont détachés du débogueur.|  
|Menu **Déboguer** :<br /><br /> -   **Arrêter tout**|Tous les processus sont terminés.|  
|Menu **Déboguer** :<br /><br /> -   **Détacher tout**|Le débogueur se détache de tous les processus.|  
|Menu contextuel de la fenêtre **processus** :<br /><br /> -   **Détacher le processus**|Le débogueur se détache du processus sélectionné.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Menu contextuel de la fenêtre **processus** :<br /><br /> -   **Terminer le processus**|Le processus sélectionné est terminé.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Menu contextuel de la fenêtre **processus** :<br /><br /> -   **Détacher lorsque le débogage s’arrête**|Bascule le comportement de débogage, **arrêter le débogage** pour le processus sélectionné : **Debug**<br /><br /> -Checked : le débogueur se détache du processus.<br />-Cleared : le processus est terminé.|  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [arrêter le débogage, terminer ou détacher des processus](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Retour au contenu du haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les fichiers de symboles (. pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Navigation dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
