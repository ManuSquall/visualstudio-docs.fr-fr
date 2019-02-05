---
title: Annotation du comportement de verrouillage
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 4ee8e68cea1a4f6b708b304b6ca889d29eff0bad
ms.sourcegitcommit: 0f7411c1a47d996907a028e920b73b53c2098c9f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55690309"
---
# <a name="annotating-locking-behavior"></a>Annotation du comportement de verrouillage
Pour éviter les bogues d’accès concurrentiel dans votre programme multithread, suivez toujours une discipline de verrouillage appropriée et utilisez les annotations SAL.

 Il est notoirement difficile de reproduire, de diagnostiquer et de déboguer des bogues d'accès concurrentiel en raison de leur nature non déterministe. Comprendre les entrelacements de thread est au mieux difficile, et devient impossible lorsque vous concevez un corps de code qui compte plus que quelques threads. Par conséquent, il est recommandé de suivre une règle de verrouillage dans vos programmes multithread. Par exemple, obéir à un ordre de verrou tout en obtenant plusieurs verrous permet d'éviter des interblocages, et acquérir le verrou de garde approprié avant d'accéder à une ressource partagée permet d'éviter des conditions de concurrence.

 Malheureusement, ces règles de verrouillage apparemment simples peuvent être étonnamment difficiles à suivre en pratique. Une restriction fondamentale dans les compilateurs et les langages de programmation d’aujourd'hui est qu’ils ne gèrent pas directement la spécification et l’analyse des exigences d’accès concurrentiel. Les programmeurs doivent s'appuyer sur les commentaires de code informels pour exprimer leurs intentions sur la façon dont ils utilisent des verrous.

 Les annotations SAL d'accès concurrentiel sont conçues pour vous aider à spécifier les effets secondaires du verrouillage, le responsable du verrouillage, la tutelle de données, la hiérarchie d'ordre de verrou et d'autres comportements de verrouillage prévus. En transformant des règles implicites en règles explicites, les annotations d'accès concurrence SAL vous permettent de documenter la façon dont votre code utilise des règles de verrouillage. Les annotations d’accès concurrentiel améliorent également la capacité des outils d’analyse du code à rechercher des conditions de concurrence, des interblocages, des opérations de synchronisation incompatibles et d’autres erreurs subtiles d’accès concurrentiel.

## <a name="general-guidelines"></a>Indications générales
 Les annotations permettent aux programmeurs de déclarer les contrats sous-entendus par les définitions de fonction entre les implémentations (appelés) et les clients (appelants) et d'exprimer les invariants et d'autres propriétés du programme qui peuvent améliorer davantage l'analyse.

 SAL prend en charge de nombreux types de primitives de verrouillage, tels que les sections critiques, les mutex, les verrous de rotation et d'autres objets de ressource. Plusieurs annotations d’accès concurrentiel prennent une expression de verrouillage en tant que paramètre. Par convention, un verrou est indiqué par l’expression de chemin d’accès de l’objet de verrouillage sous-jacent.

 Quelques règles de propriété concernant les threads à garder en tête :

-   Les verrous de rotation sont des verrous non numérotés qui ont une propriété de thread précise.

-   Les mutex et les sections critiques sont des verrous numérotés qui ont une propriété de thread précise.

-   Les sémaphores et les événements sont des verrous numérotés qui n'ont pas de propriété de thread précise.

## <a name="locking-annotations"></a>Annotations de verrouillage
 Le tableau suivant répertorie les annotations de verrouillage.

|Annotation|Description|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction incrémente d’une unité le nombre de verrous exclusifs de l’objet verrou nommé par `expr`.|
|`_Acquires_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction incrémente d’une unité le nombre de verrous de l’objet verrou nommé par `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Le verrou nommé par `expr` est acquis.  Une erreur est signalée si le verrou est déjà détenu.|
|`_Acquires_shared_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction incrémente d’une unité le nombre de verrous partagés de l’objet verrou nommé par `expr`.|
|`_Create_lock_level_(name)`|Instruction qui déclare le symbole `name` comme un niveau de verrou afin qu'il puisse être utilisé dans les annotations `_Has_Lock_level_` et `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Annote n’importe quel objet pour affiner les informations de type d’un objet de ressource. Parfois, un type commun est utilisé pour différents types de ressources et le type surchargé n’est pas suffisant pour distinguer les exigences sémantiques entre les différentes ressources. Voici la liste des paramètres `kind` prédéfinis :<br /><br /> `_Lock_kind_mutex_`<br /> ID de type de verrouillage pour les mutex.<br /><br /> `_Lock_kind_event_`<br /> ID de type de verrouillage pour les événements.<br /><br /> `_Lock_kind_semaphore_`<br /> ID de type de verrouillage pour les sémaphores.<br /><br /> `_Lock_kind_spin_lock_`<br /> ID de type de verrouillage pour les verrous de rotation.<br /><br /> `_Lock_kind_critical_section_`<br /> ID de type de verrouillage pour les sections critiques.|
|`_Has_lock_level_(name)`|Annote un objet verrou, en lui donnant le niveau de verrou de `name`.|
|`_Lock_level_order_(name1, name2)`|Une instruction qui donne le verrou de classement entre `name1` et `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Annote une fonction et indique qu’à l’état postérieur les deux verrous, `expr1` et `expr2`, sont traités comme s’ils étaient le même objet verrou.|
|`_Releases_exclusive_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction décrémente d’une unité le nombre de verrous exclusifs de l’objet verrou nommé par `expr`.|
|`_Releases_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction décrémente d’une unité le nombre de verrous de l’objet verrou nommé par `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Le verrou nommé par `expr` est libéré. Une erreur est signalée si le verrou n'est pas actuellement détenu.|
|`_Releases_shared_lock_(expr)`|Annote une fonction et indique qu’à l’état postérieur la fonction décrémente d’une unité le nombre de verrous partagés de l’objet verrou nommé par `expr`.|
|`_Requires_lock_held_(expr)`|Annote une fonction et indique qu’à l’état antérieur le nombre de verrous de l’objet nommé par `expr` est d’au moins un.|
|`_Requires_lock_not_held_(expr)`|Annote une fonction et indique qu’à l’état antérieur le nombre de verrous de l’objet nommé par `expr` est zéro.|
|`_Requires_no_locks_held_`|Annote une fonction et indique que le nombre de verrous de tous les verrous connus par le vérificateur est égal à zéro.|
|`_Requires_shared_lock_held_(expr)`|Annote une fonction et indique qu’à l’état antérieur le nombre de verrous partagés de l’objet nommé par `expr` est d’au moins un.|
|`_Requires_exclusive_lock_held_(expr)`|Annote une fonction et indique qu’à l’état antérieur le nombre de verrous exclusifs de l’objet nommé par `expr` est d’au moins un.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Intrinsèques SAL pour les objets de verrouillage non exposés
 Certains objets de verrou ne sont pas exposés par l’implémentation des fonctions de verrouillage associées.  Le tableau suivant répertorie les variables intrinsèques SAL qui autorisent les annotations sur les fonctions qui s'exécutent sur ces objets verrous non exposés.

