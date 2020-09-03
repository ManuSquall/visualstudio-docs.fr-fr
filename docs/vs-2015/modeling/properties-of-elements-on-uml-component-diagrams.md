---
title: Propriétés des éléments dans les diagrammes de composants UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.componentdiagram.shapes.properties
helpviewer_keywords:
- component diagrams, properties
- UML, element properties
ms.assetid: fa0a9460-6675-4642-aa00-50f8719a892d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39350a9e1d340651f8e15de109ecf61eb98996bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671433"
---
# <a name="properties-of-elements-on-uml-component-diagrams"></a>Propriétés des éléments dans les diagrammes de composants UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de composant UML, chaque élément du diagramme possède des propriétés. Pour afficher les propriétés d’un élément, cliquez avec le bouton droit sur l’élément dans le diagramme ou dans l' **Explorateur de modèles UML** , puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre **Propriétés** .

> [!NOTE]
> Cette rubrique traite des propriétés d'éléments dans les diagrammes de composants UML. Pour plus d’informations sur la lecture des diagrammes de composants UML, consultez [diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md). Pour plus d’informations sur la façon de dessiner des diagrammes de composants UML, consultez [diagrammes de composants UML : indications](../modeling/uml-component-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriétés des éléments

|Propriété|Default|Élément|Description|
|--------------|-------------|-------------|-----------------|
|**Nom**|Nom par défaut|Tous|Identifie l'élément.|
|**Nom qualifié**|Espace de noms :: nom|Tous|Identifie l'élément de manière unique.<br /><br /> Le nom d'un composant ou d'un type a pour préfixe le nom qualifié du package qui le contient.<br /><br /> Le nom d'une partie ou d'un port a pour préfixe le nom qualifié du composant qui le possède.|
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Description**|(aucun)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|
|**Couleur**|(valeur par défaut pour le type)|Composant, élément, délégation, assembly d'élément|Couleur de la forme. Contrairement aux autres propriétés, c'est la couleur de la forme plutôt que l'élément de modèle que la forme affiche.|
|**Is Indirectly Instantiated**|True|Composant|Le composant existe uniquement en tant qu'un artefact de conception. Au moment de l'exécution, seuls ses éléments existent.|
|**Est abstrait**|False|Composant|La définition du composant peut être utilisée uniquement comme une généralisation à partir de laquelle d'autres composants peuvent être spécialisés.|
|**Visibilité**|Public|Composant, élément, port|**Public** -visible globalement.<br /><br /> **Package** : visible dans le package.<br /><br /> **Private** : visible dans le composant propriétaire.<br /><br /> **Protégé** : visible pour les composants dérivés du propriétaire.|
|**Type**|Type à la création|Élément<br /><br /> Port|Le type d'un élément est un composant ou une classe.<br /><br /> Le type d'un port est une interface.|
|**Multiplicité**|1|Élément<br /><br /> Port|Indique le nombre d'instances du type spécifié faisant partie du composant parent.<br /><br /> `1` -exactement un.<br /><br /> `0..1` -un ou aucun.<br /><br /> `*` : collection d’un nombre quelconque.<br /><br /> `n..m` : collection d’instances de n à m.|
|**Is Behavior**|False|Port|Si la valeur est True, les messages envoyés à ce port sont contrôlés par des activités ou des opérations qui sont décrites dans le cadre du composant, et non dans ses éléments.|
|**Is Service**|False|Port|Si la valeur est True, ce port fait partie de l'interface publiée de ce composant.|
|**LinkedPackage**|Modèle|Diagramme|Espace de noms par défaut pour les éléments ajoutés à ce diagramme.|

## <a name="see-also"></a>Voir aussi
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md) [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md)
