---
title: "Comment&#160;: d&#233;boguer des clients COM et des serveurs &#224; l&#39;aide du d&#233;bogage RPC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "clients COM, débogage"
  - "serveurs COM, débogage"
  - "COM, débogage"
  - "débogage d'appel de procédure distante en cours"
  - "débogage RPC hors processus"
  - "débogage distant, appel de procédure distante (RPC)"
  - "appel de procédure distante (RPC)"
  - "appel de procédure distante (RPC), débogage"
  - "appel de procédure distante (RPC), déboguer des clients et serveurs COM"
ms.assetid: 3e8526c8-43b5-4b87-8e0d-b22c24f0a3ea
caps.latest.revision: 23
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 23
---
# Comment&#160;: d&#233;boguer des clients COM et des serveurs &#224; l&#39;aide du d&#233;bogage RPC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser le débogage RPC pour déboguer des applications client\/serveur COM.  Vous devez activer le débogage RPC pour l'utiliser.  Lorsque le débogage RPC est activé, si vous effectuez un pas à pas détaillé dans l'appel serveur à partir du client, le débogueur est attaché au serveur, ce qui permet de déboguer son code.  Une fois que le débogueur est attaché, vous pouvez utiliser toutes ses fonctionnalités avec les processus client et serveur.  
  
### Pour activer le débogage RPC  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, cliquez sur le dossier **Débogage**.  
  
3.  Cliquez sur la page **Natif**.  
  
4.  Activez la case à cocher **Débogage RPC**.  
  
    > [!NOTE]
    >  Pour déboguer des appels RPC, vous devez posséder les privilèges Administrateur ou Utilisateur avec pouvoirs.  
  
    > [!NOTE]
    >  Le processus d'exécution pas à pas RPC sur un serveur distant qui exécute Microsoft Windows Vista fonctionne uniquement si un débogueur natif est attaché au serveur distant.  Sinon, l'appel RPC échoue sans message d'erreur.  Sinon, l'appel RPC s'effectue, mais le processus d'exécution pas à pas dans l'appel RPC ne fonctionne pas.  
  
## Voir aussi  
 [Débogage de serveurs et de conteneurs COM](../debugger/com-server-and-container-debugging.md)   
 [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md)