---
title: "Comment&#160;: attacher &#224; un script | Microsoft Docs"
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
  - "processus, attacher à un script"
  - "débogage distant, attacher à un script"
  - "débogage de script, attacher à un script"
  - "script, attacher à"
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: attacher &#224; un script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette rubrique explique comment attacher manuellement le débogueur Visual Studio à un fichier de script pour le débogage.  
  
### Pour établir un attachement à un processus en cours d'exécution  
  
1.  Dans le menu **Débogage**, sélectionnez **Attacher au processus**. Si aucun projet n'est ouvert, cliquez sur **Attacher au processus** dans le menu **Outils**.  
  
2.  Dans la boîte de dialogue **Attacher au processus**, dans la liste **Processus disponibles** recherchez le processus de script à attacher.  Vous pouvez identifier les processus de script dans la colonne **Type**.  
  
    1.  Si le processus que vous souhaitez déboguer est en cours d'exécution sur un autre ordinateur, sélectionnez d'abord l'ordinateur distant.  Pour plus d'informations, consultez [How to: Select a Remote Computer](http://msdn.microsoft.com/fr-fr/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Si le processus s'exécute sous un compte d'utilisateur différent, activez la case à cocher **Afficher les processus de tous les utilisateurs**.  
  
    3.  Si vous êtes connecté via une **Connexion Bureau à distance** , activez la case à cocher **Afficher les processus de toutes les sessions**.  
  
3.  Cliquez sur le processus que vous voulez attacher.  
  
4.  Dans la zone **Attacher à**, **Code de script** ou **Automatique : Code de script** devrait s'afficher.  Si un élément différent est affiché, suivez ces étapes :  
  
    1.  Cliquez sur **Sélectionner**.  
  
    2.  Dans la boîte de dialogue **Sélectionner le type de code**, sous **Déboguer ces types de codes** et sélectionnez **Script**.  
  
    3.  Cliquez sur **OK**.  
  
5.  Cliquez sur **Attacher**.  
  
     Vous pouvez visualiser un avertissement vous indiquant que le débogage de script est désactivé dans Internet Explorer.  Dans ce cas, consultez [Avertissement : le débogage de script est désactivé](../debugger/warning-script-debugging-disabled.md).  
  
 La liste **Processus disponibles** s'affiche automatiquement lorsque vous ouvrez la boîte de dialogue **Processus**.  Les processus peuvent démarrer et s'interrompre en arrière\-plan pendant que la boîte de dialogue est ouverte.  Le contenu n'est donc pas toujours à jour.  Vous pouvez réactualiser la liste à tout moment pour afficher la liste des processus en cours en appuyant sur le bouton **Actualiser**.  
  
 Vous pouvez attacher un débogueur à plusieurs programmes à la fois, mais seul l'un d'entre eux est actif dans le débogueur à un moment donné.  Vous pouvez définir le programme actif dans la barre d'outils Emplacement de débogage.  Pour plus d'informations, consultez [How to: Set the Current Process](http://msdn.microsoft.com/fr-fr/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Toutes les commandes d'exécution du menu **Déboguer** affectent le programme actif.  Vous pouvez interrompre n'importe quel programme débogué à partir de la boîte de dialogue Processus. Voir [Utilisation des points d'arrêt](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si vous essayez d'établir un attachement à un processus appartenant à un compte d'utilisateur non fiable, une boîte de dialogue d'avertissement de sécurité s'affiche avec un message de confirmation.  Pour plus d'informations, consultez [Avertissement de sécurité : L'attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou en cas de doutes, n'attachez pas ce processus.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
 Dans certains cas, lors du débogage dans une session Terminal Services \(Bureau à distance\), la liste Processus disponibles n'affiche pas tous les processus disponibles.  Dans [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] ou une version ultérieure, si vous exécutez Visual Studio avec un compte d'utilisateur limité, la liste Processus disponibles n'affiche pas les processus qui s'exécutent dans la session 0, qui est utilisée pour les services et les autres processus serveur, notamment w3wp.exe.  Vous pouvez résoudre le problème en exécutant Visual Studio sous un compte administrateur ou à partir de la console serveur au lieu d'une session Terminal Services.  Si aucune de ces solutions n'est possible, la troisième option consiste à attacher le débogueur au processus en entrant vsjitdebugger.exe \-p ProcessId dans la ligne de commande Windows.  Vous pouvez déterminer l'ID de processus à l'aide de tlist.exe.  Pour obtenir tlist.exe, téléchargez et installez les outils de débogage pour Windows, qui sont disponibles dans [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651) \(page éventuellement en anglais\).  
  
## Voir aussi  
 [Débogage de scripts côté client](../debugger/client-side-script-debugging.md)   
 [Attacher aux processus en cours d'exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Avertissement de sécurité : L'attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations suivantes semblent suspectes ou en cas de doutes, n'attachez pas ce processus.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)