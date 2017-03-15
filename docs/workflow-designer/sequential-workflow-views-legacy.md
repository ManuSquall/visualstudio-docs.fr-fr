---
title: "Vues de workflow s&#233;quentiel (h&#233;rit&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "vues de workflow séquentiel"
  - "workflows séquentiels, vues"
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Vues de workflow s&#233;quentiel (h&#233;rit&#233;es)
[!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] fournit un [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui peut être utilisé pour cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] permet de créer graphiquement des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] grâce à l'interface utilisateur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que vous connaissez bien.Les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] sont composées d'étapes du processus de flux de travail appelées activités.Pour créer un workflow, composez des activités sur l'aire de conception en faisant glisser leurs concepteurs d'activités respectifs de la **boîte à outils** sur l'aire de conception.  
  
 Lorsque vous créez un workflow séquentiel, qui correspond à un [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040), trois vues du workflow sont disponibles.Ces vues sont accessibles dans le menu **Workflow** et dans le menu contextuel sur l'aire de conception.  
  
 Le tableau suivant contient le nom et la description de chaque vue.  
  
|Option de menu\/d'onglet|Description|  
|------------------------------|-----------------|  
|**Afficher le workflow séquentiel**|Cliquez avec le bouton droit sur l'aire de conception et sélectionnez l'option **Afficher le workflow séquentiel** dans le menu contextuel pour afficher la vue **Workflow séquentiel**, qui affiche la représentation graphique basée sur les activités du workflow séquentiel.Vous pouvez également sélectionner **Afficher le workflow séquentiel** dans le menu **Workflow**.|  
|**Afficher le gestionnaire d'annulation**|Cliquez avec le bouton droit sur l'aire de conception et sélectionnez l'option **Afficher le gestionnaire d'annulation** dans le menu contextuel pour afficher la vue **Workflow séquentiel**, qui affiche l'activité [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) associée au workflow.Vous pouvez également sélectionner **Afficher le gestionnaire d'annulation** dans le menu **Workflow**.|  
|**Afficher le gestionnaire d'erreur**|Cliquez avec le bouton droit sur l'aire de conception et sélectionnez l'option **Afficher le gestionnaire d'erreur** dans le menu contextuel pour afficher la vue **Erreurs**, qui affiche l'activité [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) associée au workflow.Vous pouvez également sélectionner **Afficher les gestionnaires d'erreur** dans le menu **Workflow**.|  
  
 Pour plus d'informations sur des vues similaires, consultez [Vues d'activité \(héritées\)](../workflow-designer/activity-views-legacy.md).  
  
## Voir aussi  
 [Vues d'activité \(héritées\)](../workflow-designer/activity-views-legacy.md)   
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Modes de création de workflows](http://go.microsoft.com/fwlink?LinkID=65014)