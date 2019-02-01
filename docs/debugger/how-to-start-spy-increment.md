---
title: 'Procédure : Démarrer Spy ++ | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e16c5d540aa59ae0c5d56ccb311618ab311bd9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993455"
---
# <a name="how-to-start-spy"></a>Procédure : Démarrer Spy++

Vous pouvez démarrer Spy ++ à partir de Visual Studio ou à une invite de commandes.  
  
 Lorsque vous démarrez Spy ++, si un message s’affiche pour demander l’autorisation d’apporter des modifications à l’ordinateur, sélectionnez **Oui**.  
  
> [!NOTE]
>  Vous pouvez exécuter qu’une seule instance de Spy ++. Si vous essayez de démarrer une deuxième instance, en fait l’instance en cours d’exécution obtenir le focus.

## <a name="prerequisites"></a>Prérequis

Spy ++ requiert les composants suivants. Vous pouvez sélectionner ces composants à partir de Visual Studio Installer en sélectionnant le **composants individuels** onglet, puis en sélectionnant les composants suivants.

* Sous débogage et test, sélectionnez **outils de profilage C++**
* Sous les activités de développement, sélectionnez **les fonctionnalités de base C++ de Visual Studio**

Si vous apporté des modifications, suivez les invites pour installer ces composants.
  
## <a name="start-spy-from-visual-studio"></a>Démarrer Spy ++ à partir de Visual Studio
  
Sur le **outils** menu, sélectionnez **Spy ++**.  
  
Étant donné que Spy ++ s’exécute indépendamment, après le démarrage, vous pouvez fermer Visual Studio.  
  
> [!NOTE]
>  Si vous consignez des messages avec Spy ++, il peut entraîner le système d’exploitation exécute plus lentement.  
  
## <a name="start-spy-at-a-command-prompt"></a>Démarrer Spy ++ à une invite de commandes  
  
1.  Dans une fenêtre d’invite de commandes, accédez au dossier qui contient spyxx.exe. En règle générale, le chemin d’accès à ce dossier est... \\ *Dossier d’installation de visual Studio*\Common7\Tools\\.  
  
2.  Entrez **spyxx.exe**. 
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Spy++](../debugger/using-spy-increment.md)   
 [Vues Spy++](../debugger/spy-increment-views.md)   
 [Informations de référence sur Spy++](../debugger/spy-increment-reference.md)