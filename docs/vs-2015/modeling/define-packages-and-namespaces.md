---
title: Définir des packages et des espaces de noms | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669899"
---
# <a name="define-packages-and-namespaces"></a>Définir des packages et des espaces de noms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, un *package* est un conteneur pour les définitions d’éléments UML tels que les classes, les cas d’usage et les composants. Un package peut également contenir d'autres packages.

 Dans l'Explorateur de modèles UML, toutes les définitions à l'intérieur d'un package sont imbriquées sous le package. Le modèle UML est un genre de package qui forme la racine de l'arborescence.

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Dans cette rubrique
 [Espaces de noms](#Namespaces)

 [Création et affichage de packages](#Packages)

 [Création d’éléments de modèle dans des packages](#Elements)

 [Déplacement d’éléments à l’intérieur ou à l’extérieur d’un package](#Moving)

 [Collage d’éléments dans un package](#Pasting)

 [Importer des relations entre des packages](#Import)

 [Références d’un espace de noms à un autre](#References)

 [Propriétés des packages](#Properties)

## <a name="Namespaces"></a>Espaces
 Les packages sont utiles pour séparer le travail en différentes zones. Chaque package définit un espace de noms pour que les noms définis dans différents packages ne soient pas en conflit les uns avec les autres.

 La propriété de nom qualifié de chaque élément est le nom qualifié du package auquel il appartient, suivi du nom de l'élément. Par exemple, si votre package se nomme `MyPackage`, une classe dans le package aura un nom qualifié tel que `MyPackage::MyClass`. Chaque élément étant contenu à l'intérieur d'un modèle, chaque nom qualifié commence par le nom du modèle.

 Un modèle définit aussi un espace de noms. Ainsi, le nom qualifié de chaque élément dans un modèle commence par le nom du modèle.

 D'autres éléments de modèle définissent également des espaces de noms. Par exemple, une opération appartient à l'espace de noms défini par sa classe parente. Son nom qualifié a donc le format `MyModel ::MyPackage ::MyClass ::MyOperation`. De la même manière, une action appartient à l'espace de noms défini par son activité parente.

 Les packages sont des conteneurs. Si vous déplacez ou supprimez un package, les classes, packages et autres éléments définis dedans sont également déplacés ou supprimés. Il en est de même des autres éléments qui définissent des espaces de noms.

## <a name="Packages"></a>Création et affichage de packages
 Vous pouvez créer un package sur un diagramme de classes UML ou dans l'Explorateur de modèles UML.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Pour créer un package dans un diagramme de classes UML

1. Ouvrez un diagramme de classes UML ou créez-en un.

2. Cliquez sur l’outil **package** .

3. Cliquez n'importe où sur le diagramme. Une nouvelle forme de package apparaît.

     Vous pouvez cliquer à l'intérieur d'un package existant pour imbriquer un package dans un autre.

4. Tapez un nouveau nom pour le package.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>Pour créer un package dans l'Explorateur de modèles UML

1. Ouvrez l' **Explorateur de modèles UML**. Dans le menu **architecture** , pointez sur **fenêtres**, puis cliquez sur l **'Explorateur de modèles UML**.

2. Cliquez avec le bouton droit sur un package ou un modèle auquel vous souhaitez ajouter un nouveau package.

   > [!NOTE]
   > Vous pouvez imbriquer un package dans un autre.

3. Pointez sur **Ajouter** , puis cliquez sur **package**.

    Un nouveau package apparaît dans le modèle.

4. Tapez un nouveau nom pour le package.

   Si vous avez créé un package dans l'Explorateur de modèles UML, vous pouvez l'afficher sur un diagramme de classes UML. Vous pouvez aussi afficher un package sur plusieurs diagrammes de classes UML.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Pour afficher un package existant sur un diagramme de classes UML

- Faites glisser le package de l'Explorateur de modèles UML vers le diagramme de classes.

    > [!NOTE]
    > Cela crée une vue du package sur ce diagramme, mais ne montre pas nécessairement tous les éléments contenus dans le package. Pour être sûr de voir tout le contenu d'un package, vous devez l'afficher dans l'Explorateur de modèles UML.

## <a name="Elements"></a>Création d’éléments de modèle dans des packages
 Il existe quatre manières de placer des éléments de modèle à l'intérieur d'un package :

- Ajouter un nouvel élément à un package dans l'Explorateur de modèles UML.

- Ajouter des classes et d'autres types à des packages dans un diagramme de classes UML.

- Définissez la propriété **LinkedPackage** d’un diagramme de manière à ce que les nouveaux éléments créés sur le diagramme soient placés dans le package que vous spécifiez. Vous pouvez lier des diagrammes de classes, des diagrammes de composants et des diagrammes de cas d'usage à un package de cette manière.

- Déplacer des éléments dans ou hors d'un package dans l'Explorateur de modèles UML.

  Un élément contenu dans un package apparaît sous celui-ci dans l'Explorateur de modèles UML et son nom qualifié commence par le nom qualifié du package. Pour afficher le nom qualifié d’un élément, cliquez avec le bouton droit sur l’élément, puis cliquez sur **Propriétés**. La propriété **nom qualifié** s’affiche dans la fenêtre **Propriétés** .

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Pour créer un élément dans un package dans l'Explorateur de modèles UML

1. Ouvrez l' **Explorateur de modèles UML**. Dans le menu **affichage** , pointez sur **autres fenêtres**, puis cliquez sur **Explorateur de modèles UML**.

2. Cliquez avec le bouton droit sur un package ou un modèle auquel vous souhaitez ajouter un nouvel élément.

3. Pointez sur **Ajouter**, puis cliquez sur le type d’élément que vous souhaitez ajouter.

     Le nouvel élément apparaît sous le package.

4. Tapez un nom pour le nouvel élément.

    > [!NOTE]
    > Le nouvel élément n'apparaît sur aucun diagramme. Pour créer une vue du nouvel élément, vous pouvez le faire glisser de l'Explorateur de modèles UML vers un diagramme. Le diagramme doit être un type qui affichera ce genre d'élément.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Pour créer un élément dans un package sur un diagramme de classes UML

1. Ouvrez un diagramme de classes sur lequel le package apparaît.

    - Créez un package si ce n'est déjà fait.

    - Pour qu’un package existant apparaisse sur un diagramme de classes, vous pouvez faire glisser le package de l' **Explorateur de modèles UML** vers le diagramme de classes.

2. Cliquez sur l'outil pour une classe, une interface, une énumération ou un package.

3. Cliquez sur le package où vous souhaitez placer le nouvel élément.

     Le nouvel élément apparaît à l'intérieur du package.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Pour créer tous les éléments d'un diagramme dans un package spécifié

1. Créez le package si ce n'est déjà fait.

2. Ouvrez un diagramme de composant, un diagramme de cas d'usage ou un diagramme de classes UML.

3. Ouvrez les propriétés du diagramme. Cliquez avec le bouton droit dans une partie vide du diagramme, puis cliquez sur **Propriétés**.

4. Dans la propriété **package lié** , choisissez le package qui doit contenir le contenu du diagramme.

5. Créez des éléments dans le diagramme. Ceux-ci seront placés dans le package.

    - Le **nom qualifié** de chaque élément commence par le nom qualifié du package.

    - Dans l' **Explorateur de modèles UML**, chaque élément s’affiche sous le package.

## <a name="Moving"></a>Déplacement d’éléments à l’intérieur et à l’extérieur des packages
 Vous pouvez déplacer un ou plusieurs éléments dans ou hors d'un package.

 Si vous déplacez un package, tout son contenu est déplacé avec lui.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Pour déplacer un élément dans ou hors d'un package

- Dans l'Explorateur de modèles UML, faites glisser l'élément dans ou hors de l'arborescence dont la racine est le package.

     Le nom qualifié de l'élément change et indique son nouveau package ou modèle propriétaire.

     \- ou -

- Dans un diagramme de classes, faites glisser l'élément dans une forme de package.

     Le nom qualifié de l'élément change et indique son nouveau package propriétaire.

    > [!NOTE]
    > Si vous faites glisser un élément hors d'un package dans une partie vide du diagramme, son package propriétaire ne change pas. Cela vous permet de créer un diagramme qui montre des éléments de plusieurs packages sans avoir à afficher les packages eux-mêmes.

## <a name="Pasting"></a>Collage d’éléments dans un package
 Vous pouvez coller un élément dans un package. Si vous collez un groupe d'éléments associés dans un package, les relations entre ces éléments sont également copiées.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Pour coller des éléments dans un package sur un diagramme de classes UML

1. Sur un diagramme de classes UML, sélectionnez tous les éléments à copier. Cliquez avec le bouton droit sur l’un d’eux, puis cliquez sur **copier**.

2. Cliquez avec le bouton droit sur le package, puis cliquez sur **coller**.

    > [!NOTE]
    > Le package peut être sur un autre diagramme.

## <a name="Import"></a>Importer des relations entre des packages
 Vous pouvez définir une relation d’importation entre des packages, à l’aide de l’outil d' **importation** .

 Le terme « importer » signifie que les éléments définis dans le package importé, qui sont les éléments à l'extrémité flèche de la relation, sont aussi définis dans le package d'importation. Tous les éléments dont la visibilité est définie en tant que **package** seront également visibles dans le package d’importation.

 Évitez de créer des boucles dans les relations d'importation.

## <a name="References"></a>Références d’un espace de noms à un autre
 Si vous souhaitez faire référence à un élément d'un package à partir d'un autre, vous devez utiliser le nom qualifié de l'élément.

 Par exemple, supposez que le package `SalesCommon` définit le type `CustomerAddress`. Dans un autre package `RestaurantSales`, vous souhaitez définir un type `MealOrder`, qui a un attribut de type Customer Address. Vous avez deux options :

- Spécifier le type de l'attribut en utilisant le nom qualifié complet `SalesCommon::CustomerAddress`. Vous devez effectuer cette opération uniquement si `CustomerAddress` a sa propriété **Visibility** définie sur **public**.

- Créer une relation d'importation du package `RestaurantSales` vers le package `SalesCommon`. Vous pouvez ensuite utiliser `CustomerAddress` sans utiliser son nom qualifié.

## <a name="Properties"></a>Propriétés des packages
 Chaque package a les propriétés suivantes. Pour afficher les propriétés, cliquez avec le bouton droit sur le package, sur un diagramme ou dans l’Explorateur de modèles UML, puis cliquez sur **Propriétés**.

|Property|Valeur par défaut|Description|
|--------------|-------------------|-----------------|
|**Nom**|(un nouveau nom)|Nom du package. Vous pouvez le modifier sur le diagramme ou dans la fenêtre Propriétés.|
|**Nom qualifié**|*Conteneur* :: *nom du package*|Nom complet, précédé du nom du package ou du modèle qui contient ce package. Pour plus d’informations, consultez l’article [Espaces de noms](#Namespaces).|
|**Profils**|(vide)|Liste des profils liés à ce package. Ces profils fournissent des stéréotypes qui peuvent être appliqués aux éléments à l'intérieur du package. Pour plus d’informations, consultez [personnaliser votre modèle avec des profils et des stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Visibilité**|**Public**|Visibilité du package en dehors de son package parent.|
|**Éléments de travail**|(vide)|Liste d'éléments de travail liés. Pour plus d’informations, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Emplacement de la définition**|(nom)|Nom du fichier où sont stockés les détails du package. Les fichiers se trouvent dans le dossier du projet **ModelDefinition** . Ces informations peuvent être utiles pour le contrôle de code source.|
|**Description**|(vide)|Description du package.|
|**Stéréotypes**|(vide)|Stéréotypes appliqués à ce package. La liste des stéréotypes disponibles est déterminée par les profils que vous avez choisis pour ce package et les packages qui le contiennent. Pour plus d’informations, consultez [personnaliser votre modèle avec des profils et des stéréotypes](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Stockage des packages
 Lorsque vous créez un nouveau package, un nouveau fichier **. Uml** est créé dans le dossier du projet **ModelDefinition** . Le modèle racine, qui est également un package, est également stocké dans un fichier **. Uml** .

 En outre, chaque diagramme est stocké dans deux fichiers, un qui représente les formes du diagramme et un fichier **. Layout** qui enregistre les positions des formes.

## <a name="see-also"></a>Voir aussi
 [Modifier des diagrammes et des modèles UML](../modeling/edit-uml-models-and-diagrams.md) [diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md) [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md) [gérer des modèles et des diagrammes sous contrôle de version](../modeling/manage-models-and-diagrams-under-version-control.md)
