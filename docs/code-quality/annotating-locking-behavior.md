---
title: "Annotation du comportement de verrouillage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_Releases_nonreentrant_lock_"
  - "_Lock_kind_mutex_"
  - "_Lock_kind_critical_section_"
  - "_Acquires_lock_"
  - "_Releases_lock_"
  - "_Has_lock_kind_"
  - "_Releases_exclusive_lock_"
  - "_Post_same_lock_"
  - "_Requires_exclusive_lock_held_"
  - "_Requires_shared_lock_held_"
  - "_Lock_kind_semaphore_"
  - "_Requires_lock_held_"
  - "_Acquires_exclusive_lock_"
  - "_Create_lock_level_"
  - "_Acquires_nonreentrant_lock_"
  - "_Releases_shared_lock_"
  - "_Has_lock_level_"
  - "_Lock_kind_spin_lock_"
  - "_Requires_lock_not_held_"
  - "_Acquires_shared_lock_"
  - "_Requires_no_locks_held_"
  - "_Lock_level_order_"
  - "_Lock_kind_event_"
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Annotation du comportement de verrouillage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Pour éviter les bogues d'accès concurrentiel dans votre programme multithread, suivez toujours une règle appropriée de verrouillage et utilisez les annotations de SEL.  
  
 Il est notoirement difficile de reproduire, diagnostiquer, et déboguer des bogues d'accès concurrentiel en raison de leur nature non déterministe.  Comprendre les entrelacements de thread est au mieux difficile, et devient impossible lorsque vous concevez un corps de code qui a plus que quelques threads.  Par conséquent, il est recommandé de suivre une règle de verrouillage dans vos programmes multithread.  Par exemple, obéir à un ordre de verrou tout en obtenant plusieurs verrous permet d'éviter des interblocages et acquérir le verrou de garde approprié avant d'accéder à une ressource partagée permet d'éviter des conditions de concurrence critique.  
  
 Malheureusement, ces règles de verrouillage apparemment simples peuvent être étonnemment difficiles à suivre en pratique.  Une limitation fondamentale dans les langages de programmation et les compilateurs d'aujourd'hui est qu'ils ne prennent pas directement en charge la spécification et l'analyse des spécifications d'accès concurrentiel.  Les programmeurs doivent s'appuyer sur les commentaires de code informels pour exprimer les intentions sur la façon dont ils utilisent des verrous.  
  
 Les annotations SEL d'accès concurrentiel sont conçues pour vous aider à spécifier les effets secondaires de verrouillage, le responsable du verrouillage, la tutelle de données, la hiérarchie de commande de verrou, et d'autres comportements de verrouillage prévu.  En transformant des règles implicites en explicites, les annotations de concurrence SEL vous permettent de documenter la façon dont votre code utilise des règles de verrouillage.  Les annotations d'accès concurrentiel améliorent également la capacité des outils d'analyse du code pour rechercher des conditions de concurrence, des blocages, des opérations de synchronisation incompatibles, et d'autres erreurs subtiles de concurrence.  
  
## Indications générales  
 Les annotations permettent aux programmeurs de déclarer les contrats sous\-entendus par les définitions de fonction entre les implémentations \(appelés\) et les clients \(appelants\) et pour exprimer les invariants et d'autres propriétés du programme qui peuvent améliorer encore l'analyse.  
  
 SAL prend en charge de nombreux genres de primitives de verrouillage tels que les sections critiques, les mutex, les verrous de rotation, et d'autres objets de ressource.  De nombreuses annotations d'accès concurrentiel prennent une expression de verrou comme paramètre.  Par convention, un verrouillage est illustré par l'expression du chemin d'accès de l'objet verrou sous\-jacent.  
  
 Certaines règles concernant les threads à garder en tête :  
  
-   Les verrous de rotation sont des verrous non numérotés qui ont un propriétaire de thread clair.  
  
-   Les mutex et les sections critiques sont des verrous numérotés qui ont un propriétaire de thread clair.  
  
-   Les sémaphores et les événements sont des verrous numérotés qui n'ont pas de propriétaire de thread clair.  
  
## Annotations de verrouillage  
 Le tableau suivant répertorie les annotations de verrouillage.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Acquires_exclusive_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction incrémente le nombre de verrous exclusifs sur l'objet verrou nommé par `expr`.|  
