---
title: 'Erreur : RPC requiert une authentification | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c473916a6b689984f234736eb8b763056fc002d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850457"
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Exécutez `\` *windir*`\system32\regedt32.exe`

2. Localisez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.

3. Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.

4. Si le problème persiste, contactez votre administrateur de domaine sur le **Configuration ordinateur > modèles d’administration > système > appel de procédure distante > Restrictions pour les clients RPC non authentifiés** stratégie de groupe paramètre.