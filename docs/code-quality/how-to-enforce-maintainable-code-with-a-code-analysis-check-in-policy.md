---
title: "Comment&#160;: appliquer du code facile &#224; maintenir avec une strat&#233;gie d’archivage de l’analyse du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "analyse du code, stratégies d’archivage"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: appliquer du code facile &#224; maintenir avec une strat&#233;gie d’archivage de l’analyse du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les développeurs peuvent utiliser l'outil Métrique du code pour mesurer la complexité et la facilité de maintenance de leur code, mais ne peuvent pas l'appeler dans le cadre d'une stratégie d'archivage.  Toutefois, une équipe peut activer des règles d'analyse du code afin de vérifier la conformité de son code avec les normes de la métrique du code et appliquer les règles à l'aide de stratégies d'archivage.  Pour plus d'informations sur la métrique du code, consultez [Valeurs de la métrique du code](../code-quality/code-metrics-values.md).  
  
 Les développeurs peuvent activer les règles de profondeur d'héritage, de couplage de classes, d'indice de maintenabilité et de complexité pour obtenir du code facile à maintenir à l'aide des stratégies d'archivage de l'analyse du code.  Ces quatre règles figurent toutes dans la catégorie « Règles de maintenance » de l'éditeur de stratégies d'analyse du code.  
  
 Les administrateurs du contrôle de version pour [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] peuvent ajouter les règles de maintenance de l'analyse du code aux exigences des stratégies d'archivage.  Pour ces stratégies d'archivage, les développeurs doivent exécuter l'analyse du code en fonction des modifications apportées aux règles avant de démarrer un archivage.  
  
### Pour ouvrir l'éditeur de stratégies d'analyse du code  
  
1.  Dans **Team Explorer**, cliquez avec le bouton droit sur le projet d'équipe, cliquez sur **Paramètres du projet d'équipe**, puis cliquez sur **Contrôle de source de données**.  
  
     La boîte de dialogue **Contrôle de source de données** s'affiche.  
  
2.  Sous l'onglet **Stratégie d'archivage**, cliquez sur **Ajouter**.  
  
     La boîte de dialogue **Ajouter une stratégie d'archivage** s'affiche.  
  
3.  Dans la liste **Stratégie d'archivage**, activez la case à cocher **Analyse du code**, puis cliquez sur **OK**.  
  
     La boîte de dialogue **Éditeur de stratégies d'analyse du code** s'affiche.  
  
### Pour activer les règles de maintenance de l'analyse du code  
  
1.  Dans la boîte de dialogue **Éditeur de stratégies d'analyse du code**, sous **Paramètres de règle**, développez le nœud **Règles de maintenance**.  
  
2.  Activez les cases à cocher pour les règles suivantes :  
  
    -   Profondeur d'héritage : **CA1501 AvoidExcessiveInheritance** \- Seuil : avertissement au\-dessus de 5 niveaux  
  
    -   Complexité : **CA1502 AvoidExcessiveComplexity** \- Seuil : avertissement au\-dessus de 25  
  
    -   Indice de maintenabilité : **CA1505 AvoidUnmaintainableCode** \- Seuil : avertissement en dessous de 20  
  
    -   Couplage de classes : **CA1506 AvoidExcessiveClassCoupling** \- Seuil : avertissement au\-dessus de 80 pour une classe et au\-dessus de 30 pour une méthode  
  
    -   De plus, si vous souhaitez qu'une violation de règle empêche une génération, activez la case à cocher **Traiter un avertissement comme une erreur** située en regard de la description de la règle.  
  
3.  Cliquez sur **OK**.  La nouvelle stratégie d'archivage s'applique désormais aux archivages ultérieurs.  
  
## Voir aussi  
 [Valeurs de la métrique du code](../code-quality/code-metrics-values.md)   
 [Création et utilisation de stratégies d'archivage de l'analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)