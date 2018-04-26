---
title: Ensemble de règles des règles recommandées mixtes
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77774f4460bab7b36fd3684175228e7522a67027
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="mixed-recommended-rules-rule-set"></a>Ensemble de règles des règles recommandées mixtes

Les règles recommandées mixtes Microsoft vous concentrer sur les problèmes plus courants et critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, notamment les failles de sécurité potentielles, application tombe en panne et autres erreurs de logique et de conception importantes. Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.

|Règle|Description|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Utilisation d'une mémoire non initialisée|
|[C6011](../code-quality/c6011.md)|Déréférencement du pointeur Null|
|[C6029](../code-quality/c6029.md)|Utilisation d'une valeur non vérifiée|
|[C6031](../code-quality/c6031.md)|Valeur de retour ignorée|
|[C6053](../code-quality/c6053.md)|Terminaison par zéro de l'appel|
|[C6054](../code-quality/c6054.md)|Zéro arrêt manquant|
|[C6059](../code-quality/c6059.md)|Concaténation non valide|
|[C6063](../code-quality/c6063.md)|Argument de chaîne manquant pour le formatage de la fonction|
|[C6064](../code-quality/c6064.md)|Argument d’entier manquant pour le formatage de la fonction|
|[C6066](../code-quality/c6066.md)|Argument de pointeur manquant pour le formatage de la fonction|
|[C6067](../code-quality/c6067.md)|Argument de pointeur de chaîne manquant pour le formatage de la fonction|
|[C6101](../code-quality/c6101.md)|Retour d'une mémoire non initialisée|
|[C6200](../code-quality/c6200.md)|L'index dépasse la taille maximale autorisée par la mémoire tampon|
|[C6201](../code-quality/c6201.md)|L'index dépasse la taille maximale autorisée par la mémoire tampon allouée par la pile|
|[C6214](../code-quality/c6214.md)|Transtypage de HRESULT vers BOOL non valide|
|[C6215](../code-quality/c6215.md)|Transtypage de BOOL vers HRESULT non valide|
|[C6216](../code-quality/c6216.md)|Cast inséré par le compilateur BOOL vers HRESULT non valide|
|[C6217](../code-quality/c6217.md)|Test HRESULT non valide avec NOT|
|[C6220](../code-quality/c6220.md)|Comparaison HRESULT non valide-1|
|[C6226](../code-quality/c6226.md)|Affectation de HRESULT non valide à -1|
|[C6230](../code-quality/c6230.md)|Utilisation HRESULT non valide en tant que valeur booléenne|
|[C6235](../code-quality/c6235.md)|Une constante non nulle avec logique- ou|
|[C6236](../code-quality/c6236.md)|Logique- ou avec une constante Non nulle|
|[C6237](../code-quality/c6237.md)|Zéro avec logique- et perd ses effets|
|[C6242](../code-quality/c6242.md)|Déroulement local forcé|
|[C6248](../code-quality/c6248.md)|Créer des DACL Null|
|[C6250](../code-quality/c6250.md)|Descripteurs d’adresses non commercialisés|
|[C6255](../code-quality/c6255.md)|Utilisation non protégée d’Alloca|
|[C6258](../code-quality/c6258.md)|À l’aide de terminer le Thread|
|[C6259](../code-quality/c6259.md)|Bloquer le Code au niveau du bit- ou limités commutateur|
|[C6260](../code-quality/c6260.md)|Utilisation de l’arithmétique d’octets|
|[C6262](../code-quality/c6262.md)|Utilisation de la pile excessive|
|[C6263](../code-quality/c6263.md)|Utilisation d’Alloca dans une boucle|
|[C6268](../code-quality/c6268.md)|Parenthèses manquantes dans un Cast|
|[C6269](../code-quality/c6269.md)|Déréférencement de pointeur ignoré|
|[C6270](../code-quality/c6270.md)|Argument float manquant pour le formatage de la fonction|
|[C6271](../code-quality/c6271.md)|Argument supplémentaire pour le formatage de la fonction|
|[C6272](../code-quality/c6272.md)|Argument non float pour le formatage de la fonction|
|[C6273](../code-quality/c6273.md)|Argument non entier pour le formatage de la fonction|
|[C6274](../code-quality/c6274.md)|Argument autre qu’un caractère pour le formatage de la fonction|
|[C6276](../code-quality/c6276.md)|Cast de chaîne non valide|
|[C6277](../code-quality/c6277.md)|Appel CreateProcess non valide|
|[C6278](../code-quality/c6278.md)|Incompatibilité de tableau New et scalaire Delete|
|[C6279](../code-quality/c6279.md)|Incompatibilité de Scalar-nouveau tableau-supprimer|
|[C6280](../code-quality/c6280.md)|Incompatibilité de désallocation de l’Allocation de mémoire|
|[C6281](../code-quality/c6281.md)|Priorité de la Relation au niveau du bit|
|[C6282](../code-quality/c6282.md)|Affectation remplace le Test|
|[C6283](../code-quality/c6283.md)|Incompatibilité de tableau New et scalaire Delete primitifs|
|[C6284](../code-quality/c6284.md)|Argument d’objet non valide pour le formatage de la fonction|
|[C6285](../code-quality/c6285.md)|Logique- ou des constantes|
|[C6286](../code-quality/c6286.md)|Différent de zéro logique- ou perte des effets secondaires|
|[C6287](../code-quality/c6287.md)|Test redondant|
|[C6288](../code-quality/c6288.md)|L’Inclusion mutuelle sur logique- et a la valeur False|
|[C6289](../code-quality/c6289.md)|L’Exclusion mutuelle sur logique- ou a la valeur True|
|[C6290](../code-quality/c6290.md)|Priorité NOT logique et AND au niveau du bit|
|[C6291](../code-quality/c6291.md)|Priorité NOT logique et OR au niveau du bit|
|[C6292](../code-quality/c6292.md)|La boucle calcule à partir de la valeur maximale|
|[C6293](../code-quality/c6293.md)|Boucle calcule à rebours à partir de la valeur minimale|
|[C6294](../code-quality/c6294.md)|Corps de la boucle jamais exécuté|
|[C6295](../code-quality/c6295.md)|Boucle infinie|
|[C6296](../code-quality/c6296.md)|Boucle exécutée une fois|
|[C6297](../code-quality/c6297.md)|Effectuer un Cast du résultat du décalage à plus grande taille|
|[C6299](../code-quality/c6299.md)|Champ de bits et comparaison booléenne|
|[C6302](../code-quality/c6302.md)|Argument de chaîne de caractères non valide pour le formatage de la fonction|
|[C6303](../code-quality/c6303.md)|Argument de chaîne de caractères larges non valide pour le formatage de la fonction|
|[C6305](../code-quality/c6305.md)|Incompatibilité entre la taille et la quantité|
|[C6306](../code-quality/c6306.md)|Appel de fonction d’argument de variable non valide|
|[C6308](../code-quality/c6308.md)|Realloc fuite|
|[C6310](../code-quality/c6310.md)|Constante de filtre d’Exception non conforme|
|[C6312](../code-quality/c6312.md)|L’exception Continue la boucle d’exécution|
|[C6314](../code-quality/c6314.md)|Au niveau du bit- ou la priorité|
|[C6317](../code-quality/c6317.md)|Complément est pas|
|[C6318](../code-quality/c6318.md)|L’exception Continue la recherche|
|[C6319](../code-quality/c6319.md)|Ignoré par une virgule|
|[C6324](../code-quality/c6324.md)|Copie d’une chaîne au lieu de la comparaison de chaînes|
|[C6328](../code-quality/c6328.md)|Incompatibilité de type d’argument possible|
|[C6331](../code-quality/c6331.md)|Indicateurs de VirtualFree n’est pas valide|
|[C6332](../code-quality/c6332.md)|Paramètre non valide de VirtualFree|
|[C6333](../code-quality/c6333.md)|Taille de VirtualFree n’est pas valide|
|[C6335](../code-quality/c6335.md)|Handle de processus|
|[C6381](../code-quality/c6381.md)|Arrêt informations manquantes|
|[C6383](../code-quality/c6383.md)|Nombre d’éléments Byte-dépassement de mémoire tampon de nombre|
|[C6384](../code-quality/c6384.md)|Division de taille de pointeur|
|[C6385](../code-quality/c6385.md)|Dépassement en lecture|
|[C6386](../code-quality/c6386.md)|Dépassement en écriture|
|[C6387](../code-quality/c6387.md)|Valeur de paramètre non valide|
|[C6388](../code-quality/c6388.md)|Valeur de paramètre non valide|
|[C6500](../code-quality/c6500.md)|Propriété d'attribut non valide|
|[C6501](../code-quality/c6501.md)|Valeurs de propriété d'attribut en conflit|
|[C6503](../code-quality/c6503.md)|Les références ne peuvent pas être Null|
|[C6504](../code-quality/c6504.md)|Null sur élément non pointeur|
|[C6505](../code-quality/c6505.md)|MustCheck sur Void|
|[C6506](../code-quality/c6506.md)|Taille de mémoire tampon sur élément non pointeur ou tableau|
|[C6508](../code-quality/c6508.md)|Accès en écriture sur constante|
|[C6509](../code-quality/c6509.md)|Retour utilisé sur condition préalable|
|[C6510](../code-quality/c6510.md)|Terminaison par Null sur élément non pointeur|
|[C6511](../code-quality/c6511.md)|MustCheck doit avoir la valeur Yes ou No|
|[C6513](../code-quality/c6513.md)|Taille d'élément sans taille de mémoire tampon|
|[C6514](../code-quality/c6514.md)|Taille de mémoire tampon dépasse la taille du tableau|
|[C6515](../code-quality/c6515.md)|Taille de la mémoire tampon sur élément non pointeur|
|[C6516](../code-quality/c6516.md)|Attribut sans propriété|
|[C6517](../code-quality/c6517.md)|Taille valide dans mémoire tampon non lisible|
|[C6518](../code-quality/c6518.md)|Taille accessible en écriture dans mémoire tampon non accessible en écriture|
|[C6522](../code-quality/c6522.md)|Type de chaîne de taille non valide|
|[C6525](../code-quality/c6525.md)|Chaîne de taille non valide. Emplacement inaccessible|
|[C6527](../code-quality/c6527.md)|Annotation non valide : la propriété NeedsRelease ne doit pas être utilisée sur des valeurs de type void|
|[C6530](../code-quality/c6530.md)|Style de chaîne de format non reconnu|
|[C6540](../code-quality/c6540.md)|L'utilisation des annotations d'attribut sur cette fonction rendra non valides toutes ses annotations __declspec existantes|
|[C6551](../code-quality/c6551.md)|Spécification de taille non valide : expression impossible à analyser|
|[C6552](../code-quality/c6552.md)|Deref= ou Noref= non valide : expression impossible à analyser|
|[C6701](../code-quality/c6701.md)|La valeur n'est pas une valeur Yes/No/Maybe valide|
|[C6702](../code-quality/c6702.md)|La valeur n'est pas une valeur de chaîne|
|[C6703](../code-quality/c6703.md)|La valeur n'est pas un nombre|
|[C6704](../code-quality/c6704.md)|Erreur d'expression de l'annotation inattendue|
|[C6705](../code-quality/c6705.md)|Le nombre d’arguments attendu pour l’annotation ne correspond pas au nombre réel d’arguments pour l’annotation|
|[C6706](../code-quality/c6706.md)|Erreur d'annotation inattendue pour l'annotation|
|[C6995](../code-quality/c6995.md)|Impossible d’enregistrer le fichier journal XML|
|[C26100](../code-quality/c26100.md)|Condition de concurrence|
|[C26101](../code-quality/c26101.md)|Absence d’utilisation d’une opération à blocage correctement|
|[C26110](../code-quality/c26110.md)|Appelant ne parvenant pas à maintenir le verrou|
|[C26111](../code-quality/c26111.md)|Appelant ne parvenant pas à libérer le verrou|
|[C26112](../code-quality/c26112.md)|L’appelant ne peut pas contenir un verrou quelconque|
|[C26115](../code-quality/c26115.md)|Échec de libération du verrou|
|[C26116](../code-quality/c26116.md)|Échec d’acquisition ou du maintien du verrou|
|[C26117](../code-quality/c26117.md)|Libérer un verrou non maintenu|
|[C26140](../code-quality/c26140.md)|Erreur d’annotation SAL d’accès concurrentiel|
|[C28020](../code-quality/c28020.md)|L’expression n’est pas true dans cet appel|
|[C28021](../code-quality/c28021.md)|Le paramètre annoté doit être un pointeur|
|[C28022](../code-quality/c28022.md)|Les classes de fonction sur cette fonction ne correspondent pas à la fonction ou les classes sur le typedef utilisé pour le définir.|
|[C28023](../code-quality/c28023.md)|La fonction est assigné ou passée doit avoir un _Function_class\_ annotation pour au moins de l’ou les classes|
|[C28024](../code-quality/c28024.md)|Le pointeur de fonction assigné à est annoté avec la classe de fonction, ce qui n’est pas contenue dans la liste de classes de fonction.|
|[C28039](../code-quality/c28039.md)|Le type du paramètre réel doit correspondre exactement au type|
|[C28112](../code-quality/c28112.md)|Une variable qui est accessible via une fonction Interlocked doit toujours être accessible via une fonction Interlocked.|
|[C28113](../code-quality/c28113.md)|L’accès à une variable locale via une fonction Interlocked|
|[C28125](../code-quality/c28125.md)|La fonction doit être appelée à partir de dans un bloc try / except bloc|
|[C28137](../code-quality/c28137.md)|L’argument de variable doit être à la place d’une constante (littérale)|
|[C28138](../code-quality/c28138.md)|L’argument constante doit plutôt être une variable|
|[C28159](../code-quality/c28159.md)|Envisagez d’utiliser une autre fonction à la place.|
|[C28160](../code-quality/c28160.md)|annotation d'erreur|
|[C28163](../code-quality/c28163.md)|La fonction ne doit jamais être appelée à partir d’un bloc try / except bloc|
|[C28164](../code-quality/c28164.md)|L’argument est passé à une fonction qui attend un pointeur vers un objet (pas un pointeur vers un pointeur)|
|[C28182](../code-quality/c28182.md)|Déréférencement du pointeur NULL. Le pointeur contient la même valeur NULL qu'un autre pointeur.|
|[C28183](../code-quality/c28183.md)|L’argument peut être une valeur, et est une copie de la valeur trouvée dans le pointeur|
|[C28193](../code-quality/c28193.md)|La variable contienne une valeur qui doit être examinée.|
|[C28196](../code-quality/c28196.md)|La configuration requise n’est pas satisfaite. (L’expression ne correspond pas à la valeur true).|
|[C28202](../code-quality/c28202.md)|Référence non autorisée à un membre non statique|
|[C28203](../code-quality/c28203.md)|Référence ambiguë à un membre de classe.|
|[C28205](../code-quality/c28205.md)|_Success\_ ou _On_failure\_ utilisé dans un contexte non autorisé|
|[C28206](../code-quality/c28206.md)|L’opérande de gauche pointe vers un struct, utiliser '->'|
|[C28207](../code-quality/c28207.md)|L’opérande de gauche est un struct, utiliser '.'|
|[C28209](../code-quality/c28209.md)|La déclaration du symbole possède une déclaration en conflit|
|[C28210](../code-quality/c28210.md)|Les annotations pour le contexte __on_failure ne doivent pas se trouver dans un contexte préalable explicite|
|[C28211](../code-quality/c28211.md)|Nom du contexte statique attendu pour SAL_context|
|[C28212](../code-quality/c28212.md)|Expression de pointeur attendue pour l'annotation|
|[C28213](../code-quality/c28213.md)|L’annotation _Use_decl_annotations\_ doit être utilisée pour référencer, sans modification, une déclaration antérieure.|
|[C28214](../code-quality/c28214.md)|Les noms des paramètres d'attribut doivent être p1...p9|
|[C28215](../code-quality/c28215.md)|Le typefix ne peut pas être appliqué à un paramètre qui contient déjà un typefix|
|[C28216](../code-quality/c28216.md)|L'annotation checkReturn ne s'applique qu'aux post-conditions pour le paramètre de fonction spécifique.|
|[C28217](../code-quality/c28217.md)|Pour la fonction, le nombre de paramètres de l'annotation ne correspond pas au nombre trouvé dans le fichier|
|[C28218](../code-quality/c28218.md)|Paramètre de fonction, paramètre de l’annotation ne correspond pas trouvé dans le fichier|
|[C28219](../code-quality/c28219.md)|Membre de l'énumération attendu pour une annotation, le paramètre dans l'annotation|
|[C28220](../code-quality/c28220.md)|Expression d'entier attendue pour une annotation, le paramètre dans l'annotation|
|[C28221](../code-quality/c28221.md)|Expression de chaîne attendue pour le paramètre dans l'annotation|
|[C28222](../code-quality/c28222.md)|__yes, \__no ou \__maybe attendus pour l’annotation|
|[C28223](../code-quality/c28223.md)|Jeton/identificateur introuvable pour l'annotation, paramètre|
|[C28224](../code-quality/c28224.md)|L'annotation requiert des paramètres|
|[C28225](../code-quality/c28225.md)|Nombre correct de paramètres requis introuvable dans l'annotation|
|[C28226](../code-quality/c28226.md)|L'annotation ne peut pas être également un PrimOp (dans la déclaration actuelle)|
|[C28227](../code-quality/c28227.md)|L'annotation ne peut pas être également un PrimOp (voir la déclaration antérieure)|
|[C28228](../code-quality/c28228.md)|Paramètre d'annotation : impossible d'utiliser ce type dans les annotations|
|[C28229](../code-quality/c28229.md)|L'annotation ne prend pas en charge les paramètres|
|[C28230](../code-quality/c28230.md)|Le type de paramètre ne contient pas de membre.|
|[C28231](../code-quality/c28231.md)|L'annotation n'est valide que sur un tableau|
|[C28232](../code-quality/c28232.md)|pre, post, ou deref ne sont appliqués à aucune annotation|
|[C28233](../code-quality/c28233.md)|pre, post ou deref sont appliqués à un bloc|
|[C28234](../code-quality/c28234.md)|l'expression __at ne s'applique pas à la fonction actuelle|
|[C28235](../code-quality/c28235.md)|La fonction ne peut pas constituer à elle seule une annotation|
|[C28236](../code-quality/c28236.md)|L'annotation ne peut pas être utilisée dans une expression|
|[C28237](../code-quality/c28237.md)|L'annotation sur le paramètre n'est plus prise en charge|
|[C28238](../code-quality/c28238.md)|Plusieurs value, stringValue et longValue sont définies dans l'annotation sur le paramètre. Utiliser paramn=xxx|
|[C28239](../code-quality/c28239.md)|value, stringValue ou longValue, et paramn=xxx sont définis en même temps dans l'annotation sur le paramètre. Utiliser uniquement paramn=xxx|
|[C28240](../code-quality/c28240.md)|L'annotation sur le paramètre possède un param2, mais pas de param1|
|[C28241](../code-quality/c28241.md)|L'annotation pour la fonction sur le paramètre n'est pas reconnue|
|[C28243](../code-quality/c28243.md)|L’annotation pour la fonction sur le paramètre nécessite plus de déréférencements que le type réel annoté ne le permet.|
|[C28244](../code-quality/c28244.md)|L’annotation pour la fonction a une annotation de paramètre non analysable/externes|
|[C28245](../code-quality/c28245.md)|L’annotation pour la fonction annote ’this’ sur une fonction non membre|
|[C28246](../code-quality/c28246.md)|L'annotation du paramètre ne correspond pas au type du paramètre|
|[C28250](../code-quality/c28250.md)|Annotation incohérente pour une fonction : l'instance précédente contient une erreur.|
|[C28251](../code-quality/c28251.md)|Annotation incohérente pour une fonction : cette instance contient une erreur.|
|[C28252](../code-quality/c28252.md)|Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.|
|[C28253](../code-quality/c28253.md)|Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() n'est pas pris en charge dans les annotations|
|[C28262](../code-quality/c28262.md)|Une erreur de syntaxe dans l'annotation a été trouvée dans la fonction, pour l'annotation|
|[C28263](../code-quality/c28263.md)|Une erreur de syntaxe dans une annotation conditionnelle a été trouvée pour l'annotation intrinsèque|
|[C28267](../code-quality/c28267.md)|Une erreur de syntaxe dans les annotations a été trouvée pour l'annotation dans la fonction.|
|[C28272](../code-quality/c28272.md)|L'annotation pour la fonction, paramètre pendant la vérification est incohérente avec la déclaration de fonction|
|[C28273](../code-quality/c28273.md)|Pour la fonction, les indices sont incohérents avec la déclaration de fonction|
|[C28275](../code-quality/c28275.md)|Le paramètre de _Macro_value\_ a une valeur null|
|[C28279](../code-quality/c28279.md)|Pour le symbole, un 'begin' a été trouvé sans le 'end' correspondant|
|[C28280](../code-quality/c28280.md)|Pour le symbole, un 'end' a été trouvé sans le 'begin' correspondant|
|[C28282](../code-quality/c28282.md)|Les chaînes de format doivent être comprises dans des conditions préalables|
|[C28285](../code-quality/c28285.md)|Pour la fonction, erreur de syntaxe dans le paramètre|
|[C28286](../code-quality/c28286.md)|Pour la fonction, erreur de syntaxe près de la fin|
|[C28287](../code-quality/c28287.md)|Pour la fonction, erreur de syntaxe dans l’annotation _At\_() (nom de paramètre non reconnu)|
|[C28288](../code-quality/c28288.md)|Pour la fonction, erreur de syntaxe dans l’annotation _At\_() (nom de paramètre non valide)|
|[C28289](../code-quality/c28289.md)|Pour la fonction : ReadableTo ou WritableTo n'a pas eu de spécification de limites en tant que paramètre|
|[C28290](../code-quality/c28290.md)|l'annotation pour la fonction contient plus d'Externals que le nombre réel de paramètres|
|[C28291](../code-quality/c28291.md)|post null/notnull au niveau 0 deref n'a pas de sens pour la fonction.|
|[C28300](../code-quality/c28300.md)|Opérandes d’expression de types incompatibles pour l’opérateur|
|[C28301](../code-quality/c28301.md)|Aucune annotation pour la première déclaration de la fonction.|
|[C28302](../code-quality/c28302.md)|Un opérateur extra _Deref\_ a été trouvé dans une annotation.|
|[C28303](../code-quality/c28303.md)|Un opérateur ambigu _Deref\_ a été trouvé dans une annotation.|
|[C28304](../code-quality/c28304.md)|Un opérateur _Notref\_ placé de manière incorrecte et appliqué à un jeton a été trouvé.|
|[C28305](../code-quality/c28305.md)|Une erreur a été détectée pendant l'analyse d'un jeton.|
|[C28306](../code-quality/c28306.md)|L’annotation sur le paramètre est obsolète|
|[C28307](../code-quality/c28307.md)|L’annotation sur le paramètre est obsolète|
|[C28350](../code-quality/c28350.md)|L'annotation décrit une situation qui n'est pas applicable de manière conditionnelle.|
|[C28351](../code-quality/c28351.md)|L'annotation décrit l'emplacement auquel une valeur dynamique (une variable) ne peut pas être utilisée dans la condition.|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Déclarer les gestionnaires d’événements correctement|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Méthodes d’interface doivent pouvoir être appelées par les types enfants|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Ne pas masquer les méthodes de classe de base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implémenter IDisposable correctement|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Ne pas lever d’exceptions dans des emplacements inattendus|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Points d’entrée P/Invoke doivent exister|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke ne doivent pas être visible|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Types base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Méthodes d’inscription COM doivent être mises en correspondance.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Déclarer correctement les méthodes P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Champs de type valeur doivent être portables|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Les déclarations P/Invoke doivent être portables|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ne verrouillent pas sur des objets à identité faible|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Passez en revue les requêtes SQL des failles de sécurité|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Sécurité de la méthode doit être un sur-ensemble du type|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N’exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de remplacement doivent être identiques à la base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Finally vulnérables clauses dans externe try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Liaison de types nécessitent des demandes d’héritage|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas faire partie de l’équivalence de type|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Transparence des méthodes doivent rester cohérente lors de la substitution de méthodes de base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes avec l’attribut SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Types doivent être au moins aussi critiques que leurs types de base et les interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser de sécurité des assertions|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler dans du code natif|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Levez de nouveau pour conserver les détails de la pile|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Ne pas supprimer des objets plusieurs fois|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Initialiser les champs statiques de type valeur en ligne|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Ne marquez pas les composants pris en charge avec WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Des champs supprimables doivent être supprimés.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|N’appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Les finaliseurs doivent appeler le finaliseur de la classe de base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implémentez des constructeurs de sérialisation|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur equals en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Points d’entrée d’interrogation Windows Forms avec STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marquez tous les champs non sérialisables|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Appeler des méthodes de classe de base sur les types ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implémentez les méthodes de sérialisation|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implémentez ISerializable correctement|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Fournissez des arguments corrects aux méthodes de mise en forme|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Correctement des tests NaN|