---
title: "Comment&#160;: d&#233;boguer sur un cluster hautement performant | Microsoft Docs"
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
helpviewer_keywords: 
  - "débogage de cluster"
  - "débogage haute performance"
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Comment&#160;: d&#233;boguer sur un cluster hautement performant
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogage d'un programme multitraitement sur un cluster hautement performant est identique au débogage d'un programme ordinaire sur un ordinateur distant.  Il y a toutefois d'autres éléments à prendre en compte.  Pour plus d'informations sur les besoins généraux de configuration distante, consultez [Débogage distant](../debugger/remote-debugging.md).  
  
 Lorsque vous déboguez sur un cluster hautement performant, vous pouvez utiliser toutes les fenêtres de débogage et les techniques [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] disponibles pour le débogage distant.  Cependant, puisque vous déboguez à distance, la fenêtre de console externe n'est pas disponible.  
  
 Les fenêtres **Threads** et **Processus** sont particulièrement utiles pour déboguer des applications parallèles.  Pour obtenir des conseils sur l'utilisation de ces fenêtres, consultez [How to: Use the Processes Window](http://msdn.microsoft.com/fr-fr/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) et [Comment : utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md).  
  
 Les procédures suivantes présentent quelques techniques particulièrement utiles pour le débogage sur un cluster hautement performant.  
  
 Lors du débogage d'une application parallèle, vous souhaitez définir un point d'arrêt sur un thread, un processus ou un ordinateur particulier.  Pour ce faire, vous pouvez créer un point d'arrêt normal, puis ajouter un filtre de point d'arrêt.  
  
### Pour ouvrir la boîte de dialogue Filtre de point d'arrêt  
  
1.  Cliquez avec le bouton droit sur un glyphe de point d'arrêt dans une fenêtre source, la fenêtre **Code machine**, **Pile des appels** ou **Points d'arrêt**.  
  
2.  Dans le menu contextuel, cliquez sur **Filtre**.  Cette option peut s'afficher en haut ou dans le sous\-menu sous **Points d'arrêt**.  
  
### Pour définir un point d'arrêt sur un ordinateur spécifique  
  
1.  Obtenez le nom de l'ordinateur dans la fenêtre **Processus**.  
  
2.  Sélectionnez un point d'arrêt et ouvrez la boîte de dialogue **Filtre de point d'arrêt**, comme décrit dans la procédure précédente.  
  
3.  Dans la boîte de dialogue **Filtre de point d'arrêt**, tapez :  
  
     MachineName \=*nom\_de\_votre\_ordinateur*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
### Pour définir un point d'arrêt sur un processus spécifique  
  
1.  Obtenez le nom du processus ou le numéro d'identifiant du processus de la fenêtre **Processus**.  
  
2.  Sélectionnez un point d'arrêt et ouvrez la boîte de dialogue **Filtre de point d'arrêt**, comme décrit dans la première procédure.  
  
3.  Dans la boîte de dialogue **Filtre de point d'arrêt**, tapez :  
  
     `ProcessName =`  *nom\_de\_votre\_processeur*  
  
     \- ou \-  
  
     `ProcessID =` *ID\_de\_votre\_processeur*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
### Pour définir un point d'arrêt sur un thread spécifique  
  
1.  Obtenez le nom du thread ou le numéro d'ID de thread dans la fenêtre **Threads**.  
  
2.  Sélectionnez un point d'arrêt et ouvrez la boîte de dialogue **Filtre de point d'arrêt**, comme décrit dans la première procédure.  
  
3.  Dans la boîte de dialogue **Filtre de point d'arrêt**, tapez :  
  
     `ThreadName =` *nom\_de\_votre\_thread*  
  
     \- ou \-  
  
     `ThreadID =` *ID\_de\_votre\_thread*  
  
     Pour créer un filtre plus complexe, vous pouvez associer des clauses à l'aide de `&`, de l'opérateur AND, `||`, de l'opérateur OR `!`, de l'opérateur NOT et de parenthèses.  
  
4.  Cliquez sur **OK**.  
  
## Exemple  
 L'exemple suivant montre comment créer un filtre pour un point d'arrêt sur un ordinateur nommé `marvin` et un thread nommé `fourier1`.  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## Voir aussi  
 [Déboguer les applications multithread](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Débogage distant](../debugger/remote-debugging.md)   
 [How to: Use the Processes Window](http://msdn.microsoft.com/fr-fr/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Comment : utiliser la fenêtre Threads](../debugger/how-to-use-the-threads-window.md)   
 [Threads and Processes](http://msdn.microsoft.com/fr-fr/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Utilisation des points d'arrêt](../debugger/using-breakpoints.md)