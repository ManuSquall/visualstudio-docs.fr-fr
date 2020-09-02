---
title: 'Comment : créer une bibliothèque de workflows séquentiels (héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: adc2e71678e6892d12640a3153f24bfb90dfa429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663396"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Procédure : créer une bibliothèque de workflows séquentiels (héritée)
Suivez ces étapes pour créer un projet de bibliothèque de workflows séquentiels à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité fourni par [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-library-project"></a>Pour créer un projet de bibliothèque de workflow séquentiel

1. Démarrez Visual Studio.

2. Dans le menu **Fichier** , pointez sur **Nouveau**, puis sélectionnez **Projet**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Sélectionnez l’option **.NET Framework 3,0** ou l’option **.NET Framework 3,5** dans la liste déroulante en haut de la fenêtre **nouveau projet** pour accéder au concepteur hérité.

    > [!NOTE]
    > L’option par défaut dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] est **.NET Framework 4**. Cette option permet de créer des applications [!INCLUDE[wf](../includes/wf-md.md)] qui ciblent le [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] et elle n'utilise pas le concepteur hérité.

4. Dans le volet **types de projets** , sélectionnez Visual C# ou Visual Basic (dans **autres langages**), puis sélectionnez **flux de travail**.

5. Dans le volet **modèles** , sélectionnez **bibliothèque de workflows séquentiels**.

6. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

7. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

     Si vous souhaitez créer un répertoire de solution pour le projet, activez la case à cocher **créer le répertoire pour la solution** et entrez un nom dans la zone nom de la **solution** .

8. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi
 [Création de projets de workflow hérités](../workflow-designer/creating-legacy-workflow-projects.md) [styles de création de flux de travail](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739)