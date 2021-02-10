---
title: Ajouter des activités à la boîte à outils
description: Dans Concepteur de flux de travail, Découvrez comment ajouter des activités à la boîte à outils dans votre solution en les ajoutant à partir de votre projet actuel ou en les référençant à partir d’un autre projet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6def442b6500ac1265f83aef49db8c79c8e05ae7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971672"
---
# <a name="how-to-add-activities-to-the-toolbox"></a>Comment : ajouter des activités à la boîte à outils

Les activités peuvent être ajoutées à la **boîte à outils** dans votre solution de différentes manières. Vous pouvez les ajouter à partir de votre projet en cours, les référencer à partir d'un autre projet ou les référencer à partir d'un autre assembly.

## <a name="to-add-an-activity-from-within-your-current-project"></a>Pour ajouter une activité à partir de votre projet en cours

1. Ajoutez une nouvelle activité personnalisée à votre projet de workflow actif. Pour plus d’informations sur l’ajout d’une nouvelle activité personnalisée à votre projet, consultez [Comment : ajouter un nouvel élément à un projet de workflow](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).

2. Ajoutez une logique personnalisée à votre activité.

3. Créez le projet. Si la génération a réussi, une nouvelle catégorie de la **boîte à outils** nommée « \<*project name*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

    > [!NOTE]
    > Si la boîte à outils est réinitialisée, des activités personnalisées sont supprimées, même si la solution est générée à nouveau. Pour remplir à nouveau la boîte à outils avec des activités personnalisées après sa réinitialisation, redémarrez Visual Studio.

    > [!NOTE]
    > La boîte à outils ne peut afficher qu'une activité d'un nom donné. Si deux activités de différents assemblys ont le même nom de classe, une seule s'affiche.

    > [!NOTE]
    > Le domaine d'application est partagé entre des instances de l'éditeur ; si des variables statiques sont utilisées, elles sont également partagées par les instances de l'éditeur. S'il ne s'agit pas du comportement souhaité, un service doit être utilisé pour assurer le suivi des instances variables. Pour plus d’informations sur l’utilisation des services dans le concepteur, consultez [utilisation du contexte d’édition ModelItem](/dotnet/framework/windows-workflow-foundation/using-the-modelitem-editing-context) .

## <a name="to-add-an-activity-from-within-a-different-project"></a>Pour ajouter une activité à partir d'un autre projet

1. Ouvrez une solution qui contient au moins un projet de workflow, ainsi qu'un projet de bibliothèque d'activités personnalisées ou un autre projet de workflow qui définit une activité personnalisée.

2. Générez les deux projets. Si les builds ont réussi, une nouvelle catégorie de la **boîte à outils** nommée « \<*project name*> » avec l’activité personnalisée incluse dans cette catégorie s’affiche.

## <a name="to-add-an-activity-to-the-toolbox-from-an-assembly"></a>Pour ajouter une activité à la boîte à outils à partir d'un assembly

1. Ouvrez une solution de workflow.

2. Dans le menu **Outils** , sélectionnez **choisir des éléments de boîte à outils**.

3. Dans la boîte de dialogue **choisir des éléments de boîte à outils** , sélectionnez l’onglet **composants System. Activities** , puis cliquez sur **Parcourir** pour accéder à l’assembly qui contient l’activité personnalisée que vous souhaitez ajouter.

4. Sélectionnez l’assembly, puis cliquez sur **OK**. Le composant d'activité personnalisée est ajouté à la liste de composants et est automatiquement sélectionné.

    1. Cliquez sur **OK** pour fermer la boîte de dialogue.

5. Pour afficher la boîte à outils, sélectionnez **boîte à outils** dans le menu **affichage** .

6. L’activité personnalisée s’affiche dans la **boîte à outils** sous la catégorie qui était active avant l’ajout de l’élément. Par exemple, si la catégorie **général** a été sélectionnée dans la **boîte à outils** avant l’ajout de l’élément de boîte à outils, l’activité s’affiche sous la catégorie **général** .

## <a name="see-also"></a>Voir aussi

- [Utilisation du Concepteur de flux de travail](developing-applications-with-the-workflow-designer.md)
