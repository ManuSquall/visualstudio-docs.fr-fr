---
title: 'Erreur : RPC requiert une authentification | Microsoft Docs'
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
- vs.debug.error.rpc_requires_authentication
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5643e815386541bb9045eb56cacbd68e7e9b998d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193829"
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Exécutez `\` *windir*`\system32\regedt32.exe`  
  
2.  Localisez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4.  Si le problème persiste, contactez votre administrateur de domaine sur le **Configuration ordinateur -> modèles d’administration - > système -> Remote Procedure Call -> Restrictions pour les clients RPC non authentifiés** groupe paramètre de stratégie.



