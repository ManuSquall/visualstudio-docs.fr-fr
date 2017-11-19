---
title: "Exécuter les applications UWP sur l’ordinateur local | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Exécuter les applications UWP sur l’ordinateur local
![S’applique uniquement à Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Pour déboguer, tester ou exécuter l’analyse de performances sur une application UWP, vous pouvez exécuter l’application sur le même ordinateur qui héberge Visual Studio. Si l'appareil dispose d'un écran tactile, vous pouvez tester l'ensemble des fonctionnalités de l'application ; sinon, vous devrez vous contenter du clavier et des mouvements de la souris.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Comment exécuter sur un ordinateur local  
 Pour exécuter l’application sur l’ordinateur local, sélectionnez **ordinateur Local** dans la liste déroulante en regard du bouton Démarrer le débogage du débogueur **Standard** barre d’outils.  
  
 ![Exécuter sur l’ordinateur Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Si vous ne voyez pas le **Standard** barre d’outils, cliquez sur le **vue** menu, pointez sur **barres d’outils**, puis cliquez sur **Standard**.  
  
 Le choix que vous effectuez dans la liste déroulante est conservé dans le fichier des propriétés du projet et devient la cible d’exécution par défaut.  
  
 Vous pouvez aussi définir directement la cible d'exécution dans le fichier des propriétés du projet. Cliquez sur le nom du projet dans **l’Explorateur de solutions** , puis **propriétés**. Effectuez ensuite l'une des opérations suivantes :  
  
-   Dans les projets c# et Visual Basic, cliquez sur **déboguer** , puis sélectionnez **ordinateur Local** à partir de la **appareil cible** liste déroulante.  
  
     ![C &#35; page de propriétés de projet Visual Basic et](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   Dans les projets C++ et JavaScript, développez le **propriétés de Configuration** nœud, cliquez sur **débogage**, puis sélectionnez **débogueur Local** à partir de la **débogueur Pour lancer** liste.  
  
     ![C &#43; &#43; page de propriétés projet JavaScript et](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  