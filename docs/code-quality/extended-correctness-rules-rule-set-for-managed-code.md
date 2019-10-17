---
title: Ensemble de règles de règles de vérification étendue pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc279f0ae9e0420810e12c21f5f7cf29de0d15e7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449155"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de vérification étendue pour le code managé

L’ensemble de règles de règles de vérification étendue Microsoft maximise les erreurs d’utilisation de la logique et de l’infrastructure qui sont signalées par l’analyse du code. Une importance supplémentaire est placée sur des scénarios spécifiques tels que l’interopérabilité COM et les applications mobiles. Vous devez envisager d’inclure cet ensemble de règles si l’un de ces scénarios s’applique à votre projet ou de rechercher d’autres problèmes dans votre projet.

L’ensemble de règles des règles de vérification étendue Microsoft inclut les règles qui se trouvent dans l’ensemble de règles de [règles de vérification de base](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) , qui contient les règles qui se trouvent dans l’ensemble de règles des [règles recommandées managées](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md) .

Le tableau suivant décrit toutes les règles de l’ensemble de règles des règles de vérification étendue Microsoft.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Déclarer les gestionnaires d'événements correctement|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Les méthodes d'interface doivent pouvoir être appelées par les types enfants|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Ne pas masquer les méthodes de la classe de base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implémenter IDisposable correctement|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Ne pas lever d'exceptions dans les emplacements inattendus|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Des points d'entrée P/Invoke doivent exister|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|Les P/Invoke ne doivent pas être visibles|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Les types de base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Les méthodes d'inscription COM doivent être mises en correspondance|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Déclarer correctement les méthodes P/Invoke|
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Les enums doivent avoir la valeur zéro|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Ne pas passer de littéraux en paramètres localisés|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normaliser les chaînes en majuscules|
|[CA1806](../code-quality/ca1806.md)|N'ignorez pas les résultats des méthodes|
|[CA1816](../code-quality/ca1816.md)|Appeler GC.SuppressFinalize correctement|
|[CA1819](../code-quality/ca1819.md)|Les propriétés ne doivent pas retourner des tableaux|
|[CA1820](../code-quality/ca1820.md)|Vérifiez la présence de chaînes vides par la longueur de chaîne|
|[CA1903](../code-quality/ca1903.md)|Utiliser uniquement l'API à partir du Framework cible|
|[CA2004](../code-quality/ca2004.md)|Supprimez les appels à GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Utilisez SafeHandle pour encapsuler les ressources natives|
|[CA2102](../code-quality/ca2102.md)|Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux|
|[CA2104](../code-quality/ca2104.md)|Ne déclarez pas les types référence mutables en lecture seule|
|[CA2105](../code-quality/ca2105.md)|Les champs de tableau ne doivent pas être en lecture seule|
|[CA2106](../code-quality/ca2106.md)|Assertions sécurisées|
|[CA2115](../code-quality/ca2115.md)|Appelez GC.KeepAlive lorsque vous utilisez des ressources natives|
|[CA2119](../code-quality/ca2119.md)|Scellez les méthodes qui satisfont les interfaces privées|
|[CA2120](../code-quality/ca2120.md)|Sécurisez les constructeurs de sérialisation|
|[CA2121](../code-quality/ca2121.md)|Les constructeurs statiques doivent être privés|
|[CA2130](../code-quality/ca2130.md)|Les constantes critiques de sécurité doivent être transparentes|
|[CA2205](../code-quality/ca2205.md)|Utilisez des équivalents managés de l'API Win32|
|[CA2215](../code-quality/ca2215.md)|Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base|
|[CA2221](../code-quality/ca2221.md)|Les finaliseurs doivent être protégés|
|[CA2222](../code-quality/ca2222.md)|Ne réduisez pas la visibilité des membres hérités|
|[CA2223](../code-quality/ca2223.md)|Les membres ne doivent pas différer uniquement par leur type de retour|
|[CA2224](../code-quality/ca2224.md)|Remplacez Equals au moment de surcharger l'opérateur égal|
|[CA2226](../code-quality/ca2226.md)|Les opérateurs doivent contenir des surcharges symétriques|
|[CA2227](../code-quality/ca2227.md)|Les propriétés de collection doivent être en lecture seule|
|[CA2239](../code-quality/ca2239.md)|Spécifiez des méthodes de désérialisation pour les champs facultatifs|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implémenter des constructeurs d'exception standard|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Les paramètres URI ne doivent pas être des chaînes|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Les valeurs de retour URI ne doivent pas être des chaînes|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Les propriétés URI ne doivent pas être des chaînes|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Les surcharges d'URI de chaîne appellent les surcharges de System.Uri|
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Éviter les surcharges dans les interfaces COM visibles|
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Éviter les arguments Int64 pour les clients Visual Basic 6|
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Éviter les membres statiques dans les types visibles par COM|
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Ne pas utiliser le paramètre AutoDual ClassInterfaceType|
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Les types visibles par Com doivent pouvoir être créés|
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Les méthodes d'inscription COM ne doivent pas être visibles|
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Marquer les interfaces ComSource comme IDispatch|
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Éviter les champs non publics dans les types valeur visibles par COM|
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Marquer les arguments P/Invoke booléens comme MarshalAs|
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|Ne pas utiliser de priorité de processus inactif|
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Ne pas utiliser de minuteries qui empêchent les changements d'état de l'alimentation|
|[CA1824](../code-quality/ca1824.md)|Marquer les assemblys avec NeutralResourcesLanguageAttribute|
|[CA2001](../code-quality/ca2001.md)|Évitez d'appeler des méthodes susceptibles de poser des problèmes|
|[CA2003](../code-quality/ca2003.md)|Ne traitez pas les fibres comme des threads|
|[CA2135](../code-quality/ca2135.md)|Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Les membres ne doivent pas avoir d'annotations de transparence conflictuelles|
|[CA2139](../code-quality/ca2139.md)|Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions|
|[CA2142](../code-quality/ca2142.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|
|[CA2144](../code-quality/ca2144.md)|Le code transparent ne doit pas charger d'assemblys depuis des tableaux d'octets|
|[CA2145](../code-quality/ca2145.md)|Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|
|[CA2204](../code-quality/ca2204.md)|Les littéraux doivent être orthographiés correctement|
|[CA2211](../code-quality/ca2211.md)|Les champs non constants ne doivent pas être visibles|
|[CA2217](../code-quality/ca2217.md)|Ne marquez pas les enums avec l'attribut FlagsAttribute|
|[CA2218](../code-quality/ca2218.md)|Remplacez GetHashCode au moment de remplacer Equals|
|[CA2219](../code-quality/ca2219.md)|Ne pas lever d'exceptions dans les clauses d'exception|
|[CA2225](../code-quality/ca2225.md)|Les surcharges d'opérateur offrent d'autres méthodes nommées|
|[CA2228](../code-quality/ca2228.md)|Ne distribuez pas des formats de ressources non commercialisés|
|[CA2230](../code-quality/ca2230.md)|Utilisez le mot clé params pour les arguments de variables|
|[CA2233](../code-quality/ca2233.md)|Les opérations ne doivent pas déborder|
|[CA2234](../code-quality/ca2234.md)|Passez des objets System.Uri à la place de chaînes|
|[CA2243](../code-quality/ca2243.md)|Les littéraux de chaîne d'attribut doivent être analysés correctement|
