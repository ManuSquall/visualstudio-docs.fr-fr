---
title: 'Comment : ajouter des activités à la boîte à outils | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8fc2af704ab587480913c51cdbc593e6cc0f483a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663464"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Comment : ajouter des activités à la boîte à outils
Les activités peuvent être ajoutées à la **boîte à outils** dans votre solution de différentes manières. Vous pouvez les ajouter à partir de votre projet en cours, les référencer à partir d'un autre projet ou les référencer à partir d'un autre assembly.

### <a name="to-add-an-activity-from-within-your-current-project"></a>Pour ajouter une activité à partir de votre projet en cours

1. Ajoutez une nouvelle activité personnalisée à votre projet de workflow actif. [!INCLUDE[crabout](../includes/crabout-md.md)] l’ajout d’une nouvelle activité personnalisée à votre projet, consultez [Comment : ajouter un nouvel élément à un projet de workflow](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Ajoutez une logique personnalisée à votre activité.

3. Créez le projet. Si la génération a réussi, une nouvelle catégorie de la **boîte à outils** nommée « \<*project name*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

    > [!NOTE]
    > Si la boîte à outils est réinitialisée, des activités personnalisées sont supprimées, même si la solution est générée à nouveau. Pour remplir de nouveau la boîte à outils avec des activités personnalisées, redémarrez [!INCLUDE[vs2010](../includes/vs2010-md.md)] après que la boîte à outils a été réinitialisée.

    > [!NOTE]
    > La boîte à outils ne peut afficher qu'une activité d'un nom donné. Si deux activités de différents assemblys ont le même nom de classe, une seule s'affiche.

    > [!NOTE]
    > Le domaine d'application est partagé entre des instances de l'éditeur ; si des variables statiques sont utilisées, elles sont également partagées par les instances de l'éditeur. S'il ne s'agit pas du comportement souhaité, un service doit être utilisé pour assurer le suivi des instances variables. Pour plus d’informations sur l’utilisation des services dans le concepteur, consultez [utilisation du contexte d’édition ModelItem](https://msdn.microsoft.com/library/7f9f1ea5-0147-4079-8eca-be94f00d3aa1) .

### <a name="to-add-an-activity-from-within-a-different-project"></a>Pour ajouter une activité à partir d'un autre projet

1. Ouvrez une solution qui contient au moins un projet de workflow, ainsi qu'un projet de bibliothèque d'activités personnalisées ou un autre projet de workflow qui définit une activité personnalisée.

2. Générez les deux projets. Si les builds ont réussi, une nouvelle catégorie de la **boîte à outils** nommée « \<*project name*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

### <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Pour ajouter une activité à la boîte à outils à partir d'un assembly

1. Ouvrez une solution de workflow.

2. Dans le menu **Outils** , sélectionnez **choisir des éléments de boîte à outils...**.

3. Dans la boîte de dialogue **choisir des éléments de boîte à outils** , sélectionnez l’onglet **composants System. Activities** , puis cliquez sur **Parcourir...** pour accéder à l’assembly qui contient l’activité personnalisée que vous souhaitez ajouter.

4. Sélectionnez l’assembly, puis cliquez sur **OK**. Le composant d'activité personnalisée est ajouté à la liste de composants et est automatiquement sélectionné.

    1. Cliquez sur **OK** pour fermer la boîte de dialogue.

5. Pour afficher la boîte à outils, sélectionnez **boîte à outils** dans le menu **affichage** .

6. L’activité personnalisée s’affiche dans la **boîte à outils** sous la catégorie qui était active avant l’ajout de l’élément. Par exemple, si la catégorie **général** a été sélectionnée dans la **boîte à outils** avant l’ajout de l’élément de boîte à outils, l’activité s’affiche sous la catégorie **général** .

## <a name="see-also"></a>Voir aussi
 [Utilisation du Concepteur de flux de travail](../workflow-designer/using-the-workflow-designer.md)