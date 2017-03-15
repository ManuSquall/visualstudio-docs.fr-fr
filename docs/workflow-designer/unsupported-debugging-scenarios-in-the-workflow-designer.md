---
title: "Sc&#233;narios de d&#233;bogage non pris en charge dans le Concepteur de workflow | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6adbe379-41d0-4681-9cd0-b91f187c3c2c
caps.latest.revision: 4
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 4
---
# Sc&#233;narios de d&#233;bogage non pris en charge dans le Concepteur de workflow
Le Concepteur de workflow du [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] a ajouté de nombreuses nouvelles fonctionnalités, mais certains scénarios de débogage ne sont pas encore pris en charge.Ce document présente en détail les scénarios de débogage du Concepteur de workflow qui ne sont pas pris en charge.  
  
-   Impossible de continuer l'exécution une fois que le code a été modifié.  
  
-   Impossible de continuer l'exécution à partir d'un point arbitraire dans le workflow \(Définir l'instruction suivante\).  
  
-   Impossible de continuer l'exécution tant que la ligne qui contient le curseur n'est pas atteinte \(Exécuter jusqu'au curseur\).  
  
-   Impossible d'utiliser le Concepteur de workflow pour déboguer les workflows créés à l'aide de code sans utiliser le concepteur.  
  
-   Impossible de déboguer les workflows créés dans les versions antérieures de [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le concepteur [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)].  
  
-   Impossible de définir des points d'arrêt sur les liaisons entre activités ou nœuds <xref:System.Activities.Statements.Flowchart>.  
  
-   Le Presse\-papiers n'est pas disponible lors du débogage.  
  
-   Les points d'arrêt ne sont pas conservés lorsque les activités sont copiées ou collées.  
  
-   Impossible de définir des points d'arrêt de workflow dans la fenêtre Pile des appels.  
  
-   Si vous créez des points d'arrêt dans le concepteur, les paramètres **Ligne** et **Caractère** de la boîte de dialogue **Nouveau point d'arrêt** sont utilisés.  
  
-   La fenêtre ou le menu contextuel Point d'arrêt ne prend pas en charge les colonnes ou options suivantes pour le débogage de flux de travail :  
  
    -   Condition  
  
    -   Nombre d'accès  
  
    -   Lorsqu'il est atteint  
  
    -   Fonction  
  
    -   Données  
  
    -   Processus  
  
    -   Atteindre le code machine