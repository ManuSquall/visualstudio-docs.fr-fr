---
title: 'Diagrammes de séquence UML : Référence | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 5c92d9eb8ee7858a036fdbb8dfb621c269e3ed4c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797024"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagrammes de séquence UML : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, un *diagramme de séquence* montre une interaction, qui représente la séquence de messages entre des instances de classes, les composants, les sous-systèmes ou acteurs. Le diagramme suit une chronologie de haut en bas et il montre le flux de contrôle d'un participant à un autre. Utilisez des diagrammes de séquence pour visualiser des instances et des événements, plutôt que des classes et des méthodes. Plusieurs instances du même type peuvent apparaître dans le diagramme. Plusieurs occurrences du même message peuvent également apparaître.  
  
 Les diagrammes de séquence UML font partie d'un modèle UML et ils existent uniquement dans des projets de modélisation UML. Pour créer un diagramme de séquence UML, dans le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**. Découvrez comment créer et dessiner [diagrammes de séquence UML](../modeling/uml-sequence-diagrams-guidelines.md) ou [diagrammes de modélisation UML](../modeling/edit-uml-models-and-diagrams.md) en général.  
  
 Pour connaître les versions de Visual Studio qui prennent en charge cette fonctionnalité, consultez [Prise en charge des versions pour les outils d'architecture et de modélisation](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-sequence-diagrams"></a>Lecture des diagrammes de séquence  
 Le tableau suivant décrit les éléments visibles dans un diagramme de séquence. En savoir plus sur ces [propriétés des éléments](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).  
  
 ![Parties d’un diagramme de séquence](../modeling/media/uml-sequence.png "UML_Sequence")  
  
|**Forme**|**Élément**|**Description**|  
|---------------|-----------------|---------------------|  
|1|**Ligne de vie**|Ligne verticale qui représente la séquence d'événements qui se produisent dans un participant pendant une interaction, pendant que le temps s'écoule le long de la ligne, vers le bas. Ce participant peut être une instance d'une classe, d'un composant ou d'un acteur.|  
|2|**Acteur**|Participant qui est externe au système que vous développez.<br /><br /> Vous pouvez afficher un symbole d’acteur en haut d’une ligne de vie en définissant son **acteur** propriété.|  
|3|**Message synchrone**|L'expéditeur attend une réponse à un message synchrone avant de continuer. Le diagramme montre l'appel et le retour. Les messages synchrones servent à représenter des appels de fonctions ordinaires dans un programme, ainsi que d'autres genres de messages qui se comportent de la même façon.|  
|4|**Message asynchrone**|Message qui ne nécessite pas de réponse pour que l'expéditeur continue. Un message asynchrone montre uniquement un appel de l'expéditeur. Permet de représenter la communication entre des threads distincts ou la création d'un nouveau thread.|  
|5|**Occurrence d’exécution**|Rectangle grisé vertical affiché sur la ligne de vie d'un participant, qui représente la période pendant laquelle le participant exécute une opération.<br /><br /> L'exécution commence là où le participant reçoit un message. Si le message de départ était un message synchrone, l'exécution se termine avec une flèche de « retour » à l'expéditeur.|  
|6|**Message de rappel**|Message qui revient à un participant qui attend le retour d'un appel précédent. L'occurrence d'exécution résultante est affichée par-dessus l'occurrence existante.|  
|7|**Message personnel**|Message d'un participant à lui-même. L'occurrence d'exécution résultante est affichée par-dessus l'exécution expéditrice.|  
|8|**Créer le message**|Message qui crée un participant. Si un participant reçoit un message de création, il doit s'agir du premier qu'il reçoit.|  
|9|**Message trouvé**|Message asynchrone provenant d'un participant inconnu ou non spécifié.|  
|10|**Message perdu**|Message asynchrone destiné à un participant inconnu ou non spécifié.|  
|11|**Commentaire**|Vous pouvez attacher un commentaire à n'importe quel point sur une ligne de vie.|  
|12|**Utilisation d’interaction**|Joint une séquence de messages définis dans un autre diagramme.<br /><br /> Pour créer un **utilisation d’Interaction**, cliquez sur l’outil et puis faites glisser les lignes de vie que vous souhaitez inclure.|  
|13|**Fragment combiné**|Collection de fragments. Chaque fragment peut joindre un ou plusieurs messages. Il existe différents types de fragments combinés. Pour plus d’informations, consultez [Describe des flux de contrôle avec des fragments de diagrammes de séquence UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Pour créer un fragment, cliquez sur un message, pointez sur **entourer**, puis cliquez sur un type de fragment.|  
|14|**Garde de fragment**|Peut être utilisé pour déclarer une condition indiquant si le fragment aura lieu.<br /><br /> Pour définir la garde, sélectionnez un fragment, puis sélectionnez la garde et tapez une valeur.|  
|**X**|**Événement de destruction**|Représente le point auquel l'objet est supprimé ou n'est plus accessible. Apparaît en bas de chaque ligne de vie.|  
||**Interaction**|Collection de messages et de lignes de vie affichée dans le diagramme de séquence. Pour afficher les propriétés d’une Interaction, vous devez la sélectionner dans **Explorateur de modèles UML**.|  
||**Diagramme de séquence**|Diagramme qui montre une activité. Pour afficher ses propriétés, cliquez sur une partie vide du diagramme. **Remarque :** les noms du diagramme de séquence, l’Interaction qu’il affiche, et le fichier qui contient le diagramme peut tous être différents.|  
  
## <a name="see-also"></a>Voir aussi  
 [Diagrammes de séquence UML : indications](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes de cas d’usage UML : référence](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammes de classes UML : référence](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammes de composants UML : référence](../modeling/uml-component-diagrams-reference.md)   
 [Informations de référence sur les diagrammes de composants UML](../modeling/uml-component-diagrams-reference.md)



