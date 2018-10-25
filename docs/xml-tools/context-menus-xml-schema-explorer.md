---
title: Menus contextuels dans l’Explorateur de schémas XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6f13a2dc434602819a423b8122a97675e332cab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939119"
---
# <a name="context-menus-xml-schema-explorer"></a>Menus contextuels (Explorateur de schémas XML)

Les éléments de menu contextuel suivants vous permettent d'effectuer des recherches spécifiques au schéma et d'autres opérations.

## <a name="node-type-schema-set"></a>Type de nœud : jeu de schémas

Le tableau suivant décrit les options disponibles pour un nœud de type jeu de schémas.

|Option|Description|
|-|-----------------|
|**Afficher les éléments racines les plus probables**|Recherche et met en surbrillance tous les éléments globaux qui ne sont pas référencés à partir d'éléments globaux autres qu'eux-mêmes.|
|**Afficher les Types globaux**|Recherche et met en surbrillance tous les types globaux dans le jeu de schémas.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans le jeu de schémas.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-namespace"></a>Type de nœud : Namespace
 Le tableau suivant décrit les options disponibles pour un nœud de type espace de noms.

|Option|Description|
|-|-----------------|
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance les fichiers qui importent l'espace de noms sélectionné.|
|**Afficher toutes les références sortantes**|Pour chaque fichier de l'espace de noms sélectionné, recherche et met en surbrillance les éléments suivants :<br /><br /> -Tous les espaces de noms référencés dans des instructions import sans un `schemaLocation` attribut.<br />-Tous les fichiers dans les espaces de noms autre que celui sélectionné qui sont spécifiés dans le `schemaLocation` d’attribut dans l’importation et d’inclure des instructions.|
|**Afficher les Types globaux**|Recherche et met en surbrillance tous les types globaux dans l'espace de noms sélectionné.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans l'espace de noms sélectionné.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-file"></a>Type de nœud : fichier
 Le tableau suivant décrit les options disponibles pour un nœud de type fichier.

|Option|Description|
|-|-----------------|
|**Afficher toutes les références entrantes**|Recherche et met en surbrillance tous les fichiers qui spécifient le fichier sélectionné dans les attributs `schemaLocation` de leurs instructions include et import.|
|**Afficher toutes les références sortantes**|Recherche et met en surbrillance les éléments suivants :<br /><br /> -Tous les espaces de noms spécifiés dans les attributs de l’espace de noms de toutes les instructions d’importation qui n’ont pas le `schemaLocation` attribut.<br />-Tous les fichiers spécifiés dans le `schemaLocation` attributs de toutes les instructions import et include.|
|**Afficher les Types globaux**|Recherche et met en surbrillance tous les types globaux dans ce fichier.|
|**Afficher les éléments globaux**|Recherche et met en surbrillance tous les éléments globaux dans ce fichier.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML. L'élément sélectionné dans l'Explorateur de schémas XML est également sélectionné dans l'Éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

## <a name="all-global-node-types"></a>Tous les types de nœuds globaux
 Le tableau suivant décrit les options disponibles pour tous les nœuds globaux.

|Option|Description|
|-|-----------------|
|**Afficher dans la vue du graphique**|Ouvre la vue du graphique. Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|
|**Afficher en vue de modèle de contenu**|Ouvre la vue de modèle de contenu. Si le nœud sélectionné n'est pas dans l'espace de travail, ajoute ce nœud à l'espace de travail et sélectionne le nœud.|
|**Afficher le code**|Ouvre le fichier qui contient le nœud sélectionné dans l'Éditeur XML. L'élément sélectionné dans l'Explorateur de schémas XML est également sélectionné dans l'Éditeur XML.|
|**Propriétés (fenêtre)**|Ouvre le **propriétés** fenêtre (si elle n’est pas déjà ouvert). Cette fenêtre affiche des informations sur le nœud.|

## <a name="node-type-element"></a>Type de nœud : élément
 En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds d'élément comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition de Type**|Navigue vers la définition de type de l'élément sélectionné. Ceci s'applique lorsque le type utilisé pour l'élément est un type global.|
|**Accédez à l’élément d’origine**|Pour les références d'élément, navigue vers la définition réelle de l'élément.|
|**Afficher toutes les références**|Pour les éléments globaux, recherche et met en surbrillance toutes les références (éléments qui ont `ref="selectedElement"`) à l'élément sélectionné.|
|**Afficher les membres du groupe de Substitution**|Pour les en-têtes d'un groupe de substitution, recherche et met en surbrillance tous les éléments qui sont membres du groupe de substitution dont l'élément sélectionné est membre. Cela permet d'afficher les participants directs et indirects.|
|**Afficher le groupe de Substitution têtes**|Pour les éléments globaux qui sont membres d'un groupe de substitution, recherche et met en surbrillance tous les en-têtes directs et indirects de l'élément sélectionné, notamment :<br /><br /> : Un en-tête de groupe de substitution spécifié sur l’élément sélectionné.<br />: Un en-tête de groupe de substitution spécifié sur son élément head.|
|**Générer un exemple de XML**|Disponible uniquement pour les éléments globaux. Génère un exemple de fichier XML pour l'élément global.|

## <a name="node-type-global-types"></a>Type de nœud : types globaux
 En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds de type global comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Afficher le Type de Base**|Si le type sélectionné est dérivé d'un type global, navigue vers le type de base du type sélectionné.|
|**Afficher toutes les références**|Recherche et met en surbrillance toutes les références au type sélectionné. Ceci inclut les éléments et attributs du type sélectionné ainsi que les types dérivés du type sélectionné.|
|**Afficher tous les types dérivés**|Recherche et met en surbrillance tous les types qui sont directement et indirectement dérivés du type sélectionné.|
|**Afficher tous les ancêtres**|Affiche tous les types parents (de base).|

## <a name="node-type-attribute"></a>Type de nœud : attribut
 En plus des options relatives aux nœuds globaux décrites ci-dessus, le menu contextuel pour les nœuds d'attribut comprend les options suivantes :

|Option|Description|
|-|-----------------|
|**Atteindre la définition de Type**|Lorsque le type utilisé pour l'attribut est un type global, navigue vers la définition de type de l'attribut sélectionné.|
|**Accédez à l’attribut d’origine**|Pour les références d'attribut, navigue vers la définition réelle de l'attribut.|
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
- [Recherche dans le jeu de schéma](../xml-tools/searching-the-schema-set.md)