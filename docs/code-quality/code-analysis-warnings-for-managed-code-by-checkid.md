---
title: Avertissements d'analyse du code pour le code managé par CheckId
ms.date: 04/18/2019
ms.topic: reference
f1_keywords:
- CA1000
- CA1001
- CA1002
- CA1003
- CA1004
- CA1005
- CA1006
- CA1007
- CA1008
- CA1009
- CA1010
- CA1011
- CA1012
- CS1013
- CS1014
- CA1016
- CA1017
- CA1018
- CA1019
- CA1020
- CA1021
- CA1022
- CA1023
- CA1024
- CS1025
- CA1026
- CA1027
- CA1028
- CA1029
- CA1030
- CA1031
- CA1032
- CA1033
- CA1034
- CA1035
- CA1036
- CA1037
- CA1038
- CA1039
- CA1040
- CA1041
- CA1042
- CA1043
- CA1044
- CA1045
- CA1046
- CA1047
- CA1048
- CA1049
- CA1050
- CA1051
- CA1052
- CA1053
- CA1054
- CA1055
- CA1056
- CA1057
- CA1058
- CA1059
- CA1060
- CA1061
- CA1062
- CA1063
- CA1064
- CA1065
- CA1068
- CA1200
- CA1300
- CA1301
- CA1302
- CA1303
- CA1304
- CA1305
- CA1306
- CA1307
- CA1308
- CA1309
- CA1400
- CA1401
- CA1402
- CA1403
- CA1404
- CA1405
- CA1406
- CA1407
- CA1408
- CA1409
- CA1410
- CA1411
- CA1412
- CA1413
- CA1414
- CA1415
- CA1500
- CA1501
- CA1502
- CA1503
- CA1504
- CA1505
- CA1506
- CA1507
- CA1600
- CA1601
- CA1700
- CA1701
- CA1702
- CA1703
- CA1704
- CA1707
- CA1708
- CA1709
- CA1710
- CA1711
- CA1712
- CA1713
- CA1714
- CA1715
- VA1716
- CA1717
- CA1719
- CA1720
- CA1721
- CA1722
- CA1723
- CA1724
- CA1725
- CA1726
- CA1727
- CA1728
- CA1729
- CA1730
- CA1800
- CA1801
- CA1802
- CA1803
- CA1804
- CA1806
- CA1809
- CA1810
- CA1811
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
- CA2007
- CA2100
- CA2101
- CA2102
- CA2103
- CA2104
- CA2105
- CA2106
- CA2107
- CA2108
- CA2109
- CA2110
- CA2111
- CA2112
- CA2114
- CA2115
- CA2116
- CA2117
- CA2118
- CA2119
- CA2120
- CA2121
- CA2122
- CA2123
- CA2124
- CA2126
- CA2127
- CA2128
- CA2129
- CA2130
- CA2131
- CA2132
- CA2133
- CA2134
- CA2135
- CA2136
- CA2137
- CA2138
- CA2139
- CA2140
- CA2141
- CA2142
- CA2143
- CA2144
- CA2145
- CA2146
- CA2147
- CA2148
- CA2149
- CA2150
- CA2151
- CA2200
- CA2201
- CA2202
- CA2204
- CA2205
- CA2207
- CA2208
- CA2210
- CA2211
- CA2212
- CA2213
- CA2214
- CA2215
- CA2216
- CA2217
- CA2218
- CA2219
- CA2220
- CA2221
- CA2222
- CA2223
- CA2224
- CA2225
- CA2226
- CA2228
- CA2229
- CA2227
- CA2230
- CA2231
- CA2232
- CA2233
- CA2234
- CA2235
- CA2236
- CA2237
- CA2238
- CA2239
- CA2240
- CA2241
- CA2242
- CA2243
- CA5122
ms.assetid: 5cb221f6-dc59-4abf-9bfa-adbd6f907f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6ac6fccb69770c003f21875e5ab3809c2d6415b4
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305882"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Avertissements d’analyse du code pour le code managé par CheckId

Le tableau suivant répertorie les avertissements d'analyse du code pour le code managé par l'identificateur CheckId de l'avertissement.

