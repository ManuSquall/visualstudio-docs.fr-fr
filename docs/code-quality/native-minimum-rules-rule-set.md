---
title: "Ensemble de r&#232;gles des r&#232;gles minimales natives | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 3
---
# Ensemble de r&#232;gles des r&#232;gles minimales natives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les Règles Minimum Natives Microsoft se concentrent sur les problèmes les plus critiques rencontrés dans votre code natif, notamment les failles de sécurité potentielles et les blocages d'applications.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisé que vous créez pour vos projets natifs.  
  
|Règle|Description|  
|-----------|-----------------|  
|[C6001](../code-quality/c6001.md)|Utilisation de d'une mémoire non initialisée|  
|[C6011](../code-quality/c6011.md)|Suppression de la référence du pointeur NULL|  
|[C6029](../code-quality/c6029.md)|Utilisation d'une valeur non vérifiée|  
|[C6053](../code-quality/c6053.md)|Terminaison par zéro de l'appel|  
|[C6059](../code-quality/c6059.md)|Mauvaise Concaténation|  
|[C6063](../code-quality/c6063.md)|Argument String manquant pour formater la fonction|  
|[C6064](../code-quality/c6064.md)|Argument Integer manquant pour formater la fonction|  
|[C6066](../code-quality/c6066.md)|Argument Pointer manquant pour formater la fonction|  
|[C6067](../code-quality/c6067.md)|Argument String Pointer manquant pour formater la fonction|  
|[C6101](../code-quality/c6101.md)|Renvoi de la mémoire non initialisée|  
|[C6200](../code-quality/c6200.md)|L'index dépasse la taille maximale autorisée par la mémoire tampon|  
|[C6201](../code-quality/c6201.md)|L'index dépasse la taille maximale autorisée par la mémoire tampon allouée par la pile|  
|[C6270](../code-quality/c6270.md)|Argument float manquant pour le formatage de la fonction|  
|[C6271](../code-quality/c6271.md)|Argument supplémentaire pour le formatage de la fonction|  
|[C6272](../code-quality/c6272.md)|Argument non float pour le formatage de la fonction|  
|[C6273](../code-quality/c6273.md)|Argument non entier pour le formatage de la fonction|  
|[C6274](../code-quality/c6274.md)|Argument autre qu'un caractère pour le formatage de la fonction|  
|[C6276](../code-quality/c6276.md)|Transtypage de chaîne non valide|  
|[C6277](../code-quality/c6277.md)|Appel CreateProcess non valide|  
|[C6284](../code-quality/c6284.md)|Argument objet manquant pour le formatage de la fonction|  
|[C6290](../code-quality/c6290.md)|Priorité NOT logique et AND au niveau du bit|  
|[C6291](../code-quality/c6291.md)|Priorité NOT logique et OR au niveau du bit|  
|[C6302](../code-quality/c6302.md)|Argument de chaîne de caractères non valide pour formater la fonction|  
|[C6303](../code-quality/c6303.md)|Argument de chaîne de caractères larges invalide pour formater la fonction|  
|[C6305](../code-quality/c6305.md)|Incompatibilité entre la taille et la quantité|  
|[C6306](../code-quality/c6306.md)|Appel de fonction d'argument de variable non valide|  
|[C6328](../code-quality/c6328.md)|Incompatibilité de type d'argument possible|  
|[C6385](../code-quality/c6385.md)|Dépassement en lecture|  
|[C6386](../code-quality/c6386.md)|Dépassement en écriture|  
|[C6387](../code-quality/c6387.md)|Valeur du paramètre non valide|  
|[C6500](../code-quality/c6500.md)|Propriété d'attribut non\-valide|  
|[C6501](../code-quality/c6501.md)|Valeurs de propriété d'attribut en conflit|  
|[C6503](../code-quality/c6503.md)|Les références ne peut pas avoir la valeur null|  
|[C6504](../code-quality/c6504.md)|Null sur élément non pointeur|  
|[C6505](../code-quality/c6505.md)|MustCheck sur Void|  
|[C6506](../code-quality/c6506.md)|Taille de mémoire tampon sur élément non pointeur ou tableau|  
|[C6507](http://msdn.microsoft.com/fr-fr/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Incompatibilité de Null de déférencement de zéro|  
|[C6508](../code-quality/c6508.md)|Accès en écriture sur constante|  
|[C6509](../code-quality/c6509.md)|Retour utilisé sur condition préalable|  
|[C6510](../code-quality/c6510.md)|Terminaison par Null sur élément non pointeur|  
|[C6511](../code-quality/c6511.md)|MustCheck doit avoir la valeur Yes ou No|  
|[C6513](../code-quality/c6513.md)|Taille d'élément sans taille de mémoire tampon|  
|[C6514](../code-quality/c6514.md)|Taille de mémoire tampon dépasse la taille du tableau|  
|[C6515](../code-quality/c6515.md)|Taille de mémoire tampon sur élément non pointeur|  
|[C6516](../code-quality/c6516.md)|Pas de propriétés sur l'attribut|  
|[C6517](../code-quality/c6517.md)|Taille valide dans mémoire tampon non lisible|  
|[C6518](../code-quality/c6518.md)|Taille accessible en écriture dans mémoire tampon non accessible en écriture|  
|[C6519](http://msdn.microsoft.com/fr-fr/2b6326b0-0539-4d26-8fb1-720114933232)|Annotation non valide : la valeur de la propriété 'NeedsRelease' doit être définie à Yes ou No|  
|[C6521](http://msdn.microsoft.com/fr-fr/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|Déférencement de String Size non valide|  
|[C6522](../code-quality/c6522.md)|Type de String Size Invalid|  
|[C6523](http://msdn.microsoft.com/fr-fr/11397a31-b224-46b0-afb7-d49ca576a3bb)|Paramètre de taille de chaîne non valide|  
|[C6525](../code-quality/c6525.md)|Chaîne de taille non valide. Emplacement inaccessible.|  
|[C6526](http://msdn.microsoft.com/fr-fr/59c590c7-0098-4166-a1ac-87f324596002)|Taille du type de tampon de chaîne invalide|  
|[C6527](../code-quality/c6527.md)|Annotation non valide : la propriété 'NeedsRelease' peut ne pas être utilisée dans des valeurs de type void|  
|[C6530](../code-quality/c6530.md)|Style de chaîne de format non reconnu|  
|[C6540](../code-quality/c6540.md)|L'utilisation d'annotations d'attribut sur cette fonction invalidera l'ensemble de ses annotations \_\_declspec existantes|  
|[C6551](../code-quality/c6551.md)|Spécification de taille non valide : l'expression n'est pas analysable|  
|[C6552](../code-quality/c6552.md)|Deref\= ou Notref\= non valide : l'expression n'est pas analysable|  
|[C6701](../code-quality/c6701.md)|La valeur n'est pas une valeur Yes\/No\/Maybe valide|  
|[C6702](../code-quality/c6702.md)|La valeur n'est pas une valeur de chaîne|  
|[C6703](../code-quality/c6703.md)|La valeur n'est pas un nombre|  
|[C6704](../code-quality/c6704.md)|Erreur d'expression de l'annotation inattendue|  
|[C6705](../code-quality/c6705.md)|Le nombre d'arguments attendus pour l'annotation ne correspond pas au nombre réel d'arguments pour l'annotation|  
|[C6706](../code-quality/c6706.md)|Erreur d'Annotation pour l'annotation inattendue|  
|[C28021](../code-quality/c28021.md)|Le paramètre annoté doit être un pointeur|  
|[C28182](../code-quality/c28182.md)|Déréférencer le pointeur NULL.  Le pointeur contient la même valeur NULL que contenait un autre pointeur.|  
|[C28202](../code-quality/c28202.md)|Référence non autorisée au membre non statique|  
|[C28203](../code-quality/c28203.md)|Référence ambiguë au membre de classe.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ ou \_On\_failure\_ utilisés dans un contexte non autorisé|  
|[C28206](../code-quality/c28206.md)|L'opérande de gauche pointe vers un struct, utiliser '\-\>'|  
|[C28207](../code-quality/c28207.md)|L'opérande de gauche est un struct, utiliser '.'|  
|[C28210](../code-quality/c28210.md)|Les annotations pour le contexte \_\_on\_failure ne doivent pas se trouver dans un contexte préalable explicite|  
|[C28211](../code-quality/c28211.md)|Nom du contexte statique attendu pour SAL\_context|  
|[C28212](../code-quality/c28212.md)|Expression de pointeur attendue pour l'annotation|  
|[C28213](../code-quality/c28213.md)|L'annotation \_Use\_decl\_annotations\_ doit être utilisée pour référencer, sans modification, une déclaration antérieure.|  
|[C28214](../code-quality/c28214.md)|Les noms des paramètres d'attribut doivent être p1…p9|  
|[C28215](../code-quality/c28215.md)|Le typefix ne peut pas être appliqué à un paramètre qui contient déjà un typefix|  
|[C28216](../code-quality/c28216.md)|L'annotation checkReturn s'applique uniquement aux postconditions pour le paramètre fonction spécifique.|  
|[C28217](../code-quality/c28217.md)|Pour la fonction, le nombre de paramètres de l'annotation ne correspond pas au nombre trouvé dans le fichier|  
|[C28218](../code-quality/c28218.md)|Pour le paramètre de la fonction, le paramètre de l'annotation ne correspond pas au nombre trouvé sur le fichier|  
|[C28219](../code-quality/c28219.md)|Membre de l'énumération attendu pour une annotation, le paramètre dans l'annotation|  
|[C28220](../code-quality/c28220.md)|Expression d'entier attendue pour annotation du paramètre dans l'annotation|  
|[C28221](../code-quality/c28221.md)|Expression de chaîne attendue pour le paramètre dans l'annotation|  
|[C28222](../code-quality/c28222.md)|\_\_yes, \_\_no, ou \_\_maybe attendu pour l'annotation|  
|[C28223](../code-quality/c28223.md)|Jeton\/identificateur attendu pour le paramètre de l'annotation|  
|[C28224](../code-quality/c28224.md)|L'annotation requiert des paramètres|  
|[C28225](../code-quality/c28225.md)|N'a pas trouvé le nombre correcte de paramètres requis dans l'annotation|  
|[C28226](../code-quality/c28226.md)|L'annotation ne peut pas être un PrimOp également \(dans la déclaration actuelle\)|  
|[C28227](../code-quality/c28227.md)|L'annotation ne peut pas être un PrimOp également \(voir la déclaration antérieure\)|  
|[C28228](../code-quality/c28228.md)|Annotation paramètre : le type ne peut pas être utilisé dans les annotations|  
|[C28229](../code-quality/c28229.md)|L'annotation ne prend pas en charge des paramètres|  
|[C28230](../code-quality/c28230.md)|Le type de paramètre n'a aucun membre.|  
|[C28231](../code-quality/c28231.md)|L'annotation n'est valide que sur un tableau|  
|[C28232](../code-quality/c28232.md)|pre, post, ou deref ne sont appliqués à aucune annotation|  
|[C28233](../code-quality/c28233.md)|pre, post, ou deref sont appliqués à un bloc|  
|[C28234](../code-quality/c28234.md)|L'expression \_\_at ne s'applique pas à la fonction active|  
|[C28235](../code-quality/c28235.md)|La fonction ne peut pas être une annotation autonome|  
|[C28236](../code-quality/c28236.md)|L'annotation ne peut pas être utilisée dans une expression|  
|[C28237](../code-quality/c28237.md)|L'annotation sur paramètre n'est plus prise en charge|  
|[C28238](../code-quality/c28238.md)|L'annotation sur paramètre possède plusieurs valeurs, stringValue, et longValue.  Utilisez paramn\=xxx|  
|[C28239](../code-quality/c28239.md)|L'annotation sur paramètre possède à la fois value, stringValue, ou longValue ; et paramn\=xxx.  Utiliser uniquement paramn\=xxx|  
|[C28240](../code-quality/c28240.md)|L'annotation sur paramètre possède param2 et non param1|  
|[C28241](../code-quality/c28241.md)|L'Annotation pour la fonction sur paramètre n'est pas reconnu|  
|[C28243](../code-quality/c28243.md)|L'annotation pour la fonction sur paramètre nécessite plus de déréférencements que ne l'autorise le type réel annoté|  
|[C28245](../code-quality/c28245.md)|L'annotation pour la fonction annote 'this' sur une fonction non membre|  
|[C28246](../code-quality/c28246.md)|Le paramètre d'annotation pour la fonction ne correspond pas au type du paramètre|  
|[C28250](../code-quality/c28250.md)|Annotation incohérente pour la function : l'instance précédente présente une erreur.|  
|[C28251](../code-quality/c28251.md)|Annotation incohérente pour la fonction : Cette instance a une erreur.|  
|[C28252](../code-quality/c28252.md)|Annotation incohérente pour la fonction : paramètre a une annotation sur cet instance.|  
|[C28253](../code-quality/c28253.md)|Annotation incohérente pour la fonction : paramètre a une annotation sur cet instance.|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast\<\>\(\) n'est pas pris en charge dans les annotations|  
|[C28262](../code-quality/c28262.md)|Une erreur de syntaxe dans l'annotation a été trouvée dans la fonction pour l'annotation|  
|[C28263](../code-quality/c28263.md)|Une erreur de syntaxe dans une annotation conditionnelle a été trouvée pour l'annotation intrinsèque|  
|[C28264](http://msdn.microsoft.com/fr-fr/bf6ea983-a06e-4752-a042-747a7dbf338c)|Les valeurs des listes de résultats doivent être des constantes.|  
|[C28267](../code-quality/c28267.md)|Une erreur de syntaxe dans les annotations a été trouvée dans la fonction d'annotation.|  
|[C28272](../code-quality/c28272.md)|L'annotation pour la fonction, paramètre lors de l'examen est incohérente avec la déclaration de la fonction|  
|[C28273](../code-quality/c28273.md)|Pour la fonction, les indices sont incohérentes avec la déclaration de la fonction|  
|[C28275](../code-quality/c28275.md)|Le paramètre de \_Macro\_value\_ a la valeur null|  
|[C28279](../code-quality/c28279.md)|Pour le symbole, un 'begin' a été trouvé sans 'end' correspondant|  
|[C28280](../code-quality/c28280.md)|Pour le symbole, un 'end' a été trouvé sans 'begin' correspondant|  
|[C28282](../code-quality/c28282.md)|Les chaînes de format doivent se trouver dans les conditions préalables|  
|[C28285](../code-quality/c28285.md)|Pour la fonction, une erreur de syntaxe dans le paramètre|  
|[C28286](../code-quality/c28286.md)|Pour la fonction, une erreur de syntax vers la fin|  
|[C28287](../code-quality/c28287.md)|Pour la fonction erreur dans l'annotation \_At\_\(\) \(nom de paramètre non reconnu\)|  
|[C28288](../code-quality/c28288.md)|Pour la fonction, erreur dans l'annotation \_At\_\(\) \(nom de paramètre non valide\)|  
|[C28289](../code-quality/c28289.md)|Pour la fonction : ReadableTo ou WritableTo n'a pas eu de spécification de limites en tant que paramètre|  
|[C28290](../code-quality/c28290.md)|L'annotation pour la fonction contient plus d'Externals que le nombre réel de paramètres|  
|[C28291](../code-quality/c28291.md)|post null\/notnull au niveau 0 deref n'a pas de sens pour la fonction.|  
|[C28300](../code-quality/c28300.md)|Opérandes d'expression de types incompatibles pour l'opérateur|  
|[C28301](../code-quality/c28301.md)|Aucune annotation pour la première déclaration de la fonction.|  
|[C28302](../code-quality/c28302.md)|Un opérateur supplémentaire \_Deref\_ a été trouvé sur l'annotation.|  
|[C28303](../code-quality/c28303.md)|Un opérateur ambigu \_Deref\_ a été trouvé sur l'annotation.|  
|[C28304](../code-quality/c28304.md)|Un opérateur \_Notref\_ placé de manière incorrecte a été trouvé appliqué au token.|  
|[C28305](../code-quality/c28305.md)|Une erreur a été découverte lors de l'analyse du token.|  
|[C28350](../code-quality/c28350.md)|L'annotation décrit une situation qui n'est pas applicable de manière conditionnelle.|  
|[C28351](../code-quality/c28351.md)|L'annotation décrit lorsqu'une valeur dynamique \(une variable\) ne peut pas être utilisée dans la condition.|