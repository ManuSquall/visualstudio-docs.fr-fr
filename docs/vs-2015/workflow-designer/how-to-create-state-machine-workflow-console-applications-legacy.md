---
title: 'Comment : créer des applications console de workflow d’ordinateur d’État (hérité) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- console applications, state machine workflows
- state machine workflow console applications
- state machine workflows, console applicationa
ms.assetid: d6170b5d-5d4f-48e1-8257-c78604f27eac
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48c7e06c2cb0e59de754b1ab36b693c4c9872985
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662717"
---
# <a name="how-to-create-state-machine-workflow-console-applications-legacy"></a>Procédure : créer des applications console de workflow d'ordinateur d'état (héritée)
Suivez ces étapes pour créer un projet d'application console de workflow d'ordinateur d'état à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-state-machine-application-project"></a>Pour créer un projet d'application d'ordinateur d'état

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Sélectionnez l’option **.NET Framework 3,0** ou l’option **.NET Framework 3,5** dans la liste déroulante en haut de la fenêtre **nouveau projet** pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.

4. Dans le volet **types de projets** , sélectionnez Visual C# ou Visual Basic (dans **autres langages**), puis sélectionnez **flux de travail**.

5. Dans le volet **modèles** , sélectionnez **application console de workflow**de l’ordinateur d’État.

6. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

     Si vous souhaitez créer un répertoire de solution pour le projet, activez la case à cocher **créer le répertoire pour la solution** et entrez un nom dans la zone nom de la **solution** .

8. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 [Création de projets de workflow hérités](../workflow-designer/creating-legacy-workflow-projects.md) [Comment : créer une bibliothèque de workflows d’ordinateur d’État (héritée)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)