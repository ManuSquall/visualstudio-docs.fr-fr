---
title: 'Procédure : Créer des Applications de Console de Workflow séquentiel (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: aaa7288d46b57204a637dc81d1d8b943debd87fa
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63417456"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procédure : Créer des applications console de workflows séquentiels (héritées)
Suivez ces étapes pour créer un projet d'application console de workflow séquentiel à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Pour créer une application console de workflow séquentiel  
  
1. Démarrez Visual Studio.  
  
2. Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3. Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.  
  
    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.  
  
4. Dans le **Types de projets** volet, sélectionnez projets Visual c# ou Visual Basic (sous **autres langages**), puis sélectionnez **Workflow**.  
  
5. Dans le **modèles** volet, sélectionnez **Application Console de Workflow séquentiel**.  
  
6. Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.  
  
7. Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
     Le Concepteur Windows Forms s'ouvre et affiche le Form1 du projet que vous avez créé.  
  
8. Cliquez sur **OK**.  
  
     Le Concepteur de flux de travail s'ouvre et affiche l'aire de conception de workflow du workflow séquentiel créé.  
  
9. Faites glisser une activité à partir de la **boîte à outils** à l’aire de conception dans le **déposer l’activité** zone désignée.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Développement de Workflows](http://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)