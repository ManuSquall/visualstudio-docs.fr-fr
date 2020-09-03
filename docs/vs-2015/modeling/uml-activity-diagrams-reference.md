---
title: 'Diagrammes d’activités UML : référence | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 960e9469290bca42abd252d497c2ce72e62e41a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85531532"
---
# <a name="uml-activity-diagrams-reference"></a>Diagrammes d'activités UML : référence
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *diagramme d’activités* montre un processus d’entreprise ou un processus logiciel sous la forme d’un workflow à travers une série d’actions. Ces actions peuvent être effectuées par des personnes, des composants logiciels ou des ordinateurs.

 Vous pouvez utiliser un diagramme d'activités pour décrire des processus de plusieurs types, par exemple :

- Un processus métier ou un flux de travail entre les utilisateurs et votre système. Pour plus d’informations, consultez [Configuration requise](../modeling/model-user-requirements.md)pour les utilisateurs du modèle.

- Les étapes exécutées dans un cas d'usage. Pour plus d’informations, consultez [diagrammes de cas d’usage UML : indications](../modeling/uml-use-case-diagrams-guidelines.md).

- Un protocole logiciel, autrement dit les séquences autorisées d'interactions entre les composants.

- Un algorithme logiciel.

  Cette rubrique décrit les éléments que vous pouvez utiliser sur les diagrammes d'activités. Pour plus d’informations sur le dessin des diagrammes d’activités, consultez [diagrammes d’activités UML : instructions](../modeling/uml-activity-diagrams-guidelines.md). Pour créer un diagramme d’activités UML, dans le menu **architecture** , cliquez sur **nouveau diagramme UML ou diagramme de couche**. Pour plus d’informations sur la façon de dessiner des diagrammes de modélisation en général, consultez [modifier des modèles et des diagrammes UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Lecture des diagrammes d'activités
 Les tableaux fournis dans les sections suivantes décrivent les éléments que vous pouvez utiliser sur un diagramme d'activités et leurs principales propriétés. Pour obtenir la liste complète des propriétés des éléments, consultez [propriétés d’éléments sur les diagrammes d’activités UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Les actions et autres éléments qui apparaissent dans un diagramme d'activités forment une activité. Vous pouvez voir l'activité dans l'Explorateur de modèles UML. Il est créé quand vous ajoutez le premier élément au diagramme.

 Pour lire un diagramme, imaginez qu'un jeton, ou thread de contrôle, passe le long des connecteurs d'une action à la suivante.

