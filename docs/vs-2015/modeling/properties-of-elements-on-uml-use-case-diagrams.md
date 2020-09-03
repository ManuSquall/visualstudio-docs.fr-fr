---
title: Propriétés des éléments dans les diagrammes de cas d’usage UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.artifact.properties
- vs.teamarch.usecasediagram.shapes.properties
helpviewer_keywords:
- use case diagrams, properties
ms.assetid: 2728fb26-a275-4fce-8a2c-5a78af6bee04
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: db3dc649d979c87960a42d38ffa211e352be175b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671414"
---
# <a name="properties-of-elements-on-uml-use-case-diagrams"></a>Propriétés d'éléments sur des diagrammes de cas d'usage UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de cas d'usage UML, chaque élément possède des propriétés. Pour afficher les propriétés d’un élément, cliquez avec le bouton droit sur l’élément dans le diagramme ou dans l' **Explorateur de modèles UML** , puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre **Propriétés** .

> [!NOTE]
> Cette rubrique traite des propriétés d'éléments dans les diagrammes de cas d'usage UML. Pour plus d’informations sur la lecture des diagrammes d’activités UML, consultez [diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md). Pour plus d’informations sur la façon de dessiner des diagrammes d’activités UML, consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriétés des éléments

|Propriété|Default|Élément|Description|
|--------------|-------------|-------------|-----------------|
|**Name**|Nom par défaut|Tous|Identifie l'élément.|
|**Nom qualifié**|Package :: Nom|Tous|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Description**|(aucun)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|
|**Couleur**|(par défaut)|Tous|Couleur de la forme. Contrairement aux autres propriétés, il ne s'agit pas d'une propriété de l'élément affichée par la forme.|
|**Chemin d'accès à l'image**|(aucun)|Acteur|Chemin d'accès d'une image qui doit être utilisée au lieu de l'icône d'acteur par défaut. L'icône doit être un fichier de ressources dans le projet Visual Studio.|
|**Sujets**|(aucun)|Cas d’usage|Sous-système ou autre type qui possède le cas d'usage.<br /><br /> Vous pouvez le définir en plaçant le cas d'usage sur un sous-système dans le diagramme.|
|**Visibilité**|Public|Cas d'usage, Acteur, Sous-système|**Public** -visible globalement.<br /><br /> **Package** : visible dans le package.|
|**IsAbstract**|Faux|Cas d'usage, Acteur, Sous-système|Si la valeur est true, le type ne peut pas être instancié et constitue une base pour la spécialisation par d'autres définitions.|
|**Is Indirectly Instantiated**|Vrai|Subsystem|Le sous-système existe uniquement en tant qu'artefact de conception. Au moment de l'exécution, seuls ses éléments existent.|
|**Lien hypertexte**|(aucun)|Artefact|Chemin d'accès de fichier ou URL du diagramme ou du document vers lequel l'artefact fournit un lien.|

 Pour obtenir la liste des propriétés des associations, consultez [propriétés d’associations dans des diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

## <a name="see-also"></a>Voir aussi
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md) [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)
