---
title: "Cr&#233;ation de rapports de profileur &#224; partir de la ligne de commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Cr&#233;ation de rapports de profileur &#224; partir de la ligne de commande
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'outil en ligne de commande **VSPerfReport** vous permet de créer des rapports .xml ou .csv à partir des fichiers de données de profilage \(.vsp\).  Le rapport VSPerfReport catégorise les étroites correspondances des vues basées sur la table, de l'interface pour [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Vous pouvez filtrer le rapport pour afficher uniquement votre code et afficher uniquement un segment du fichier de données de profilage.  Pour plus d'informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
 Vous pouvez également simplifier vos fichiers de données de profilage à partager en incorporant des symboles dans les fichiers .vsp et en créant des fichiers de rapport pré\-analysés \(.vsps\) qui sont plus petits et plus rapides à ouvrir.  
  
## Tâches courantes  
  
|Tâche|Contenu associé|  
|-----------|---------------------|  
|**Créer un rapport de base :** créez tous les types de rapports VSPerfReport ou un sous\-ensemble de ces derniers.|-   [Création de rapports de base](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Comparer deux fichiers de données de profilage :** créez un rapport « diff » qui compare les données de performance dans deux fichiers de données de profilage.|-   [Comment : créer un rapport de comparaisons du profileur à partir d'une invite de commandes](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Afficher les données de suivi d'appels et de Suivi d'événements pour Windows \(ETW\) :** créez un rapport de suivi d'appels qui répertorie les informations de temporisation pour chaque point d'entrée et de sortie de vos fonctions d'application et chaque appel passé à d'autres fonctions par votre fonction.  Vous pouvez également créer une liste détaillée des événements ETW collectés lors d'une exécution du profilage.|-   [Comment : créer un rapport de suivi d'appels](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrer un rapport :** limitez un rapport aux seules fonctions de votre code ou à une heure spécifique dans le fichier de données de profilage.|-   [Comment : filtrer des rapports à partir de la ligne de commande](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Créer des fichiers de données de profilage portables :** pour simplifier le partage des données de profilage, vous pouvez incorporer les symboles d'une exécution du profilage dans le fichier .vsp.  Vous pouvez également créer un fichier de données de profilage pré\-analysé \(.vsps\) qui est plus petit et plus rapide à ouvrir.|-   [Création de fichiers de données de profilage portables](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|