---
title: Le débogage &apos; n’est pas possible, car un débogueur du noyau est activé sur le système | Microsoft Docs
description: Ce message s’affiche lorsque vous essayez de déboguer du code managé sur un système Windows 7 ou Windows Vista qui a été démarré en mode débogage et que l’application utilise la version CLR 2,0, 3,0 ou 3,5.
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ced7fb79a11321678ae2963241807e5ddd4600ab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466457"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Erreur : le débogage n’est pas&#39;possible, car un débogueur du noyau est activé sur le système
Lorsque vous déboguez du code managé, le message d'erreur suivant peut s'afficher :

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Ce message se produit lorsque vous essayez de déboguer du code managé :

- sur un [!INCLUDE[win7](../debugger/includes/win7_md.md)] [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] système ou qui a été démarré en mode débogage.

- l'application utilise la version CLR CLR 2.0, 3.0, ou 3.5.

## <a name="solution"></a>Solution

#### <a name="to-fix-this-problem"></a>Pour corriger ce problème

- Mettez votre application à niveau pour utiliser la version CLR 4.0 ou 4.5

   Ou

- Désactivez le débogage du noyau et déboguez dans [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   Ou

- Déboguez à l'aide du débogueur du noyau au lieu de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   Ou

- Dans le débogueur du noyau, désactivez les exceptions en mode utilisateur.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Pour désactiver le débogage du noyau dans la session active

- À l’invite de commandes, tapez :

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Pour désactiver le débogage du noyau pour toutes les sessions (Windows Vista et Windows 7)

1. À l’invite de commandes, tapez :

    ```cmd
    bcdedit /debug off
    ```

2. Redémarrez l'ordinateur.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Pour désactiver le débogage du noyau pour toutes les sessions (systèmes d'exploitation autres que Windows)

1. Recherchez le fichier boot.ini sur votre lecteur système (généralement C:\\). Le fichier boot.ini peut être masqué et en lecture seule. Par conséquent, vous devez utiliser la commande suivante pour l'afficher :

    ```cmd
    dir /ASH
    ```

2. Ouvrez boot.ini en utilisant le Bloc-notes et supprimez les options suivantes :

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Redémarrez l'ordinateur.

#### <a name="to-debug-with-the-kernel-debugger"></a>Pour déboguer avec le débogueur du noyau

1. Si le débogueur du noyau est raccordé, un message s'affiche pour demander si vous souhaitez continuer le débogage. Cliquez sur le bouton pour continuer.

2. Vous pouvez obtenir une `User break exception(Int 3).`. Dans ce cas, entrez la commande du débogueur du noyau suivante pour poursuivre le débogage :

     `gn`

## <a name="see-also"></a>Voir aussi
- [Sécurité du débogueur](../debugger/debugger-security.md)
- [Débogage du code managé](../debugger/debugging-managed-code.md)
