---
title: 'Comment : attacher à un Script | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- script debugging, attaching to script
- script, attaching to
- processes, attaching to script
- remote debugging, attaching to script
ms.assetid: 82013e9a-ef53-4fd2-b451-a6891cdc6307
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c38e965c5d424c7a3a6ffe4047e9422f1f9bb4f0
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="how-to-attach-to-script"></a>Comment : attacher à un script
Cette rubrique explique comment attacher manuellement le débogueur Visual Studio à un fichier de script pour le débogage.  
  
### <a name="to-attach-to-a-running-process"></a>Pour établir un attachement à un processus en cours d'exécution  
  
1.  Dans le menu **Débogage** , sélectionnez **Attacher au processus**. (Si aucun projet n’est ouvert, choisissez **attacher au processus** sur la **outils** menu.)  
  
2.  Dans le **attacher au processus** boîte de dialogue, examinez le **processus disponibles** liste et rechercher le processus de script vous voulez attacher. Vous pouvez identifier les processus de script en examinant le **Type** colonne.  
  
    1.  Si le processus que vous souhaitez déboguer est en cours d'exécution sur un autre ordinateur, sélectionnez d'abord l'ordinateur distant. Pour plus d’informations, consultez [Comment : sélectionner un ordinateur distant](http://msdn.microsoft.com/en-us/4332ba8e-2f0b-4f62-b96a-e762b9f3c3ba).  
  
    2.  Si le processus s’exécute sous un compte d’utilisateur différent, cochez la case **Afficher les processus de tous les utilisateurs** .  
  
    3.  Si vous êtes connecté via **connexion Bureau à distance**, sélectionnez le **afficher les processus de toutes les sessions** case à cocher.  
  
3.  Cliquez sur le processus que vous voulez attacher.  
  
4.  Dans le **attacher à** zone, vous devez voir **code de Script** ou **automatique : code de Script**. Si un élément différent est affiché, suivez ces étapes :  
  
    1.  Cliquez sur **Sélectionner**.  
  
    2.  Dans le **sélectionner le Type de Code** boîte de dialogue, cliquez sur **déboguer ces types de codes** et sélectionnez **Script**.  
  
    3.  Cliquez sur **OK**.  
  
5.  Cliquez sur **Attacher**.  
  
     Vous pouvez visualiser un avertissement vous indiquant que le débogage de script est désactivé dans Internet Explorer. Si cela se produit, consultez [Avertissement : le débogage de Script est désactivé](../debugger/warning-script-debugging-disabled.md).  
  
 La liste **Processus disponibles** s’affiche automatiquement quand vous ouvrez la boîte de dialogue **Processus** . Les processus peuvent démarrer et s’interrompre en arrière-plan pendant que la boîte de dialogue est ouverte. Le contenu n'est donc pas toujours à jour. Vous pouvez actualiser la liste à tout moment pour afficher la liste actuelle des processus en appuyant sur la **Actualiser** bouton.  
  
 Vous pouvez attacher un débogueur à plusieurs programmes à la fois, mais un seul d’entre eux est actif dans le débogueur à un moment donné. Vous pouvez définir le programme actif dans la barre d'outils Emplacement de débogage. Pour plus d’informations, consultez [Comment : définir le processus actuel](http://msdn.microsoft.com/en-us/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).  
  
 Tous les **déboguer** commandes de menu d’exécution affectent le programme actif. Vous pouvez interrompre tout programme débogué à partir de la boîte de dialogue processus. Consultez [à l’aide de points d’arrêt](../debugger/using-breakpoints.md).  
  
> [!NOTE]
>  Si vous essayez d'établir un attachement à un processus appartenant à un compte d'utilisateur non fiable, une boîte de dialogue d'avertissement de sécurité s'affiche avec un message de confirmation. Pour plus d’informations, consultez [avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations ci-dessous semblent suspectes ou si vous n’êtes pas sûr, n’attachez pas ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md).  
  
 Dans certains cas, lors du débogage dans une session Terminal Services (Bureau à distance), la liste Processus disponibles n'affiche pas tous les processus disponibles. Dans [!INCLUDE[WinXPSvr](../debugger/includes/winxpsvr_md.md)] ou une version ultérieure, si vous exécutez Visual Studio avec un compte d'utilisateur limité, la liste Processus disponibles n'affiche pas les processus qui s'exécutent dans la session 0, qui est utilisée pour les services et les autres processus serveur, notamment w3wp.exe. Vous pouvez résoudre le problème en exécutant Visual Studio sous un compte administrateur ou à partir de la console serveur au lieu d'une session Terminal Services. Si aucune de ces solutions n’est possible, une troisième option consiste à attacher au processus en entrant vsjitdebugger.exe ProcessId -p à la ligne de commande Windows. Vous pouvez déterminer l'ID de processus à l'aide de tlist.exe. Pour obtenir tlist.exe, téléchargez et installez les outils de débogage pour Windows, disponible à l’adresse [Windows Hardware Developer Central](http://go.microsoft.com/fwlink/?linkid=1651).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage de Script côté client](../debugger/client-side-script-debugging.md)   
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Avertissement de sécurité : L’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations ci-dessous semblent suspectes ou si vous n’êtes pas sûr, n’attachez pas ce processus](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)