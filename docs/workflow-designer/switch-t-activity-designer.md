---
title: Concepteur d’activités Concepteur de flux de travail-Switch &lt; T &gt;
description: Découvrez comment utiliser le <T> Concepteur d’activités Switch pour créer et configurer une <T> activité Switch dans le concepteur de flux de travail.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6bdf05878c08b1c175b78ff2205b74c4ea5669b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433932"
---
# <a name="switcht-activity-designer"></a>Concepteur d’activités Switch\<T>

L'activité <xref:System.Activities.Statements.Switch%601> évalue une expression spécifiée et exécute l'activité à partir d'une collection d'activités dont la clé associée correspond à la valeur obtenue de l'évaluation.

Le concepteur d’activités **Switch<T \>** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Switch%601> activité dans le concepteur de flux de travail.

## <a name="the-switchtactivity"></a>Activité Switch \<T>

Une activité <xref:System.Activities.Statements.Switch%601> contient une propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et un dictionnaire de propriétés <xref:System.Activities.Statements.Switch%601.Cases%2A>. Chaque cas dans le dictionnaire se compose d’une paire qui contient une *clé* et une activité qui sert de *valeur* correspondante. L'activité <xref:System.Activities.Statements.Switch%601> évalue la propriété <xref:System.Activities.Statements.Switch%601.Expression%2A> et la compare à chacune des clés. Si une correspondance est trouvée, l'activité correspondante est exécutée. Une seule correspondance est possible, car les clés de dictionnaire doivent être uniques par rapport au type d'égalité défini par le comparateur d'égalité du dictionnaire. Si aucune correspondance n'est trouvée, l'activité <xref:System.Activities.Statements.Switch%601.Default%2A> est exécutée.

## <a name="how-to-use-the-switcht-activity-designer"></a>Comment utiliser le concepteur d' \<T> activités Switch

Accédez au concepteur d’activités **\<T> switch** dans la catégorie **Flow Control** de la **boîte à outils**. Après l’avoir supprimée dans le Concepteur de flux de travail, il affiche la boîte de dialogue **Sélectionner les types** pour permettre à l’utilisateur de spécifier le type générique *T* utilisé dans l' <xref:System.Activities.Statements.Switch%601> activité. La valeur par défaut est **Int32**. Une fois que le type générique *t* a été sélectionné, un **commutateur \><t** Designer est ajouté dans le concepteur de Workflow.

Voici les propriétés du **commutateur<T \>** designer. Toutes ces propriétés peuvent être modifiées dans la grille des propriétés. Certaines peuvent également être modifiées dans l'aire du concepteur.

Le tableau suivant répertorie les propriétés de l'activité <xref:System.Activities.Statements.Switch%601> qui sont les plus utiles et décrit comment elles sont utilisées dans le concepteur.

|Nom de la propriété|Obligatoire|Usage|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Spécifie le nom convivial du concepteur d'activités <xref:System.Activities.Statements.Switch%601>. La valeur par défaut est Switch<Int32 \> . La valeur peut être modifiée dans la fenêtre **Propriétés** ou directement dans l’en-tête du concepteur.<br /><br /> Bien que la propriété <xref:System.Activities.Activity.DisplayName%2A> ne soit pas strictement obligatoire, il est recommandé d'en utiliser une.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Vrai|Spécifie l'expression à comparer aux clés dans la collection de cas pour déterminer le cas à exécuter.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Spécifie l'activité exécutée si aucune correspondance n'est trouvée. Cliquez sur le bouton **Ajouter une activité** dans le concepteur pour ouvrir la zone **par défaut** dans laquelle l’activité peut être supprimée.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Spécifie les cas à évaluer. Pour ajouter un cas, cliquez sur le bouton **Ajouter un nouveau cas** en bas du concepteur de **commutateur \<T>** . Le bouton se transforme en zone de texte (zone de liste déroulante si le type générique sélectionné lors de l’ajout du commutateur \<T> est une chaîne ou une énumération). Après l’ajout d’une clé dans la zone **valeur de cas** , la zone de cas se développe et une activité peut être supprimée là où le texte d’indication « déposer l’activité ici » pour définir la logique d’exécution du cas.|

Plusieurs cas peuvent être ajoutés tant que les clés de cas ne sont pas dupliquées. Sinon, une boîte de dialogue d'erreur s'affiche pour signaler que la clé de cas spécifiée existe déjà et que vous devez en choisir une autre. Dans le concepteur de **commutateur \<T>** , une seule zone de cas peut être développée à la fois. Si une zone de cas est affiché en mode réduit, cliquez dessus pour la développer. Notez que lorsqu'un cas est affiché en mode réduit, le concepteur place le nom d'affichage de l'activité (si elle existe) à l'intérieur du cas, à droite. Dans le cas contraire, il affiche le bouton **Ajouter une activité** qui développe le cas si vous cliquez dessus et vous permet d’ajouter une activité.

Cliquer sur la clé d'un cas existant transforme l'apparence de cette dernière d'étiquette en zone de texte afin que vous puissiez la modifier.

Vous disposez de 2 méthodes pour supprimer un cas :

- Sélectionnez le cas et supprimez-le.

- Sélectionnez le cas, cliquez avec le bouton droit pour afficher le menu contextuel et sélectionnez **supprimer**.

Notez que vous devez sélectionner le cas lui-même pour le supprimer. La sélection et la suppression de l'activité à l'intérieur d'un cas supprime uniquement l'activité mais pas le cas.

## <a name="see-also"></a>Voir aussi

- [Flux de contrôle](../workflow-designer/control-flow-activity-designers.md)
