---
title: Une erreur DCOM s’est produite lors de la tentative de contact de l’ordinateur distant. Accès refusé. | Microsoft Docs
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
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 95c9abfbba2eb1e5c3e107440f0988b1002c1386
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215798"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Une erreur DCOM s’est produite lors de la tentative de contact de l’ordinateur distant. Accès refusé.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogage distant utilise DCOM pour les communications entre l’ordinateur hôte et l’ordinateur distant dans les situations suivantes :  
  
-   Le débogueur est défini sur **Mode de compatibilité natif** ou l’option **Mode de compatibilité managé** est activée dans la page **Outils/Options/Débogage** .  
  
-   Vous déboguez du code C++ managé (C++/CLI).  
  
-   Dans Visual Studio 2013, l’option **Activer Modifier &amp; Continuer natif** est activée dans la page **Outils/Options/Débogage** .  
  
-   Quelques scénarios de débogage tiers  
  
 Cette erreur se produit lorsque le processus Visual Studio ne peut pas s'authentifier (ou que les informations d'identification fournies ont été considérées inappropriées) lors du processus du débogueur distant sur DCOM. Une ou plusieurs des solutions suivantes peuvent résoudre le problème :  
  
-   Désactivez  **Mode de compatibilité natif** et **Mode de compatibilité managé**.  
  
-   Dans Visual Studio 2013, désactivez **Activer Modifier &amp; Continuer natif**.  
  
-   Redémarrez les deux ordinateurs.  
  
-   Si le débogage distant requiert la saisie des informations d'identification, activez l'option pour enregistrer les informations d'identification.  
  
## <a name="see-also"></a>Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



