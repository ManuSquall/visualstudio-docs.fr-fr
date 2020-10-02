---
title: Ensemble de règles de règles de conception de base pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2bf7542d94b16042df27ec8b780cc93c9061d6e8
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659125"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de conception de base pour le code managé

Vous pouvez utiliser l’ensemble de règles des règles de conception de base de Microsoft pour vous concentrer sur la compréhension et l’utilisation de votre code. Vous devez inclure cet ensemble de règles si votre projet inclut du code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour le code qui est facile à gérer.

Les règles de conception de base incluent toutes les règles dans l’ensemble de règles des [règles recommandées managées](managed-recommended-rules-rule-set-for-managed-code.md) .

Le tableau suivant décrit toutes les règles de l’ensemble de règles des règles de conception de base de Microsoft.

|Règle|Description|
|----------|-----------------|
|[CA1000](/dotnet/fundamentals/code-analysis/quality-rules/ca1000)|Ne pas déclarer de membres statiques sur les types génériques|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1002](/dotnet/fundamentals/code-analysis/quality-rules/ca1002)|Ne pas exposer de listes génériques|
|[CA1003](/dotnet/fundamentals/code-analysis/quality-rules/ca1003)|Utiliser les instances du gestionnaire d'événements génériques|
|[CA1004](../code-quality/ca1004.md)|Les méthodes génériques doivent fournir un paramètre de type|
|[CA1005](/dotnet/fundamentals/code-analysis/quality-rules/ca1005)|Éviter les paramètres excessifs sur les types génériques|
|[CA1006](../code-quality/ca1006.md)|Ne pas imbriquer les types génériques dans les signatures de membre|
|[CA1007](../code-quality/ca1007.md)|Utiliser des classes génériques lorsque cela est approprié|
|[CA1008](/dotnet/fundamentals/code-analysis/quality-rules/ca1008)|Les enums doivent avoir la valeur zéro|
|[CA1009](../code-quality/ca1009.md)|Déclarer les gestionnaires d'événements correctement|
|[CA1010](/dotnet/fundamentals/code-analysis/quality-rules/ca1010)|Les collections doivent implémenter une interface générique|
|[CA1011](../code-quality/ca1011.md)|Si possible, transmettez les types de base en tant que paramètres|
|[CA1012](/dotnet/fundamentals/code-analysis/quality-rules/ca1012)|Les types abstract ne doivent pas avoir de constructeurs|
|[CA1013](../code-quality/ca1013.md)|Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction|
|[CA1014](/dotnet/fundamentals/code-analysis/quality-rules/ca1014)|Marquer les assemblys avec CLSCompliantAttribute|
|[CA1016](/dotnet/fundamentals/code-analysis/quality-rules/ca1016)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1017](/dotnet/fundamentals/code-analysis/quality-rules/ca1017)|Marquer les assemblys avec ComVisibleAttribute|
|[CA1018](/dotnet/fundamentals/code-analysis/quality-rules/ca1018)|Marquer les attributs avec AttributeUsageAttribute|
|[CA1019](/dotnet/fundamentals/code-analysis/quality-rules/ca1019)|Définir des accesseurs pour les arguments d'attribut|
|[CA1023](../code-quality/ca1023.md)|Les indexeurs ne doivent pas être multidimensionnels|
|[CA1024](/dotnet/fundamentals/code-analysis/quality-rules/ca1024)|Utiliser les propriétés lorsque cela est approprié|
|[CA1025](../code-quality/ca1025.md)|Remplacer les arguments répétitifs par un tableau params|
|[CA1026](../code-quality/ca1026.md)|Les paramètres par défaut ne doivent pas être utilisés|
|[CA1027](/dotnet/fundamentals/code-analysis/quality-rules/ca1027)|Marquer les enums avec FlagsAttribute|
|[CA1028](/dotnet/fundamentals/code-analysis/quality-rules/ca1028)|Enum Storage doit être Int32|
|[CA1030](/dotnet/fundamentals/code-analysis/quality-rules/ca1030)|Utiliser des événements lorsque cela est approprié|
|[CA1031](/dotnet/fundamentals/code-analysis/quality-rules/ca1031)|Ne pas intercepter des types d'exception générale|
|[CA1032](/dotnet/fundamentals/code-analysis/quality-rules/ca1032)|Implémenter des constructeurs d'exception standard|
|[CA1033](/dotnet/fundamentals/code-analysis/quality-rules/ca1033)|Les méthodes d'interface doivent pouvoir être appelées par les types enfants|
|[CA1034](/dotnet/fundamentals/code-analysis/quality-rules/ca1034)|Les types imbriqués ne doivent pas être visibles|
|[CA1035](../code-quality/ca1035.md)|Les implémentations ICollection possèdent des membres fortement typés|
|[CA1036](/dotnet/fundamentals/code-analysis/quality-rules/ca1036)|Substituer les méthodes sur les types Comparable|
|[CA1038](../code-quality/ca1038.md)|Les énumérateurs doivent être fortement typés|
|[CA1039](../code-quality/ca1039.md)|Les listes sont fortement typées|
|[CA1041](/dotnet/fundamentals/code-analysis/quality-rules/ca1041)|Fournir un message ObsoleteAttribute|
|[CA1043](/dotnet/fundamentals/code-analysis/quality-rules/ca1043)|Utiliser un argument de chaîne ou intégral pour les indexeurs|
|[CA1044](/dotnet/fundamentals/code-analysis/quality-rules/ca1044)|Les propriétés ne doivent pas être en écriture seule|
|[CA1046](/dotnet/fundamentals/code-analysis/quality-rules/ca1046)|Ne pas surcharger l'opérateur égal à sur les types référence|
|[CA1047](/dotnet/fundamentals/code-analysis/quality-rules/ca1047)|Ne pas déclarer les membres protégés dans les types sealed|
|[CA1048](../code-quality/ca1048.md)|Ne pas déclarer les membres virtuels dans les types sealed|
|[CA1049](../code-quality/ca1049.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1050](/dotnet/fundamentals/code-analysis/quality-rules/ca1050)|Déclarer les types dans des espaces de noms|
|[CA1051](/dotnet/fundamentals/code-analysis/quality-rules/ca1051)|Ne pas déclarer de champs d'instances visibles|
|[CA1052](/dotnet/fundamentals/code-analysis/quality-rules/ca1052)|Les types de conteneurs statiques doivent être sealed|
|[CA1053](/dotnet/fundamentals/code-analysis/quality-rules/ca1053)|Les types de conteneurs statiques ne doivent pas comporter de constructeur|
|[CA1054](/dotnet/fundamentals/code-analysis/quality-rules/ca1054)|Les paramètres URI ne doivent pas être des chaînes|
|[CA1055](/dotnet/fundamentals/code-analysis/quality-rules/ca1055)|Les valeurs de retour URI ne doivent pas être des chaînes|
|[CA1056](/dotnet/fundamentals/code-analysis/quality-rules/ca1056)|Les propriétés URI ne doivent pas être des chaînes|
|[CA1057](../code-quality/ca1057.md)|Les surcharges d'URI de chaîne appellent les surcharges de System.Uri|
|[CA1058](/dotnet/fundamentals/code-analysis/quality-rules/ca1058)|Les types ne doivent pas étendre certains types de base|
|[CA1059](../code-quality/ca1059.md)|Les membres ne doivent pas exposer certains types concrets|
|[CA1060](/dotnet/fundamentals/code-analysis/quality-rules/ca1060)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](/dotnet/fundamentals/code-analysis/quality-rules/ca1061)|Ne pas masquer les méthodes de la classe de base|
|[CA1063](/dotnet/fundamentals/code-analysis/quality-rules/ca1063)|Implémenter IDisposable correctement|
|[CA1064](/dotnet/fundamentals/code-analysis/quality-rules/ca1064)|Les exceptions doivent être publiques|
|[CA1065](/dotnet/fundamentals/code-analysis/quality-rules/ca1065)|Ne pas lever d'exceptions dans les emplacements inattendus|
|[CA1301](../code-quality/ca1301.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400.md)|Des points d'entrée P/Invoke doivent exister|
|[CA1401](/dotnet/fundamentals/code-analysis/quality-rules/ca1401)|Les P/Invoke ne doivent pas être visibles|
|[CA1403](../code-quality/ca1403.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Les types de base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410.md)|Les méthodes d'inscription COM doivent être mises en correspondance|
|[CA1415](../code-quality/ca1415.md)|Déclarer correctement les méthodes P/Invoke|
|[CA1500](../code-quality/ca1500.md)|Les noms de variables ne doivent pas être identiques aux noms de champs|
|[CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)|Éviter l'excès de complexité|
|[CA1708](/dotnet/fundamentals/code-analysis/quality-rules/ca1708)|Les identificateurs ne doivent pas différer uniquement par leur casse|
|[CA1716](/dotnet/fundamentals/code-analysis/quality-rules/ca1716)|Les identificateurs ne doivent pas correspondre à des mots clés|
|[CA1801](/dotnet/fundamentals/code-analysis/quality-rules/ca1801)|Passez en revue les paramètres inutilisés|
|[CA1804](../code-quality/ca1804.md)|Supprimez les variables locales inutilisées|
|[CA1809](../code-quality/ca1809.md)|Évitez le surplus de variables locales|
|[CA1810](/dotnet/fundamentals/code-analysis/quality-rules/ca1810)|Initialisez les champs statiques de type référence en ligne|
|[CA1811](../code-quality/ca1811.md)|Évitez le recours à du code privé non appelé|
|[CA1812](/dotnet/fundamentals/code-analysis/quality-rules/ca1812)|Évitez les classes internes non instanciées|
|[CA1813](/dotnet/fundamentals/code-analysis/quality-rules/ca1813)|Évitez les attributs unsealed|
|[CA1814](/dotnet/fundamentals/code-analysis/quality-rules/ca1814)|Utilisez des tableaux en escalier à la place de tableaux multidimensionnels|
|[CA1815](/dotnet/fundamentals/code-analysis/quality-rules/ca1815)|Remplacez Equals et l'opérateur égal à dans les types valeur|
|[CA1819](/dotnet/fundamentals/code-analysis/quality-rules/ca1819)|Les propriétés ne doivent pas retourner des tableaux|
|[CA1820](/dotnet/fundamentals/code-analysis/quality-rules/ca1820)|Vérifiez la présence de chaînes vides par la longueur de chaîne|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Supprimez les finaliseurs vides|
|[CA1822](/dotnet/fundamentals/code-analysis/quality-rules/ca1822)|Marquez les membres comme static|
|[CA1823](/dotnet/fundamentals/code-analysis/quality-rules/ca1823)|Évitez les champs privés inutilisés|
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
|[CA2201](/dotnet/fundamentals/code-analysis/quality-rules/ca2201)|Ne levez pas des types d'exceptions réservés|
|[CA2202](../code-quality/ca2202.md)|Ne pas supprimer d'objets plusieurs fois|
|[CA2205](../code-quality/ca2205.md)|Utilisez des équivalents managés de l'API Win32|
|[CA2207](/dotnet/fundamentals/code-analysis/quality-rules/ca2207)|Initialisez les champs statiques des types valeur en ligne|
|[CA2208](/dotnet/fundamentals/code-analysis/quality-rules/ca2208)|Instanciez les exceptions d'argument comme il se doit|
|[CA2211](/dotnet/fundamentals/code-analysis/quality-rules/ca2211)|Les champs non constants ne doivent pas être visibles|
|[CA2212](../code-quality/ca2212.md)|Ne marquez pas les composants pris en charge avec webMethod|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Les champs pouvant être supprimés doivent l’être|
|[CA2214](/dotnet/fundamentals/code-analysis/quality-rules/ca2214)|N'appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](/dotnet/fundamentals/code-analysis/quality-rules/ca2216)|Les types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2217](/dotnet/fundamentals/code-analysis/quality-rules/ca2217)|Ne marquez pas les enums avec l'attribut FlagsAttribute|
|[CA2219](/dotnet/fundamentals/code-analysis/quality-rules/ca2219)|Ne pas lever d'exceptions dans les clauses d'exception|
|[CA2220](../code-quality/ca2220.md)|Les finaliseurs doivent appeler le finaliseur de leur classe de base|
|[CA2221](../code-quality/ca2221.md)|Les finaliseurs doivent être protégés|
|[CA2222](../code-quality/ca2222.md)|Ne réduisez pas la visibilité des membres hérités|
|[CA2223](../code-quality/ca2223.md)|Les membres ne doivent pas différer uniquement par leur type de retour|
|[CA2224](../code-quality/ca2224.md)|Remplacez Equals au moment de surcharger l'opérateur égal|
|[CA2225](/dotnet/fundamentals/code-analysis/quality-rules/ca2225)|Les surcharges d'opérateur offrent d'autres méthodes nommées|
|[CA2226](/dotnet/fundamentals/code-analysis/quality-rules/ca2226)|Les opérateurs doivent contenir des surcharges symétriques|
|[CA2227](/dotnet/fundamentals/code-analysis/quality-rules/ca2227)|Les propriétés de collection doivent être en lecture seule|
|[CA2229](/dotnet/fundamentals/code-analysis/quality-rules/ca2229)|Implémentez des constructeurs de sérialisation|
|[CA2230](../code-quality/ca2230.md)|Utilisez le mot clé params pour les arguments de variables|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Marquez les points d'entrée Windows Forms avec STAThread|
|[CA2234](/dotnet/fundamentals/code-analysis/quality-rules/ca2234)|Passez des objets System.Uri à la place de chaînes|
|[CA2235](/dotnet/fundamentals/code-analysis/quality-rules/ca2235)|Marquez tous les champs non sérialisés|
|[CA2236](../code-quality/ca2236.md)|Appelez les méthodes de la classe de base sur les types ISerializable|
|[CA2237](/dotnet/fundamentals/code-analysis/quality-rules/ca2237)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Implémentez les méthodes de sérialisation comme il se doit|
|[CA2239](../code-quality/ca2239.md)|Spécifiez des méthodes de désérialisation pour les champs facultatifs|
|[CA2240](../code-quality/ca2240.md)|Implémentez ISerializable comme il se doit|
|[CA2241](/dotnet/fundamentals/code-analysis/quality-rules/ca2241)|Indiquer le nombre correct d'arguments dans les méthodes de mise en forme|
|[CA2242](/dotnet/fundamentals/code-analysis/quality-rules/ca2242)|Effectuez correctement des tests NaN|
