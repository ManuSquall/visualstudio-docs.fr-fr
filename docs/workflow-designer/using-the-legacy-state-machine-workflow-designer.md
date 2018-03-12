---
title: "L’aide du Concepteur de flux de travail de Machine état hérité | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 99be4338bcee9ffb5c7cb9cf28f6187128345f85
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Utilisation du Concepteur de Workflow d'ordinateur d'état hérité
Quand vous créez un nouveau projet de flux de travail de machine état dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], vous pouvez choisir d’utiliser le **Application Console de Workflow d’ordinateur état** ou le  **Bibliothèque de flux de travail de Machine d’état** modèle de projet hérité. Si vous choisissez l'un de ces modèles de projet d'ordinateur d'état, le concepteur d'ordinateurs d'état est présenté comme interface utilisateur de concepteur de workflow hérité. Pour plus d’informations sur les modèles de projet d’ordinateur état hérité, consultez [Comment : créer état Machine Applications Console de Workflow (héritée)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) et [Comment : créer une bibliothèque de flux de travail de Machine état (héritée)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Un workflow d'ordinateur d'état se compose d'un ensemble d'états. Un état représente un état initial. Chaque état peut recevoir certains événements spécifiques. En fonction d'un événement, une transition peut s'effectuer vers un autre état. Le workflow d'ordinateur d'état peut porter un état final. Lorsqu'une transition est effectuée vers l'état final, l'exécution de workflow prend fin.  
  
## <a name="state-machine-designer-views"></a>Vues du concepteur de workflow de l'ordinateur d'état  
 Le concepteur de l'ordinateur d'état est un concepteur de formes libres, ce qui signifie que les activités peuvent être déplacées librement sur l'aire de conception. Le Concepteur de machine d’état dispose de deux vues : *état* vue et *pilotée par événements* vue.  
  
 La vue d'état affiche les activités d'état et les activités pilotées par événements qui peuvent être contenues dans une activité d'état. Dans cette vue, les transitions d'un état à un autre sont représentées par des lignes qui relient l'activité pilotée par événements portant un état spécifique et l'activité portant un autre état. Vous pouvez également créer des transitions en dessinant vous-même cette ligne. Pour dessiner la transition, sélectionnez l'activité pilotée par événements, puis sélectionnez l'une des poignées de l'activité et faites-la glisser. Cette action permet de dessiner une ligne. Cette ligne est ensuite reliée à l'état cible, indiquant une transition entre les états.  
  
 Pour accéder à la vue des activités pilotées par événements, double-cliquez sur une activité pilotée par événements. Le concepteur qui apparaît s'apparente au concepteur de workflow séquentiel. Dans sa partie supérieure, une barre de navigation affiche la hiérarchie des activités jusqu'à l'activité pilotée par événements. Vous pouvez naviguer jusqu'à la vue d'état en cliquant sur un élément de la hiérarchie affichée. Si vous avez dessiné une transition d'un état vers un autre état dans la vue d'état, et si vous affichez la vue de l'activité pilotée par événements, une activité d'état définie est ajoutée à l'activité pilotée par événements. Si vous modifiez les propriétés de l'activité d'état définie, ces modifications sont répercutées dans la vue d'état.  
  
## <a name="state-machine-workflow-activities"></a>Activités de workflow de l'ordinateur d'état  
 Le tableau suivant décrit les activités clés utilisées dans un concepteur de workflow d'ordinateur d'état.  
  
|Nom de boîte à outils|Activité|Description|  
|------------------|--------------|-----------------|  
|**État**|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Représente un état dans une machine à États ; peut contenir supplémentaires **StateActivity** activités. Pour plus d’informations, consultez [à l’aide de l’activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Spécifie une transition vers un nouvel état. Pour plus d’informations, consultez [à l’aide de l’activité SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Elle est exécutée lorsqu'un état est entré ; elle peut contenir d'autres activités. Pour plus d’informations, consultez [à l’aide de l’activité StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Exécute les activités contenues en quittant un [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) activité. Pour plus d’informations, consultez [à l’aide de l’activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Utilisée pour des états pour lesquels un événement externe déclenche l'exécution. Le **EventDrivenActivity** activité doit avoir une activité qui implémente le [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interface comme première activité enfant. Pour plus d’informations, consultez [à l’aide de l’activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Le composant principal d’un workflow de machine d’état est la [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) activité. Puisque les événements sont capturés à différents points d’un workflow d’ordinateur d’état, des états différents sont entrés pour gérer les tâches associées aux événements. Pendant la durée de vie du workflow, ce dernier peut porter plusieurs états différents. Ces États se connectent entre eux à l’aide de la [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) activité.  
  
 Lorsque vous faites glisser une nouvelle **StateActivity** sur l’aire de conception de workflow, vous pouvez ajouter [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), ou une autre **StateActivity** activités en tant qu’activités enfants.  
  
> [!CAUTION]
>  Lorsque vous utilisez le Concepteur de flux de travail de machine état pour créer des workflows, vous devez analyser la structure du flux de travail que vous créez avec le **structure du Document** fenêtre d’affichage. La vue de la structure du workflow de machine d’état dans le **structure du Document** vue fenêtre reflète la disposition logique des activités dans le fichier de balisage de flux de travail. La disposition physique des activités de workflow, telles qu'elles apparaissent dans l'aire de conception, peut ne pas refléter la disposition logique des activités dans le fichier de balisage du workflow.  
>   
>  Pour ouvrir la **structure du Document** fenêtre, dans le **vue** menu, pointez sur **autres fenêtres**, puis sélectionnez **structure du Document**.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer des Applications de Console de Workflow de Machine d’état (héritée)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Comment : créer une bibliothèque de workflows d’ordinateur d’état (héritée)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Flux de travail de Machine à États](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Utilisation de l’activité StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Utilisation de l’activité StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Utilisation de l’activité StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Utilisation de l’activité SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Utilisation de l’activité EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)