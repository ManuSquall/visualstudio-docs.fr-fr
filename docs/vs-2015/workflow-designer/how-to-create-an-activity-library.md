---
title: 'Comment : créer une bibliothèque d’activités | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9dec73d392dc6af74e5daef99bd6d306f7d58409
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662754"
---
# <a name="how-to-create-an-activity-library"></a>Procédure : créer une bibliothèque d'activités
Les activités personnalisées permettent de modeler vos processus d'entreprise particuliers dans un workflow. Le modèle Bibliothèque d'activités dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] a été fourni pour vous permettre de créer visuellement de telles activités personnalisées à l'aide du [!INCLUDE[wfd1](../includes/wfd1-md.md)].

### <a name="to-create-a-workflow-activity-library"></a>Pour créer une bibliothèque d'activités de workflow

1. Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Dans le menu **fichier** , pointez sur **nouveau**, puis sélectionnez **projet...**.

     La boîte de dialogue **Nouveau projet** s’affiche.

3. Dans le volet **types de projets** , sélectionnez flux de **travail** à partir des projets **Visual C#** ou **Visual Basic** regroupements en fonction de vos préférences linguistiques.

4. Dans le volet **modèles** , sélectionnez **bibliothèque d’activités**.

5. Dans la zone **nom** , tapez un nom descriptif pour votre projet afin de faciliter son identification.

6. Dans la zone **emplacement** , tapez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

7. Dans la zone **solution** , tapez un nom descriptif pour votre solution, puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] , cliquez avec le bouton droit sur la solution dans **Explorateur de solutions**, puis sélectionnez **Ajouter**, puis **nouveau projet...** pour ouvrir la boîte de dialogue **nouveau projet** . Procédez comme décrit ci-dessus dans cette procédure.

8. Le modèle de projet crée une définition d'activité au format XAML. [!INCLUDE[wfd1](../includes/wfd1-md.md)] s'ouvre et affiche la zone de dessin pour votre activité personnalisée.

9. Faites glisser une activité de la **boîte à outils** vers l’aire de conception pour l’inclure dans votre activité personnalisée.

    > [!CAUTION]
    > Une seule activité enfant est autorisée dans le corps de votre activité personnalisée ; toutefois, cette activité enfant peut être une activité composite, telle qu'une activité <xref:System.Activities.Statements.Sequence> ou une activité <xref:System.Activities.Statements.Flowchart>.

## <a name="see-also"></a>Voir aussi
 [Comment : créer une activité](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [créant un projet de workflow](../workflow-designer/creating-a-workflow-project.md)