### <a name="simple-control-flows"></a>Flux de contrôle simples
 Vous pouvez montrer une séquence d'actions avec des branches et des boucles. Pour plus d’informations sur l’utilisation des éléments décrits ici, consultez la section Description du workflow de contrôle de la rubrique [diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md).

 ![Flux de contrôle simple](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

|**Forme**|**Element**|**Description et principales propriétés**|
|-|-|-|
|1|**Action**|Une étape dans l'activité, dans laquelle les utilisateurs ou les logiciels effectuent une tâche.<br /><br /> L'action peut démarrer quand un jeton est arrivé à tous ses flux entrants. Quand elle se termine, les jetons sont envoyés à tous les flux sortants.<br /><br /> -   **Corps** : spécifie l’action en détail.<br />-   **Language** : langage de l’expression dans le corps.<br />-   **Post-conditions locales** : contraintes qui doivent être satisfaites lorsque l’exécution se termine. Objectif atteint par l'action.<br />-   **Conditions** préalables locales : contraintes qui doivent être satisfaites avant le début de l’exécution.|
|2|**Flux de contrôle**|Connecteur qui montre le flux de contrôle entre des actions. Pour interpréter le diagramme, imaginez qu'un jeton s'écoule d'une action à la suivante.<br /><br /> Pour créer un workflow de contrôle, utilisez l’outil **connecteur** .|
|3|**Nœud initial**|Indique la ou les premières actions dans l'activité. Quand l'activité démarre, un jeton s'écoule à partir du nœud initial.|
|4|**Nœud final de l'activité**|Fin de l'activité. Quand un jeton arrive, l'activité se termine.|
|5|**Nœud de décision**|Branche conditionnelle dans un flux. Possède une entrée et plusieurs sorties. Un jeton entrant émerge d'une seule des sorties.|
|6|**Guard**|Condition qui indique si un jeton peut s'écouler le long d'un connecteur. Utilisé le plus souvent sur les flux sortants d'un nœud de décision.<br /><br /> Pour définir une protection, cliquez avec le bouton droit sur un Flow, cliquez sur **Propriétés** , puis définissez la propriété **garde** .|
|7|**Nœud de fusion**|Nécessaire pour fusionner des flux qui ont été fractionnés avec un nœud de décision. Possède plusieurs entrées et une sortie. Un jeton sur une entrée quelconque émerge sur la sortie.|
|8|**Commentaire**|Fournit des informations supplémentaires sur les éléments auxquels il est lié.|
|9|**Action Appeler un comportement**|Action qui est définie plus en détail sur un autre diagramme d'activités.<br /><br /> -   **IsSynchronous** : si la valeur est true, l’action attend jusqu’à ce que l’activité se termine.<br />-   **Comportement** : activité appelée.|
|(non affiché)|**Action Appeler une opération**|Action qui appelle une opération sur une instance d'une classe.|
||**Activité**|Flux de travail qui est représenté par un diagramme d'activités. Pour afficher les propriétés d’une activité, vous devez la sélectionner dans l' **Explorateur de modèles UML**.<br /><br /> -   **Est en lecture seule** -si la valeur est true, l’activité ne doit pas modifier l’état d’un objet.<br />-   **Est une exécution unique** : si la valeur est true, il y a au plus une exécution de ce diagramme à la fois.|
||**Diagramme d’activités UML**|Diagramme qui affiche une activité. Pour afficher ses propriétés, cliquez sur une partie vide du diagramme. **Remarque :**  Les noms du diagramme d’activités, le fichier qui contient le diagramme et l’activité affichée par le diagramme peuvent tous être différents.|

### <a name="concurrent-flows"></a>Flux simultanés
 Vous pouvez décrire des séquences d'actions qui s'exécutent en même temps. Pour plus d'informations, consultez Dessin de flux simultanés.

 ![Diagramme d'activités montrant le flux simultané](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

|**Forme**|**Element**|**Description**|
|-|-|-|
|11|**Nœud de bifurcation**|Divise un flux unique en flux simultanés. Chaque jeton entrant produit un jeton sur chaque connecteur sortant.|
|12|**Nœud de jointure**|Combine des flux simultanés en un flux unique. Quand chaque flux entrant a un jeton en attente, un jeton est produit sur la sortie.|
|13|**Action Envoyer un signal**|Action qui envoie un message ou un signal à une autre activité ou à un thread simultané dans la même activité. Le type et le contenu du message sont déduits du titre de l'action ou spécifiés dans des commentaires supplémentaires.<br /><br /> L'action peut envoyer des données dans le signal, qui peuvent être passées à l'action dans un flux d'objet ou une broche d'entrée (16).|
|14|**Action Accepter un événement**|Action qui attend la réception d'un message ou d'un signal pour continuer l'action. Le type du message que l'action peut recevoir est déduit du titre ou spécifié dans des commentaires supplémentaires.<br /><br /> Si l'action n'a aucun flux de contrôle entrant, elle produit un jeton chaque fois qu'elle reçoit un message.<br /><br /> L'action peut recevoir des données dans le signal, qui peuvent être passées dans un flux d'objet ou une broche d'entrée (17).<br /><br /> -   **IsUnmarshall** : si la valeur est true, il peut y avoir plusieurs broches de sortie typées et les données sont démarshalées sur elles. Si la valeur est false, toutes les données apparaissent sur une seule broche.|

### <a name="data-flows"></a><a name="DataFlow"></a> Flux de données
 Vous pouvez décrire le flux de données d'une action à une autre. Pour plus d'informations sur les éléments utilisés dans cette section, consultez la section Dessin de flux de données de la rubrique Instructions pour dessiner un diagramme d'activités.

 ![Diagramme d'activités montrant le flux de données](../modeling/media/uml-actovdata.png "UML_ActOvData")

|**Forme**|**Element**|**Description**|
|-|-|-|
|15|**Nœud d’objet**|Représente des données qui passent le long d'un flux.<br /><br /> -   **Classement** : comment plusieurs jetons sont stockés.<br />-   **Selection** : appelle un processus, qui peut être défini dans un autre diagramme, qui filtre les données.<br />-   Limite **supérieure** -0 indique que les données doivent passer directement le long du fluide ; \*indique que les données peuvent être stockées dans le Flow.<br />-   **Type** : type des objets stockés et transmis.|
|16|**Broche d'entrée**|Représente des données qu'une action peut recevoir quand elle s'exécute.<br /><br /> -   **Type** : type des objets transmis.|
|17|**Broche de sortie**|Représente des données qu'une action produit quand elle s'exécute.<br /><br /> -   **Type** : type des objets transmis.|
|18|**Nœud de paramètre de l'activité**|Nœud d'objet via lequel des données peuvent être reçues ou  produites par l'activité.<br /><br /> Utilisé quand l'activité représentée par le diagramme est appelée à partir d'une autre activité ou quand le diagramme décrit une opération ou une fonction.<br /><br /> -   **Type** : type des objets transmis.|
|(non affiché)|**Flux d'objet**|Connecteur qui montre le flux de données entre des actions et des nœuds d'objets.<br /><br /> Pour créer un workflow d’objet, utilisez l’outil **connecteur** pour lier une broche d’entrée ou de sortie ou un nœud d’objet à un autre élément.<br /><br /> -   **Selection** : appelle un processus, qui peut être défini dans un autre diagramme, qui filtre les données.<br />-   **Transformation** : appelle un processus, qui peut être défini dans un autre diagramme, qui transforme les données.<br />-   **IsMulticast** : indique qu’il peut y avoir plusieurs objets ou composants destinataires.<br />-   **IsMultireceive** : indique que les entrées peuvent être reçues à partir de plusieurs objets ou composants.|

## <a name="see-also"></a>Voir aussi
 [Modifier des diagrammes et des modèles UML](../modeling/edit-uml-models-and-diagrams.md) [diagrammes d’activités UML : indications](../modeling/uml-activity-diagrams-guidelines.md)
