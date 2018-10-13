---
title: 'Comment : utiliser l’arborescence de Navigation | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 19f9add69f8746962e6ed0ef9e4beea0f7ba37ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259028"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Procédure : utiliser l'exploration à l'aide de la barre de navigation
Il existe trois méthodes principales pour modifier l'ensemble des activités affichées dans [!INCLUDE[wfd1](../includes/wfd1-md.md)] :  
  
1.  Double-cliquez pour descendre dans la hiérarchie et accéder à une activité enfant.  
  
2.  Cliquez sur un bouton de la barre de navigation pour accéder à une activité ancêtre.  
  
3.  Développez ou réduisez les activités sur place.  
  
### <a name="using-breadcrumb-navigation"></a>Utilisation de l'exploration à l'aide de la barre de navigation  
  
1.  Double-cliquez sur une activité de [!INCLUDE[wfd2](../includes/wfd2-md.md)] pour qu'elle remplace l'activité racine. L'activité sur laquelle vous avez cliqué est alors entièrement développée à la racine et ses ancêtres sont affichés dans la barre de navigation. Cette procédure est parfois appelée exploration avant ou arrière d'une activité.  
  
2.  Pour accéder à un ancêtre de l'activité racine actuelle, cliquez sur l'activité dans la barre de navigation.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Développement ou réduction d'une activité sur place  
  
1.  Cliquer sur les chevrons sur une activité se développe ou réduit l'activité en place.  
  
2.  Lorsque l'état de développement est modifié en cliquant sur le bouton, le nouvel état de développement est enregistré en XAML.  
  
    > [!WARNING]
    >  Toutes les activités ne peuvent pas être développées sur place. Il existe deux cas pour lesquels il est impossible de développer une activité sur place : soit le parent de l'activité n'autorise pas ses enfants à être développés sur place, (par exemple, les activités d'un organigramme ne peuvent pas être développées sur place), soit le concepteur d'activités lui-même ne peut pas être développé sur place. Bien que ce ne soit pas le cas des concepteurs d'activités inclus dans [!INCLUDE[wfd2](../includes/wfd2-md.md)], certaines activités personnalisées peuvent présenter ce comportement.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Développement ou réduction de toutes les activités  
  
1.  Utilisez le **développer tout** et **réduire tout** boutons dans l’interface utilisateur pour développer ou réduire toutes les activités sous la racine actuelle de la barre de navigation. Notez que Développer tout et Réduire tout sont des états globaux. Cela signifie que lorsque vous modifiez l’activité racine à l’aide de la navigation hiérarchique, le développer tout état ou réduisez tout persiste jusqu'à ce que vous cliquiez **restaurer**.  
  
2.  Une fois que vous avez appliqué une développer tout ou réduisez tous les États, vous pouvez cliquer sur le **restaurer** bouton qui apparaît à revenir en arrière pour examiner l’état précédemment appliqué à chaque activité.  
  
    > [!WARNING]
    >  Si une activité, tel que <xref:System.Activities.Statements.Flowchart>, a choisi de développement en place, les fonctionnalités associées du **développer tout** et **réduire tout** boutons sont désactivé sur le **organigramme**  concepteur. [!INCLUDE[crabout](../includes/crabout-md.md)] le **organigramme** concepteur, consultez le [organigramme](../workflow-designer/flowchart-activity-designer.md) rubrique.  
  
    > [!WARNING]
    >  Développer tout a également un effet spécial **commutateur** et **TryCatch** concepteurs d’activités. Lorsque vous cliquez sur **développer tout**, tous les cas de commutateur et tous les blocs try/catch/finally sont affichés. En cliquant sur **restaurer** ou **réduire tout** ces concepteurs retrouvent leur état par défaut, à partir de laquelle vous pouvez cliquer sur un cas/bloc individuel pour afficher son contenu.