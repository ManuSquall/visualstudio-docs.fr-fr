---
title: Déboguer plusieurs processus | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 56982a3b5c0a0d8a5cb0b682ab67b6f5eb133dd1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793046"
---
# <a name="debug-multiple-processes"></a>Déboguer plusieurs processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici comment démarrer les processus de débogage, basculer d'un processus à un autre, arrêter et continuer l'exécution, parcourir la source, arrêter le débogage et mettre fin ou se détacher d'un processus.  
  
##  <a name="BKMK_Contents"></a> Sommaire  
 [Configurer le comportement d’exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Rechercher les sources et symboles (fichiers .pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Démarrer plusieurs processus dans une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Basculer les processus, arrêter et poursuivre l’exécution, accéder à la source](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Arrêter le débogage, le terminer ou détacher des processus](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Configurer le comportement d’exécution de plusieurs processus  
 Par défaut, lorsque plusieurs processus s'exécutent dans le débogueur, les commandes de saut, de progression et d'arrêt du débogueur affectent généralement tous les processus. Par exemple, lorsqu'un processus est interrompu à un point d'arrêt, l'exécution de tous les autres processus est également interrompu. Vous pouvez modifier ce comportement par défaut pour mieux contrôler les cibles des commandes d'exécution.  
  
1. Dans le menu **Déboguer** , choisissez **Options et paramètres**.  
  
2. Sur le **débogage**, **général** page, désactivez le **arrêter tous les processus lorsqu’un processus s’arrête** case à cocher.  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les sources et symboles (fichiers .pdb)  
 Pour parcourir le code source d'un processus, le débogueur doit accéder aux fichiers sources et aux fichiers de symboles du processus. Consultez [Spécifier les fichiers de symbole (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer en utilisant la fenêtre Code Machine. Consultez [Comment : utiliser la fenêtre code machine](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Démarrer plusieurs processus dans une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur  
  
-   [Démarrer le débogage de plusieurs processus dans une solution Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [modifier le projet de démarrage](#BKMK_Change_the_startup_project) • [démarrer un projet spécifique dans une solution](#BKMK_Start_a_specific_project_in_a_solution) • [démarrer plusieurs projets dans un solution](#BKMK_Start_multiple_projects_in_a_solution) • [attacher à un processus](#BKMK_Attach_to_a_process) • [démarrer automatiquement un processus dans le débogueur](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution. Pour déboguer un processus enfant :  
> 
> - Effectuez un attachement au processus enfant après son démarrage.  
> 
>   - ou -  
>   -   Configurez Windows pour démarrer automatiquement le processus enfant dans une nouvelle instance du débogueur.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Démarrer le débogage de plusieurs processus dans une solution Visual Studio  
 Lorsque vous disposez de plusieurs projets dans une solution Visual Studio qui peuvent s'exécuter indépendamment (projets qui s'exécutent dans des processus distincts), vous pouvez sélectionner les projets que le débogueur démarre.  
  
 ![Modification du type de démarrage pour un projet](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Modifier le projet de démarrage  
 Pour modifier le projet de démarrage pour une solution, sélectionnez le projet dans l’Explorateur de solutions, puis choisissez **définir comme projet de démarrage** dans le menu contextuel.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Démarrer un projet spécifique dans une solution  
 Pour démarrer un projet pour une solution sans modifier le projet de démarrage par défaut, sélectionnez le projet dans l’Explorateur de solutions, puis choisissez **déboguer** dans le menu contextuel. Vous pouvez ensuite choisir **démarrer une nouvelle instance** ou **pas à pas détaillé de nouvelle instance**.  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [démarrer plusieurs processus dans une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Démarrer plusieurs projets dans une solution  
  
1. Sélectionnez la solution dans l’Explorateur de solutions, puis choisissez **propriétés** dans le menu contextuel.  
  
2. Sélectionnez **propriétés communes**, **projet de démarrage** sur le **propriétés** boîte de dialogue.  
  
3. Pour chaque projet que vous souhaitez modifier, choisissez **Démarrer**, **démarrer sans débogage**, ou **aucun**.  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [démarrer plusieurs processus dans une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Attacher à un processus  
 Le débogueur peut également *attacher* aux programmes qui sont exécutent dans le processus en dehors de Visual Studio, y compris les programmes qui sont exécutent sur un périphérique distant. Une fois l'attachement au programme effectué, vous pouvez utiliser les commandes d'exécution du débogueur, inspecter l'état du programme, et ainsi de suite. Les possibilités d'inspection peuvent dépendre de la présence d'informations de débogage dans le programme, de vos droits d'accès au code source de ce dernier et du suivi des informations de débogage par le compilateur JIT Common Language Runtime.  
  
 Consultez [attacher aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) pour plus d’informations.  
  
 **Attacher à un processus qui s’exécute sur votre ordinateur local**  
  
 Choisissez **déboguer**, **attacher au processus**. Sur le **attacher au processus** boîte de dialogue, sélectionnez le processus à partir de la **processus disponibles** liste, puis choisissez **attacher**.  
  
 ![Attacher à la boîte de dialogue traiter](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Démarrer automatiquement un processus dans le débogueur  
 Il peut être utile de déboguer le code de démarrage d'un programme lancé par un autre processus. C'est le cas des services et des actions d'installation personnalisée. Dans ces scénarios, il est possible de demander un lancement du débogueur et sa connexion automatique au démarrage de l'application.  
  
1. Démarrez l’Éditeur du Registre (**regedit.exe**).  
  
2. Accédez à la **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options** dossier.  
  
3. Sélectionnez le dossier de l’application à démarrer dans le débogueur.  
  
    Si le nom de l’application n’est pas répertorié comme un dossier enfant, sélectionnez **Image File Execution Options** , puis **New**, **clé** dans le menu contextuel. Sélectionnez la nouvelle clé, choisissez **renommer** dans le menu contextuel, puis entrez le nom de l’application.  
  
4. Dans le menu contextuel du dossier d’application, choisissez **New**, **valeur de chaîne**.  
  
5. Modifier le nom de la nouvelle valeur à partir de **nouvelle valeur** à `debugger`.  
  
6. Dans le menu contextuel de l’entrée du débogueur, choisissez **modifier**.  
  
7. Dans la boîte de dialogue Modifier la chaîne, tapez `vsjitdebugger.exe` dans le **données de la valeur** boîte.  
  
    ![Modifier la boîte de dialogue chaîne](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrée de démarrage du débogueur automatique dans regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Basculer les processus, arrêter et poursuivre l’exécution, accéder à la source  
  
-   [Basculer entre les processus](#BKMK_Switch_between_processes) • [Break, étape et continue de commandes](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Basculer entre les processus  
 Pendant un débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir actif ou *actuel* processus dans la barre d’outils emplacement de débogage ou dans le **processus** fenêtre. Pour basculer entre les processus, les deux processus doivent être en mode arrêt.  
  
 **Pour définir le processus actuel**  
  
- Dans la barre d’outils emplacement de débogage, choisissez **processus** pour afficher le **processus** zone de liste. Sélectionnez le processus que vous souhaitez désigner comme processus actuel.  
  
   ![Basculer entre les processus](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Si le **emplacement de débogage** barre d’outils n’est pas visible, choisissez **outils**, **personnaliser**. Sur le **barres d’outils** , choisir **emplacement de débogage**.  
  
- Ouvrez le **processus** fenêtre (raccourci **Ctrl + Alt + Z**), recherchez le processus que vous souhaitez définir en tant que le processus en cours et double-cliquez dessus.  
  
   ![Fenêtre processus](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Le processus actuel est marqué par une flèche jaune.  
  
  Basculer vers un projet en fait le processus en cours du débogage. La fenêtre de débogueur que vous voyez affiche l'état du processus actuel, et toutes les commandes de progression n'affectent que le processus actuel.  
  
  ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [basculer les processus, arrêter et poursuivre l’exécution, accéder à la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Arrêter, l’étape et continue de commandes  
  
> [!NOTE]
>  Par défaut, les commandes de débogage break, continue et step affectent tous les processus en cours de débogage. Pour modifier ce comportement, consultez [configurer le comportement d’exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Commande**|**Arrêter tous les processus lorsqu’un processus s’arrête**<br /><br /> Activé (valeur par défaut)|**Arrêter tous les processus lorsqu’un processus s’arrête**<br /><br /> Effacé|  
|**Déboguer** menu :<br /><br /> -   **Interrompre tout**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|  
|**Déboguer** menu :<br /><br /> -   **Continuer**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|  
|**Déboguer** menu :<br /><br /> -   **Pas à pas détaillé**<br />-   **Pas à pas principal**<br />-   **Pas à pas sortant**|Tous les processus s'exécutent pendant les étapes de processus actuelles.<br /><br /> Puis, tous les processus s'arrêtent.|Étapes de processus actuel.<br /><br /> Les processus suspendus reprennent.<br /><br /> Les processus en cours d'exécution se poursuivent.|  
|**Déboguer** menu :<br /><br /> -   **Pas à pas détaillé des processus en cours**<br />-   **Pas à pas principal des processus en cours**<br />-   **Pas à pas sortant des processus en cours**|N/A|Étapes de processus actuel.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Fenêtre source<br /><br /> -   **Point d’arrêt**|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|  
|Menu contextuel de la fenêtre source :<br /><br /> -   **Exécuter jusqu’au curseur**<br /><br /> La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br /><br /> Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contextuel de fenêtre :<br /><br /> -   **Arrêter le processus**|N/A|Le processus sélectionné s'interrompt.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contextuel de fenêtre :<br /><br /> -   **Continuer le processus**|N/A|Le processus sélectionné reprend.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [basculer les processus, arrêter et poursuivre l’exécution, accéder à la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Arrêter le débogage, le terminer ou détacher des processus  
  
- [Arrêter, terminer et détacher des commandes](#BKMK_Stop__terminate__and_detach_commands)  
  
  Par défaut, lorsque vous choisissez **déboguer**, **arrêter le débogage** lorsque plusieurs processus sont ouverts dans le débogueur, le débogueur s’arrête ou se détache de tous les processus en fonction de la façon dont le processus a été ouvert dans le débogueur :  
  
- Si le processus actuel a été lancé dans le débogueur, ce processus serait terminé.  
  
- Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.  
  
  Par exemple, si vous démarrez le débogage d’un processus à partir d’une solution Visual Studio, attachez à un autre processus est déjà en cours d’exécution, puis choisissez **arrêter le débogage**, la session de débogage se termine, le processus qui a été démarré dans Visual Studio se termine, tandis que le processus que vous avez attaché est laissé en cours d’exécution. Vous pouvez utiliser les procédures suivantes pour contrôler la façon dont vous arrêtez le débogage.  
  
> [!NOTE]
>  Le **arrêter tous les processus lorsqu’un processus s’arrête** option n’affecte pas l’arrêt de débogage ou l’arrêt et détachement des processus.  
  
 **Pour modifier comment arrêter le débogage affecte un processus individuel**  
  
-   Ouvrez le **processus** fenêtre (raccourci **Ctrl + Alt + Z**). Sélectionnez un processus puis activez ou désactivez le **détacher lorsque le débogage est arrêté** case à cocher.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Arrêter, terminer et détacher des commandes  
  
|||  
|-|-|  
|**Commande**|**Description**|  
|**Déboguer** menu :<br /><br /> -   **Arrêter le débogage**|À moins que le comportement est modifié par **processus** fenêtre **détacher lorsque le débogage s’arrête** option :<br /><br /> 1.  Les processus démarrés par le débogueur sont terminés.<br />2.  Les processus attachés sont détachés du débogueur.|  
|**Déboguer** menu :<br /><br /> -   **Tout arrêter**|Tous les processus sont terminés.|  
|**Déboguer** menu :<br /><br /> -   **Détacher tout**|Le débogueur se détache de tous les processus.|  
|**Processus** menu contextuel de fenêtre :<br /><br /> -   **Détacher le processus**|Le débogueur se détache du processus sélectionné.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contextuel de fenêtre :<br /><br /> -   **Terminer le processus**|Le processus sélectionné est terminé.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contextuel de fenêtre :<br /><br /> -   **Détacher lorsque le débogage s’arrête**|Active ou désactive le comportement de **déboguer**, **arrêter le débogage** pour le processus sélectionné :<br /><br /> -Checked : Le débogueur se détache du processus.<br />-Désactivé : Le processus est terminé.|  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [arrêter le débogage, le terminer ou détacher des processus](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Retour au début](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Sommaire](#BKMK_Contents)  
  
## <a name="see-also"></a>Voir aussi  
 [Spécifier les symboles (.pdb) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Débogage juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)



