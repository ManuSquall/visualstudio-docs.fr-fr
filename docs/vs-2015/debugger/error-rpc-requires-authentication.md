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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a693b8ad331bbee5a920b0853f43ba521de2a105
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806800"
---
# <a name="error-rpc-requires-authentication"></a>Erreur : RPC requiert une authentification
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant. Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Exécutez `\` *windir*`\system32\regedt32.exe`  
  
2.  Localisez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4.  Si le problème persiste, contactez votre administrateur de domaine sur le **Configuration ordinateur -> modèles d’administration - > système -> Remote Procedure Call -> Restrictions pour les clients RPC non authentifiés** groupe paramètre de stratégie.



