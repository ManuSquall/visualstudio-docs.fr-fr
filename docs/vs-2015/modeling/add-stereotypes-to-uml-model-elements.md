---
title: Ajouter des stéréotypes à des éléments de modèle UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292331"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Ajouter des stéréotypes à des éléments de modèle UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter un stéréotype à un élément de modèle UML pour l'annoter et lui associer des propriétés spécialisées. Pour ajouter un stéréotype à un élément de modèle, il faut que le stéréotype soit défini dans un profil et vous devez lier ce profil à un package ou au modèle qui contient l'élément de modèle. Chaque stéréotype peut être ajouté uniquement à certains types d'éléments de modèles, tels que les classes UML, les cas d'usage ou les composants.

 Par exemple, si vous souhaitez définir une classe UML avec le stéréotype « spécification », vous devez le créer dans un package ou un modèle qui est lié au Profil standard L2.

 Par défaut, chaque modèle est lié aux Profils standard UML L2 et L3.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Pour lier un profil à un modèle ou à un package

1. Ouvrez l' **Explorateur de modèles UML**. Dans le menu **architecture** , pointez sur **fenêtres**, puis cliquez sur **Explorateur de modèles UML**.

2. Recherchez un package ou un modèle qui contient tous les éléments auxquels vous souhaitez appliquer les stéréotypes dans le profil.

3. Cliquez avec le bouton droit sur le package ou le modèle, puis cliquez sur **Propriétés**.

4. Dans la fenêtre **Propriétés** , définissez la propriété **profils** sur les profils qui contiennent les stéréotypes que vous souhaitez utiliser.

     Les stéréotypes du profil seront maintenant disponibles sur tous les éléments dans le modèle ou le package. Si le package contient d'autres packages, les stéréotypes seront également disponibles sur les éléments qu'ils contiennent.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Pour ajouter des stéréotypes à des éléments de modèle ou des relations

1. Cliquez avec le bouton droit sur l’élément de modèle ou la relation, sur un diagramme ou dans l' **Explorateur de modèles UML**, puis cliquez sur **Propriétés**.

    > [!NOTE]
    > Pour ajouter les mêmes stéréotypes à plusieurs éléments, vous pouvez sélectionner plusieurs éléments, puis cliquer avec le bouton droit sur l'un d'eux.

2. Cliquez sur la propriété **stéréotypes** et sélectionnez les stéréotypes que vous souhaitez appliquer.

     Les stéréotypes sélectionnés sont affichés entre « chevrons » dans l'élément de modèle pour la plupart des types de relations et d'éléments.

    > [!NOTE]
    > Si vous ne voyez pas la propriété **stéréotypes** , ou si le stéréotype souhaité n’apparaît pas, vérifiez que l’élément de modèle est à l’intérieur d’un package ou d’un modèle auquel le profil approprié a été lié.

3. Certains stéréotypes vous permettent de définir les valeurs de propriétés supplémentaires pour l'élément de modèle. Pour afficher ces propriétés, développez la propriété **stéréotypes** .

### <a name="to-create-model-elements-within-a-package"></a>Pour créer des éléments de modèle dans un package

1. Créez un package dans un diagramme de classes UML ou dans l' **Explorateur de modèles UML**.

2. Ajoutez des éléments de modèle au package de l'une des manières suivantes :

    - Dans un diagramme de classes UML, cliquez sur l'outil pour un élément, puis cliquez à l'intérieur du package sur le diagramme.

         \- ou -

    - Dans l’Explorateur de modèles UML, cliquez avec le bouton droit sur le package, pointez sur **Ajouter**, puis cliquez sur un type d’élément.

         \- ou -

    - Dans l'Explorateur de modèles UML, faites glisser un élément existant dans le package.

         \- ou -

    - Liez un diagramme au package, puis créez des éléments sur le diagramme.

         Pour ce faire, cliquez avec le bouton droit sur une partie vide du diagramme, puis cliquez sur **Propriétés**. Dans la fenêtre **Propriétés** , définissez **package lié** sur le package de votre choix.

         Tous les nouveaux éléments que vous créez sur le diagramme seront définis dans ce package.

         Cette opération est possible uniquement avec certains types de diagrammes.

## <a name="see-also"></a>Voir aussi
 [Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md) [personnaliser votre modèle avec des profils et des stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md)