| CheckId | Warning | Description |
|---------| - | - |
| CA1000 | @NO__T 0CA1000 : Ne pas déclarer de membres statiques sur des types génériques @ no__t-0 | Lorsqu’un membre statique d’un type générique est appelé, l’argument de type doit être spécifié pour le type. Lorsqu’un membre d’instance générique qui ne prend pas en charge l’inférence est appelé, l’argument de type doit être spécifié pour le membre. Dans ces deux cas, la syntaxe permettant de spécifier l’argument de type est différente et peut être facilement confondue. |
| CA1001 | [CA1001 : Les types qui possèdent des champs supprimables doivent être supprimables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Une classe déclare et implémente un champ d'instance qui est un type System.IDisposable, et elle n'implémente pas IDisposable. Une classe qui déclare un champ IDisposable possède indirectement une ressource non managée et doit implémenter l'interface IDisposable. |
| CA1002 | @NO__T 0CA1002 : Ne pas exposer les listes génériques @ no__t-0 | System.Collections.Generic.List < (de \<(T >) >) est une collection générique qui est conçue pour les performances, pas l’héritage. Par conséquent, la liste ne contient aucun membre virtuel. Les collections génériques qui sont conçues pour l'héritage doivent être exposées à la place. |
| CA1003 | @NO__T 0CA1003 : Utiliser les instances du gestionnaire d’événements génériques @ no__t-0 |Un type contienne un délégué qui retourne void, dont la signature contient deux paramètres (le premier est un objet et le second est un type pouvant être assigné à EventArgs), et l’assembly conteneur cible Microsoft .NET Framework 2.0. |
| CA1004 | @NO__T 0CA1004 : Les méthodes génériques doivent fournir le paramètre de type @ no__t-0 | L’inférence désigne la manière dont l’argument de type d’une méthode générique est déterminé par le type d’argument passé à la méthode, au lieu d’utiliser la spécification explicite de l’argument de type. Pour activer l’inférence, la signature de paramètre d’une méthode générique doit contenir un paramètre du même type que le paramètre de type de la méthode. Dans ce cas, il n’est pas nécessaire de spécifier l’argument de type. Lors de l'utilisation de l'inférence pour tous les paramètres de type, la syntaxe d'appel aux méthodes d'instance génériques et non génériques est identique. Cela simplifie l'utilisation des méthodes génériques. |
| CA1005 | @NO__T 0CA1005 : Éviter les paramètres excessifs sur les types génériques @ no__t-0 | Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type. Il est généralement évident avec un paramètre de type, comme dans la liste\<T > et dans certains cas ayant deux paramètres de type, comme dans Dictionary\<TKey, TValue >. Cependant, s’il existe plus de deux paramètres de type, la difficulté devient trop grande pour la plupart des utilisateurs. |
| CA1006 | @NO__T 0CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre @ no__t-0 | Un argument de type imbriqué est un argument de type qui est également un type générique. Pour appeler un membre dont la signature contient un argument de type imbriqué, l’utilisateur doit instancier un type générique et passer ce type au constructeur d’un deuxième type générique. La procédure et la syntaxe requises sont complexes et doivent être évitées. |
| CA1007 |@NO__T 0CA1007 : Utilisez des génériques là où @ no__t-0 est approprié | Une méthode visible de l'extérieur contient un paramètre de référence de type System.Object. L'utilisation d'une méthode générique autorise le passage de tous les types, soumis à des contraintes, dans la méthode sans cast préalable du type vers le type de paramètre de référence. |
| CA1008 | @NO__T 0CA1008 : Les enums doivent avoir la valeur zéro @ no__t-0 | La valeur par défaut d'une énumération non initialisée, comme d'autres types valeur, est zéro. Une énumération attribuée sans indicateur doit définir un membre de valeur zéro afin que la valeur par défaut soit une valeur valide de l'énumération. Si une énumération à laquelle l'attribut FlagsAttribute est appliqué définit un membre de valeur zéro, son nom doit être "None" pour indiquer qu'aucune valeur n'a été définie dans l'énumération. |
| CA1009 | @NO__T 0CA1009 : Déclarer les gestionnaires d’événements correctement @ no__t-0 | Les méthodes du gestionnaire d'événements acceptent deux paramètres. Le premier est de type System.Object et se nomme "sender". Il s'agit de l'objet qui déclenche l'événement. Le deuxième paramètre est de type System.EventArgs et se nomme "e". Il s'agit des données qui sont associées à l'événement. Les méthodes du gestionnaire d'événements ne doivent pas retourner de valeur ; dans le langage de programmation C#, ceci est indiqué par le type de retour void. |
| CA1010 | @NO__T 0CA1010 : Les collections doivent implémenter l’interface générique @ no__t-0 | Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. La collection peut être ensuite utilisée pour remplir des types de collection génériques. |
| CA1011 |@NO__T 0CA1011 : Envisagez de passer des types de base en tant que paramètres @ no__t-0 | Lorsqu’un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu’argument correspondant à la méthode. Si les fonctionnalités supplémentaires fournies par le type de paramètre dérivé ne sont pas requises, l'utilisation du type de base permet une exploitation plus large de la méthode. |
| CA1012 | @NO__T 0CA1012 : Les types abstraits ne doivent pas avoir de constructeurs @ no__t-0 | Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés. Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte. |
| CA1013 | @NO__T 0CA1013 : Surchargez l’opérateur égal lors de la surcharge de l’opérateur Add et Subtract @ no__t-0 | Un type public ou protégé implémente les opérateurs d'addition ou de soustraction sans implémenter l'opérateur d'égalité. |
| CA1014 | @NO__T 0CA1014 : Marquer les assemblys avec CLSCompliantAttribute @ no__t-0 | La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Un design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>. Si cet attribut n'est pas présent sur un assembly, l'assembly n'est pas conforme. |
| CA1016 | @NO__T 0CA1016 : Marquer les assemblys avec AssemblyVersionAttribute @ no__t-0 | .NET utilise le numéro de version pour identifier de manière unique un assembly et pour établir une liaison aux types dans des assemblys avec nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites. |
| CA1017 | @NO__T 0CA1017 : Marquer les assemblys avec ComVisibleAttribute @ no__t-0 |ComVisibleAttribute détermine comment les clients COM accèdent à du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. La visibilité COM peut être définie pour l'assembly en entier, puis être substituée pour des types et des membres de type individuels. Si cet attribut n'est pas présent, les clients COM peuvent voir le contenu de l'assembly. |
| CA1018 | @NO__T 0CA1018 : Marquer les attributs avec AttributeUsageAttribute @ no__t-0 | Lorsque vous définissez un attribut personnalisé, marquez-le à l'aide d'AttributeUsageAttribute pour indiquer où l'attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. |
| CA1019 | @NO__T 0CA1019 : Définir des accesseurs pour les arguments d’attribut @ no__t-0 | Les attributs peuvent définir des arguments obligatoires qui doivent être spécifiés lorsque vous appliquez l’attribut à une cible. Ceux-ci sont également appelés arguments positionnels parce qu’ils sont fournis aux constructeurs d’attributs en tant que paramètres positionnels. Pour chaque argument obligatoire, l’attribut doit également fournir une propriété en lecture seule correspondante afin que la valeur de l’argument puisse être récupérée au moment de l’exécution. Les attributs peuvent également définir des arguments facultatifs, qui sont également appelés arguments nommés. Ces arguments sont fournis aux constructeurs d’attributs par noms et doivent disposer d’une propriété en lecture/écriture correspondante. |
| CA1020 | @NO__T 0CA1020 : Évitez les espaces de noms avec peu de types @ no__t-0 | Assurez-vous que chacun de vos espaces de noms bénéficie d'une organisation logique, et qu'une raison valide justifie le placement des types dans un espace de noms peu rempli. |
| CA1021 | @NO__T 0CA1021 : Évitez les paramètres out @ no__t-0 | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Par ailleurs, la différence entre les paramètres out et ref est généralement peu comprise. |
| CA1023 | @NO__T 0CA1023 : Les indexeurs ne doivent pas être multidimensionnels @ no__t-0 | Les indexeurs, c'est-à-dire les propriétés indexées, doivent utiliser un index unique. Les indexeurs multidimensionnels peuvent considérablement diminuer la facilité d'utilisation de la bibliothèque. |
| CA1024 | @NO__T 0CA1024 : Utilisez les propriétés quand @ no__t-0 est approprié | Le nom d'une méthode publique ou protégée commence par « Get », n'accepte aucun paramètre et retourne une valeur qui n'est pas un tableau. La méthode est susceptible de devenir une propriété. |
| CA1025 | @NO__T 0CA1025 : Remplacer les arguments répétitifs par un tableau de paramètres @ no__t-0 | Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et lorsque les arguments variables sont de même type ou peuvent être passés comme étant de même type. |
| CA1026 | @NO__T 0CA1026 : Les paramètres par défaut ne doivent pas être utilisés @ no__t-0 | Les méthodes qui utilisent des paramètres par défaut sont autorisées dans le cadre de la spécification de langage commun CLS (Common Language Specification) ; toutefois, cette spécification permet aux compilateurs d'ignorer les valeurs assignées à ces paramètres. Pour préserver le comportement souhaité d'un langage de programmation à l'autre, les méthodes qui utilisent des paramètres par défaut doivent être remplacées par des surcharges de méthode qui fournissent les paramètres par défaut. |
| CA1027 |@NO__T 0CA1027 : Marquer les enums avec FlagsAttribute @ no__t-0 | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Appliquez FlagsAttribute à une énumération lorsque ses constantes nommées peuvent être combinées de manière pertinente. |
| CA1028 | @NO__T 0CA1028 : Le stockage enum doit être Int32 @ no__t-0 | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le type de données System.Int32 est utilisé pour stocker la valeur de constante. Bien que vous puissiez modifier ce type sous-jacent, ce n'est ni obligatoire, ni recommandé dans la plupart des scénarios. |
| CA1030 | @NO__T 0CA1030 : Utiliser des événements quand @ no__t-0 est approprié |Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Si une méthode est appelée en réponse à une modification d'état clairement définie, la méthode doit être appelée par un gestionnaire d'événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode. |
| CA1031 | @NO__T 0CA1031 : Ne pas intercepter les types d’exception générale @ no__t-0 | Les exceptions générales ne doivent pas être interceptées. Interceptez une exception plus spécifique ou levez à nouveau l'exception générale en tant que dernière instruction dans le bloc catch. |
| CA1032 |@NO__T 0CA1032 : Implémenter des constructeurs d’exception standard @ no__t-0 | Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. |
| CA1033 | @NO__T 0CA1033 : Les méthodes d’interface doivent pouvoir être appelées par les types enfants @ no__t-0 | Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom. |
| CA1034 | @NO__T 0CA1034 : Les types imbriqués ne doivent pas être visibles @ no__t-0 | Un type imbriqué représente un type déclaré dans la portée d'un autre type. Les types imbriqués sont utiles pour encapsuler les détails de l'implémentation privée du type conteneur. Utilisés à cette fin, les types imbriqués ne doivent pas être visibles de l'extérieur. |
| CA1035 | @NO__T 0CA1035 : Les implémentations ICollection ont des membres fortement typés @ no__t-0 | Cette règle requiert que les implémentations ICollection fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d’effectuer un cast d’arguments en type Object lorsqu’ils utilisent les fonctionnalités fournies par l’interface. Cette règle suppose que le type qui implémente ICollection procède ainsi pour gérer une collection d'instances d'un type plus fort qu'Object. |
| CA1036 | @NO__T 0CA1036 : Substituer les méthodes sur les types comparables @ no__t-0 |Un type public ou protégé implémente l'interface System.IComparable. Il ne substitue pas Object.Equals, ni ne surcharge l'opérateur égal à, différent de, inférieur à ou supérieur à propre au langage. |
| CA1038 | @NO__T 0CA1038 : Les énumérateurs doivent être fortement typés @ no__t-0 | Cette règle requiert que les implémentations IEnumerator fournissent également une version fortement typée de la propriété Current afin que les utilisateurs ne soient pas tenus d'effectuer un cast de la valeur de retour en type fort lorsqu'ils utilisent les fonctionnalités fournies par l'interface. |
| CA1039 | @NO__T 0CA1039 : Les listes sont fortement typées @ no__t-0 | Cette règle requiert que les implémentations IList fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d’effectuer un cast d’arguments en type System.Object lorsqu’ils utilisent les fonctionnalités fournies par l’interface. |
| CA1040 |@NO__T 0CA1040 : Éviter les interfaces vides @ no__t-0 | Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit aucun membre ; par conséquent, elle ne définit aucun contrat pouvant être implémenté. |
| CA1041 | @NO__T 0CA1041 : Fournir le message ObsoleteAttribute @ no__t-0 | Un type ou un membre est marqué avec un attribut System.ObsoleteAttribute dont la propriété ObsoleteAttribute.Message n'est pas spécifiée. Lorsqu'un type ou membre marqué avec ObsoleteAttribute est compilé, la propriété Message de l'attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. |
| CA1043 | @NO__T 0CA1043 : Utiliser un argument de chaîne ou intégral pour les indexeurs @ no__t-0 | Les indexeurs (c'est-à-dire les propriétés indexées) doivent utiliser des types intégral ou chaîne pour l'index. Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d'utilisation de la bibliothèque. L'utilisation du type Object doit se restreindre aux cas où le type intégral ou de chaîne spécifique ne peut pas être spécifié au moment du design. |
| CA1044 | @NO__T 0CA1044 : Les propriétés ne doivent pas être en écriture seule @ no__t-0 | Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. Le fait de permettre à un utilisateur de définir une valeur et l'empêcher ensuite de la consulter n'offre aucune garantie de sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité. |
| CA1045 |@NO__T 0CA1045 : Ne pas passer de types par référence @ no__t-0 | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Les architectes de bibliothèque qui se contentent de concevoir pour un public général ne doivent pas s’attendre à ce que les utilisateurs maîtrisent le travail avec les paramètres `out` ou `ref`. |
| CA1046 | @NO__T 0CA1046 : Ne pas surcharger l’opérateur égal à sur les types référence @ no__t-0 | Pour les types référence, l’implémentation par défaut de l’opérateur d’égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet. |
| CA1047 |@NO__T 0CA1047 : Ne pas déclarer les membres protégés dans les types sealed @ no__t-0 | Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, les types sealed ne peuvent pas être hérités, ce qui signifie que les méthodes protégées sur les types sealed ne peuvent pas être appelées. |
| CA1048 | @NO__T 0CA1048 : Ne pas déclarer les membres virtuels dans les types sealed @ no__t-0 | Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, un type sealed ne peut pas être hérité. Une méthode virtuelle sur un type sealed est alors sans signification. |
| CA1049 | @NO__T 0CA1049 : Les types qui possèdent des ressources natives doivent être supprimables @ no__t-0 | Les types qui allouent des ressources non managées doivent implémenter IDisposable pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui les détiennent. |
| CA1050 | @NO__T 0CA1050 : Déclarer des types dans des espaces de noms @ no__t-0 | Les types sont déclarés au sein d'espaces de noms pour empêcher des collisions de dénomination, ainsi qu'en guise que méthode d'organisation de types connexes au sein d'une hiérarchie d'objets. |
| CA1051 | @NO__T 0CA1051 : Ne pas déclarer les champs d’instance visibles @ no__t-0 | Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent être privés ou internes, et doivent être exposés au moyen de propriétés. |
| CA1052 | @NO__T 0CA1052 : Les types de conteneurs statiques doivent être sealed @ no__t-0 | Un type public ou protégé contient uniquement des membres statiques et n'est pas déclaré avec le modificateur sealed (Référence C#) (NotInheritable). Un type qui n'est pas destiné à être hérité doit être marqué avec le modificateur sealed pour empêcher son utilisation en tant que type de base. |
| CA1053 |@NO__T 0CA1053 : Les types de conteneurs statiques ne doivent pas avoir de constructeurs @ no__t-0 | Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé. Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type. La surcharge de chaîne doit appeler la surcharge d’URI (Uniform Resource Identifier) à l’aide de l’argument de chaîne pour des raisons de sécurité. |
| CA1054 | @NO__T 0CA1054 : Les paramètres d’URI ne doivent pas être des chaînes @ no__t-0 | Si une méthode accepte une représentation sous forme de chaîne d'un URI, une surcharge correspondante qui accepte une instance de la classe URI doit être fournie ; elle-même fournit ces services de manière sûre et sécurisée. |
| CA1055 | @NO__T 0CA1055 : Les valeurs de retour URI ne doivent pas être des chaînes @ no__t-0 | Cette règle considère que la méthode retourne un URI. Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1056 | @NO__T 0CA1056 : Les propriétés URI ne doivent pas être des chaînes @ no__t-0 | Cette règle considère que la propriété représente un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1057 | @NO__T 0CA1057 : Les surcharges d’URI de chaîne appellent les surcharges de System. Uri @ no__t-0 | Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d'un paramètre de chaîne par un paramètre System.Uri. La surcharge qui accepte le paramètre de chaîne n'appelle pas la surcharge qui accepte le paramètre URI. |
| CA1058 | @NO__T 0CA1058 : Les types ne doivent pas étendre certains types de base](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | Un type visible de l'extérieur étend certains types de base. Utilisez l'une des solutions de remplacement. |
| CA1059 |@NO__T 0CA1059 : Les membres ne doivent pas exposer certains types concrets @ no__t-0 | Un type concret est un type qui présente une implémentation complète et, par conséquent, peut être instancié. Pour permettre une utilisation généralisée du membre, remplacez le type concret par l'interface suggérée. |
| CA1060 | @NO__T 0CA1060 : Déplacer les P/Invoke vers une classe NativeMethods @ no__t-0 | Les méthodes d'appel de code non managé, telles que celles qui sont marquées avec l'attribut System.Runtime.InteropServices.DllImportAttribute, ou les méthodes définies à l'aide du mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], accèdent à du code non managé. Ces méthodes doivent être de la classe NativeMethods, SafeNativeMethods ou UnsafeNativeMethods. |
| CA1061 |@NO__T 0CA1061 : Ne pas masquer les méthodes de la classe de base @ no__t-0 | Une méthode dans un type de base est masquée par une méthode portant le même nom dans un type dérivé, lorsque la signature de paramètre de la méthode dérivée diffère uniquement par les types qui sont dérivés plus faiblement que les types correspondants dans la signature de paramètre de la méthode de base. |
| CA1062 | @NO__T 0CA1062 : Valider les arguments des méthodes publiques @ no__t-0 | Tous les arguments de référence passés aux méthodes visibles de l’extérieur doivent être vérifiés pour voir s’ils ont la valeur null. |
| CA1063 | @NO__T 0CA1063 : Implémenter IDisposable correctement @ no__t-0 | Tous les types IDisposable doivent implémenter le modèle Dispose correctement. |
| CA1064 | @NO__T 0CA1064 : Les exceptions doivent être publiques @ no__t-0 | Une exception interne est uniquement visible à l'intérieur de sa propre portée interne. Lorsque l'exception se situe en dehors de la portée interne, seule l'exception de base peut être utilisée pour intercepter l'exception. Si l’exception interne est héritée de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, le code externe n’aura pas d’informations suffisantes pour savoir que faire avec l’exception. |
| CA1065 | @NO__T 0CA1065 : Ne levez pas d’exceptions dans des emplacements inattendus @ no__t-0 | Une méthode dont l'objet n'est pas de lever des exceptions lève une exception. |
| CA1068 | @NO__T 0CA1068 : Les paramètres CancellationToken doivent être au dernier @ no__t-0 | Une méthode a un paramètre CancellationToken qui n’est pas le dernier paramètre. |
| CA1200 | @NO__T 0CA1200 : Évitez d’utiliser des balises CREF avec un préfixe @ no__t-0 | L’attribut [cref](https://docs.microsoft.com/dotnet/csharp/programming-guide/xmldoc/cref-attribute) dans une balise de documentation XML signifie « référence du code ». Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété. Évitez d’utiliser des balises `cref` avec des préfixes, car cela empêche le compilateur de vérifier les références. Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations. |
| CA1300 | @NO__T 0CA1300 : Spécifiez MessageBoxOptions @ no__t-0 | Pour afficher correctement une boîte de message pour les cultures qui utilisent un sens de lecture de droite à gauche, les membres RightAlign et RtlReading de l'énumération MessageBoxOptions doivent être passés à la méthode Show. |
| CA1301 | @NO__T 0CA1301 : Éviter les accélérateurs en double @ no__t-0 | Une touche d'accès rapide, également connue sous le nom d'accélérateur, autorise l'accès à un contrôle par le biais du clavier, à l'aide de la touche ALT. Lorsque plusieurs contrôles ont des clés d’accès en double, le comportement de la clé d’accès n’est pas bien défini. |
| CA1302 | @NO__T 0CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux @ no__t-0 | L’énumération System.Environment.SpecialFolder contient des membres qui font référence à des dossiers système spéciaux. Les emplacements de ces dossiers peuvent avoir des valeurs distinctes selon le système d'exploitation ; l'utilisateur peut modifier certains des emplacements, et ces derniers sont localisés. La méthode Environment.GetFolderPath retourne les emplacements associés à l'énumération Environment.SpecialFolder, localisés et appropriés pour l'ordinateur en cours d'exécution. |
| CA1303 | @NO__T 0CA1303 : Ne pas passer de littéraux en tant que paramètres localisés @ no__t-0 | Une méthode visible de l’extérieur passe un littéral de chaîne en tant que paramètre à une méthode ou un constructeur .NET, et cette chaîne doit être localisable. |
| CA1304 | @NO__T 0CA1304 : Spécifier CultureInfo @ no__t-0 | Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo. Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1305 | @NO__T 0CA1305 : Spécifier IFormatProvider @ no__t-0 | Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider. Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1306 | @NO__T 0CA1306 : Définir les paramètres régionaux pour les types de données @ no__t-0 | Les paramètres régionaux déterminent des éléments de présentation des données spécifiques à la culture, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l'ordre de tri. Lorsque vous créez un DataTable ou un DataSet, vous devez définir les paramètres régionaux explicitement. |
| CA1307 | @NO__T 0CA1307 : Spécifier StringComparison @ no__t-0 | Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison. |
| CA1308 |@NO__T 0CA1308 : Normaliser les chaînes en majuscules @ no__t-0 | Les chaînes doivent être normalisées en majuscules. En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller-retour. |
| CA1309 | @NO__T 0CA1309 : Utiliser StringComparison @ no__t-0 | Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison. En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable. |
| CA1400 | @NO__T 0CA1400 : Les points d’entrée P/Invoke doivent exister @ no__t-0 |Une méthode publique ou protégée est marquée avec l'attribut System.Runtime.InteropServices.DllImportAttribute. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. |
| CA1401 | @NO__T 0CA1401 : Les P/Invoke ne doivent pas être visibles @ no__t-0 | Une méthode publique ou protégée dans un type public a l'attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). De telles méthodes ne doivent pas être exposées. |
| CA1402 |@NO__T 0CA1402 : Éviter les surcharges dans les interfaces COM visibles @ no__t-0 | Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom. Les surcharges suivantes sont renommées de manière unique par l'ajout d'un trait de soulignement (_) au nom et d'un entier qui correspond à l'ordre de déclaration de la surcharge. |
| CA1403 | @NO__T 0CA1403 : Les types de disposition automatique ne doivent pas être visibles par COM @ no__t-0 | Un type valeur visible par COM est marqué avec l'attribut System.Runtime.InteropServices.StructLayoutAttribute qui a la valeur LayoutKind.Auto. La disposition de ces types peut changer entre les versions de .NET, ce qui entraîne l’arrêt des clients COM qui attendent une disposition spécifique. |
| CA1404 | @NO__T 0CA1404 : Appeler GetLastError immédiatement après P/Invoke @ no__t-0 | Un appel est effectué à la méthode Marshal.GetLastWin32Error ou l’équivalent [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] fonction GetLastError et l’appel immédiatement antérieur n’est pas un système d’exploitation appeler la méthode. |
| CA1405 | @NO__T 0CA1405 : Les types de base de type visibles par COM doivent être visibles par COM @ no__t-0 | Un type visible par COM dérive d'un type qui n'est pas visible par COM. |
| CA1406 |@NO__T 0CA1406 : Éviter les arguments Int64 pour Visual Basic 6 clients @ no__t-0 | Les clients COM Visual Basic 6 ne peut pas accéder aux entiers de 64 bits. |
| CA1407 |@NO__T 0CA1407 : Éviter les membres statiques dans les types visibles par COM @ no__t-0 | COM ne prend pas en charge les méthodes statiques. |
| CA1408 | @NO__T 0CA1408 : N’utilisez pas AutoDual ClassInterfaceType @ no__t-0 | Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si l'attribut ClassInterfaceAttribute n'est pas spécifié, une interface de répartition uniquement est utilisée. |
| CA1409 | @NO__T 0CA1409 : Les types visibles par com doivent pouvoir être créés @ no__t-0 |Un type référence marqué spécifiquement comme visible par des clients COM contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre). Les clients COM ne peuvent pas créer de type sans constructeur public par défaut. |
| CA1410 | @NO__T 0CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance @ no__t-0 | Un type déclare une méthode marquée avec l'attribut System.Runtime.InteropServices.ComRegisterFunctionAttribute, mais ne déclare pas une méthode marquée avec l'attribut System.Runtime.InteropServices.ComUnregisterFunctionAttribute, ou vice versa. |
| CA1411 | @NO__T 0CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles @ no__t-0 | Une méthode marquée avec l'attribut System.Runtime.InteropServices.ComRegisterFunctionAttribute ou System.Runtime.InteropServices.ComUnregisterFunctionAttribute est visible de l'extérieur. |
| CA1412 | @NO__T 0CA1412 : Marquer les interfaces ComSource comme IDispatch @ no__t-0 | Un type est marqué avec l'attribut System.Runtime.InteropServices.ComSourceInterfacesAttribute et au moins une des interfaces spécifiées n'est pas marquée avec l'attribut System.Runtime.InteropServices.InterfaceTypeAttribute ayant la valeur ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | @NO__T 0CA1413 : Évitez les champs non publics dans les types valeur visibles par COM @ no__t-0 | Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM. Passez en revue le contenu des champs pour voir les informations qui ne doivent pas être exposées, sinon vous aurez une conception imprévue ou des conséquences sur la sécurité. |
| CA1414 | @NO__T 0CA1414 : Marquer les arguments P/Invoke booléens avec MarshalAs @ no__t-0 | Le type de données booléen contient plusieurs représentations dans le code non managé. |
| CA1415 | @NO__T 0CA1415 : Déclarer correctement les P/Invoke @ no__t-0 | Cette règle recherche des déclarations de méthode d'appel de code non managé qui ciblent des fonctions [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] présentant un pointeur vers un paramètre de structure OVERLAPPED, et le paramètre managé correspondant n'est pas un pointeur vers une structure System.Threading.NativeOverlapped. |
| CA1500 | @NO__T 0CA1500 : Les noms de variables ne doivent pas correspondre aux noms de champs @ no__t-0 | Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant, ce qui entraîne des erreurs. |
| CA1501 | @NO__T 0CA1501 : Éviter l’héritage excessif @ no__t-0 | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| CA1502 | @NO__T 0CA1502 : Éviter la complexité excessive @ no__t-0 | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| CA1504 | @NO__T 0CA1504 : Examiner les noms de champs trompeurs @ no__t-0 | Le nom d’un champ d’instance commence par « s_ » ou le nom d’un champ statique de (Shared en Visual Basic) commence par « m_ ». |
| CA1505 | @NO__T 0CA1505 : Éviter le code non gérable @ no__t-0 | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| CA1506 |@NO__T 0CA1506 : Éviter un couplage de classe excessif @ no__t-0 | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| CA1600 | @NO__T 0CA1600 : Ne pas utiliser la priorité de processus inactif @ no__t-0 | N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille. |
| CA1601 | @NO__T 0CA1601 : N’utilisez pas de minuteries qui empêchent les modifications de l’état d’alimentation @ no__t-0 | En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie. |
| CA1700 | @NO__T 0CA1700 : Ne nommez pas les valeurs enum’reserved' ](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture. |
| CA1701 | @NO__T 0CA1701 : La casse des mots composés de la chaîne de ressources doit être correcte @ no__t-0 | Chaque mot dans la chaîne de ressource est fractionné en jetons basés sur la casse. Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft. S'il est reconnu, le mot produit une violation de la règle. |
| CA1702 | @NO__T 0CA1702 : La casse des mots composés doit être correcte @ no__t-0 | Le nom d'un identificateur contient plusieurs mots et au moins l'un des mots semble être un mot composé qui ne présente pas une casse correcte. |
| CA1703 | @NO__T 0CA1703 : Les chaînes de ressources doivent être correctement orthographiées @ no__t-0 | Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft. |
| CA1704 | @NO__T 0CA1704 : Les identificateurs doivent être correctement orthographiés @ no__t-0 | Le nom d'un identificateur visible de l'extérieur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft. |
| CA1707 | @NO__T 0CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement @ no__t-0 | Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). Cette règle vérifie les espaces de noms, types, membres et paramètres. |
| CA1708 | @NO__T 0CA1708 : Les identificateurs doivent différer par plus que la casse @ no__t-0 | Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. |
| CA1709 | @NO__T 0CA1709 : La casse des identificateurs doit être correcte @ no__t-0 | Par convention, les noms de paramètres utilisent la casse mixte et les noms d'espaces de noms, de types et de membres utilisent la convention de casse Pascal. |
| CA1710 | @NO__T 0CA1710 : Les identificateurs doivent avoir le suffixe correct @ no__t-0 |Par convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou encore des types dérivés de ces types, présentent un suffixe associé au type de base ou à l'interface. |
| CA1711 | @NO__T 0CA1711 : Les identificateurs ne doivent pas avoir un suffixe incorrect @ no__t-0 | Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques. Les autres noms de types ne doivent pas utiliser ces suffixes réservés. |
| CA1712 | @NO__T 0CA1712 : Ne pas préfixer les valeurs d’énumération avec le nom de type @ no__t-0 | Les noms des membres de l'énumération n'ont pas pour préfixe le nom de type, car les outils de développement sont censés fournir les informations de type. |
| CA1713 | @NO__T 0CA1713 : Les événements ne doivent pas avoir le préfixe Before ou after @ no__t-0 | Le nom d'un événement commence par « Before » ou « After ». Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions. |
| CA1714 | @NO__T 0CA1714 : Les énumérations d’indicateurs doivent avoir des noms au pluriel @ no__t-0 | Une énumération publique comporte l'attribut System.FlagsAttribute et son nom ne se termine pas par « s ». Les types marqués avec FlagsAttribute ont des noms au pluriel, car l'attribut indique que plusieurs valeurs peuvent être spécifiées. |
| CA1715 | @NO__T 0CA1715 : Les identificateurs doivent avoir le préfixe @ no__t-0 | Le nom d'une interface extérieurement visible ne commence pas par un « I » majuscule. Le nom d'un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « T » majuscule. |
| CA1716 | @NO__T 0CA1716 : Les identificateurs ne doivent pas correspondre aux mots clés @ no__t-0 | Un nom d'espace de noms ou un nom de type correspond à un mot clé réservé dans un langage de programmation. Les identificateurs des espaces de noms et des types ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime. |
| CA1717 | @NO__T 0CA1717 : Seules les énumérations FlagsAttribute doivent avoir des noms au pluriel @ no__t-0 | Selon les conventions d'attribution de nom, un nom au pluriel pour une énumération indique que plusieurs valeurs de l'énumération peuvent être spécifiées simultanément. |
| CA1719 | @NO__T 0CA1719 : Les noms des paramètres ne doivent pas correspondre aux noms des membres @ no__t-0 | Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser. |
| CA1720 |@NO__T 0CA1720 : Les identificateurs ne doivent pas contenir de noms de types @ no__t-0 | Le nom d'un paramètre dans un membre extérieurement visible contient un nom de type de données, ou le nom d'un membre extérieurement visible contient un nom de type de données spécifique à une langue. |
| CA1721 | @NO__T 0CA1721 : Les noms de propriété ne doivent pas correspondre aux méthodes d’extraction @ no__t-0 |Le nom d'un membre public ou protégé commence par « Get ». Sinon, il correspond au nom d'une propriété publique ou protégée. Les méthodes et propriétés « Get » doivent porter des noms distinguant clairement leur fonction. |
| CA1722 | @NO__T 0CA1722 : Les identificateurs ne doivent pas comporter un préfixe @ no__t-0 | Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique. |
| CA1724 | @NO__T 0CA1724 : Les noms de types ne doivent pas correspondre à des espaces de noms @ no__t-0 | Les noms de types ne doivent pas correspondre aux noms des espaces de noms .NET. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque. |
| CA1725 | @NO__T 0CA1725 : Les noms de paramètres doivent correspondre à la déclaration de base @ no__t-0 | La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode. |
| CA1726 | @NO__T 0CA1726 : Utiliser les termes préférés @ no__t-0 | Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Le nom peut également inclure le terme « Indicateur » ou « Indicateurs ». |
| CA1800 | @NO__T 0CA1800 : Ne pas effectuer de cast inutilement @ no__t-0 | Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. |
| CA1801 | @NO__T 0CA1801 : Passer en revue les paramètres inutilisés @ no__t-0 | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| CA1802 |@NO__T 0CA1802 : Utilisez des littéraux quand @ no__t-0 est approprié |Un champ est déclaré statique et en lecture seule (Shared et ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), et est initialisé avec une valeur qui est calculable à la compilation. La valeur est assignée au champ ciblé étant calculable à la compilation, modifiez la déclaration const (Const en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) afin que la valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| CA1804 | @NO__T 0CA1804 : Supprimer les variables locales inutilisées @ no__t-0 | Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances. |
| CA1806 | @NO__T 0CA1806 : Ne pas ignorer les résultats de la méthode @ no__t-0 | Un nouvel objet est créé mais jamais utilisé ; ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée ; ou une méthode COM ou P/Invoke retourne un code HRESULT ou d'erreur qui n'est jamais utilisé. |
| CA1809 |@NO__T 0CA1809 : Évitez les variables locales excessives @ no__t-0 | Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ». Pour augmenter les chances que toutes les variables locales sont inscrites dans le Registre, limitez le nombre de variables locales à 64. |
| CA1810 | @NO__T 0CA1810 : Initialiser les champs statiques de type référence en ligne @ no__t-0 | Lorsqu’un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d’instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| CA1811 | @NO__T 0CA1811 : Éviter le code privé non appelé @ no__t-0 | Un membre privé ou interne (de niveau assembly) n'a pas d'appelants dans l'assembly, et n'est appelé ni par le Common Language Runtime, ni par un délégué. |
| CA1812 | @NO__T 0CA1812 : Évitez les classes internes non instanciées @ no__t-0 | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| CA1813 | @NO__T 0CA1813 : Évitez les attributs non scellés @ no__t-0 | .NET fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| CA1814 | @NO__T 0CA1814 : Préférer les tableaux en escalier à des tableaux multidimensionnels @ no__t-0 | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données. |
| CA1815 | @NO__T 0CA1815 : Remplacer Equals et l’opérateur d’égalité dans les types valeur](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| CA1816 | @NO__T 0CA1816 : Appelez GC. SuppressFinalize correctement @ no__t-0 | Une méthode qui est une implémentation de Dispose n’appelle pas de catalogue global. SuppressFinalize ; ou une méthode qui n’est pas une implémentation de Dispose appelle GC. SuppressFinalize ; ou une méthode appelle GC. SuppressFinalize et passe un élément autre que cette (Me en Visual Basic). |
| CA1819 | @NO__T 0CA1819 : Les propriétés ne doivent pas retourner des tableaux @ no__t-0 | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| CA1820 | @NO__T 0CA1820 : Tester les chaînes vides à l’aide de la longueur de chaîne @ no__t-0 | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| CA1821 | [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821-remove-empty-finalizers.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une charge supplémentaire sans aucun avantage. |
| CA1822 |@NO__T 0CA1822 : Marquer les membres comme static @ no__t-0 | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| CA1823 | @NO__T 0CA1823 : Évitez les champs privés inutilisés @ no__t-0 | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| CA1824 |@NO__T 0CA1824 : Marquer les assemblys avec NeutralResourcesLanguageAttribute @ no__t-0 | L’attribut NeutralResourcesLanguage informe le gestionnaire de ressources de la langue utilisée pour afficher les ressources d’une culture neutre pour un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| CA1825 |@NO__T 0CA1825 : Évitez les allocations de tableau de longueur nulle @ no__t-0 | L’initialisation d’un tableau de longueur zéro provoque une allocation de mémoire inutile. Utilisez plutôt l’instance de tableau vide allouée statiquement en appelant <xref:System.Array.Empty%2A?displayProperty=nameWithType>. L’allocation de mémoire est partagée entre tous les appels de cette méthode. |
| CA1900 | @NO__T 0CA1900 : Les champs de type valeur doivent être portables @ no__t-0 | Cette règle vérifie que les structures déclarées avec une disposition explicite s’aligneront correctement lorsqu’elles seront marshalées pour le code non managé sur les systèmes d’exploitation 64 bits. |
| CA1901 | @NO__T 0CA1901 : Les déclarations P/Invoke doivent être portables @ no__t-0 | Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke, puis vérifie que la taille du paramètre est correcte lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 32 bits et 64 bits. |
| CA1903 | @NO__T 0CA1903 : Utiliser uniquement l’API du Framework ciblé @ no__t-0 | Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet. |
| CA2000 | @NO__T 0CA2000 : Supprimer les objets avant de perdre l’étendue @ no__t-0 | Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée. |
| CA2001 | @NO__T 0CA2001 : Évitez d’appeler les méthodes problématiques @ no__t-0 | Un membre appelle une méthode potentiellement dangereuse ou problématique. |
| CA2002 |@NO__T 0CA2002 : Ne pas verrouiller sur les objets avec une identité faible @ no__t-0 |Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet. |
| CA2003 |@NO__T 0CA2003 : Ne pas traiter les fibres comme des threads @ no__t-0 | Un thread managé est traité comme un thread [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]. |
| CA2004 | @NO__T 0CA2004 : Supprimez les appels à GC. KeepAlive @ no__t-0 | Si vous envisagez d'utiliser SafeHandle, supprimez tous les appels à GC.KeepAlive (objet). Dans ce cas, les classes n'ont pas à appeler GC.KeepAlive. Cela suppose qu'elles n'ont pas de finaliseur mais qu'elles dépendent de SafeHandle pour finaliser le handle du système d'exploitation à leur place. |
| CA2006 | @NO__T 0CA2006 : Utiliser SafeHandle pour encapsuler les ressources natives @ no__t-0 | L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s'il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place. |
| CA2007 | @NO__T 0CA2007 : Ne pas attendre directement une tâche @ no__t-0 | Une méthode asynchrone [attend](/dotnet/csharp/language-reference/keywords/await) un <xref:System.Threading.Tasks.Task> directement. Lorsqu’une méthode asynchrone attend directement une <xref:System.Threading.Tasks.Task>, la continuation se produit dans le thread qui a créé la tâche. Ce comportement peut être coûteux en termes de performances et peut entraîner un blocage sur le thread d’interface utilisateur. Envisagez d’appeler <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> pour signaler votre intention de continuation. |
| CA2100 | @NO__T 0CA2100 : Examiner les requêtes SQL pour les vulnérabilités de sécurité @ no__t-0 | Une méthode définit la propriété System.Data.IDbCommand.CommandText à l’aide d’une chaîne générée à partir d’un argument de chaîne à la méthode. Cette règle suppose que l’argument de chaîne contient des entrées d’utilisateur. Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL. |
| CA2101 |@NO__T 0CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke @ no__t-0 | Un membre d’appel de code non managé autorise les appelants dotés d’un niveau de confiance partielle, présente un paramètre de chaîne et ne marshale pas explicitement la chaîne. Cela peut provoquer une faille de sécurité potentielle. |
| CA2102 | @NO__T 0CA2102 : Intercepter les exceptions non CLSCompliant dans les gestionnaires généraux @ no__t-0 | Un membre dans un assembly qui n'est pas marqué avec RuntimeCompatibilityAttribute ou qui est marqué avec RuntimeCompatibility(WrapNonExceptionThrows = false) contient un bloc catch qui gère System.Exception et ne contient pas de bloc catch général immédiatement après. |
| CA2103 | @NO__T 0CA2103 : Vérifier la sécurité impérative @ no__t-0 |Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active. Utilisez la sécurité de déclaration dès que possible. |
| CA2104 |@NO__T 0CA2104 : Ne déclarez pas les types référence mutables en lecture seule @ no__t-0 | Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable. Un type mutable est un type dont les données d’instance peuvent être modifiées. |
| CA2105 | @NO__T 0CA2105 : Les champs de tableau ne doivent pas être en lecture seule @ no__t-0 |Lorsque vous appliquez le modificateur en lecture seule (ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) à un champ qui contient un tableau, ce champ ne peut pas être modifié pour référencer un tableau différent. Toutefois, les éléments du tableau stockés dans un champ en lecture seule peuvent être modifiés. |
| CA2106 | @NO__T 0CA2106 : Assertions sécurisées @ no__t-0 | Une méthode déclare une autorisation et aucune vérification de sécurité n’est exécutée sur l’appelant. L’assertion d’une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter. |
| CA2107 | @NO__T 0CA2107 : Passer en revue les activités refuser et autoriser uniquement @ no__t-0 |La méthode PermitOnly et les actions de sécurité CodeAccessPermission. Deny doivent être utilisées uniquement par les personnes qui ont une connaissance approfondie de la sécurité .NET. Le code qui utilise ces actions de sécurité doit subir une révision de sécurité. |
| CA2108 | @NO__T 0CA2108 : Passer en revue la sécurité déclarative sur les types valeur @ no__t-0 | Un type valeur public ou protégé est sécurisé par l’accès aux données ou des demandes de liaison. |
| CA2109 | @NO__T 0CA2109 : Passer en revue les gestionnaires d’événements visibles @ no__t-0 | Une méthode de gestion d’événements publique ou protégée a été détectée. Les méthodes de gestion d'événements ne doivent pas être exposées sauf nécessité absolue. |
| CA2111 |@NO__T 0CA2111 : Les pointeurs ne doivent pas être visibles @ no__t-0 | Un pointeur n’est ni privé, ni interne ni en lecture seule. Un code malveillant peut modifier la valeur du pointeur, ce qui peut permettre l'accès aux emplacements arbitraires en mémoire ou provoquer des défaillances des applications ou du système. |
| CA2112 | @NO__T 0CA2112 : Les types sécurisés ne doivent pas exposer les champs @ no__t-0 | Un type public ou protégé contient des champs publics et est sécurisé par des demandes de liaison. Si un code a accès à une instance d'un type sécurisé par une demande de liaison, ce code n'a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type. |
| CA2114 | @NO__T 0CA2114 : La sécurité de la méthode doit être un sur-ensemble de type @ no__t-0 | Pour une même action, une méthode ne doit pas présenter de sécurité déclarative à la fois au niveau méthode et au niveau type. |
| CA2115 | @NO__T 0CA2115 : Appelez GC. KeepAlive quand vous utilisez des ressources natives @ no__t-0 | Cette règle détecte les erreurs susceptibles de se produire du fait qu’une ressource non managée est en cours de finalisation alors qu’elle est encore utilisée dans un code non managé. |
| CA2116 | @NO__T 0CA2116 : Les méthodes APTCA doivent uniquement appeler les méthodes APTCA @ no__t-0 |Lorsque l'attribut APTCA (AllowPartiallyTrustedCallersAttribute) est présent dans un assembly entièrement fiable, et lorsque cet assembly exécute du code dans un autre assembly qui n'autorise pas les appelants partiellement fiables, il en résulte une faille de sécurité dont l'exploitation est possible. |
| CA2117 | @NO__T 0CA2117 : Les types APTCA doivent uniquement étendre les types de base APTCA @ no__t-0 | Lorsque l'attribut APTCA est présent dans un assembly entièrement fiable, et lorsqu'un type présent dans l'assembly hérite d'un type qui n'autorise pas les appelants partiellement approuvés, il en résulte une faille de sécurité dont l'exploitation est possible. |
| CA2118 | @NO__T 0CA2118 : Passez en revue les syntaxes SuppressUnmanagedCodeSecurityAttribute @ no__t-0 |SuppressUnmanagedCodeSecurityAttribute modifie le comportement par défaut du système en matière de sécurité pour les membres qui exécutent du code non managé utilisant COM Interop ou l'appel de code non managé. Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s'accompagnent de risques substantiels pour la sécurité. |
| CA2119 | @NO__T 0CA2119 : Scellez les méthodes qui satisfont les interfaces privées @ no__t-0 | Un type public pouvant être hérité fournit une implémentation de méthode substituable d'une interface interne (Friend en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly. |
| CA2120 | @NO__T 0CA2120 : Sécuriser les constructeurs de sérialisation @ no__t-0 | Ce type possède un constructeur qui accepte un objet System.Runtime.Serialization.SerializationInfo et un objet System.Runtime.Serialization.StreamingContext (la signature du constructeur de sérialisation). Ce constructeur n’est pas sécurisé par une vérification de la sécurité, mais au moins un des constructeurs normaux dans le type est sécurisé. |
| CA2121 | @NO__T 0CA2121 : Les constructeurs statiques doivent être privés](../code-quality/ca2121-static-constructors-should-be-private.md) | Le système appelle le constructeur statique avant la création de la première instance du type ou le référencement de tout membre statique. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le système. Selon les opérations effectuées dans le constructeur, cette possibilité peut provoquer un comportement inattendu. |
| CA2122 | @NO__T 0CA2122 : N’exposez pas indirectement des méthodes avec des demandes de liaison @ no__t-0 | Un membre public ou protégé a des demandes de liaison et est appelé par un membre qui ne procède à aucune vérification de la sécurité. Une demande de liaison vérifie uniquement les autorisations de l'appelant immédiat. |
| CA2123 | @NO__T 0CA2123 : Les demandes de liaison de substitution doivent être identiques à base @ no__t-0 | Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune. Si cette règle est violée, un appelant malveillant peut ignorer la demande de liaison simplement en appelant la méthode non protégée. |
| CA2124 | @NO__T 0CA2124 : Inclure dans un wrapper les clauses finally vulnérables dans Outer try @ no__t-0 | Une méthode publique ou protégée contient un bloc try/finally. Le bloc finally semble réinitialiser l’état de sécurité et n’est lui-même placé dans aucun bloc finally. |
| CA2126 | @NO__T 0CA2126 : Les demandes de liaison de type requièrent des demandes d’héritage @ no__t-0 | Un type unsealed public est protégé par une demande de liaison et a une méthode substituable. Ni le type ni la méthode ne sont protégés par une demande d'héritage. |
| CA2127 | @NO__T 0CA2136 : Les membres ne doivent pas avoir d’annotations de transparence en conflit @ no__t-0 | Le code critique ne peut pas apparaître dans un assembly transparent à 100 pour cent. Cette règle analyse les assemblys transparents de 100 pour cent pour toutes les annotations SecurityCritical au type, champ et les niveaux de méthode. |
| CA2128 |@NO__T 0CA2147 : Les méthodes transparentes ne peuvent pas utiliser des assertions de sécurité @ no__t-0 | Cette règle analyse toutes les méthodes et les types dans un assembly qui est transparent à 100 pour cent ou mixte mi-critique et elle signale toute utilisation déclarative ou impérative d’Assert. |
| CA2129 | @NO__T 0CA2140 : Le code transparent ne doit pas faire référence à des éléments critiques de sécurité @ no__t-0 | Les méthodes marquées avec SecurityTransparentAttribute appellent des membres non publics marqués en tant que SecurityCritical. Cette règle analyse toutes les méthodes et tous les types dans un assembly qui est mi-transparent et mi-critique, et elle signale tous les appels du code transparent au code critique non public qui ne sont pas marqués comme SecurityTreatAsSafe. |
| CA2130 | @NO__T 0CA2130 : Les constantes critiques de sécurité doivent être transparentes @ no__t-0 | La mise en application de la transparence n’est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu’aucune recherche ne soit requise au moment de l’exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante. |
| CA2131 | @NO__T 0CA2131 : Les types critiques de sécurité ne peuvent pas participer à l’équivalence de type @ no__t-0 | Un type participe à l'équivalence des types et un type lui-même, ou un membre ou champ du type, est marqué à l'aide de l'attribut SecurityCriticalAttribute. Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l'équivalence de type. Lorsque le CLR détecte un tel type, il ne peut pas le charger avec une exception TypeLoadException au moment de l'exécution. En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l'équivalence de type manuellement plutôt qu'en comptant sur tlbimp et les compilateurs pour faire l'équivalence de type. |
| CA2132 | @NO__T 0CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base @ no__t-0 |Les types et les membres qui possèdent l’attribut SecurityCriticalAttribute ne peuvent pas être utilisés par le code d’application Silverlight. Les types et membres critiques de sécurité (security-critical) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight. Parce qu'une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d'une classe marqué SecurityCritical. |
| CA2133 | @NO__T 0CA2133 : Les délégués doivent être liés aux méthodes avec une transparence cohérente @ no__t-0 | Cet avertissement se déclenche sur une méthode qui lie un délégué marqué à l'aide de l'attribut SecurityCriticalAttribute à une méthode transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. L'avertissement se déclenche également sur une méthode qui lie un délégué transparent ou critique sécurisé (security-safe-critical) à une méthode critique. |
| CA2134 | @NO__T 0CA2134 : Les méthodes doivent conserver une transparence cohérente lors du remplacement des méthodes de base @ no__t-0 |Cette règle se déclenche lorsqu'une méthode marquée à l'aide de l'attribut SecurityCriticalAttribute remplace une méthode qui est transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. La règle se déclenche également lorsqu'une méthode qui est transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute remplace une méthode qui est marquée à l'aide d'un attribut SecurityCriticalAttribute. La règle est appliquée lors de la substitution d’une méthode virtuelle ou de l’implémentation d’une interface. |
| CA2135 | @NO__T 0CA2135 : Les assemblys de niveau 2 ne doivent pas contenir LinkDemands @ no__t-0 | L’utilisation de LinkDemands est déconseillée dans l’ensemble de règles de sécurité de niveau 2. Au lieu d'utiliser LinkDemands pour implémenter la sécurité au moment de la compilation JIT, marquez les méthodes, types et champs avec l'attribut SecurityCriticalAttribute. |
| CA2136 | @NO__T 0CA2136 : Les membres ne doivent pas avoir d’annotations de transparence en conflit @ no__t-0 | Les attributs de transparence sont appliqués à partir d’éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d'éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe marquée à l'aide de l'attribut SecurityCriticalAttribute ne peut pas contenir de méthode marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. |
| CA2137 | @NO__T 0CA2137 : Les méthodes transparentes doivent contenir uniquement le langage intermédiaire vérifiable @ no__t-0 | Une méthode contient du code non vérifiable ou retourne un type par référence. Cette règle se déclenche lorsque le code transparent de sécurité tente d'exécuter du code MISL (Microsoft Intermediate Language) non vérifiable. Toutefois, la règle ne contient pas de vérificateur IL (Intermediate Language) complet, et à la place utilise l’heuristique pour intercepter la plupart des violations de vérification MSIL. |
| CA2138 | @NO__T 0CA2138 : Les méthodes transparentes ne doivent pas appeler de méthodes avec l’attribut SuppressUnmanagedCodeSecurity @ no__t-0 | Une méthode transparente de sécurité appelle une méthode qui est marquée à l'aide de l'attribut SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | @NO__T 0CA2139 : Les méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions @ no__t-0 | Cette règle est déclenchée par toute méthode transparente qui essaie de gérer une exception qui endommage un processus à l'aide de l'attribut HandleProcessCorruptedStateExceptionsAttribute. Une exception qui endommage un processus est une classification d'exception CLR version 4.0 des exceptions comme AccessViolationException. L'attribut HandleProcessCorruptedStateExceptionsAttribute peut uniquement être utilisé par des méthodes critiques de sécurité et sera ignoré s'il s'applique à une méthode transparente. |
| CA2140 | @NO__T 0CA2140 : Le code transparent ne doit pas faire référence à des éléments critiques de sécurité @ no__t-0 | Un élément de code marqué à l'aide de l'attribut SecurityCriticalAttribute est critique de sécurité. Une méthode transparente ne peut pas utiliser un élément critique de sécurité. Si un type transparent essaie d'utiliser un type critique de sécurité, TypeAccessException, MethodAccessException ou FieldAccessException est déclenché. |
| CA2141 |[CA2141 : Les méthodes transparentes ne satisfont pas les LinkDemands](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Une méthode transparente de sécurité appelle une méthode dans un assembly qui n'est pas marqué à l'aide de l'attribut APTCA, ou une méthode transparente de sécurité satisfait une demande LinkDemand pour un type ou une méthode. |
| CA2142 | @NO__T 0CA2142 : Le code transparent ne doit pas être protégé avec LinkDemands @ no__t-0 | Cette règle se déclenche sur les méthodes transparentes qui requièrent l'accès de LinkDemands. Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. |
| CA2143 | @NO__T 0CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité @ no__t-0 | Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Le code transparent de sécurité doit utiliser des demandes complètes pour prendre des décisions de sécurité et le code critique sécurisé ne doit pas dépendre du code transparent pour l’exécution de ces demandes. |
| CA2144 | @NO__T 0CA2144 : Le code transparent ne doit pas charger d’assemblys à partir de tableaux d’octets @ no__t-0 | La revue de sécurité du code transparent n’est pas aussi complète que la revue de sécurité du code critique, car le code transparent ne peut pas exécuter d’actions relatives à la sécurité. Les assemblys chargés à partir d'un tableau d'octets peuvent ne pas être remarqués dans du code transparent, et ce tableau d'octets peut contenir du code critique, voire critique de sécurité, qui doit être audité. |
| CA2145 | @NO__T 0CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute @ no__t-0 | Les méthodes décorées par l'attribut SuppressUnmanagedCodeSecurityAttribute ont un LinkDemand implicite sur toute méthode qui l'appelle. Ce LinkDemand requiert que le code appelant soit critique de sécurité. Le marquage de la méthode qui utilise SuppressUnmanagedCodeSecurity avec l’attribut SecurityCriticalAttribute rend cette exigence plus évidente pour les appelants de la méthode. |
| CA2146 | @NO__T 0CA2146 : Les types doivent être au moins aussi critiques que leurs types de base et interfaces @ no__t-0 | Cette règle se déclenche lorsqu'un type dérivé a un attribut de transparence de sécurité qui n'est pas aussi critique que son type de base ou l'interface implémentée. Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées. |
| CA2147 |@NO__T 0CA2147 : Les méthodes transparentes ne peuvent pas utiliser des assertions de sécurité @ no__t-0 | Aucune autorisation suffisante n’est accordée à un code marqué comme attribut SecurityTransparentAttribute pour procéder à une assertion. |
| CA2149 | @NO__T 0CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif @ no__t-0 | Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif (par exemple, via un appel P/Invoke). Les violations de cette règle provoquent une exception MethodAccessException dans le modèle de transparence de niveau 2, et une demande complète pour le code UnmanagedCode dans le modèle de transparence de niveau 1. |
| CA2151 |@NO__T 0CA2151 : Les champs avec des types critiques doivent être critiques pour la sécurité @ no__t-0 | Pour utiliser les types critiques de sécurité, le code qui référence le type doit être critique de sécurité ou critique sécurisé. Ceci est vrai même si la référence est indirecte. Par conséquent, un champ transparent de sécurité ou critique sécurisé est trompeur, car le code transparent ne pourra toujours pas accéder au champ. |
| CA2200 | @NO__T 0CA2200 : Lever à nouveau pour conserver les détails de la pile @ no__t-0 | Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue. |
| CA2201 | @NO__T 0CA2201 : Ne levez pas les types d’exceptions réservés @ no__t-0 | Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2202 | @NO__T 0CA2202 : Ne pas supprimer les objets plusieurs fois @ no__t-0 |Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à System.IDisposable.Dispose ou un Dispose équivalent (par exemple, une méthode Close() sur certains types) sur le même objet. |
| CA2204 | @NO__T 0CA2204 : Les littéraux doivent être orthographiés correctement @ no__t-0 | Une chaîne littéral dans un corps de méthode contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d'orthographe Microsoft. |
| CA2205 | @NO__T 0CA2205 : Utiliser des équivalents managés de l’API Win32 @ no__t-0 | Une méthode d’appel du système d’exploitation est définie et une méthode .NET ayant les fonctionnalités équivalentes est disponible. |
| CA2207 | @NO__T 0CA2207 : Initialiser les champs statiques de type valeur Inline @ no__t-0 | Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique. |
| CA2208 |@NO__T 0CA2208 : Instancier les exceptions d’argument correctement @ no__t-0 | Un appel est passé au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive d’ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive d’ArgumentException. |
| CA2210 |@NO__T 0CA2210 : Les assemblys doivent avoir des noms forts valides @ no__t-0 | Le nom fort protège les clients du chargement à leur insu d'un assembly falsifié. Les assemblys sans noms forts ne doivent pas être déployés hors de scénarios très limités. Si vous partagez ou distribuez des assemblys qui ne sont pas signés correctement, ceux-ci peuvent être falsifiés, le Common Language Runtime peut ne pas les charger ou l'utilisateur peut être amené à désactiver une vérification sur son ordinateur. |
| CA2211 |@NO__T 0CA2211 : Les champs non constants ne doivent pas être visibles @ no__t-0 | Les champs static qui ne sont ni constants ni en lecture seule ne sont pas thread-safe. L'accès à un tel champ doit être scrupuleusement contrôlé et requiert des techniques de programmation évoluées pour synchroniser l'accès à l'objet de classe. |
| CA2212 | @NO__T 0CA2212 : Ne Marquez pas les composants pris en service avec WebMethod @ no__t-0 |Une méthode dans un type qui hérite de System.EnterpriseServices.ServicedComponent est marquée avec System.Web.Services.WebMethodAttribute. Sachant que WebMethodAttribute et une méthode ServicedComponent ont des comportements incompatibles et des exigences en matière de contexte et de flux de transactions, le comportement de la méthode est incorrect dans certains scénarios. |
| CA2213 | [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n’est pas appelée par la méthode Dispose du type déclarant. |
| CA2214 | @NO__T 0CA2214 : N’appelez pas de méthodes substituables dans les constructeurs @ no__t-0 | Lorsqu'un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l'instance qui appelle la méthode n'ait pas été exécuté. |
| CA2215 | @NO__T 0CA2215 : Les méthodes dispose doivent appeler la classe de base dispose @ no__t-0 | Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose. |
| CA2216 |@NO__T 0CA2216 : Les types jetables doivent déclarer un finaliseur @ no__t-0 | Un type qui implémente System.IDisposable et présente des champs qui laissent entendre l'utilisation de ressources non managées n'implémente pas de finaliseur conforme à la description de Object.Finalize. |
| CA2217 | @NO__T 0CA2217 : Ne Marquez pas les enums avec FlagsAttribute @ no__t-0 |Une énumération extérieurement visible est marquée par FlagsAttribute et possède une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies dans l'énumération. |
| CA2218 |@NO__T 0CA2218 : Substituez GetHashCode lors du remplacement de est égal à @ no__t-0 | GetHashCode retourne une valeur fondée sur l’instance actuelle adaptée aux algorithmes de hachage et aux structures de données telles qu’une table de hachage. Deux objets de même type et égaux doivent retourner le même code de hachage. |
| CA2219 | @NO__T 0CA2219 : Ne levez pas d’exceptions dans les clauses d’exception @ no__t-0 | Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2220 | @NO__T 0CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base @ no__t-0 | La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir ce procédé, les types doivent appeler leur méthode Finalize de classe de base à partir de leur propre méthode Finalize. |
| CA2221 |@NO__T 0CA2221 : Les finaliseurs doivent être protégés @ no__t-0 | Les finaliseurs doivent utiliser le modificateur d’accès family. |
| CA2222 | @NO__T 0CA2222 : Ne pas réduire la visibilité des membres hérités @ no__t-0 |Vous ne devez pas modifier le modificateur d’accès destiné aux membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode. |
| CA2223 | @NO__T 0CA2223 : Les membres doivent différer par plus que le type de retour @ no__t-0 | Bien que le Common Language Runtime autorise l’utilisation de types de retour pour différencier des membres autrement identiques, cette fonctionnalité ne figure pas dans la Common Language Specification, et n’est pas une fonctionnalité courante des langages de programmation .NET. |
| CA2224 | @NO__T 0CA2224 : Remplacer Equals lors de la surcharge de l’opérateur est égal à @ no__t-0 | Un type public implémente l'opérateur d'égalité, mais ne se substitue pas à Object.Equals. |
| CA2225 | @NO__T 0CA2225 : Les surcharges d’opérateur ont des alternatives nommées @ no__t-0 |Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé donne accès aux mêmes fonctionnalités que l'opérateur. Il est fourni aux développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés. |
| CA2226 | @NO__T 0CA2226 : Les opérateurs doivent avoir des surcharges symétriques @ no__t-0 | Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé. |
| CA2227 |@NO__T 0CA2227 : Les propriétés de collection doivent être en lecture seule @ no__t-0 |Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis. |
| CA2228 | @NO__T 0CA2228 : Ne fournissez pas de formats de ressources non commercialisés @ no__t-0 | Les fichiers de ressources générés à l’aide des versions préliminaires de .NET peuvent ne pas être utilisables par les versions prises en charge de .NET. |
| CA2229 | [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md) | Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé. |
| CA2230 | @NO__T 0CA2230 : Utiliser des paramètres pour les arguments de variable @ no__t-0 | Un type public ou protégé contient une méthode publique ou protégée qui utilise la convention d’appel VarArgs au lieu du mot clé params. |
| CA2231 | [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Un type valeur se substitue à Object.Equals mais n'implémente pas l'opérateur d'égalité. |
| CA2232 | @NO__T 0CA2232 : Marquer Windows Forms points d’entrée avec STAThread @ no__t-0 | STAThreadAttribute indique que le modèle de thread COM pour l'application est un thread cloisonné (STA, Single-Threaded Apartment). Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. |
| CA2233 |@NO__T 0CA2233 : Les opérations ne doivent pas dépasser @ no__t-0 | Vous ne devez pas exécuter d’opérations arithmétiques sans valider au préalable les opérandes. Cela permet de vérifier que le résultat de l'opération ne se trouve pas hors de la plage des valeurs possibles pour les types de données impliqués. |
| CA2234 | @NO__T 0CA2234 : Passer des objets System. URI à la place de Strings @ no__t-0 | Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ». Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri. |
| CA2235 | [CA2235 : Marquez tous les champs non sérialisés](../code-quality/ca2235-mark-all-non-serializable-fields.md) | Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable. |
| CA2236 | @NO__T 0CA2236 : Appeler les méthodes de la classe de base sur les types ISerializable @ no__t-0 | Pour corriger une violation de cette règle, appelez la méthode GetObjectData ou le constructeur de sérialisation du type de base issu du constructeur ou de la méthode du type dérivé correspondant. |
| CA2237 | [CA2237 : Marquer les types ISerializable avec SerializableAttribute @ no__t-0 | Pour être reconnus par le Common Language Runtime comme sérialisables, les types doivent être marqués avec l'attribut SerializableAttribute même s'ils utilisent une routine de sérialisation personnalisée par le biais de l'implémentation de l'interface ISerializable. |
| CA2238 |@NO__T 0CA2238 : Implémentez correctement les méthodes de sérialisation @ no__t-0 | Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée. |
| CA2239 | @NO__T 0CA2239 : Fournir des méthodes de désérialisation pour les champs facultatifs @ no__t-0 | Un type présente un champ marqué avec l’attribut System.Runtime.Serialization.OptionalFieldAttribute et ne fournit aucune méthode de gestion des événements de désérialisation. |
| CA2240 | @NO__T 0CA2240 : Implémentez ISerializable correctement @ no__t-0 | Pour corriger une violation de cette règle, rendez la méthode GetObjectData visible et substituable, et assurez-vous que tous les champs d'instance sont intégrés au processus de sérialisation ou sont marqués explicitement avec l'attribut NonSerializedAttribute. |
| CA2241 | @NO__T 0CA2241 : Fournir des arguments corrects aux méthodes de mise en forme @ no__t-0 | L’argument de format passé à System.String.Format ne contient aucun élément de mise en forme pour chaque argument objet correspondant, ou vice versa. |
| CA2242 |@NO__T 0CA2242 : Test de NaN correctement @ no__t-0 | Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur. |
| CA2243 |@NO__T 0CA2243 : Les littéraux de chaîne d’attribut doivent être analysés correctement @ no__t-0 | Le paramètre de littéral de chaîne d'un attribut n'effectue pas une analyse correcte pour une URL, un GUID ou une version. |
| CA5122 | [CA5122 : Les déclarations P-Invoke ne doivent pas être critiques sécurisées](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Les méthodes sont marquées SecuritySafeCritical lorsqu’elles effectuent une opération relative à la sécurité, mais elle peuvent également être utilisées en toute sécurité par du code transparent. Le code transparent peut ne jamais appeler directement du code natif via P/Invoke. Par conséquent, marquer une méthode P/Invoke comme critique sécurisé ne permet pas au code transparent de l’appeler et s’avère trompeur pour l’analyse de sécurité. |
