---
title: Diagrammes de séquence de propriétés des éléments UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.properties
- vs.teamarch.sequencediagram.shapes.properties
helpviewer_keywords:
- UML sequence diagrams, properties
- sequence diagrams, properties
ms.assetid: 475c10f3-a2d2-4a1e-b366-dc28997d437e
caps.latest.revision: 22
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7af657496fc95b07c7149f75fa03087eb1988606
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245217"
---
# <a name="properties-of-elements-on-uml-sequence-diagrams"></a>Propriétés d'éléments de diagrammes de séquence UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans un diagramme de séquence UML, chaque élément possède des propriétés. Pour afficher les propriétés d’un élément, cliquez sur l’élément sur le diagramme ou dans **Explorateur de modèles UML** puis cliquez sur **propriétés**. Les propriétés s’affichent dans le **propriétés** fenêtre.  
  
> [!NOTE]
>  Cette rubrique traite des propriétés d'éléments dans les diagrammes de séquence UML. Pour plus d’informations sur la lecture des diagrammes de séquence UML, consultez [diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md). Pour plus d’informations sur le dessin des diagrammes de séquence UML, consultez [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).  
  
## <a name="properties-of-elements"></a>Propriétés des éléments  
  
|Propriété|Par défaut|Élément|Description|  
|--------------|-------------|-------------|-----------------|  
|**Name**|Nom par défaut|Tous|Identifie l'élément.|  
|**Nom qualifié**|Package :: Nom|Tous|Identifie l'élément de manière unique. A pour préfixe le nom qualifié du package qui le contient.|  
|**Éléments de travail**|{0} associé|Tous|Nombre d'éléments de travail associés à cet élément. Pour associer des éléments de travail, consultez [lier des éléments de modèle et des éléments de travail](../modeling/link-model-elements-and-work-items.md).|  
|**Description**|(vide)|Tous|Vous pouvez consigner des remarques générales concernant l'élément.|  
|**Couleur**|(valeur par défaut pour le type d'élément)|Ligne de vie, Message|Couleur de la forme. Il s'agit d'une propriété de la forme, plutôt que de l'élément qu'elle affiche.|  
|**Type**|(vide)|Ligne de vie|Type de l'instance que représente la ligne de vie.<br /><br /> Si un symbole de référence est affiché dans l'en-tête de la ligne de vie, cela signifie que cette classe ou interface existe séparément dans l'Explorateur de modèles UML et qu'elle peut être affichée dans un diagramme de classes.|  
|**Acteur**|False|Ligne de vie|Indique si la ligne de vie représente un utilisateur, un périphérique ou un composant logiciel qui est externe au composant décrit par ce diagramme.|  
|**Type**|**Complète** -un message qui a l’expéditeur et récepteur.<br /><br /> **Trouvé** -un message qui a un expéditeur non spécifié.<br /><br /> **Perdu** -un message qui a un destinataire non spécifié.|Message|Indique les extrémités d'un message qui sont attachées à une ligne de vie.<br /><br /> Vous ne pouvez pas modifier cette propriété. Elle est définie quand vous créez le message.|  
|**Tri**|**AsynchCall** -message asynchrone.<br /><br /> **SynchCall** -un message synchrone.<br /><br /> **Réponse** -la partie de retournée d’un message synchrone.<br /><br /> **CreateMessage** -message de création d’instance.|Message|Type de message. Vous ne pouvez pas modifier cette propriété. Elle est déterminée par l'outil que vous utilisez pour créer le message.|  
|**Opération**|(vide)|Message|Méthode appelée par le message dans la ligne de vie de réception.<br /><br /> Visible uniquement si la ligne de vie de réception est liée à une interface ou à une classe.|  
|**Fait référence à**|Diagramme de séquence|Utilisation d'interaction|Diagramme de séquence appelé par cette utilisation d'interaction.|  
|**Opérateur d’interaction**|Définie lorsque vous avez utilisé le **entourer** commande|Fragment combiné|Opérateur représenté par ce fragment ou cette collection de fragments.|  
|**Guard**|(vide)|Opérande d'interaction dans un fragment combiné|La séquence du fragment ne se produit que si la garde a la valeur true.<br /><br /> Pour sélectionner le fragment supérieur d'un fragment combiné, cliquez sous le titre du fragment.|  
|**Min, Max.**|(aucune restriction)|Fragment combiné Loop|Nombre minimal et maximal d'exécutions de la boucle.|  
|**Messages**|(vide)|Fragments combinés<br /><br /> Consider et Ignore|Messages qui sont pris en compte ou ignorés dans ce fragment.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de séquence UML : référence](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Décrire le flux de contrôle avec des fragments dans les diagrammes de séquence UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md)



