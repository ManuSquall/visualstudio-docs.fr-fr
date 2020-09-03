---
title: Exécuter des applications du Windows Store sur l’ordinateur local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196324"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Exécuter des applications du Windows Store sur un ordinateur local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows uniquement] (.. /Image/windows_only_content.png « windows_only_content »)  
  
 Pour déboguer, tester ou exécuter l'analyse des performances d'une application du Windows Store, vous pouvez exécuter l'application sur le même ordinateur que celui qui héberge Visual Studio. Si l'appareil dispose d'un écran tactile, vous pouvez tester l'ensemble des fonctionnalités de l'application ; sinon, vous devrez vous contenter du clavier et des mouvements de la souris.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Dans cette rubrique  
 Vous pouvez apprendre :  
  
 [Comment exécuter sur un ordinateur local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Comment basculer entre une application du Windows Store et Visual Studio sur un même écran](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Comment exécuter sur un ordinateur local  
 Pour exécuter l’application sur l’ordinateur local, sélectionnez **ordinateur local** dans la liste déroulante en regard du bouton Démarrer le débogage de la barre d’outils **standard** du débogueur.  
  
 ![Exécution sur l'ordinateur local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Si vous ne voyez pas la barre d’outils **standard** , cliquez sur le menu **affichage** , pointez sur **barres d’outils**, puis cliquez sur **standard**.  
  
 Le choix que vous effectuez dans la liste déroulante est conservé dans le fichier des propriétés du projet et devient la cible d'exécution par défaut.  
  
 Vous pouvez aussi définir directement la cible d'exécution dans le fichier des propriétés du projet. Dans **Explorateur de solutions** , cliquez avec le bouton droit sur le nom du projet, puis choisissez **Propriétés**. Ensuite, effectuez l’une des actions suivantes :  
  
- Dans les projets C# et Visual Basic, cliquez sur **Déboguer** , puis sélectionnez **ordinateur local** dans la liste déroulante **périphérique cible** .  
  
     ![Page de propriétés du projet C&#35; et Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- Dans les projets C++ et JavaScript, développez le nœud **Propriétés de configuration** , cliquez sur **débogage**, puis sélectionnez **débogueur local** dans la liste **débogueur à lancer** .  
  
     ![Page de propriétés du projet C&#43;&#43; et JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Guide pratique pour basculer entre une application du Windows Store et Visual Studio sur une seule analyse  
 **Pour basculer d'une instance en cours d'exécution d'une application du Windows Store vers Visual Studio**  
  
 Lorsque vous exécutez une application du Windows Store sur un ordinateur local et n'utilisez qu'un seul moniteur, il se peut que vous souhaitiez revenir vers Visual Studio lorsque vous quittez l'application. Par exemple, l'application peut se trouver dans un état qui ne peut pas être atteint par un point d'arrêt, comme l'attente d'un événement ou la prise au piège dans une boucle longue ou infinie. Pour revenir dans Visual Studio, appuyez sur ALT + TAB.
