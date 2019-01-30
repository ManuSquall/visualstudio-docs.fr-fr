---
title: Visualisation des événements EventSource comme marqueurs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8db20a51872af37ce9f7ee655a365efb98d2f687
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938618"
---
# <a name="visualize-eventsource-events-as-markers"></a>Visualiser des événements EventSource en tant que marqueurs
Le visualiseur concurrentiel peut afficher des événements EventSource comme marqueurs, dont vous pouvez contrôler le mode d’affichage. Pour afficher les marqueurs EventSource, inscrivez le GUID du fournisseur ETW à l’aide de la boîte de dialogue [Paramètres avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md). Le visualiseur concurrentiel a des conventions par défaut pour représenter les événements EventSource comme [marqueurs d’indicateurs](../profiling/flag-markers.md), [marqueurs d’intervalles](../profiling/span-markers.md) et [marqueurs de messages](../profiling/message-markers.md). Vous pouvez personnaliser l’affichage des événements EventSource en ajoutant des champs personnalisés aux événements. Pour plus d’informations sur les marqueurs, consultez [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md). Pour plus d’informations sur les événements EventSource, consultez <xref:System.Diagnostics.Tracing>.  
  
## <a name="default-visualization-of-eventsource-events"></a>Visualisation par défaut des événements EventSource  
 Par défaut, le visualiseur concurrentiel utilise les conventions suivantes pour représenter les événements EventSource.  
  
### <a name="marker-type"></a>Type de marqueur  
  
1.  Les événements ayant l’[Opcode](/windows/desktop/WES/eventmanifestschema-opcodetype-complextype) win:Start ou win:Stop sont traités en tant que début ou fin d’un intervalle, respectivement.  Les intervalles imbriqués ou se chevauchant ne peuvent pas être affichés. Les paires d’événements qui commencent sur un thread et se terminent sur un autre ne peuvent pas être affichées.  
  
2.  Un événement dont l’Opcode n’est ni win:Start ni win:Stop est traité en tant qu’indicateur de marqueur, sauf si son champ [Level](/windows/desktop/WES/defining-severity-levels) (EVENT_RECORD.EVENT_HEADER.EVENT_DESCRIPTOR) a pour valeur minimale win:Verbose.  
  
3.  Dans tous les autres cas, l’événement est traité en tant que message.  
  
### <a name="importance"></a>Importance  
 Le tableau suivant établit une correspondance entre le niveau d’événement et l’importance du marqueur.  
  
|Niveau ETW|Importance dans le visualiseur concurrentiel|  
|---------------|---------------------------------------|  
|win:LogAlways|Normale|  
|win:Critical|Critique|  
|win:Error|Critique|  
|win:Warning|Haute|  
|win:Informational|Normale|  
|win:Verbose|Faible|  
|Supérieur à win:verbose|Faible|  
  
### <a name="series-name"></a>Nom de la série  
 Le nom de la tâche de l’événement est utilisé pour le nom de la série. Le nom de la série est vide si aucune tâche n’a été définie pour l’événement.  
  
### <a name="category"></a>Category  
 Si le niveau est win:Critical ou win:Error, la catégorie est Alerte (-1). Sinon, la catégorie est la valeur par défaut (0).  
  
### <a name="text"></a>Texte  
 Si un message de texte de format de type printf a été défini pour l’événement, il est affiché en tant que description du marqueur. Sinon, la description est le nom de l’événement et la valeur de chaque champ de charge utile.  
  
## <a name="customize-visualization-of-eventsource-events"></a>Personnaliser la visualisation des événements EventSource  
 Vous pouvez personnaliser l’affichage des événements EventSource en ajoutant les champs appropriés à l’événement, comme décrit dans les sections suivantes.  
  
### <a name="marker-type"></a>Type de marqueur  
 Utilisez le champ `cvType`, un octet, pour contrôler le type de marqueur qui sert à représenter l’événement. Voici les valeurs disponibles pour cvType :  
  
|Valeur de cvType|Type de marqueur résultant|  
|------------------|---------------------------|  
|0|Message|  
|1|Début de l’intervalle|  
|2|Fin de l’intervalle|  
|3|Indicateur|  
|Toutes les autres erreurs|Message|  
  
### <a name="importance"></a>Importance  
 Vous pouvez utiliser le champ `cvImportance`, un octet, pour contrôler le paramètre d’importance d’un événement EventSource. Toutefois, nous vous recommandons de contrôler l’importance affichée d’un événement à l’aide de son niveau (Level).  
  
|Valeur de cvImportance|Importance dans le visualiseur concurrentiel|  
|------------------------|---------------------------------------|  
|0|Normale|  
|1|Critique|  
|2|Haute|  
|3|Haute|  
|4|Normale|  
|5|Faible|  
|Toutes les autres erreurs|Faible|  
  
### <a name="series-name"></a>Nom de la série  
 Utilisez le champ d’événement `cvSeries`, une chaîne, pour contrôler le nom de série que le visualiseur concurrentiel donne à un événement EventSource.  
  
### <a name="category"></a>Category  
 Utilisez le champ `cvCategory`, un octet, pour contrôler la catégorie que le visualiseur concurrentiel donne à un événement EventSource.  
  
### <a name="text"></a>Texte  
 Utilisez le champ `cvTextW`, une chaîne, pour contrôler la description que le visualiseur concurrentiel donne à un événement EventSource.  
  
### <a name="spanid"></a>ID d’intervalle  
 Utilisez le champ cvSpanId, un entier, pour faire correspondre des paires d’événements. La valeur de chaque paire d’événements de démarrage et d’arrêt qui représentent un intervalle doit être unique. En général, pour du code concurrent, vous devez utiliser des primitives de synchronisation comme <xref:System.Threading.Interlocked.Exchange%2A> pour que la clé (la valeur utilisée pour CvSpanID) soit correcte.  
  
> [!NOTE]
>  L’utilisation de l’ID d’intervalle pour imbriquer des intervalles, permettre à des intervalles de se chevaucher partiellement sur le même thread ou permettre à des intervalles de démarrer sur un thread et de se terminer sur un autre n’est pas prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)