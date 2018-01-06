---
title: "Comment : créer des projets de Workflow (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 1f3dd415646f9205794ed51572ed9dbcfc5b45b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procédure : créer des projets de workflow (héritée)
Suivez ces étapes pour créer un projet [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]. Cette procédure utilise le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité fourni par [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].  
  
### <a name="to-create-a-workflow-project"></a>Pour créer un projet de workflow  
  
1.  Démarrez [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **nouveau**, puis sélectionnez **projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.  
  
    > [!NOTE]
    >  L’option par défaut dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] et elle n'utilise pas le concepteur hérité.  
  
4.  Dans le **Types de projets** volet, sélectionnez des projets Visual c# ou Visual Basic, puis **Workflow**.  
  
5.  Dans le **modèles** volet, sélectionnez un des modèles de projet installés :  
  
    -   Application console de workflow séquentiel  
  
    -   Bibliothèque de workflow séquentiel  
  
    -   Bibliothèque d'activité de workflow  
  
    -   Application console de workflow d'ordinateur d'état  
  
    -   Bibliothèque de workflows d'ordinateur d'état  
  
    -   Projet de workflow vide  
  
6.  Dans le **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.  
  
7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur la zone **Parcourir** pour accéder au répertoire.  
  
     Si vous souhaitez un répertoire de solution créé pour le projet, sélectionnez le **créer le répertoire pour la solution** case à cocher et entrez un nom dans la **nom de la Solution** boîte.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)