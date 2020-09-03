---
title: 'Comment : créer une bibliothèque de concepteur d’activités | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 5b62e092-63b3-462d-9d77-fb112482f45d
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 63404d3d81c44ac4b8308d949cdb87df419f2e04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662871"
---
# <a name="how-to-create-an-activity-designer-library"></a>Procédure : créer une bibliothèque ActivityDesigner
Les concepteurs d'activités personnalisées vous permettent de créer une interface utilisateur pour une activité standard ou personnalisée. Vous contrôlez la complexité de l'interface utilisateur et avez la possibilité de créer plusieurs concepteurs d'activités pour une activité. Ce scénario vous permet de créer des concepteurs adaptés pour plusieurs audiences.

### <a name="to-create-an-activity-designer-library"></a>Pour créer une bibliothèque ActivityDesigner

1. Démarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Dans le menu **fichier** , pointez sur **nouveau**, puis sélectionnez **projet...** pour ouvrir la boîte de dialogue **nouveau projet** .

3. Dans le volet **types de projets** , sélectionnez flux de **travail** à partir des regroupements **Visual C#** ou **Visual Basic** en fonction de votre langue par défaut.

4. Dans le volet **modèles** , sélectionnez **bibliothèque du concepteur d’activités**.

5. Dans la zone **nom** , entrez un nom descriptif pour votre projet afin de faciliter son identification.

6. Dans la zone **emplacement** , entrez le répertoire dans lequel vous souhaitez enregistrer votre projet ou cliquez sur **Parcourir** pour y accéder.

7. Dans la zone **solution** , tapez un nom descriptif pour votre solution, puis cliquez sur **OK**.

    > [!NOTE]
    > Si vous souhaitez ajouter une application console de workflow à une solution existante, ouvrez cette solution dans [!INCLUDE[vs2010](../includes/vs2010-md.md)] , cliquez avec le bouton droit sur la solution dans **Explorateur de solutions**, puis sélectionnez **Ajouter**, puis **nouveau projet...** pour ouvrir la boîte de dialogue **nouveau projet** . Procédez comme décrit ci-dessus dans cette procédure.

8. Le modèle de projet crée une définition de concepteur d'activités en XAML et le fichier d'implémentation code-behind dans le code source. [!INCLUDE[wfd1](../includes/wfd1-md.md)] s'ouvre et affiche la zone de dessin pour votre concepteur d'activités.

9. Faites glisser les [!INCLUDE[avalon1](../includes/avalon1-md.md)] contrôles de la **boîte à outils** vers l’aire de conception afin de les utiliser dans votre concepteur d’activités personnalisées.  Pour obtenir un exemple d’implémentation d’un concepteur d’activités personnalisé, consultez [Comment : créer un concepteur d’activités personnalisées](https://msdn.microsoft.com/library/2f3aade6-facc-44ef-9657-a407ef8b9b31).

    > [!WARNING]
    > Les concepteurs d’activités personnalisées peuvent être utilisés pour les activités personnalisées, ainsi que pour les activités par défaut [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .

## <a name="see-also"></a>Voir aussi
 [Création d'un projet de workflow](../workflow-designer/creating-a-workflow-project.md)