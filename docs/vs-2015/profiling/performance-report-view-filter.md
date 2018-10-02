---
title: Filtre de la vue Rapport de performances | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- profiling tools, Profiler Report view filter
- Profiler Report View filter, profiling tools
ms.assetid: 35f89d86-4683-4db1-aa0c-ae0ce65fa524
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1568ec12a635014239a1533bf00df09a1e63ac14
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501703"
---
# <a name="performance-report-view-filter"></a>Filtre de la vue Rapport de performances
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [filtre de vue de rapport de performances](https://docs.microsoft.com/visualstudio/profiling/performance-report-view-filter).  
  
La fenêtre de filtre de la vue Rapport du profileur se trouve en haut de la fenêtre Rapport de performances. Si elle n’est pas visible, cliquez sur le bouton **Afficher le filtre**.  
  
 Vous pouvez modifier chaque clause de filtre pour affiner vos résultats. Les colonnes suivantes sont disponibles dans le générateur de filtres.  
  
|Élément de filtre|Description|  
|-----------------|-----------------|  
|Et/ou|Choisissez **Et** si cette clause et la suivante doivent être vraies pour correspondre à un résultat. Choisissez **Ou** si cette clause ou la suivante peut être vraie pour correspondre à un résultat.|  
|Champ|Sélectionnez le champ à utiliser dans la clause de filtre dans la liste des champs de données disponibles dans le fichier de rapport actuel.|  
|Opérateur|Sélectionnez l’opérateur qui spécifie la relation qui doit exister entre le champ et la valeur.<br /><br /> =    Égal<br /><br /> <>  Différent de<br /><br /> <    Inférieur à<br /><br /> >    Supérieur à<br /><br /> <=  Inférieur ou égal à<br /><br /> >=  Supérieur ou égal à|  
|Value|Sélectionnez ou entrez la valeur à rechercher. Certains champs répertorient les valeurs disponibles.|  
  
 Vous pouvez ajouter des clauses jusqu’à ce que le filtre soit susceptible de fournir les meilleurs résultats possibles. Cliquez sur **Exécuter le filtre** pour appliquer le filtre au fichier de données.  
  
 À partir de la vue de rapport **Marques**, vous pouvez générer des clauses de filtre pour limiter les données dans les vues de rapport aux données collectées entre deux marques. Sélectionnez les marques de début et de fin des données de rapport, cliquez avec le bouton droit, puis sélectionnez **Ajouter un filtre aux marques** ou **Ajouter un filtre aux horodatages**. Ces deux filtres limitent les données du fichier de données actuel à la même étendue. L’option **Ajouter un filtre aux marques** peut être appliquée à d’autres fichiers .vsp.  
  
 Pour enregistrer le filtre, cliquez sur **Exporter le filtre** dans la barre d’outils Rapport de performances, puis spécifiez un emplacement et un nom pour le fichier .vspf. Pour charger un filtre déjà enregistré, cliquez sur **Importer le filtre**, puis recherchez le fichier de filtre enregistré. Les fichiers de filtres peuvent également servir à filtrer des fichiers de données sur des ordinateurs sur lesquels les outils de profilage autonomes sont installés. Pour plus d’informations, consultez [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse des données des outils d’analyse des performances](../profiling/analyzing-performance-tools-data.md)   
 [VSPerfReport](../profiling/vsperfreport.md)



