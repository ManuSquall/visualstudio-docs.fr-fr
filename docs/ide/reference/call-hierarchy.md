---
title: Rechercher les appels à une méthode
ms.date: 05/18/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.CallHierarchy
helpviewer_keywords:
- Call Hierarchy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e1ca479a335cc46e199a107ec38d937dc5774d2f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915693"
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

- La fenêtre **Définition de code**, si elle est ouverte, affiche le code du membre sélectionné (C++ uniquement). Pour plus d’informations sur cette fenêtre, consultez [Afficher la structure du code](../../ide/viewing-the-structure-of-code.md).

> [!NOTE]
> La fonctionnalité **Hiérarchie d’appels** ne recherche pas les références au groupe de méthodes, ce qui inclut les emplacements auxquels une méthode est ajoutée en tant que gestionnaire d’événements ou est assignée à un délégué. Pour rechercher toutes les références à une méthode, vous pouvez utiliser la commande **Rechercher toutes les références**.

## <a name="shortcut-menu-items"></a>Éléments de menu contextuel

Le tableau suivant décrit plusieurs options de menu contextuel qui sont disponibles quand vous cliquez avec le bouton droit sur un nœud dans le volet d’arborescence.

|Élément de menu contextuel|Description|
| - |-----------------|
|**Ajouter comme nouvelle racine**|Ajoute le nœud sélectionné au volet d’arborescence en tant que nouveau nœud racine. Cela vous permet de concentrer votre attention sur une sous-arborescence spécifique.|
|**Supprimer racine**|Supprime le nœud racine sélectionné du volet d’arborescence. Cette option est disponible uniquement à partir d’un nœud racine.<br /><br /> Vous pouvez également utiliser le bouton de barre d’outils **Supprimer racine** pour supprimer le nœud racine sélectionné.|
|**Atteindre la définition**|Exécute la commande Atteindre la définition sur le nœud sélectionné. Cela permet de naviguer jusqu’à la définition d’origine pour un appel de membre ou une définition de variable.<br /><br /> Pour exécuter la commande Atteindre la définition, vous pouvez également double-cliquer sur le nœud sélectionné ou appuyer sur F12.|
|**Rechercher toutes les références**|Exécute la commande Rechercher toutes les références sur le nœud sélectionné. Cela permet de rechercher toutes les lignes de code de votre projet qui référencent une classe ou un membre.<br /><br /> Vous pouvez également utiliser Maj+F12 pour exécuter la commande Rechercher toutes les références sur le nœud sélectionné.|
|**Copier**|Copie le contenu du nœud sélectionné (mais pas ses sous-nœuds).|
|**Actualiser**|Réduit le nœud sélectionné afin qu’il puisse être redéveloppé pour afficher des informations actualisées.|