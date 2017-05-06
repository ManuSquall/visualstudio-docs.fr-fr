---
title: "Comment&#160;: mapper des sch&#233;mas &#224; des documents Word dans Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "mappages (développement Office dans Visual Studio), schémas XML aux documents Word"
  - "Word (développement Office dans Visual Studio), mapper des schémas XML"
  - "schémas XML (développement Office dans Visual Studio), mapper"
ms.assetid: 9bfb3c7b-6392-45bd-b4c1-b2012b9ded69
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Comment&#160;: mapper des sch&#233;mas &#224; des documents Word dans Visual Studio
  **important** les informations présentées dans cette rubrique concernant Microsoft Word est présenté exclusivement pour l'avantage et l'utilisation des personnes et organisations qui se trouvent en dehors de les états\-unis et de ses territoires ou qui utilisent, ou de développer des programmes qui s'exécutent sur, les produits Microsoft Word qui ont été autorisés par Microsoft avant janvier 2010, lorsque Microsoft a supprimé une implémentation de fonctionnalités spécifique liée à une personnalisée XML Microsoft Word.  Ces informations liées à Microsoft Word ne peuvent pas être lues ou utilisées par des individus ou des organisations se trouvant aux États\-Unis ou dans ses territoires qui utilisent, ou développent des programmes exécutés avec, des produits Microsoft Word dont la licence Microsoft est postérieure à janvier 2010 ; ces produits n'auront pas le même comportement que ceux dont la licence est antérieure à cette date ou ceux qui ont été achetés ou ont bénéficié d'une licence d'utilisation en dehors des États\-Unis.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Vous pouvez mapper un schéma XML à un document ouvert dans Visual Studio.  Pour ce faire, vous devez utiliser les mêmes outils Microsoft Office Word que lorsque le document est ouvert en dehors de Visual Studio.  Le projet Office crée les mêmes objets que vous mappiez le schéma au document avant ou après avoir créé votre solution Word.  
  
### Pour mapper un schéma XML à un document Word dans Visual Studio  
  
1.  Ouvrez le document ou projet de modèle Word dans Visual Studio.  
  
2.  Cliquez dans le document pour déplacer le focus sur le concepteur.  
  
3.  Dans le ruban, cliquez sur l'onglet **Développeur**.  
  
    > [!NOTE]  
    >  Si l'onglet **Développeur** n'est pas visible, vous devez préalablement l'afficher.  Pour plus d’informations, consultez [Comment : afficher l'onglet Développeur sur le ruban](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Dans le groupe **XML**, cliquez sur **Schéma**.  
  
     La boîte de dialogue **Modèles et compléments** s'ouvre.  
  
5.  Cliquez sur l'onglet **Schéma XML**.  
  
6.  Cliquez sur **Ajouter un schéma**.  
  
     La boîte de dialogue **Ajouter un schéma** s'affiche.  
  
7.  Recherchez votre fichier schéma, sélectionnez\-le, puis cliquez sur **Ouvrir**.  
  
     La boîte de dialogue **Paramètres du schéma** s'affiche.  
  
8.  Assignez un alias ou cliquez sur **OK** pour ajouter le schéma sans alias.  
  
9. Cliquez sur **OK**.  
  
     La fenêtre **Structure XML** s'affiche.  
  
10. Faites glisser les éléments de la fenêtre **Structure XML** vers les endroits de votre document où vous souhaitez que les contrôles correspondants soient créés.  
  
## Voir aussi  
 [Comment : mapper des schémas à des feuilles de calcul dans Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)   
 [Schémas et données XML dans les personnalisations au niveau du document](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  