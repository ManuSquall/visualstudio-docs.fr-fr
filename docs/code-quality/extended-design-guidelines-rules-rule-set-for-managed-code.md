---
title: Ensemble de règles de règles de conception étendue pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d37e540df9a480f559e81e650f57ad5bb87d0ddd
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72535891"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de conception étendue pour le code managé

L’ensemble de règles des règles de conception étendue de Microsoft développe les règles de base pour optimiser les problèmes de facilité d’utilisation et de maintenance signalés. Une mise en évidence supplémentaire est placée dans les instructions d’affectation de noms. Vous devez envisager d’inclure cet ensemble de règles si votre projet inclut du code de bibliothèque ou si vous souhaitez appliquer les normes les plus élevées pour écrire du code facile à gérer.

Les règles de la conception étendue incluent toutes les règles dans l’ensemble de règles de [règles de conception de base](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) , qui inclut les règles dans l’ensemble de règles des [règles recommandées managées](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

Le tableau suivant décrit toutes les règles de l’ensemble de règles des règles de conception étendue Microsoft.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1009](../code-quality/ca1009.md)|Déclarer les gestionnaires d'événements correctement|
|[CA1016](../code-quality/ca1016.md)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033.md)|Les méthodes d'interface doivent pouvoir être appelées par les types enfants|
|[CA1049](../code-quality/ca1049.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1060](../code-quality/ca1060.md)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Ne pas masquer les méthodes de la classe de base|
|[CA1063](../code-quality/ca1063.md)|Implémenter IDisposable correctement|
|[CA1065](../code-quality/ca1065.md)|Ne pas lever d'exceptions dans les emplacements inattendus|
|[CA1301](../code-quality/ca1301.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400.md)|Des points d'entrée P/Invoke doivent exister|
|[CA1401](../code-quality/ca1401.md)|Les P/Invoke ne doivent pas être visibles|
|[CA1403](../code-quality/ca1403.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Les types de base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410.md)|Les méthodes d'inscription COM doivent être mises en correspondance|
|[CA1415](../code-quality/ca1415.md)|Déclarer correctement les méthodes P/Invoke|
|[CA1821](../code-quality/ca1821.md)|Supprimez les finaliseurs vides|
|[CA1900](../code-quality/ca1900.md)|Les champs de type valeur doivent être portables|
|[CA1901](../code-quality/ca1901.md)|Les déclarations P/Invoke doivent être portables|
|[CA2002](../code-quality/ca2002.md)|Ne définissez pas un verrou sur des objets à identité faible|
|[CA2100](../code-quality/ca2100.md)|Vérifier si les requêtes SQL présentent des failles de sécurité|
|[CA2101](../code-quality/ca2101.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
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
|[CA2200](../code-quality/ca2200.md)|Levez à nouveau une exception pour conserver les détails de la pile|
|[CA2202](../code-quality/ca2202.md)|Ne pas supprimer d'objets plusieurs fois|
|[CA2207](../code-quality/ca2207.md)|Initialisez les champs statiques des types valeur en ligne|
|[CA2212](../code-quality/ca2212.md)|Ne marquez pas les composants pris en charge avec webMethod|
|[CA2213](../code-quality/ca2213.md)|Les champs pouvant être supprimés doivent l’être|
|[CA2214](../code-quality/ca2214.md)|N'appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](../code-quality/ca2216.md)|Les types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2220](../code-quality/ca2220.md)|Les finaliseurs doivent appeler le finaliseur de leur classe de base|
|[CA2229](../code-quality/ca2229.md)|Implémentez des constructeurs de sérialisation|
|[CA2231](../code-quality/ca2231.md)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marquez les points d'entrée Windows Forms avec STAThread|
|[CA2235](../code-quality/ca2235.md)|Marquez tous les champs non sérialisés|
|[CA2236](../code-quality/ca2236.md)|Appelez les méthodes de la classe de base sur les types ISerializable|
|[CA2237](../code-quality/ca2237.md)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implémentez les méthodes de sérialisation comme il se doit|
|[CA2240](../code-quality/ca2240.md)|Implémentez ISerializable comme il se doit|
|[CA2241](../code-quality/ca2241.md)|Indiquer le nombre correct d'arguments dans les méthodes de mise en forme|
|[CA2242](../code-quality/ca2242.md)|Effectuez correctement des tests NaN|
|[CA1000](../code-quality/ca1000.md)|Ne pas déclarer de membres statiques sur les types génériques|
|[CA1002](../code-quality/ca1002.md)|Ne pas exposer de listes génériques|
|[CA1003](../code-quality/ca1003.md)|Utiliser les instances du gestionnaire d'événements génériques|
|[CA1004](../code-quality/ca1004.md)|Les méthodes génériques doivent fournir un paramètre de type|
|[CA1005](../code-quality/ca1005.md)|Éviter les paramètres excessifs sur les types génériques|
|[CA1006](../code-quality/ca1006.md)|Ne pas imbriquer les types génériques dans les signatures de membre|
|[CA1007](../code-quality/ca1007.md)|Utiliser des classes génériques lorsque cela est approprié|
|[CA1008](../code-quality/ca1008.md)|Les enums doivent avoir la valeur zéro|
|[CA1010](../code-quality/ca1010.md)|Les collections doivent implémenter une interface générique|
|[CA1011](../code-quality/ca1011.md)|Si possible, transmettez les types de base en tant que paramètres|
|[CA1012](../code-quality/ca1012.md)|Les types abstract ne doivent pas avoir de constructeurs|
|[CA1013](../code-quality/ca1013.md)|Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction|
|[CA1014](../code-quality/ca1014.md)|Marquer les assemblys avec CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017.md)|Marquer les assemblys avec ComVisibleAttribute|
|[CA1018](../code-quality/ca1018.md)|Marquer les attributs avec AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019.md)|Définir des accesseurs pour les arguments d'attribut|
|[CA1023](../code-quality/ca1023.md)|Les indexeurs ne doivent pas être multidimensionnels|
|[CA1024](../code-quality/ca1024.md)|Utiliser les propriétés lorsque cela est approprié|
|[CA1025](../code-quality/ca1025.md)|Remplacer les arguments répétitifs par un tableau params|
|[CA1026](../code-quality/ca1026.md)|Les paramètres par défaut ne doivent pas être utilisés|
|[CA1027](../code-quality/ca1027.md)|Marquer les enums avec FlagsAttribute|
|[CA1028](../code-quality/ca1028.md)|Enum Storage doit être Int32|
|[CA1030](../code-quality/ca1030.md)|Utiliser des événements lorsque cela est approprié|
|[CA1031](../code-quality/ca1031.md)|Ne pas intercepter des types d'exception générale|
|[CA1032](../code-quality/ca1032.md)|Implémenter des constructeurs d'exception standard|
|[CA1034](../code-quality/ca1034.md)|Les types imbriqués ne doivent pas être visibles|
|[CA1035](../code-quality/ca1035.md)|Les implémentations ICollection possèdent des membres fortement typés|
|[CA1036](../code-quality/ca1036.md)|Substituer les méthodes sur les types Comparable|
|[CA1038](../code-quality/ca1038.md)|Les énumérateurs doivent être fortement typés|
|[CA1039](../code-quality/ca1039.md)|Les listes sont fortement typées|
|[CA1041](../code-quality/ca1041.md)|Fournir un message ObsoleteAttribute|
|[CA1043](../code-quality/ca1043.md)|Utiliser un argument de chaîne ou intégral pour les indexeurs|
|[CA1044](../code-quality/ca1044.md)|Les propriétés ne doivent pas être en écriture seule|
|[CA1046](../code-quality/ca1046.md)|Ne pas surcharger l'opérateur égal à sur les types référence|
|[CA1047](../code-quality/ca1047.md)|Ne pas déclarer les membres protégés dans les types sealed|
|[CA1048](../code-quality/ca1048.md)|Ne pas déclarer les membres virtuels dans les types sealed|
|[CA1050](../code-quality/ca1050.md)|Déclarer les types dans des espaces de noms|
|[CA1051](../code-quality/ca1051.md)|Ne pas déclarer de champs d'instances visibles|
|[CA1052](../code-quality/ca1052.md)|Les types de conteneurs statiques doivent être sealed|
|[CA1053](../code-quality/ca1053.md)|Les types de conteneurs statiques ne doivent pas comporter de constructeur|
|[CA1054](../code-quality/ca1054.md)|Les paramètres URI ne doivent pas être des chaînes|
|[CA1055](../code-quality/ca1055.md)|Les valeurs de retour URI ne doivent pas être des chaînes|
|[CA1056](../code-quality/ca1056.md)|Les propriétés URI ne doivent pas être des chaînes|
|[CA1057](../code-quality/ca1057.md)|Les surcharges d'URI de chaîne appellent les surcharges de System.Uri|
|[CA1058](../code-quality/ca1058.md)|Les types ne doivent pas étendre certains types de base|
|[CA1059](../code-quality/ca1059.md)|Les membres ne doivent pas exposer certains types concrets|
|[CA1064](../code-quality/ca1064.md)|Les exceptions doivent être publiques|
|[CA1500](../code-quality/ca1500.md)|Les noms de variables ne doivent pas être identiques aux noms de champs|
|[CA1502](../code-quality/ca1502.md)|Éviter l'excès de complexité|
|[CA1708](../code-quality/ca1708.md)|Les identificateurs ne doivent pas différer uniquement par leur casse|
|[CA1716](../code-quality/ca1716.md)|Les identificateurs ne doivent pas correspondre à des mots clés|
|[CA1801](../code-quality/ca1801.md)|Passez en revue les paramètres inutilisés|
|[CA1804](../code-quality/ca1804.md)|Supprimez les variables locales inutilisées|
|[CA1809](../code-quality/ca1809.md)|Évitez le surplus de variables locales|
|[CA1810](../code-quality/ca1810.md)|Initialisez les champs statiques de type référence en ligne|
|[CA1811](../code-quality/ca1811.md)|Évitez le recours à du code privé non appelé|
|[CA1812](../code-quality/ca1812.md)|Évitez les classes internes non instanciées|
|[CA1813](../code-quality/ca1813.md)|Évitez les attributs unsealed|
|[CA1814](../code-quality/ca1814.md)|Utilisez des tableaux en escalier à la place de tableaux multidimensionnels|
|[CA1815](../code-quality/ca1815.md)|Remplacez Equals et l'opérateur égal à dans les types valeur|
|[CA1819](../code-quality/ca1819.md)|Les propriétés ne doivent pas retourner des tableaux|
|[CA1820](../code-quality/ca1820.md)|Vérifiez la présence de chaînes vides par la longueur de chaîne|
|[CA1822](../code-quality/ca1822.md)|Marquez les membres comme static|
|[CA1823](../code-quality/ca1823.md)|Évitez les champs privés inutilisés|
|[CA2201](../code-quality/ca2201.md)|Ne levez pas des types d'exceptions réservés|
|[CA2205](../code-quality/ca2205.md)|Utilisez des équivalents managés de l'API Win32|
|[CA2208](../code-quality/ca2208.md)|Instanciez les exceptions d'argument comme il se doit|
|[CA2211](../code-quality/ca2211.md)|Les champs non constants ne doivent pas être visibles|
|[CA2217](../code-quality/ca2217.md)|Ne marquez pas les enums avec l'attribut FlagsAttribute|
|[CA2219](../code-quality/ca2219.md)|Ne pas lever d'exceptions dans les clauses d'exception|
|[CA2221](../code-quality/ca2221.md)|Les finaliseurs doivent être protégés|
|[CA2222](../code-quality/ca2222.md)|Ne réduisez pas la visibilité des membres hérités|
|[CA2223](../code-quality/ca2223.md)|Les membres ne doivent pas différer uniquement par leur type de retour|
|[CA2224](../code-quality/ca2224.md)|Remplacez Equals au moment de surcharger l'opérateur égal|
|[CA2225](../code-quality/ca2225.md)|Les surcharges d'opérateur offrent d'autres méthodes nommées|
|[CA2226](../code-quality/ca2226.md)|Les opérateurs doivent contenir des surcharges symétriques|
|[CA2227](../code-quality/ca2227.md)|Les propriétés de collection doivent être en lecture seule|
|[CA2230](../code-quality/ca2230.md)|Utilisez le mot clé params pour les arguments de variables|
|[CA2234](../code-quality/ca2234.md)|Passez des objets System.Uri à la place de chaînes|
|[CA2239](../code-quality/ca2239.md)|Spécifiez des méthodes de désérialisation pour les champs facultatifs|
|[CA1020](../code-quality/ca1020.md)|Éviter les espaces de noms comportant peu de types|
|[CA1021](../code-quality/ca1021.md)|Éviter les paramètres out|
|[CA1040](../code-quality/ca1040.md)|Éviter les interfaces vides|
|[CA1045](../code-quality/ca1045.md)|Ne pas passer de types par référence|
|[CA1062](../code-quality/ca1062.md)|Valider les arguments de méthodes publiques|
|[CA1501](../code-quality/ca1501.md)|Éviter l'excès d'héritage|
|[CA1504](../code-quality/ca1504.md)|Vérifier les noms de champs trompeurs|
|[CA1505](../code-quality/ca1505.md)|Éviter le code impossible à maintenir|
|[CA1506](../code-quality/ca1506.md)|Éviter les couplages de classe excessifs|
|[CA1700](../code-quality/ca1700.md)|Ne nommez pas les valeurs enum 'Reserved'|
|[CA1701](../code-quality/ca1701.md)|La casse des mots composés de la chaîne de ressources doit être correcte|
|[CA1702](../code-quality/ca1702.md)|La casse des mots composés doit être correcte|
|[CA1703](../code-quality/ca1703.md)|L'orthographe des chaînes de ressources doit être correcte|
|[CA1704](../code-quality/ca1704.md)|L'orthographe des identificateurs doit être correcte|
|[CA1707](../code-quality/ca1707.md)|Les identificateurs ne doivent pas contenir de traits de soulignement|
|[CA1709](../code-quality/ca1709.md)|La casse des identificateurs doit être correcte|
|[CA1710](../code-quality/ca1710.md)|Les identificateurs doivent être dotés d'un suffixe correct|
|[CA1711](../code-quality/ca1711.md)|Les identificateurs ne doivent pas porter un suffixe incorrect|
|[CA1712](../code-quality/ca1712.md)|N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum|
|[CA1713](../code-quality/ca1713.md)|Les événements ne doivent pas être munis d'un préfixe Before ou After|
|[CA1714](../code-quality/ca1714.md)|Les noms des enums Flags doivent être au pluriel|
|[CA1715](../code-quality/ca1715.md)|Les identificateurs doivent être dotés d'un préfixe correct|
|[CA1717](../code-quality/ca1717.md)|Seuls les noms des enums FlagsAttribute doivent être au pluriel|
|[CA1719](../code-quality/ca1719.md)|Les noms des paramètres ne doivent pas être identiques aux noms des membres|
|[CA1720](../code-quality/ca1720.md)|Les identificateurs ne doivent pas contenir de noms de types|
|[CA1721](../code-quality/ca1721.md)|Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get|
|[CA1722](../code-quality/ca1722.md)|Les identificateurs ne doivent pas porter un préfixe incorrect|
|[CA1724](../code-quality/ca1724.md)|Les noms de types ne doivent pas être identiques aux espaces de noms|
|[CA1725](../code-quality/ca1725.md)|Les noms des paramètres doivent correspondre à la déclaration de base|
|[CA1726](../code-quality/ca1726.md)|Utilisez les termes par défaut|
|[CA2204](../code-quality/ca2204.md)|Les littéraux doivent être orthographiés correctement|
