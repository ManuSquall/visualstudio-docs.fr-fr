---
title: 'Procédure : Créer une bibliothèque d’activités de flux de travail (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activity library projects
- workflow activity libraries
- projects, workflow activity libraries
ms.assetid: fb5aa940-2ae8-4b52-b52c-51c20861a7b4
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9baa358c3728c6cbedc5f8768b29ba7efe64b399
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703295"
---
# <a name="how-to-create-a-workflow-activity-library-legacy"></a>Procédure : Créer une bibliothèque d’activités de workflow (héritée)
Suivez ces étapes pour créer un projet de bibliothèque d'activités de workflow à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-workflow-activity-library-project"></a>Pour créer un projet de bibliothèque d'activité de workflow  
  
1. Démarrez Visual Studio.  
  
2. Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3. Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.  
  
    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.  
  
4. Dans le **Types de projets** volet, sélectionnez Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.  
  
5. Dans le **modèles** volet, sélectionnez **Workflow Activity Library**.  
  
6. Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.  
  
7. Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
     Si vous souhaitez un répertoire de solution créé pour le projet, sélectionnez le **créer le répertoire pour la solution** case et entrez un nom dans la **nom de la Solution** boîte.  
  
8. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)   
 [À l’aide du Concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)   
 [Activités de flux de travail hérité](../workflow-designer/legacy-workflow-activities.md)   
 [Développement d’activités de flux de travail](https://msdn.microsoft.com/19876dfc-dfa5-4d52-b1f5-1d087474cc52)   
 [Activités Windows Workflow Foundation](https://msdn.microsoft.com/192c4c1e-afb6-4f58-ab11-2b5bbbc2d2c0)