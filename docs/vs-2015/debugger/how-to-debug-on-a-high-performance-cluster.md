---
title: 'Procédure : Déboguer sur un Cluster hautement performant | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702690"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Procédure : déboguer sur un cluster à hautes performances
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage d'un programme multitraitement sur un cluster hautement performant est identique au débogage d'un programme ordinaire sur un ordinateur distant. Il y a toutefois d'autres éléments à prendre en compte. Pour les besoins généraux de configuration à distance, consultez [le débogage à distance](../debugger/remote-debugging.md).  
  
 Lorsque vous déboguez sur un cluster hautement performant, vous pouvez utiliser toutes les fenêtres de débogage et les techniques [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] disponibles pour le débogage distant. Cependant, puisque vous déboguez à distance, la fenêtre de console externe n'est pas disponible.  
  
 Les fenêtres **Threads** et **Processus** sont particulièrement utiles pour déboguer des applications parallèles. Pour obtenir des conseils sur l’utilisation de ces fenêtres, consultez [Comment : Utiliser la fenêtre processus](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) et [Comment : Utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).  
  
 Les procédures suivantes présentent quelques techniques particulièrement utiles pour le débogage sur un cluster hautement performant.  
  
 Lors du débogage d'une application parallèle, vous souhaitez définir un point d'arrêt sur un thread, un processus ou un ordinateur particulier. Pour ce faire, vous pouvez créer un point d'arrêt normal, puis ajouter un filtre de point d'arrêt.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Pour ouvrir la boîte de dialogue Filtre de point d'arrêt  
  
1. Cliquez avec le bouton droit sur un glyphe de point d’arrêt dans une fenêtre source, la fenêtre **Code machine**, **Pile des appels** ou **Points d’arrêt**.  
  
2. Dans le menu contextuel, cliquez sur **Filtre**. Cette option peut s’afficher en haut ou dans le sous-menu sous **Points d’arrêt**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Pour définir un point d'arrêt sur un ordinateur spécifique  
  
1. Obtenez le nom de l’ordinateur dans la fenêtre **Processus**.  
  
2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la procédure précédente.  
  
3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :  
  
     MachineName =*nom_de_votre_ordinateur*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4. Cliquez sur **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Pour définir un point d'arrêt sur un processus spécifique  
  
1. Obtenez le nom du processus ou le numéro d’identifiant du processus de la fenêtre **Processus**.  
  
2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la première procédure.  
  
3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :  
  
     `ProcessName =`  *nom_de_votre_processeur*  
  
     - ou -  
  
     `ProcessID =` *ID_de_votre_processeur*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4. Cliquez sur **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Pour définir un point d'arrêt sur un thread spécifique  
  
1. Obtenez le nom du thread ou le numéro d’ID de thread dans la fenêtre **Threads**.  
  
2. Sélectionnez un point d’arrêt et ouvrez la boîte de dialogue **Filtre de point d’arrêt**, comme décrit dans la première procédure.  
  
3. Dans la boîte de dialogue **Filtre de point d’arrêt**, tapez :  
  
     `ThreadName =` *nom_de_votre_thread*  
  
     - ou -  
  
     `ThreadID =` *ID_de_votre_thread*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4. Cliquez sur **OK**.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment créer un filtre pour un point d'arrêt sur un ordinateur nommé `marvin` et un thread nommé `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage distant](../debugger/remote-debugging.md)   
 [Guide pratique pour Utiliser la fenêtre processus](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Guide pratique pour Utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads et processus](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Utilisation des points d’arrêt](../debugger/using-breakpoints.md)
