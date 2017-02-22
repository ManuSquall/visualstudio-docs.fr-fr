---
title: "Visualisation des &#233;v&#233;nements EventSource en tant que marqueurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a10022a-5c37-48b1-a833-dd35902176b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Visualisation des &#233;v&#233;nements EventSource en tant que marqueurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le Visualiseur concurrentiel peut afficher des événements EventSource comme les marqueurs, et vous pouvez contrôler la façon dont les marqueurs sont affichés.  Pour afficher les marqueurs EventSource, enregistrez le GUID du fournisseur ETW à l'aide de la boîte de dialogue [Paramètres Avancés](../profiling/advanced-settings-dialog-box-concurrency-visualizer.md).  Le Visualiseur concurrentiel présente les conventions par défaut pour représenter des événements EventSource comme [Repérer les marqueurs](../profiling/flag-markers.md), [Marqueurs Span](../profiling/span-markers.md), et [Marqueurs de messages](../profiling/message-markers.md).  Vous pouvez personnaliser la façon dont les événements EventSource sont affichés en ajoutant des champs personnalisés aux événements.  Pour plus d'informations sur les marqueurs, consultez [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md).  Pour plus d'informations sur les événements EventSource, consultez <xref:System.Diagnostics.Tracing>.  
  
## Visualisation par Défaut des événements EventSource  
 Par défaut, le Visualiseur concurrentiel utilise les conventions suivantes pour représenter des événements EventSource.  
  
### Type de marqueur  
  
1.  Les événements qui ont [Opcode](http://msdn.microsoft.com/fr-fr/d97953df-669b-4c55-b1a8-925022b339b7) win:Start ou win:Stop sont traités comme le début ou la fin d'une étendue, respectivement.  Les étendues imbriquées ou superposées ne peuvent pas être affichées.  Les paires d'événements qui commencent sur un thread et se termine sur un autre ne peuvent pas être affichées.  
  
2.  Un événement dont l'opcode n'est ni win:Start ni win:Stop est traité comme un flag de marqueur à moins que son [Niveau](http://msdn.microsoft.com/fr-fr/dfa4e0a9-4d89-4f50-aef9-1dae0dc11726) \(champ d'EVENT\_RECORD.EVENT\_HEADER.EVENT\_DESCRIPTOR\) ne soit win:Verbose ou supérieur.  
  
3.  Dans tous les autres cas, l'événement est traité comme un message.  
  
### Importance  
 Le tableau suivant définit comment le niveau d'événements s'associe à l'importance de marqueur.  
  
|Niveau ETW|Importance du Visualiseur Concurrentiel|  
|----------------|---------------------------------------------|  
|win:LogAlways|Normal|  
|win:Critical|Critical|  
|win:Error|Critical|  
|win:Warning|Élevée|  
|win:Informational|Normal|  
|win:Verbose|Basse|  
|Supérieur à win:verbose|Basse|  
  
### Nom de la série  
 Le nom de la tâche de l'événement est utilisé pour le nom de la série.  Le nom de la série est vide si aucune tâche n'a été définie pour l'événement.  
  
### Catégorie  
 Si le niveau est win:Critical ou win:Error, alors la catégorie est Alert \(\-1\).  Sinon, la catégorie est la valeur par défaut \(0\).  
  
### Texte  
 Si un message textuel de mise en forme de type printf a été défini pour l'événement, il est affiché comme une description du marqueur.  Sinon, la description est le nom de l'événement et la valeur de chaque champ de charge.  
  
## Personnaliser la visualisation des événements EventSource  
 Vous pouvez personnaliser la façon dont les événements EventSource sont affichés en ajoutant les champs appropriés à l'événement, comme décrit dans les sections suivantes.  
  
### Type de marqueur  
 Utilisez le champ `cvType`, un octet, pour vérifier le type de marqueur qui est utilisé pour représenter l'événement.  Voici les valeurs disponibles pour cvType :  
  
|Valeur cvType|Type de marqueur résultant|  
|-------------------|--------------------------------|  
|0|Message|  
|1|Début de l'étendue|  
|2|Fin de l'étendue|  
|3|Indicateur|  
|Toutes les autres valeurs|Message|  
  
### Importance  
 Vous pouvez utiliser le champ `cvImportance`, un octet, pour contrôler le paramètre d'importance pour un événement EventSource.  Toutefois, nous vous recommandons de contrôler l'importance affichée d'un événement à l'aide de son niveau.  
  
|valeur de cvImportance|Importance du Visualiseur Concurrentiel|  
|----------------------------|---------------------------------------------|  
|0|Normal|  
|1|Critical|  
|2|Élevée|  
|3|Élevée|  
|4|Normal|  
|5|Basse|  
|Toutes les autres valeurs|Basse|  
  
### Nom de la série  
 Utilisez le champ d'événement `cvSeries`, une chaîne, pour vérifier le nom de la série que le visualiseur d'accès concurrentiel donne à un événement EventSource.  
  
### Catégorie  
 Utilisez le champ `cvCategory`, un octet, pour vérifier la catégorie que le visualiseur d'accès concurrentiel donne à un événement EventSource.  
  
### Texte  
 Utilisez le champ `cvTextW`, une chaîne, pour vérifier la description que le visualiseur d'accès concurrentiel donne à un événement EventSource.  
  
### SpanID  
 Utilisez le champ cvSpanId, un entier, pour correspondre aux paires d'événements.  La valeur de chaque paire d'événements de début et de fin qui représentent une étendue doit être unique.  En général pour le code simultané, cela requiert l'utilisation des primitives de synchronisation telles que <xref:System.Threading.Interlocked.Exchange%2A> pour garantir que la clé \(la valeur utilisée pour CvSpanID\) est correcte.  
  
> [!NOTE]
>  L'utilisation de SpanID pour imbriquer des étendues, leur permettre de partiellement dépasser sur le même thread, ou leur permettre de démarrer sur un thread et de terminer sur un autre n'est pas prise en charge.  
  
## Voir aussi  
 [Marqueurs du visualiseur concurrentiel](../profiling/concurrency-visualizer-markers.md)