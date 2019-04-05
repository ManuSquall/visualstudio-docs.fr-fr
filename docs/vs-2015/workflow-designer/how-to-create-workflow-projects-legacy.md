---
title: 'Procédure : Créer des projets de flux de travail (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f9c67f16e81bd0176ec25aa490c2119267b94159
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938513"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procédure : Créer des projets de workflow (hérités)
Suivez ces étapes pour créer un projet [!INCLUDE[wf](../includes/wf-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Cette procédure utilise le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
### <a name="to-create-a-workflow-project"></a>Pour créer un projet de workflow  
  
1.  Démarrez [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].  
  
2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.  
  
    > [!NOTE]
    >  L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.  
  
4.  Dans le **Types de projets** volet, sélectionnez les projets Visual c# ou Visual Basic, puis **Workflow**.  
  
5.  Dans le **modèles** volet, sélectionnez un des modèles de projet installés :  
  
    -   Application console de workflow séquentiel  
  
    -   Bibliothèque de workflow séquentiel  
  
    -   Bibliothèque d'activité de workflow  
  
    -   Application console de workflow d'ordinateur d'état  
  
    -   Bibliothèque de workflows d'ordinateur d'état  
  
    -   Projet de workflow vide  
  
6.  Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.  
  
7.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur **Parcourir** pour accéder au répertoire.  
  
     Si vous souhaitez un répertoire de solution créé pour le projet, sélectionnez le **créer le répertoire pour la solution** case et entrez un nom dans la **nom de la Solution** boîte.  
  
8.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)