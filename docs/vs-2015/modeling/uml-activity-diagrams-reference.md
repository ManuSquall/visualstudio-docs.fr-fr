---
title: 'Diagrammes d’activités UML : Référence | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: eed16e010c4fc070b9cc8be57731c97c2f03b2ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862279"
---
# <a name="uml-activity-diagrams-reference"></a>Diagrammes d'activités UML : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *diagramme d’activités* montre un processus d’entreprise ou un processus logiciel comme un flux de travail via une série d’actions. Ces actions peuvent être effectuées par des personnes, des composants logiciels ou des ordinateurs.  
  
 Vous pouvez utiliser un diagramme d'activités pour décrire des processus de plusieurs types, par exemple :  
  
- Un processus métier ou un flux de travail entre les utilisateurs et votre système. Pour plus d’informations, consultez [modéliser les besoins de l’utilisateur](../modeling/model-user-requirements.md).  
  
- Les étapes exécutées dans un cas d'usage. Pour plus d’informations, consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Un protocole logiciel, autrement dit les séquences autorisées d'interactions entre les composants.  
  
- Un algorithme logiciel.  
  
  Cette rubrique décrit les éléments que vous pouvez utiliser sur les diagrammes d'activités. Pour plus d’informations sur l’activité de dessin de diagrammes, consultez [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md). Pour créer un diagramme d’activités UML, sur le **Architecture** menu, cliquez sur **nouveau UML ou diagramme de couche**. Pour plus d’informations sur la façon de dessiner des diagrammes de modélisation en général, consultez [modèles et diagrammes UML modifier](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Lecture des diagrammes d'activités  
 Les tableaux fournis dans les sections suivantes décrivent les éléments que vous pouvez utiliser sur un diagramme d'activités et leurs principales propriétés. Pour obtenir une liste complète des propriétés des éléments, consultez [propriétés d’éléments des diagrammes d’activités UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Les actions et autres éléments qui apparaissent dans un diagramme d'activités forment une activité. Vous pouvez voir l'activité dans l'Explorateur de modèles UML. Il est créé quand vous ajoutez le premier élément au diagramme.  
  
 Pour lire un diagramme, imaginez qu'un jeton, ou thread de contrôle, passe le long des connecteurs d'une action à la suivante.  
  
### <a name="simple-control-flows"></a>Flux de contrôle simples  
 Vous pouvez montrer une séquence d'actions avec des branches et des boucles. Pour plus d’informations sur la façon d’utiliser les éléments décrits ici, consultez la section Description du flux de contrôle de la rubrique [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Un flux de contrôle simple](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Forme**|**Élément**|**Description et principales propriétés**|  
|1|**Action**|Une étape dans l'activité, dans laquelle les utilisateurs ou les logiciels effectuent une tâche.<br /><br /> L'action peut démarrer quand un jeton est arrivé à tous ses flux entrants. Quand elle se termine, les jetons sont envoyés à tous les flux sortants.<br /><br /> -   **Corps** -Spécifie l’action de manière détaillée.<br />-   **Langue** -la langue de l’expression dans le corps.<br />-   **Post-conditions locales** -contraintes qui doivent être remplies lors de la fin de l’exécution. Objectif atteint par l'action.<br />-   **Local Preconditions** -contraintes qui doivent être satisfaites avant le début de l’exécution.|  
|2|**Flux de contrôle**|Connecteur qui montre le flux de contrôle entre des actions. Pour interpréter le diagramme, imaginez qu'un jeton s'écoule d'une action à la suivante.<br /><br /> Pour créer un flux de contrôle, utilisez la **connecteur** outil.|  
|3|**Nœud initial**|Indique la ou les premières actions dans l'activité. Quand l'activité démarre, un jeton s'écoule à partir du nœud initial.|  
|4|**Nœud Final de l’activité**|Fin de l'activité. Quand un jeton arrive, l'activité se termine.|  
|5|**Nœud de décision**|Branche conditionnelle dans un flux. Possède une entrée et plusieurs sorties. Un jeton entrant émerge d'une seule des sorties.|  
|6|**Guard**|Condition qui indique si un jeton peut s'écouler le long d'un connecteur. Utilisé le plus souvent sur les flux sortants d'un nœud de décision.<br /><br /> Pour définir un garde, cliquez sur un flux, cliquez sur **propriétés** puis définissez la **protéger** propriété.|  
|7|**Nœud de fusion**|Nécessaire pour fusionner des flux qui ont été fractionnés avec un nœud de décision. Possède plusieurs entrées et une sortie. Un jeton sur une entrée quelconque émerge sur la sortie.|  
|8|**Commentaire**|Fournit des informations supplémentaires sur les éléments auxquels il est lié.|  
|9|**Action appeler un comportement**|Action qui est définie plus en détail sur un autre diagramme d'activités.<br /><br /> -   **IsSynchronous** : si la valeur est true, l’action patiente jusqu'à ce que l’activité se termine.<br />-   **Comportement** -activité appelée.|  
|(non affiché)|**Action appeler une opération**|Action qui appelle une opération sur une instance d'une classe.|  
||**Activité**|Flux de travail qui est représenté par un diagramme d'activités. Pour afficher les propriétés d’une activité, vous devez la sélectionner dans **Explorateur de modèles UML**.<br /><br /> -   **Est en lecture seule** : si la valeur est true, l’activité ne doit pas modifier l’état de n’importe quel objet.<br />-   **Is Single Execution** : si la valeur est true, il existe au plus une exécution de ce diagramme à la fois.|  
||**Diagramme d’activités UML**|Diagramme qui affiche une activité. Pour afficher ses propriétés, cliquez sur une partie vide du diagramme. **Remarque :** les noms du diagramme d’activités, le fichier qui contient le diagramme et l’activité affichée par le diagramme peut tous être différents.|  
  
