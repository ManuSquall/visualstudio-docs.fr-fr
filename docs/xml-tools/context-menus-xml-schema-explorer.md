---
title: Menus contextuels dans l’Explorateur de schémas XML
description: Découvrez les menus contextuels de l’Explorateur de schémas XML qui contiennent des éléments permettant d’effectuer des recherches spécifiques au schéma et d’autres opérations.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c5d78196a64ca0ab2067d0df73410c41cbeca35
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049163"
---
# <a name="context-menus-xml-schema-explorer"></a>Menus contextuels (Explorateur de schémas XML)

Un menu contextuel est le menu qui s’affiche lorsque vous cliquez avec le bouton droit sur un événement. Les éléments de menu contextuel suivants vous permettent d'effectuer des recherches spécifiques au schéma et d'autres opérations.

## <a name="node-type-schema-set"></a>Type de nœud : ensemble de schémas

Le tableau suivant décrit les options disponibles pour un nœud de type jeu de schémas.

|Option|Description|
|-|-----------------|
|**Afficher les éléments racines les plus probables**|Recherche et met en surbrillance tous les éléments globaux qui ne sont pas référencés à partir d'éléments globaux autres qu'eux-mêmes.|
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans le jeu de schémas.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans le jeu de schémas.|
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-namespace"></a>Type de nœud : espace de noms
Le tableau suivant décrit les options disponibles pour un nœud de type espace de noms.

|Option|Description|
|-|-----------------|
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance les fichiers qui importent l'espace de noms sélectionné.|
|**Afficher toutes les références sortantes**|Pour chaque fichier de l'espace de noms sélectionné, recherche et met en surbrillance les éléments suivants :<br /><br /> -Tous les espaces de noms référencés dans les instructions Import sans `schemaLocation` attribut.<br />-Tous les fichiers dans les espaces de noms autres que celui sélectionné qui sont spécifiés dans l' `schemaLocation` attribut dans les instructions import et include.|
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans l'espace de noms sélectionné.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans l'espace de noms sélectionné.|
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-file"></a>Type de nœud : fichier
Le tableau suivant décrit les options disponibles pour un nœud de type fichier.

|Option|Description|
|-|-----------------|
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance tous les fichiers qui spécifient le fichier sélectionné dans les attributs `schemaLocation` de leurs instructions include et import.|
|**Afficher toutes les références sortantes**|Recherche et met en surbrillance les éléments suivants :<br /><br /> -Tous les espaces de noms spécifiés dans les attributs d’espace de noms de toutes les instructions Import qui n’ont pas l' `schemaLocation` attribut.<br />-Tous les fichiers spécifiés dans les `schemaLocation` attributs de toutes les instructions import et include.|
|**Afficher les types globaux**|Recherche et met en surbrillance tous les types globaux dans ce fichier.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans ce fichier.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément sélectionné dans l’Explorateur de schémas XML est également sélectionné dans l’éditeur XML.|
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

## <a name="all-global-node-types"></a>Tous les types de nœuds globaux
Le tableau suivant décrit les options disponibles pour tous les nœuds globaux.

|Option|Description|
|-|-----------------|
|**Afficher dans la vue du graphique**|Ouvre la vue du graphique. Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|
|**Afficher dans la vue de modèle de contenu**|Ouvre la vue de modèle de contenu. Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l’éditeur XML. L’élément sélectionné dans l’Explorateur de schémas XML est également sélectionné dans l’éditeur XML.|
|**Fenêtre Propriétés**|Ouvre la fenêtre **Propriétés** (si elle n’est pas déjà ouverte). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-element"></a>Type de nœud : élément
En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds d'élément comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition du type**|Navigue vers la définition de type de l'élément sélectionné. Ceci s'applique lorsque le type utilisé pour l'élément est un type global.|
|**Aller à l'élément d'origine**|Pour les références d'élément, navigue vers la définition réelle de l'élément.|
|**Afficher toutes les références**|Pour les éléments globaux, recherche et met en surbrillance toutes les références (éléments qui ont `ref="selectedElement"`) à l'élément sélectionné.|
|**Afficher les membres du groupe de substitution**|Pour les en-têtes d'un groupe de substitution, recherche et met en surbrillance tous les éléments qui sont membres du groupe de substitution dont l'élément sélectionné est membre. Cela permet d'afficher les participants directs et indirects.|
|**Afficher les en-têtes du groupe de substitution**|Pour les éléments globaux qui sont membres d'un groupe de substitution, recherche et met en surbrillance tous les en-têtes directs et indirects de l'élément sélectionné, notamment :<br /><br /> : Un en-tête de groupe de substitution spécifié sur l’élément sélectionné.<br />: En-tête de groupe de substitution spécifié sur son élément head.|
|**Générer un exemple de code XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|

## <a name="node-type-global-types"></a>Type de nœud : types globaux
En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds de type global comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Afficher le type de base**|Si le type sélectionné est dérivé d'un type global, navigue vers le type de base du type sélectionné.|
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références au type sélectionné. Ceci inclut les éléments et attributs du type sélectionné ainsi que les types dérivés du type sélectionné.|
|**Afficher tous les types dérivés**|Recherche et met en surbrillance tous les types qui sont directement et indirectement dérivés du type sélectionné.|
|**Afficher tous les ancêtres**|Affiche tous les types parents (de base).|

## <a name="node-type-attribute"></a>Type de nœud : attribut
En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds d'attribut comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition du type**|Lorsque le type utilisé pour l'attribut est un type global, navigue vers la définition de type de l'attribut sélectionné.|
|**Aller à l'attribut d'origine**|Pour les références d'attribut, navigue vers la définition réelle de l'attribut.|
|**Afficher toutes les références**|Pour les attributs globaux, recherche et met en surbrillance toutes les références (autres attributs qui ont `ref="selectedAttribute"`) à l'attribut sélectionné.|

## <a name="node-type-attribute-group"></a>Type de nœud : groupe d’attributs
En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds d'attribut comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition**|Pour les références, navigue vers la définition réelle de l'attribut.|
|**Afficher tous les membres**|Recherche et met en surbrillance tous les membres du groupe d'attributs.|
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références (groupes d'attributs qui ont `ref="selectedAttributeGroup"`) au groupe d'attributs sélectionné.|

## <a name="node-type-named-group"></a>Type de nœud : groupe nommé
En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds de groupe nommé comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition**|Pour les références, navigue vers la définition réelle de l'attribut.|
|**Afficher tous les membres**|Recherche et met en surbrillance tous les membres du groupe nommé.|
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références (groupes qui ont `ref="selectedGroup"`) au groupe sélectionné.|

## <a name="see-also"></a>Voir aussi

- [Explorateur de schémas XML](../xml-tools/xml-schema-explorer.md)
- [Recherche dans le jeu de schémas](../xml-tools/searching-the-schema-set.md)
