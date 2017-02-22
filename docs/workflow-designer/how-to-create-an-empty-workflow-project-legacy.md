---
title: "Proc&#233;dure&#160;: cr&#233;er un projet de workflow vide (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "projets de workflow vides"
  - "projets, workflow vide"
  - "workflows, projets de workflow vides"
ms.assetid: f81b9cf2-9adb-47a2-936b-cb1851614e19
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: cr&#233;er un projet de workflow vide (h&#233;rit&#233;e)
Suivez ces étapes pour créer un projet de workflow vide à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité fourni par [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### Pour créer un projet de workflow vide  
  
1.  Lancez Visual Studio.  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez l'option **.NET Framework 3.0** ou **.NET Framework 3.5** dans la liste déroulante située en haut de la fenêtre **Nouveau projet** pour accéder au concepteur hérité.  
  
    > [!NOTE]
    >  L'option par défaut dans [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] est **.NET Framework 4**.Cette option permet de créer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] et elle n'utilise pas le concepteur hérité.  
  
4.  Dans le volet **Types de projet**, sélectionnez Visual C\# ou Visual Basic \(dans **Autres langages**\), puis **Workflow**.  
  
5.  Dans le volet **Modèles**, sélectionnez **Projet de workflow**.  
  
6.  Dans la zone **Nom**, entrez un nom descriptif associé à votre projet afin de faciliter son identification.  
  
7.  Dans la zone **Emplacement**, entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur le bouton **Parcourir** pour vous y rendre.  
  
     Si vous souhaitez créer un répertoire de solution pour le projet, activez la case à cocher **Créer le répertoire pour la solution** et entrez un nom dans la zone **Nom de solution**.  
  
8.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)