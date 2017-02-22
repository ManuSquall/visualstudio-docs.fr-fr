---
title: "Cr&#233;ation de fichiers de donn&#233;es de profilage portables &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2ceb63a7-b835-4988-b756-2afc3fcc4808
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Cr&#233;ation de fichiers de donn&#233;es de profilage portables &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour simplifier le partage de données de profilage, vous pouvez utiliser l'outil en ligne de commande [VSPerfReport](../profiling/vsperfreport.md) pour incorporer les symboles pour une exécution du profilage dans le fichier .vsp.  
  
 Vous pouvez également créer un fichier de données de profilage pré\-analysé \(.vsps\) qui est plus petit et plus rapide pour charger dans l'IDE.  
  
> [!NOTE]
>  Assurez\-vous que les fichiers de symboles \(.pdb\) sont disponibles pour **VSPerfReport**.  Pour plus d'informations, consultez [Comment : spécifier les emplacements du fichier de symboles à partir de la ligne de commande](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
>   
>  Pour plus d'informations sur le chemin d'accès à **VSReport**, consultez [Spécification du chemin d'accès aux outils en ligne de commande](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Les données de profilage dans un fichier .vsps ne peuvent pas être filtrées.  
  
### Pour incorporer les symboles pour une exécution du profilage dans un fichier de données de profilage \(.vsp\)  
  
-   Dans la fenêtre d'invite de commandes, tapez la commande suivante :  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/PackSymbols**  
  
     Par défaut, le fichier .vsps est nommé avec le nom de base du fichier .vsp.  Vous pouvez spécifier un autre nom à l'aide de l'option **Output**.  
  
### Pour créer un fichier de données de profilage résumé  
  
-   Dans la fenêtre d'invite de commandes, tapez la commande suivante :  
  
     \<Path\>**VSPerfReport \<**VSP File\> **\/SummaryFile** \[**\/Output:**\<File Name\>\]  
  
     Par défaut, le fichier .vsps est nommé avec le nom de base du fichier .vsp.  Vous pouvez spécifier un autre nom à l'aide de l'option **Output**.