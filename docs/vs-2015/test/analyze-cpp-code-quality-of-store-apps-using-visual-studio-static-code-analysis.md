---
title: Applications du magasin d’analyse du code statique C++
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.native.express
ms.assetid: c5355e43-a37c-4686-a969-18e3dfc59a9c
caps.latest.revision: 15
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c20fe8bccdf48cf307dda72a085b3c2a72f1d0cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672707"
---
# <a name="analyze-c-code-quality-of-store-apps-using-visual-studio-static-code-analysis"></a>Analyser la qualité du code C++ des applications du Windows Store à l'aide de l'analyse statique du code Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

S’applique à Windows et Windows Phone] (.. /Image/windows_and_phone_content.png « windows_and_phone_content »)

 L'outil d'analyse du code dans les éditions Visual Studio Express examine votre code à la recherche d'un ensemble d'erreurs courantes et du non-respect d'une bonne approche en matière de programmation. Les avertissements de l'analyse du code diffèrent des erreurs et des avertissements du compilateur, car l'analyse du code recherche des modèles de code spécifiques qui sont valides, mais qui peuvent créer des problèmes pour vous ou d'autres utilisateurs de votre code. L'analyse du code peut également trouver des erreurs dans votre code qui seraient difficiles à détecter en testant. L'exécution de l'outil d'analyse du code à intervalles réguliers pendant le processus de développement peut améliorer la qualité de votre application terminée.

> [!NOTE]
> Dans Visual Studio Ultimate, Visual Studio Premium et Visual Studio Professional, vous pouvez utiliser les fonctionnalités complètes des outils d'analyse du code. Consultez [Analyse de la qualité des applications à l’aide des outils d’analyse du code](https://msdn.microsoft.com/library/dd264897.aspx) dans MSDN Library.

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Exécution de l’analyse du code
 Pour exécuter l'analyse du code sur votre solution Visual Studio :

- Dans le menu **Générer**, choisissez **Exécuter l’analyse du code sur la solution**.

  Pour exécuter automatiquement l'analyse du code chaque fois que vous générez un projet :

1. Dans l’Explorateur de solutions, choisissez le nom du projet, puis choisissez **Propriétés**.

