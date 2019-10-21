---
title: Propriétés de types dans des diagrammes de classes UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.shapes.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 6e1ef2d0-d67a-401a-bd64-d5e034decd2c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9881393e792cf8bf49dc6d0b9459b18969dea171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671318"
---
# <a name="properties-of-types-on-uml-class-diagrams"></a>Propriétés de types dans des diagrammes de classes UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de classes UML, un *type* est une classe, une interface ou une énumération.

> [!NOTE]
> Cette rubrique traite des propriétés de types dans les diagrammes de classes UML Pour plus d’informations, consultez les rubriques suivantes :

- [Informations de référence sur les diagrammes de classes UML](../modeling/uml-class-diagrams-reference.md)

- [Diagrammes de classes UML : recommandations](../modeling/uml-class-diagrams-guidelines.md)

- [Propriétés d’attributs dans des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propriétés d’opérations dans des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Propriétés des associations dans les diagrammes de classes UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

## <a name="properties"></a>Propriétés
 Il s'agit des propriétés d'une classe, interface ou énumération.

 Pour afficher les propriétés d’un type, cliquez avec le bouton droit sur le type dans le diagramme ou dans l' **Explorateur de modèles UML**, puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre **Propriétés** .

|**Property**|**Default**|Apparaît dans|Description|
|------------------|-----------------|----------------|-----------------|
|**Nom**|Nom par défaut|Tous les éléments|Identifie l'élément.|
|**Nom qualifié**|Package conteneur :: Nom du type|Tous les éléments|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|
|**Couleur**|Par défaut pour le genre de type|Tous les éléments|Couleur de cette forme. Contrairement aux autres propriétés, il ne s'agit pas d'une propriété de l'élément de modèle sous-jacent. Différentes vues du même type peuvent avoir différentes couleurs.|
|**Est abstrait**|False|Class|Si la valeur est true, la classe ne peut pas être instanciée et est destinée à être utilisée comme classe de base.|
|**Est une feuille**|False|Classe, Interface|Si la valeur est true, le type n'est pas destiné à avoir des types dérivés.|
|**Est actif**|False|Class|Si la valeur est true, chaque instance de ce type est associée à un thread de contrôle.|
|**Visibilité**|Public|Classe, Interface, Énumération|-Public-visible globalement.<br />-Private : ce type est visible dans le package qui le possède.<br />-Package : visible dans le package.|
|**Éléments de travail**|{0} associé|Tous les éléments|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Description**|(vide)|Tous les éléments|Vous pouvez consigner des remarques générales concernant l'élément.|
|**Liaison de modèle**|(aucune)|Classe, Interface, Énumération|Si la valeur n'est pas vide, ce type est défini en liant des valeurs de paramètres à cette classe de modèle. Développez la propriété pour afficher les liaisons des paramètres du modèle.|
|**Paramètres de modèle**|(aucune)|Classe, Interface, Énumération|Si la valeur n'est pas vide, il s'agit d'une classe de modèle qui a les paramètres répertoriés ici. Pour ajouter des paramètres ou afficher les propriétés de paramètres individuels, cliquez sur **[...]** .|

## <a name="see-also"></a>Voir aussi
 [Propriétés d’attributs sur des diagrammes de classes UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [propriétés d’opérations sur des diagrammes de classes UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [propriétés d’associations dans](../modeling/properties-of-associations-on-uml-class-diagrams.md) des diagrammes de classes UML [diagrammes de classes UML : indications](../modeling/uml-class-diagrams-guidelines.md)
