---
title: "Filtrage des vues des rapports des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "outils de profilage, configurer"
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Filtrage des vues des rapports des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez appliquer des filtres aux fichiers de données de profilage pour limiter les données de profilage qui sont affichées dans les vues Rapport de performances et sont exportées vers les fichiers de rapport.  Vous pouvez limiter un rapport aux données entre deux valeurs d'horodatage, et vous pouvez limiter les données à des processus et threads spécifiques.  Vous pouvez enregistrer des filtres dans un fichier, puis créez un filtre sur un autre fichier de données de profilage en important le filtre enregistré.  
  
 Vous pouvez également limiter un rapport à un intervalle de temps en utilisant la chronologie graphique de la vue Résumé.  Consultez [Comment : filtrer les vues de rapport à partir de la chronologie Résumé](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
 Pour exclure du code système et tiers d'un rapport, consultez [Procédure : filtrer les vues de rapport de façon à afficher Uniquement mon code](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md)  
  
## Procédures  
  
#### Pour créer un filtre de rapport de profileur  
  
1.  Si la fenêtre Filtre de la vue Rapport de performances n'est pas affichée, cliquez sur **Afficher le filtre** dans la barre d'outils de la vue Rapport de performances.  
  
     La fenêtre Filtre de la vue Rapport de performances se présente sous la forme d'une table.  Chaque ligne de la table représente une clause du filtre.  Vous pouvez ajouter autant de clauses que vous souhaitez à un filtre.  
  
2.  Pour chaque clause que vous souhaitez ajouter à un filtre, sélectionnez ou entrez des valeurs dans les champs suivants d'une ligne.  
  
    |Champ|Description|  
    |-----------|-----------------|  
    |**Et\/ou**|Choisissez **Et** si cette clause et la suivante doivent avoir la valeur true pour correspondre à un résultat.  Choisissez **Ou** si cette clause ou la suivante peut avoir la valeur true pour correspondre à un résultat.|  
    |**Champ**|Dans la liste des champs de données affichée, sélectionnez le champ de rapport à utiliser dans la clause de filtre.|  
    |**Opérateur**|Sélectionnez l'opérateur qui spécifie la relation qui doit exister entre le champ et la valeur dans la clause.<br /><br /> \=    Est égal à<br /><br /> \<\>  Est différent de<br /><br /> \<    Inférieur à<br /><br /> \>    Supérieur à<br /><br /> \<\=  Inférieur ou égal à<br /><br /> \>\=  Supérieur ou égal à|  
    |**Valeur**|Sélectionnez ou entrez la valeur à rechercher.  Certains champs répertorient les valeurs disponibles.|  
  
#### Pour créer un filtre de rapport de profileur depuis la vue de rapport Marques  
  
1.  Sélectionnez **Marques** dans la liste **Affichage actuel** de la barre d'outils de la vue Rapport de performances.  
  
     Le rapport de profileur Marques s'affiche.  
  
2.  Sélectionnez l'événement ETW ou l'événement d'échantillonnage que vous souhaitez utiliser comme point de départ du rapport.  
  
3.  Appuyez sur la touche CTRL et, tout en la maintenant enfoncée, cliquez sur l'événement que vous souhaitez utiliser comme point final du rapport.  
  
4.  Cliquez avec le bouton droit, puis cliquez sur l'une des options suivantes :  
  
    -   **Ajouter un filtre sur les marques** crée des clauses de filtre qui utilisent la colonne Marque comme zone de filtre.  
  
    -   **Ajouter un filtre aux horodatages** pour créer des clauses de filtre qui utilisent la colonne Horodatage en millisecondes comme champ de filtre.  
  
     Les deux options filtrent le fichier de données actuel aux mêmes points de début et de fin.  L'une ou l'autre peut être la meilleure des options si vous exportez le filtre pour l'utiliser dans d'autres rapports.  
  
#### Pour charger un filtre existant à partir d'un fichier  
  
1.  Dans la barre d'outils de la vue Rapport de performances, cliquez sur **Importer le filtre**.  
  
     La boîte de dialogue **Charger le filtre** s'ouvre.  
  
2.  Spécifiez l'emplacement et le nom de fichier du fichier de filtre \(.vspf\) à charger.  
  
#### Pour exécuter un filtre  
  
-   Dans la barre d'outils de la vue Rapport de performances, cliquez sur **Exécuter le filtre**.  
  
#### Pour arrêter un filtre dont l'exécution est trop lente  
  
-   Dans la barre d'outils de la vue Rapport de performances, cliquez sur **Arrêter le filtre**.  
  
#### Pour supprimer un filtre d'une vue de rapport  
  
1.  Supprimez les lignes de clauses dans le filtre de la vue Rapport de performances.  
  
2.  Dans la barre d'outils de la vue Rapport de performances, cliquez sur **Exécuter le filtre**.  
  
#### Pour enregistrer un filtre dans un fichier  
  
1.  Dans la barre d'outils de la vue Rapport de performances, cliquez sur **Exporter le filtre**.  
  
     La boîte de dialogue **Enregistrer le filtre** s'ouvre.  
  
2.  Spécifiez l'emplacement et le nom de fichier du fichier de filtre \(.vspf\) à enregistrer.  
  
## Voir aussi  
 [Personnalisation des vues des rapports des outils de profilage](../profiling/customizing-performance-tools-report-views.md)