|`_Acquires_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction incrémente le nombre de verrous sur l'objet verrou nommé par `expr`.|  
|`_Acquires_nonreentrant_lock_(expr)`|Le verrou qui est nommé par `expr` est acquis.  Une erreur est signalée si le verrou est déjà obtenu.|  
|`_Acquires_shared_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction incrémente le nombre de verrous partagés sur l'objet verrou nommé par `expr`.|  
|`_Create_lock_level_(name)`|Une instruction qui déclare le symbole `name` pour être un niveau de verrou afin qu'elle puisse être utilisée dans les annotations `_Has_Lock_level_`, et `_Lock_level_order_`.|  
|`_Has_lock_kind_(kind)`|Annote tout objet pour affiner les informations de type d'un objet de ressource.  Quelquefois un type commun est utilisé pour différents types de ressources et le type surchargé n'est pas suffisant pour distinguer les spécifications sémantiques entre différentes ressources.  Voici une liste des paramètres `kind` prédéfinis :<br /><br /> `_Lock_kind_mutex_`<br /> ID de type de verrou pour les mutex.<br /><br /> `_Lock_kind_event_`<br /> ID de type de verrou pour les événements.<br /><br /> `_Lock_kind_semaphore_`<br /> ID de type de verrou pour les sémaphores.<br /><br /> `_Lock_kind_spin_lock_`<br /> ID de type de verrou pour les verrous de rotation.<br /><br /> `_Lock_kind_critical_section_`<br /> ID de type de verrou pour les sections critiques.|  
|`_Has_lock_level_(name)`|Annote un objet verrou, en lui donnant le niveau de verrou de `name`.|  
|`_Lock_level_order_(name1, name2)`|Une instruction qui donne le classement des verrous entre `name1` et `name2`.|  
|`_Post_same_lock_(expr1, expr2)`|Annote une fonction et indique que dans l'état de publication les deux verrous, `expr1` et `expr2`, seront traités comme s'ils étaient le même objet verrou.|  
|`_Releases_exclusive_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction décrémente le nombre de verrous exclusifs sur l'objet verrou nommé par `expr`.|  
|`_Releases_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction décrémente le nombre de verrous sur l'objet verrou nommé par `expr`.|  
|`_Releases_nonreentrant_lock_(expr)`|Le verrou qui est nommée par `expr` est libéré.  Une erreur est signalée si le verrou n'est pas actuellement obtenu.|  
|`_Releases_shared_lock_(expr)`|Annote une fonction et indique que dans l'état de publication la fonction décrémente le nombre de verrous partagés sur l'objet verrou nommé par `expr`.|  
|`_Requires_lock_held_(expr)`|Annote une fonction et indique que dans le pré\-état le nombre de verrous de l'objet nommé par `expr` est au moins de un.|  
|`_Requires_lock_not_held_(expr)`|Annote une fonction et indique que dans l'état pre le nombre de verrous de l'objet nommé par `expr` est de zéro.|  
|`_Requires_no_locks_held_`|Annote une fonction et indique que le nombre de verrous de tous les verrous connus par le vérificateur est de zéro.|  
|`_Requires_shared_lock_held_(expr)`|Annote une fonction et indique que dans le pré\-état le nombre de verrous partagés de l'objet nommé par `expr` est au moins de un.|  
|`_Requires_exclusive_lock_held_(expr)`|Annote une fonction et indique que dans l'état pre le nombre de verrous exclusifs de l'objet nommé par `expr` est au moins de un.|  
  
## Intrinsèques SAL pour les objets de verrouillage non exposés  
 Certains objets verrous ne sont pas exposés par l'implémentation des fonctions associées de verrouillage.  Le tableau suivant répertorie les variables intrinsèques de SEL qui autorisent les annotations sur les fonctions qui gèrent ces objets lock pas exposés.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Global_cancel_spin_lock_`|Décrit le verrou d'annulation de rotation.|  
|`_Global_critical_region_`|Décrit la zone critique.|  
|`_Global_interlock_`|Décrit les opérations enclenchées.|  
|`_Global_priority_region_`|Décrit la zone de priorité.|  
  
## Annotations d'Accès aux Données Partagées  
 Le tableau suivant répertorie les annotations à utiliser avec l'accès aux données partagées.  
  
|Annotation|Description|  
|----------------|-----------------|  
|`_Guarded_by_(expr)`|Annote une variable et indique qu'chaque fois que la variable est atteinte le nombre de verrous de l'objet verrou nommé par `expr` est au moins de un.|  
|`_Interlocked_`|Annote une variable et son équivalent à `_Guarded_by_(_Global_interlock_)`.|  
|`_Interlocked_operand_`|Le paramètre de fonction annoté est l'opérande cible de l'une des différentes fonctions interverrouillées.  Ces opérandes doivent avoir des propriétés supplémentaires spécifiques.|  
|`_Write_guarded_by_(expr)`|Annote une variable et indique qu'chaque fois que la variable est modifiée, le nombre de verrous de l'objet verrou nommé par `expr` est au moins de un.|  
  
## Voir aussi  
 [Utilisation d’annotations SAL pour réduire les défauts du code C\/C\+\+](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Présentation de SAL](../code-quality/understanding-sal.md)   
 [Annotation de paramètres de fonction et valeurs de retour](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Annotation du comportement d’une fonction](../code-quality/annotating-function-behavior.md)   
 [Structs et classes d’annotation](../code-quality/annotating-structs-and-classes.md)   
 [Spécification du moment où une annotation est applicable et dans quel cas](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Fonctions intrinsèques](../code-quality/intrinsic-functions.md)   
 [Meilleures pratiques et exemples](../code-quality/best-practices-and-examples-sal.md)   
 [Blog de l'équipe d'analyse du code](http://go.microsoft.com/fwlink/p/?LinkId=251197)