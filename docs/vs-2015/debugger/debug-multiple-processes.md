---
title: Debug Processus multiples (fr) Microsoft Docs
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
ms.openlocfilehash: 9a2679825d41a6360dde05e7511d607f8be69dfa
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302552"
---
# <a name="debug-multiple-processes"></a>Déboguer plusieurs processus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Voici comment démarrer les processus de débogage, basculer d'un processus à un autre, arrêter et continuer l'exécution, parcourir la source, arrêter le débogage et mettre fin ou se détacher d'un processus.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a>Contenu  
 [Configurer le comportement d'exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Trouver les fichiers source et symbole (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Changer les processus, casser et poursuivre l’exécution, passez à travers la source](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Arrêter le débogage, le terminer ou le détacher des processus](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
## <a name="configure-the-execution-behavior-of-multiple-processes"></a><a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a>Configurer le comportement d’exécution de plusieurs processus  
 Par défaut, lorsque plusieurs processus s'exécutent dans le débogueur, les commandes de saut, de progression et d'arrêt du débogueur affectent généralement tous les processus. Par exemple, lorsqu'un processus est interrompu à un point d'arrêt, l'exécution de tous les autres processus est également interrompu. Vous pouvez modifier ce comportement par défaut pour mieux contrôler les cibles des commandes d'exécution.  
  
1. Dans le menu **Déboguer** , choisissez **Options et paramètres**.  
  
2. Sur la **page Debugging**, **General,** effacer la pause tous les processus quand un processus casse la case à **cocher.**  
  
   ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="find-the-source-and-symbol-pdb-files"></a><a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les fichiers sources et de symboles (.pdb)  
 Pour parcourir le code source d'un processus, le débogueur doit accéder aux fichiers sources et aux fichiers de symboles du processus. Voir [Specify Symbol (.pdb) et Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer en utilisant la fenêtre Code Machine. Voir [comment : Utilisez la fenêtre de démontage](../debugger/how-to-use-the-disassembly-window.md)  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="start-multiple-processes-in-a-vs-solution-attach-to-a-process-automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a>Démarrer plusieurs processus dans une solution VS, joindre à un processus, démarrer automatiquement un processus dans le débailleur  
  
- [Commencer à débogage de plusieurs processus dans une solution Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) - Changer le projet de [démarrage](#BKMK_Change_the_startup_project) - Démarrer un projet spécifique dans [une solution](#BKMK_Start_a_specific_project_in_a_solution) - Démarrer [plusieurs projets dans une solution](#BKMK_Start_multiple_projects_in_a_solution) - Joindre à un [processus](#BKMK_Attach_to_a_process) - Démarrer automatiquement un processus dans [le débogage](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
> Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution. Pour déboguer un processus enfant :  
> 
> - Effectuez un attachement au processus enfant après son démarrage.  
> 
>   -ou-  
>   - Configurez Windows pour démarrer automatiquement le processus enfant dans une nouvelle instance du débogueur.  
  
### <a name="start-debugging-multiple-processes-in-a-visual-studio-solution"></a><a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a>Commencez à débogage de plusieurs processus dans une solution Visual Studio  
 Lorsque vous disposez de plusieurs projets dans une solution Visual Studio qui peuvent s'exécuter indépendamment (projets qui s'exécutent dans des processus distincts), vous pouvez sélectionner les projets que le débogueur démarre.  
  
 ![Modification du type de démarrage pour un projet](../debugger/media/dbg-execution-startmultipleprojects.png "DBG_Execution_StartMultipleProjects")  
  
#### <a name="change-the-startup-project"></a><a name="BKMK_Change_the_startup_project"></a>Changer le projet de démarrage  
 Pour modifier le projet de démarrage d’une solution, sélectionnez le projet dans Solution Explorer, puis choisissez **Set comme Startup Project** dans le menu context.  
  
#### <a name="start-a-specific-project-in-a-solution"></a><a name="BKMK_Start_a_specific_project_in_a_solution"></a>Démarrer un projet spécifique dans une solution  
 Pour démarrer un projet de solution sans modifier le projet de démarrage par défaut, sélectionnez le projet dans Solution Explorer, puis choisissez **Debug** dans le menu contextuelle. Vous pouvez alors choisir **Démarrer nouvelle instance** ou step Into nouvelle **instance**.  
  
 ![Retour vers le haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Démarrer plusieurs processus dans une solution VS, joindre à un processus, démarrer automatiquement un processus dans le débailleur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
#### <a name="start-multiple-projects-in-a-solution"></a><a name="BKMK_Start_multiple_projects_in_a_solution"></a>Démarrer plusieurs projets dans une solution  
  
1. Sélectionnez la solution dans Solution Explorer, puis choisissez **des propriétés** sur le menu contextuelle.  
  
2. Sélectionnez **Common Properties**, **Startup Project** sur la boîte de dialogue **Propriétés.**  
  
3. Pour chaque projet que vous voulez changer, choisissez soit **Démarrer**, **Démarrer sans débogage**, ou **Aucun**.  
  
   ![Retour vers le haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Démarrer plusieurs processus dans une solution VS, joindre à un processus, démarrer automatiquement un processus dans le débailleur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
   ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
### <a name="attach-to-a-process"></a><a name="BKMK_Attach_to_a_process"></a>Joindre à un processus  
 Le débbugger peut également *s’attacher* à des programmes qui sont en cours d’exécution dans les processus en dehors de Visual Studio, y compris les programmes qui sont en cours d’exécution sur un appareil distant. Une fois l'attachement au programme effectué, vous pouvez utiliser les commandes d'exécution du débogueur, inspecter l'état du programme, et ainsi de suite. Les possibilités d'inspection peuvent dépendre de la présence d'informations de débogage dans le programme, de vos droits d'accès au code source de ce dernier et du suivi des informations de débogage par le compilateur JIT Common Language Runtime.  
  
 Voir [Joindre aux processus d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) pour plus d’informations.  
  
 **Attacher à un processus qui s'exécute sur votre ordinateur local**  
  
 Choisissez **Debug**, **Attachez-vous au processus**. Sur la boîte de dialogue **Attach to Process,** sélectionnez le processus dans la liste **des processus disponibles,** puis choisissez **Attach**.  
  
 ![Joindre à la boîte de dialogue Process](../debugger/media/dbg-attachtoprocessdlg.png "DBG_AttachToProcessDlg")  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
### <a name="automatically-start-a-process-in-the-debugger"></a><a name="BKMK_Automatically_start_an_process_in_the_debugger"></a>Démarrez automatiquement un processus dans le débagé  
 Il peut être utile de déboguer le code de démarrage d'un programme lancé par un autre processus. C'est le cas des services et des actions d'installation personnalisée. Dans ces scénarios, il est possible de demander un lancement du débogueur et sa connexion automatique au démarrage de l'application.  
  
1. Démarrer l’éditeur de registre (**regedit.exe**).  
  
2. Naviguez vers le **dossier HKEY_LOCAL_MACHINE-Software-Microsoft-Windows NT-CurrentVersion-Image File Options.**  
  
3. Sélectionnez le dossier de l’application à démarrer dans le débogueur.  
  
    Si le nom de l’application n’est pas répertorié comme un dossier pour enfants, sélectionnez **les options d’exécution des fichiers d’images** et choisissez ensuite **De nouvelles** **, Clé** sur le menu contexte. Sélectionnez la nouvelle clé, choisissez **Rename** sur le menu raccourci, puis entrez le nom de l’application.  
  
4. Sur le menu contextuelle du dossier d’application, choisissez **New**, **String Value**.  
  
5. Changer le nom de la nouvelle `debugger`valeur de New **Value** à .  
  
6. Au menu contextuelle de l’entrée de débogé, choisissez **Modifier**.  
  
7. Sur la boîte de dialogue `vsjitdebugger.exe` Edit String, tapez dans la boîte **de données De valeur.**  
  
    ![Boîte de dialogue Modification de la chaîne](../debugger/media/dbg-execution-automaticstart-editstringdlg.png "DBG_Execution_AutomaticStart_EditStringDlg")  
  
   ![Entrée de démarrage du débogueur automatique dans regedit.exe](../debugger/media/dbg-execution-automaticstart-result.png "DBG_Execution_AutomaticStart_Result")  
  
   ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="switch-processes-break-and-continue-execution-step-through-source"></a><a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a>Changer les processus, casser et poursuivre l’exécution, passez à travers la source  
  
- [Passer d’un processus à l’autre](#BKMK_Switch_between_processes) : [Casser, faire un pas et continuer les commandes](#BKMK_Break__step__and_continue_commands)  
  
### <a name="switch-between-processes"></a><a name="BKMK_Switch_between_processes"></a> Basculer entre processus  
 Pendant un débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir le processus actif ou *en cours* dans la barre d’outils Debug Location ou dans la fenêtre **Processes.** Pour basculer entre les processus, les deux processus doivent être en mode arrêt.  
  
 **Pour définir le processus en cours**  
  
- Sur la barre d’outils Debug Location, choisissez **Process** pour afficher la case de liste **de processus.** Sélectionnez le processus que vous souhaitez désigner comme processus actuel.  
  
   ![Basculer d’un processus à l’autre](../debugger/media/dbg-execution-switchbetweenmodules.png "DBG_Execution_SwitchBetweenModules")  
  
   Si la barre **d’outils Debug Location** n’est pas visible, choisissez **Des outils,** **personnalisez**. Sur l’onglet **Toolbars,** choisissez **Debug Location**.  
  
- Ouvrez la fenêtre **Processes** (raccourci **Ctrl-Alt-Z**), trouvez le processus que vous souhaitez définir comme processus actuel, et double-cliquez dessus.  
  
   ![Fenêtre de processus](../debugger/media/dbg-processeswindow.png "DBG_ProcessesWindow")  
  
   Le processus actuel est marqué par une flèche jaune.  
  
  Basculer vers un projet en fait le processus en cours du débogage. La fenêtre de débogueur que vous voyez affiche l'état du processus actuel, et toutes les commandes de progression n'affectent que le processus actuel.  
  
  ![Retour au haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [des processus Switch, casser et continuer l’exécution, passer à travers la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
  ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
### <a name="break-step-and-continue-commands"></a><a name="BKMK_Break__step__and_continue_commands"></a> Commandes Arrêter, Exécuter pas à pas et Continuer  
  
> [!NOTE]
> Par défaut, les commandes de débogage break, continue et step affectent tous les processus en cours de débogage. Pour modifier ce comportement, voir [Configurer le comportement d’exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Commande**|**Briser tous les processus lorsqu’un processus se brise**<br /><br /> Activé (valeur par défaut)|**Briser tous les processus lorsqu’un processus se brise**<br /><br /> Désactivé|  
|**Menu Debug:**<br /><br /> -   **Briser tous les**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|  
|**Menu Debug:**<br /><br /> -   **Continuer**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|  
|**Menu Debug:**<br /><br /> -   **Entrez dans**<br />-   **Étape au-dessus**<br />-   **Sortez**|Tous les processus s'exécutent pendant les étapes de processus actuelles.<br /><br /> Puis, tous les processus s'arrêtent.|Étapes de processus actuel.<br /><br /> Les processus suspendus reprennent.<br /><br /> Les processus en cours d'exécution se poursuivent.|  
|**Menu Debug:**<br /><br /> -   **Entrez dans le processus actuel**<br />-   **Étape sur le processus actuel**<br />-   **Sortez le processus actuel**|N/A|Étapes de processus actuel.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|Fenêtre source<br /><br /> -   **Breakpoint**|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|  
|Menu contextuel de la fenêtre source :<br /><br /> -   **Courir au curseur**<br /><br /> La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br /><br /> Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contexte fenêtre:<br /><br /> -   **Processus de rupture**|N/A|Le processus sélectionné s'interrompt.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contexte fenêtre:<br /><br /> -   **Processus continu**|N/A|Le processus sélectionné reprend.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
  
 ![Retour au haut](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [des processus Switch, casser et continuer l’exécution, passer à travers la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="stop-debugging-terminate-or-detach-from-processes"></a><a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a>Arrêtez de débogage, terminez ou détachez-vous des processus  
  
- [Commandes Arrêter, Terminer et Détacher](#BKMK_Stop__terminate__and_detach_commands)  
  
  Par défaut, lorsque vous choisissez **Debug**, **Arrêtez Debugging** lorsque plusieurs processus sont ouverts dans le débogage, le débbuggeur se termine ou se détache de tous les processus en fonction de la façon dont le processus a été ouvert dans le débogage:  
  
- Si le processus actuel a été lancé dans le débogueur, ce processus serait terminé.  
  
- Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.  
  
  Par exemple, si vous commencez à débogage d’un processus à partir d’une solution Visual Studio, attachez-vous à un autre processus qui est déjà en cours d’exécution, puis choisissez **Stop Debugging**, la session de débogage se termine, le processus qui a été commencé dans Visual Studio est terminé, tandis que le processus que vous avez attaché est laissé en cours d’exécution. Vous pouvez utiliser les procédures suivantes pour contrôler la façon dont vous arrêtez le débogage.  
  
> [!NOTE]
> La **pause de tous les processus lorsqu’une** option de ruptures de processus n’affecte pas l’arrêt du débogage ou la fin et le détachement des processus.  
  
 **Pour modifier la façon dont l'arrêt du débogage affecte un processus individuel**  
  
- Ouvrez la fenêtre **Processes** (raccourci **Ctrl-Alt-Z**). Sélectionnez un processus, puis sélectionnez ou effacez le **détachement lorsque le débogage a cessé** de cocher la case.  
  
### <a name="stop-terminate-and-detach-commands"></a><a name="BKMK_Stop__terminate__and_detach_commands"></a>Arrêtez, terminez et détachez les commandes  
  
|||  
|-|-|  
|**Commande**|**Description**|  
|**Menu Debug:**<br /><br /> -   **Arrêtez Debugging**|Sauf si le comportement est modifié par la fenêtre **Processes** **Détacher lorsque le débogage arrête l’option:**<br /><br /> 1. Les processus commencés par le débbuggeur sont terminés.<br />2. Les processus ci-joints sont détachés du débagé.|  
|**Menu Debug:**<br /><br /> -   **Mettre fin à tous les**|Tous les processus sont terminés.|  
|**Menu Debug:**<br /><br /> -   **Détachez tous**|Le débogueur se détache de tous les processus.|  
|**Processus** menu contexte fenêtre:<br /><br /> -   **Processus de détachement**|Le débogueur se détache du processus sélectionné.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contexte fenêtre:<br /><br /> -   **Processus de résiliation**|Le processus sélectionné est terminé.<br /><br /> D'autres processus conservent leur état existant (Suspendu ou En cours d'exécution).|  
|**Processus** menu contexte fenêtre:<br /><br /> -   **Détachez lorsque le débogage s’arrête**|Toggles le comportement de **Debug**, **Arrêtez Debugging** pour le processus sélectionné:<br /><br /> - Vérifié : Le débbuggeur se détache du processus.<br />- Effacement : Le processus est terminé.|  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Arrêtez de débogage, terminez ou détachez-vous des processus](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Retour au sommet](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contenu](#BKMK_Contents)  
  
## <a name="see-also"></a> Voir aussi  
 [Spécifier les fichiers symbole (.pdb) et source](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Joindre aux processus d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Naviguer à travers code avec le Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Débugging juste-à-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)
