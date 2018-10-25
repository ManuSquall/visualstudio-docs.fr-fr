---
title: Avertissements d’analyse du Code Visual Studio pour le Code managé par CheckId
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
- CA1900
- CA1901
- CA1903
- CA2000
- CA2001
- CA2002
- CA2003
- CA2004
- CA2006
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
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5dc92c12d0a60040cc216d0b9b3bee542c2bd8d8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49878919"
---
# <a name="code-analysis-warnings-for-managed-code-by-checkid"></a>Avertissements d’analyse du code pour le code managé par CheckId

Le tableau suivant répertorie les avertissements d'analyse du code pour le code managé par l'identificateur CheckId de l'avertissement.

| CheckId | Warning | Description |
|---------| - | - |
| CA1000 | [CA1000 : Ne déclarez pas de membres statiques sur les types génériques](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md) | Lorsqu’un membre statique d’un type générique est appelé, l’argument de type doit être spécifié pour le type. Lorsqu’un membre d’instance générique qui ne prend pas en charge l’inférence est appelé, l’argument de type doit être spécifié pour le membre. Dans ces deux cas, la syntaxe permettant de spécifier l’argument de type est différente et peut être facilement confondue. |
| CA1001 | [CA1001 : Les types qui ont des champs supprimables doivent être supprimables](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md) | Une classe déclare et implémente un champ d'instance qui est un type System.IDisposable, et elle n'implémente pas IDisposable. Une classe qui déclare un champ IDisposable possède indirectement une ressource non managée et doit implémenter l'interface IDisposable. |
| CA1002 | [CA1002 : N’exposez pas de listes génériques](../code-quality/ca1002-do-not-expose-generic-lists.md) | System.Collections.Generic.List < (de \<(T >) >) est une collection générique qui est conçue pour les performances, pas l’héritage. Par conséquent, la liste ne contient aucun membre virtuel. Les collections génériques qui sont conçues pour l'héritage doivent être exposées à la place. |
| CA1003 | [CA1003 : Utiliser les instances du gestionnaire d’événements génériques](../code-quality/ca1003-use-generic-event-handler-instances.md) |Un type contienne un délégué qui retourne void, dont la signature contient deux paramètres (le premier est un objet et le second est un type pouvant être assigné à EventArgs), et l’assembly conteneur cible Microsoft .NET Framework 2.0. |
| CA1004 | [CA1004 : Les méthodes génériques doivent fournir un paramètre de type](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md) | L’inférence désigne la manière dont l’argument de type d’une méthode générique est déterminé par le type d’argument passé à la méthode, au lieu d’utiliser la spécification explicite de l’argument de type. Pour activer l’inférence, la signature de paramètre d’une méthode générique doit contenir un paramètre du même type que le paramètre de type de la méthode. Dans ce cas, il n’est pas nécessaire de spécifier l’argument de type. Lors de l'utilisation de l'inférence pour tous les paramètres de type, la syntaxe d'appel aux méthodes d'instance génériques et non génériques est identique. Cela simplifie l'utilisation des méthodes génériques. |
| CA1005 | [CA1005 : Évitez trop de paramètres sur les types génériques](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md) | Plus un type générique contient de paramètres de type, plus il est difficile de déterminer et de mémoriser la représentation de chaque paramètre de type. Il est généralement évident avec un paramètre de type, comme dans la liste\<T > et dans certains cas ayant deux paramètres de type, comme dans Dictionary\<TKey, TValue >. Cependant, s’il existe plus de deux paramètres de type, la difficulté devient trop grande pour la plupart des utilisateurs. |
| CA1006 | [CA1006 : Ne pas imbriquer les types génériques dans les signatures de membre](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md) | Un argument de type imbriqué est un argument de type qui est également un type générique. Pour appeler un membre dont la signature contient un argument de type imbriqué, l’utilisateur doit instancier un type générique et passer ce type au constructeur d’un deuxième type générique. La procédure et la syntaxe requises sont complexes et doivent être évitées. |
| CA1007 |[CA1007 : Utiliser des méthodes génériques lorsque cela est approprié](../code-quality/ca1007-use-generics-where-appropriate.md) | Une méthode visible de l'extérieur contient un paramètre de référence de type System.Object. L'utilisation d'une méthode générique autorise le passage de tous les types, soumis à des contraintes, dans la méthode sans cast préalable du type vers le type de paramètre de référence. |
| CA1008 | [CA1008 : Les énumérations doivent avoir la valeur zéro](../code-quality/ca1008-enums-should-have-zero-value.md) | La valeur par défaut d'une énumération non initialisée, comme d'autres types valeur, est zéro. Une énumération attribuée sans indicateur doit définir un membre de valeur zéro afin que la valeur par défaut soit une valeur valide de l'énumération. Si une énumération à laquelle l'attribut FlagsAttribute est appliqué définit un membre de valeur zéro, son nom doit être "None" pour indiquer qu'aucune valeur n'a été définie dans l'énumération. |
| CA1009 | [CA1009 : Déclarez les gestionnaires d’événements correctement](../code-quality/ca1009-declare-event-handlers-correctly.md) | Les méthodes du gestionnaire d'événements acceptent deux paramètres. Le premier est de type System.Object et se nomme "sender". Il s'agit de l'objet qui déclenche l'événement. Le deuxième paramètre est de type System.EventArgs et se nomme "e". Il s'agit des données qui sont associées à l'événement. Les méthodes du gestionnaire d'événements ne doivent pas retourner de valeur ; dans le langage de programmation C#, ceci est indiqué par le type de retour void. |
| CA1010 | [CA1010 : Les collections doivent implémenter une interface générique](../code-quality/ca1010-collections-should-implement-generic-interface.md) | Pour étendre la facilité d’utilisation d’une collection, implémentez l’une des interfaces de collection génériques. La collection peut être ensuite utilisée pour remplir des types de collection génériques. |
| CA1011 |[CA1011 : Envisagez de passer les types de base comme paramètres](../code-quality/ca1011-consider-passing-base-types-as-parameters.md) | Lorsqu’un type de base est spécifié en tant que paramètre dans une déclaration de méthode, tout type dérivé du type de base peut être passé en tant qu’argument correspondant à la méthode. Si les fonctionnalités supplémentaires fournies par le type de paramètre dérivé ne sont pas requises, l'utilisation du type de base permet une exploitation plus large de la méthode. |
| CA1012 | [CA1012 : Les types abstraits ne doivent pas avoir de constructeurs](../code-quality/ca1012-abstract-types-should-not-have-constructors.md) | Les constructeurs des types abstraits peuvent être appelés uniquement par des types dérivés. Étant donné que les constructeurs publics créent des instances d'un type et que vous ne pouvez pas créer d'instance d'un type abstrait, un type abstrait doté d'un constructeur public est de conception incorrecte. |
| CA1013 | [CA1013 : Surchargez l’opérateur égal lors de la surcharge de l’opérateur d’addition et de soustraction](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md) | Un type public ou protégé implémente les opérateurs d'addition ou de soustraction sans implémenter l'opérateur d'égalité. |
| CA1014 | [CA1014 : Marquez les assemblys avec CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md) | La spécification de langage commun CLS (Common Language Specification) définit des restrictions de dénomination, des types de données, et des règles auxquelles les assemblys doivent se conformer s'ils doivent être utilisés à l'échelle de différents langages de programmation. Un design correct stipule que tous les assemblys indiquent explicitement la conformité CLS avec <xref:System.CLSCompliantAttribute>. Si cet attribut n'est pas présent sur un assembly, l'assembly n'est pas conforme. |
| CA1016 | [CA1016 : Marquez les assemblys avec AssemblyVersionAttribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md) | Le .NET Framework utilise le numéro de version pour identifier de façon unique un assembly et à lier aux types dans les assemblys à nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites. |
| CA1017 | [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md) |ComVisibleAttribute détermine comment les clients COM accèdent à du code managé. Un bon design stipule que les assemblys indiquent explicitement la visibilité COM. La visibilité COM peut être définie pour l'assembly en entier, puis être substituée pour des types et des membres de type individuels. Si cet attribut n'est pas présent, les clients COM peuvent voir le contenu de l'assembly. |
| CA1018 | [CA1018 : Marquez les attributs avec AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md) | Lorsque vous définissez un attribut personnalisé, marquez-le à l'aide d'AttributeUsageAttribute pour indiquer où l'attribut personnalisé peut être appliqué dans le code source. La signification et l'utilisation prévue d'un attribut déterminent ses emplacements valides au sein d'un code. |
| CA1019 | [CA1019 : Définissez des accesseurs pour les arguments d’attribut](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) | Les attributs peuvent définir des arguments obligatoires qui doivent être spécifiés lorsque vous appliquez l’attribut à une cible. Ceux-ci sont également appelés arguments positionnels parce qu’ils sont fournis aux constructeurs d’attributs en tant que paramètres positionnels. Pour chaque argument obligatoire, l’attribut doit également fournir une propriété en lecture seule correspondante afin que la valeur de l’argument puisse être récupérée au moment de l’exécution. Les attributs peuvent également définir des arguments facultatifs, qui sont également appelés arguments nommés. Ces arguments sont fournis aux constructeurs d’attributs par noms et doivent disposer d’une propriété en lecture/écriture correspondante. |
| CA1020 | [CA1020 : Éviter les espaces de noms comportant peu de types](../code-quality/ca1020-avoid-namespaces-with-few-types.md) | Assurez-vous que chacun de vos espaces de noms bénéficie d'une organisation logique, et qu'une raison valide justifie le placement des types dans un espace de noms peu rempli. |
| CA1021 | [CA1021 : Évitez les paramètres out](../code-quality/ca1021-avoid-out-parameters.md) | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Par ailleurs, la différence entre les paramètres out et ref est généralement peu comprise. |
| CA1023 | [CA1023 : Les indexeurs ne doivent pas être multidimensionnels](../code-quality/ca1023-indexers-should-not-be-multidimensional.md) | Les indexeurs, c'est-à-dire les propriétés indexées, doivent utiliser un index unique. Les indexeurs multidimensionnels peuvent considérablement diminuer la facilité d'utilisation de la bibliothèque. |
| CA1024 | [CA1024 : Utilisez des propriétés quand c’est approprié](../code-quality/ca1024-use-properties-where-appropriate.md) | Le nom d'une méthode publique ou protégée commence par « Get », n'accepte aucun paramètre et retourne une valeur qui n'est pas un tableau. La méthode est susceptible de devenir une propriété. |
| CA1025 | [CA1025 : Remplacez les arguments répétitifs par un tableau params](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md) | Utilisez un tableau de paramètres au lieu d’arguments répétés lorsque le nombre exact d’arguments est inconnu et lorsque les arguments variables sont de même type ou peuvent être passés comme étant de même type. |
| CA1026 | [CA1026 : N’utilisez pas de paramètres par défaut](../code-quality/ca1026-default-parameters-should-not-be-used.md) | Les méthodes qui utilisent des paramètres par défaut sont autorisées dans le cadre de la spécification de langage commun CLS (Common Language Specification) ; toutefois, cette spécification permet aux compilateurs d'ignorer les valeurs assignées à ces paramètres. Pour préserver le comportement souhaité d'un langage de programmation à l'autre, les méthodes qui utilisent des paramètres par défaut doivent être remplacées par des surcharges de méthode qui fournissent les paramètres par défaut. |
| CA1027 |[CA1027 : Marquez les énumérations avec FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md) | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Appliquez FlagsAttribute à une énumération lorsque ses constantes nommées peuvent être combinées de manière pertinente. |
| CA1028 | [CA1028 : Le stockage de l’énumération doit être Int32](../code-quality/ca1028-enum-storage-should-be-int32.md) | Une énumération est un type valeur qui définit un jeu de constantes nommées associées. Par défaut, le type de données System.Int32 est utilisé pour stocker la valeur de constante. Bien que vous puissiez modifier ce type sous-jacent, ce n'est ni obligatoire, ni recommandé dans la plupart des scénarios. |
| CA1030 | [CA1030 : Utiliser des événements lorsque cela est approprié](../code-quality/ca1030-use-events-where-appropriate.md) |Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Si une méthode est appelée en réponse à une modification d'état clairement définie, la méthode doit être appelée par un gestionnaire d'événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode. |
| CA1031 | [CA1031 : Ne pas intercepter des types d’exception générale](../code-quality/ca1031-do-not-catch-general-exception-types.md) | Les exceptions générales ne doivent pas être interceptées. Interceptez une exception plus spécifique ou levez à nouveau l'exception générale en tant que dernière instruction dans le bloc catch. |
| CA1032 |[CA1032 : Implémentez des constructeurs d’exception standard](../code-quality/ca1032-implement-standard-exception-constructors.md) | Ne pas fournir le jeu complet de constructeurs peut rendre difficile une gestion des exceptions correcte. |
| CA1033 | [CA1033 : Les méthodes d’interface doivent pouvoir être appelées par les types enfants](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md) | Un type unsealed visible de l'extérieur fournit une implémentation de méthode explicite d'une interface publique mais ne fournit aucune méthode de substitution visible de l'extérieur de même nom. |
| CA1034 | [CA1034 : Les types imbriqués ne doivent pas être visibles](../code-quality/ca1034-nested-types-should-not-be-visible.md) | Un type imbriqué représente un type déclaré dans la portée d'un autre type. Les types imbriqués sont utiles pour encapsuler les détails de l'implémentation privée du type conteneur. Utilisés à cette fin, les types imbriqués ne doivent pas être visibles de l'extérieur. |
| CA1035 | [CA1035 : Les implémentations ICollection ont des membres fortement typés](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md) | Cette règle requiert que les implémentations ICollection fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d’effectuer un cast d’arguments en type Object lorsqu’ils utilisent les fonctionnalités fournies par l’interface. Cette règle suppose que le type qui implémente ICollection procède ainsi pour gérer une collection d'instances d'un type plus fort qu'Object. |
| CA1036 | [CA1036 : Remplacez les méthodes sur les types comparables](../code-quality/ca1036-override-methods-on-comparable-types.md) |Un type public ou protégé implémente l'interface System.IComparable. Il ne substitue pas Object.Equals, ni ne surcharge l'opérateur égal à, différent de, inférieur à ou supérieur à propre au langage. |
| CA1038 | [CA1038 : Les énumérateurs doivent être fortement typés](../code-quality/ca1038-enumerators-should-be-strongly-typed.md) | Cette règle requiert que les implémentations IEnumerator fournissent également une version fortement typée de la propriété Current afin que les utilisateurs ne soient pas tenus d'effectuer un cast de la valeur de retour en type fort lorsqu'ils utilisent les fonctionnalités fournies par l'interface. |
| CA1039 | [CA1039 : Les listes sont fortement typées](../code-quality/ca1039-lists-are-strongly-typed.md) | Cette règle requiert que les implémentations IList fournissent des membres fortement typés afin que les utilisateurs ne soient pas tenus d’effectuer un cast d’arguments en type System.Object lorsqu’ils utilisent les fonctionnalités fournies par l’interface. |
| CA1040 |[CA1040 : Évitez les interfaces vides](../code-quality/ca1040-avoid-empty-interfaces.md) | Les interfaces définissent des membres qui fournissent un comportement ou un contrat d'utilisation. Les fonctionnalités décrites par l'interface peuvent être adoptées par tout type, indépendamment de l'endroit où le type figure dans la hiérarchie d'héritage. Un type implémente une interface en fournissant des implémentations pour les membres de celle-ci. Une interface vide ne définit aucun membre ; par conséquent, elle ne définit aucun contrat pouvant être implémenté. |
| CA1041 | [CA1041 : Fournir un message ObsoleteAttribute](../code-quality/ca1041-provide-obsoleteattribute-message.md) | Un type ou un membre est marqué avec un attribut System.ObsoleteAttribute dont la propriété ObsoleteAttribute.Message n'est pas spécifiée. Lorsqu'un type ou membre marqué avec ObsoleteAttribute est compilé, la propriété Message de l'attribut est affichée. Cela fournit à l'utilisateur des informations sur le type ou le membre obsolète. |
| CA1043 | [CA1043 : Utiliser un argument entier ou chaîne pour les indexeurs](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md) | Les indexeurs (c'est-à-dire les propriétés indexées) doivent utiliser des types intégral ou chaîne pour l'index. Ces types sont généralement utilisés pour indexer des structures de données et augmentent la facilité d'utilisation de la bibliothèque. L'utilisation du type Object doit se restreindre aux cas où le type intégral ou de chaîne spécifique ne peut pas être spécifié au moment du design. |
| CA1044 | [CA1044 : Les propriétés ne doivent pas être en écriture seule](../code-quality/ca1044-properties-should-not-be-write-only.md) | Bien qu'il soit acceptable et souvent nécessaire de disposer d'une propriété en lecture seule, les règles de conception interdisent l'utilisation de propriétés en écriture seule. Le fait de permettre à un utilisateur de définir une valeur et l'empêcher ensuite de la consulter n'offre aucune garantie de sécurité. De plus, sans accès en lecture, l'état des objets partagés ne peut s'afficher, ce qui limite leur utilité. |
| CA1045 |[CA1045 : Ne pas passer de types par référence](../code-quality/ca1045-do-not-pass-types-by-reference.md) | Passer des types par référence (en utilisant out ou ref) nécessite une certaine expérience des pointeurs, de comprendre la différence entre les types valeur et les types référence, ainsi que la gestion de méthodes impliquant plusieurs valeurs de retour. Les architectes de bibliothèques qui réalisent un travail de conception destiné à une audience générale ne doivent pas s'attendre à ce que les utilisateurs maîtrisent l'utilisation des paramètres out ou ref. |
| CA1046 | [CA1046 : Ne pas surcharger l’opérateur égal sur les types de référence](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md) | Pour les types référence, l’implémentation par défaut de l’opérateur d’égalité est presque toujours correcte. Par défaut, deux références sont égales uniquement si elles pointent sur le même objet. |
| CA1047 |[CA1047 : Ne déclarez pas des membres protégés dans les types sealed](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md) | Les types déclarent des membres protégés afin que des types qui héritent puissent accéder au membre ou le substituer. Par définition, les types sealed ne peuvent pas être hérités, ce qui signifie que les méthodes protégées sur les types sealed ne peuvent pas être appelées. |
| CA1048 | [CA1048 : Ne déclarez pas de membres virtuels dans les types sealed](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md) | Les types déclarent des méthodes comme étant virtuelles afin d'hériter de types en mesure de substituer l'implémentation de la méthode virtuelle. Par définition, un type sealed ne peut pas être hérité. Une méthode virtuelle sur un type sealed est alors sans signification. |
| CA1049 | [CA1049 : Les types qui ont des ressources natives doivent être supprimables](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md) | Les types qui allouent des ressources non managées doivent implémenter IDisposable pour permettre aux appelants de libérer ces ressources à la demande et de raccourcir les durées de vie des objets qui les détiennent. |
| CA1050 | [CA1050 : Déclarez les types dans des espaces de noms](../code-quality/ca1050-declare-types-in-namespaces.md) | Les types sont déclarés au sein d'espaces de noms pour empêcher des collisions de dénomination, ainsi qu'en guise que méthode d'organisation de types connexes au sein d'une hiérarchie d'objets. |
| CA1051 | [CA1051 : Ne déclarez pas de champs d’instances visibles](../code-quality/ca1051-do-not-declare-visible-instance-fields.md) | Un champ s'utilise principalement en tant que détail d'implémentation. Les champs doivent être privés ou internes, et doivent être exposés au moyen de propriétés. |
| CA1052 | [CA1052 : Les types de conteneurs statiques doivent être sealed](../code-quality/ca1052-static-holder-types-should-be-sealed.md) | Un type public ou protégé contient uniquement des membres statiques et n'est pas déclaré avec le modificateur sealed (Référence C#) (NotInheritable). Un type qui n'est pas destiné à être hérité doit être marqué avec le modificateur sealed pour empêcher son utilisation en tant que type de base. |
| CA1053 |[CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md) | Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé. Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type. La surcharge de chaîne doit appeler la surcharge d’URI (Uniform Resource Identifier) à l’aide de l’argument de chaîne pour des raisons de sécurité. |
| CA1054 | [CA1054 : Les paramètres d’URI ne doivent pas être des chaînes](../code-quality/ca1054-uri-parameters-should-not-be-strings.md) | Si une méthode accepte une représentation sous forme de chaîne d'un URI, une surcharge correspondante qui accepte une instance de la classe URI doit être fournie ; elle-même fournit ces services de manière sûre et sécurisée. |
| CA1055 | [CA1055 : Les valeurs de retour d’URI ne doivent pas être des chaînes](../code-quality/ca1055-uri-return-values-should-not-be-strings.md) | Cette règle considère que la méthode retourne un URI. Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1056 | [CA1056 : Les propriétés d’URI ne doivent pas être des chaînes](../code-quality/ca1056-uri-properties-should-not-be-strings.md) | Cette règle considère que la propriété représente un URI (Uniform Resource Identifier). Une représentation sous forme de chaîne d'un URI est sujette aux erreurs d'analyse et d'encodage, et peut entraîner des failles de sécurité. La classe System.Uri fournit ces services de manière sûre et sécurisée. |
| CA1057 | [CA1057 : Les surcharges d’URI de chaîne appellent des surcharges de System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md) | Un type déclare des surcharges de méthode qui diffèrent uniquement par le remplacement d'un paramètre de chaîne par un paramètre System.Uri. La surcharge qui accepte le paramètre de chaîne n'appelle pas la surcharge qui accepte le paramètre URI. |
| CA1058 | [CA1058 : Les types ne doivent pas étendre certains types de base](../code-quality/ca1058-types-should-not-extend-certain-base-types.md) | Un type visible de l'extérieur étend certains types de base. Utilisez l'une des solutions de remplacement. |
| CA1059 |[CA1059 : Les membres ne doivent pas exposer certains types concrets](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md) | Un type concret est un type qui présente une implémentation complète et, par conséquent, peut être instancié. Pour permettre une utilisation généralisée du membre, remplacez le type concret par l'interface suggérée. |
| CA1060 | [CA1060 : Déplacer les P/Invoke vers une classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md) | Les méthodes d'appel de code non managé, telles que celles qui sont marquées avec l'attribut System.Runtime.InteropServices.DllImportAttribute, ou les méthodes définies à l'aide du mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], accèdent à du code non managé. Ces méthodes doivent être de la classe NativeMethods, SafeNativeMethods ou UnsafeNativeMethods. |
| CA1061 |[CA1061 : Ne masquez pas les méthodes de la classe de base](../code-quality/ca1061-do-not-hide-base-class-methods.md) | Une méthode dans un type de base est masquée par une méthode portant le même nom dans un type dérivé, lorsque la signature de paramètre de la méthode dérivée diffère uniquement par les types qui sont dérivés plus faiblement que les types correspondants dans la signature de paramètre de la méthode de base. |
| CA1062 | [CA1062 : Valider les arguments de méthodes publiques](../code-quality/ca1062-validate-arguments-of-public-methods.md) | Tous les arguments de référence passés aux méthodes visibles de l’extérieur doivent être vérifiés pour voir s’ils ont la valeur null. |
| CA1063 | [CA1063 : Implémentez IDisposable correctement](../code-quality/ca1063-implement-idisposable-correctly.md) | Tous les types IDisposable doivent implémenter le modèle Dispose correctement. |
| CA1064 | [CA1064 : Les exceptions doivent être publiques](../code-quality/ca1064-exceptions-should-be-public.md) | Une exception interne est uniquement visible à l'intérieur de sa propre portée interne. Lorsque l'exception se situe en dehors de la portée interne, seule l'exception de base peut être utilisée pour intercepter l'exception. Si l’exception interne est héritée de <xref:System.Exception>, <xref:System.SystemException>, ou <xref:System.ApplicationException>, le code externe n’aura pas d’informations suffisantes pour savoir que faire avec l’exception. |
| CA1065 | [CA1065 : Ne levez pas d’exceptions dans des emplacements inattendus](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md) | Une méthode dont l'objet n'est pas de lever des exceptions lève une exception. |
| CA1300 | [CA1300 : Spécifiez MessageBoxOptions](../code-quality/ca1300-specify-messageboxoptions.md) | Pour afficher correctement une boîte de message pour les cultures qui utilisent un sens de lecture de droite à gauche, les membres RightAlign et RtlReading de l'énumération MessageBoxOptions doivent être passés à la méthode Show. |
| CA1301 | [CA1301 : Évitez les accélérateurs en doublon](../code-quality/ca1301-avoid-duplicate-accelerators.md) | Une touche d'accès rapide, également connue sous le nom d'accélérateur, autorise l'accès à un contrôle par le biais du clavier, à l'aide de la touche ALT. Lorsque plusieurs contrôles présentent des touches d'accès rapide en doublon, le comportement de ces dernières n'est pas correctement défini. |
| CA1302 | [CA1302 : Ne codez pas en dur les chaînes spécifiques aux paramètres régionaux](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md) | L’énumération System.Environment.SpecialFolder contient des membres qui font référence à des dossiers système spéciaux. Les emplacements de ces dossiers peuvent avoir des valeurs distinctes selon le système d'exploitation ; l'utilisateur peut modifier certains des emplacements, et ces derniers sont localisés. La méthode Environment.GetFolderPath retourne les emplacements associés à l'énumération Environment.SpecialFolder, localisés et appropriés pour l'ordinateur en cours d'exécution. |
| CA1303 | [CA1303 : Ne passez pas des littéraux comme paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md) | Une méthode visible de l’extérieur passe une littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans la bibliothèque de classes .NET Framework, et cette chaîne doit être localisable. |
| CA1304 | [CA1304 : Spécifier CultureInfo](../code-quality/ca1304-specify-cultureinfo.md) | Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo. Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1305 | [CA1305 : Spécifier IFormatProvider](../code-quality/ca1305-specify-iformatprovider.md) | Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider. Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux. |
| CA1306 | [CA1306 : Définir les paramètres régionaux pour les types de données](../code-quality/ca1306-set-locale-for-data-types.md) | Les paramètres régionaux déterminent des éléments de présentation des données spécifiques à la culture, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l'ordre de tri. Lorsque vous créez un DataTable ou un DataSet, vous devez définir les paramètres régionaux explicitement. |
| CA1307 | [CA1307 : Spécifiez StringComparison](../code-quality/ca1307-specify-stringcomparison.md) | Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison. |
| CA1308 |[CA1308 : Normalisez les chaînes en majuscules](../code-quality/ca1308-normalize-strings-to-uppercase.md) | Les chaînes doivent être normalisées en majuscules. En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller-retour. |
| CA1309 | [CA1309 : Utilisez StringComparison avec la valeur Ordinal](../code-quality/ca1309-use-ordinal-stringcomparison.md) | Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison. En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable. |
| CA1400 | [CA1400 : Des points d’entrée P/Invoke doivent exister](../code-quality/ca1400-p-invoke-entry-points-should-exist.md) |Une méthode publique ou protégée est marquée avec l'attribut System.Runtime.InteropServices.DllImportAttribute. La bibliothèque non managée n'a pas pu être localisée, ou la méthode n'a pu être mise en correspondance avec aucune fonction de la bibliothèque. |
| CA1401 | [CA1401 : Les P/Invoke ne doivent pas être visibles](../code-quality/ca1401-p-invokes-should-not-be-visible.md) | Une méthode publique ou protégée dans un type public a l'attribut System.Runtime.InteropServices.DllImportAttribute (également implémenté par le mot clé Declare en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). De telles méthodes ne doivent pas être exposées. |
| CA1402 |[CA1402 : Évitez les surcharges dans les interfaces COM visibles](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md) | Lorsque les méthodes surchargées sont exposées aux clients COM, seule la première surcharge de méthode conserve son nom. Les surcharges suivantes sont renommées de manière unique par l'ajout d'un trait de soulignement (_) au nom et d'un entier qui correspond à l'ordre de déclaration de la surcharge. |
| CA1403 | [CA1403 : Les types Structurer automatiquement ne doivent pas être visibles par COM](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md) | Un type valeur visible par COM est marqué avec l'attribut System.Runtime.InteropServices.StructLayoutAttribute qui a la valeur LayoutKind.Auto. La disposition de ces types peut varier entre les versions du .NET Framework, ce qui bloque les clients COM qui attendent une disposition spécifique. |
| CA1404 | [CA1404 : Appeler GetLastError immédiatement après P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md) | Un appel est effectué à la méthode Marshal.GetLastWin32Error ou l’équivalent [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] fonction GetLastError et l’appel immédiatement antérieur n’est pas un système d’exploitation appeler la méthode. |
| CA1405 | [CA1405 : Les types de base type visibles par COM doivent être visibles par COM](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md) | Un type visible par COM dérive d'un type qui n'est pas visible par COM. |
| CA1406 |[CA1406 : Éviter les arguments Int64 pour les clients Visual Basic 6](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md) | Les clients COM Visual Basic 6 ne peut pas accéder aux entiers de 64 bits. |
| CA1407 |[CA1407 : Éviter les membres statiques dans les types visibles par COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md) | COM ne prend pas en charge les méthodes statiques. |
| CA1408 | [CA1408 : N’utilisez pas le paramètre AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md) | Les types qui utilisent une interface double permettent aux clients de se lier à une disposition d'interface spécifique. Les modifications apportées à une version future de la disposition du type ou des types de base bloquent les clients COM qui se lient à l'interface. Par défaut, si l'attribut ClassInterfaceAttribute n'est pas spécifié, une interface de répartition uniquement est utilisée. |
| CA1409 | [CA1409 : Les types visibles par COM doivent pouvoir être créés](../code-quality/ca1409-com-visible-types-should-be-creatable.md) |Un type référence marqué spécifiquement comme visible par des clients COM contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre). Les clients COM ne peuvent pas créer de type sans constructeur public par défaut. |
| CA1410 | [CA1410 : Les méthodes d’inscription COM doivent être mises en correspondance](../code-quality/ca1410-com-registration-methods-should-be-matched.md) | Un type déclare une méthode marquée avec l'attribut System.Runtime.InteropServices.ComRegisterFunctionAttribute, mais ne déclare pas une méthode marquée avec l'attribut System.Runtime.InteropServices.ComUnregisterFunctionAttribute, ou vice versa. |
| CA1411 | [CA1411 : Les méthodes d’inscription COM ne doivent pas être visibles](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md) | Une méthode marquée avec l'attribut System.Runtime.InteropServices.ComRegisterFunctionAttribute ou System.Runtime.InteropServices.ComUnregisterFunctionAttribute est visible de l'extérieur. |
| CA1412 | [CA1412 : Marquez les interfaces ComSource comme IDispatch](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md) | Un type est marqué avec l'attribut System.Runtime.InteropServices.ComSourceInterfacesAttribute et au moins une des interfaces spécifiées n'est pas marquée avec l'attribut System.Runtime.InteropServices.InterfaceTypeAttribute ayant la valeur ComInterfaceType.InterfaceIsIDispatch. |
| CA1413 | [CA1413 : Évitez les champs non publics dans les types valeur visibles par COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md) | Les champs d'instance non publics des types valeur visibles par COM sont visibles par les clients COM. Passez en revue le contenu des champs pour voir les informations qui ne doivent pas être exposées, sinon vous aurez une conception imprévue ou des conséquences sur la sécurité. |
| CA1414 | [CA1414 : Marquer les arguments P/Invoke booléens comme MarshalAs](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md) | Le type de données booléen contient plusieurs représentations dans le code non managé. |
| CA1415 | [CA1415 : Déclarer correctement les méthodes P/Invoke](../code-quality/ca1415-declare-p-invokes-correctly.md) | Cette règle recherche des déclarations de méthode d'appel de code non managé qui ciblent des fonctions [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)] présentant un pointeur vers un paramètre de structure OVERLAPPED, et le paramètre managé correspondant n'est pas un pointeur vers une structure System.Threading.NativeOverlapped. |
| CA1500 | [CA1500 : Les noms de variable ne doivent pas être identiques à des noms de champs](../code-quality/ca1500-variable-names-should-not-match-field-names.md) | Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant, ce qui entraîne des erreurs. |
| CA1501 | [CA1501 : Évitez l’excès d’héritage](../code-quality/ca1501-avoid-excessive-inheritance.md) | Un type est imbriqué de plus de quatre niveaux dans sa hiérarchie d'héritage. Les hiérarchies de type profondément imbriquées peuvent être difficiles à suivre, comprendre et gérer. |
| CA1502 | [CA1502 : Éviter une complexité excessive](../code-quality/ca1502-avoid-excessive-complexity.md) | Cette règle évalue le nombre de chemins linéairement indépendants dans la méthode, déterminé par le nombre et la complexité des branches conditionnelles. |
| CA1504 | [CA1504 : Vérifiez les noms de champs peu clairs](../code-quality/ca1504-review-misleading-field-names.md) | Le nom d’un champ d’instance commence par « s_ » ou le nom d’un champ statique de (Shared en Visual Basic) commence par « m_ ». |
| CA1505 | [CA1505 : Évitez le code impossible à maintenir](../code-quality/ca1505-avoid-unmaintainable-code.md) | Un type ou une méthode a une faible valeur d'indice de maintenabilité. Un faible indice de maintenabilité indique qu'un type ou qu'une méthode est probablement difficile à maintenir et qu'il/elle se prête bien à une nouvelle conception. |
| CA1506 |[CA1506 : Évitez les couplages de classe excessifs](../code-quality/ca1506-avoid-excessive-class-coupling.md) | Cette règle mesure l'accouplement de classes en comptant le nombre de références de type uniques contenues dans un type ou une méthode. |
| CA1600 | [CA1600 : N’utilisez pas de priorité de processus inactif](../code-quality/ca1600-do-not-use-idle-process-priority.md) | N'affectez pas la valeur Idle à la priorité de processus. Sinon, les processus avec System.Diagnostics.ProcessPriorityClass.Idle occuperaient le processeur alors qu'il devrait être inactif et bloqueraient par conséquent la veille. |
| CA1601 | [CA1601 : Ne pas utiliser de minuteries qui empêchent les changements d’état de l’alimentation](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md) | En effet, toute activité périodique supérieure à cette fréquence occupe le processeur et interfère avec les minuteries d'inactivité qui déclenchent la mise en veille de l'écran et des disques durs pour économiser de l'énergie. |
| CA1700 | [CA1700 : Ne nommez pas les valeurs d’énumération 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md) | Cette règle suppose qu'un membre de l'énumération dont le nom contient le terme "reserved" n'est pas utilisé actuellement, mais constitue un espace réservé à renommer ou à supprimer dans une version ultérieure. Renommer ou supprimer un membre constitue une modification avec rupture. |
| CA1701 | [CA1701 : La casse des mots composés de chaînes de ressources doit être correcte](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md) | Chaque mot dans la chaîne de ressource est fractionné en jetons basés sur la casse. Chaque combinaison de deux jetons contiguë est vérifiée par la bibliothèque du correcteur orthographique Microsoft. S'il est reconnu, le mot produit une violation de la règle. |
| CA1702 | [CA1702 : La casse des mots composés doit être correcte](../code-quality/ca1702-compound-words-should-be-cased-correctly.md) | Le nom d'un identificateur contient plusieurs mots et au moins l'un des mots semble être un mot composé qui ne présente pas une casse correcte. |
| CA1703 | [CA1703 : Les chaînes de ressources doit être orthographiées correctement](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md) | Une chaîne de ressource contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft. |
| CA1704 | [CA1704 : Les identificateurs doivent être correctement orthographiés](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md) | Le nom d'un identificateur visible de l'extérieur contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque du vérificateur d'orthographe Microsoft. |
| CA1707 | [CA1707 : Les identificateurs ne doivent pas contenir de traits de soulignement](../code-quality/ca1707-identifiers-should-not-contain-underscores.md) | Par convention, les noms d'identificateurs ne contiennent pas de trait de soulignement (_). Cette règle vérifie les espaces de noms, types, membres et paramètres. |
| CA1708 | [CA1708 : Les identificateurs ne doivent pas différer que par leur casse](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md) | Les identificateurs des espaces de noms, types, membres et paramètres ne peuvent pas différer uniquement par la casse car les langages qui ciblent le Common Language Runtime ne sont pas tenus de respecter celle-ci. |
| CA1709 | [CA1709 : La casse des identificateurs doit être correcte](../code-quality/ca1709-identifiers-should-be-cased-correctly.md) | Par convention, les noms de paramètres utilisent la casse mixte et les noms d'espaces de noms, de types et de membres utilisent la convention de casse Pascal. |
| CA1710 | [CA1710 : Les identificateurs doivent avoir un suffixe correct](../code-quality/ca1710-identifiers-should-have-correct-suffix.md) |Par convention, les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou encore des types dérivés de ces types, présentent un suffixe associé au type de base ou à l'interface. |
| CA1711 | [CA1711 : Les identificateurs ne doivent pas avoir un suffixe incorrect](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md) | Par convention, seuls les noms des types qui étendent certains types de base ou qui implémentent certaines interfaces, ou les types dérivés de ces types, doivent se terminer par des suffixes réservés spécifiques. Les autres noms de types ne doivent pas utiliser ces suffixes réservés. |
| CA1712 | [CA1712 : Ne préfixez pas les valeurs d’énumération avec le nom du type](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md) | Les noms des membres de l'énumération n'ont pas pour préfixe le nom de type, car les outils de développement sont censés fournir les informations de type. |
| CA1713 | [CA1713 : Les événements ne doivent avoir le préfixe Before ou After](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md) | Le nom d'un événement commence par « Before » ou « After ». Pour nommer des événements associés déclenchés dans une séquence spécifique, utilisez le présent ou le passé pour indiquer la position relative dans la séquence d'actions. |
| CA1714 | [CA1714 : Les énumérations d’indicateurs doivent avoir des noms au pluriel](../code-quality/ca1714-flags-enums-should-have-plural-names.md) | Une énumération publique comporte l'attribut System.FlagsAttribute et son nom ne se termine pas par « s ». Les types marqués avec FlagsAttribute ont des noms au pluriel, car l'attribut indique que plusieurs valeurs peuvent être spécifiées. |
| CA1715 | [CA1715 : Les identificateurs doivent avoir un préfixe correct](../code-quality/ca1715-identifiers-should-have-correct-prefix.md) | Le nom d'une interface extérieurement visible ne commence pas par un « I » majuscule. Le nom d'un paramètre de type générique sur un type ou une méthode extérieurement visible ne commence pas par un « T » majuscule. |
| CA1716 | [CA1716 : Les identificateurs ne doivent pas correspondre à des mots clés](../code-quality/ca1716-identifiers-should-not-match-keywords.md) | Un nom d'espace de noms ou un nom de type correspond à un mot clé réservé dans un langage de programmation. Les identificateurs des espaces de noms et des types ne doivent pas correspondre aux mots clés définis par les langages qui ciblent le Common Language Runtime. |
| CA1717 | [CA1717 : Seuls les noms des énumérations FlagsAttribute doivent être au pluriel](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md) | Selon les conventions d'attribution de nom, un nom au pluriel pour une énumération indique que plusieurs valeurs de l'énumération peuvent être spécifiées simultanément. |
| CA1719 | [CA1719 : Les noms des paramètres ne doivent pas être identiques aux noms des membres](../code-quality/ca1719-parameter-names-should-not-match-member-names.md) | Un nom de paramètre doit véhiculer la signification du paramètre et un nom de membre celle du membre. Un design où ceux-ci sont identiques est rare. Donner à un paramètre le même que son membre n'est pas une méthode intuitive et rend la bibliothèque difficile à utiliser. |
| CA1720 |[CA1720 : Les identificateurs ne doivent pas contenir de noms de types](../code-quality/ca1720-identifiers-should-not-contain-type-names.md) | Le nom d'un paramètre dans un membre extérieurement visible contient un nom de type de données, ou le nom d'un membre extérieurement visible contient un nom de type de données spécifique à une langue. |
| CA1721 | [CA1721 : Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md) |Le nom d'un membre public ou protégé commence par « Get ». Sinon, il correspond au nom d'une propriété publique ou protégée. Les méthodes et propriétés « Get » doivent porter des noms distinguant clairement leur fonction. |
| CA1722 | [CA1722 : Les identificateurs ne doivent pas avoir un préfixe incorrect](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md) | Par convention, seuls certains éléments de programmation présentent des noms qui commencent par un préfixe spécifique. |
| CA1724 | [CA1724 : Les noms de types ne doivent pas être identiques aux espaces de noms](../code-quality/ca1724-type-names-should-not-match-namespaces.md) | Noms de types ne doivent pas correspondre aux noms des espaces de noms définis dans la bibliothèque de classes .NET Framework. Enfreindre cette règle peut réduire la facilité d'utilisation de la bibliothèque. |
| CA1725 | [CA1725 : Les noms de paramètres doivent correspondre à la déclaration de base](../code-quality/ca1725-parameter-names-should-match-base-declaration.md) | La désignation cohérente des paramètres dans une hiérarchie de substitution augmente la facilité d'utilisation des substitutions de méthode. Un nom de paramètre dans une méthode dérivée qui diffère du nom dans la déclaration de base peut créer une confusion pour déterminer si la méthode est une substitution de la méthode de base ou une nouvelle surcharge de la méthode. |
| CA1726 | [CA1726 : Utilisez les termes préférés](../code-quality/ca1726-use-preferred-terms.md) | Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Le nom peut également inclure le terme « Indicateur » ou « Indicateurs ». |
| CA1800 | [CA1800 : N’effectuez pas de cast inutilement](../code-quality/ca1800-do-not-cast-unnecessarily.md) | Les casts en doublon font baisser les performances, surtout lorsque les casts sont exécutés au sein d'instructions d'itération compactes. |
| CA1801 | [CA1801 : Passez en revue les paramètres inutilisés](../code-quality/ca1801-review-unused-parameters.md) | Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode. |
| CA1802 |[CA1802 : Utilisez des littéraux où c’est approprié](../code-quality/ca1802-use-literals-where-appropriate.md) |Un champ est déclaré statique et en lecture seule (Shared et ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), et est initialisé avec une valeur qui est calculable à la compilation. La valeur est assignée au champ ciblé étant calculable à la compilation, modifiez la déclaration const (Const en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) afin que la valeur est calculée au moment de la compilation plutôt qu’au moment de l’exécution. |
| CA1804 | [CA1804 : Supprimez les variables locales inutilisées](../code-quality/ca1804-remove-unused-locals.md) | Les variables locales inutilisées et les assignations inutiles augmentent la taille d'un assembly et font baisser les performances. |
| CA1806 | [CA1806 : Ne pas ignorer les résultats de méthode](../code-quality/ca1806-do-not-ignore-method-results.md) | Un nouvel objet est créé mais jamais utilisé ; ou une méthode qui crée et retourne une nouvelle chaîne est appelée et la nouvelle chaîne n'est jamais utilisée ; ou une méthode COM ou P/Invoke retourne un code HRESULT ou d'erreur qui n'est jamais utilisé. |
| CA1809 |[CA1809 : Évitez le surplus de variables locales](../code-quality/ca1809-avoid-excessive-locals.md) | Une méthode d'optimisation des performances courante consiste à stocker une valeur dans un registre de processeur au lieu de la mémoire ; cette méthode est appelée « enregistrement de la valeur ». Pour augmenter les chances que toutes les variables locales sont inscrites dans le Registre, limitez le nombre de variables locales à 64. |
| CA1810 | [CA1810 : Initialisez les champs statiques de type référence en ligne](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Lorsqu’un type déclare un constructeur statique explicite, le compilateur juste-à-temps (JIT, Just-In-Time) ajoute une vérification à chacun des méthodes statiques et constructeurs d’instances du type afin de garantir que le constructeur statique a été appelé précédemment. Les vérifications des constructeurs statiques peuvent diminuer les performances. |
| CA1811 | [CA1811 : Évitez le recours à du code privé non appelé](../code-quality/ca1811-avoid-uncalled-private-code.md) | Un membre privé ou interne (de niveau assembly) n'a pas d'appelants dans l'assembly, et n'est appelé ni par le Common Language Runtime, ni par un délégué. |
| CA1812 | [CA1812 : Évitez les classes internes non instanciées](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Une instance d'un type de niveau assembly n'est pas créée par le code au sein de l'assembly. |
| CA1813 | [CA1813 : Évitez les attributs unsealed](../code-quality/ca1813-avoid-unsealed-attributes.md) | La bibliothèque de classes .NET Framework fournit des méthodes pour récupérer des attributs personnalisés. Par défaut, ces méthodes recherchent la hiérarchie d'héritage des attributs. Le fait de sceller l'attribut élimine la recherche dans la hiérarchie d'héritage et peut améliorer les performances. |
| CA1814 | [CA1814 : Utilisez des tableaux en escalier à la place de tableaux multidimensionnels](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Un tableau en escalier est un tableau dont les éléments sont des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui conduit à un gaspillage d'espace plus restreint pour certains groupes de données. |
| CA1815 | [CA1815 : Remplacez Equals et l’opérateur égal à dans les types valeur](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Pour les types valeur, l'implémentation héritée de Equals utilise la bibliothèque Reflection et compare le contenu de tous les champs. Le processus de réflexion sollicite fortement les ressources informatiques et la comparaison de chaque champ à la recherche d'une égalité peut s'avérer inutile. Si des utilisateurs sont susceptibles de comparer ou de trier des instances, ou de les utiliser en tant que clés de table de hachage, votre type valeur doit implémenter Equals. |
| CA1816 | [CA1816 : Appelez GC.SuppressFinalize correctement](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Une méthode qui est une implémentation de Dispose n’appelle pas de catalogue global. SuppressFinalize ; ou une méthode qui n’est pas une implémentation de Dispose appelle GC. SuppressFinalize ; ou une méthode appelle GC. SuppressFinalize et passe un élément autre que cette (Me en Visual Basic). |
| CA1819 | [CA1819 : Les propriétés ne doivent pas retourner des tableaux](../code-quality/ca1819-properties-should-not-return-arrays.md) | Les tableaux retournés par les propriétés ne sont pas protégés en écriture, même si la propriété est en lecture seule. Pour protéger le tableau de toute falsification, la propriété doit retourner une copie du tableau. En général, les utilisateurs ne comprennent l'incidence négative en matière de performances de l'appel à une telle propriété. |
| CA1820 | [CA1820 : Vérifiez la présence de chaînes vides en utilisant la longueur de chaîne](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | La comparaison de chaînes à l'aide de la propriété String.Length ou de la méthode String.IsNullOrEmpty est nettement plus rapide que l'utilisation d'Equals. |
| CA1821 | [CA1821 : Supprimez les finaliseurs vides](../code-quality/ca1821-remove-empty-finalizers.md) | Évitez autant que possible d'utiliser des finaliseurs en raison de la surcharge supplémentaire des performances impliquée dans le suivi de la durée de vie de l'objet. Un finaliseur vide entraîne une charge supplémentaire sans aucun avantage. |
| CA1822 |[CA1822 : Marquez les membres comme statique](../code-quality/ca1822-mark-members-as-static.md) | Les membres qui n'accèdent pas aux données d'instance ou n'appellent pas de méthodes d'instance peuvent être marquées comme static (Shared en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Une fois que les méthodes ont été marquées comme static, le compilateur émet des sites d'appel non virtuels vers ces membres. Cette opération se traduit par un gain de performances mesurable pour le code dépendant des performances. |
| CA1823 | [CA1823 : Évitez les champs privés inutilisés](../code-quality/ca1823-avoid-unused-private-fields.md) | Des champs privés qui ne sont pas accessibles dans l'assembly ont été détectés. |
| CA1824 |[CA1824 : Marquez les assemblys avec NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | L'attribut NeutralResourcesLanguage informe le ResourceManager de la langue qui a été utilisée pour afficher les ressources d'une culture neutre d'un assembly. Cela permet d'améliorer les performances de recherche de la première ressource chargée et de réduire votre jeu de travail. |
| CA1900 | [CA1900 : Les champs de type valeur doivent être portables](../code-quality/ca1900-value-type-fields-should-be-portable.md) | Cette règle vérifie que les structures déclarées avec une disposition explicite s’aligneront correctement lorsqu’elles seront marshalées pour le code non managé sur les systèmes d’exploitation 64 bits. |
| CA1901 | [CA1901 : Les déclarations P/Invoke doivent être portables](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md) | Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke, puis vérifie que la taille du paramètre est correcte lorsqu’elle est marshalée au code non managé sur les systèmes d’exploitation 32 bits et 64 bits. |
| CA1903 | [CA1903 : Utiliser l’API seulement à partir de l’infrastructure cible](../code-quality/ca1903-use-only-api-from-targeted-framework.md) | Un membre ou un type utilise un membre ou un type qui a été introduit dans un Service Pack qui ne figurait pas dans le Framework ciblé du projet. |
| CA2000 | [CA2000 : Supprimez les objets avant de perdre l’étendue](../code-quality/ca2000-dispose-objects-before-losing-scope.md) | Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée. |
| CA2001 | [CA2001 : Évitez d’appeler des méthodes susceptibles de poser des problèmes](../code-quality/ca2001-avoid-calling-problematic-methods.md) | Un membre appelle une méthode potentiellement dangereuse ou problématique. |
| CA2002 |[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md) |Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet. |
| CA2003 |[CA2003 : Ne traitez pas les fibres comme des threads](../code-quality/ca2003-do-not-treat-fibers-as-threads.md) | Un thread managé est traité comme un thread [!INCLUDE[TLA2#tla_win32](../code-quality/includes/tla2sharptla_win32_md.md)]. |
| CA2004 | [CA2004 : Supprimez les appels à GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md) | Si vous envisagez d'utiliser SafeHandle, supprimez tous les appels à GC.KeepAlive (objet). Dans ce cas, les classes n'ont pas à appeler GC.KeepAlive. Cela suppose qu'elles n'ont pas de finaliseur mais qu'elles dépendent de SafeHandle pour finaliser le handle du système d'exploitation à leur place. |
| CA2006 | [CA2006 : Utilisez SafeHandle pour encapsuler les ressources natives](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md) | L'utilisation de IntPtr dans du code managé peut être le signe d'un problème potentiel de sécurité et de fiabilité. Toute utilisation de IntPtr doit être passée en revue pour déterminer s'il est nécessaire de recourir à un SafeHandle ou une technologie similaire à la place. |
| CA2100 | [CA2100 : Recherchez les failles de sécurité dans des requêtes SQL](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md) | Une méthode définit la propriété System.Data.IDbCommand.CommandText à l’aide d’une chaîne générée à partir d’un argument de chaîne à la méthode. Cette règle suppose que l’argument de chaîne contient des entrées d’utilisateur. Une chaîne de commande SQL générée par une entrée d'utilisateur est vulnérable aux attaques par injection de code SQL. |
| CA2101 |[CA2101 : Spécifier le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md) | Un membre d’appel de code non managé autorise les appelants dotés d’un niveau de confiance partielle, présente un paramètre de chaîne et ne marshale pas explicitement la chaîne. Cela peut provoquer une faille de sécurité potentielle. |
| CA2102 | [CA2102 : Interceptez les exceptions non CLSCompliant dans des gestionnaires généraux](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md) | Un membre dans un assembly qui n'est pas marqué avec RuntimeCompatibilityAttribute ou qui est marqué avec RuntimeCompatibility(WrapNonExceptionThrows = false) contient un bloc catch qui gère System.Exception et ne contient pas de bloc catch général immédiatement après. |
| CA2103 | [CA2103 : Vérifiez la sécurité impérative](../code-quality/ca2103-review-imperative-security.md) |Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active. Utilisez la sécurité de déclaration dès que possible. |
| CA2104 |[CA2104 : Ne déclarez pas les types référence mutables en lecture seule](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md) | Un type visible de l’extérieur contient un champ en lecture seule visible de l’extérieur qui constitue un type référence mutable. Un type mutable est un type dont les données d’instance peuvent être modifiées. |
| CA2105 | [CA2105 : Les champs de tableau ne doivent pas être en lecture seule](../code-quality/ca2105-array-fields-should-not-be-read-only.md) |Lorsque vous appliquez le modificateur en lecture seule (ReadOnly en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) à un champ qui contient un tableau, ce champ ne peut pas être modifié pour référencer un tableau différent. Toutefois, les éléments du tableau stockés dans un champ en lecture seule peuvent être modifiés. |
| CA2106 | [CA2106 : Sécurisez les assertions](../code-quality/ca2106-secure-asserts.md) | Une méthode déclare une autorisation et aucune vérification de sécurité n’est exécutée sur l’appelant. L’assertion d’une autorisation de sécurité effectuée sans vérification de sécurité peut rendre votre code vulnérable et facile à exploiter. |
| CA2107 | [CA2107 : Passez en revue l’utilisation des méthodes Deny et PermitOnly](../code-quality/ca2107-review-deny-and-permit-only-usage.md) |La méthode PermitOnly et les actions de sécurité CodeAccessPermission.Deny doivent être uniquement utilisées par les qui ont une connaissance avancée de la sécurité .NET Framework. Le code qui utilise ces actions de sécurité doit subir une révision de sécurité. |
| CA2108 | [CA2108 : Vérifiez la sécurité déclarative dans les types de valeurs](../code-quality/ca2108-review-declarative-security-on-value-types.md) | Un type valeur public ou protégé est sécurisé par l’accès aux données ou des demandes de liaison. |
| CA2109 | [CA2109 : Passez en revue les gestionnaires d’événements visibles](../code-quality/ca2109-review-visible-event-handlers.md) | Une méthode de gestion d’événements publique ou protégée a été détectée. Les méthodes de gestion d'événements ne doivent pas être exposées sauf nécessité absolue. |
| CA2111 |[CA2111 : Les pointeurs ne doivent pas être visibles](../code-quality/ca2111-pointers-should-not-be-visible.md) | Un pointeur n’est ni privé, ni interne ni en lecture seule. Un code malveillant peut modifier la valeur du pointeur, ce qui peut permettre l'accès aux emplacements arbitraires en mémoire ou provoquer des défaillances des applications ou du système. |
| CA2112 | [CA2112 : Les types sécurisés ne doivent pas exposer de champs](../code-quality/ca2112-secured-types-should-not-expose-fields.md) | Un type public ou protégé contient des champs publics et est sécurisé par des demandes de liaison. Si un code a accès à une instance d'un type sécurisé par une demande de liaison, ce code n'a pas besoin de satisfaire la demande de liaison pour accéder aux champs du type. |
| CA2114 | [CA2114 : La sécurité de la méthode doit être un sur-ensemble du type](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md) | Pour une même action, une méthode ne doit pas présenter de sécurité déclarative à la fois au niveau méthode et au niveau type. |
| CA2115 | [CA2115 : Appelez GC.KeepAlive lorsque vous utilisez des ressources natives](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md) | Cette règle détecte les erreurs susceptibles de se produire du fait qu’une ressource non managée est en cours de finalisation alors qu’elle est encore utilisée dans un code non managé. |
| CA2116 | [CA2116 : Les méthodes APTCA doivent appeler seulement des méthodes APTCA](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md) |Lorsque l'attribut APTCA (AllowPartiallyTrustedCallersAttribute) est présent dans un assembly entièrement fiable, et lorsque cet assembly exécute du code dans un autre assembly qui n'autorise pas les appelants partiellement fiables, il en résulte une faille de sécurité dont l'exploitation est possible. |
| CA2117 | [CA2117 : Les types APTCA doivent étendre seulement des types de base APTCA](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md) | Lorsque l'attribut APTCA est présent dans un assembly entièrement fiable, et lorsqu'un type présent dans l'assembly hérite d'un type qui n'autorise pas les appelants partiellement approuvés, il en résulte une faille de sécurité dont l'exploitation est possible. |
| CA2118 | [CA2118 : Passez en revue l’utilisation de SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) |SuppressUnmanagedCodeSecurityAttribute modifie le comportement par défaut du système en matière de sécurité pour les membres qui exécutent du code non managé utilisant COM Interop ou l'appel de code non managé. Cet attribut est essentiellement utilisé pour accroître les performances ; toutefois, les gains de performance s'accompagnent de risques substantiels pour la sécurité. |
| CA2119 | [CA2119 : Scellez les méthodes qui satisfont les interfaces privées](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md) | Un type public pouvant être hérité fournit une implémentation de méthode substituable d'une interface interne (Friend en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Pour corriger une violation de cette règle, empêchez la méthode d’être substituée en dehors de l’assembly. |
| CA2120 | [CA2120 : Sécurisez les constructeurs de sérialisation](../code-quality/ca2120-secure-serialization-constructors.md) | Ce type possède un constructeur qui accepte un objet System.Runtime.Serialization.SerializationInfo et un objet System.Runtime.Serialization.StreamingContext (la signature du constructeur de sérialisation). Ce constructeur n’est pas sécurisé par une vérification de la sécurité, mais au moins un des constructeurs normaux dans le type est sécurisé. |
| CA2121 | [CA2121 : Les constructeurs statiques doivent être privés](../code-quality/ca2121-static-constructors-should-be-private.md) | Le système appelle le constructeur statique avant la création de la première instance du type ou le référencement de tout membre statique. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le système. Selon les opérations effectuées dans le constructeur, cette possibilité peut provoquer un comportement inattendu. |
| CA2122 | [CA2122 : N’exposez pas indirectement des méthodes avec des demandes de liaison](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md) | Un membre public ou protégé a des demandes de liaison et est appelé par un membre qui ne procède à aucune vérification de la sécurité. Une demande de liaison vérifie uniquement les autorisations de l'appelant immédiat. |
| CA2123 | [CA2123 : Les demandes de liaison de substitution doivent être identiques au composant de base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md) | Cette règle met en correspondance une méthode et sa méthode de base, qui est soit une interface, soit une méthode virtuelle dans un autre type, puis compare les demandes de liaison sur chacune. Si cette règle est violée, un appelant malveillant peut ignorer la demande de liaison simplement en appelant la méthode non protégée. |
| CA2124 | [CA2124 : Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md) | Une méthode publique ou protégée contient un bloc try/finally. Le bloc finally semble réinitialiser l’état de sécurité et n’est lui-même placé dans aucun bloc finally. |
| CA2126 | [CA2126 : Les demandes de liaison de types nécessitent des demandes d’héritage](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md) | Un type unsealed public est protégé par une demande de liaison et a une méthode substituable. Ni le type ni la méthode ne sont protégés par une demande d'héritage. |
| CA2127 | [CA2136 : Les membres ne doivent pas avoir d’annotations de transparence en conflit](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Le code critique ne peut pas apparaître dans un assembly transparent à 100 pour cent. Cette règle analyse les assemblys transparents de 100 pour cent pour toutes les annotations SecurityCritical au type, champ et les niveaux de méthode. |
| CA2128 |[CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | Cette règle analyse toutes les méthodes et les types dans un assembly qui est transparent à 100 pour cent ou mixte mi-critique et elle signale toute utilisation déclarative ou impérative d’Assert. |
| CA2129 | [CA2140 : Le code transparent ne doit référencer des éléments critiques de sécurité](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Les méthodes marquées avec SecurityTransparentAttribute appellent des membres non publics marqués en tant que SecurityCritical. Cette règle analyse toutes les méthodes et tous les types dans un assembly qui est mi-transparent et mi-critique, et elle signale tous les appels du code transparent au code critique non public qui ne sont pas marqués comme SecurityTreatAsSafe. |
| CA2130 | [CA2130 : Les constantes critiques de sécurité doivent être transparentes](../code-quality/ca2130-security-critical-constants-should-be-transparent.md) | La mise en application de la transparence n’est pas effectuée pour les valeurs de constante car les compilateurs alignent les valeurs de constante afin qu’aucune recherche ne soit requise au moment de l’exécution. Les champs constants doivent être transparents de sécurité (security-transparent) afin que les relecteurs de code ne supposent pas que le code transparent ne peut pas accéder à la constante. |
| CA2131 | [CA2131 : Les types critiques de sécurité ne peuvent pas participer à l’équivalence des types](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md) | Un type participe à l'équivalence des types et un type lui-même, ou un membre ou champ du type, est marqué à l'aide de l'attribut SecurityCriticalAttribute. Cette règle se déclenche sur tout type ou type critique contenant des méthodes critiques ou des champs qui participent à l'équivalence de type. Lorsque le CLR détecte un tel type, il ne peut pas le charger avec une exception TypeLoadException au moment de l'exécution. En général, cette règle se déclenche uniquement lorsque les utilisateurs implémentent l'équivalence de type manuellement plutôt qu'en comptant sur tlbimp et les compilateurs pour faire l'équivalence de type. |
| CA2132 | [CA2132 : Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md) |Les types et les membres qui possèdent l’attribut SecurityCriticalAttribute ne peuvent pas être utilisés par le code d’application Silverlight. Les types et membres critiques de sécurité (security-critical) peuvent être uniquement utilisés par le code de confiance dans la bibliothèque de classes .NET Framework pour Silverlight. Parce qu'une construction publique ou protégée dans une classe dérivée doit avoir la même transparence ou une transparence supérieure à sa classe de base, une classe dans une application ne peut pas être dérivée d'une classe marqué SecurityCritical. |
| CA2133 | [CA2133 : Les délégués doivent lier les méthodes avec une transparence cohérente](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md) | Cet avertissement se déclenche sur une méthode qui lie un délégué marqué à l'aide de l'attribut SecurityCriticalAttribute à une méthode transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. L'avertissement se déclenche également sur une méthode qui lie un délégué transparent ou critique sécurisé (security-safe-critical) à une méthode critique. |
| CA2134 | [CA2134 : La transparence des méthodes doit rester cohérente lors du remplacement des méthodes de base](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md) |Cette règle se déclenche lorsqu'une méthode marquée à l'aide de l'attribut SecurityCriticalAttribute remplace une méthode qui est transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. La règle se déclenche également lorsqu'une méthode qui est transparente ou marquée à l'aide de l'attribut SecuritySafeCriticalAttribute remplace une méthode qui est marquée à l'aide d'un attribut SecurityCriticalAttribute. La règle est appliquée lors de la substitution d’une méthode virtuelle ou de l’implémentation d’une interface. |
| CA2135 | [CA2135 : Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md) | L’utilisation de LinkDemands est déconseillée dans l’ensemble de règles de sécurité de niveau 2. Au lieu d'utiliser LinkDemands pour implémenter la sécurité au moment de la compilation JIT, marquez les méthodes, types et champs avec l'attribut SecurityCriticalAttribute. |
| CA2136 | [CA2136 : Les membres ne doivent pas avoir d’annotations de transparence en conflit](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md) | Les attributs de transparence sont appliqués à partir d’éléments de code de plus grande portée à des éléments de plus petite portée. Les attributs de transparence d'éléments de code avec une plus grande portée sont prioritaires sur les attributs de transparence des éléments de code contenus dans le premier élément. Par exemple, une classe marquée à l'aide de l'attribut SecurityCriticalAttribute ne peut pas contenir de méthode marquée à l'aide de l'attribut SecuritySafeCriticalAttribute. |
| CA2137 | [CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md) | Une méthode contient du code non vérifiable ou retourne un type par référence. Cette règle se déclenche lorsque le code transparent de sécurité tente d'exécuter du code MISL (Microsoft Intermediate Language) non vérifiable. Toutefois, la règle ne contient pas de vérificateur IL (Intermediate Language) complet, et à la place utilise l’heuristique pour intercepter la plupart des violations de vérification MSIL. |
| CA2138 | [CA2138 : Les méthodes transparentes ne doivent pas appeler les méthodes avec l’attribut SuppressUnmanagedCodeSecurity](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md) | Une méthode transparente de sécurité appelle une méthode qui est marquée à l'aide de l'attribut SuppressUnmanagedCodeSecurityAttribute. |
| CA2139 | [CA2139 : Les méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md) | Cette règle est déclenchée par toute méthode transparente qui essaie de gérer une exception qui endommage un processus à l'aide de l'attribut HandleProcessCorruptedStateExceptionsAttribute. Une exception qui endommage un processus est une classification d'exception CLR version 4.0 des exceptions comme AccessViolationException. L'attribut HandleProcessCorruptedStateExceptionsAttribute peut uniquement être utilisé par des méthodes critiques de sécurité et sera ignoré s'il s'applique à une méthode transparente. |
| CA2140 | [CA2140 : Le code transparent ne doit référencer des éléments critiques de sécurité](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md) | Un élément de code marqué à l'aide de l'attribut SecurityCriticalAttribute est critique de sécurité. Une méthode transparente ne peut pas utiliser un élément critique de sécurité. Si un type transparent essaie d'utiliser un type critique de sécurité, TypeAccessException, MethodAccessException ou FieldAccessException est déclenché. |
| CA2141 |[CA2141 : Les méthodes transparentes ne satisfont pas les LinkDemands](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md) | Une méthode transparente de sécurité appelle une méthode dans un assembly qui n'est pas marqué à l'aide de l'attribut APTCA, ou une méthode transparente de sécurité satisfait une demande LinkDemand pour un type ou une méthode. |
| CA2142 | [CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md) | Cette règle se déclenche sur les méthodes transparentes qui requièrent l'accès de LinkDemands. Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. |
| CA2143 | [CA2143 : Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md) | Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d’une opération. Par conséquent, il ne doit pas demander d’autorisations. Le code transparent de sécurité doit utiliser des demandes complètes pour prendre des décisions de sécurité et le code critique sécurisé ne doit pas dépendre du code transparent pour l’exécution de ces demandes. |
| CA2144 | [CA2144 : Le code transparent ne doit pas charger d’assemblys depuis des tableaux d’octets](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md) | La revue de sécurité du code transparent n’est pas aussi complète que la revue de sécurité du code critique, car le code transparent ne peut pas exécuter d’actions relatives à la sécurité. Les assemblys chargés à partir d'un tableau d'octets peuvent ne pas être remarqués dans du code transparent, et ce tableau d'octets peut contenir du code critique, voire critique de sécurité, qui doit être audité. |
| CA2145 | [CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md) | Les méthodes décorées par l'attribut SuppressUnmanagedCodeSecurityAttribute ont un LinkDemand implicite sur toute méthode qui l'appelle. Ce LinkDemand requiert que le code appelant soit critique de sécurité. Le marquage de la méthode qui utilise SuppressUnmanagedCodeSecurity avec l’attribut SecurityCriticalAttribute rend cette exigence plus évidente pour les appelants de la méthode. |
| CA2146 | [CA2146 : Les types doivent être au moins aussi critiques que leurs types de base et leurs interfaces](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md) | Cette règle se déclenche lorsqu'un type dérivé a un attribut de transparence de sécurité qui n'est pas aussi critique que son type de base ou l'interface implémentée. Seuls les types critiques peuvent dériver des types de base critiques ou implémenter des interfaces critiques, et seuls les types critiques ou critiques sécurisés peuvent dériver des types de base critiques sécurisés ou implémenter des interfaces critiques sécurisées. |
| CA2147 |[CA2147 : Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md) | Aucune autorisation suffisante n’est accordée à un code marqué comme attribut SecurityTransparentAttribute pour procéder à une assertion. |
| CA2149 | [CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md) | Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif (par exemple, via un appel P/Invoke). Les violations de cette règle provoquent une exception MethodAccessException dans le modèle de transparence de niveau 2, et une demande complète pour le code UnmanagedCode dans le modèle de transparence de niveau 1. |
| CA2151 |[CA2151 : Les champs avec des types critiques doivent être des champs critiques de sécurité](../code-quality/ca2151-fields-with-critical-types-should-be-security-critical.md) | Pour utiliser les types critiques de sécurité, le code qui référence le type doit être critique de sécurité ou critique sécurisé. Ceci est vrai même si la référence est indirecte. Par conséquent, un champ transparent de sécurité ou critique sécurisé est trompeur, car le code transparent ne pourra toujours pas accéder au champ. |
| CA2200 | [CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](../code-quality/ca2200-rethrow-to-preserve-stack-details.md) | Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue. |
| CA2201 | [CA2201 : Ne levez pas des types d’exceptions réservés](../code-quality/ca2201-do-not-raise-reserved-exception-types.md) | Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2202 | [CA2202 : Ne pas supprimer des objets plusieurs fois](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md) |Une implémentation de méthode contient des chemins d’accès de code qui peuvent provoquer des appels multiples à System.IDisposable.Dispose ou un Dispose équivalent (par exemple, une méthode Close() sur certains types) sur le même objet. |
| CA2204 | [CA2204 : Les littéraux doivent être correctement orthographiés](../code-quality/ca2204-literals-should-be-spelled-correctly.md) | Une chaîne littéral dans un corps de méthode contient un ou plusieurs mots qui ne sont pas reconnus par la bibliothèque de vérificateur d'orthographe Microsoft. |
| CA2205 | [CA2205 : Utilisez des équivalents managés de l’API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md) | Un système d’exploitation appeler la méthode est définie et une méthode qui a les mêmes fonctionnalités se trouve dans la bibliothèque de classes .NET Framework. |
| CA2207 | [CA2207 : Initialisez les champs statiques des types de valeurs inline](../code-quality/ca2207-initialize-value-type-static-fields-inline.md) | Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique. |
| CA2208 |[CA2208 : Instanciez les exceptions d’argument correctement](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md) | Un appel est passé au constructeur par défaut (sans paramètre) d’un type d’exception qui est ou dérive d’ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d’un type d’exception qui est ou dérive d’ArgumentException. |
| CA2210 |[CA2210 : Les assemblys doivent avoir des noms forts valides](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md) | Le nom fort protège les clients du chargement à leur insu d'un assembly falsifié. Les assemblys sans noms forts ne doivent pas être déployés hors de scénarios très limités. Si vous partagez ou distribuez des assemblys qui ne sont pas signés correctement, ceux-ci peuvent être falsifiés, le Common Language Runtime peut ne pas les charger ou l'utilisateur peut être amené à désactiver une vérification sur son ordinateur. |
| CA2211 |[CA2211 : Les champs non constants ne doivent pas être visibles](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md) | Les champs static qui ne sont ni constants ni en lecture seule ne sont pas thread-safe. L'accès à un tel champ doit être scrupuleusement contrôlé et requiert des techniques de programmation évoluées pour synchroniser l'accès à l'objet de classe. |
| CA2212 | [CA2212 : Ne marquez pas les composants pris en charge avec WebMethod](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md) |Une méthode dans un type qui hérite de System.EnterpriseServices.ServicedComponent est marquée avec System.Web.Services.WebMethodAttribute. Sachant que WebMethodAttribute et une méthode ServicedComponent ont des comportements incompatibles et des exigences en matière de contexte et de flux de transactions, le comportement de la méthode est incorrect dans certains scénarios. |
| CA2213 | [CA2213 : Les champs pouvant être supprimés doivent l’être](../code-quality/ca2213-disposable-fields-should-be-disposed.md) | Un type qui implémente System.IDisposable déclare des champs de types qui implémentent également IDisposable. La méthode Dispose du champ n’est pas appelée par la méthode Dispose du type déclarant. |
| CA2214 | [CA2214 : N’appelez pas de méthodes substituables dans les constructeurs](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md) | Lorsqu'un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l'instance qui appelle la méthode n'ait pas été exécuté. |
| CA2215 | [CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md) | Si un type hérite d'un type pouvant être supprimé, il doit appeler la méthode Dispose du type de base issu de sa propre méthode Dispose. |
| CA2216 |[CA2216 : Les types supprimables doivent déclarer un finaliseur](../code-quality/ca2216-disposable-types-should-declare-finalizer.md) | Un type qui implémente System.IDisposable et présente des champs qui laissent entendre l'utilisation de ressources non managées n'implémente pas de finaliseur conforme à la description de Object.Finalize. |
| CA2217 | [CA2217 : Ne marquez pas les énumérations avec FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md) |Une énumération extérieurement visible est marquée par FlagsAttribute et possède une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies dans l'énumération. |
| CA2218 |[CA2218 : Remplacez GetHashCode lors du remplacement de Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md) | GetHashCode retourne une valeur fondée sur l’instance actuelle adaptée aux algorithmes de hachage et aux structures de données telles qu’une table de hachage. Deux objets de même type et égaux doivent retourner le même code de hachage. |
| CA2219 | [CA2219 : Ne levez pas d’exceptions dans les clauses d’exception](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md) | Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l'erreur d'origine difficile à détecter et à déboguer. |
| CA2220 | [CA2220 : Les finaliseurs doivent appeler le finaliseur de la classe de base](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md) | La finalisation doit être propagée par le biais de la hiérarchie d'héritage. Pour garantir ce procédé, les types doivent appeler leur méthode Finalize de classe de base à partir de leur propre méthode Finalize. |
| CA2221 |[CA2221 : Les finaliseurs doivent être protégés](../code-quality/ca2221-finalizers-should-be-protected.md) | Les finaliseurs doivent utiliser le modificateur d’accès family. |
| CA2222 | [CA2222 : Ne réduisez pas la visibilité des membres hérités](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md) |Vous ne devez pas modifier le modificateur d’accès destiné aux membres hérités. La modification d'un membre hérité au profit d'un état privé n'empêche pas les appelants d'accéder à l'implémentation de classe de base de la méthode. |
| CA2223 | [CA2223 : Les membres ne doivent pas différer uniquement par leur type de retour](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md) | Bien que le Common Language Runtime autorise l’utilisation de types de retour pour différencier des membres autrement identiques, cette fonctionnalité ne figure pas dans la Common Language Specification, et n’est pas une fonctionnalité courante des langages de programmation .NET. |
| CA2224 | [CA2224 : Remplacez Equals lors de la surcharge de l’opérateur égal](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md) | Un type public implémente l'opérateur d'égalité, mais ne se substitue pas à Object.Equals. |
| CA2225 | [CA2225 : Les surcharges d’opérateur ont d’autres méthodes nommées](../code-quality/ca2225-operator-overloads-have-named-alternates.md) |Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé donne accès aux mêmes fonctionnalités que l'opérateur. Il est fourni aux développeurs qui programment dans les langages qui ne prennent pas en charge les opérateurs surchargés. |
| CA2226 | [CA2226 : Les opérateurs doivent avoir des surcharges symétriques](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md) | Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé. |
| CA2227 |[CA2227 : Les propriétés de collection doivent être en lecture seule](../code-quality/ca2227-collection-properties-should-be-read-only.md) |Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis. |
| CA2228 | [CA2228 : Ne distribuez pas des formats de ressources non commercialisés](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md) | Les fichiers de ressources qui ont été créés à l’aide des versions préliminaires du .NET Framework n’est peut-être pas utilisables par les versions prises en charge du .NET Framework. |
| CA2229 | [CA2229 : Implémentez des constructeurs de sérialisation](../code-quality/ca2229-implement-serialization-constructors.md) | Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé. |
| CA2230 | [CA2230 : Utilisez le mot clé params pour les arguments de variables](../code-quality/ca2230-use-params-for-variable-arguments.md) | Un type public ou protégé contient une méthode publique ou protégée qui utilise la convention d’appel VarArgs au lieu du mot clé params. |
| CA2231 | [CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md) | Un type valeur se substitue à Object.Equals mais n'implémente pas l'opérateur d'égalité. |
| CA2232 | [CA2232 : Marquez les points d’entrée Windows Forms avec STAThread](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md) | STAThreadAttribute indique que le modèle de thread COM pour l'application est un thread cloisonné (STA, Single-Threaded Apartment). Cet attribut doit être présent au point d'entrée de toute application qui utilise des Windows Forms ; s'il est omis, les composants Windows peuvent ne pas fonctionner correctement. |
| CA2233 |[CA2233 : Les opérations ne doivent pas provoquer de dépassement de capacité](../code-quality/ca2233-operations-should-not-overflow.md) | Vous ne devez pas exécuter d’opérations arithmétiques sans valider au préalable les opérandes. Cela permet de vérifier que le résultat de l'opération ne se trouve pas hors de la plage des valeurs possibles pour les types de données impliqués. |
| CA2234 | [CA2234 : Passez des objets System.Uri au lieu de chaînes](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md) | Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ». Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un paramètre System.Uri. |
| CA2235 | [CA2235 : Marquez tous les champs non sérialisables](../code-quality/ca2235-mark-all-non-serializable-fields.md) | Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable. |
| CA2236 | [CA2236 : Appelez les méthodes de la classe de base sur les types ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md) | Pour corriger une violation de cette règle, appelez la méthode GetObjectData ou le constructeur de sérialisation du type de base issu du constructeur ou de la méthode du type dérivé correspondant. |
| CA2237 | [CA2237 : Marquez les types ISerializable avec SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) | Pour être reconnus par le Common Language Runtime comme sérialisables, les types doivent être marqués avec l'attribut SerializableAttribute même s'ils utilisent une routine de sérialisation personnalisée par le biais de l'implémentation de l'interface ISerializable. |
| CA2238 |[CA2238 : Implémentez les méthodes de sérialisation correctement](../code-quality/ca2238-implement-serialization-methods-correctly.md) | Une méthode qui gère un événement de sérialisation n’a pas la signature, le type de retour ou la visibilité appropriée. |
| CA2239 | [CA2239 : Spécifiez des méthodes de désérialisation pour les champs facultatifs](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md) | Un type présente un champ marqué avec l’attribut System.Runtime.Serialization.OptionalFieldAttribute et ne fournit aucune méthode de gestion des événements de désérialisation. |
| CA2240 | [CA2240 : Implémentez ISerializable correctement](../code-quality/ca2240-implement-iserializable-correctly.md) | Pour corriger une violation de cette règle, rendez la méthode GetObjectData visible et substituable, et assurez-vous que tous les champs d'instance sont intégrés au processus de sérialisation ou sont marqués explicitement avec l'attribut NonSerializedAttribute. |
| CA2241 | [CA2241 : Fournissez des arguments corrects aux méthodes de mise en forme](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md) | L’argument de format passé à System.String.Format ne contient aucun élément de mise en forme pour chaque argument objet correspondant, ou vice versa. |
| CA2242 |[CA2242 : Effectuez correctement des tests NaN](../code-quality/ca2242-test-for-nan-correctly.md) | Cette expression teste une valeur par rapport à Single.Nan ou Double.Nan. Utilisez Single.IsNan(Single) ou Double.IsNan(Double) pour tester la valeur. |
| CA2243 |[CA2243 : Les littéraux de chaîne d’attribut doivent être analysés correctement](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md) | Le paramètre de littéral de chaîne d'un attribut n'effectue pas une analyse correcte pour une URL, un GUID ou une version. |
| CA5122 | [CA5122 : Les déclarations P-Invoke ne doivent pas être critiques sécurisées](../code-quality/ca5122-p-invoke-declarations-should-not-be-safe-critical.md) | Les méthodes sont marquées SecuritySafeCritical lorsqu’elles effectuent une opération relative à la sécurité, mais elle peuvent également être utilisées en toute sécurité par du code transparent. Le code transparent peut ne jamais appeler directement du code natif via P/Invoke. Par conséquent, marquer une méthode P/Invoke comme critique sécurisé ne permet pas au code transparent de l’appeler et s’avère trompeur pour l’analyse de sécurité. |