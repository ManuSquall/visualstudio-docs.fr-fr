---
title: Vue d’ensemble de l’interface utilisateur des Outils Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bffb1f7fe6449f078c21c14b0a070cbd23db539
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652137"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Vue d'ensemble de l'interface utilisateur des outils de langage spécifique à un domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous ouvrez pour la première fois une solution des Outils Domain-Specific Language (Outils DSL) dans [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], l’interface utilisateur ressemble à l’image suivante.

 ![Concepteur dsl](../modeling/media/dsl-designer.png "dsl_designer")

 Le tableau suivant explique comment les parties de l’interface utilisateur sont utilisées.

|**Élément**|**Définition**|
|-----------------|--------------------|
|Diagramme|Le diagramme affiche le modèle de domaine.<br /><br /> Le diagramme comporte deux parties. Une partie définit les types des éléments de vos modèles. L’autre partie définit comment vos modèles apparaissent à l’écran.|
|Boîte à outils|Faites glisser les outils de la boîte à outils vers le diagramme pour ajouter des classes de domaine et des types de forme. Pour ajouter des connecteurs, des relations et des mappages de formes, cliquez sur l’outil, sur le nœud source du diagramme, puis sur le nœud cible.|
|explorateur DSL|L’**Explorateur DSL** s’affiche lorsqu’une définition DSL est la fenêtre active. Il montre le langage DSL sous forme d’arborescence. L’Explorateur DSL vous permet de modifier les fonctionnalités du modèle qui ne sont pas affichées sur le diagramme. Par exemple, vous pouvez ajouter des éléments de boîte à outils et basculer sur le processus de validation à l’aide de l’**Explorateur DSL**.|
|Fenêtre Détails DSL|La fenêtre **Détails DSL** montre les propriétés des éléments du modèle de domaine qui vous permettent de contrôler la façon dont les éléments sont affichés, copiés et supprimés.<br /><br /> Par défaut, la fenêtre **Détails DSL** s’affiche à côté des fenêtres **Liste d’erreurs** et **Sortie**.|

## <a name="the-domain-model-diagram"></a>Diagramme du modèle de domaine
 Le diagramme du modèle de domaine est divisé en deux parties. Une partie du diagramme montre les éléments et les relations du modèle. L’autre partie montre comment le modèle doit être affiché et inclut les formes qui sont utilisées pour afficher les éléments et les propriétés du diagramme de modèle. L’image suivante montre les éléments du diagramme.

 ![Concepteur dsl avec couloir](../modeling/media/dsl-desinger.png "dsl_desinger")

 Le tableau suivant décrit certains des éléments du diagramme du modèle de domaine.

|**Terme**|**Définition**|
|--------------|--------------------|
|Classe de domaine|Les classes de domaine sont les types d’éléments de vos modèles.<br /><br /> Une classe de domaine peut apparaître plusieurs fois dans un diagramme, si elle est la cible de plusieurs relations.<br /><br /> Pour ajouter une classe de domaine, faites glisser l’outil de classe de domaine depuis la **Boîte à outils** vers la partie **Classes et relations** du diagramme.|
|Relation de domaine|Les relations de domaine sont les types de liens entre les éléments de vos modèles.<br /><br /> Une *relation d’incorporation* indique que l’élément cible est détenu ou contenu par l’élément source et apparaît sous la forme d’une ligne pleine. Chaque élément d’un modèle doit être la cible d’une relation d’incorporation afin que le modèle forme une arborescence. Une *relation de référence* indique un lien général entre les éléments de modèle et apparaît sous la forme d’une ligne en pointillés. Les éléments peuvent avoir n’importe quel nombre de liens de référence.<br /><br /> Créez une relation en cliquant sur l’outil dans la **Boîte à outils**, sur la classe de domaine source, puis sur la classe cible.|
|Formes et connecteurs|Les formes spécifient comment les éléments de modèle doivent être affichés sur un diagramme DSL. Les connecteurs spécifient les lignes d’un diagramme DSL qui peuvent être utilisées pour afficher les relations.<br /><br /> Pour créer une forme ou un connecteur, faites glisser l’outil dans la partie **Éléments du diagramme** du diagramme.|
|Mappages de formes|Une carte de forme s’affiche sous forme de ligne sur le diagramme du modèle de domaine et lie une forme à la classe de domaine qu’elle affiche, ou un connecteur à la relation de domaine qu’elle affiche.|

## <a name="see-also"></a> Voir aussi
 [Aperçu des outils linguistiques spécifiques au domaine](../modeling/overview-of-domain-specific-language-tools.md) Des [outils linguistiques Glossaires](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) [Personnalisation et extension d’une langue spécifique au domaine](../modeling/customizing-and-extending-a-domain-specific-language.md)
