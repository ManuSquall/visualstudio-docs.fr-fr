---
title: Ajouter des stéréotypes à des éléments de modèle UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: dbd5f4288833a29bdfef2df97ee71ac765ae168f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725374"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Ajouter des stéréotypes à des éléments de modèle UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter un stéréotype à un élément de modèle UML pour l'annoter et lui associer des propriétés spécialisées. Pour ajouter un stéréotype à un élément de modèle, il faut que le stéréotype soit défini dans un profil et vous devez lier ce profil à un package ou au modèle qui contient l'élément de modèle. Chaque stéréotype peut être ajouté uniquement à certains types d'éléments de modèles, tels que les classes UML, les cas d'usage ou les composants.  
  
 Par exemple, si vous souhaitez définir une classe UML avec le stéréotype « spécification », vous devez le créer dans un package ou un modèle qui est lié au Profil standard L2.  
  
 Par défaut, chaque modèle est lié aux Profils standard UML L2 et L3.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Pour lier un profil à un modèle ou à un package  
  
1.  Ouvrez **Explorateur de modèles UML**. Sur le **Architecture** menu, pointez sur **Windows**, puis cliquez sur **Explorateur de modèles UML**.  
  
2.  Recherchez un package ou un modèle qui contient tous les éléments auxquels vous souhaitez appliquer les stéréotypes dans le profil.  
  
3.  Cliquez sur le package ou le modèle, puis sur **propriétés**.  
  
4.  Dans le **propriétés** fenêtre, définissez la **profils** propriété pour les profils qui contiennent les stéréotypes que vous souhaitez utiliser.  
  
     Les stéréotypes du profil seront maintenant disponibles sur tous les éléments dans le modèle ou le package. Si le package contient d'autres packages, les stéréotypes seront également disponibles sur les éléments qu'ils contiennent.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Pour ajouter des stéréotypes à des éléments de modèle ou des relations  
  
1.  Avec le bouton droit de l’élément de modèle ou la relation, sur un diagramme ou dans **Explorateur de modèles UML**, puis cliquez sur **propriétés**.  
  
    > [!NOTE]
    >  Pour ajouter les mêmes stéréotypes à plusieurs éléments, vous pouvez sélectionner plusieurs éléments, puis cliquer avec le bouton droit sur l'un d'eux.  
  
2.  Cliquez sur le **stéréotypes** propriété et sélectionnez les stéréotypes que vous souhaitez appliquer.  
  
     Les stéréotypes sélectionnés sont affichés entre « chevrons » dans l'élément de modèle pour la plupart des types de relations et d'éléments.  
  
    > [!NOTE]
    >  Si vous ne voyez pas le **stéréotypes** propriété, ou si le stéréotype souhaité n’apparaît pas, vérifiez que l’élément de modèle est à l’intérieur d’un package ou un modèle auquel le profil approprié a été lié.  
  
3.  Certains stéréotypes vous permettent de définir les valeurs de propriétés supplémentaires pour l'élément de modèle. Pour afficher ces propriétés, développez le **stéréotypes** propriété.  
  
### <a name="to-create-model-elements-within-a-package"></a>Pour créer des éléments de modèle dans un package  
  
1.  Créez un package dans un diagramme de classes UML ou dans **Explorateur de modèles UML**.  
  
2.  Ajoutez des éléments de modèle au package de l'une des manières suivantes :  
  
    -   Dans un diagramme de classes UML, cliquez sur l'outil pour un élément, puis cliquez à l'intérieur du package sur le diagramme.  
  
         \- ou -  
  
    -   Dans l’Explorateur de modèles UML, cliquez sur le package, pointez sur **ajouter**, puis cliquez sur un type d’élément.  
  
         \- ou -  
  
    -   Dans l'Explorateur de modèles UML, faites glisser un élément existant dans le package.  
  
         \- ou -  
  
    -   Liez un diagramme au package, puis créez des éléments sur le diagramme.  
  
         Pour ce faire, cliquez sur une partie vide du diagramme, puis cliquez sur **propriétés**. Dans le **propriétés** fenêtre, définissez **Package lié** le package que vous souhaitez.  
  
         Tous les nouveaux éléments que vous créez sur le diagramme seront définis dans ce package.  
  
         Cette opération est possible uniquement avec certains types de diagrammes.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un profil pour étendre UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Personnaliser votre modèle avec des profils et stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md)   
 [Color UML Classes by Stereotype](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)



