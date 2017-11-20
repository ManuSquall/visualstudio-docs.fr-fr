---
title: "Erreur : RPC requiert une authentification | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3431ee286787d99e8601fbed7cad3012ffcaf68e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Exécutez `\` *windir*`\system32\regedt32.exe`  
  
2.  Recherchez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4.  Si le problème persiste, contactez votre administrateur de domaine sur le **Configuration ordinateur > modèles d’administration > système > appel de procédure distante > Restrictions pour les clients RPC non authentifiés** la stratégie de groupe paramètre.