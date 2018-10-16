---
title: Applications d’exécution Windows Store sur l’ordinateur local | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b460d1eecfe96cddce27926ee8e31aae258d8dcf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188381"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Exécuter des applications du Windows Store sur un ordinateur local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique uniquement à Windows] (.. /Image/windows_only_content.png « windows_only_content »)  
  
 Pour déboguer, tester ou exécuter l'analyse des performances d'une application du Windows Store, vous pouvez exécuter l'application sur le même ordinateur que celui qui héberge Visual Studio. Si l'appareil dispose d'un écran tactile, vous pouvez tester l'ensemble des fonctionnalités de l'application ; sinon, vous devrez vous contenter du clavier et des mouvements de la souris.  
  
##  <a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Vous pouvez apprendre :  
  
 [Comment exécuter sur un ordinateur local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Comment basculer entre une application du Windows Store et de Visual Studio sur un même écran](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Comment exécuter sur un ordinateur local  
 Pour exécuter l’application sur l’ordinateur local, sélectionnez **ordinateur Local** dans la liste déroulante en regard du bouton Démarrer le débogage sur le débogueur **Standard** barre d’outils.  
  
 ![Exécuter sur l’ordinateur Local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Si vous ne voyez pas le **Standard** barre d’outils, cliquez sur le **vue** menu, pointez sur **barres d’outils**, puis cliquez sur **Standard**.  
  
 Le choix que vous effectuez dans la liste déroulante est conservé dans le fichier des propriétés du projet et devient la cible d’exécution par défaut.  
  
 Vous pouvez aussi définir directement la cible d'exécution dans le fichier des propriétés du projet. Cliquez sur le nom de projet dans **l’Explorateur de solutions** , puis **propriétés**. Effectuez ensuite l'une des opérations suivantes :  
  
-   Dans les projets c# et Visual Basic, cliquez sur **déboguer** , puis sélectionnez **ordinateur Local** à partir de la **appareil cible** liste déroulante.  
  
     ![C&#35; et page de propriétés de projet Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   Dans les projets C++ et JavaScript, développez le **propriétés de Configuration** nœud, cliquez sur **débogage**, puis sélectionnez **débogueur Local** à partir de la **débogueur Pour lancer** liste.  
  
     ![C&#43; &#43; et page de propriétés de projet JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Comment basculer entre une application du Windows Store et de Visual Studio sur un même écran  
 **Pour passer d’une instance en cours d’exécution d’une application Windows Store à Visual Studio**  
  
 Lorsque vous exécutez une application du Windows Store sur un ordinateur local et n'utilisez qu'un seul moniteur, il se peut que vous souhaitiez revenir vers Visual Studio lorsque vous quittez l'application. Par exemple, l'application peut se trouver dans un état qui ne peut pas être atteint par un point d'arrêt, comme l'attente d'un événement ou la prise au piège dans une boucle longue ou infinie. Pour revenir dans Visual Studio, appuyez sur ALT + TAB.



