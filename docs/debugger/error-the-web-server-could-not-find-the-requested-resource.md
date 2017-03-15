---
title: "Erreur&#160;: le serveur Web n&#39;a pas trouv&#233; la ressource demand&#233;e | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "débogueur, erreurs d'applications Web"
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Erreur&#160;: le serveur Web n&#39;a pas trouv&#233; la ressource demand&#233;e
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour des raisons de sécurité, IIS a retourné une erreur générique.  
  
 Une des causes possibles est la configuration de la sécurité du serveur.  IIS 6.0 et les versions antérieures utilisaient un programme supplémentaire, appelé URLScan, pour filtrer les requêtes suspectes et incorrectes.  IIS 7.0 dispose du filtrage des demandes intégré pour le même objectif.  Dans les deux cas, un filtrage des demandes restrictif peut empêcher Visual Studio à déboguer le serveur.  
  
 Cette erreur peut se produire pour de nombreuses raisons.  Certaines des causes courantes incluent un problème lié à l'installation ou la configuration d'IIS, à la configuration de site Web, ou aux autorisations du système de fichiers.  Vous pouvez essayer d'accéder à la ressource avec un navigateur.  Selon comment IIS est configuré, vous devrez peut\-être utiliser un navigateur local sur le serveur ou examiner le journal des erreurs IIS pour obtenir un message d'erreur détaillé.  
  
 Pour plus d'informations sur la résolution des problèmes liés à IIS, consultez [IIS Management and Administration \(gestion et administration IIS\)](http://go.microsoft.com/fwlink/?LinkId=255872) \(page éventuellement en anglais\).  
  
## Voir aussi  
 [Outil de sécurité UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Erreur : le serveur Web est verrouillé et bloque l'exécution du verbe DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)