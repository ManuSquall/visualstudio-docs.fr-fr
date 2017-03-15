---
title: "Applications serveur SDI | Microsoft Docs"
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
  - "applications serveur SDI"
  - "applications serveur SDI, débogage"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Applications serveur SDI
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Si vous déboguez une application serveur SDI, vous devez spécifier `/Embedding` ou `/Automation` dans la propriété **Arguments de la ligne de commande** de la boîte de dialogue Pages de propriétés de *Project* pour les projets C\/C\+\+, C\# ou Visual Basic.  
  
 Avec ces arguments de la ligne de commande, le débogueur peut lancer l'application serveur comme si elle était lancée d'un conteneur.  Le démarrage du conteneur à partir du Gestionnaire de programmes ou du Gestionnaire de fichiers entraîne l'utilisation par le conteneur de l'instance du serveur démarrée dans le débogueur.  
  
## Recherche de la propriété Arguments de la ligne de commande  
 Pour accéder à la boîte de dialogue Pages de propriétés de *Project*, cliquez avec le bouton droit sur votre projet dans l'Explorateur de solutions, puis sélectionnez Propriétés dans le menu contextuel.  Pour trouver la propriété Arguments de la ligne de commande, développez la catégorie Propriétés de configuration, puis cliquez sur la page Débogage.  
  
## Voir aussi  
 [Débogage COM et ActiveX](../debugger/com-and-activex-debugging.md)   
 [Comment : déboguer des serveurs COM](../Topic/How%20to:%20Debug%20COM%20Servers.md)