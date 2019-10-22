---
title: 'Diagrammes de cas d’usage UML : référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbea61c2a26b1dc81487365ef8fc3f320ac95943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657302"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagrammes de cas d'usage UML : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, un *diagramme de cas d’usage* résume qui utilise votre application ou système, et ce qu’il peut en faire. Pour créer un diagramme de cas d’usage UML, dans le menu **architecture** , cliquez sur **nouveau diagramme UML ou diagramme de couche**.

 Un diagramme de cas d'usage est l'emplacement central où vous décrivez les besoins des utilisateurs. Il décrit les relations entre les besoins, les utilisateurs et les principaux composants. Il ne décrit pas les besoins en détail. Ceux-ci peuvent être décrits dans des diagrammes séparés ou dans des documents qui peuvent être liés à chaque cas d'usage. Pour plus d’informations sur la façon dont les diagrammes de cas d’usage peuvent vous aider à comprendre, discuter et communiquer les besoins de vos utilisateurs, consultez [Configuration requise pour l’utilisateur du modèle](../modeling/model-user-requirements.md).

 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Cette rubrique décrit les éléments qui sont disponibles dans les diagrammes de cas d'usage. Pour plus d’informations sur la façon de dessiner des diagrammes de cas d’usage, consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md). Pour plus d’informations sur la création et le dessin de diagrammes de modélisation, consultez [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-use-case-diagrams"></a>Lecture des diagrammes de cas d'usage
 Les tableaux des sections suivantes décrivent les éléments qui sont disponibles sur un diagramme de cas d'usage, ainsi que leurs principales propriétés. Pour obtenir la liste complète des propriétés, consultez [propriétés d’éléments dans les diagrammes de cas d’usage UML](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).

### <a name="actors-use-cases-and-subsystems"></a>Acteurs, cas d'usage et sous-systèmes
 ![Éléments dans un diagramme de cas d’usage](../modeling/media/uml-ucovactor.png "UML_UCOvActor")

|**Automatiques**|**Élément**|**Description et propriétés principales**|
|---------------|-----------------|-----------------------------------------|
|1|**Intervenant**|Représente un utilisateur, une organisation ou un système externe qui interagit avec votre application ou votre système. Un acteur est un genre de type.<br /><br /> -   **chemin d’accès** à l’image : chemin d’accès de fichier d’une image qui doit être utilisée à la place de l’icône d’acteur par défaut. L'icône doit être un fichier de ressources dans le projet Visual Studio.|
|2|**Cas d’usage**|Représente les actions exécutées par un ou plusieurs acteurs dans le cadre d'un objectif particulier. Un cas d'usage est un genre de type.<br /><br /> **sujets** de -    : sous-système dans lequel s’affiche le cas d’usage.|
|3|**Association**|Indique qu'un acteur participe à un cas d'usage.|
|4|**Sous-système ou composant**|Application ou système sur lequel vous travaillez, ou une partie de celui-ci. Peut être beaucoup de choses, d'une simple classe dans une application jusqu'à un réseau de grande taille.<br /><br /> Les cas d'usage pris en charge par un système ou un composant sont affichés à l'intérieur de son rectangle. Il peut être utile d'afficher certains cas d'usage hors du rectangle, pour clarifier la portée de votre système.<br /><br /> Un sous-système dans un diagramme de cas d'usage a fondamentalement le même type qu'un composant dans un diagramme de composant.<br /><br /> -   **est instancié indirectement** -si la valeur est false, votre système en cours d’exécution possède un ou plusieurs objets qui correspondent directement à ce sous-système. Si la valeur est true, le sous-système est une construction dans votre conception qui apparaît dans le système en cours d'exécution uniquement par l'intermédiaire de l'instanciation de ses parties constituantes.|

### <a name="structuring-use-cases"></a>Structures des cas d'usage
 ![Cas d’usage avec include, Extend et généralisation](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")

|Forme|**Élément**|Description|
|-----------|-----------------|-----------------|
|5|**Inclusion**|Un cas d'usage d'inclusion appelle le cas d'usage inclus. L'inclusion sert à montrer comment un cas d'usage se divise en étapes plus petites. Le cas d'usage inclus se trouve à l'extrémité dotée d'une flèche.<br /><br /> Notez que le diagramme n'indique pas l'ordre des étapes. Vous pouvez utiliser un diagramme d'activités, un diagramme de séquence ou tout autre document pour décrire ces détails.|
|6|**Étendre**|Un cas d'usage d'extension ajoute des objectifs et des étapes au cas d'usage étendu. Les extensions opèrent uniquement sous certaines conditions. Le cas d'usage étendu est à l'extrémité dotée d'une flèche.<br /><br /> Notez que le diagramme n'indique pas les circonstances exactes dans lesquelles l'extension s'applique : vous pouvez les consigner dans un commentaire ou tout autre document.|
|7|**Héritage**|Se rapporte à un élément spécialisé et à un élément généralisé. L'élément généralisé est à l'extrémité dotée d'une flèche.<br /><br /> Un cas d'usage spécialisé hérite des objectifs et des acteurs de sa généralisation et peut ajouter des objectifs et des étapes plus spécifiques pour atteindre ces objectifs.<br /><br /> Un acteur spécialisé hérite des cas d'usage, des attributs et des associations de sa généralisation et peut en ajouter d'autres.|
|8|**Dépendance**|Indique que la conception de la source dépend de la conception de la cible.|
|9|**Commentaireaire**|Permet d'ajouter des remarques générales au diagramme.|
|10|**Erratique**|Un artefact fournit un lien vers un autre diagramme ou document. Vous pouvez le créer en faisant glisser un fichier depuis l'Explorateur de solutions. Il peut être lié avec une dépendance à tout autre élément sur le diagramme. Un artefact sert généralement à lier un cas d'usage à un diagramme de séquence, une page OneNote, un document Word ou une présentation PowerPoint qui le décrit en détail. Le document peut être un élément dans la solution [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ou un document à un emplacement partagé tel qu'un site SharePoint.<br /><br /> -   **un lien hypertexte**. URL ou chemin d'accès de fichier du diagramme ou du document.<br /><br /> Double-cliquez sur un artefact pour ouvrir la page web ou le fichier auquel il est lié.|
|11 (non illustré)|**Paquet**|Les cas d'usage, les acteurs et les sous-systèmes peuvent être contenus dans des packages. Les formes de package n’apparaissent pas dans le diagramme, mais vous pouvez définir la propriété **LinkedPackage** du diagramme. Les éléments que vous créez ultérieurement dans le diagramme sont placés dans le package. Pour plus d’informations, consultez [définir des packages et des espaces de noms](../modeling/define-packages-and-namespaces.md).|

## <a name="see-also"></a>Voir aussi
 [Diagrammes de cas d’usage UML : instructions](../modeling/uml-use-case-diagrams-guidelines.md) [modification de modèles et de diagrammes UML](../modeling/edit-uml-models-and-diagrams.md) [diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md) [diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md) diagrammes de [composants UML : référence](../modeling/uml-component-diagrams-reference.md) [diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)
