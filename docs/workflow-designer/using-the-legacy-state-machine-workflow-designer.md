---
title: "Utilisation du Concepteur de Workflow d&#39;ordinateur d&#39;&#233;tat h&#233;rit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "EventDrivenActivity (activité)"
  - "SetStateActivity (activité)"
  - "Concepteur de flux de travail de l'ordinateur d'état"
  - "workflows d'ordinateur d'état, activités"
  - "workflows d'ordinateur d'état, concepteur"
  - "StateActivity (activité)"
  - "StateFinalizationActivity (activité)"
  - "StateInitializationActivity (activité)"
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Utilisation du Concepteur de Workflow d&#39;ordinateur d&#39;&#233;tat h&#233;rit&#233;
Lorsque vous créez un projet de workflow d'ordinateur d'état dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], vous pouvez choisir d'utiliser l'**Application console de workflow d'ordinateur d'état** ou le modèle de projet hérité **Bibliothèque de workflows d'ordinateur d'état**.Si vous choisissez l'un de ces modèles de projet d'ordinateur d'état, le concepteur d'ordinateurs d'état est présenté comme interface utilisateur de concepteur de workflow hérité.Pour plus d'informations sur les modèles de projet d'ordinateur d'état hérités, consultez [Procédure : créer des applications console de workflow d'ordinateur d'état \(héritée\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md) et [Procédure : créer une bibliothèque de workflows d'ordinateur d'état \(héritée\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md).  
  
 Un workflow d'ordinateur d'état se compose d'un ensemble d'états.Un état représente un état initial.Chaque état peut recevoir certains événements spécifiques.En fonction d'un événement, une transition peut s'effectuer vers un autre état.Le workflow d'ordinateur d'état peut porter un état final.Lorsqu'une transition est effectuée vers l'état final, l'exécution de workflow prend fin.  
  
## Vues du concepteur de workflow de l'ordinateur d'état  
 Le concepteur de l'ordinateur d'état est un concepteur de formes libres, ce qui signifie que les activités peuvent être déplacées librement sur l'aire de conception.Le concepteur de l'ordinateur d'état dispose de deux vues \(la vue *d'état* et la vue *pilotée par événements*.  
  
 La vue d'état affiche les activités d'état et les activités pilotées par événements qui peuvent être contenues dans une activité d'état.Dans cette vue, les transitions d'un état à un autre sont représentées par des lignes qui relient l'activité pilotée par événements portant un état spécifique et l'activité portant un autre état.Vous pouvez également créer des transitions en dessinant vous\-même cette ligne.Pour dessiner la transition, sélectionnez l'activité pilotée par événements, puis sélectionnez l'une des poignées de l'activité et faites\-la glisser.Cette action permet de dessiner une ligne.Cette ligne est ensuite reliée à l'état cible, indiquant une transition entre les états.  
  
 Pour accéder à la vue des activités pilotées par événements, double\-cliquez sur une activité pilotée par événements.Le concepteur qui apparaît s'apparente au concepteur de workflow séquentiel.Dans sa partie supérieure, une barre de navigation affiche la hiérarchie des activités jusqu'à l'activité pilotée par événements.Vous pouvez naviguer jusqu'à la vue d'état en cliquant sur un élément de la hiérarchie affichée.Si vous avez dessiné une transition d'un état vers un autre état dans la vue d'état, et si vous affichez la vue de l'activité pilotée par événements, une activité d'état définie est ajoutée à l'activité pilotée par événements.Si vous modifiez les propriétés de l'activité d'état définie, ces modifications sont répercutées dans la vue d'état.  
  
## Activités de workflow de l'ordinateur d'état  
 Le tableau suivant décrit les activités clés utilisées dans un concepteur de workflow d'ordinateur d'état.  
  
|Nom de boîte à outils|Activité|Description|  
|---------------------------|--------------|-----------------|  
|**État**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Représente un état présent au sein d'un ordinateur d'état pouvant contenir des activités **StateActivity** supplémentaires.Pour plus d'informations, consultez [Utilisation de l'activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083) \(page pouvant être en anglais\).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Spécifie une transition vers un nouvel état.Pour plus d'informations, consultez [Utilisation de l'activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65082) \(page pouvant être en anglais\).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Elle est exécutée lorsqu'un état est entré ; elle peut contenir d'autres activités.Pour plus d'informations, consultez [Utilisation de l'activité StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006) \(page pouvant être en anglais\).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Elle exécute les activités contenues lorsqu'une activité [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) prend fin.Pour plus d'informations, consultez [Utilisation de l'activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008) \(page pouvant être en anglais\).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Utilisé pour des états pour lesquels un événement externe déclenche l'exécution.L'activité **EventDrivenActivity** doit contenir une activité qui implémente l'interface [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) comme première activité enfant.Pour plus d'informations, consultez [Utilisation de l'activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068) \(page pouvant être en anglais\).|  
  
 Le composant principal d'un workflow d'ordinateur d'état est l'activité [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042).Puisque les événements sont capturés à différents points d'un workflow d'ordinateur d'état, des états différents sont entrés pour gérer les tâches associées aux événements.Pendant la durée de vie du workflow, ce dernier peut porter plusieurs états différents.Ces états sont reliés via l'activité [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041).  
  
 Lorsque vous faites glisser un nouveau **StateActivity** sur l'aire de conception de workflow, vous pouvez ajouter des activités [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), ou encore d'autres activités **StateActivity** en tant qu'activités enfants.  
  
> [!CAUTION]
>  Lorsque vous utilisez le concepteur de workflow d'ordinateur d'état pour créer des workflows, vous devez surveiller la structure du workflow que vous concevez à l'aide de la fenêtre **Structure du document**.La vue de la structure du workflow d'ordinateur d'état dans la fenêtre **Structure du document** reflète la disposition logique des activités dans le fichier de balisage du workflow.La disposition physique des activités de workflow, telles qu'elles apparaissent dans l'aire de conception, peut ne pas refléter la disposition logique des activités dans le fichier de balisage du workflow.  
>   
>  Pour ouvrir la fenêtre **Structure du document**, dans le menu **Affichage**, pointez sur **Autres fenêtres**, puis sélectionnez **Structure du document**.  
  
## Voir aussi  
 [Procédure : créer des applications console de workflow d'ordinateur d'état \(héritée\)](../Topic/How%20to:%20Create%20State%20Machine%20Workflow%20Console%20Applications%20\(Legacy\).md)   
 [Procédure : créer une bibliothèque de workflows d'ordinateur d'état \(héritée\)](../Topic/How%20to:%20Create%20a%20State%20Machine%20Workflow%20Library%20\(Legacy\).md)   
 [Workflows d'ordinateur d'état](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Utilisation de l'activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Utilisation de l'activité StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Utilisation de l'activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Utilisation de l'activité SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Utilisation de l'activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)