|Annotation|Description|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Décrit le verrou d'annulation de rotation.|
|`_Global_critical_region_`|Décrit la zone critique.|
|`_Global_interlock_`|Décrit les opérations verrouillées.|
|`_Global_priority_region_`|Décrit la zone de priorité.|

## <a name="shared-data-access-annotations"></a>Annotations d’accès de données partagée
 Le tableau suivant répertorie les annotations à utiliser avec l'accès aux données partagées.

|Annotation|Description|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Annote une variable et indique qu’à chaque accès à la variable, le nombre de verrous de l’objet verrou nommé par `expr` est d’au moins un.|
|`_Interlocked_`|Annote une variable et équivaut à `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Le paramètre de fonction annoté est l’opérande de cible d’une des diverses fonctions Interlocked.  Les opérandes doivent avoir des propriétés supplémentaires spécifiques.|
|`_Write_guarded_by_(expr)`|Annote une variable et indique qu’à chaque modification de la variable, le nombre de verrous de l’objet verrou nommé par `expr` est d’au moins un.|


## <a name="smart-lock-and-raii-annotations"></a>Smart Lock et Annotations de RAII
 En général, verrous intelligents encapsulent les verrous natifs et gérer leur durée de vie. Le tableau suivant répertorie les annotations qui peuvent être utilisées avec les verrous intelligents et RAII modèles prenant en charge de codage `move` sémantique.

|Annotation|Description|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Indique à l’Analyseur de supposer qu’un verrou intelligent a été acquis. Cette annotation attend un type de verrou de référence comme son paramètre.|
|`_Analysis_assume_smart_lock_released_`|Indique à l’Analyseur de supposer qu’un verrou intelligent a été débloqué. Cette annotation attend un type de verrou de référence comme son paramètre.|
|`_Moves_lock_(target, source)`|Décrit `move constructor` opération qui transfère l’état du verrouillage à partir de la `source` de l’objet à le `target`. Le `target` est considéré comme un objet nouvellement construit, donc tout état qu’elle avait avant est perdu et remplacé par le `source` état. Le `source` est également rétablir un état propre avec aucune cible de nombres ou des alias de verrou, mais les alias qui pointe vers elle restent inchangés.|
|`_Replaces_lock_(target, source)`|Décrit `move assignment operator` sémantique où cible soient déverrouillées avant de transférer l’état de la source. Cela peut être considéré comme une combinaison de `_Moves_lock_(target, source)` précédé par un `_Releases_lock_(target)`.|
|`_Swaps_locks_(left, right)`|Décrit la norme `swap` comportement part du principe que les objets `left` et `right` exchange leur état. L’état échangé inclut la cible du nombre et les alias de verrou, le cas échéant. Les alias qui pointent vers le `left` et `right` objets restent inchangées.|
|`_Detaches_lock_(detached, lock)`|Décrit un scénario dans lequel un type de wrapper de verrou permet de dissociation avec sa ressource de relation contenant-contenu. Cela est similaire à la manière dont `std::unique_ptr` fonctionne avec son pointeur interne : il permet aux programmeurs d’extraire le pointeur et de laisser de son conteneur de pointeur intelligent dans un état propre. Une logique similaire est pris en charge par `std::unique_lock` et peut être implémentée dans les wrappers de verrouillage personnalisé. Le verrou détaché conserve son état (verrou count et alias cible, le cas échéant), tandis que le wrapper est réinitialisé pour contenir zéro nombre de verrous et qu’aucune cible de l’alias, tout en conservant ses propres alias. Il n’existe aucune opération sur le nombre de verrous (libérer et acquérir). Cette annotation se comporte exactement comme `_Moves_lock_` , à ceci près que l’argument détachée doit être `return` plutôt que `this`.|

## <a name="see-also"></a>Voir aussi

- [Utilisation d’annotations SAL pour réduire les défauts du code C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Présentation de SAL](../code-quality/understanding-sal.md)
- [Annotation des paramètres de fonction et des valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)
- [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)
- [Annotations des structs et des classes](../code-quality/annotating-structs-and-classes.md)
- [Spécification du moment et de l’endroit où une annotation s’applique](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)
- [Bonnes pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)
- [Blog de l’équipe analyse du code](http://go.microsoft.com/fwlink/p/?LinkId=251197)