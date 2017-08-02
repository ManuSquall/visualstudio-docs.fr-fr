---
title: "D&#233;boguer un ou plusieurs processus dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.programs"
  - "vs.debug.processes.attaching"
  - "vs.debug.activeprogram"
  - "vs.debug.attaching"
  - "vs.debug.attachedprocesses"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: bde37134-66af-4273-b02e-05b3370c31ab
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# D&#233;boguer un ou plusieurs processus dans Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Voici comment démarrer les processus de débogage, basculer d'un processus à un autre, arrêter et continuer l'exécution, parcourir la source, arrêter le débogage et mettre fin ou se détacher d'un processus.  
  
##  <a name="BKMK_Contents"></a> Sommaire  
 [Configurer le comportement d'exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
 [Rechercher les fichiers sources et de symboles (.pdb)](#BKMK_Find_the_source_and_symbol___pdb__files)  
  
 [Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 [Basculer les processus, arrêter et poursuivre l'exécution, accéder à la source](#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 [Arrêter le débogage, le terminer ou le détacher des processus](#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
##  <a name="BKMK_Configure_the_execution_behavior_of_multiple_processes"></a> Configurer le comportement d'exécution de plusieurs processus  
 Par défaut, lorsque plusieurs processus s'exécutent dans le débogueur, les commandes de saut, de progression et d'arrêt du débogueur affectent généralement tous les processus.  Par exemple, lorsqu'un processus est interrompu à un point d'arrêt, l'exécution de tous les autres processus est également interrompu.  Vous pouvez modifier ce comportement par défaut pour mieux contrôler les cibles des commandes d'exécution.  
  
1.  Dans le menu **Déboguer**, choisissez **Options et paramètres**.  
  
2.  Sur la page **Débogage**, **Général**, désactivez la case à cocher **Arrêter tous les processus lorsqu'un processus s'arrête**.  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Find_the_source_and_symbol___pdb__files"></a> Rechercher les fichiers sources et de symboles \(.pdb\)  
 Pour parcourir le code source d'un processus, le débogueur doit accéder aux fichiers sources et aux fichiers de symboles du processus.  Consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
 Si vous ne pouvez pas accéder aux fichiers pour un processus, vous pouvez naviguer en utilisant la fenêtre Code Machine.  Consultez [Comment : utiliser la fenêtre Code Machine](../debugger/how-to-use-the-disassembly-window.md).  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger"></a> Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur  
  
-   [Démarrer plusieurs processus de débogage dans une solution Visual Studio](#BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution) • [Modifier le projet de démarrage](#BKMK_Change_the_startup_project) • [Exécuter un projet spécifique dans une solution](#BKMK_Start_a_specific_project_in_a_solution) • [Démarrer plusieurs projets dans une solution](#BKMK_Start_multiple_projects_in_a_solution) • [Attacher à un processus](#BKMK_Attach_to_a_process) • [Démarrer automatiquement un processus du débogueur](#BKMK_Automatically_start_an_process_in_the_debugger)  
  
> [!NOTE]
>  Le débogueur n'effectue pas un attachement automatique à un processus enfant démarré par un processus débogué, même si le projet enfant se trouve dans la même solution.  Pour déboguer un processus enfant :  
>   
>  -   Effectuez un attachement au processus enfant après son démarrage.  
>   
>      ou  
> -   Configurez Windows pour démarrer automatiquement le processus enfant dans une nouvelle instance du débogueur.  
  
###  <a name="BKMK_Start_debugging_multiple_processes_in_a_Visual_Studio_solution"></a> Démarrer plusieurs processus de débogage dans une solution Visual Studio  
 Lorsque vous disposez de plusieurs projets dans une solution Visual Studio qui peuvent s'exécuter indépendamment \(projets qui s'exécutent dans des processus distincts\), vous pouvez sélectionner les projets que le débogueur démarre.  
  
 ![Modification du type de démarrage pour un projet](../debugger/media/dbg_execution_startmultipleprojects.png "DBG\_Execution\_StartMultipleProjects")  
  
####  <a name="BKMK_Change_the_startup_project"></a> Modifier le projet de démarrage  
 Pour modifier le projet de démarrage d'une solution, sélectionnez le projet dans l'Explorateur de solutions, puis choisissez **Définir comme projet de démarrage** dans le menu contextuel.  
  
####  <a name="BKMK_Start_a_specific_project_in_a_solution"></a> Exécuter un projet spécifique dans une solution  
 Pour démarrer un projet pour une solution sans modifier le projet de démarrage par défaut, sélectionnez le projet dans l'Explorateur de solutions, puis choisissez **Déboguer** dans le menu contextuel.  Vous pouvez ensuite sélectionner **Démarrer une nouvelle instance** ou **Pas à pas détaillé dans la nouvelle instance**.  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
####  <a name="BKMK_Start_multiple_projects_in_a_solution"></a> Démarrer plusieurs projets dans une solution  
  
1.  Dans l'Explorateur de solutions, sélectionnez la solution puis, dans le menu contextuel, sélectionnez **Propriétés**.  
  
2.  Sélectionnez **Propriétés communes**, **Projet de démarrage** dans la boîte de dialogue **Propriétés**.  
  
3.  Pour chaque projet à modifier, choisissez **Démarrer**, **Exécuter sans débogage** ou **Aucun**.  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Démarrer plusieurs processus d'une solution VS, attacher à un processus, démarrer automatiquement un processus dans le débogueur](../debugger/debug-multiple-processes.md#BKMK_Start_multiple_processes_in_a_VS_solution__attach_to_a_process__automatically_start_a_process_in_the_debugger)  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Attach_to_a_process"></a> Attacher à un processus  
 Le débogueur peut également *s'attacher* aux programmes qui s'exécutent dans des processus en dehors de Visual Studio, notamment les programmes qui s'exécutent sur un périphérique distant.  Une fois l'attachement au programme effectué, vous pouvez utiliser les commandes d'exécution du débogueur, inspecter l'état du programme, et ainsi de suite.  Les possibilités d'inspection peuvent dépendre de la présence d'informations de débogage dans le programme, de vos droits d'accès au code source de ce dernier et du suivi des informations de débogage par le compilateur JIT Common Language Runtime.  
  
 Pour plus d'informations, consultez [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 **Attacher à un processus qui s'exécute sur votre ordinateur local**  
  
 Sélectionnez **Déboguer**, **Attacher au processus**.  Dans la boîte de dialogue **Attacher au processus**, sélectionnez le processus dans la liste **Processus disponibles**, puis choisissez **Attacher**.  
  
 ![Boîte de dialogue Attacher au processus](../debugger/media/dbg_attachtoprocessdlg.png "DBG\_AttachToProcessDlg")  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Automatically_start_an_process_in_the_debugger"></a> Démarrer automatiquement un processus du débogueur  
 Il peut être utile de déboguer le code de démarrage d'un programme lancé par un autre processus.  C'est le cas des services et des actions d'installation personnalisée.  Dans ces scénarios, il est possible de demander un lancement du débogueur et sa connexion automatique au démarrage de l'application.  
  
1.  Démarrez l'Éditeur du Registre \(**regedit.exe**\).  
  
2.  Accédez au dossier **HKEY\_LOCAL\_MACHINE\\Software\\Microsoft\\Windows NT\\CurrentVersion\\Image File Execution Options**.  
  
3.  Sélectionnez le dossier de l'application à démarrer dans le débogueur.  
  
     Si le nom de l'application n'est pas répertorié comme dossier enfant, sélectionnez **Options d'exécution de fichier image** puis **Nouveau**, **Clé** dans le menu contextuel.  Sélectionnez la nouvelle clé, choisissez **Renommer** dans le menu contextuel, puis entrez le nom de l'application.  
  
4.  Dans le menu contextuel du dossier d'application, choisissez **Nouveau**, **Valeur de chaîne**.  
  
5.  Modifiez le nom de la nouvelle valeur de **New Value** en `débogueur`.  
  
6.  Dans le menu contextuel de l'entrée du débogueur, choisissez **Modifier**.  
  
7.  Dans la boîte de dialogue Modification de la chaîne, tapez `vsjitdebugger.exe` dans la zone **Données de la valeur**.  
  
     ![Boîte de dialogue Modification de la chaîne](../debugger/media/dbg_execution_automaticstart_editstringdlg.png "DBG\_Execution\_AutomaticStart\_EditStringDlg")  
  
 ![Entrée de démarrage du débogueur automatique dans regedit.exe](~/docs/debugger/media/dbg_execution_automaticstart_result.png "DBG\_Execution\_AutomaticStart\_Result")  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Switch_processes__break_and_continue_execution__step_through_source"></a> Basculer les processus, arrêter et poursuivre l'exécution, accéder à la source  
  
-   [Basculer entre les processus](#BKMK_Switch_between_processes) • [Commandes Arrêter, Exécuter pas à pas, Continuer](#BKMK_Break__step__and_continue_commands)  
  
###  <a name="BKMK_Switch_between_processes"></a> Basculer entre les processus  
 Pendant un débogage, vous pouvez attacher plusieurs processus à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné.  Vous pouvez définir le processus actif ou *actuel* dans la barre d'outils Emplacement de débogage ou dans la fenêtre **Processus**.  Pour basculer entre les processus, les deux processus doivent être en mode arrêt.  
  
 **Pour définir le processus en cours**  
  
-   Dans la barre d'outils Emplacement de débogage, choisissez **Processus** pour afficher la zone de liste **Processus**.  Sélectionnez le processus que vous souhaitez désigner comme processus actuel.  
  
     ![Basculer entre processus](../debugger/media/dbg_execution_switchbetweenmodules.png "DBG\_Execution\_SwitchBetweenModules")  
  
     Si la barre d'outils **Emplacement de débogage** n'est pas visible, sélectionnez **Outils**, **Personnaliser**.  Sous l'onglet **Barres d'outils**, choisissez **Emplacement de débogage**.  
  
-   Ouvrez la fenêtre **Processus** \(raccourci **Ctrl\+Alt\+Z**\), recherchez le processus que vous souhaitez définir comme processus actuel et double\-cliquez dessus.  
  
     ![Fenêtre Processus](../debugger/media/dbg_processeswindow.png "DBG\_ProcessesWindow")  
  
     Le processus actuel est marqué par une flèche jaune.  
  
 Basculer vers un projet en fait le processus en cours du débogage.  La fenêtre de débogueur que vous voyez affiche l'état du processus actuel, et toutes les commandes de progression n'affectent que le processus actuel.  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Basculer les processus, arrêter et poursuivre l'exécution, accéder à la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
###  <a name="BKMK_Break__step__and_continue_commands"></a> Commandes Arrêter, Exécuter pas à pas, Continuer  
  
> [!NOTE]
>  Par défaut, les commandes de débogage break, continue et step affectent tous les processus en cours de débogage.  Pour modifier ce comportement, consultez [Configurer le comportement d'exécution de plusieurs processus](#BKMK_Configure_the_execution_behavior_of_multiple_processes)  
  
||||  
|-|-|-|  
|**Commande**|**Arrêter tous les processus lorsqu'un processus s'arrête**<br /><br /> Activé \(valeur par défaut\)|**Arrêter tous les processus lorsqu'un processus s'arrête**<br /><br /> Effacé|  
|Menu**Déboguer** :<br /><br /> -   **Interrompre tout**|Tous les processus s'arrêtent.|Tous les processus s'arrêtent.|  
|Menu**Déboguer** :<br /><br /> -   **Continue**|Tout les processus reprennent.|Tous les processus suspendus reprennent.|  
|Menu**Déboguer** :<br /><br /> -   **Pas à pas détaillé**<br />-   **Pas à pas principal**<br />-   **Pas à pas sortant**|Tous les processus s'exécutent pendant les étapes de processus actuelles.<br /><br /> Puis, tous les processus s'arrêtent.|Étapes de processus actuel.<br /><br /> Les processus suspendus reprennent.<br /><br /> Les processus en cours d'exécution se poursuivent.|  
|Menu**Déboguer** :<br /><br /> -   **Pas à pas détaillé du processus actuel**<br />-   **Pas à pas principal du processus actuel**<br />-   **Pas à pas sortant du processus actuel**|N\/A|Étapes de processus actuel.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
|Fenêtre source<br /><br /> -   **Point d'arrêt**|Tous les processus s'arrêtent.|Seul le processus de fenêtre source est rompu.|  
|Menu contextuel de la fenêtre source :<br /><br /> -   **Exécuter jusqu'au curseur**<br /><br /> La fenêtre source doit figurer dans le processus actuel.|Tous les processus s'exécutent pendant que le processus de fenêtre source s'exécute jusqu'au curseur puis s'arrête.<br /><br /> Puis, tous les autres processus s'arrêtent.|Le processus de fenêtre source s'exécute sur le curseur.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
|Menu contextuel de la fenêtre**Processus** :<br /><br /> -   **Arrêter le processus**|N\/A|Le processus sélectionné s'interrompt.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
|Menu contextuel de la fenêtre**Processus** :<br /><br /> -   **Continuer le processus**|N\/A|Le processus sélectionné reprend.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Basculer les processus, arrêter et poursuivre l'exécution, accéder à la source](../debugger/debug-multiple-processes.md#BKMK_Switch_processes__break_and_continue_execution__step_through_source)  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
##  <a name="BKMK_Stop_debugging__terminate_or_detach_from_processes"></a> Arrêter le débogage, le terminer ou le détacher des processus  
  
-   [Commandes Arrêter, Terminer et Détacher](#BKMK_Stop__terminate__and_detach_commands)  
  
 Par défaut, lorsque vous choisissez **Déboguer**, **Arrêter le débogage** lorsque plusieurs processus sont ouverts dans le débogueur, le débogueur se termine ou se détache de tous les processus selon la façon dont le processus a été ouvert dans le débogueur :  
  
-   Si le processus actuel a été lancé dans le débogueur, ce processus serait terminé.  
  
-   Si vous avez attaché le débogueur au processus actuel, le débogueur se détache du processus et le conserve.  
  
 Par exemple, si vous commencez à déboguer un processus à partir d'une solution Visual Studio, effectuez un attachement à un autre processus qui s'exécute déjà, puis choisissez **Arrêter le débogage**, la session de débogage se termine, le processus qui a été démarré dans Visual Studio est terminé, tandis que le processus que vous avez attaché est autorisé à s'exécuter.  Vous pouvez utiliser les procédures suivantes pour contrôler la façon dont vous arrêtez le débogage.  
  
> [!NOTE]
>  L'option **Arrêter tous les processus lorsqu'un processus s'arrête** n'affecte pas l'arrêt du débogage ou l'arrêt et le détachement des processus.  
  
 **Pour modifier la façon dont l'arrêt du débogage affecte un processus individuel**  
  
-   Ouvrez la fenêtre **Processus** \(raccourci **Ctrl\+Alt\+Z**\).  Sélectionnez un processus puis activez ou désactivez la case à cocher **Détacher lorsque le débogage est arrêté**.  
  
###  <a name="BKMK_Stop__terminate__and_detach_commands"></a> Commandes Arrêter, Terminer et Détacher  
  
|||  
|-|-|  
|**Commande**|**Description**|  
|Menu**Déboguer** :<br /><br /> -   **Arrêter le débogage**|Sauf si le comportement est modifié par l'option **Détacher lorsque le débogage est arrêté** dans la fenêtre **Processus** :<br /><br /> 1.  Les processus démarrés par le débogueur sont terminés.<br />2.  Les processus attachés sont détachés du débogueur.|  
|Menu**Déboguer** :<br /><br /> -   **Tout arrêter**|Tous les processus sont terminés.|  
|Menu**Déboguer** :<br /><br /> -   **Détacher tout**|Le débogueur se détache de tous les processus.|  
|Menu contextuel de la fenêtre**Processus** :<br /><br /> -   **Détacher le processus**|Le débogueur se détache du processus sélectionné.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
|Menu contextuel de la fenêtre**Processus** :<br /><br /> -   **Terminer le processus**|Le processus sélectionné est terminé.<br /><br /> D'autres processus conservent leur état existant \(Suspendu ou En cours d'exécution\).|  
|Menu contextuel de la fenêtre**Processus** :<br /><br /> -   **Détacher lorsque le débogage s'arrête**|Bascule le comportement de **Déboguer**, **Arrêter le débogage** pour le processus sélectionné :<br /><br /> -   Activé : le débogueur se détache du processus sélectionné.<br />-   Effacé : le processus est terminé.|  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Arrêter le débogage, le terminer ou le détacher des processus](../debugger/debug-multiple-processes.md#BKMK_Stop_debugging__terminate_or_detach_from_processes)  
  
 ![Retour au début](~/docs/debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Sommaire](#BKMK_Contents)  
  
## Voir aussi  
 [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md)   
 [Débogage juste\-à\-temps](../debugger/just-in-time-debugging-in-visual-studio.md)   
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)