### <a name="concurrent-flows"></a>Flux simultanés  
 Vous pouvez décrire des séquences d'actions qui s'exécutent en même temps. Pour plus d'informations, consultez Dessin de flux simultanés.  
  
 ![Diagramme d’activités montrant le flux simultané](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Forme**|**Élément**|**Description**|  
|11|**Nœud de bifurcation**|Divise un flux unique en flux simultanés. Chaque jeton entrant produit un jeton sur chaque connecteur sortant.|  
|12|**Joindre le nœud**|Combine des flux simultanés en un flux unique. Quand chaque flux entrant a un jeton en attente, un jeton est produit sur la sortie.|  
|13|**Action envoyer un Signal**|Action qui envoie un message ou un signal à une autre activité ou à un thread simultané dans la même activité. Le type et le contenu du message sont déduits du titre de l'action ou spécifiés dans des commentaires supplémentaires.<br /><br /> L'action peut envoyer des données dans le signal, qui peuvent être passées à l'action dans un flux d'objet ou une broche d'entrée (16).|  
|14|**Action Accepter un événement**|Action qui attend la réception d'un message ou d'un signal pour continuer l'action. Le type du message que l'action peut recevoir est déduit du titre ou spécifié dans des commentaires supplémentaires.<br /><br /> Si l'action n'a aucun flux de contrôle entrant, elle produit un jeton chaque fois qu'elle reçoit un message.<br /><br /> L'action peut recevoir des données dans le signal, qui peuvent être passées dans un flux d'objet ou une broche d'entrée (17).<br /><br /> -   **IsUnmarshall** : si la valeur est true, il peut y avoir plusieurs broches de sortie typées et données y sont démarshalées. Si la valeur est false, toutes les données apparaissent sur une seule broche.|  
  
###  <a name="DataFlow"></a> Flux de données  
 Vous pouvez décrire le flux de données d'une action à une autre. Pour plus d'informations sur les éléments utilisés dans cette section, consultez la section Dessin de flux de données de la rubrique Instructions pour dessiner un diagramme d'activités.  
  
 ![Diagramme d’activités montrant le flux de données](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Forme**|**Élément**|**Description**|  
|15|**Nœud d’objet**|Représente des données qui passent le long d'un flux.<br /><br /> -   **Classement** : manière dont plusieurs jetons sont stockés.<br />-   **Sélection** -appelle un processus, ce qui peut être défini dans un autre diagramme, qui filtre les données.<br />-   **Limite supérieure** -0 indique que les données doivent passer directement le long du flux ; \* indique que les données peuvent être stockées dans le flux.<br />-   **Type** -type des objets stockés et transmis.|  
|16|**Broche d’entrée**|Représente des données qu'une action peut recevoir quand elle s'exécute.<br /><br /> -   **Type** -le type des objets transmis.|  
|17|**Broche de sortie**|Représente des données qu'une action produit quand elle s'exécute.<br /><br /> -   **Type** -le type des objets transmis.|  
|18|**Nœud de paramètre d’activité**|Nœud d'objet via lequel des données peuvent être reçues ou  produites par l'activité.<br /><br /> Utilisé quand l'activité représentée par le diagramme est appelée à partir d'une autre activité ou quand le diagramme décrit une opération ou une fonction.<br /><br /> -   **Type** -le type des objets transmis.|  
|(non affiché)|**Flux d’objet**|Connecteur qui montre le flux de données entre des actions et des nœuds d'objets.<br /><br /> Pour créer un flux d’objet, utilisez le **connecteur** outil pour lier une entrée ou d’une broche de sortie ou d’un nœud d’objet à un autre élément.<br /><br /> -   **Sélection** -appelle un processus, ce qui peut être défini dans un autre diagramme, qui filtre les données.<br />-   **Transformation** -appelle un processus, ce qui peut être défini dans un autre diagramme, qui transforme les données.<br />-   **IsMulticast** -indique qu’il peut exister plusieurs objets ou composants destinataires.<br />-   **IsMultiReceive** -indique que les entrées peuvent être reçues à partir de plusieurs objets ou composants.|  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier des modèles UML et des diagrammes](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammes d’activités UML : conseils](../modeling/uml-activity-diagrams-guidelines.md)



