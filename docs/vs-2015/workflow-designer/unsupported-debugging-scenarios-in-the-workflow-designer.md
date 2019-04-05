---
title: Non pris en charge les scénarios dans le Concepteur de flux de travail de débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2f9799aa821c2281c8d7889009871e28a72dd5f6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58951964"
---
# <a name="unsupported-debugging-scenarios-in-the-workflow-designer"></a>Scénarios de débogage non pris en charge dans le Concepteur de workflow
Le Concepteur de workflow du [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] a ajouté de nombreuses nouvelles fonctionnalités, mais certains scénarios de débogage ne sont pas encore pris en charge. Ce document présente en détail les scénarios de débogage du Concepteur de workflow qui ne sont pas pris en charge.  
  
-   Impossible de continuer l'exécution une fois que le code a été modifié.  
  
-   Impossible de continuer l'exécution à partir d'un point arbitraire dans le workflow (Définir l'instruction suivante).  
  
-   Impossible de continuer l'exécution tant que la ligne qui contient le curseur n'est pas atteinte (Exécuter jusqu'au curseur).  
  
-   Impossible d'utiliser le Concepteur de workflow pour déboguer les workflows créés à l'aide de code sans utiliser le concepteur.  
  
-   Impossible de déboguer les workflows créés dans les versions antérieures de [!INCLUDE[wf](../includes/wf-md.md)] dans le concepteur [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].  
  
-   Impossible de définir des points d'arrêt sur les liaisons entre activités ou nœuds <xref:System.Activities.Statements.Flowchart>.  
  
-   Le Presse-papiers n'est pas disponible lors du débogage.  
  
-   Les points d'arrêt ne sont pas conservés lorsque les activités sont copiées ou collées.  
  
-   Impossible de définir des points d'arrêt de workflow dans la fenêtre Pile des appels.  
  
-   Lors de la création des points d’arrêt dans le concepteur, le **ligne** et **caractère** paramètres dans le **nouveau point d’arrêt** boîte de dialogue ne sont pas utilisés.  
  
-   La fenêtre ou le menu contextuel Point d'arrêt ne prend pas en charge les colonnes ou options suivantes pour le débogage de flux de travail :  
  
    -   Condition  
  
    -   Nombre d’accès  
  
    -   Lorsqu'il est atteint  
  
    -   Fonction  
  
    -   Données  
  
    -   Process  
  
    -   Atteindre le code machine