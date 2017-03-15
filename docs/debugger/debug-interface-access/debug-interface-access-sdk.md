---
title: "Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access | Microsoft Docs"
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
  - "débogage (DIA SDK)"
  - "débogueur (DIA SDK)"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Kit de d&#233;veloppement logiciel de Debug&#160;Interface&#160;Access
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le Kit de développement logiciel DIA de débogage \(Microsoft intermediate diamètre Kit de développement logiciel windows\) permet d'accéder aux informations de débogage stockées dans les fichiers de base de données du programme \(.pdb\) générés par les outils de postcompiler Microsoft.  Étant donné que le format du fichier .pdb généré par les outils de postcompiler entraîne une révision constante, exposer le format est pas pratique.  Utilisation de l'API de diamètre, vous pouvez développer des applications qui les trouver pour et parcourez les informations de débogage stockées dans un fichier .pdb.  De telles applications peuvent, par exemple, stocker les informations de suivi de pile et analyser les données de performance.  
  
## Dans cette section  
 [Prise en main](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Donne une vue d'ensemble du diamètre Kit de développement logiciel fonctionnalités et spécifie où le diamètre Kit de développement DAO SDK est installé ainsi que l'en\-tête et les fichiers bibliothèques obligatoires.  
  
 [Interrogation du fichier .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Fournit des instructions sur la façon d'utiliser l'API de diamètre pour interroger le fichier .pdb.  
  
 [Balises Symbols et Symbol](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Explique comment les symboles et les balises de symboles sont utilisés dans l'API de diamètre.  
  
 [Référence](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contient les interfaces, des méthodes, des énumérations, et les structures de l'API de diamètre.  
  
 [Dia2dump, exemple](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Montre comment utiliser l'API de diamètre pour rechercher et de parcourir les informations de débogage.  
  
 [Dia2dump.cpp, fichier source](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Code source utilisé par [Dia2dump, exemple](../../debugger/debug-interface-access/dia2dump-sample.md) pour afficher l'API de diamètre.