---
title: 'Erreur : RPC requiert une authentification | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf0c2d13668dbf380f326ee3a49e0389815a8fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535734"
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1. Exécuter `\` *windir*`\system32\regedt32.exe`  
  
2. Recherchez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients` .  
  
3. Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4. Si le problème persiste, contactez votre administrateur de domaine à propos du paramètre de stratégie de groupe **Configuration ordinateur->modèles d’administration->de l’appel de procédure distante->des Restrictions >pour les clients RPC non authentifiés** .
