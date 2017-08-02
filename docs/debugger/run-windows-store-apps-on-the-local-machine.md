---
title: "Ex&#233;cuter des applications du Windows&#160;Store sur un ordinateur local | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Ex&#233;cuter des applications du Windows&#160;Store sur un ordinateur local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![S'applique uniquement à Windows](~/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Pour déboguer, tester ou exécuter l'analyse des performances d'une application du Windows Store, vous pouvez exécuter l'application sur le même ordinateur que celui qui héberge Visual Studio.  Si l'appareil dispose d'un écran tactile, vous pouvez tester l'ensemble des fonctionnalités de l'application ; sinon, vous devrez vous contenter du clavier et des mouvements de la souris.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Vous pouvez apprendre :  
  
 [Comment exécuter sur un ordinateur local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Comment basculer entre une application du Windows Store et Visual Studio sur un même écran](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Comment exécuter sur un ordinateur local  
 Pour exécuter l'application sur l'ordinateur local, sélectionnez **Ordinateur local** dans la liste déroulante située en regard du bouton Démarrer le débogage dans la barre d'outils **Standard** de Visual Studio.  
  
 ![Exécution sur l'ordinateur local](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
 Si la barre d'outils **Standard** n'apparaît pas, cliquez sur le menu **Affichage**, pointez sur **Barres d'outils**, puis cliquez sur **Standard**.  
  
 Le choix que vous effectuez dans la liste déroulante est conservé dans le fichier des propriétés du projet et devient la cible d'exécution par défaut.  
  
 Vous pouvez aussi définir directement la cible d'exécution dans le fichier des propriétés du projet.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le nom du projet, puis choisissez **Propriétés**.  Effectuez ensuite l'une des opérations suivantes :  
  
-   Dans les projets C\# et Visual Basic, cliquez sur **Déboguer**, puis sélectionnez **Ordinateur local** dans la liste déroulante **Périphérique cible**.  
  
     ![Page de propriétés du projet C&#35; et Visual Basic](~/debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN\_CS\_VB\_ProjProp\_Local")  
  
-   Dans les projets C\+\+ et JavaScript, développez le nœud **Propriétés de configuration**, cliquez sur **Débogage**, puis sélectionnez **Débogueur local** dans la liste **Débogueur à lancer**.  
  
     ![Page de propriétés du projet C&#43;&#43; et JavaScript](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN\_CPP\_JS\_ProjProp\_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Comment basculer entre une application du Windows Store et Visual Studio sur un même écran  
 **Pour basculer d'une instance en cours d'exécution d'une application du Windows Store vers Visual Studio**  
  
 Lorsque vous exécutez une application du Windows Store sur un ordinateur local et n'utilisez qu'un seul moniteur, il se peut que vous souhaitiez revenir vers Visual Studio lorsque vous quittez l'application.  Par exemple, l'application peut se trouver dans un état qui ne peut pas être atteint par un point d'arrêt, comme l'attente d'un événement ou la prise au piège dans une boucle longue ou infinie.  Pour revenir dans Visual Studio, appuyez sur ALT \+ TAB.