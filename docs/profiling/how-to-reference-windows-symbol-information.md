---
title: "Comment&#160;: r&#233;f&#233;rencer les informations de symboles Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils d’analyse des performances, serveurs de symboles"
  - "serveurs, serveurs de symboles"
  - "outils de profilage, serveurs de symboles"
  - "serveurs de symboles"
ms.assetid: b7c67318-6be2-4b1e-a161-077b1f4a7c30
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Comment&#160;: r&#233;f&#233;rencer les informations de symboles Windows
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les outils de profilage Visual Studio utilisent des fichiers de symboles \(.pdb\) pour résoudre les noms symboliques, tels que les noms de fonction dans les fichiers binaires d'un programme.  Vous pouvez suivre ces étapes pour télécharger et mettre à jour automatiquement les fichiers .pdb correspondant à la version de Windows installée sur l'ordinateur local.  
  
> [!NOTE]
>  Ce paramètre n'affecte pas les rapports existants.  Seuls les rapports créés après la spécification du serveur de symboles auront les informations relatives aux symboles.  
  
 Pour plus d’informations, consultez [Spécifier les fichiers de symbole \(.pdb\) et les fichiers sources](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
### Pour utiliser le serveur de symboles de Microsoft  
  
1.  Créez un dossier destiné aux informations de fichier de symboles \(C:\\SymbolCache, par exemple\).  
  
2.  Dans le menu **Outils**, cliquez sur **Options**.  
  
     La boîte de dialogue **Options** s'affiche.  
  
3.  Développez l'arborescence **Débogage**, puis cliquez sur **Symboles**.  
  
4.  Dans **Emplacements du fichier de symboles \(.pdb\)**, sélectionnez **Serveurs de symboles Microsoft**  
  
5.  Dans **Mettre en cache les symboles à partir du serveur de symboles dans ce répertoire**, tapez le chemin d'accès du dossier qui a été créé au cours de l'étape 1, par exemple :  
  
     C:\\SymbolCache  
  
     Vous pouvez également cliquer sur le bouton de sélection \(**...**\) puis sélectionner un dossier de la boîte de dialogue **Rechercher un dossier** .  
  
## Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Procédure : sérialiser les informations de symboles](../profiling/how-to-serialize-symbol-information.md)