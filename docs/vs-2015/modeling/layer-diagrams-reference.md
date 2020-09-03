---
title: 'Diagrammes de couche : référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: f26c986c-1e79-420e-b29a-a283e6d8a71d
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 448a74b739bbb339d5f3b3e56c0ba59072994109
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850617"
---
# <a name="layer-diagrams-reference"></a>Diagrammes de couche : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser un *diagramme de couche* pour visualiser l’architecture logique de haut niveau de votre système. Un diagramme de couche organise les artefacts physiques dans votre système en groupes logiques abstraits appelés *couches*. Ces couches décrivent les tâches principales que les artefacts exécutent ou les principaux composants de votre système. Chaque couche peut également contenir des couches imbriquées qui décrivent des tâches plus détaillées.

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Vous pouvez spécifier les dépendances prévues ou existantes entre des couches. Ces dépendances, représentées comme des flèches, indiquent quelles couches peuvent utiliser ou actuellement utiliser la fonctionnalité représentée par d'autres couches. En organisant votre système en couches qui décrivent des fonctions et des rôles distincts, un diagramme de couche peut simplifier la compréhension, la réutilisation et la maintenance de votre code.

 Utilisez un diagramme de couche pour vous aider à effectuer les tâches suivantes :

- communiquer l'architecture logique existante ou prévue de votre système ;

- découvrir des conflits entre votre code existant et l'architecture prévue ;

- visualiser l'impact de modifications sur l'architecture prévue quand vous refactorisez, mettez à jour ou faites évoluer votre système ;

- renforcer l'architecture prévue pendant le développement et la maintenance de votre code en incluant la validation avec vos opérations de build et d'archivage.

  Cette rubrique décrit les éléments que vous pouvez utiliser sur un diagramme de couche. Pour plus d’informations sur la création et le dessin de diagrammes de couche, consultez [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md). Pour plus d’informations sur les modèles de superposition, consultez le [site patterns & Practices](https://apparch.codeplex.com/Wiki/View.aspx?title=Application Patterns&referringTitle=Home).

## <a name="reading-layer-diagrams"></a>Lecture des diagrammes de couche
 ![Éléments des diagrammes de couche](../modeling/media/uml-layerrefreading.png "UML_LayerRefReading")

 Le tableau suivant décrit les éléments que vous pouvez utiliser sur un diagramme de couche.

|**Forme**|**Element**|**Description**|
|---------------|-----------------|---------------------|
|1|**Couche**|Groupe logique d'artefacts physiques dans votre système. Ces artefacts peuvent correspondre à des espaces de noms, des projets, des classes, des méthodes, etc.<br /><br /> Pour afficher les artefacts liés à une couche, ouvrez le menu contextuel de la couche, puis choisissez afficher les **liens** pour ouvrir l' **Explorateur de couches**.<br /><br /> Pour plus d’informations, consultez [Explorateur de couches](#Explorer).<br /><br /> -   **Dépendances d’espaces de noms interdits** : spécifie que les artefacts associés à cette couche ne peuvent pas dépendre des espaces de noms spécifiés.<br />-   **Espaces de noms interdits** : spécifie que les artefacts associés à cette couche ne doivent pas appartenir aux espaces de noms spécifiés.<br />-   **Espaces de noms requis** : spécifie que les artefacts associés à cette couche doivent appartenir à l’un des espaces de noms spécifiés.|
|2|**Dépendance**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, mais pas l'inverse.<br /><br /> -   **Direction** : spécifie la direction de la dépendance.|
|3|**Dépendance bidirectionnelle**|Indique qu'une couche peut utiliser les fonctionnalités d'une autre couche, et vice versa.<br /><br /> -   **Direction** : spécifie la direction de la dépendance.|
|4|**Commentaire**|Permet d'ajouter des remarques générales au diagramme ou aux éléments du diagramme.|
|5|**Lien de commentaire**|Permet de lier des commentaires aux éléments du diagramme.|

## <a name="layer-explorer"></a><a name="Explorer"></a> Explorateur de couches
 Vous pouvez lier chaque couche aux artefacts de votre solution, tels que des projets, des classes, des espaces de noms, des fichiers projet et d'autres parties de votre logiciel. Le nombre indiqué sur une couche représente le nombre d’artefacts liés à cette couche. Toutefois, quand vous lisez le nombre d'artefacts sur une couche, tenez compte des points suivants :

- Si une couche est liée à un artefact contenant d'autres artefacts, mais n'est pas directement liée à ces autres artefacts, le nombre représentera uniquement les artefacts auxquels elle est directement liée. Toutefois, les autres artefacts sont inclus dans l'analyse pendant la validation de couche.

   Par exemple, si une couche est liée à un espace de noms unique, le nombre d'artefacts liés est égal à 1, même si l'espace de noms contient des classes. Si la couche a également des liens vers chaque classe de l'espace de noms, le nombre comprendra les classes liées.

- Si une couche contient d'autres couches liées à des artefacts, la couche du conteneur est également liée à ces artefacts, même si le nombre indiqué sur la couche du conteneur ne comprend pas ces artefacts.

  Pour plus d'informations sur la liaison des couches et des artefacts, consultez :

- [Diagrammes de couche : recommandations](../modeling/layer-diagrams-guidelines.md)

- [Créer des diagrammes de couche à partir de votre code](../modeling/create-layer-diagrams-from-your-code.md)

#### <a name="to-examine-the-linked-artifacts"></a>Pour examiner les artefacts liés

- Dans le diagramme de couche, ouvrez le menu contextuel d’une ou plusieurs couches, puis choisissez **afficher les liens**.

     L' **Explorateur de couches** s’ouvre et affiche les artefacts liés aux couches sélectionnées. L' **Explorateur de couches** contient une colonne qui affiche chacune des propriétés des liens d’artefact.

    > [!NOTE]
    > Si vous ne voyez pas toutes ces propriétés, développez la fenêtre **Explorateur de couches** .

    |**Colonne dans l'Explorateur de couches**|**Description**|
    |----------------------------------|---------------------|
    |**Catégories**|Genre d'artefact, tel qu'une classe, un espace de noms, un fichier source, etc.|
    |**Couche**|Couche liée à l'artefact.|
    |**Prend en charge la validation**|Si la **valeur est true**, le processus de validation de couche peut vérifier que le projet est conforme aux dépendances vers ou à partir de cet élément.<br /><br /> Si la **valeur est false**, le lien ne participe pas au processus de validation de couche.<br /><br /> Pour plus d’informations, consultez [diagrammes de couche : instructions](../modeling/layer-diagrams-guidelines.md).|
    |**Identificateur**|Référence à l'artefact lié.|

## <a name="see-also"></a>Voir aussi
 [Créer des modèles pour votre application](../modeling/create-models-for-your-app.md)
