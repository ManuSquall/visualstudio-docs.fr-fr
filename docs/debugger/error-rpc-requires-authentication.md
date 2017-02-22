---
title: "Erreur&#160;: RPC requiert une authentification | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.rpc_requires_authentication"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 88362b3b-8fbe-431f-96a4-80e2d822bbc7
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Erreur&#160;: RPC requiert une authentification
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le débogueur Visual Studio ne peut pas se connecter à l'ordinateur distant.  Une stratégie RPC est activée sur l'ordinateur local qui empêche le débogage distant.  
  
### Pour corriger cette erreur  
  
1.  Exécutez `\`*windir*`\system32\regedt32.exe`  
  
2.  Recherchez et supprimez `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows NT\RPC\RestrictRemoteClients`.  
  
3.  Redémarrez votre ordinateur afin que la modification du Registre entre en vigueur.  
  
4.  Si le problème persiste, contactez votre administrateur de domaine à propos du paramètre de stratégie de groupe Configuration de l'ordinateur\-\>Modèles d'administration\-\>Système\-\>Appel de procédure distante\>Restrictions pour les clients à distance RPC non authentifiés.