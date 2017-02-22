---
title: "Proc&#233;dure&#160;: cr&#233;er des applications console de workflow s&#233;quentiel (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "applications console, workflow séquentiel"
  - "workflows séquentiels, applications console"
  - "workflows, applications console"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: cr&#233;er des applications console de workflow s&#233;quentiel (h&#233;rit&#233;e)
Suivez ces étapes pour créer un projet d'application console de workflow séquentiel à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité fourni par [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Pour créer une application console de workflow séquentiel  
  
1.  Lancez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez l'option **.NET Framework 3.0** ou **.NET Framework 3.5** dans la liste déroulante située en haut de la fenêtre **Nouveau projet** pour accéder au concepteur hérité.  
  
    > [!NOTE]
    >  L'option par défaut dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] est **.NET Framework 4**.Cette option permet de créer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] et elle n'utilise pas le concepteur hérité.  
  
4.  Dans le volet **Types de projet**, sélectionnez des projets Visual C\# ou Visual Basic \(dans **Autres langages**\), puis sélectionnez **Workflow**.  
  
5.  Dans le volet **Modèles**, sélectionnez **Application console de workflow séquentiel**.  
  
6.  Dans la zone **Nom**, entrez un nom descriptif associé à votre projet afin de faciliter son identification.  
  
7.  Dans la zone **Emplacement**, entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur le bouton **Parcourir** pour vous y rendre.  
  
     Le Concepteur Windows Forms s'ouvre et affiche le Form1 du projet que vous avez créé.  
  
8.  Cliquez sur **OK**.  
  
     Le Concepteur de flux de travail s'ouvre et affiche l'aire de conception de workflow du workflow séquentiel créé.  
  
9. Faites glisser une activité de la **Boîte à outils** vers l'aire de conception de la zone désignée de **déplacement d'activité**.  
  
## Voir aussi  
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/fr-fr/557bcb1f-a7ab-49f6-8df7-2706b7001301)