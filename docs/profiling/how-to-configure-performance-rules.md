---
title: "Comment&#160;: configurer les r&#232;gles de performance des outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.ruleseditor"
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Comment&#160;: configurer les r&#232;gles de performance des outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les avertissements de performance des outils de profilage Visual Studio indiquent des problèmes dans une application profilée qui peuvent ralentir l'exécution du programme.  Les avertissements peuvent également indiquer que vous devrez peut\-être modifier des méthodes de collection pour collecter des données plus utiles.  Les avertissements de performance sont générés automatiquement dans une session de profilage et s'affichent dans la fenêtre **Liste d'erreurs** lorsqu'un fichier de données de profilage est ouvert dans l'IDE de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)].  Certains avertissements peuvent ne se pas s'appliquer aux scénarios qui vous intéressent et certains avertissements peuvent être déclenchés de manière inappropriée.  Vous pouvez configurer les avertissements sur les performances de manière à afficher ou masquer des avertissements spécifiques.  
  
### Pour configurer des avertissements sur les performances du profileur  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Développez **Outils d'analyse des performances**, puis cliquez sur **Règles**.  
  
3.  Pour activer ou désactiver un avertissement, activez ou désactivez la case à cocher en regard de l' **ID** et du nom de l'avertissement.  
  
4.  Pour spécifier le niveau d'avertissement d'une règle, cliquez sur la cellule **Action** située en regard de la règle, puis cliquez sur le niveau d'avertissement.  
  
    -   **Désactivé** \- désactive la règle \(cela revient à désactiver la case à cocher située en regard de l'ID de la règle\).  
  
    -   **Avertissement** \- affiche la règle sous forme d'avertissement.  
  
    -   **Erreur** \- arrête l'exécution du profilage et affiche la règle sous forme d'erreur.  
  
    -   **Informations** \- affiche la règle à titre d'information uniquement.