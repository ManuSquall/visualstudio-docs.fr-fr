---
title: 'Comment : créer des projets de flux de travail (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflow projects, creating
- projects, workflow
ms.assetid: 32299555-662c-469d-a90d-89f4700dc78c
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3cf68c1a28f662bfa4e271d3c402ef1c8946b6f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668676"
---
# <a name="how-to-create-workflow-projects-legacy"></a>Procédure : créer des projets de workflow (héritée)
Suivez ces étapes pour créer un projet [!INCLUDE[wf](../includes/wf-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]. Cette procédure utilise le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)].

### <a name="to-create-a-workflow-project"></a>Pour créer un projet de workflow

1. Démarrez [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)].

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Sélectionnez l’option **.NET Framework 3,0** ou l’option **.NET Framework 3,5** dans la liste déroulante en haut de la fenêtre **nouveau projet** pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.

4. Dans le volet **types de projets** , sélectionnez projets Visual C# ou Visual Basic projets, puis sélectionnez **flux de travail**.

5. Dans le volet **modèles** , sélectionnez l’un des modèles de projet installés :

    - Application console de workflow séquentiel

    - Bibliothèque de workflow séquentiel

    - Bibliothèque d'activité de workflow

    - Application console de workflow d'ordinateur d'état

    - Bibliothèque de workflows d'ordinateur d'état

    - Projet de workflow vide

6. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour accéder au répertoire.

     Si vous souhaitez créer un répertoire de solution pour le projet, activez la case à cocher **créer le répertoire pour la solution** et entrez un nom dans la zone nom de la **solution** .

8. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 [Création de projets de workflows hérités](../workflow-designer/creating-legacy-workflow-projects.md)