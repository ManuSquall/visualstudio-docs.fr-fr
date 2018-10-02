---
title: 'Comment : déboguer sur un Cluster hautement performant | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce148ab317b14aad6cd1e2c48a6f9245c81df98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506230"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Comment : déboguer sur un cluster hautement performant
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : déboguer sur un Cluster hautement performant](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-on-a-high-performance-cluster).  
  
Le débogage d'un programme multitraitement sur un cluster hautement performant est identique au débogage d'un programme ordinaire sur un ordinateur distant. Il y a toutefois d'autres éléments à prendre en compte. Pour les besoins généraux de configuration à distance, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
 Lorsque vous déboguez sur un cluster hautement performant, vous pouvez utiliser toutes les fenêtres de débogage et les techniques [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] disponibles pour le débogage distant. Cependant, puisque vous déboguez à distance, la fenêtre de console externe n'est pas disponible.  
  
 Le **Threads** fenêtre et **processus** sont particulièrement utiles pour déboguer des applications parallèles. Pour obtenir des conseils sur l’utilisation de ces fenêtres, consultez [Comment : utiliser la fenêtre processus](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) et [Comment : utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).  
  
 Les procédures suivantes présentent quelques techniques particulièrement utiles pour le débogage sur un cluster hautement performant.  
  
 Lors du débogage d'une application parallèle, vous souhaitez définir un point d'arrêt sur un thread, un processus ou un ordinateur particulier. Pour ce faire, vous pouvez créer un point d'arrêt normal, puis ajouter un filtre de point d'arrêt.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Pour ouvrir la boîte de dialogue Filtre de point d'arrêt  
  
1.  Avec le bouton droit à un glyphe de point d’arrêt dans une fenêtre source, le **désassemblage** fenêtre, le **pile des appels** fenêtre, ou le **des points d’arrêt** fenêtre.  
  
2.  Dans le menu contextuel, cliquez sur **filtre**. Cette option peut s’afficher en haut ou dans le sous-menu sous **des points d’arrêt**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Pour définir un point d'arrêt sur un ordinateur spécifique  
  
1.  Obtenir le nom d’ordinateur à partir de la **processus** fenêtre.  
  
2.  Sélectionnez un point d’arrêt et ouvrez le **filtre de point d’arrêt** boîte de dialogue, comme décrit dans la procédure précédente.  
  
3.  Dans le **filtre de point d’arrêt** boîte de dialogue, tapez :  
  
     MachineName =*nomdevotremachine*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Pour définir un point d'arrêt sur un processus spécifique  
  
1.  Obtenir le nom du processus ou le numéro d’ID à partir de processus la **processus** fenêtre.  
  
2.  Sélectionnez un point d’arrêt et ouvrez le **filtre de point d’arrêt** boîte de dialogue comme dans la première procédure.  
  
3.  Dans le **filtre de point d’arrêt** boîte de dialogue, tapez :  
  
     `ProcessName =`  *yourprocessname*  
  
     - ou -  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Pour définir un point d'arrêt sur un thread spécifique  
  
1.  Obtenir le nom de thread ou le numéro d’ID à partir de thread la **Threads** fenêtre.  
  
2.  Sélectionnez un point d’arrêt et ouvrez le **filtre de point d’arrêt** boîte de dialogue, comme décrit dans la première procédure.  
  
3.  Dans le **filtre de point d’arrêt** boîte de dialogue, tapez :  
  
     `ThreadName =` *yourthreadname*  
  
     - ou -  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un filtre pour un point d'arrêt sur un ordinateur nommé `marvin` et un thread nommé `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les Applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage à distance](../debugger/remote-debugging.md)   
 [Comment : utiliser la fenêtre processus](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Comment : utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads et processus](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)



