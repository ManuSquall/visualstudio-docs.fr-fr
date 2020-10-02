---
title: Ensemble de règles des règles minimales mixtes
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bc8df61c-19af-40ab-a871-315807e5f4bf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edacd898cc1deb0382dd8e8b4b048af895c3b579
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658462"
---
# <a name="mixed-minimum-rules-rule-set"></a>Ensemble de règles des règles minimales mixtes

Les règles minimales de Microsoft se concentrent sur les problèmes les plus critiques des projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles et les blocages d’application.

Incluez cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.

|Règle|Description|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Utilisation d'une mémoire non initialisée|
|[C6011](/cpp/code-quality/c6011)|Déréférencement du pointeur Null|
|[C6029](/cpp/code-quality/c6029)|Utilisation d'une valeur non vérifiée|
|[C6053](/cpp/code-quality/c6053)|Terminaison par zéro de l'appel|
|[C6059](/cpp/code-quality/c6059)|Concaténation non valide|
|[C6063](/cpp/code-quality/c6063)|Argument de chaîne manquant pour le formatage de la fonction|
|[C6064](/cpp/code-quality/c6064)|Argument d’entier manquant pour le formatage de la fonction|
|[C6066](/cpp/code-quality/c6066)|Argument de pointeur manquant pour le formatage de la fonction|
|[C6067](/cpp/code-quality/c6067)|Argument de pointeur de chaîne manquant pour le formatage de la fonction|
|[C6101](/cpp/code-quality/c6101)|Retour d'une mémoire non initialisée|
|[C6200](/cpp/code-quality/c6200)|L'index dépasse la taille maximale autorisée par la mémoire tampon|
|[C6201](/cpp/code-quality/c6201)|L'index dépasse la taille maximale autorisée par la mémoire tampon allouée par la pile|
|[C6270](/cpp/code-quality/c6270)|Argument float manquant pour le formatage de la fonction|
|[C6271](/cpp/code-quality/c6271)|Argument supplémentaire pour le formatage de la fonction|
|[C6272](/cpp/code-quality/c6272)|Argument non float pour le formatage de la fonction|
|[C6273](/cpp/code-quality/c6273)|Argument non entier pour la fonction Format|
|[C6274](/cpp/code-quality/c6274)|Argument autre qu’un caractère pour le formatage de la fonction|
|[C6276](/cpp/code-quality/c6276)|Cast de chaîne non valide|
|[C6277](/cpp/code-quality/c6277)|Appel CreateProcess non valide|
|[C6284](/cpp/code-quality/c6284)|Argument d’objet non valide pour le formatage de la fonction|
|[C6290](/cpp/code-quality/c6290)|Priorité NOT logique et AND au niveau du bit|
|[C6291](/cpp/code-quality/c6291)|Priorité NOT logique et OR au niveau du bit|
|[C6302](/cpp/code-quality/c6302)|Argument de chaîne de caractères non valide pour le formatage de la fonction|
|[C6303](/cpp/code-quality/c6303)|Argument de chaîne de caractères larges non valide pour le formatage de la fonction|
|[C6305](/cpp/code-quality/c6305)|Incompatibilité entre la taille et la quantité|
|[C6306](/cpp/code-quality/c6306)|Appel de fonction d’argument de variable non valide|
|[C6328](/cpp/code-quality/c6328)|Incompatibilité de type d’argument possible|
|[C6385](/cpp/code-quality/c6385)|Dépassement en lecture|
|[C6386](/cpp/code-quality/c6386)|Dépassement en écriture|
|[C6387](/cpp/code-quality/c6387)|Valeur de paramètre non valide|
|[C6500](/cpp/code-quality/c6500)|Propriété d'attribut non valide|
|[C6501](/cpp/code-quality/c6501)|Valeurs de propriété d'attribut en conflit|
|[C6503](/cpp/code-quality/c6503)|Les références ne peuvent pas être Null|
|[C6504](/cpp/code-quality/c6504)|Null sur élément non pointeur|
|[C6505](/cpp/code-quality/c6505)|MustCheck sur Void|
|[C6506](/cpp/code-quality/c6506)|Taille de mémoire tampon sur élément non pointeur ou tableau|
|[C6508](/cpp/code-quality/c6508)|Accès en écriture sur constante|
|[C6509](/cpp/code-quality/c6509)|Retour utilisé sur condition préalable|
|[C6510](/cpp/code-quality/c6510)|Terminaison par Null sur élément non pointeur|
|[C6511](/cpp/code-quality/c6511)|MustCheck doit avoir la valeur Yes ou No|
|[C6513](/cpp/code-quality/c6513)|Taille d'élément sans taille de mémoire tampon|
|[C6514](/cpp/code-quality/c6514)|Taille de mémoire tampon dépasse la taille du tableau|
|[C6515](/cpp/code-quality/c6515)|Taille de la mémoire tampon sur élément non pointeur|
|[C6516](/cpp/code-quality/c6516)|Attribut sans propriété|
|[C6517](/cpp/code-quality/c6517)|Taille valide dans mémoire tampon non lisible|
|[C6518](/cpp/code-quality/c6518)|Taille accessible en écriture dans mémoire tampon non accessible en écriture|
|[C6522](/cpp/code-quality/c6522)|Type de chaîne de taille non valide|
|[C6525](/cpp/code-quality/c6525)|Chaîne de taille non valide. Emplacement inaccessible|
|[C6527](/cpp/code-quality/c6527)|Annotation non valide : la propriété NeedsRelease ne doit pas être utilisée sur des valeurs de type void|
|[C6530](/cpp/code-quality/c6530)|Style de chaîne de format non reconnu|
|[C6540](/cpp/code-quality/c6540)|L'utilisation des annotations d'attribut sur cette fonction rendra non valides toutes ses annotations __declspec existantes|
|[C6551](/cpp/code-quality/c6551)|Spécification de taille non valide : expression impossible à analyser|
|[C6552](/cpp/code-quality/c6552)|Deref= ou Noref= non valide : expression impossible à analyser|
|[C6701](/cpp/code-quality/c6701)|La valeur n'est pas une valeur Yes/No/Maybe valide|
|[C6702](/cpp/code-quality/c6702)|La valeur n'est pas une valeur de chaîne|
|[C6703](/cpp/code-quality/c6703)|La valeur n'est pas un nombre|
|[C6704](/cpp/code-quality/c6704)|Erreur d'expression de l'annotation inattendue|
|[C6705](/cpp/code-quality/c6705)|Le nombre d’arguments attendu pour l’annotation ne correspond pas au nombre réel d’arguments pour l’annotation|
|[C6706](/cpp/code-quality/c6706)|Erreur d'annotation inattendue pour l'annotation|
|[C28021](/cpp/code-quality/c28021)|Le paramètre annoté doit être un pointeur|
|[C28182](/cpp/code-quality/c28182)|Déréférencement du pointeur NULL. Le pointeur contient la même valeur NULL qu'un autre pointeur.|
|[C28202](/cpp/code-quality/c28202)|Référence non autorisée à un membre non statique|
|[C28203](/cpp/code-quality/c28203)|Référence ambiguë à un membre de classe.|
|[C28205](/cpp/code-quality/c28205)|\_Réussite \_ ou \_ \_ échec \_ utilisé dans un contexte non conforme|
|[C28206](/cpp/code-quality/c28206)|L’opérande de gauche pointe vers un struct, utiliser '->'|
|[C28207](/cpp/code-quality/c28207)|L’opérande de gauche est un struct, utiliser '.'|
|[C28210](/cpp/code-quality/c28210)|Les annotations pour le contexte __on_failure ne doivent pas se trouver dans un contexte préalable explicite|
|[C28211](/cpp/code-quality/c28211)|Nom du contexte statique attendu pour SAL_context|
|[C28212](/cpp/code-quality/c28212)|Expression de pointeur attendue pour l'annotation|
|[C28213](/cpp/code-quality/c28213)|L' \_ \_ annotation use decl \_ Annotations \_ doit être utilisée pour référencer, sans modification, une déclaration antérieure.|
|[C28214](/cpp/code-quality/c28214)|Les noms des paramètres d'attribut doivent être p1...p9|
|[C28215](/cpp/code-quality/c28215)|Le typefix ne peut pas être appliqué à un paramètre qui contient déjà un typefix|
|[C28216](/cpp/code-quality/c28216)|L'annotation checkReturn ne s'applique qu'aux post-conditions pour le paramètre de fonction spécifique.|
|[C28217](/cpp/code-quality/c28217)|Pour la fonction, le nombre de paramètres de l'annotation ne correspond pas au nombre trouvé dans le fichier|
|[C28218](/cpp/code-quality/c28218)|Pour le paramètre de fonction, le paramètre de l’annotation ne correspond pas à celui trouvé dans le fichier|
|[C28219](/cpp/code-quality/c28219)|Membre de l'énumération attendu pour une annotation, le paramètre dans l'annotation|
|[C28220](/cpp/code-quality/c28220)|Expression d'entier attendue pour une annotation, le paramètre dans l'annotation|
|[C28221](/cpp/code-quality/c28221)|Expression de chaîne attendue pour le paramètre dans l'annotation|
|[C28222](/cpp/code-quality/c28222)|__yes, \__no ou \__maybe attendus pour l’annotation|
|[C28223](/cpp/code-quality/c28223)|Jeton/identificateur introuvable pour l'annotation, paramètre|
|[C28224](/cpp/code-quality/c28224)|L'annotation requiert des paramètres|
|[C28225](/cpp/code-quality/c28225)|Nombre correct de paramètres requis introuvable dans l'annotation|
|[C28226](/cpp/code-quality/c28226)|L'annotation ne peut pas être également un PrimOp (dans la déclaration actuelle)|
|[C28227](/cpp/code-quality/c28227)|L'annotation ne peut pas être également un PrimOp (voir la déclaration antérieure)|
|[C28228](/cpp/code-quality/c28228)|Paramètre d'annotation : impossible d'utiliser ce type dans les annotations|
|[C28229](/cpp/code-quality/c28229)|L'annotation ne prend pas en charge les paramètres|
|[C28230](/cpp/code-quality/c28230)|Le type de paramètre ne contient pas de membre.|
|[C28231](/cpp/code-quality/c28231)|L'annotation n'est valide que sur un tableau|
|[C28232](/cpp/code-quality/c28232)|pre, post, ou deref ne sont appliqués à aucune annotation|
|[C28233](/cpp/code-quality/c28233)|pre, post ou deref sont appliqués à un bloc|
|[C28234](/cpp/code-quality/c28234)|l'expression __at ne s'applique pas à la fonction actuelle|
|[C28235](/cpp/code-quality/c28235)|La fonction ne peut pas constituer à elle seule une annotation|
|[C28236](/cpp/code-quality/c28236)|L'annotation ne peut pas être utilisée dans une expression|
|[C28237](/cpp/code-quality/c28237)|L'annotation sur le paramètre n'est plus prise en charge|
|[C28238](/cpp/code-quality/c28238)|Plusieurs value, stringValue et longValue sont définies dans l'annotation sur le paramètre. Utiliser paramn=xxx|
|[C28239](/cpp/code-quality/c28239)|value, stringValue ou longValue, et paramn=xxx sont définis en même temps dans l'annotation sur le paramètre. Utiliser uniquement paramn=xxx|
|[C28240](/cpp/code-quality/c28240)|L'annotation sur le paramètre possède un param2, mais pas de param1|
|[C28241](/cpp/code-quality/c28241)|L'annotation pour la fonction sur le paramètre n'est pas reconnue|
|[C28243](/cpp/code-quality/c28243)|L’annotation pour la fonction sur le paramètre nécessite plus de déréférencements que le type réel annoté ne le permet.|
|[C28245](/cpp/code-quality/c28245)|L’annotation pour la fonction annote ’this’ sur une fonction non membre|
|[C28246](/cpp/code-quality/c28246)|L'annotation du paramètre ne correspond pas au type du paramètre|
|[C28250](/cpp/code-quality/c28250)|Annotation incohérente pour une fonction : l'instance précédente contient une erreur.|
|[C28251](/cpp/code-quality/c28251)|Annotation incohérente pour une fonction : cette instance contient une erreur.|
|[C28252](/cpp/code-quality/c28252)|Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.|
|[C28253](/cpp/code-quality/c28253)|Annotation incohérente pour une fonction : le paramètre contient d'autres annotations sur cette instance.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<>() n'est pas pris en charge dans les annotations|
|[C28262](/cpp/code-quality/c28262)|Une erreur de syntaxe dans l'annotation a été trouvée dans la fonction, pour l'annotation|
|[C28263](/cpp/code-quality/c28263)|Une erreur de syntaxe dans une annotation conditionnelle a été trouvée pour l'annotation intrinsèque|
|[C28267](/cpp/code-quality/c28267)|Une erreur de syntaxe dans les annotations a été trouvée pour l'annotation dans la fonction.|
|[C28272](/cpp/code-quality/c28272)|L'annotation pour la fonction, paramètre pendant la vérification est incohérente avec la déclaration de fonction|
|[C28273](/cpp/code-quality/c28273)|Pour la fonction, les indices sont incohérents avec la déclaration de fonction|
|[C28275](/cpp/code-quality/c28275)|Le paramètre de \_ la \_ valeur de macro \_ est null|
|[C28279](/cpp/code-quality/c28279)|Pour le symbole, un 'begin' a été trouvé sans le 'end' correspondant|
|[C28280](/cpp/code-quality/c28280)|Pour le symbole, un 'end' a été trouvé sans le 'begin' correspondant|
|[C28282](/cpp/code-quality/c28282)|Les chaînes de format doivent être comprises dans des conditions préalables|
|[C28285](/cpp/code-quality/c28285)|Pour la fonction, erreur de syntaxe dans le paramètre|
|[C28286](/cpp/code-quality/c28286)|Pour la fonction, erreur de syntaxe près de la fin|
|[C28287](/cpp/code-quality/c28287)|Pour la fonction, erreur de syntaxe dans l’annotation \_At\_() (nom de paramètre non reconnu)|
|[C28288](/cpp/code-quality/c28288)|Pour la fonction, erreur de syntaxe dans l’annotation \_At\_() (nom de paramètre non valide)|
|[C28289](/cpp/code-quality/c28289)|Pour la fonction : ReadableTo ou WritableTo n'a pas eu de spécification de limites en tant que paramètre|
|[C28290](/cpp/code-quality/c28290)|l'annotation pour la fonction contient plus d'Externals que le nombre réel de paramètres|
|[C28291](/cpp/code-quality/c28291)|post null/notnull au niveau 0 deref n'a pas de sens pour la fonction.|
|[C28300](/cpp/code-quality/c28300)|Opérandes d’expression de types incompatibles pour l’opérateur|
|[C28301](/cpp/code-quality/c28301)|Aucune annotation pour la première déclaration de la fonction.|
|[C28302](/cpp/code-quality/c28302)|Un opérateur \_Deref\_ en trop a été trouvé dans une annotation.|
|[C28303](/cpp/code-quality/c28303)|Un opérateur ambigu \_Deref\_ a été trouvé dans une annotation.|
|[C28304](/cpp/code-quality/c28304)|Un opérateur \_Notref\_ placé de manière incorrecte et appliqué à un jeton a été trouvé.|
|[C28305](/cpp/code-quality/c28305)|Une erreur a été détectée pendant l'analyse d'un jeton.|
|[C28350](/cpp/code-quality/c28350)|L'annotation décrit une situation qui n'est pas applicable de manière conditionnelle.|
|[C28351](/cpp/code-quality/c28351)|L'annotation décrit l'emplacement auquel une valeur dynamique (une variable) ne peut pas être utilisée dans la condition.|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Supprimez les finaliseurs vides|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Les champs pouvant être supprimés doivent l’être|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|