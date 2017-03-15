---
title: "Mode R&#233;sum&#233; - Donn&#233;es d’&#233;chantillonnage du profileur | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "méthode de profilage par échantillonnage, mode Résumé"
  - "Mode Résumé"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Mode R&#233;sum&#233; - Donn&#233;es d’&#233;chantillonnage du profileur
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le mode Résumé affiche des informations sur les fonctions les plus performantes dans une exécution de profilage.  Pour plus d'informations, y compris une description des liens de notification et des listes de rapports, consultez [Mode Résumé](../profiling/summary-view.md).  
  
> [!NOTE]
>  Les fonctionnalités de sécurité renforcée dans windows 8 et Windows Server 2012 requises des modifications significatives de la manière que le profileur Visual Studio collecte des données sur ces plateformes.  Les applications de mémoire de fenêtres requièrent également de nouvelles techniques de collection.  Consultez [Profilage d'applications Windows 8 et Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Graphique de chronologie  
 Le graphique de chronologie du mode Résumé affiche le pourcentage d'utilisation du processeur de l'application profilée pendant la durée du profilage.  Vous pouvez utiliser le graphique de chronologie pour filtrer la vue selon un intervalle de temps sélectionné.  Pour plus d’informations, consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Chemin réactif  
 Le **chemin réactif** affiche le chemin d'exécution dans lequel la plupart des échantillons ont été collectés.  Vous pouvez cliquer sur une fonction pour afficher la vue Informations relatives à la fonction pour la fonction.  Pour consulter d'autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue dans la liste.  
  
 Le **chemin réactif** inclut les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom de la fonction.|  
|**% d'échantillons inclusifs**|Le pourcentage de tous les échantillons qui se sont produits lorsque cette fonction ou une fonction appelée par cette fonction s'exécutait.|  
|**% d'échantillons exclusifs**|Le pourcentage de tous les échantillons qui se sont produits lorsque la fonction exécutait du code dans le corps de la fonction.  Les échantillons collectés dans les fonctions appelées par cette fonction ne sont pas inclus.|  
  
## Fonctions faisant le plus de travail individuel  
 La liste **Fonctions faisant le plus de travail individuel** affiche les fonctions qui ont le plus grand nombre d'échantillons exclusifs dans l'exécution du profilage.  Un échantillon exclusif est assigné à une fonction si la fonction exécute son propre code au moment où l'échantillon est collecté.  Un échantillon exclusif n'est pas assigné à une fonction si la fonction appelle une autre fonction au moment où l'échantillon est collecté.  Un grand nombre d'échantillons exclusifs indique que beaucoup de temps a été passé au sein de la fonction.  
  
 Vous pouvez cliquer sur une fonction pour afficher la vue Informations relatives à la fonction pour la fonction.  Pour consulter d'autres vues pour la fonction, cliquez avec le bouton droit sur la fonction, puis cliquez sur une vue dans la liste.  
  
 Les **Fonctions exigeant le plus de travail individuel** incluent les données suivantes pour chaque fonction :  
  
|Colonne|Description|  
|-------------|-----------------|  
|**Nom**|Nom de la fonction.|  
|**% d'échantillons exclusifs**|Le pourcentage de tous les échantillons dans l'exécution du profilage collectés lorsque la fonction exécutait le code au sein du corps de la fonction.  Le pourcentage exclut les échantillons collectés lorsque les fonctions que cette fonction a appelées s'exécutaient.|  
  
## Voir aussi  
 [Mode Résumé](../profiling/summary-view-dotnet-memory-data.md)   
 [Mode Résumé](../profiling/summary-view-instrumentation-data.md)