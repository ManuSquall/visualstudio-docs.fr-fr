---
title: "Erreur&#160;: Pare-feu sur ordinateur local | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.firewall.localmachine"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Erreur&#160;: Pare-feu sur ordinateur local
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le pare\-feu de connexion Internet sur l'ordinateur local, à partir duquel vous exécutez Visual Studio, n'est pas configuré pour autoriser le débogage distant.  Pour le débogage distant managé ou natif avec le transport par défaut, le port TCP 135 doit être ouvert pour le trafic DCOM.  Le partage de fichiers et d'imprimantes doit être ouvert, et devenv.exe doit être ajouté à la liste d'exceptions.  L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
 Pour plus d'informations, consultez [Configurer les outils de contrôle à distance sur le périphérique](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).