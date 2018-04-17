---
title: 'Erreur : RPC requiert une authentification | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7134a52f4c219b985cff3174703cf217057a5150
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Exécutez `\` *windir*`\system32\regedt32.exe`  
  
2.  Recherchez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4.  Si le problème persiste, contactez votre administrateur de domaine sur le **Configuration ordinateur > modèles d’administration > système > appel de procédure distante > Restrictions pour les clients RPC non authentifiés** la stratégie de groupe paramètre.