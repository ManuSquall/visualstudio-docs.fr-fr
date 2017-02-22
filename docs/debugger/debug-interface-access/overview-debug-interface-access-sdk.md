---
title: "Vue d’ensemble (Kit de d&#233;veloppement logiciel Debug&#160;Interface&#160;Access) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "types définis par l’utilisateur"
  - "fichiers .dbg"
  - "modules"
  - "interfaces [Kit de développement DIA (SDK)]"
  - "fichiers DBG"
  - "procédures [Kit de développement DIA (SDK)]"
  - "fichiers exécutables"
  - "objets COM, dans le Kit de développement DIA (SDK)"
  - "compilands"
  - "images exécutables"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Vue d’ensemble (Kit de d&#233;veloppement logiciel Debug&#160;Interface&#160;Access)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilisez le diamètre Kit de développement logiciel pour accéder aux informations de débogage Microsoft.  Le diamètre Kit de développement SDK fournit un ensemble d'API basé sur COM qui élimine la nécessité de réécrire votre code chaque fois que Microsoft modifie le format des informations de débogage.  Le diamètre Kit de développement logiciel vous permet également à la lecture d'un ensemble de sélectionner des versions précédentes des informations de débogage, situées dans les fichiers .pdb et de .dbg générés par les versions 5,0 de [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] et versions ultérieures.  
  
 Chaque interface dans le diamètre Kit de développement logiciel représente un objet COM différent, sauf dans indiquée sinon.  Les interfaces supplémentaires, etc. des objets supplémentaires, sont créés par l'intermédiaire de requêtes explicites, comme [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) ou [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), plutôt qu'en appelant `QueryInterface` sur les pointeurs d'interface existants.  
  
## Voir aussi  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)