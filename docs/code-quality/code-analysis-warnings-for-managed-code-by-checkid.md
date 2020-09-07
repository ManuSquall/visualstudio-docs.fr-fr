---
title: Vue d’ensemble des règles de la qualité du code
ms.date: 08/27/2020
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1005
- CA1008
- CA1010
- CA1012
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1021
- CA1024
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1036
- CA1040
- CA1041
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1058
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1066
- CA1067
- CA1068
- CA1069
- CA1070
- CA1200
- CA1303
- CA1304
- CA1305
- CA1307
- CA1308
- CA1309
- CA1310
- CA1401
- CA1417
- CA1501
- CA1502
- CA1505
- CA1506
- CA1507
- CA1508
- CA1509
- CA1700
- CA1707
- CA1708
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- CA1716
- CA1717
- CA1720
- CA1721
- CA1724
- CA1725
- CA1801
- CA1802
- CA1805
- CA1806
- CA1810
- CA1812
- CA1813
- CA1814
- CA1815
- CA1816
- CA1819
- CA1820
- CA1821
- CA1822
- CA1823
- CA1824
- CA1825
- CA1826
- CA1827
- CA1828
- CA1829
- CA1830
- CA1831
- CA1832
- CA1833
- CA1834
- CA1835
- CA1836
- CA1837
- CA1838
- CA2000
- CA2002
- CA2007
- CA2008
- CA2009
- CA2011
- CA2012
- CA2013
- CA2014
- CA2015
- CA2016
- CA2100
- CA2101
- CA2109
- CA2119
- CA2153
- CA2200
- CA2201
- CA2207
- CA2208
- CA2211
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2219
- CA2225
- CA2226
- CA2227
- CA2229
- CA2231
- CA2234
- CA2235
- CA2237
- CA2241
- CA2242
- CA2243
- CA2245
- CA2246
- CA2247
- CA2248
- CA2249
- CA2300
- CA2301
- CA2302
- CA2305
- CA2310
- CA2311
- CA2312
- CA2315
- CA2321
- CA2322
- CA2326
- CA2327
- CA2328
- CA2329
- CA2330
- CA2350
- CA2351
- CA2352
- CA2353
- CA2354
- CA2355
- CA2356
- CA2361
- CA2362
- CA3001
- CA3002
- CA3003
- CA3004
- CA3005
- CA3006
- CA3007
- CA3008
- CA3009
- CA3010
- CA3011
- CA3012
- CA3061
- CA3075
- CA3076
- CA3077
- CA5347
- CA5350
- CA5351
- CA5359
- CA5360
- CA5361
- CA5362
- CA5363
- CA5364
- CA5365
- CA5366
- CA5367
- CA5368
- CA5369
- CA5370
- CA5371
- CA5372
- CA5373
- CA5374
- CA5375
- CA5376
- CA5377
- CA5378
- CA5379
- CA5380
- CA5381
- CA5382
- CA5383
- CA5384
- CA5385
- CA5386
- CA5387
- CA5388
- CA5389
- CA5390
- CA5391
- CA5392
- CA5393
- CA5394
- CA5395
- CA5397
- CA5398
- CA5399
- CA5400
- CA5401
- CA5402
- CA5403
- IL3000
- IL3001
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e4b728fab6eb47501bb0d1bb752d22c0c29a8b4
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509443"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Avertissements d’analyse du code pour le code managé par CheckId

Le tableau suivant répertorie les avertissements d'analyse du code pour le code managé par l'identificateur CheckId de l'avertissement.

