---
title: 'Comment : créer une bibliothèque d’activités | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8e3579061b65d142fdfb0cc992813ffc45663464
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508816"
---
# <a name="how-to-create-an-activity-library"></a>Procédure : créer une bibliothèque d'activités
Les activités personnalisées permettent de modeler vos processus d'entreprise particuliers dans un workflow. Le modèle Bibliothèque d'activités dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] a été fourni pour vous permettre de créer visuellement de telles activités personnalisées à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
### <a name="to-create-a-workflow-activity-library"></a>Pour créer une bibliothèque d'activités de workflow  
  
1.  Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  Sur le **fichier** menu, pointez sur **New**, puis sélectionnez **projet...** .  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans le **Types de projets** volet, sélectionnez **Workflow** à partir de le le **Visual C#** projets ou **Visual Basic** regroupements en fonction de votre langue de préférence.  
  
4.  Dans le **modèles** volet, sélectionnez **bibliothèque d’activités**.  
  
5.  Dans le **nom** zone, tapez un nom descriptif pour votre projet pour faciliter l’identification.  
  
6.  Dans le **emplacement** zone, tapez dans le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour naviguer jusqu'à lui.  
  
7.  Dans le **Solution** zone, tapez un nom descriptif pour votre solution, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous souhaitez ajouter une application de console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)], cliquez avec le bouton droit sur la solution dans **l’Explorateur de solutions**, puis sélectionnez **ajouter**, puis  **Nouveau projet...** Pour ouvrir le **nouveau projet** boîte de dialogue. Procédez comme décrit ci-dessus dans cette procédure.  
  
8.  Le modèle de projet crée une définition d'activité au format XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] s'ouvre et affiche la zone de dessin pour votre activité personnalisée.  
  
9. Faites glisser une activité à partir de la **boîte à outils** vers l’aire de conception pour l’inclure dans votre activité personnalisée.  
  
    > [!CAUTION]
    >  Une seule activité enfant est autorisée dans le corps de votre activité personnalisée ; toutefois, cette activité enfant peut être une activité composite, telle qu'une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Flowchart>.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : créer une activité](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [Création d’un projet de flux de travail](../workflow-designer/creating-a-workflow-project.md)