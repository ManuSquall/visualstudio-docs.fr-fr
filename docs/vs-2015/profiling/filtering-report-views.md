---
title: Filtrage des vues des rapports | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, configuring
ms.assetid: 820cf192-7fd6-4bee-9a51-aa69154aca85
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 344a2dbe0e629f62f609806008b963be2be058a1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108707"
---
# <a name="filtering-report-views"></a>Filtrage des vues des rapports
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez appliquer des filtres aux fichiers de données de profilage pour limiter les données qui sont affichées dans les vues des rapports de performances et exportées dans les fichiers de rapport. Vous pouvez limiter un rapport aux données entre des valeurs d’horodatage, et limiter les données à des processus et des threads spécifiques. Vous pouvez enregistrer les filtres dans un fichier, puis créer un filtre sur un autre fichier de données de profilage en important le filtre enregistré.  
  
 Vous pouvez également limiter un rapport à un intervalle de temps en utilisant la chronologie graphique de la vue Résumé. Consultez [Guide pratique pour filtrer les vues de rapport à partir de la chronologie Résumé](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
 Pour exclure le code système et le code de tiers d’un rapport, consultez [Guide pratique pour filtrer les vues de rapport des outils de profilage de façon à afficher Uniquement mon code](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md)  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-create-a-profiler-report-filter"></a>Pour créer un filtre de rapport de profileur  
  
1. Si la fenêtre Filtre de la vue Rapport de performances n’est pas affichée, cliquez sur **Afficher le filtre** sur la barre d’outils de la vue Rapport de performances.  
  
     Le Filtre de la vue Rapport de performances est un tableau. Chaque ligne du tableau représente une clause du filtre. Vous pouvez ajouter autant de clauses que vous le souhaitez à un filtre.  
  
2. Pour chaque clause que vous voulez ajouter à un filtre, sélectionnez ou entrez des valeurs dans les champs suivants d’une ligne.  
  
    |Champ|Description|  
    |-----------|-----------------|  
    |**Et/ou**|Choisissez **Et** si cette clause et la suivante doivent être vraies pour correspondre à un résultat. Choisissez **Ou** si cette clause ou la suivante peut être vraie pour correspondre à un résultat.|  
    |**Champ**|Sélectionnez le champ du rapport à utiliser dans la clause du filtre dans la liste de champs de données.|  
    |**Operator**|Sélectionnez l’opérateur qui spécifie la relation qui doit exister dans la clause entre le champ et la valeur.<br /><br /> =    Égal<br /><br /> <>  Différent de<br /><br /> <    Inférieur à<br /><br /> >    Supérieur à<br /><br /> <=  Inférieur ou égal à<br /><br /> >=  Supérieur ou égal à|  
    |**Valeur**|Sélectionnez ou entrez la valeur à rechercher. Certains champs répertorient les valeurs disponibles.|  
  
3. 
  
#### <a name="to-create-a-profiler-report-filter-from-the-marks-report-view"></a>Pour créer un filtre de rapport de profileur à partir de la vue du rapport Marques  
  
1. Sélectionnez **Marques** dans la liste **Vue actuelle** sur la barre d’outils de la vue Rapport de performances.  
  
    Le rapport de profileur Marques s’affiche.  
  
2. Sélectionnez l’événement ETW ou l’événement d’échantillonnage que vous voulez utiliser comme point de départ du rapport.  
  
3. Appuyez sur la touche Ctrl tout en la maintenant enfoncée et cliquez sur l’événement que vous voulez utiliser comme point de fin du rapport.  
  
4. Cliquez avec le bouton droit, puis cliquez sur une des options suivantes :  
  
   - **Ajouter un filtre aux marques** crée des clauses de filtre qui utilisent la colonne Marque comme champ de filtre.  
  
   - **Ajouter un filtre aux horodatages** crée des clauses de filtre qui utilisent la colonne Horodatage en millisecondes comme champ de filtre.  
  
     Les deux options filtrent le fichier de données actif aux mêmes points de début et de fin. L’une ou l’autre des options peut être préférable si vous exportez le filtre pour l’utiliser dans d’autres rapports.  
  
#### <a name="to-load-an-existing-filter-from-a-file"></a>Pour charger un filtre existant à partir d’un fichier  
  
1. Dans la barre d’outils de la vue Rapport de performances, cliquez sur **Importer un filtre**.  
  
     La boîte de dialogue **Charger un filtre** s’affiche.  
  
2. Spécifiez l’emplacement et le nom de fichier du fichier de filtre (.vspf) à charger.  
  
#### <a name="to-execute-a-filter"></a>Pour exécuter un filtre  
  
- Dans la barre d’outils de la vue Rapport de performances, cliquez sur **Exécuter le filtre**.  
  
#### <a name="to-stop-a-filter-that-is-taking-too-long-to-execute"></a>Pour arrêter un filtre dont l’exécution est trop longue  
  
- Dans la barre d’outils de la vue Rapport de performances, cliquez sur **Arrêter le filtre**.  
  
#### <a name="to-remove-a-filter-on-a-report-view"></a>Pour supprimer un filtre sur une vue de rapport  
  
1. Supprimer les lignes des clauses dans le Filtre de la vue Rapport de performances.  
  
2. Dans la barre d’outils de la vue Rapport de performances, cliquez sur **Exécuter le filtre**.  
  
#### <a name="to-save-a-filter-to-a-file"></a>Pour enregistrer un filtre dans un fichier  
  
1. Dans la barre d’outils de la vue Rapport de performances, cliquez sur **Exporter le filtre**.  
  
     La boîte de dialogue **Enregistrer le filtre** s’affiche.  
  
2. Spécifiez l’emplacement et le nom de fichier du fichier de filtre (.vspf) à enregistrer.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des vues des rapports des outils d’analyse des performances](../profiling/customizing-performance-tools-report-views.md)
