---
title: Rechercher les appels à une méthode
description: Découvrez comment utiliser la fenêtre hiérarchie d’appels pour parcourir tous les appels à et, parfois, à partir d’une méthode, d’une propriété ou d’un constructeur sélectionné.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7384376b604f2097d68bf8bac06b2af0158e09b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836473"
---
# <a name="view-call-hierarchy"></a>Afficher la hiérarchie d'appels

En affichant la hiérarchie d’appels pour votre code, vous pouvez parcourir tous les appels à destination et parfois en provenance d’une méthode, d’une propriété ou d’un constructeur sélectionné. Cela vous permet de mieux comprendre le flux du code et d’évaluer les effets des modifications apportées au code. Vous pouvez examiner plusieurs niveaux de code pour afficher les chaînes complexes d’appels de méthodes et les points d’entrée supplémentaires dans le code, ce qui vous permet d’explorer tous les chemins d’exécution possibles.

Dans Visual Studio, vous pouvez afficher une hiérarchie d’appels au moment de la conception. Cela signifie que vous n’êtes pas obligé de définir un point d’arrêt et de démarrer le débogueur pour afficher la pile des appels à l’exécution.

## <a name="use-the-call-hierarchy-window"></a>Utiliser la fenêtre Hiérarchie d'appels

Pour afficher la fenêtre **Hiérarchie d’appels**, cliquez avec le bouton droit dans l’éditeur de code sur le nom d’un appel de méthode, de propriété ou de constructeur, puis sélectionnez **Afficher la hiérarchie d’appels**.

Le nom du membre s’affiche dans un volet d’arborescence dans la fenêtre **Hiérarchie d’appels**. Si vous développez le nœud correspondant au membre, les sous-nœuds **Appels à** *nom de membre* et, pour C++, **Appels de** *nom de membre* apparaissent.

Pour le code C++, vous pouvez afficher les appels émis et reçus par un membre :

![Hiérarchie d’appels pour le code C++ dans Visual Studio](media/call-hierarchy-cpp.png)

Pour le code C# et Visual Basic, vous pouvez afficher les appels envoyés à un membre, mais pas les appels provenant de :

![Hiérarchie d’appels pour le code C# dans Visual Studio](media/call-hierarchy-csharp.png)

- Si vous développez le nœud **Appels à**, tous les membres qui appellent le membre sélectionné sont affichés.

- Pour C++, si vous développez le nœud **Appels de**, tous les membres qui sont appelés par le membre sélectionné sont affichés.

Vous pouvez développer chaque membre appelant pour voir ses nœuds **Appels à** et, pour C++, ses nœuds **Appels de**. Cela vous permet de naviguer dans la pile des appelants, comme indiqué dans l’image suivante :

![Fenêtre Hiérarchie d’appels avec plusieurs niveaux développés](media/call-hierarchy-csharp-expanded.png)

Pour les membres définis en tant que membres virtuels ou abstraits, un nœud **Remplace nom de méthode** apparaît. Pour les membres d’interface, un nœud **Implémente nom de méthode** apparaît. Ces nœuds pouvant être développés apparaissent au même niveau que les nœuds **Appels à** et **Appels de**.

La zone **Étendue de recherche** de la barre d’outils contient des choix pour **Ma solution**, **Projet actif** et **Document actif**.

Quand vous sélectionnez un membre enfant dans le volet d’arborescence **Hiérarchie d’appels** :

- Le volet d’informations **Hiérarchie d’appels** affiche toutes les lignes de code dans lesquelles ce membre enfant est appelé à partir du membre parent.

- La fenêtre **définition de code** , si elle est ouverte, affiche le code du membre sélectionné (C++ uniquement). Pour plus d’informations sur cette fenêtre, consultez [Afficher la structure du code](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> La fonctionnalité **hiérarchie d’appels** ne trouve pas de références de groupe de méthodes, qui incluent des emplacements où une méthode est ajoutée en tant que gestionnaire d’événements ou qui est assignée à un délégué. Pour rechercher toutes les références à une méthode, vous pouvez utiliser la commande **Rechercher toutes les références**.

## <a name="shortcut-menu-items"></a>Éléments de menu contextuel

Le tableau suivant décrit plusieurs options de menu contextuel qui sont disponibles quand vous cliquez avec le bouton droit sur un nœud dans le volet d’arborescence.

|Élément de menu contextuel|Description|
| - |-----------------|
|**Ajouter en tant que nouvelle racine**|Ajoute le nœud sélectionné au volet d’arborescence en tant que nouveau nœud racine. Cela vous permet de concentrer votre attention sur une sous-arborescence spécifique.|
|**Supprimer racine**|Supprime le nœud racine sélectionné du volet d’arborescence. Cette option est disponible uniquement à partir d’un nœud racine.<br /><br /> Vous pouvez également utiliser le bouton de barre d’outils **Supprimer racine** pour supprimer le nœud racine sélectionné.|
|**Atteindre la définition**|Exécute la commande Atteindre la définition sur le nœud sélectionné. Cela permet de naviguer jusqu’à la définition d’origine pour un appel de membre ou une définition de variable.<br /><br /> Pour exécuter la commande Atteindre la définition, vous pouvez également double-cliquer sur le nœud sélectionné ou appuyer sur F12.|
|**Rechercher toutes les références**|Exécute la commande Rechercher toutes les références sur le nœud sélectionné. Cela permet de rechercher toutes les lignes de code de votre projet qui référencent une classe ou un membre.<br /><br /> Vous pouvez également utiliser Maj+F12 pour exécuter la commande Rechercher toutes les références sur le nœud sélectionné.|
|**Copy**|Copie le contenu du nœud sélectionné (mais pas ses sous-nœuds).|
|**Actualiser**|Réduit le nœud sélectionné afin qu’il puisse être redéveloppé pour afficher des informations actualisées.|