2. Dans la page des propriétés du projet, choisissez **Analyse du code**, puis **Activer l’analyse du code pour la génération C/C++ sur la build**.

   La solution est compilée et l'analyse du code s'exécute. Les résultats s'affichent dans la fenêtre Analyse du code.

   ![Fenêtre d'analyse du code](../test/media/ca-cpp-collapsed.png "CA_CPP_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Analyse et résolution des avertissements de l’analyse du code
 Pour analyser un avertissement spécifique, choisissez le titre de l'avertissement dans la fenêtre Analyse du code. L'avertissement se développe pour afficher des informations détaillées sur le problème. Quand cela est possible, l'analyse du code affiche le numéro de la ligne et la logique de l'analyse qui a conduit à l'avertissement.

 ![Avertissements liés à l'analyse du code développé](../test/media/ca-cpp-expanded-callout.png "CA_CPP_Expanded_Callout")

 Quand vous développez un avertissement, les lignes de code à l’origine de l’avertissement sont mises en surbrillance dans l’éditeur de Visual Studio Code.

 ![Code source en surbrillance](../test/media/ca-cpp-sourceline.png "CA_CPP_SourceLine")

 Après avoir identifié le problème, vous pouvez le résoudre dans votre code. Relancez ensuite l'analyse du code pour vérifier que l'avertissement ne s'affiche plus dans la fenêtre Analyse du code, et que le correctif n'a pas levé de nouveaux avertissements.

> [!TIP]
> Vous pouvez réexécuter l'analyse du code dans la fenêtre Analyse du code. Choisissez le bouton **Analyser**, puis choisissez la portée de l’analyse. Vous pouvez réexécuter l'analyse sur la solution complète ou sur un projet sélectionné.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Suppression des avertissements d’analyse du code
 Vous pouvez décider, dans certaines situations, de ne pas corriger un avertissement de l'analyse du code. Vous pouvez décider que la résolution de l'avertissement requiert un recodage trop important par rapport à la probabilité que le problème se produise dans une implémentation réelle de votre code. Vous pouvez également estimer que l'analyse utilisée dans l'avertissement est inadéquate pour le contexte particulier. Vous pouvez supprimer des avertissements individuels afin qu'ils n'apparaissent plus dans la fenêtre Analyse du code.

 Pour supprimer un avertissement :

1. Si les informations détaillées ne s’affichent pas, développez le titre de l’avertissement.

2. Choisissez le lien **Actions** au bas de l’avertissement.

3. Choisissez de **Supprimer le message**, puis choisissez **Dans la source**.

   La suppression d’un message insère `#pragma(warning:` *warningld,* `)` qui supprime l’avertissement pour la ligne de code.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Recherche et filtrage des résultats de l’analyse du code
 Vous pouvez effectuer une recherche dans de longues listes de messages d'avertissement, et vous pouvez filtrer les avertissements dans les solutions à projets multiples.

 ![Rechercher et filtrer la fenêtre d'analyse du code](../test/media/ca-searchfilter.png "CA_SearchFilter")

## <a name="c-code-analysis-warnings"></a><a name="Warnings"></a> Avertissements d’analyse du code C++
 L'analyse du code génère les avertissements suivants pour le code C++ :

|                                      Règle                                      |                                                  Description                                                  |
|--------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
|                       [C6001](../code-quality/c6001.md)                        |                                          Utilisation d'une mémoire non initialisée                                           |
|                       [C6011](../code-quality/c6011.md)                        |                                          Déréférencement du pointeur Null                                           |
|                       [C6029](../code-quality/c6029.md)                        |                                            Utilisation d'une valeur non vérifiée                                             |
|                       [C6053](../code-quality/c6053.md)                        |                                          Terminaison par zéro de l'appel                                           |
|                       [C6059](../code-quality/c6059.md)                        |                                               Concaténation non valide                                               |
|                       [C6063](../code-quality/c6063.md)                        |                                  Argument de chaîne manquant pour le formatage de la fonction                                   |
|                       [C6064](../code-quality/c6064.md)                        |                                  Argument d’entier manquant pour le formatage de la fonction                                  |
|                       [C6066](../code-quality/c6066.md)                        |                                  Argument de pointeur manquant pour le formatage de la fonction                                  |
|                       [C6067](../code-quality/c6067.md)                        |                              Argument de pointeur de chaîne manquant pour le formatage de la fonction                               |
|                       [C6101](../code-quality/c6101.md)                        |                                        Retour d'une mémoire non initialisée                                         |
|                       [C6200](../code-quality/c6200.md)                        |                                         L'index dépasse la taille maximale autorisée par la mémoire tampon                                          |
|                       [C6201](../code-quality/c6201.md)                        |                                      L'index dépasse la taille maximale autorisée par la mémoire tampon allouée par la pile                                       |
|                       [C6270](../code-quality/c6270.md)                        |                                   Argument float manquant pour le formatage de la fonction                                   |
|                       [C6271](../code-quality/c6271.md)                        |                                       Argument supplémentaire pour le formatage de la fonction                                       |
|                       [C6272](../code-quality/c6272.md)                        |                                     Argument non float pour le formatage de la fonction                                     |
|                       [C6273](../code-quality/c6273.md)                        |                                    Argument non entier pour la fonction Format                                     |
|                       [C6274](../code-quality/c6274.md)                        |                                   Argument autre qu’un caractère pour le formatage de la fonction                                   |
|                       [C6276](../code-quality/c6276.md)                        |                                              Cast de chaîne non valide                                              |
|                       [C6277](../code-quality/c6277.md)                        |                                          Appel CreateProcess non valide                                           |
|                       [C6284](../code-quality/c6284.md)                        |                                  Argument d’objet non valide pour le formatage de la fonction                                   |
|                       [C6290](../code-quality/c6290.md)                        |                                      Priorité NOT logique et AND au niveau du bit                                       |
|                       [C6291](../code-quality/c6291.md)                        |                                       Priorité NOT logique et OR au niveau du bit                                       |
|                       [C6302](../code-quality/c6302.md)                        |                             Argument de chaîne de caractères non valide pour le formatage de la fonction                              |
|                       [C6303](../code-quality/c6303.md)                        |                           Argument de chaîne de caractères larges non valide pour le formatage de la fonction                           |
|                       [C6305](../code-quality/c6305.md)                        |                                         Incompatibilité entre la taille et la quantité                                         |
|                       [C6306](../code-quality/c6306.md)                        |                                   Appel de fonction d’argument de variable non valide                                   |
|                       [C6328](../code-quality/c6328.md)                        |                                       Incompatibilité de type d’argument possible                                        |
|                       [C6385](../code-quality/c6385.md)                        |                                                 Dépassement en lecture                                                  |
|                       [C6386](../code-quality/c6386.md)                        |                                                 Dépassement en écriture                                                 |
|                       [C6387](../code-quality/c6387.md)                        |                                            Valeur de paramètre non valide                                            |
|                       [C6500](../code-quality/c6500.md)                        |                                          Propriété d'attribut non valide                                           |
|                       [C6501](../code-quality/c6501.md)                        |                                     Valeurs de propriété d'attribut en conflit                                     |
|                       [C6503](../code-quality/c6503.md)                        |                                           Les références ne peuvent pas être Null                                           |
|                       [C6504](../code-quality/c6504.md)                        |                                              Null sur élément non pointeur                                              |
|                       [C6505](../code-quality/c6505.md)                        |                                               MustCheck sur Void                                               |
|                       [C6506](../code-quality/c6506.md)                        |                                      Taille de mémoire tampon sur élément non pointeur ou tableau                                      |
| [C6507](https://msdn.microsoft.com/18f88cd1-d035-4403-a6a4-12dd0affcf21)        |                                       Incompatibilité de null au déréférencement nul                                       |
|                       [C6508](../code-quality/c6508.md)                        |                                           Accès en écriture sur constante                                            |
|                       [C6509](../code-quality/c6509.md)                        |                                          Retour utilisé sur condition préalable                                          |
|                       [C6510](../code-quality/c6510.md)                        |                                        Terminaison par Null sur élément non pointeur                                         |
|                       [C6511](../code-quality/c6511.md)                        |                                          MustCheck doit avoir la valeur Yes ou No                                          |
|                       [C6513](../code-quality/c6513.md)                        |                                       Taille d'élément sans taille de mémoire tampon                                        |
|                       [C6514](../code-quality/c6514.md)                        |                                        Taille de mémoire tampon dépasse la taille du tableau                                         |
|                       [C6515](../code-quality/c6515.md)                        |                                          Taille de la mémoire tampon sur élément non pointeur                                           |
|                       [C6516](../code-quality/c6516.md)                        |                                          Attribut sans propriété                                           |
|                       [C6517](../code-quality/c6517.md)                        |                                       Taille valide dans mémoire tampon non lisible                                       |
|                       [C6518](../code-quality/c6518.md)                        |                                     Taille accessible en écriture dans mémoire tampon non accessible en écriture                                      |
| [C6521](https://msdn.microsoft.com/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)  |                                        Déréférencement de chaîne de taille non valide                                        |
|                       [C6522](../code-quality/c6522.md)                        |                                           Type de chaîne de taille non valide                                            |
| [C6523](https://msdn.microsoft.com/11397a31-b224-46b0-afb7-d49ca576a3bb)  |                                         Paramètre de chaîne de taille non valide                                         |
|                       [C6525](../code-quality/c6525.md)                        |                                   Chaîne de taille non valide. Emplacement inaccessible                                    |
| [C6526](https://msdn.microsoft.com/59c590c7-0098-4166-a1ac-87f324596002)  |                                        Type de tampon de chaîne de taille non valide                                        |
|                       [C6527](../code-quality/c6527.md)                        |              Annotation non valide : la propriété NeedsRelease ne doit pas être utilisée sur des valeurs de type void               |
|                       [C6530](../code-quality/c6530.md)                        |                                       Style de chaîne de format non reconnu                                        |
|                       [C6540](../code-quality/c6540.md)                        | L'utilisation des annotations d'attribut sur cette fonction rendra non valides toutes ses annotations __declspec existantes  |
|                       [C6551](../code-quality/c6551.md)                        |                              Spécification de taille non valide : expression impossible à analyser                              |
|                       [C6552](../code-quality/c6552.md)                        |                              Deref= ou Noref= non valide : expression impossible à analyser                               |
|                       [C6701](../code-quality/c6701.md)                        |                                  La valeur n'est pas une valeur Yes/No/Maybe valide                                  |
|                       [C6702](../code-quality/c6702.md)                        |                                        La valeur n'est pas une valeur de chaîne                                        |
|                       [C6703](../code-quality/c6703.md)                        |                                           La valeur n'est pas un nombre                                           |
|                       [C6704](../code-quality/c6704.md)                        |                                    Erreur d'expression de l'annotation inattendue                                     |
|                       [C6705](../code-quality/c6705.md)                        |     Le nombre d’arguments attendu pour l’annotation ne correspond pas au nombre réel d’arguments pour l’annotation      |
|                       [C6706](../code-quality/c6706.md)                        |                                  Erreur d'annotation inattendue pour l'annotation                                   |
|                      [C28021](../code-quality/c28021.md)                       |                                Le paramètre annoté doit être un pointeur                                |
|                      [C28182](../code-quality/c28182.md)                       |         Déréférencement du pointeur NULL. Le pointeur contient la même valeur NULL qu'un autre pointeur.          |
|                      [C28202](../code-quality/c28202.md)                       |                                    Référence non autorisée à un membre non statique                                     |
|                      [C28203](../code-quality/c28203.md)                       |                                     Référence ambiguë à un membre de classe.                                      |
|                      [C28205](../code-quality/c28205.md)                       |                           \_Success\_ ou \_On_failure\_ utilisé dans un contexte non autorisé                            |
|                      [C28206](../code-quality/c28206.md)                       |                                   L’opérande de gauche pointe vers un struct, utiliser '->'                                   |
|                      [C28207](../code-quality/c28207.md)                       |                                       L’opérande de gauche est un struct, utiliser '.'                                       |
|                      [C28210](../code-quality/c28210.md)                       |                 Les annotations pour le contexte __on_failure ne doivent pas se trouver dans un contexte préalable explicite                  |
|                      [C28211](../code-quality/c28211.md)                       |                                 Nom du contexte statique attendu pour SAL_context                                  |
|                      [C28212](../code-quality/c28212.md)                       |                                  Expression de pointeur attendue pour l'annotation                                   |
|                      [C28213](../code-quality/c28213.md)                       | L’annotation \_Use_decl_annotations\_ doit être utilisée pour référencer, sans modification, une déclaration antérieure. |
|                      [C28214](../code-quality/c28214.md)                       |                                   Les noms des paramètres d'attribut doivent être p1...p9                                   |
|                      [C28215](../code-quality/c28215.md)                       |                    Le typefix ne peut pas être appliqué à un paramètre qui contient déjà un typefix                    |
|                      [C28216](../code-quality/c28216.md)                       |        L'annotation checkReturn ne s'applique qu'aux post-conditions pour le paramètre de fonction spécifique.         |
|                      [C28217](../code-quality/c28217.md)                       |            Pour la fonction, le nombre de paramètres de l'annotation ne correspond pas au nombre trouvé dans le fichier             |
|                      [C28218](../code-quality/c28218.md)                       |             Pour le paramètre de fonction, le paramètre de l’annotation ne correspond pas à celui trouvé dans le fichier              |
|                      [C28219](../code-quality/c28219.md)                       |                 Membre de l'énumération attendu pour une annotation, le paramètre dans l'annotation                 |
|                      [C28220](../code-quality/c28220.md)                       |                  Expression d'entier attendue pour une annotation, le paramètre dans l'annotation                   |
|                      [C28221](../code-quality/c28221.md)                       |                        Expression de chaîne attendue pour le paramètre dans l'annotation                         |
|                      [C28222](../code-quality/c28222.md)                       |                               __yes, \__no ou \__maybe attendus pour l’annotation                               |
|                      [C28223](../code-quality/c28223.md)                       |                       Jeton/identificateur introuvable pour l'annotation, paramètre                        |
|                      [C28224](../code-quality/c28224.md)                       |                                        L'annotation requiert des paramètres                                         |
|                      [C28225](../code-quality/c28225.md)                       |                     Nombre correct de paramètres requis introuvable dans l'annotation                      |
|                      [C28226](../code-quality/c28226.md)                       |                          L'annotation ne peut pas être également un PrimOp (dans la déclaration actuelle)                          |
|                      [C28227](../code-quality/c28227.md)                       |                          L'annotation ne peut pas être également un PrimOp (voir la déclaration antérieure)                           |
|                      [C28228](../code-quality/c28228.md)                       |                             Paramètre d'annotation : impossible d'utiliser ce type dans les annotations                              |
|                      [C28229](../code-quality/c28229.md)                       |                                    L'annotation ne prend pas en charge les paramètres                                     |
|                      [C28230](../code-quality/c28230.md)                       |                                     Le type de paramètre ne contient pas de membre.                                      |
|                      [C28231](../code-quality/c28231.md)                       |                                       L'annotation n'est valide que sur un tableau                                       |
|                      [C28232](../code-quality/c28232.md)                       |                               pre, post, ou deref ne sont appliqués à aucune annotation                               |
|                      [C28233](../code-quality/c28233.md)                       |                                    pre, post ou deref sont appliqués à un bloc                                     |
|                      [C28234](../code-quality/c28234.md)                       |                              l'expression __at ne s'applique pas à la fonction actuelle                               |
|                      [C28235](../code-quality/c28235.md)                       |                               La fonction ne peut pas constituer à elle seule une annotation                                |
|                      [C28236](../code-quality/c28236.md)                       |                                L'annotation ne peut pas être utilisée dans une expression                                 |
|                      [C28237](../code-quality/c28237.md)                       |                              L'annotation sur le paramètre n'est plus prise en charge                               |
|                      [C28238](../code-quality/c28238.md)                       |      Plusieurs value, stringValue et longValue sont définies dans l'annotation sur le paramètre. Utiliser paramn=xxx       |
|                      [C28239](../code-quality/c28239.md)                       |  value, stringValue ou longValue, et paramn=xxx sont définis en même temps dans l'annotation sur le paramètre. Utiliser uniquement paramn=xxx   |
|                      [C28240](../code-quality/c28240.md)                       |                             L'annotation sur le paramètre possède un param2, mais pas de param1                              |
|                      [C28241](../code-quality/c28241.md)                       |                          L'annotation pour la fonction sur le paramètre n'est pas reconnue                           |
|                      [C28243](../code-quality/c28243.md)                       |   L’annotation pour la fonction sur le paramètre nécessite plus de déréférencements que le type réel annoté ne le permet.   |
|                      [C28245](../code-quality/c28245.md)                       |                     L’annotation pour la fonction annote ’this’ sur une fonction non membre                     |
|                      [C28246](../code-quality/c28246.md)                       |                L'annotation du paramètre ne correspond pas au type du paramètre                 |
|                      [C28250](../code-quality/c28250.md)                       |                    Annotation incohérente pour une fonction : l'instance précédente contient une erreur.                     |
|                      [C28251](../code-quality/c28251.md)                       |                       Annotation incohérente pour une fonction : cette instance contient une erreur.                       |
|                      [C28252](../code-quality/c28252.md)                       |           Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.           |
|                      [C28253](../code-quality/c28253.md)                       |           Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.           |
|                      [C28254](../code-quality/c28254.md)                       |                               dynamic_cast<>() n'est pas pris en charge dans les annotations                                |
|                      [C28262](../code-quality/c28262.md)                       |                    Une erreur de syntaxe dans l'annotation a été trouvée dans la fonction, pour l'annotation                     |
|                      [C28263](../code-quality/c28263.md)                       |                 Une erreur de syntaxe dans une annotation conditionnelle a été trouvée pour l'annotation intrinsèque                 |
|                      [C28267](../code-quality/c28267.md)                       |                    Une erreur de syntaxe dans les annotations a été trouvée pour l'annotation dans la fonction.                    |
|                      [C28272](../code-quality/c28272.md)                       |      L'annotation pour la fonction, paramètre pendant la vérification est incohérente avec la déclaration de fonction      |
|                      [C28273](../code-quality/c28273.md)                       |                    Pour la fonction, les indices sont incohérents avec la déclaration de fonction                     |
|                      [C28275](../code-quality/c28275.md)                       |                                   Le paramètre de \_Macro_value\_ a une valeur null                                    |
|                      [C28279](../code-quality/c28279.md)                       |                           Pour le symbole, un 'begin' a été trouvé sans le 'end' correspondant                            |
|                      [C28280](../code-quality/c28280.md)                       |                           Pour le symbole, un 'end' a été trouvé sans le 'begin' correspondant                           |
|                      [C28282](../code-quality/c28282.md)                       |                                    Les chaînes de format doivent être comprises dans des conditions préalables                                    |
|                      [C28285](../code-quality/c28285.md)                       |                                    Pour la fonction, erreur de syntaxe dans le paramètre                                    |
|                      [C28286](../code-quality/c28286.md)                       |                                    Pour la fonction, erreur de syntaxe près de la fin                                    |
|                      [C28287](../code-quality/c28287.md)                       |                Pour la fonction, erreur de syntaxe dans l’annotation \_At\_() (nom de paramètre non reconnu)                |
|                      [C28288](../code-quality/c28288.md)                       |                  Pour la fonction, erreur de syntaxe dans l’annotation \_At\_() (nom de paramètre non valide)                   |
|                      [C28289](../code-quality/c28289.md)                       |                Pour la fonction : ReadableTo ou WritableTo n'a pas eu de spécification de limites en tant que paramètre                |
|                      [C28290](../code-quality/c28290.md)                       |           l'annotation pour la fonction contient plus d'Externals que le nombre réel de paramètres            |
|                      [C28291](../code-quality/c28291.md)                       |                        post null/notnull au niveau 0 deref n'a pas de sens pour la fonction.                        |
|                      [C28300](../code-quality/c28300.md)                       |                            Opérandes d’expression de types incompatibles pour l’opérateur                             |
|                      [C28301](../code-quality/c28301.md)                       |                               Aucune annotation pour la première déclaration de la fonction.                               |
|                      [C28302](../code-quality/c28302.md)                       |                             Un opérateur \_Deref\_ en trop a été trouvé dans une annotation.                              |
|                      [C28303](../code-quality/c28303.md)                       |                           Un opérateur ambigu \_Deref\_ a été trouvé dans une annotation.                            |
|                      [C28304](../code-quality/c28304.md)                       |                     Un opérateur \_Notref\_ placé de manière incorrecte et appliqué à un jeton a été trouvé.                      |
|                      [C28305](../code-quality/c28305.md)                       |                                Une erreur a été détectée pendant l'analyse d'un jeton.                                 |
|                      [C28350](../code-quality/c28350.md)                       |                  L'annotation décrit une situation qui n'est pas applicable de manière conditionnelle.                   |
|                      [C28351](../code-quality/c28351.md)                       |         L'annotation décrit l'emplacement auquel une valeur dynamique (une variable) ne peut pas être utilisée dans la condition.          |
