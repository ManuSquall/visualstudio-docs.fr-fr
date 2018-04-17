---
title: 'Comment : créer des projets de Workflow (hérité) | Documents Microsoft'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6fdbbd8a744c472c06fdefbdafce77679ec2c9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procédure : créer des projets de workflow (héritée)
Suivez ces étapes pour créer un projet [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]. Cette procédure utilise le Concepteur de flux de travail Windows hérité fourni par [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)].

### <a name="to-create-a-workflow-project"></a>Pour créer un projet de workflow

1.  Démarrez [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].

2.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s'affiche.

3.  Sélectionnez le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] qui ciblent le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] et elle n'utilise pas le concepteur hérité.

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

- [Création de projets de flux de travail hérités](../workflow-designer/creating-legacy-workflow-projects.md)