---
title: Utilisation du code Visual C++ (Concepteur de classes)
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.cpplimitation
helpviewer_keywords:
- Visual C++, Class Designer
- Class Designer, Visual C++ support
- Class Designer, limitations
- Class Designer, tasks in Visual C++
- Visual C++, class diagrams
- C++, class diagrams
- C++, Class Designer
ms.assetid: f5b40921-2ef7-4de0-b595-45b44c79ffa6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 1497730cf7c2b2e9abc17ec6cb82179deebb30d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948048"
---
# <a name="work-with-visual-c-code-in-class-designer"></a>Utiliser le code Visual C++ dans le Concepteur de classes

Le **Concepteur de classes** affiche une aire de conception visuelle appelée *diagramme de classes*, qui fournit une représentation visuelle des éléments de code dans votre projet. Vous pouvez utiliser des diagrammes de classes pour concevoir et visualiser des classes et d'autres types dans un projet.

Le **Concepteur de classes** prend en charge les éléments de code C++ suivants :

- Classe (ressemble à une forme de classe managée, mais peut avoir plusieurs relations d'héritage)

- Classe anonyme (affiche le nom généré de l'Affichage de classes pour le type anonyme)

- Classe de modèle

- Struct

- Enum

- Macro (montre l'affichage post-traité de la macro)

- TypeDef

> [!NOTE]
> Cela est différent du diagramme de classes UML, que vous pouvez créer dans un projet de modélisation. Pour plus d'informations, consultez [Diagrammes de classes UML : Référence](../../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="troubleshoot-type-resolution-and-display-issues"></a>Résoudre les problèmes de résolution de type et d’affichage

### <a name="location-of-source-files"></a>Emplacement des fichiers sources

Le **Concepteur de classes** n’effectue pas un suivi de l’emplacement des fichiers sources. Si vous modifiez votre structure de projet ou que vous déplacez des fichiers sources dans votre projet, le **Concepteur de classes** peut donc perdre la trace du type (surtout le type source d’un typedef, de classes de base ou de types d’associations). Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.

### <a name="update-and-performance-issues"></a>Problèmes de mise à jour et de performances

Pour les projets Visual C++, la modification dans le fichier source peut prendre 30 à 60 secondes avant d'apparaître dans le diagramme de classes. Ce délai peut également forcer le **Concepteur de classes** à générer l’erreur **Aucun type n’a été trouvé dans la sélection**. Si vous obtenez une telle erreur, cliquez sur **Annuler** dans le message d’erreur et attendez que l’élément de code apparaisse dans **l’Affichage de classes**. Le **Concepteur de classes** doit ensuite pouvoir afficher le type.

En cas d'échec de la mise à jour d'un diagramme de classes suite à la modification du code, il peut s'avérer nécessaire de fermer le diagramme, puis de le rouvrir.

### <a name="type-resolution-issues"></a>Problèmes de résolution de type

Le **Concepteur de classes** peut ne pas être en mesure de résoudre des types pour les raisons suivantes :

- Le type se trouve dans un projet ou un assembly non référencé à partir du projet qui contient le diagramme de classes. Pour corriger cette erreur, ajoutez une référence au projet ou à l'assembly qui contient le type. Pour plus d’informations, consultez [Gestion des références dans un projet](../managing-references-in-a-project.md).

- Le type ne se trouvant pas dans la portée correcte, le **Concepteur de classes** ne peut pas le localiser. Vérifiez qu'il ne manque pas une instruction `using`, `imports` ou `#include` au code. Assurez-vous également que vous n'avez pas déplacé le type (ou un type connexe) hors de l'espace de noms dans lequel il a été initialement localisé.

- Le type n'existe pas (ou a été commenté). Pour corriger cette erreur, assurez-vous que vous n'avez pas commenté ni supprimé le type.

- Le type se trouve dans une bibliothèque référencée par une directive #import. Une solution de contournement possible consiste à ajouter manuellement le code généré (le fichier .tlh) à une directive #include dans le fichier d'en-tête.

- Vérifiez que le **Concepteur de classes** prend en charge le type que vous avez entré. Consultez [Limitations pour les éléments de code C++](#limitations-for-c-code-elements).

L’erreur que vous allez probablement voir en cas de problème de résolution de type est la suivante : **Code introuvable pour une ou plusieurs formes dans le diagramme de classes ’\<élément>’**. Ce message d'erreur n'indique pas nécessairement que votre code est erroné. Il indique seulement que le Concepteur de classes n'a pas pu afficher votre code. Essayez les actions suivantes :

- Assurez-vous que le type existe. Vérifiez que vous n'avez pas involontairement commenté ni supprimé le code source.

- Essayez de résoudre le type. Le type se trouve peut-être dans un projet ou un assembly non référencé à partir du projet qui contient le diagramme de classes. Pour corriger cette erreur, ajoutez une référence au projet ou à l'assembly qui contient le type. Pour plus d’informations, consultez [Gestion des références dans un projet](../managing-references-in-a-project.md).

- Assurez-vous que le type se trouve dans la portée correcte afin que le Concepteur de classes puisse le localiser. Vérifiez qu'il ne manque pas une instruction `using`, `imports` ou `#include` au code. Assurez-vous également que vous n'avez pas déplacé le type (ou un type connexe) hors de l'espace de noms dans lequel il a été initialement localisé.

### <a name="troubleshoot-other-error-messages"></a>Résoudre d’autres messages d’erreur

Vous pouvez trouver de l'aide sur la résolution des erreurs et des avertissements dans les forums publics Microsoft Developer Network (MSDN). Consultez le [Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).

## <a name="limitations-for-c-code-elements"></a>Limitations pour les éléments de code C++

- Quand un projet Visual C++ est chargé, le **Concepteur de classes** fonctionne en lecture seule. Vous pouvez modifier le diagramme de classes, mais vous ne pouvez pas réenregistrer les modifications du diagramme de classes dans le code source.

- Le **Concepteur de classes** prend en charge uniquement la sémantique C++ native. Pour les projets Visual C++ compilés dans le code managé, le **Concepteur de classes** visualise uniquement les éléments de code qui sont des types natifs. Vous pouvez donc ajouter un diagramme de classes à un projet, mais le **Concepteur de classes** ne vous autorise pas à visualiser les éléments dans lesquels la propriété `IsManaged` a la valeur `true` (autrement dit, les types valeur et types référence).

- Pour les projets Visual C++, le **Concepteur de classes** lit uniquement la définition du type. Par exemple, supposons que vous définissez un type dans un fichier d'en-tête (.h) et que vous définissez ses membres dans un fichier d'implémentation (.cpp). Si vous appelez « Afficher le diagramme de classes » sur le fichier d’implémentation (.cpp), le **Concepteur de classes** n’affiche rien. Autre exemple, si vous appelez « Afficher le diagramme de classes » sur un fichier .cpp qui utilise une instruction `#include` pour inclure d’autres fichiers, mais qui ne contient pas de définitions de classe réelles, le **Concepteur de classes** n’affiche toujours rien.

- Les fichiers IDL (.idl) qui définissent des interfaces COM et des bibliothèques de types ne s'affichent pas dans les diagrammes, sauf s'ils sont compilés en code C++ natif.

- Le **Concepteur de classes** ne prend pas en charge les fonctions et variables globales.

- Le **Concepteur de classes** ne prend pas en charge les unions. Il s'agit d'un type spécial de classe dans laquelle la mémoire allouée est uniquement suffisante pour la plus grande donnée membre de l'union.

- Le **Concepteur de classes** n’affiche pas les types de données de base comme `int` et `char`.

- Le **Concepteur de classes** n’affiche pas les types qui sont définis en dehors du projet actuel si le projet n’a pas de références correctes à ces types.

- Le **Concepteur de classes** peut afficher les types imbriqués, mais pas les relations entre un type imbriqué et d’autres types.

- Le **Concepteur de classes** ne peut pas afficher les types void ou dérivés d’un type void.

## <a name="see-also"></a>Voir aussi

- [Conception et affichage des classes et des types](designing-and-viewing-classes-and-types.md)
- [Informations supplémentaires sur les erreurs du Concepteur de classes](additional-information-about-errors.md)
- [Classes de Visual C++ dans le concepteur de classes](visual-cpp-classes.md)
- [Structures de Visual C++ dans le Concepteur de classes](visual-cpp-structures.md)
- [Énumérations de Visual C++ dans le concepteur de classes](visual-cpp-enumerations.md)
- [Typedefs de Visual C++ dans le Concepteur de classes](visual-cpp-typedefs.md)