| CheckId | Avertissement | Description |
|---------| - | - |
| CA1000 | [CA1000 : Ne pas déclarer de membres statiques sur les types génériques](../code-quality/ca1000.md) | Lorsqu'un membre statique d'un type générique est appelé, l'argument de type doit être spécifié pour le type. Lorsqu'un membre d'instance générique qui ne prend pas en charge l'inférence est appelé, l'argument de type doit être spécifié pour le membre. Dans ces deux cas, la syntaxe permettant de spécifier l'argument de type est différente et peut être facilement confondue. |
| CA1001 | [CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables](../code-quality/ca1001.md) | Une classe déclare et implémente un champ d'instance qui est un type System.IDisposable, et elle n'implémente pas IDisposable. Une classe qui déclare un champ IDisposable possède indirectement une ressource non managée et doit implémenter l'interface IDisposable. |
| CA1002 | [CA1002 : Ne pas exposer de listes génériques](../code-quality/ca1002.md) | System. Collections. Generic. List< (of \<(T> ) >) est une collection générique conçue pour les performances, et non pour l’héritage. Par conséquent, la liste ne contient aucun membre virtuel. Les collections génériques qui sont conçues pour l’héritage doivent être exposées à la place. |
| CA1003 | [CA1003 : Utiliser les instances du gestionnaire d'événements génériques](../code-quality/ca1003.md) |Un type contient un délégué qui retourne void, dont la signature contient deux paramètres (le premier est un objet et le second est un type pouvant être assigné à EventArgs), et l'assembly conteneur cible Microsoft .NET Framework 2.0. |
| CA1005 | [CA1005 : Éviter les paramètres excessifs sur les types génériques](../code-quality/ca1005.md) | Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type. Elle est généralement évidente avec un paramètre de type, comme dans la liste \<T> , et dans certains cas, il existe deux paramètres de type, comme dans Dictionary \<TKey, TValue> . Cependant, s’il existe plus de deux paramètres de type, la difficulté devient trop grande pour la plupart des utilisateurs. |
| CA1008 | [CA1008 : Les enums doivent avoir la valeur zéro](../code-quality/ca1008.md) | La valeur par défaut d'une énumération non initialisée, comme d'autres types valeur, est zéro. Une énumération attribuée sans indicateur doit définir un membre de valeur zéro afin que la valeur par défaut soit une valeur valide de l'énumération. Si une énumération à laquelle l'attribut FlagsAttribute est appliqué définit un membre de valeur zéro, son nom doit être "None" pour indiquer qu'aucune valeur n'a été définie dans l'énumération. |
| CA1010 | [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010.md) | Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. La collection peut être ensuite utilisée pour remplir des types de collection génériques. |
| CA1012 | [CA1012 : Les types abstract ne doivent pas avoir de constructeurs](../code-quality/ca1012.md) | Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés. Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte. |
| CA1014 | [CA1014 : Marquer les assemblys avec CLSCompliantAttribute](../code-quality/ca1014.md) | La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Un design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>. Si cet attribut n'est pas présent sur un assembly, l'assembly n'est pas conforme. |
| CA1016 | [CA1016 : Marquer les assemblys avec AssemblyVersionAttribute](../code-quality/ca1016.md) | .NET utilise le numéro de version pour identifier de manière unique un assembly et pour établir une liaison aux types dans des assemblys avec nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites. |
| CA1017 | [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017.md) |ComVisibleAttribute détermine comment les clients COM accèdent à du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. La visibilité COM peut être définie pour l'assembly en entier, puis être substituée pour des types et des membres de type individuels. Si cet attribut n'est pas présent, les clients COM peuvent voir le contenu de l'assembly. |
| CA1018 | [CA1018 : Marquer les attributs avec AttributeUsageAttribute](../code-quality/ca1018.md) | Lorsque vous définissez un attribut personnalisé, marquez-le à l'aide d'AttributeUsageAttribute pour indiquer où l'attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. |
| CA1019 | [CA1019 : Définir des accesseurs pour les arguments d'attribut](../code-quality/ca1019.md) | Les attributs peuvent définir des arguments obligatoires qui doivent être spécifiés lorsque vous appliquez l’attribut à une cible. Ceux-ci sont également appelés arguments positionnels parce qu’ils sont fournis aux constructeurs d’attributs en tant que paramètres positionnels. Pour chaque argument obligatoire, l'attribut doit également fournir une propriété en lecture seule correspondante afin que la valeur de l'argument puisse être récupérée au moment de l'exécution. Les attributs peuvent également définir des arguments facultatifs, qui sont également appelés arguments nommés. Ces arguments sont fournis aux constructeurs d’attributs par noms et doivent disposer d’une propriété en lecture/écriture correspondante. |
| CA1021 | [CA1021 : Éviter les paramètres out](../code-quality/ca1021.md) | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Par ailleurs, la différence entre les paramètres out et ref est généralement peu comprise. |
| CA1024 | [CA1024 : Utiliser les propriétés lorsque cela est approprié](../code-quality/ca1024.md) | Le nom d'une méthode publique ou protégée commence par « Get », n'accepte aucun paramètre et retourne une valeur qui n'est pas un tableau. La méthode est susceptible de devenir une propriété. |
| CA1027 |[CA1027 : Marquer les enums avec FlagsAttribute](../code-quality/ca1027.md) | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Appliquez FlagsAttribute à une énumération lorsque ses constantes nommées peuvent être combinées de manière pertinente. |
| CA1028 | [CA1028 : Enum Storage doit être Int32](../code-quality/ca1028.md) | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le type de données System.Int32 est utilisé pour stocker la valeur de constante. Bien que vous puissiez modifier ce type sous-jacent, ce n'est ni obligatoire, ni recommandé dans la plupart des scénarios. |
| CA1030 | [CA1030 : Utiliser des événements lorsque cela est approprié](../code-quality/ca1030.md) |Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Si une méthode est appelée en réponse à une modification d'état clairement définie, la méthode doit être appelée par un gestionnaire d'événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode. |
| CA1031 | [CA1031 : Ne pas intercepter des types d'exception générale](../code-quality/ca1031.md) | Les exceptions générales ne doivent pas être interceptées. Interceptez une exception plus spécifique ou levez à nouveau l'exception générale en tant que dernière instruction dans le bloc catch. |
| CA1032 |[CA1032 : Implémenter des constructeurs d'exception standard](../code-quality/ca1032.md) | Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. |
| CA1033 | [CA1033 : Les méthodes d'interface doivent pouvoir être appelées par les types enfants](../code-quality/ca1033.md) | Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom. |
| CA1034 | [CA1034 : Les types imbriqués ne doivent pas être visibles](../code-quality/ca1034.md) | Un type imbriqué représente un type déclaré dans la portée d'un autre type. Les types imbriqués sont utiles pour encapsuler les détails de l'implémentation privée du type conteneur. Utilisés à cette fin, les types imbriqués ne doivent pas être visibles de l'extérieur. |
| CA1036 | [CA1036 : Substituer les méthodes sur les types Comparable](../code-quality/ca1036.md) |Un type public ou protégé implémente l'interface System.IComparable. Il ne substitue pas Object.Equals, ni ne surcharge l'opérateur égal à, différent de, inférieur à ou supérieur à propre au langage. |
| CA1040 |[CA1040 : Éviter les interfaces vides](../code-quality/ca1040.md) | Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit aucun membre ; par conséquent, elle ne définit aucun contrat pouvant être implémenté. |
| CA1041 | [CA1041 : Fournir un message ObsoleteAttribute](../code-quality/ca1041.md) | Un type ou un membre est marqué avec un attribut System.ObsoleteAttribute dont la propriété ObsoleteAttribute.Message n'est pas spécifiée. Lorsqu'un type ou membre marqué avec ObsoleteAttribute est compilé, la propriété Message de l'attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. |
| CA1043 | [CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs](../code-quality/ca1043.md) | Les indexeurs (c'est-à-dire les propriétés indexées) doivent utiliser des types intégral ou chaîne pour l'index. Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d'utilisation de la bibliothèque. L'utilisation du type Object doit se restreindre aux cas où le type intégral ou de chaîne spécifique ne peut pas être spécifié au moment du design. |
| CA1044 | [CA1044 : Les propriétés ne doivent pas être en écriture seule](../code-quality/ca1044.md) | Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. Le fait de permettre à un utilisateur de définir une valeur et l'empêcher ensuite de la consulter n'offre aucune garantie de sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité. |
| CA1045 |[CA1045 : Ne pas passer de types par référence](../code-quality/ca1045.md) | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Les architectes de bibliothèque qui sont en train de concevoir pour un public général ne doivent pas s’attendre à ce que les utilisateurs maîtrisent le travail avec les `out` `ref` paramètres ou. |
| CA1046 | [CA1046 : Ne pas surcharger l'opérateur égal à sur les types référence](../code-quality/ca1046.md) | Pour les types référence, l'implémentation par défaut de l'opérateur d'égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet. |
| CA1047 |[CA1047 : Ne pas déclarer les membres protégés dans les types sealed](../code-quality/ca1047.md) | Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, les types sealed ne peuvent pas être hérités, ce qui signifie que les méthodes protégées sur les types sealed ne peuvent pas être appelées. |
| CA1050 | [CA1050 : Déclarer les types dans des espaces de noms](../code-quality/ca1050.md) | Les types sont déclarés au sein d'espaces de noms pour empêcher des collisions de dénomination, ainsi qu'en guise que méthode d'organisation de types connexes au sein d'une hiérarchie d'objets. |
| CA1051 | [CA1051 : Ne pas déclarer de champs d'instances visibles](../code-quality/ca1051.md) | Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent être privés ou internes, et doivent être exposés au moyen de propriétés. |
| CA1052 | [CA1052 : Les types de conteneurs statiques doivent être sealed](../code-quality/ca1052.md) | Un type public ou protégé contient uniquement des membres statiques et n'est pas déclaré avec le modificateur sealed (Référence C#) (NotInheritable). Un type qui n'est pas destiné à être hérité doit être marqué avec le modificateur sealed pour empêcher son utilisation en tant que type de base. |
| CA1053 |[CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053.md) | Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé. Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type. La surcharge de chaîne doit appeler la surcharge d'URI (Uniform Resource Identifier) à l'aide de l'argument de chaîne pour des raisons de sécurité. |
| CA1054 | [CA1054 : Les paramètres URI ne doivent pas être des chaînes](../code-quality/ca1054.md) | Si une méthode accepte une représentation sous forme de chaîne d'un URI, une surcharge correspondante qui accepte une instance de la classe URI doit être fournie ; elle-même fournit ces services de manière sûre et sécurisée. |
| CA1055 | [CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes](../code-quality/ca1055.md) | Cette règle considère que la méthode retourne un URI. Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1056 | [CA1056 : Les propriétés URI ne doivent pas être des chaînes](../code-quality/ca1056.md) | Cette règle considère que la propriété représente un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1058 | [CA1058 : Les types ne doivent pas étendre certains types de base](../code-quality/ca1058.md) | Un type visible de l'extérieur étend certains types de base. Utilisez l'une des solutions de remplacement. |
| CA1060 | [CA1060 : déplacer les P/Invoke vers une classe NativeMethods](../code-quality/ca1060.md) | Les méthodes d'appel de code non managé, telles que celles qui sont marquées avec l'attribut System.Runtime.InteropServices.DllImportAttribute, ou les méthodes définies à l'aide du mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], accèdent à du code non managé. Ces méthodes doivent être de la classe NativeMethods, SafeNativeMethods ou UnsafeNativeMethods. |
| CA1061 |[CA1061 : Ne pas masquer les méthodes de la classe de base](../code-quality/ca1061.md) | Une méthode dans un type de base est masquée par une méthode portant le même nom dans un type dérivé, lorsque la signature de paramètre de la méthode dérivée diffère uniquement par les types qui sont dérivés plus faiblement que les types correspondants dans la signature de paramètre de la méthode de base. |
| CA1062 | [CA1062 : Valider les arguments de méthodes publiques](../code-quality/ca1062.md) | Tous les arguments de référence passés aux méthodes visibles de l'extérieur doivent être vérifiés pour voir s'ils ont la valeur null. |
| CA1063 | [CA1063 : Implémenter IDisposable correctement](../code-quality/ca1063.md) | Tous les types IDisposable doivent implémenter le modèle Dispose correctement. |
| CA1064 | [CA1064 : Les exceptions doivent être publiques](../code-quality/ca1064.md) | Une exception interne est uniquement visible à l'intérieur de sa propre portée interne. Lorsque l'exception se situe en dehors de la portée interne, seule l'exception de base peut être utilisée pour intercepter l'exception. Si l’exception interne est héritée de <xref:System.Exception> , <xref:System.SystemException> ou <xref:System.ApplicationException> , le code externe ne disposera pas d’informations suffisantes pour savoir ce qu’il faut faire avec l’exception. |
| CA1065 | [CA1065 : Ne pas lever d'exceptions dans les emplacements inattendus](../code-quality/ca1065.md) | Une méthode dont l'objet n'est pas de lever des exceptions lève une exception. |
| Ca1066 | [CA1066 : Implémenter IEquatable au moment de remplacer Equals](../code-quality/ca1066.md) | Un type valeur substitue la <xref:System.Object.Equals%2A> méthode, mais n’implémente pas <xref:System.IEquatable%601> . |
| Ca1067 | [CA1067: Remplacer Equals lors de l’implémentation d’IEquatable](../code-quality/ca1067.md) | Un type implémente <xref:System.IEquatable%601> , mais ne se substitue pas à la <xref:System.Object.Equals%2A> méthode. |
| Ca1068 | [CA1068 : Les paramètres CancellationToken doivent venir en dernier](../code-quality/ca1068.md) | Une méthode a un paramètre CancellationToken qui n’est pas le dernier paramètre. |
| Ca1069 | [CA1069 : Les enums ne doivent pas avoir de valeurs en double](../code-quality/ca1069.md) | Une énumération a plusieurs membres auxquels la même valeur de constante est affectée explicitement. |
| Ca1070 | [CA1070 : Ne pas déclarer de champs d’événement comme virtuels](../code-quality/ca1070.md) | Un [événement de type champ](/dotnet/csharp/language-reference/language-specification/classes#field-like-events) a été déclaré comme étant virtuel. |
| Ca1200 | [CA1200 : Éviter d’utiliser des balises cref avec un préfixe](../code-quality/ca1200.md) | L’attribut [cref](/dotnet/csharp/programming-guide/xmldoc/cref-attribute) dans une balise de documentation XML signifie « référence du code ». Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété. Évitez `cref` d’utiliser des balises avec des préfixes, car cela empêche le compilateur de vérifier les références. Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations. |
| CA1303 | [CA1303 : Ne pas passer de littéraux en paramètres localisés](../code-quality/ca1303.md) | Une méthode visible de l’extérieur passe un littéral de chaîne en tant que paramètre à une méthode ou un constructeur .NET, et cette chaîne doit être localisable. |
| CA1304 | [CA1304 : Spécifier CultureInfo](../code-quality/ca1304.md) | Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo. Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1305 | [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305.md) | Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider. Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1307 | [CA1307 : Spécifier StringComparison pour clarifier](../code-quality/ca1307.md) | Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison. |
| CA1308 |[CA1308 : Normaliser les chaînes en majuscules](../code-quality/ca1308.md) | Les chaînes doivent être normalisées en majuscules. En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller-retour. |
| CA1309 | [CA1309 : Utiliser StringComparison avec la valeur Ordinal](../code-quality/ca1309.md) | Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison. En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable. |
| Ca1310 | [CA1310 : Spécifier StringComparison pour corriger](../code-quality/ca1310.md) | Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison et utilise par défaut la comparaison de chaînes propre à la culture. |
| CA1401 | [Ca1401 : les P/Invoke ne doivent pas être visibles](../code-quality/ca1401.md) | Une méthode publique ou protégée dans un type public a l'attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). De telles méthodes ne doivent pas être exposées. |
| Ca1417 | [Ca1417 : ne pas utiliser `OutAttribute` sur les paramètres de chaîne pour les P/Invoke](../code-quality/ca1417.md) | Les paramètres de chaîne passés par valeur avec le `OutAttribute` peuvent déstabiliser le runtime si la chaîne est une chaîne internée. |
| CA1501 | [CA1501 : Éviter l'excès d'héritage](../code-quality/ca1501.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| CA1502 | [CA1502 : Éviter l'excès de complexité](../code-quality/ca1502.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| CA1505 | [CA1505 : Éviter le code impossible à maintenir](../code-quality/ca1505.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| CA1506 | [CA1506 : Éviter les couplages de classe excessifs](../code-quality/ca1506.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| Ca1507 | [CA1507 : Utiliser nameof à la place de string](../code-quality/ca1507.md) | Un littéral de chaîne est utilisé en tant qu’argument dans lequel une `nameof` expression peut être utilisée. |
| CA1508 | [CA1508 : Éviter le code conditionnel mort](../code-quality/ca1508.md) | Une méthode a un code conditionnel qui prend toujours la valeur `true` ou `false` au moment de l’exécution. Cela provoque un code mort dans la `false` branche de la condition. |
| Ca1509 | [CA1509 : Entrée non valide dans le fichier de configuration des métriques de code](../code-quality/ca1509.md) | Les règles de métrique du code, telles que [CA1501](ca1501.md), [CA1502](ca1502.md), [ca1505](ca1505.md) et [CA1506](ca1506.md), ont fourni un fichier de configuration nommé `CodeMetricsConfig.txt` qui a une entrée non valide. |
| CA1700 | [CA1700 : Ne nommez pas les valeurs enum 'Reserved'](../code-quality/ca1700.md) | Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture. |
| CA1707 | [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707.md) | Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). Cette règle vérifie les espaces de noms, types, membres et paramètres. |
| CA1708 | [CA1708 : Les identificateurs ne doivent pas différer uniquement par leur casse](../code-quality/ca1708.md) | Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. |
| CA1710 | [CA1710 : Les identificateurs doivent être dotés d'un suffixe correct](../code-quality/ca1710.md) |Par convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou encore des types dérivés de ces types, présentent un suffixe associé au type de base ou à l'interface. |
| CA1711 | [CA1711 : Les identificateurs ne doivent pas porter un suffixe incorrect](../code-quality/ca1711.md) | Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques. Les autres noms de types ne doivent pas utiliser ces suffixes réservés. |
| CA1712 | [CA1712 : N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum](../code-quality/ca1712.md) | Les noms des membres de l'énumération n'ont pas pour préfixe le nom de type, car les outils de développement sont censés fournir les informations de type. |
| CA1713 | [CA1713 : Les événements ne doivent pas être munis d'un préfixe Before ou After](../code-quality/ca1713.md) | Le nom d'un événement commence par « Before » ou « After ». Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions. |
| CA1714 | [CA1714 : Les noms des enums Flags doivent être au pluriel](../code-quality/ca1714.md) | Une énumération publique comporte l'attribut System.FlagsAttribute et son nom ne se termine pas par « s ». Les types marqués avec FlagsAttribute ont des noms au pluriel, car l'attribut indique que plusieurs valeurs peuvent être spécifiées. |
| CA1715 | [CA1715 : Les identificateurs doivent être dotés d'un préfixe correct](../code-quality/ca1715.md) | Le nom d'une interface extérieurement visible ne commence pas par un « I » majuscule. Le nom d'un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « T » majuscule. |
| CA1716 | [CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés](../code-quality/ca1716.md) | Un nom d'espace de noms ou un nom de type correspond à un mot clé réservé dans un langage de programmation. Les identificateurs des espaces de noms et des types ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime. |
| CA1717 | [CA1717 : Seuls les noms des enums FlagsAttribute doivent être au pluriel](../code-quality/ca1717.md) | Selon les conventions d'attribution de nom, un nom au pluriel pour une énumération indique que plusieurs valeurs de l'énumération peuvent être spécifiées simultanément. |
| CA1720 |[CA1720 : Les identificateurs ne doivent pas contenir de noms de types](../code-quality/ca1720.md) | Le nom d'un paramètre dans un membre extérieurement visible contient un nom de type de données, ou le nom d'un membre extérieurement visible contient un nom de type de données spécifique à une langue. |
| CA1721 | [CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get](../code-quality/ca1721.md) |Le nom d'un membre public ou protégé commence par « Get ». Sinon, il correspond au nom d'une propriété publique ou protégée. Les méthodes et propriétés « Get » doivent porter des noms distinguant clairement leur fonction. |
| CA1724 | [CA1724 : Les noms de types ne doivent pas être identiques aux espaces de noms](../code-quality/ca1724.md) | Les noms de types ne doivent pas correspondre aux noms des espaces de noms .NET. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque. |
| CA1725 | [CA1725 : Les noms des paramètres doivent correspondre à la déclaration de base](../code-quality/ca1725.md) | La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode. |
| CA1801 | [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801.md) | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| CA1802 |[CA1802 : Utilisez des littéraux quand cela est approprié](../code-quality/ca1802.md) |Un champ est déclaré statique et en lecture seule (Shared et ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), et est initialisé avec une valeur qui est calculable à la compilation. Étant donné que la valeur assignée au champ ciblé peut être calculée au moment de la compilation, remplacez la déclaration par un champ const (const in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) afin que la valeur soit calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| CA1805 | [CA1805 : Ne pas initialiser inutilement](../code-quality/ca1805.md) | Le Runtime .NET initialise tous les champs de type référence à leurs valeurs par défaut avant d’exécuter le constructeur. Dans la plupart des cas, l’initialisation explicite d’un champ à sa valeur par défaut est redondante, ce qui augmente les coûts de maintenance et peut dégrader les performances (par exemple, avec une taille d’assembly accrue). |
| CA1806 | [CA1806 : N'ignorez pas les résultats des méthodes](../code-quality/ca1806.md) | Un nouvel objet est créé mais jamais utilisé ; ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée ; ou une méthode COM ou P/Invoke retourne un code HRESULT ou d'erreur qui n'est jamais utilisé. |
| CA1810 | [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810.md) | Lorsqu'un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d'instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| CA1812 | [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812.md) | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| CA1813 | [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813.md) | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| CA1814 | [CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels](../code-quality/ca1814.md) | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données. |
| CA1815 | [CA1815 : Remplacez Equals et l'opérateur égal à dans les types valeur](../code-quality/ca1815.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| CA1816 | [CA1816 : Appeler GC.SuppressFinalize correctement](../code-quality/ca1816.md) | Une méthode qui est une implémentation de Dispose n'appelle pas GC.SuppressFinalize ; ou une méthode qui n'est pas une implémentation de Dispose appelle GC.SuppressFinalize ; ou une méthode appelle GC.SuppressFinalize et passe un élément autre que celui-ci (Me en Visual Basic). |
| CA1819 | [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819.md) | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| CA1820 | [CA1820 : Vérifiez la présence de chaînes vides par la longueur de chaîne](../code-quality/ca1820.md) | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| CA1821 | [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une charge supplémentaire sans aucun avantage. |
| CA1822 |[CA1822 : Marquez les membres comme static](../code-quality/ca1822.md) | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| CA1823 | [CA1823 : Évitez les champs privés inutilisés](../code-quality/ca1823.md) | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| CA1824 |[CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | L’attribut NeutralResourcesLanguage informe le gestionnaire de ressources de la langue utilisée pour afficher les ressources d’une culture neutre pour un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| CA1825 |[CA1825 : Éviter les allocations de tableau de longueur nulle](../code-quality/ca1825.md) | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement en appelant <xref:System.Array.Empty%2A?displayProperty=nameWithType> . L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
| CA1826 |[CA1826 : Utiliser une propriété au lieu de la méthode Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable> La méthode LINQ a été utilisée sur un type qui prend en charge une propriété équivalente et plus efficace. |
| CA1827 |[CA1827 : N’utilisez pas Count/LongCount quand Any peut être utilisé](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A> ou la <xref:System.Linq.Enumerable.LongCount%2A> méthode a été utilisée là où la <xref:System.Linq.Enumerable.Any%2A> méthode serait plus efficace. |
| CA1828 |[CA1828 : N’utilisez pas CountAsync/LongCountAsync quand AnyAsync peut être utilisé](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A> ou la <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> méthode a été utilisée là où la <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> méthode serait plus efficace. |
| CA1829 |[CA1829 : Utilisez la propriété Length/Count au lieu de la méthode Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A> La méthode LINQ a été utilisée sur un type qui prend en charge une propriété équivalente, plus efficace `Length` ou `Count` . |
| CA1830 |[CA1830 : Préférer les surcharges de méthode Append et Insert fortement typées sur StringBuilder](../code-quality/ca1830.md) | <xref:System.Text.StringBuilder.Append%2A> et <xref:System.Text.StringBuilder.Insert%2A> fournissent des surcharges pour plusieurs types au-delà de <xref:System.String> .  Dans la mesure du possible, préférez les surcharges fortement typées à l’aide de ToString () et de la surcharge basée sur une chaîne. |
| CA1831 |[CA1831 : Utiliser AsSpan à la place d’indexeurs basés sur Range pour une chaîne si approprié](../code-quality/ca1831.md) | Lors de l’utilisation d’un indexeur de plages sur une chaîne et de l’assignation implicite de la valeur au &lt; type char ReadOnlySpan &gt; , la méthode <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui génère une copie de la partie demandée de la chaîne. |
| CA1832 |[CA1832 : Utiliser AsSpan ou AsMemory à la place d’indexeurs basés sur Range pour obtenir la partie ReadOnlySpan ou ReadOnlyMemory d’un tableau](../code-quality/ca1832.md) | Lors de l’utilisation d’un indexeur de plages sur un tableau et de l’assignation implicite de la valeur à un <xref:System.ReadOnlySpan%601> <xref:System.ReadOnlyMemory%601> type ou, la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui produit une copie de la partie demandée du tableau. |
| CA1833 |[CA1833 : Utiliser AsSpan ou AsMemory à la place d’indexeurs basés sur Range pour obtenir la partie Span ou Memory d’un tableau](../code-quality/ca1833.md) | Lors de l’utilisation d’un indexeur de plages sur un tableau et de l’assignation implicite de la valeur à un <xref:System.Span%601> <xref:System.Memory%601> type ou, la méthode <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> est utilisée à la place de <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , ce qui produit une copie de la partie demandée du tableau. |
| CA1834 |[CA1834 : Utiliser StringBuilder.Append (char) pour les chaînes de caractères uniques](../code-quality/ca1834.md) | <xref:System.Text.StringBuilder> a une `Append` surcharge qui prend un `char` comme argument. Préférez l’appel `char` de la surcharge pour des raisons de performances. |
| CA1835 |[CA1835 : préférer les surcharges « Memory' » pour « ReadAsync » et « WriteAsync »](../code-quality/ca1835.md) | 'Stream’a une surcharge’ReadAsync’qui accepte’Memory &lt; Byte &gt; 'comme premier argument et une surcharge’WriteAsync’qui prend un’ReadOnlyMemory &lt; Byte &gt; 'comme premier argument. Préférez appeler les surcharges basées sur la mémoire, qui sont plus efficaces. |
| CA1836 |[CA1836 : préférer `IsEmpty` le `Count` cas échéant](../code-quality/ca1836.md) | Préférer `IsEmpty` la propriété qui est plus efficace `Count` que `Length` , <xref:System.Linq.Enumerable.Count%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> ou <xref:System.Linq.Enumerable.LongCount%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> pour déterminer si l’objet contient ou non des éléments. |
| CA1837 | [CA1837 : utilisez à la `Environment.ProcessId` place de `Process.GetCurrentProcess().Id`](../code-quality/ca1837.md) | `Environment.ProcessId` est plus simple et plus rapide que `Process.GetCurrentProcess().Id` . |
| CA1838 | [CA1838 : éviter `StringBuilder` les paramètres pour les P/Invoke](../code-quality/ca1838.md) | Le marshaling de « StringBuilder » crée toujours une copie de mémoire tampon native, ce qui entraîne plusieurs allocations pour une opération de marshaling. |
| CA2000 | [CA2000 : Supprimer les objets avant la mise hors de portée](../code-quality/ca2000.md) | Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée. |
| CA2002 |[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](../code-quality/ca2002.md) |Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet. |
| Ca2007 | [CA2007 : N’attendez pas directement une Tâche](ca2007.md) | Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) directement un <xref:System.Threading.Tasks.Task> . Lorsqu’une méthode asynchrone attend directement une <xref:System.Threading.Tasks.Task> , une continuation se produit dans le thread qui a créé la tâche. Ce comportement peut être coûteux en termes de performances et peut entraîner un blocage sur le thread d’interface utilisateur. Envisagez <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> d’appeler pour signaler votre intention de continuation. |
| CA2008 | [CA2008 : Ne pas créer de tâches sans passer TaskScheduler](ca2008.md) | Une opération de création de tâche ou de continuation utilise une surcharge de méthode qui ne spécifie pas de <xref:System.Threading.Tasks.TaskScheduler> paramètre. |
| Ca2009 | [CA2009 : N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection](ca2009.md) | `ToImmutable` la méthode était inutilement appelée sur une collection immuable de l' <xref:System.Collections.Immutable> espace de noms. |
| Ca2011 | [CA2011 : Ne pas assigner la propriété dans son setter](ca2011.md) | Une valeur a été assignée par erreur à une propriété dans son propre [accesseur Set](/dotnet/csharp/programming-guide/classes-and-structs/using-properties#the-set-accessor). |
| Ca2012 | [CA2012 : Utiliser correctement ValueTasks](ca2012.md) | Les ValueTasks retournés par les appels de membres sont censés être attendus directement.  Toute tentative d’utilisation d’un ValueTask à plusieurs reprises ou d’un accès direct à l’un des résultats avant qu’il ne soit connu peut entraîner une exception ou une altération.  En ignorant ce ValueTask, il est probable qu’il s’agit d’une indication d’un bogue fonctionnel et peut nuire aux performances. |
| Ca2013 | [CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur](ca2013.md) | Lors de la comparaison de valeurs à l’aide <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> de, si objA et objB sont des types valeur, ils sont boxed avant d’être passés à la <xref:System.Object.ReferenceEquals%2A> méthode. Cela signifie que même si objA et objB représentent la même instance d’un type valeur, la <xref:System.Object.ReferenceEquals%2A> méthode retourne néanmoins false. |
| Ca2014 | [Ca2014 : n’utilisez pas stackalloc dans les boucles.](ca2014.md) | L’espace de pile alloué par stackalloc est libéré uniquement à la fin de l’appel de la méthode actuelle.  Son utilisation dans une boucle peut entraîner une croissance de pile illimitée et des conditions de dépassement de capacité de pile éventuelles. |
| Ca2015 | [Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager &lt; T&gt;](ca2015.md) | L’ajout d’un finaliseur à un type dérivé de <xref:System.Buffers.MemoryManager%601> peut permettre la libération de la mémoire pendant qu’il est toujours utilisé par un <xref:System.Span%601> . |
| Ca2016 | [CA2016 : Transférer le paramètre CancellationToken aux méthodes qui l’acceptent](ca2016.md) | Transférez le `CancellationToken` paramètre aux méthodes qui prennent une pour garantir que les notifications d’annulation d’opération sont correctement propagées, ou transmettez `CancellationToken.None` explicitement pour indiquer intentionnellement que le jeton n’est pas propagé. |
| CA2100 | [CA2100 : Vérifier si les requêtes SQL présentent des failles de sécurité](../code-quality/ca2100.md) | Une méthode définit la propriété System.Data.IDbCommand.CommandText à l’aide d’une chaîne générée à partir d’un argument de chaîne à la méthode. Cette règle suppose que l’argument de chaîne contient des entrées d’utilisateur. Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL. |
| CA2101 |[CA2101 : spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101.md) | Un membre d’appel de code non managé autorise les appelants dotés d’un niveau de confiance partielle, présente un paramètre de chaîne et ne marshale pas explicitement la chaîne. Cela peut provoquer une faille de sécurité potentielle. |
| CA2109 | [CA2109 : Passez en revue les gestionnaires d'événements visibles](../code-quality/ca2109.md) | Une méthode de gestion d’événements publique ou protégée a été détectée. Les méthodes de gestion d’événements ne doivent pas être exposées sauf nécessité absolue. |
| CA2119 | [CA2119 : Scellez les méthodes qui satisfont les interfaces privées](../code-quality/ca2119.md) | Un type public pouvant être hérité fournit une implémentation de méthode substituable d'une interface interne (Friend en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly. |
| CA2153 |[Ca2172 : Évitez de gérer les exceptions d’état endommagé](../code-quality/ca2153.md) | Les exceptions d’état endommagé (CSE) indiquent qu’il existe une altération de la mémoire dans votre processus. Le fait d’intercepter ces exceptions au lieu d’autoriser le processus à se bloquer peut engendrer des failles de sécurité si une personne malveillante réussit à placer une attaque dans la région de la mémoire endommagée. |
| CA2200 | [CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200.md) | Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue. |
| CA2201 | [CA2201 : Ne levez pas des types d'exceptions réservés](../code-quality/ca2201.md) | Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2207 | [CA2207 : Initialisez les champs statiques des types valeur en ligne](../code-quality/ca2207.md) | Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique. |
| CA2208 |[CA2208 : Instanciez les exceptions d'argument comme il se doit](../code-quality/ca2208.md) | Un appel est passé au constructeur par défaut (sans paramètre) d'un type d'exception qui est ou dérive d'ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d'un type d'exception qui est ou dérive d'ArgumentException. |
| CA2211 |[CA2211 : Les champs non constants ne doivent pas être visibles](../code-quality/ca2211.md) | Les champs statiques qui ne sont ni constants ni en lecture seule ne sont pas thread-safe. L'accès à un tel champ doit être scrupuleusement contrôlé et requiert des techniques de programmation évoluées pour synchroniser l'accès à l'objet de classe. |
| CA2213 | [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213.md) | Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n'est pas appelée par la méthode Dispose du type déclarant. |
| CA2214 | [CA2214 : N'appelez pas de méthodes substituables dans les constructeurs](../code-quality/ca2214.md) | Lorsqu'un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l'instance qui appelle la méthode n'ait pas été exécuté. |
| CA2215 | [CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215.md) | Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose. |
| CA2216 |[CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur](../code-quality/ca2216.md) | Un type qui implémente System.IDisposable et présente des champs qui laissent entendre l'utilisation de ressources non managées n'implémente pas de finaliseur conforme à la description de Object.Finalize. |
| CA2217 | [CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](../code-quality/ca2217.md) |Une énumération extérieurement visible est marquée par FlagsAttribute et possède une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies dans l'énumération. |
| CA2219 | [CA2219 : Ne pas lever d'exceptions dans les clauses d'exception](../code-quality/ca2219.md) | Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2225 | [CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](../code-quality/ca2225.md) |Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé donne accès aux mêmes fonctionnalités que l'opérateur. Il est fourni aux développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés. |
| CA2226 | [CA2226 : Les opérateurs doivent contenir des surcharges symétriques](../code-quality/ca2226.md) | Un type implémente l'opérateur d'égalité ou d'inégalité et n'implémente pas l'opérateur opposé. |
| CA2227 |[CA2227 : Les propriétés de collection doivent être en lecture seule](../code-quality/ca2227.md) |Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis. |
| CA2229 | [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229.md) | Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé. |
| CA2231 | [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231.md) | Un type valeur se substitue à Object.Equals mais n'implémente pas l'opérateur d'égalité. |
| CA2234 | [CA2234 : Passez des objets System.Uri à la place de chaînes](../code-quality/ca2234.md) | Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ». Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri. |
| CA2235 | [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235.md) | Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable. |
| CA2237 | [CA2237 : Marquer les types ISerializable avec SerializableAttribute](../code-quality/ca2237.md) | Pour être reconnus par le Common Language Runtime comme sérialisables, les types doivent être marqués avec l'attribut SerializableAttribute même s'ils utilisent une routine de sérialisation personnalisée par le biais de l'implémentation de l'interface ISerializable. |
| CA2241 | [CA2241 : Indiquer le nombre correct d'arguments dans les méthodes de mise en forme](../code-quality/ca2241.md) | L’argument de format passé à System.String.Format ne contient aucun élément de mise en forme pour chaque argument objet correspondant, ou vice versa. |
| CA2242 |[CA2242 : Effectuez correctement des tests NaN](../code-quality/ca2242.md) | Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur. |
| CA2243 |[CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement](../code-quality/ca2243.md) | Le paramètre de littéral de chaîne d'un attribut n'effectue pas une analyse correcte pour une URL, un GUID ou une version. |
| CA2244 | [CA2244 : Ne pas dupliquer les initialisations d’éléments indexés](../code-quality/ca2244.md) | Un initialiseur d’objet a plus d’un initialiseur d’élément indexé avec le même index constant. Tout sauf le dernier initialiseur est redondant. |
| CA2245 | [CA2245 : Ne pas attribuer une propriété à elle-même](../code-quality/ca2245.md) | Une propriété a été accidentellement assignée à elle-même. |
| CA2246 | [CA2246 : Ne pas attribuer un symbole et son membre dans la même instruction](../code-quality/ca2246.md) | L’assignation d’un symbole et de son membre, autrement dit, un champ ou une propriété, dans la même instruction n’est pas recommandée. Il n’est pas évident de préciser si l’accès au membre était destiné à utiliser l’ancienne valeur du symbole avant l’assignation ou la nouvelle valeur de l’assignation dans cette instruction. |
| CA2247 | [CA2247 : l’argument passé au constructeur TaskCompletionSource doit être TaskCreationOptions enum au lieu de TaskContinuationOptions Enum.](../code-quality/ca2247.md) | TaskCompletionSource possède des constructeurs qui prennent des TaskCreationOptions qui contrôlent la tâche sous-jacente, et les constructeurs qui prennent l’état d’objet stocké dans la tâche.  Le passage accidentel d’un TaskContinuationOptions au lieu d’un TaskCreationOptions entraînera l’appel du traitement des options en tant qu’État. |
| CA2248 | [CA2248 : Fournir le bon argument enum à Enum.HasFlag](../code-quality/ca2248.md) | Le type enum passé comme argument à l' `HasFlag` appel de méthode est différent du type enum appelant. |
| CA2249 | [CA2249 : Utiliser de préférence String.Contains à la place de String.IndexOf](../code-quality/ca2249.md) | Les appels à `string.IndexOf` où le résultat est utilisé pour vérifier la présence ou l’absence d’une sous-chaîne peuvent être remplacés par `string.Contains` . |
| Ca2300 | [CA2300 : N’utilisez pas le désérialiseur non sécurisé BinaryFormatter](../code-quality/ca2300.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| Ca2301 | [CA2301 : N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable](../code-quality/ca2301.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| Ca2302 | [CA2302 : Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize](../code-quality/ca2302.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2305 | [CA2305 : N’utilisez pas le désérialiseur non sécurisé LosFormatter](../code-quality/ca2305.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2310 | [CA2310 : N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer](../code-quality/ca2310.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2311 | [CA2311 : Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder](../code-quality/ca2311.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2312 | [CA2312 : Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation](../code-quality/ca2312.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2315 | [CA2315 : N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter](../code-quality/ca2315.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2321 | [CA2321 : Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver](../code-quality/ca2321.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2322 | [CA2322 : Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation](../code-quality/ca2322.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2326 | [CA2326 : N’utilisez pas de valeurs TypeNameHandling autres que None](../code-quality/ca2326.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2327 | [CA2327 : N’utilisez pas de JsonSerializerSettings non sécurisés](../code-quality/ca2327.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2328 | [CA2328 : Vérifiez que les JsonSerializerSettings sont sécurisés](../code-quality/ca2328.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2329 | [CA2329 : Ne désérialisez pas avec JsonSerializer à l’aide d’une configuration non sécurisée](../code-quality/ca2329.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| CA2330 | [CA2330 : Vérifiez que JsonSerializer a une configuration sécurisée lors de la désérialisation.](../code-quality/ca2330.md) | Les désérialiseurs non sécurisés sont vulnérables lors de la désérialisation des données non approuvées. Une personne malveillante peut modifier les données sérialisées pour inclure des types inattendus afin d’injecter des objets avec des effets secondaires malveillants. |
| Ca2350 | [CA2350 : Vérifier que l’entrée de DataTable.ReadXml() est approuvée](ca2350.md) | Lors de la désérialisation d’un <xref:System.Data.DataTable> avec une entrée non fiable, une personne malveillante peut concevoir une entrée malveillante pour effectuer une attaque par déni de service. Il peut y avoir des vulnérabilités d’exécution de code à distance inconnues. |
| Ca2351 | [CA2351 : Vérifier que l’entrée de DataSet.ReadXml() est approuvée](ca2351.md) | Lors de la désérialisation d’un <xref:System.Data.DataSet> avec une entrée non fiable, une personne malveillante peut concevoir une entrée malveillante pour effectuer une attaque par déni de service. Il peut y avoir des vulnérabilités d’exécution de code à distance inconnues. |
| CA2352 | [CA2352 : Un jeu de données ou une table de données non sécurisé(e) dans un type sérialisable peut être vulnérable aux attaques par exécution de code à distance](ca2352.md) | Une classe ou un struct marqué avec <xref:System.SerializableAttribute> contient un champ ou une <xref:System.Data.DataSet> <xref:System.Data.DataTable> propriété, et n’a pas de <xref:System.CodeDom.Compiler.GeneratedCodeAttribute> . |
| CA2353 | [CA2353 : Jeu de données ou table de données non sécurisé(e) dans un type sérialisable](ca2353.md) | Une classe ou un struct marqué avec un attribut de sérialisation XML ou un attribut de contrat de données contient un <xref:System.Data.DataSet> champ ou une <xref:System.Data.DataTable> propriété ou. |
| CA2354 | [CA2354 : Un jeu de données ou une table de données non sécurisé(e) dans un graphe d’objets désérialisé peut être vulnérable à une attaque par exécution de code à distance](ca2354.md) | La désérialisation avec un <xref:System.Runtime.Serialization.IFormatter?displayProperty=nameWithType> sérialisé et le graphique d’objet du type casté peuvent inclure <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> . |
| CA2355 | [CA2355 : Jeu de données ou table de données non sécurisé(e) dans un graphe d’objets désérialisé](ca2355.md) | Désérialisation lorsque le graphique d’objets du type casté ou spécifié peut inclure un <xref:System.Data.DataSet> ou un <xref:System.Data.DataTable> . |
| CA2356 | [CA2356 : jeu de données ou DataTable non sécurisés dans le graphique d’objets désérialisés Web](ca2356.md) | Une méthode avec un <xref:System.Web.Services.WebMethodAttribute?displayProperty=nameWithType> ou un <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> a un paramètre qui peut faire référence à un <xref:System.Data.DataSet> ou un <xref:System.Data.DataTable> . |
| CA2361 | [CA2361 : Vérifier que la classe générée automatiquement contenant DataSet.ReadXml() n'est pas utilisée avec des données non fiables](ca2361.md) | Lors de la désérialisation d’un <xref:System.Data.DataSet> avec une entrée non fiable, une personne malveillante peut concevoir une entrée malveillante pour effectuer une attaque par déni de service. Il peut y avoir des vulnérabilités d’exécution de code à distance inconnues. |
| CA2362 | [CA2362 : Un jeu de données ou une table de données non sécurisé dans un type sérialisable généré automatiquement peut être vulnérable aux attaques par exécution de code à distance](ca2362.md) | Lors de la désérialisation d’une entrée non approuvée avec <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> et que le graphique d’objets désérialisé contient <xref:System.Data.DataSet> ou <xref:System.Data.DataTable> , une personne malveillante peut concevoir une charge utile malveillante pour effectuer une attaque d’exécution de code à distance. |
| CA3001 | [CA3001 : Passez en revue le code pour détecter les vulnérabilités de l’injection SQL](../code-quality/ca3001.md) | Lorsque vous utilisez des commandes d’entrée et SQL non fiables, tenez-vous à l’esprit des attaques par injection SQL. Une attaque par injection de SQL peut exécuter des commandes SQL malveillantes et compromettre la sécurité et l’intégrité de votre application. |
| Ca3002 | [CA3002 : Passez en revue le code pour détecter les vulnérabilités des scripts XSS](../code-quality/ca3002.md) | Lorsque vous travaillez avec des entrées non approuvées à partir de requêtes Web, gardez à l’esprit les attaques de script entre sites (XSS). Une attaque XSS injecte une entrée non fiable dans une sortie HTML brute, ce qui permet à la personne malveillante d’exécuter des scripts malveillants ou de modifier du contenu de manière malveillante dans votre page Web. |
| Ca3003 | [CA3003 : Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier](../code-quality/ca3003.md) | Lorsque vous travaillez avec des entrées non approuvées à partir de requêtes Web, pensez à utiliser une entrée contrôlée par l’utilisateur lors de la spécification des chemins d’accès aux fichiers. |
| Ca3004 | [CA3004 : Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations](../code-quality/ca3004.md) | La divulgation d’informations sur les exceptions permet aux attaquants d’obtenir des informations sur les éléments internes de votre application, ce qui peut aider les attaquants à trouver d’autres vulnérabilités à exploiter. |
| Ca3006 | [CA3006 : Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus](../code-quality/ca3006.md) | Lorsque vous travaillez avec des entrées non fiables, tenez-vous à l’esprit des attaques par injection de commande. Une attaque par injection de commande peut exécuter des commandes malveillantes sur le système d’exploitation sous-jacent, compromettant ainsi la sécurité et l’intégrité de votre serveur. |
| CA3007 | [CA3007 : Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte](../code-quality/ca3007.md) | Lors de l’utilisation d’une entrée non fiable, tenez à l’esprit des vulnérabilités de redirection ouvertes. Une personne malveillante peut exploiter une vulnérabilité de redirection ouverte pour utiliser votre site Web afin de fournir l’apparence d’une URL légitime, mais de rediriger un visiteur non suspect vers une autre page Web malveillante ou malveillante. |
| CA3008 | [CA3008 : Passez en revue le code pour détecter les vulnérabilités de l’injection XPath](../code-quality/ca3008.md) | Lors de l’utilisation d’une entrée non fiable, tenez-vous à l’esprit des attaques par injection XPath. La construction de requêtes XPath à l’aide d’une entrée non approuvée peut permettre à une personne malveillante de manipuler la requête de manière malveillante pour retourner un résultat inattendu et éventuellement divulguer le contenu du fichier XML interrogé. |
| CA3009 | [CA3009 : Passez en revue le code pour détecter les vulnérabilités de l’injection XML](../code-quality/ca3009.md) | Lorsque vous travaillez avec des entrées non fiables, soyez attentif aux attaques par injection XML. |
| Ca3010 | [CA3010 : Passez en revue le code pour détecter les vulnérabilités de l’injection XAML](../code-quality/ca3010.md) | Lorsque vous travaillez avec des entrées non fiables, tenez-vous à l’esprit des attaques par injection de code XAML. Le XAML est un langage de balisage qui représente directement l’instanciation d’objets et leur exécution. Cela signifie que les éléments créés en XAML peuvent interagir avec les ressources système (par exemple, l’accès réseau et l’e/s du système de fichiers). |
| CA3011 | [CA3011 : Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL](../code-quality/ca3011.md) | Lors de l’utilisation d’une entrée non fiable, pensez au chargement de code non fiable. Si votre application Web charge du code non fiable, une personne malveillante peut être en mesure d’injecter des dll malveillantes dans votre processus et d’exécuter du code malveillant. |
| CA3012 | [CA3012 : Passez en revue le code pour détecter les vulnérabilités de l’injection regex](../code-quality/ca3012.md) | Lorsque vous travaillez avec des entrées non fiables, soyez attentif aux attaques par injection de Regex. Une personne malveillante peut utiliser l’injection Regex pour modifier une expression régulière de manière malveillante, pour faire correspondre des résultats inattendus par l’expression régulière, ou pour faire en sorte que l’expression régulière consomme un processeur excessif, entraînant une attaque par déni de service. |
| CA3061 | [CA3061 : Ne pas ajouter de schéma par URL](../code-quality/ca3061.md) | N’utilisez pas la surcharge unsafe de la méthode Add, car elle peut provoquer des références externes dangereuses. |
| CA3075 | [CA3075 : Traitement DTD non sécurisé](../code-quality/ca3075.md) | Si vous utilisez des instances de DTDProcessing non sécurisées ou référencez des sources d’entités externes, l’analyseur peut accepter une entrée non fiable et divulguer des informations sensibles à des personnes malveillantes. |
| CA3076 | [CA3076 : Exécution non sécurisée de script XSLT](../code-quality/ca3076.md) | Si vous exécutez des transformations XSLT (Extensible Stylesheet Language Transformations) dans les applications .NET de manière non sécurisée, le processeur peut résoudre les références URI non fiables qui pourraient divulguer des informations sensibles à des attaquants, conduisant à des attaques par déni de service et intersites. |
| CA3077 | [CA3077 : Traitement non sécurisé dans la conception d’API, le document XML et le lecteur de texte XML](../code-quality/ca3077.md) | Lors de la conception d’une API dérivée de XMLDocument et XMLTextReader, tenez compte de DtdProcessing. L’utilisation d’instances de DTDProcessing non sécurisées lors de la référence ou la résolution de sources d’entités externes ou la définition de valeurs non sécurisées dans le code XML peut aboutir à la divulgation d’informations. |
| CA3147 | [CA3147 : Marquer les gestionnaires de verbe avec ValidateAntiForgeryToken](../code-quality/ca3147.md) | Lors de la conception d’un contrôleur MVC ASP.NET, soyez attentif aux attaques de falsification de requête intersites. Une attaque de falsification de requête intersite peut envoyer des demandes malveillantes d’un utilisateur authentifié à votre contrôleur ASP.NET MVC. |
| CA5350 | [CA5350 : N’utilisez pas d’algorithmes de chiffrement faibles](../code-quality/ca5350.md) | Des algorithmes de chiffrement et des fonctions de hachage faibles sont utilisés aujourd’hui pour plusieurs raisons, mais ils ne doivent pas servir à garantir la confidentialité ou l’intégrité des données qu’ils protègent. Cette règle se déclenche lorsqu’elle détecte des algorithmes TripleDES, SHA1 ou RIPEMD160 dans le code.|
| CA5351 | [CA5351 N’utilisez pas les algorithmes de chiffrement cassés](../code-quality/ca5351.md) | Les algorithmes de chiffrement cassés ne sont pas considérés comme sécurisés, et leur utilisation doit être fortement déconseillée. Cette règle se déclenche lorsqu’elle détecte l’algorithme de hachage MD5 ou les algorithmes de chiffrement RC2 ou DES dans le code. |
| CA5358 | [CA5358 : Ne pas utiliser de modes de chiffrement non sécurisés](../code-quality/ca5358.md) | Ne pas utiliser de modes de chiffrement non sécurisés |
| CA5359 | [CA5359 ne pas désactiver la validation de certificat](../code-quality/ca5359.md) | Un certificat peut aider à authentifier l’identité du serveur. Les clients doivent valider le certificat de serveur pour s’assurer que les demandes sont envoyées au serveur souhaité. Si le ServerCertificateValidationCallback retourne toujours `true` , les certificats sont validés. |
| CA5360 | [Les CA5360 n’appellent pas de méthodes dangereuses dans la désérialisation](../code-quality/ca5360.md) | Une désérialisation non sécurisée est une vulnérabilité qui se produit lorsque des données non approuvées sont utilisées pour abuser de la logique d’une application, provoquer une attaque par déni de service (DoS) ou même exécuter du code arbitraire sur la désérialisation. Il est souvent possible pour les utilisateurs malveillants d’abuser de ces fonctionnalités de désérialisation lorsque l’application désérialise des données non approuvées qui sont sous leur contrôle. Plus précisément, appelez des méthodes dangereuses dans le processus de désérialisation. Des attaques de désérialisation non sécurisées pourraient permettre à une personne malveillante d’effectuer des attaques telles que les attaques par déni de l’authentification, les contournements d’authentification et l’exécution de code à distance. |
| CA5361 | [CA5361 : Ne pas désactiver l’utilisation du chiffrement fort par SChannel](../code-quality/ca5361.md) | `Switch.System.Net.DontEnableSchUseStrongCrypto`Le paramètre pour `true` assouplit le chiffrement utilisé dans les connexions TLS (Transport Layer Security) sortantes. Un chiffrement plus faible peut compromettre la confidentialité de la communication entre votre application et le serveur, ce qui permet aux attaquants d’espionner facilement les données sensibles. |
| CA5362 | [CA5362 cycle de référence potentiel dans le graphique d’objets désérialisé](../code-quality/ca5362.md) | En cas de désérialisation de données non fiables, tout code qui traite le graphique d’objets désérialisé doit gérer les cycles de référence sans passer par des boucles infinies. Cela comprend à la fois le code qui fait partie d’un rappel de désérialisation et le code qui traite le graphique d’objet une fois la désérialisation terminée. Dans le cas contraire, une personne malveillante pourrait effectuer une attaque par déni de service avec des données malveillantes contenant un cycle de référence. |
| CA5363 | [CA5363 : Ne pas désactiver la validation de demandes](../code-quality/ca5363.md) | La validation de la demande est une fonctionnalité de ASP.NET qui examine les requêtes HTTP et détermine si elles contiennent du contenu potentiellement dangereux pouvant entraîner des attaques par injection, y compris des scripts inter-sites. |
| CA5364 | [CA5364 : Ne pas utiliser de protocoles de sécurité dépréciés](../code-quality/ca5364.md) | TLS (Transport Layer Security) sécurise la communication entre les ordinateurs, le plus souvent avec le protocole HTTPs (Hypertext Transfer Protocol Secure). Les anciennes versions de protocole TLS sont moins sécurisées que TLS 1,2 et TLS 1,3 et sont plus susceptibles d’avoir de nouvelles vulnérabilités. Évitez les anciennes versions de protocole pour réduire les risques. |
| CA5365 | [CA5365 ne désactivez pas la vérification d’en-tête HTTP](../code-quality/ca5365.md) | La vérification d’en-tête HTTP permet l’encodage des caractères de retour chariot et de saut de ligne, \r et \n, qui se trouvent dans les en-têtes de réponse. Cet encodage peut aider à éviter les attaques par injection qui exploitent une application qui renvoie les données non fiables contenues dans l’en-tête. |
| CA5366 | [CA5366 utiliser XmlReader pour lire le jeu de données XML](../code-quality/ca5366.md) | L’utilisation <xref:System.Data.DataSet> d’un pour lire des données XML avec des données non fiables peut charger des références externes dangereuses, qui doivent être limitées à l’aide d’un <xref:System.Xml.XmlReader> avec un résolveur sécurisé ou lorsque le traitement DTD est désactivé. |
| CA5367 | [CA5367 ne sérialise pas les types avec des champs de pointeur](../code-quality/ca5367.md) | Cette règle vérifie s’il existe une classe sérialisable avec un champ ou une propriété de pointeur. Les membres qui ne peuvent pas être sérialisés peuvent être un pointeur, tel que des membres statiques ou des champs marqués avec <xref:System.NonSerializedAttribute> . |
| CA5368 | [CA5368 Set ViewStateUserKey pour les classes dérivées de page](../code-quality/ca5368.md) | La définition de la <xref:System.Web.UI.Page.ViewStateUserKey> propriété peut vous aider à empêcher les attaques sur votre application en vous permettant d’affecter un identificateur à la variable d’état d’affichage pour les utilisateurs individuels afin que les attaquants ne puissent pas utiliser la variable pour générer une attaque. Dans le cas contraire, il y aura des vulnérabilités à la falsification de requête intersites. |
| CA5369 | [CA5369 : Utiliser XmlReader pour la désérialisation](../code-quality/ca5369.md) | Le traitement de schémas DTD et XML non fiables peut permettre le chargement de références externes dangereuses, qui doivent être limitées à l’aide d’un XmlReader avec un programme de résolution sécurisé ou avec la DTD et le traitement du schéma Inline XML désactivé. |
| CA5370 | [CA5370 : Utiliser XmlReader pour la validation du lecteur](../code-quality/ca5370.md) | Le traitement des DTD et des schémas XML non fiables peut permettre le chargement de références externes dangereuses. Ce chargement dangereux peut être restreint à l’aide d’un XmlReader avec un programme de résolution sécurisé ou avec la DTD et le traitement du schéma Inline XML désactivé. |
| CA5371 | [CA5371 : Utiliser XmlReader pour la lecture de schéma](../code-quality/ca5371.md) | Le traitement des DTD et des schémas XML non fiables peut permettre le chargement de références externes dangereuses. L’utilisation d’un XmlReader avec un programme de résolution sécurisé ou avec la DTD et le traitement de schéma Inline XML désactivé restreint les restrictions. |
| CA5372 | [CA5372 : Utiliser XmlReader pour XPathDocument](../code-quality/ca5372.md) | Le traitement de code XML à partir de données non fiables peut charger des références externes dangereuses, qui peuvent être limitées à l’aide d’un XmlReader avec un programme de résolution sécurisé ou lorsque le traitement DTD est désactivé. |
| CA5373 | [CA5373 : Ne pas utiliser la fonction de dérivation de clé obsolète](../code-quality/ca5373.md) | Cette règle détecte l’appel des méthodes de dérivation de clé faible <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> et `Rfc2898DeriveBytes.CryptDeriveKey` . <xref:System.Security.Cryptography.PasswordDeriveBytes?displayProperty=fullName> utilisé un algorithme PBKDF1 faible. |
| CA5374 | [CA5374 n’utilisez pas XslTransform](../code-quality/ca5374.md) | Cette règle vérifie si <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> est instancié dans le code. <xref:System.Xml.Xsl.XslTransform?displayProperty=nameWithType> est désormais obsolète et ne doit pas être utilisé. |
| CA5375 | [CA5375 n’utilise pas la signature d’accès partagé du compte](../code-quality/ca5375.md) | Une SAP de compte peut déléguer l’accès aux opérations de lecture, d’écriture et de suppression sur les conteneurs d’objets BLOB, les tables, les files d’attente et les partages de fichiers qui ne sont pas autorisés avec une SAP de service. Toutefois, il ne prend pas en charge les stratégies au niveau du conteneur et a moins de flexibilité et de contrôle sur les autorisations accordées. Une fois que les utilisateurs malveillants l’obtiennent, votre compte de stockage est facilement compromis. |
| CA5376 | [CA5376 utiliser SharedAccessProtocol HttpsOnly](../code-quality/ca5376.md) | La signature d’accès partagé est une donnée sensible qui ne peut pas être transportée en texte brut sur HTTP. |
| CA5377 | [CA5377 utiliser la stratégie d’accès au niveau du conteneur](../code-quality/ca5377.md) | Une stratégie d’accès au niveau du conteneur peut être modifiée ou révoquée à tout moment. Il offre une plus grande souplesse et un contrôle sur les autorisations accordées. |
| CA5378 | [CA5378 : Ne pas désactiver ServicePointManagerSecurityProtocols](../code-quality/ca5378.md) | Le paramètre `Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols` pour `true` limite les connexions TLS (Transport Layer Security) de Windows Communication Framework (WCF) à l’utilisation de TLS 1,0. Cette version de TLS sera dépréciée. |
| CA5379 | [CA5379 n’utilise pas l’algorithme de fonction de dérivation de clé faible](../code-quality/ca5379.md) | La <xref:System.Security.Cryptography.Rfc2898DeriveBytes> classe utilise par défaut l' <xref:System.Security.Cryptography.HashAlgorithmName.SHA1> algorithme. Vous devez spécifier l’algorithme de hachage à utiliser dans certaines surcharges du constructeur avec <xref:System.Security.Cryptography.HashAlgorithmName.SHA256> ou une version ultérieure. Remarque : <xref:System.Security.Cryptography.Rfc2898DeriveBytes.HashAlgorithm> la propriété a uniquement un `get` accesseur et n’a pas de `overriden` modificateur. |
| CA5380 | [CA5380 : Ne pas ajouter de certificats au magasin racine](../code-quality/ca5380.md) | Cette règle détecte le code qui ajoute un certificat dans le magasin de certificats des autorités de certification racines de confiance. Par défaut, le magasin de certificats des autorités de certification racines de confiance est configuré avec un ensemble d’autorités de certification publiques qui remplissent les conditions du programme de certification racine de Microsoft. |
| CA5381 | [CA5381 : S’assurer que les certificats ne sont pas ajoutés au magasin racine](../code-quality/ca5381.md) | Cette règle détecte le code qui ajoute potentiellement un certificat dans le magasin de certificats des autorités de certification racines de confiance. Par défaut, le magasin de certificats des autorités de certification racines de confiance est configuré avec un ensemble d’autorités de certification publiques qui répondent aux exigences du programme de certification racine de Microsoft. |
| CA5382 | [CA5382 utiliser des cookies sécurisés dans ASP.NET Core](../code-quality/ca5382.md) | Les applications disponibles sur HTTPs doivent utiliser des cookies sécurisés, qui indiquent au navigateur que le cookie doit être transmis uniquement à l’aide d’protocole SSL (SSL). |
| CA5383 | [CA5383 garantir l’utilisation des cookies sécurisés dans ASP.NET Core](../code-quality/ca5383.md) | Les applications disponibles sur HTTPs doivent utiliser des cookies sécurisés, qui indiquent au navigateur que le cookie doit être transmis uniquement à l’aide d’protocole SSL (SSL). |
| CA5384 | [CA5384 n’utilisez pas l’algorithme de signature numérique (DSA)](../code-quality/ca5384.md) | DSA est un algorithme de chiffrement asymétrique faible. |
| CA5385 | [CA5385 utiliser l’algorithme RSA (Rivest-Shamir-Adleman) avec une taille de clé suffisante](../code-quality/ca5385.md) | Une clé RSA inférieure à 2048 bits est plus vulnérable aux attaques par force brute. |
| CA5386 | [CA5386 : Éviter tout codage en dur de la valeur de SecurityProtocolType](../code-quality/ca5386.md) | TLS (Transport Layer Security) sécurise la communication entre les ordinateurs, le plus souvent avec le protocole HTTPs (Hypertext Transfer Protocol Secure). Les versions de protocole TLS 1,0 et TLS 1,1 sont dépréciées, tandis que TLS 1,2 et TLS 1,3 sont à jour. À l’avenir, TLS 1,2 et TLS 1,3 peuvent être déconseillés. Pour garantir la sécurité de votre application, évitez de coder en dur une version de protocole et ciblez au moins .NET Framework v 4.7.1. |
| CA5387 | [CA5387 n’utilisez pas la fonction de dérivation de clé faible avec un nombre d’itérations insuffisant](../code-quality/ca5387.md) | Cette règle vérifie si une clé de chiffrement a été générée par <xref:System.Security.Cryptography.Rfc2898DeriveBytes> avec un nombre d’itérations inférieur à 100 000. Un nombre d’itérations plus élevé peut aider à atténuer les attaques de dictionnaire qui essaient de deviner la clé de chiffrement générée. |
| CA5388 | [CA5388 garantir un nombre d’itérations suffisant lors de l’utilisation de la fonction de dérivation de clé faible](../code-quality/ca5388.md) | Cette règle vérifie si une clé de chiffrement a été générée par <xref:System.Security.Cryptography.Rfc2898DeriveBytes> avec un nombre d’itérations qui peut être inférieur à 100 000. Un nombre d’itérations plus élevé peut aider à atténuer les attaques de dictionnaire qui essaient de deviner la clé de chiffrement générée. |
| CA5389 | [CA5389 : Ne pas ajouter le chemin de l’élément d’archive au chemin du système de fichiers cible](../code-quality/ca5389.md) | Le chemin d’accès de fichier peut être relatif et peut entraîner l’accès au système de fichiers en dehors du chemin d’accès cible du système de fichiers attendu, ce qui conduit à des modifications de configuration malveillantes et à l’exécution de code à distance par le biais d’une technique de mise en attente. |
| CA5390 | [CA5390 ne pas coder en dur la clé de chiffrement](../code-quality/ca5390.md) | Pour qu’un algorithme symétrique réussisse, la clé secrète doit être connue uniquement de l’expéditeur et du récepteur. Lorsqu’une clé est codée en dur, elle est facilement découverte. Même avec les fichiers binaires compilés, il est facile pour les utilisateurs malveillants de l’extraire. Une fois la clé privée compromise, le texte chiffré peut être déchiffré directement et n’est plus protégé. |
| CA5391 | [CA5391 utiliser des jetons anti-contrefaçon dans ASP.NET Core contrôleurs MVC](../code-quality/ca5391.md) | La gestion d’une `POST` `PUT` demande,, `PATCH` ou `DELETE` sans validation d’un jeton anti-contrefaçon peut être vulnérable aux attaques de falsification de requête intersites. Une attaque de falsification de requête intersite peut envoyer des demandes malveillantes d’un utilisateur authentifié à votre contrôleur ASP.NET Core MVC. |
| CA5392 | [CA5392 utiliser l’attribut DefaultDllImportSearchPaths pour les P/Invoke](../code-quality/ca5392.md) | Par défaut, les fonctions P/Invoke utilisant <xref:System.Runtime.InteropServices.DllImportAttribute> sondent un certain nombre de répertoires, y compris le répertoire de travail actuel de la bibliothèque à charger. Il peut s’agir d’un problème de sécurité pour certaines applications, conduisant à un piratage de DLL. |
| CA5393 | [CA5393 n’utilise pas de valeur DllImportSearchPath dangereuse](../code-quality/ca5393.md) | Il peut y avoir une DLL malveillante dans les répertoires de recherche et les répertoires de l’assembly de la DLL par défaut. Ou, selon l’emplacement à partir duquel votre application est exécutée, il peut y avoir une DLL malveillante dans le répertoire de l’application. |
| CA5394 | [CA5394 n’utilisent pas le caractère aléatoire non sécurisé](../code-quality/ca5394.md) | L’utilisation d’un générateur de nombres pseudo-aléatoires faiblement faible peut permettre à une personne malveillante de prédire quelle valeur sensible à la sécurité sera générée. |
| CA5395 | [CA5395 d’échec de HttpVerb pour les méthodes d’action](../code-quality/ca5395.md) | Toutes les méthodes d’action qui créent, modifient, suppriment ou modifient des données doivent être protégées avec l’attribut anti-contrefaçon des attaques de falsification de requête intersite. L’exécution d’une opération d’extraction doit être une opération sécurisée qui n’a pas d’effets secondaires et qui ne modifie pas vos données persistantes. |
| CA5396 | [CA5396 définir HttpOnly sur true pour HttpCookie](../code-quality/ca5396.md) | En guise de mesure de défense en profondeur, vérifiez que les cookies HTTP sensibles à la sécurité sont marqués comme HttpOnly. Cela indique que les navigateurs Web doivent autoriser les scripts à accéder aux cookies. Les scripts malveillants injectés sont un moyen courant de voler des cookies. |
| CA5397 | [CA5397 : Ne pas utiliser de valeurs SslProtocols dépréciées](../code-quality/ca5397.md) | TLS (Transport Layer Security) sécurise la communication entre les ordinateurs, le plus souvent avec le protocole HTTPs (Hypertext Transfer Protocol Secure). Les anciennes versions de protocole TLS sont moins sécurisées que TLS 1,2 et TLS 1,3 et sont plus susceptibles d’avoir de nouvelles vulnérabilités. Évitez les anciennes versions de protocole pour réduire les risques. |
| CA5398 | [CA5398 : Éviter les valeurs SslProtocols codées en dur](../code-quality/ca5398.md) | TLS (Transport Layer Security) sécurise la communication entre les ordinateurs, le plus souvent avec le protocole HTTPs (Hypertext Transfer Protocol Secure). Les versions de protocole TLS 1,0 et TLS 1,1 sont dépréciées, tandis que TLS 1,2 et TLS 1,3 sont à jour. À l’avenir, TLS 1,2 et TLS 1,3 peuvent être déconseillés. Pour vous assurer que votre application reste sécurisée, évitez de coder en dur une version de protocole. |
| CA5399 | [CA5399 désactive la vérification de la liste de révocation de certificats HttpClient](../code-quality/ca5399.md) | Un certificat révoqué n’est plus approuvé. Elle peut être utilisée par des attaquants qui transmettent des données malveillantes ou dérobent des données sensibles dans la communication HTTPs. |
| Ca5400 | [Ca5400 Vérifiez que la vérification de la liste de révocation de certificats HttpClient n’est pas désactivée](../code-quality/ca5400.md) | Un certificat révoqué n’est plus approuvé. Elle peut être utilisée par des attaquants qui transmettent des données malveillantes ou dérobent des données sensibles dans la communication HTTPs. |
| CA5401 | [CA5401 n’utilisez pas CreateEncryptor avec un vecteur d’aide non défini par défaut](../code-quality/ca5401.md) | Le chiffrement symétrique doit toujours utiliser un vecteur d’initialisation non renouvelable pour empêcher les attaques de dictionnaire. |
| CA5402 | [CA5402 utiliser CreateEncryptor avec le vecteur d’aide par défaut](../code-quality/ca5402.md) | Le chiffrement symétrique doit toujours utiliser un vecteur d’initialisation non renouvelable pour empêcher les attaques de dictionnaire. |
| CA5403 | [CA5403 : Ne pas coder en dur le certificat](../code-quality/ca5403.md) | Le `data` `rawData` paramètre ou d’un <xref:System.Security.Cryptography.X509Certificates.X509Certificate> <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructeur ou est codé en dur. |
| IL3000 | [IL3000 éviter d’accéder au chemin d’accès du fichier d’assembly lors de la publication sous la forme d’un fichier unique](../code-quality/il3000.md) | Évitez d’utiliser le chemin d’accès au fichier d’assembly lors de la publication sous la forme d’un fichier unique |
| IL3001 | [IL3001 éviter d’accéder au chemin d’accès du fichier d’assembly lors de la publication en tant que fichier unique](../code-quality/il3001.md) | Évitez d’accéder au chemin d’accès du fichier d’assembly lors de la publication sous la forme d’un fichier unique |
