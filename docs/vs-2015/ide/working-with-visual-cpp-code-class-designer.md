---
title: Utilisation du code Visual C++ (Concepteur de classes) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 329125ffd1c577bb767fb3661331eeadeacada92
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508194"
---
# <a name="working-with-visual-c-code-class-designer"></a>Utilisation du code Visual C++ (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [utilisation de Code Visual C++ (Concepteur de classes)](https://docs.microsoft.com/visualstudio/ide/working-with-visual-cpp-code-class-designer).  
  
Le Concepteur de classes affiche une aire de conception visuelle appelée *diagramme de classes*, qui fournit une représentation visuelle des éléments de code dans votre projet. Vous pouvez utiliser des diagrammes de classes pour concevoir et visualiser des classes et d'autres types dans un projet.  
  
 Le Concepteur de classes prend en charge les éléments de code C++ suivants :  
  
-   Classe (ressemble à une forme de classe managée, mais peut avoir plusieurs relations d'héritage)  
  
-   Classe anonyme (affiche le nom généré de l'Affichage de classes pour le type anonyme)  
  
-   Classe de modèle  
  
-   Struct  
  
-   Enum  
  
-   Macro (montre l'affichage post-traité de la macro)  
  
-   TypeDef  
  
> [!NOTE]
>  Cela est différent du diagramme de classes UML, que vous pouvez créer dans un projet de modélisation. Pour plus d’informations, consultez [Diagrammes de classes UML : indications](../modeling/uml-class-diagrams-reference.md).  
  
## <a name="troubleshooting-type-resolution-and-display-issues"></a>Résolution des problèmes de résolution de type et d’affichage  
  
### <a name="location-of-source-files"></a>Emplacement de fichiers sources  
 Le Concepteur de classes n'effectue pas un suivi de l'emplacement des fichiers sources. Par conséquent, si vous modifiez votre structure de projet ou si vous déplacez des fichiers sources dans votre projet, le Concepteur de classes peut perdre la trace du type (surtout le type source d'un typedef, de classes de base ou de types d'associations). Vous pouvez recevoir une erreur telle que **Le Concepteur de classes n’est pas en mesure d’afficher ce type**. Dans ce cas, refaites glisser le code source modifié ou déplacé vers le diagramme de classes pour le réafficher.  
  
### <a name="update-and-performance-issues"></a>Problèmes de mise à jour et de performances  
 Pour les projets Visual C++, la modification dans le fichier source peut prendre 30 à 60 secondes avant d'apparaître dans le diagramme de classes. Ce délai peut entraîner la génération de l’erreur **Aucun type n’a été trouvé dans la sélection** par le Concepteur de classes. Si vous obtenez une telle erreur, cliquez sur **Annuler** dans le message d’erreur et attendez que l’élément de code apparaisse dans l’Affichage de classes. Le Concepteur de classes devrait ensuite être en mesure d'afficher le type.  
  
 En cas d'échec de la mise à jour d'un diagramme de classes suite à la modification du code, il peut s'avérer nécessaire de fermer le diagramme, puis de le rouvrir.  
  
### <a name="type-resolution-issues"></a>Problèmes de résolution de type  
 Le Concepteur de classes peut ne pas être en mesure de résoudre des types pour les raisons suivantes :  
  
-   Le type se trouve dans un projet ou un assembly non référencé à partir du projet qui contient le diagramme de classes. Pour corriger cette erreur, ajoutez une référence au projet ou à l'assembly qui contient le type. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
-   Le type ne se trouve pas dans la portée correcte ; le Concepteur de classes ne peut donc pas le localiser. Vérifiez qu'il ne manque pas une instruction `using`, `imports` ou `#include` au code. Assurez-vous également que vous n'avez pas déplacé le type (ou un type connexe) hors de l'espace de noms dans lequel il a été initialement localisé.  
  
-   Le type n'existe pas (ou a été commenté). Pour corriger cette erreur, assurez-vous que vous n'avez pas commenté ni supprimé le type.  
  
-   Le type se trouve dans une bibliothèque référencée par une directive #import. Une solution de contournement possible consiste à ajouter manuellement le code généré (le fichier .tlh) à une directive #include dans le fichier d'en-tête.  
  
 L’erreur que vous allez probablement voir en cas de problème de résolution de type est la suivante : **Code introuvable pour une ou plusieurs formes dans le diagramme de classes ’\<élément>’**. Ce message d'erreur n'indique pas nécessairement que votre code est erroné. Il indique seulement que le Concepteur de classes n'a pas pu afficher votre code. Essayez les actions suivantes.  
  
-   Assurez-vous que le type existe. Vérifiez que vous n'avez pas involontairement commenté ni supprimé le code source.  
  
-   Assurez-vous que le Concepteur de classes prend en charge le type que vous avez entré. Consultez [Limitations pour les éléments de code C++](#limitations).  
  
-   Essayez de résoudre le type. Le type se trouve peut-être dans un projet ou un assembly non référencé à partir du projet qui contient le diagramme de classes. Pour corriger cette erreur, ajoutez une référence au projet ou à l'assembly qui contient le type. Pour plus d’informations, consultez [NIB Comment : ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
-   Assurez-vous que le type se trouve dans la portée correcte afin que le Concepteur de classes puisse le localiser. Vérifiez qu'il ne manque pas une instruction `using`, `imports` ou `#include` au code. Assurez-vous également que vous n'avez pas déplacé le type (ou un type connexe) hors de l'espace de noms dans lequel il a été initialement localisé.  
  
### <a name="troubleshooting-other-error-messages"></a>Résolution d'autres messages d'erreur  
 Vous pouvez trouver de l'aide sur la résolution des erreurs et des avertissements dans les forums publics Microsoft Developer Network (MSDN). Consultez le [Forum du Concepteur de classes Visual Studio](http://go.microsoft.com/fwlink/?linkid=160754).  
  
##  <a name="limitations"></a> Limitations pour les éléments de code C++  
  
-   Quand un projet Visual C++ est chargé, le Concepteur de classes fonctionne en lecture seule. Vous pouvez modifier le diagramme de classes, mais vous ne pouvez pas réenregistrer les modifications du diagramme de classes dans le code source.  
  
-   Le Concepteur de classes prend en charge uniquement la sémantique C++ native. Pour les projets Visual C++ compilés dans le code managé, le Concepteur de classes visualise seulement les éléments de code qui sont des types natifs. Par conséquent, vous pouvez ajouter un diagramme de classes à un projet, mais le Concepteur de classes ne vous autorise pas à visualiser les éléments dans lesquels la propriété `IsManaged` a la valeur `true` (autrement dit, les types valeur et types référence).  
  
-   Pour les projets Visual C++, le Concepteur de classes lit uniquement la définition du type. Par exemple, supposons que vous définissez un type dans un fichier d'en-tête (.h) et que vous définissez ses membres dans un fichier d'implémentation (.cpp). Si vous appelez « Afficher le diagramme de classes » sur le fichier d'implémentation (.cpp), le Concepteur de classes n'affiche rien. Autre exemple, si vous appelez « Afficher le diagramme de classes » sur un fichier .cpp qui utilise une instruction `#include` pour inclure d'autres fichiers, mais qui ne contient pas de définitions de classe réelles, le Concepteur de classes n'affiche toujours rien.  
  
-   Les fichiers IDL (.idl) qui définissent des interfaces COM et des bibliothèques de types ne s'affichent pas dans les diagrammes, sauf s'ils sont compilés en code C++ natif.  
  
-   Le Concepteur de classes ne prend pas en charge les fonctions et variables globales.  
  
-   Le Concepteur de classes ne prend pas en charge les unions. Il s'agit d'un type spécial de classe dans laquelle la mémoire allouée est uniquement suffisante pour la plus grande donnée membre de l'union.  
  
-   Le Concepteur de classes n'affiche pas les types de données de base comme `int` et `char`.  
  
-   Le Concepteur de classes n'affiche pas les types qui sont définis en dehors du projet actuel si le projet n'a pas de références correctes à ces types.  
  
-   Le Concepteur de classes peut afficher les types imbriqués, mais pas les relations entre un type imbriqué et d'autres types.  
  
-   Le Concepteur de classes ne peut pas afficher les types void ou dérivés d'un type void.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception et affichage des classes et des types](../ide/designing-and-viewing-classes-and-types.md)   
 [Utilisation des classes et d’autres types (Concepteur de classes)](../ide/working-with-classes-and-other-types-class-designer.md)   
 [Utilisation des diagrammes de classes (Concepteur de classes)](../ide/working-with-class-diagrams-class-designer.md)   
 [Conception des classes et des types (Concepteur de classes)](../ide/designing-classes-and-types-class-designer.md)   
 [Informations supplémentaires sur les erreurs du Concepteur de classes](../ide/additional-information-about-class-designer-errors.md)   
 [Classes de Visual C++ dans le concepteur de classes](../ide/visual-cpp-classes-in-class-designer.md)   
 [Structures de Visual C++ dans le Concepteur de classes](../ide/visual-cpp-structures-in-class-designer.md)   
 [Énumérations de Visual C++ dans le concepteur de classes](../ide/visual-cpp-enumerations-in-class-designer.md)   
 [Typedefs de Visual C++ dans le Concepteur de classes](../ide/visual-cpp-typedefs-in-class-designer.md)



