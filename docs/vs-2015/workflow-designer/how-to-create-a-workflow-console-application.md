---
title: 'Comment : créer une Application de Console de flux de travail | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8a6b38f6026e7a9bba1e668f47a37b32feaa2b7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47493206"
---
# <a name="how-to-create-a-workflow-console-application"></a>Procédure : créer une application console de workflow
[!INCLUDE[wf](../includes/wf-md.md)] vous permet de créer des workflows pour l'exécution de processus système ou humains. [!INCLUDE[wfd1](../includes/wfd1-md.md)] fournit l'aire de conception pour la création de ces workflows. Le [!INCLUDE[wfd2](../includes/wfd2-md.md)] peut être utilisé pour créer des workflows depuis [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou il peut être intégré dans d'autres applications pour réhéberger le concepteur.  
  
 Cette rubrique décrit comment utiliser le [!INCLUDE[wfd2](../includes/wfd2-md.md)] dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] pour créer un workflow dans une application console.  
  
### <a name="to-create-a-workflow-console-application"></a>Pour créer une application console de workflow  
  
1.  Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **New**, puis sélectionnez **projet...** .  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le **modèles installés** volet, sélectionnez **Workflow** à partir de le le **Visual C#** ou **Visual Basic** groupements, selon votre langue de préférence.  
  
4.  Dans le volet central, sélectionnez **Application Console de Workflow**.  
  
5.  Dans le **nom** , entrez un nom descriptif pour votre projet pour faciliter l’identification.  
  
6.  Dans le **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet, ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
7.  Dans le **Solution** , entrez le nom de la nouvelle solution. Cliquez sur **OK** pour créer l’application.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application de console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet...** Pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition de workflow en XAML et la définition d'application console se trouve dans le code source. [!INCLUDE[wfd2](../includes/wfd2-md.md)] s'ouvre et affiche la zone de dessin du workflow que vous avez créé.  
  
9. Pour composer un workflow, faites glisser les activités ou autres éléments de flux de travail à partir de la **boîte à outils** vers l’aire de conception dans votre flux de travail.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)