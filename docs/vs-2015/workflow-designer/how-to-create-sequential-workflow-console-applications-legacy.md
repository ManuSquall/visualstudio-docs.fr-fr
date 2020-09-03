---
title: 'Comment : créer des applications console de workflow séquentiel (hérité) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662729"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procédure : créer des applications console de workflow séquentiel (héritée)
Suivez ces étapes pour créer un projet d'application console de workflow séquentiel à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Pour créer une application console de workflow séquentiel

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Sélectionnez l’option **.NET Framework 3,0** ou l’option **.NET Framework 3,5** dans la liste déroulante en haut de la fenêtre **nouveau projet** pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.

4. Dans le volet **types de projets** , sélectionnez projets Visual C# ou Visual Basic projets (dans **autres langages**), puis sélectionnez **flux de travail**.

5. Dans le volet **modèles** , sélectionnez **application console de workflow séquentiel**.

6. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

     Le Concepteur Windows Forms s'ouvre et affiche le Form1 du projet que vous avez créé.

8. Cliquez sur **OK**.

     Le Concepteur de flux de travail s'ouvre et affiche l'aire de conception de workflow du workflow séquentiel créé.

9. Faites glisser une activité de la **boîte à outils** vers l’aire de conception dans la zone désignée de l' **activité de dépôt** .

## <a name="see-also"></a>Voir aussi
 [Création de projets de workflow hérités](../workflow-designer/creating-legacy-workflow-projects.md) [développement de workflows](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)