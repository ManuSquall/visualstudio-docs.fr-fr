---
title: "Comment&#160;: afficher les documents de script | Microsoft Docs"
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
  - "Explorateur de scripts"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Comment&#160;: afficher les documents de script
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans les versions antérieures de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichaient dans la fenêtre Explorateur de scripts.  La fenêtre Explorateur de scripts était souvent masquée et la disponibilité du script côté client n'était pas toujours évidente.  
  
 Dans [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], les fichiers de script côté client générés depuis un script côté serveur s'affichent dans l'Explorateur de solutions visible par défaut.  La fenêtre Explorateur de scripts a été supprimée.  
  
 Les fichiers de script côté client sont visibles uniquement lorsque vous êtes en mode débogage ou en mode arrêt.  Ils apparaissent dans le nœud **Documents de script**.  
  
 Les fichiers de script côté serveur sont toujours visibles.  Ils sont affichés dans le nœud **\<Chemin du site Web\>**.  Le nom du nœud se présente comme suit : `c:\...\Website2\`  
  
### Pour afficher un document de script côté serveur  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le nœud **\<Chemin du site Web\>**.  
  
2.  Double\-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté serveur s'ouvre dans une fenêtre source.  
  
### Pour afficher un document de script côté client  
  
1.  Dans l'**Explorateur de solutions**, ouvrez le nœud **Documents de script**.  
  
2.  Double\-cliquez sur le fichier de script que vous souhaitez afficher.  
  
     Le fichier de script côté client s'ouvre dans une fenêtre source.  
  
## Voir aussi  
 [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)