---
title: "Proc&#233;dure&#160;: utiliser l&#39;exploration &#224; l&#39;aide de la barre de navigation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: utiliser l&#39;exploration &#224; l&#39;aide de la barre de navigation
Il existe trois méthodes principales pour modifier l'ensemble des activités affichées dans [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] :  
  
1.  Double\-cliquez pour descendre dans la hiérarchie et accéder à une activité enfant.  
  
2.  Cliquez sur un bouton de la barre de navigation pour accéder à une activité ancêtre.  
  
3.  Développez ou réduisez les activités sur place.  
  
### Utilisation de l'exploration à l'aide de la barre de navigation  
  
1.  Double\-cliquez sur une activité de [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] pour qu'elle remplace l'activité racine.L'activité sur laquelle vous avez cliqué est alors entièrement développée à la racine et ses ancêtres sont affichés dans la barre de navigation.Cette procédure est parfois appelée exploration avant ou arrière d'une activité.  
  
2.  Pour accéder à un ancêtre de l'activité racine actuelle, cliquez sur l'activité dans la barre de navigation.  
  
### Développement ou réduction d'une activité sur place  
  
1.  Cliquer sur les chevrons sur une activité se développe ou réduit l'activité en place.  
  
2.  Lorsque l'état de développement est modifié en cliquant sur le bouton, le nouvel état de développement est enregistré en XAML.  
  
    > [!WARNING]
    >  Toutes les activités ne peuvent pas être développées sur place.Il existe deux cas pour lesquels il est impossible de développer une activité sur place : soit le parent de l'activité n'autorise pas ses enfants à être développés sur place, \(par exemple, les activités d'un organigramme ne peuvent pas être développées sur place\), soit le concepteur d'activités lui\-même ne peut pas être développé sur place.Bien que ce ne soit pas le cas des concepteurs d'activités inclus dans [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], certaines activités personnalisées peuvent présenter ce comportement.  
  
### Développement ou réduction de toutes les activités  
  
1.  Utilisez les boutons **Développer tout** et **Réduire tout** dans l'interface utilisateur pour développer ou réduire toutes les activités sous la racine de la barre de navigation actuelle.Notez que Développer tout et Réduire tout sont des états globaux.Cela signifie que lorsque vous modifiez l'activité racine en utilisant l'exploration à l'aide de la barre de navigation, l'état Développer tout ou Réduire tout persiste jusqu'à ce que vous cliquiez sur **Restaurer**.  
  
2.  Une fois que l'état Développer tout ou Réduire tout est appliqué, vous pouvez cliquer sur le bouton **Restaurer** qui s'affiche pour revenir à l'état précédemment appliqué à chaque activité.  
  
    > [!WARNING]
    >  Si l'option de développement sur place est désactivée pour une activité, telle que <xref:System.Activities.Statements.Flowchart>, les fonctionnalités associées aux boutons **Développer tout** et **Réduire tout** sont désactivées sur le concepteur **Flowchart**.[!INCLUDE[crabout](../test/includes/crabout_md.md)] le concepteur **Organigramme**, consultez la rubrique [Organigramme](../workflow-designer/flowchart-activity-designer.md).  
  
    > [!WARNING]
    >  Le paramètre Développer tout a également un effet particulier sur les concepteurs d'activité **Switch** et **TryCatch**.Lorsque vous cliquez sur **Développer tout**, tous les switch cases et tous les blocs try\/catch\/finally sont affichés.Si sous cliquez sur **Restaurer** ou **Réduire tout**, ces concepteurs retrouvent leur état par défaut, à partir duquel vous pouvez cliquer sur un cas\/bloc individuel pour consulter son contenu.