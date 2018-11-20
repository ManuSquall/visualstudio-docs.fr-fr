---
title: 'Erreur : Le débogage n’est pas&#39;t Possible car un débogueur du noyau est activé sur le système | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea2e7d8277bc67df75be3d05d907a8bd13c29c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725287"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Erreur : Le débogage n’est pas&#39;t Possible car un débogueur du noyau est activé sur le système
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous déboguez du code managé, le message d'erreur suivant peut s'afficher :  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Ce message se produit lorsque vous essayez de déboguer du code managé :  
  
-   sur un système [!INCLUDE[win7](../includes/win7-md.md)] ou [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]qui a été démarré en mode débogage.  
  
-   l'application utilise la version CLR CLR 2.0, 3.0, ou 3.5.  
  
## <a name="solution"></a>Solution  
  
#### <a name="to-fix-this-problem"></a>Pour corriger ce problème  
  
-   Mettez votre application à niveau pour utiliser la version CLR 4.0 ou 4.5  
  
     - ou -  
  
-   Désactivez le débogage du noyau et déboguez dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     - ou -  
  
-   Déboguez à l'aide du débogueur du noyau au lieu de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     - ou -  
  
-   Dans le débogueur du noyau, désactivez les exceptions en mode utilisateur.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Pour désactiver le débogage du noyau dans la session active  
  
-   À l'invite de commandes, tapez :  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Pour désactiver le débogage du noyau pour toutes les sessions (Windows Vista et Windows 7)  
  
1.  À l'invite de commandes, tapez :  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Redémarrez l'ordinateur.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Pour désactiver le débogage du noyau pour toutes les sessions (systèmes d'exploitation autres que Windows)  
  
1.  Recherchez le fichier boot.ini sur votre lecteur système (généralement C:\\). Le fichier boot.ini peut être masqué et en lecture seule. Par conséquent, vous devez utiliser la commande suivante pour l'afficher :  
  
    ```  
    dir /ASH  
    ```  
  
2.  Ouvrez boot.ini en utilisant le Bloc-notes et supprimez les options suivantes :  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Redémarrez l'ordinateur.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Pour déboguer avec le débogueur du noyau  
  
1.  Si le débogueur du noyau est raccordé, un message s'affiche pour demander si vous souhaitez continuer le débogage. Cliquez sur le bouton pour continuer.  
  
2.  Vous pouvez obtenir une `User break exception(Int 3).`. Dans ce cas, entrez la commande du débogueur du noyau suivante pour poursuivre le débogage :  
  
     `gn`  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité du débogueur](../debugger/debugger-security.md)   
 [Débogage du code managé](../debugger/debugging-managed-code.md)



