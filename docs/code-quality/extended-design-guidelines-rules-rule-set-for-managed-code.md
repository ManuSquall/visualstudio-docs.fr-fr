---
title: "Ensemble de r&#232;gles de r&#232;gles de conception &#233;tendue pour le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Ensemble de r&#232;gles de r&#232;gles de conception &#233;tendue pour le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'ensemble de règles intitulé Règles de conception étendue Microsoft s'appuie sur les directives des Règles de conception de base pour optimiser la résolution des problèmes d'utilisation et de maintenance signalés,  en mettant l'accent sur l'aide liée à l'affectation de noms.  Vous devez envisager d'inclure cet ensemble de règles si votre projet comprend du code de bibliothèque ou si vous souhaitez appliquer les normes les plus élevées afin d'écrire du code facile à gérer.  
  
 Les Règles de conception étendue intègrent toutes les Règles de conception de base Microsoft.  Les Règles de conception de base intègrent toutes les Règles Microsoft minimales recommandées.  Pour plus d'informations, consultez [Ensemble de règles de règles de conception de base pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) et [Ensemble de règles des règles recommandées managées pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 Le tableau suivant décrit toutes les règles de l'ensemble intitulé Règles de conception étendue Microsoft.  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Déclarer les gestionnaires d'événements correctement|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marquer les assemblies avec AssemblyVersionAttribute|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|Les méthodes d'interface doivent pouvoir être appelées par les types enfants|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Les types qui possèdent des ressources natives doivent être supprimables|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Déplacer les P\/Invokes vers une classe NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Ne pas masquer les méthodes de la classe de base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implémenter IDisposable correctement|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Ne pas lever d'exceptions dans des emplacements inattendus|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|Éviter les accélérateurs en double|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|Des points d'entrée P\/Invoke devraient exister|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|Les P\/Invokes ne devraient pas être visibles|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Les types auto\-structurants ne devraient pas être visibles par COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Appeler GetLastError immédiatement après P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Les types de base de type visibles par COM devraient être visibles par COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Les méthodes d'inscription COM devraient correspondre|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Déclarer correctement les méthodes P\/Invokes|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimer les finaliseurs vides|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Les champs de type valeur doivent être portables|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Les déclarations P\/Invokes doivent être portables|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|Ne définissez pas un verrou sur des objets à identité faible|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Rechercher des failles de sécurité dans les requêtes SQL|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne devraient pas être visibles|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Les types sécurisés ne devraient pas exposer de champs|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sécurité de la méthode doit être un sur\-ensemble du type|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de surcharge doivent être identiques au composant de base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|Les demandes de liaison de types nécessitent des demandes d'héritage|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité peuvent ne pas participer à l'équivalence des types|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Les méthodes doivent garder une transparence consistante lors de la surcharge des méthodes de base|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne doivent pas répondre aux LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparents pourrait ne pas utiliser les recommandations de sécruité|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler du code natif|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Levez à nouveau une exception pour conserver les détails de la pile|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Ne pas supprimer des objets plusieurs fois|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Initialisez les champs statiques des types valeur sur une ligne|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Ne marquez pas les composants pris en charge avec WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Les champs pouvant être supprimés doivent l'être|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|N'appelez pas de méthodes substituables dans les constructeurs|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Les types pouvant être supprimés devraient déclarer un finaliseur|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Les finaliseurs devraient appeler le finaliseur de leur classe de base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implémentez des constructeurs de sérialisation|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surcharger l'opérateur égal \(equals\) en surchargeant ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Marquez les points d'entrée Windows Forms avec STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marquez tous les champs non sérialisables|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Appelez les méthodes de la classe de base sur les types ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marquer les types ISerializable avec SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implémentez les méthodes de sérialisation correctement|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|Implémentez correctement ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Fournissez des arguments corrects aux méthodes de mise en forme|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Effectuez correctement des tests NaN|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Ne pas déclarer de membres statiques sur les types génériques|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|Ne pas exposer de listes génériques|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|Ne pas utiliser d'instances du gestionnaire d'événements génériques|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Les méthodes génériques doivent fournir un paramètre de type|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Éviter les paramètres excessifs sur les types génériques|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Ne pas imbriquer les types génériques dans les signatures de membre|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utiliser des classes génériques lorsque cela est approprié|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Les enums doivent avoir la valeur zéro|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Les collections doivent implémenter une interface générique|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Si possible, transmettez les types de base en tant que paramètres|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Les types abstraits ne doivent pas avoir de constructeurs|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marquer les assemblies avec CLSCompliantAttribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marquer les assemblies avec ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marquer les attributs avec AttributeUsageAttribute|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Définir des accesseurs pour les arguments d'attribut|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Les indexeurs ne doivent pas être multidimensionnels|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utiliser les propriétés lorsque cela est approprié|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|Remplacer les arguments répétitifs par un tableau de paramètres|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|Les paramètres par défaut ne doivent pas être utilisés|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marquer les enums avec FlagsAttribute|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Le stockage d'Enum doit être Int32|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|Utiliser des événements lorsque cela est approprié|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|Ne pas intercepter des types d'exception générale|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implémenter des constructeurs d'exception standard|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Les types imbriqués ne doivent pas être visibles|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Les implémentations de ICollection possèdent des membres fortement typés|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Substituer les méthodes sur les types comparables|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Les énumérateurs doivent être fortement typés|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Les listes sont fortement typées|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|Fournir un message ObsoleteAttribute|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utiliser un argument de chaîne ou intégral pour les indexeurs|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Les propriétés ne doivent pas être en écriture seule|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Ne pas surcharger l'opérateur égal sur les types référence|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Ne pas déclarer des membres protégés dans les types sealed|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Ne pas déclarer les membres virtuels dans les types sealed|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Déclarer les types dans des espaces de noms|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Ne pas déclarer de champs d'instances visibles|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Les types de conteneurs statiques doivent être sealed|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Les types de conteneurs statiques ne doivent pas comporter de constructeur|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Les paramètres Uri ne doivent pas être des chaînes|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Les valeurs de retour Uri ne doivent pas être des chaînes|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Les propriétés Uri ne doivent pas être des chaînes|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Les surcharges d'uri de chaîne appellent les surcharges de System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Les types ne doivent pas étendre certains types de base|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Les membres ne doivent pas exposer certains types concrets|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|Les exceptions doivent être publiques|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|Les noms de variables ne doivent pas être identiques aux noms de champs|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Éviter l'excès de complexité|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Les identificateurs ne doivent pas différer que par leur casse|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Les identificateurs ne doivent pas correspondre à des mots clés|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|Passez en revue les paramètres inutilisés|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Supprimez les variables locales inutilisées|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Évitez le surplus de variables locales|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Initialisez les champs statiques de type référence en ligne|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Évitez le recours à du code privé non appelé|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|Évitez les classes internes non instanciées|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Évitez les attributs unsealed|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Utilisez des tableaux en escalier à la place de tableaux multidimensionnels|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|Surchargez Equals et l'opérateur égal dans les types valeur|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Les propriétés ne doivent pas retourner de tableaux|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Vérifiez la présence de chaînes vides en utilisant la longueur de chaîne|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|Marquez les membres comme static|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Évitez les champs privés inutilisés|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ne levez pas des types d'exceptions réservés|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilisez des équivalents managés de l'API Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Instanciez les exceptions d'argument comme il se doit|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Les champs non constants ne doivent pas être visibles|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Ne pas marquer les enums avec FlagsAttribute|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|Ne pas lever d'exceptions dans les clauses d'exception|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Les finaliseurs doivent être protégés|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Ne réduisez pas la visibilité des membres hérités|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|Les membres ne doivent pas différer uniquement par leur type de retour|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Remplacez Equals au moment de surcharger l'opérateur égal|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|Les surcharges d'opérateur offrent d'autres méthodes nommées|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Les opérateurs doivent contenir des surcharges symétriques|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Les propriétés de collection doivent être en lecture seule|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilisez le mot clé params pour les arguments de variables|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|Passez des objets System.Uri à la place de chaînes|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Spécifiez des méthodes de désérialisation pour les champs facultatifs|  
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Éviter les espaces de noms comportant peu de types|  
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Éviter les paramètres out|  
|[CA1040](../Topic/CA1040:%20Avoid%20empty%20interfaces.md)|Éviter les interfaces vides|  
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Ne pas passer de types par référence|  
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Valider les arguments de méthodes publiques|  
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Éviter l'excès d'héritage|  
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Vérifier les noms de champs trompeurs|  
|[CA1505](../Topic/CA1505:%20Avoid%20unmaintainable%20code.md)|Éviter le code impossible à maintenir|  
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Éviter les couplages de classe excessifs|  
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Ne nommez pas les valeurs enum 'Reserved'|  
|[CA1701](../Topic/CA1701:%20Resource%20string%20compound%20words%20should%20be%20cased%20correctly.md)|La casse des mots composés de chaînes de ressources doit être correcte|  
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|La casse des mots composés doit être correcte|  
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|L'orthographe des chaînes de ressources doit être correcte|  
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Les identificateurs doivent être correctement orthographiés|  
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Les identificateurs ne doivent pas contenir de traits de soulignement|  
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|La casse des identificateurs doit être correcte|  
|[CA1710](../Topic/CA1710:%20Identifiers%20should%20have%20correct%20suffix.md)|Les identificateurs doivent être dotés d'un suffixe correct|  
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Les identificateurs ne doivent pas porter un suffixe incorrect|  
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|N'ajoutez pas le nom de type en guise de préfixe à des valeurs enum|  
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Les événements ne doivent pas être munis d'un préfixe Before ou After|  
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Les énumérations d'indicateurs doivent avoir des noms au pluriel|  
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Les identificateurs doivent être dotés d'un préfixe correct|  
|[CA1717](../Topic/CA1717:%20Only%20FlagsAttribute%20enums%20should%20have%20plural%20names.md)|Seuls les noms des enums FlagsAttribute doivent être au pluriel|  
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Les noms des paramètres ne doivent pas être identiques aux noms des membres|  
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Les identificateurs ne doivent pas contenir de noms de types|  
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Les noms des propriétés ne doivent pas être identiques à ceux des méthodes Get|  
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Les identificateurs ne doivent pas porter un préfixe incorrect|  
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|les noms de types ne doivent pas être identiques aux espaces de noms|  
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Les noms de paramètres doivent correspondre à la déclaration de base|  
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Utilisez les termes par défaut|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Les littéraux doivent être correctement orthographiés|