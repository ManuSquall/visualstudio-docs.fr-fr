---
title: Propriétés des éléments sur les diagrammes de séquence UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4d0753ea7396c9f21addcbb01ab7b90be066356a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671424"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propriétés d'éléments de diagrammes de séquence UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de séquence UML, chaque élément possède des propriétés. Pour afficher les propriétés d’un élément, cliquez avec le bouton droit sur l’élément dans le diagramme ou dans l' **Explorateur de modèles UML** , puis cliquez sur **Propriétés**. Les propriétés s’affichent dans la fenêtre **Propriétés** .

> [!NOTE]
> Cette rubrique traite des propriétés d'éléments dans les diagrammes de séquence UML. Pour plus d’informations sur la lecture des diagrammes de séquence UML, consultez [diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md). Pour plus d’informations sur le dessin des diagrammes de séquence UML, consultez [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="properties-of-elements"></a>Propriétés des éléments

|Propriété|Default|Élément|Description|
|--------------|-------------|-------------|-----------------|
|**Name**|Nom par défaut|Tous|Identifie l'élément.|
|**Nom qualifié**|Package :: Nom|Tous|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|
|**Description**|(vide)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|
|**Couleur**|(valeur par défaut pour le type d'élément)|Ligne de vie, Message|Couleur de la forme. Il s'agit d'une propriété de la forme, plutôt que de l'élément qu'elle affiche.|
|**Type**|(vide)|Ligne de vie|Type de l'instance que représente la ligne de vie.<br /><br /> Si un symbole de référence est affiché dans l'en-tête de la ligne de vie, cela signifie que cette classe ou interface existe séparément dans l'Explorateur de modèles UML et qu'elle peut être affichée dans un diagramme de classes.|
|**Actor**|Faux|Ligne de vie|Indique si la ligne de vie représente un utilisateur, un périphérique ou un composant logiciel qui est externe au composant décrit par ce diagramme.|
|**Type**|**Complete** : message qui a à la fois l’expéditeur et le destinataire.<br /><br /> **Found** : message dont l’expéditeur n’est pas spécifié.<br /><br /> **Lost** -un message qui a un destinataire non spécifié.|Message|Indique les extrémités d'un message qui sont attachées à une ligne de vie.<br /><br /> Vous ne pouvez pas modifier cette propriété. Elle est définie quand vous créez le message.|
|**Sort**|**AsynchCall** : message asynchrone.<br /><br /> **SynchCall** : message synchrone.<br /><br /> **Reply** -retourne une partie d’un message synchrone.<br /><br /> **CreateMessage** -message de création d’instance.|Message|Type de message. Vous ne pouvez pas modifier cette propriété. Elle est déterminée par l'outil que vous utilisez pour créer le message.|
|**opération**|(empty)|Message|Méthode appelée par le message dans la ligne de vie de réception.<br /><br /> Visible uniquement si la ligne de vie de réception est liée à une interface ou à une classe.|
|**Fait référence à**|Diagramme de séquence|Utilisation d'interaction|Diagramme de séquence appelé par cette utilisation d'interaction.|
|**Opérateur d'interaction**|Défini lorsque vous avez utilisé la commande **entourer de**|Fragment combiné|Opérateur représenté par ce fragment ou cette collection de fragments.|
|**Guard**|(empty)|Opérande d'interaction dans un fragment combiné|La séquence du fragment ne se produit que si la garde a la valeur true.<br /><br /> Pour sélectionner le fragment supérieur d'un fragment combiné, cliquez sous le titre du fragment.|
|**Min., max.**|(aucune restriction)|Fragment combiné Loop|Nombre minimal et maximal d'exécutions de la boucle.|
|**Messages**|(empty)|Fragments combinés<br /><br /> Consider et Ignore|Messages qui sont pris en compte ou ignorés dans ce fragment.|

## <a name="see-also"></a>Voir aussi
 [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md) [diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md) [décrire le contrôle de workflow à l’aide de fragments sur des diagrammes de séquence UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)
