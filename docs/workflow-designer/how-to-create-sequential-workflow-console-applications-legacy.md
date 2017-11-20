---
title: "Comment : créer des Applications de Console de Workflow séquentiel (héritée) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7e9732334f422b4042f2cd581afaea06bf99ab16
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procédure : créer des applications console de workflow séquentiel (héritée)
Suivez ces étapes pour créer un projet d'application console de workflow séquentiel à l'aide du [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité fourni par [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Pour créer une application console de workflow séquentiel  
  
1.  Démarrez Visual Studio.  
  
2.  Sur le **fichier** menu, pointez sur **nouveau**, puis sélectionnez **projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.  
  
    > [!NOTE]
    >  L’option par défaut dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] et elle n'utilise pas le concepteur hérité.  
  
4.  Dans le **Types de projets** volet, sélectionnez projets Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.  
  
5.  Dans le **modèles** volet, sélectionnez **Application Console de Workflow séquentiel**.  
  
6.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.  
  
7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour naviguer jusqu'à lui.  
  
     Le Concepteur Windows Forms s'ouvre et affiche le Form1 du projet que vous avez créé.  
  
8.  Cliquez sur **OK**.  
  
     Le Concepteur de flux de travail s'ouvre et affiche l'aire de conception de workflow du workflow séquentiel créé.  
  
9. Faites glisser une activité de la **boîte à outils** vers l’aire de conception dans le **déposer l’activité** zone désignée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de Workflow hérité](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Développement de flux de travail](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)