---
title: Ensemble de règles des règles recommandées mixtes
ms.date: 11/04/2016
description: En savoir plus sur l’ensemble de règles de règles recommandées mixtes dans Visual Studio. Consultez les descriptions des règles pour les projets C++ qui prennent en charge le Common Language Runtime.
ms.custom: SEO-VS-2020
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc30012dc025c5fc92f6d589c8e40740d689a86b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437068"
---
# <a name="mixed-recommended-rules-rule-set"></a>Ensemble de règles des règles recommandées mixtes

Les règles Microsoft Mixed Recommended se concentrent sur les problèmes les plus courants et critiques dans vos projets C++ qui prennent en charge le Common Language Runtime, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs de conception et logique importantes. Cet ensemble de règles comprend toutes les règles de l’ensemble de règles de [règles minimales mixtes](mixed-minimum-rules-rule-set.md) .

Incluez cet ensemble de règles dans n’importe quel ensemble de règles personnalisé que vous créez pour vos projets C++ qui prennent en charge le Common Language Runtime.

|Règle|Description|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Utilisation d'une mémoire non initialisée|
|[C6011](/cpp/code-quality/c6011)|Déréférencement du pointeur Null|
|[C6029](/cpp/code-quality/c6029)|Utilisation d'une valeur non vérifiée|
|[C6031](/cpp/code-quality/c6031)|Valeur de retour ignorée|
|[C6053](/cpp/code-quality/c6053)|Terminaison par zéro de l'appel|
|[C6054](/cpp/code-quality/c6054)|Arrêt de zéro manquant|
|[C6059](/cpp/code-quality/c6059)|Concaténation non valide|
|[C6063](/cpp/code-quality/c6063)|Argument de chaîne manquant pour le formatage de la fonction|
|[C6064](/cpp/code-quality/c6064)|Argument d’entier manquant pour le formatage de la fonction|
|[C6066](/cpp/code-quality/c6066)|Argument de pointeur manquant pour le formatage de la fonction|
|[C6067](/cpp/code-quality/c6067)|Argument de pointeur de chaîne manquant pour le formatage de la fonction|
|[C6101](/cpp/code-quality/c6101)|Retour d'une mémoire non initialisée|
|[C6200](/cpp/code-quality/c6200)|L'index dépasse la taille maximale autorisée par la mémoire tampon|
|[C6201](/cpp/code-quality/c6201)|L'index dépasse la taille maximale autorisée par la mémoire tampon allouée par la pile|
|[C6214](/cpp/code-quality/c6214)|Cast de HRESULT non valide en BOOL|
|[C6215](/cpp/code-quality/c6215)|Cast de BOOL non valide en HRESULT|
|[C6216](/cpp/code-quality/c6216)|Cast Compiler-Inserted non valide de BOOL en HRESULT|
|[C6217](/cpp/code-quality/c6217)|Test HRESULT non valide avec NOT|
|[C6220](/cpp/code-quality/c6220)|Valeur HRESULT non valide comcomparée à-1|
|[C6226](/cpp/code-quality/c6226)|Assignation HRESULT non valide à-1|
|[C6230](/cpp/code-quality/c6230)|Utilisation de HRESULT non valide en tant que valeur booléenne|
|[C6235](/cpp/code-quality/c6235)|Constante non nulle avec Logical-Or|
|[C6236](/cpp/code-quality/c6236)|Logical-Or avec constante non nulle|
|[C6237](/cpp/code-quality/c6237)|Zéro avec Logical-And perd les effets secondaires|
|[C6242](/cpp/code-quality/c6242)|Déroulement local forcé|
|[C6248](/cpp/code-quality/c6248)|Création d’une liste DACL de valeur null|
|[C6250](/cpp/code-quality/c6250)|Descripteurs d’adresses incommercialisés|
|[C6255](/cpp/code-quality/c6255)|Utilisation non protégée d’alloca|
|[C6258](/cpp/code-quality/c6258)|Utilisation du thread Terminate|
|[C6259](/cpp/code-quality/c6259)|Code mort dans Bitwise-Or commutateur limité|
|[C6260](/cpp/code-quality/c6260)|Utilisation de l’arithmétique d’octets|
|[C6262](/cpp/code-quality/c6262)|Utilisation excessive de la pile|
|[C6263](/cpp/code-quality/c6263)|Utilisation d’alloca dans une boucle|
|[C6268](/cpp/code-quality/c6268)|Parenthèses manquantes dans le cast|
|[C6269](/cpp/code-quality/c6269)|Déréférencement du pointeur ignoré|
|[C6270](/cpp/code-quality/c6270)|Argument float manquant pour le formatage de la fonction|
|[C6271](/cpp/code-quality/c6271)|Argument supplémentaire pour le formatage de la fonction|
|[C6272](/cpp/code-quality/c6272)|Argument non float pour le formatage de la fonction|
|[C6273](/cpp/code-quality/c6273)|Argument non entier pour la fonction Format|
|[C6274](/cpp/code-quality/c6274)|Argument autre qu’un caractère pour le formatage de la fonction|
|[C6276](/cpp/code-quality/c6276)|Cast de chaîne non valide|
|[C6277](/cpp/code-quality/c6277)|Appel CreateProcess non valide|
|[C6278](/cpp/code-quality/c6278)|Incompatibilité de Scalar-Delete Array-New|
|[C6279](/cpp/code-quality/c6279)|Incompatibilité de Array-Delete Scalar-New|
|[C6280](/cpp/code-quality/c6280)|Incompatibilité de Allocation-Deallocation de mémoire|
|[C6281](/cpp/code-quality/c6281)|Priorité de la relation au niveau du bit|
|[C6282](/cpp/code-quality/c6282)|L’affectation remplace le test|
|[C6283](/cpp/code-quality/c6283)|Incompatibilité de Scalar-Delete de Array-New primitive|
|[C6284](/cpp/code-quality/c6284)|Argument d’objet non valide pour le formatage de la fonction|
|[C6285](/cpp/code-quality/c6285)|Logical-Or de constantes|
|[C6286](/cpp/code-quality/c6286)|Logical-Or non nulle perdant des effets secondaires|
|[C6287](/cpp/code-quality/c6287)|Test redondant|
|[C6288](/cpp/code-quality/c6288)|L’inclusion mutuelle sur Logical-And est false|
|[C6289](/cpp/code-quality/c6289)|L’exclusion mutuelle sur Logical-Or est vraie|
|[C6290](/cpp/code-quality/c6290)|Priorité NOT logique et AND au niveau du bit|
|[C6291](/cpp/code-quality/c6291)|Priorité NOT logique et OR au niveau du bit|
|[C6292](/cpp/code-quality/c6292)|Le nombre maximal de boucles est de|
|[C6293](/cpp/code-quality/c6293)|Nombre de boucles à partir de la valeur minimale|
|[C6294](/cpp/code-quality/c6294)|Le corps de la boucle n’est jamais exécuté|
|[C6295](/cpp/code-quality/c6295)|Boucle infinie|
|[C6296](/cpp/code-quality/c6296)|Boucle exécutée une seule fois|
|[C6297](/cpp/code-quality/c6297)|Résultat de la conversion du décalage en taille supérieure|
|[C6299](/cpp/code-quality/c6299)|Comparaison de champ de binaire à booléen|
|[C6302](/cpp/code-quality/c6302)|Argument de chaîne de caractères non valide pour le formatage de la fonction|
|[C6303](/cpp/code-quality/c6303)|Argument de chaîne de caractères larges non valide pour le formatage de la fonction|
|[C6305](/cpp/code-quality/c6305)|Incompatibilité entre la taille et la quantité|
|[C6306](/cpp/code-quality/c6306)|Appel de fonction d’argument de variable non valide|
|[C6308](/cpp/code-quality/c6308)|Fuite de réallocation|
|[C6310](/cpp/code-quality/c6310)|Constante de filtre d’exception non conforme|
|[C6312](/cpp/code-quality/c6312)|L’exception continue la boucle d’exécution|
|[C6314](/cpp/code-quality/c6314)|Priorité de Bitwise-Or|
|[C6317](/cpp/code-quality/c6317)|Complément non|
|[C6318](/cpp/code-quality/c6318)|L’exception continue la recherche|
|[C6319](/cpp/code-quality/c6319)|Ignoré par la virgule|
|[C6324](/cpp/code-quality/c6324)|Copie de chaîne au lieu d’une comparaison de chaînes|
|[C6328](/cpp/code-quality/c6328)|Incompatibilité de type d’argument possible|
|[C6331](/cpp/code-quality/c6331)|Indicateurs non valides VirtualFree|
|[C6332](/cpp/code-quality/c6332)|Paramètre VirtualFree non valide|
|[C6333](/cpp/code-quality/c6333)|Taille VirtualFree non valide|
|[C6335](/cpp/code-quality/c6335)|Traitement des fuites de processus|
|[C6381](/cpp/code-quality/c6381)|Informations d’arrêt manquantes|
|[C6383](/cpp/code-quality/c6383)|Element-Count Byte-Count dépassement de mémoire tampon|
|[C6384](/cpp/code-quality/c6384)|Division taille du pointeur|
|[C6385](/cpp/code-quality/c6385)|Dépassement en lecture|
|[C6386](/cpp/code-quality/c6386)|Dépassement en écriture|
|[C6387](/cpp/code-quality/c6387)|Valeur de paramètre non valide|
|[C6388](/cpp/code-quality/c6388)|Valeur de paramètre non valide|
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
|[C6995](/cpp/code-quality/c6995)|Échec de l’enregistrement du fichier journal XML|
|[C26100](/cpp/code-quality/c26100)|Condition de concurrence|
|[C26101](/cpp/code-quality/c26101)|Échec de l’utilisation de l’opération verrouillée|
|[C26110](/cpp/code-quality/c26110)|Appelant qui ne détient pas de verrou|
|[C26111](/cpp/code-quality/c26111)|Échec de libération du verrou par l’appelant|
|[C26112](/cpp/code-quality/c26112)|L’appelant ne peut pas contenir de verrou|
|[C26115](/cpp/code-quality/c26115)|Échec de libération du verrou|
|[C26116](/cpp/code-quality/c26116)|Échec de l’acquisition ou du maintien du verrou|
|[C26117](/cpp/code-quality/c26117)|Libération du verrou inmaintenu|
|[C26140](/cpp/code-quality/c26140)|Erreur d’annotation SAL concurrentielle|
|[C28020](/cpp/code-quality/c28020)|L’expression n’est pas vraie pour cet appel|
|[C28021](/cpp/code-quality/c28021)|Le paramètre annoté doit être un pointeur|
|[C28022](/cpp/code-quality/c28022)|La ou les classes de fonction sur cette fonction ne correspondent pas à la ou les classes de fonction sur le typedef utilisé pour la définir.|
|[C28023](/cpp/code-quality/c28023)|La fonction affectée ou passée doit avoir une \_ \_ \_ annotation de classe de fonction pour au moins une des classes|
|[C28024](/cpp/code-quality/c28024)|Le pointeur de fonction assigné à est annoté avec la classe de fonction, qui n’est pas contenue dans la liste des classes de fonction.|
|[C28039](/cpp/code-quality/c28039)|Le type du paramètre réel doit correspondre exactement au type|
|[C28112](/cpp/code-quality/c28112)|Une variable qui est accessible via une fonction Interlocked doit toujours être accessible via une fonction verrouillée.|
|[C28113](/cpp/code-quality/c28113)|Accès à une variable locale via une fonction verrouillée|
|[C28125](/cpp/code-quality/c28125)|La fonction doit être appelée à partir d’un bloc try/except|
|[C28137](/cpp/code-quality/c28137)|L’argument de variable doit plutôt être une constante (littérale)|
|[C28138](/cpp/code-quality/c28138)|L’argument de constante doit plutôt être une variable|
|[C28159](/cpp/code-quality/c28159)|Utilisez une autre fonction à la place.|
|[C28160](/cpp/code-quality/c28160)|annotation d'erreur|
|[C28163](/cpp/code-quality/c28163)|La fonction ne doit jamais être appelée à partir d’un bloc try/except|
|[C28164](/cpp/code-quality/c28164)|L’argument est passé à une fonction qui attend un pointeur vers un objet (pas un pointeur vers un pointeur)|
|[C28182](/cpp/code-quality/c28182)|Déréférencement du pointeur NULL. Le pointeur contient la même valeur NULL qu'un autre pointeur.|
|[C28183](/cpp/code-quality/c28183)|L’argument peut être une valeur et est une copie de la valeur trouvée dans le pointeur|
|[C28193](/cpp/code-quality/c28193)|La variable contient une valeur qui doit être examinée.|
|[C28196](/cpp/code-quality/c28196)|L’exigence n’est pas satisfaite. (L’expression n’est pas évaluée à true.)|
|[C28202](/cpp/code-quality/c28202)|Référence non autorisée à un membre non statique|
|[C28203](/cpp/code-quality/c28203)|Référence ambiguë à un membre de classe.|
|[C28205](/cpp/code-quality/c28205)|\_Réussite \_ ou \_ \_ échec \_ utilisé dans un contexte non conforme|
|[C28206](/cpp/code-quality/c28206)|L’opérande de gauche pointe vers un struct, utiliser '->'|
|[C28207](/cpp/code-quality/c28207)|L’opérande de gauche est un struct, utiliser '.'|
|[C28209](/cpp/code-quality/c28209)|La déclaration pour le symbole a une déclaration en conflit|
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
|[C28244](/cpp/code-quality/c28244)|L’annotation pour la fonction a un paramètre ou une annotation externe non analysable|
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
|[C28306](/cpp/code-quality/c28306)|L’annotation sur le paramètre est obsolète|
|[C28307](/cpp/code-quality/c28307)|L’annotation sur le paramètre est obsolète|
|[C28350](/cpp/code-quality/c28350)|L'annotation décrit une situation qui n'est pas applicable de manière conditionnelle.|
|[C28351](/cpp/code-quality/c28351)|L'annotation décrit l'emplacement auquel une valeur dynamique (une variable) ne peut pas être utilisée dans la condition.|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1009](../code-quality/ca1009.md)|Déclarer les gestionnaires d'événements correctement|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Les méthodes d'interface doivent pouvoir être appelées par les types enfants|
|[CA1049](../code-quality/ca1049.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Ne pas masquer les méthodes de la classe de base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implémenter IDisposable correctement|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Ne pas lever d'exceptions dans les emplacements inattendus|
|[CA1301](../code-quality/ca1301.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400.md)|Des points d'entrée P/Invoke doivent exister|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Les P/Invoke ne doivent pas être visibles|
|[CA1403](../code-quality/ca1403.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Les types de base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410.md)|Les méthodes d'inscription COM doivent être mises en correspondance|
|[CA1415](../code-quality/ca1415.md)|Déclarer correctement les méthodes P/Invoke|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Supprimez les finaliseurs vides|
|[CA1900](../code-quality/ca1900.md)|Les champs de type valeur doivent être portables|
|[CA1901](../code-quality/ca1901.md)|Les déclarations P/Invoke doivent être portables|
|[CA2002](/dotnet/fundamentals/code-analysis/quality-rules/ca2002)|Ne définissez pas un verrou sur des objets à identité faible|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Vérifier si les requêtes SQL présentent des failles de sécurité|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2111](../code-quality/ca2111.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112.md)|Les types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114.md)|La sécurité de la méthode doit être un sur-ensemble du type|
|[CA2116](../code-quality/ca2116.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2122](../code-quality/ca2122.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123.md)|Les demandes de liaison de substitution doivent être identiques au composant de base|
|[CA2124](../code-quality/ca2124.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|
|[CA2126](../code-quality/ca2126.md)|Les demandes de liaison de type exigent des demandes d'héritage|
|[CA2131](../code-quality/ca2131.md)|Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types|
|[CA2132](../code-quality/ca2132.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134.md)|La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base|
|[CA2137](../code-quality/ca2137.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|
|[CA2147](../code-quality/ca2147.md)|Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité|
|[CA2149](../code-quality/ca2149.md)|Les méthodes transparentes ne doivent pas appeler du code natif|
|[CA2200](/dotnet/fundamentals/code-analysis/quality-rules/ca2200)|Levez à nouveau une exception pour conserver les détails de la pile|
|[CA2202](../code-quality/ca2202.md)|Ne pas supprimer d'objets plusieurs fois|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Initialisez les champs statiques des types valeur en ligne|
|[CA2212](../code-quality/ca2212.md)|Ne marquez pas les composants pris en charge avec webMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Les champs pouvant être supprimés doivent l’être|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|N'appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Les types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2220](../code-quality/ca2220.md)|Les finaliseurs doivent appeler le finaliseur de leur classe de base|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implémentez des constructeurs de sérialisation|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marquez les points d'entrée Windows Forms avec STAThread|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Marquez tous les champs non sérialisés|
|[CA2236](../code-quality/ca2236.md)|Appelez les méthodes de la classe de base sur les types ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implémentez les méthodes de sérialisation comme il se doit|
|[CA2240](../code-quality/ca2240.md)|Implémentez ISerializable comme il se doit|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Indiquer le nombre correct d'arguments dans les méthodes de mise en forme|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Effectuez correctement des tests NaN|