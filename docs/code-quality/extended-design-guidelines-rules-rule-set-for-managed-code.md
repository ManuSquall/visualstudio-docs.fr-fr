---
title: Ensemble de règles de règles de conception étendue pour le code managé
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 2842db460d0a8e3a31921d80cf4a0c3ea0bbc847
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31927098"
---
# <a name="extended-design-guidelines-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de conception étendue pour le code managé
L’ensemble de règles intitulé règles de conception étendue Microsoft s’appuie sur les règles de conception de base pour optimiser les facilité d’utilisation et de facilité de maintenance les problèmes signalés. L’accent sur l’affectation de noms. Pensez à inclure cet ensemble de règles si votre projet contient du code de bibliothèque ou si vous souhaitez appliquer les normes optimales pour écrire du code facile à maintenir.

 Les règles de conception étendue comprennent tous les Microsoft conception les règles de base. Les règles de conception de base incluent toutes les règles Microsoft minimales recommandées. Pour plus d’informations, consultez [règle des règles de conception de base défini pour le code managé](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) et [gérés recommandé de règles défini pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)

 Le tableau suivant décrit toutes les règles dans l’ensemble de règles intitulé règles de conception étendue Microsoft.

|Règle|Description|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Les types qui possèdent des champs supprimables doivent être supprimables|
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Déclarer les gestionnaires d’événements correctement|
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Marquer les assemblys avec AssemblyVersionAttribute|
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Méthodes d’interface doivent pouvoir être appelées par les types enfants|
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|Les types qui possèdent des ressources natives doivent être supprimables|
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Déplacer les P/Invoke vers une classe NativeMethods|
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Ne pas masquer les méthodes de classe de base|
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implémenter IDisposable correctement|
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Ne pas lever d’exceptions dans des emplacements inattendus|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Éviter les accélérateurs en double|
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|Points d’entrée P/Invoke doivent exister|
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|P/Invoke ne doivent pas être visible|
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|Les types Structurer automatiquement ne doivent pas être visibles par COM|
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Appeler GetLastError immédiatement après P/Invoke|
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|Types base type visibles par COM doivent être visibles par COM|
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|Méthodes d’inscription COM doivent être mises en correspondance.|
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Déclarer correctement les méthodes P/Invoke|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Champs de type valeur doivent être portables|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Les déclarations P/Invoke doivent être portables|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ne verrouillent pas sur des objets à identité faible|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Passez en revue les requêtes SQL des failles de sécurité|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Sécurité de la méthode doit être un sur-ensemble du type|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N’exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de remplacement doivent être identiques à la base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Finally vulnérables clauses dans externe try|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Liaison de types nécessitent des demandes d’héritage|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas faire partie de l’équivalence de type|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Transparence des méthodes doivent rester cohérente lors de la substitution de méthodes de base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes avec l’attribut SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Types doivent être au moins aussi critiques que leurs types de base et les interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser de sécurité des assertions|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler dans du code natif|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Levez de nouveau pour conserver les détails de la pile|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Ne pas supprimer des objets plusieurs fois|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Initialiser les champs statiques de type valeur en ligne|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Ne marquez pas les composants pris en charge avec WebMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Des champs supprimables doivent être supprimés.|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|N’appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Les finaliseurs doivent appeler le finaliseur de la classe de base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implémentez des constructeurs de sérialisation|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur equals en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Points d’entrée d’interrogation Windows Forms avec STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marquez tous les champs non sérialisables|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Appeler des méthodes de classe de base sur les types ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implémentez les méthodes de sérialisation|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implémentez ISerializable correctement|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Fournissez des arguments corrects aux méthodes de mise en forme|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Correctement des tests NaN|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Ne pas déclarer de membres statiques sur les types génériques|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|N’exposez pas de listes génériques|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Utiliser les instances du Gestionnaire d’événements génériques|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Les méthodes génériques doivent fournir un paramètre de type|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Éviter les paramètres excessifs sur les types génériques|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Ne pas imbriquer les types génériques dans les signatures de membre|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utiliser des classes génériques lorsque cela est approprié|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Les enums doivent avoir la valeur zéro|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Les collections doivent implémenter une interface générique|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Si possible, transmettez les types de base en tant que paramètres|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Les types abstraits ne doivent pas avoir de constructeurs|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Surchargez l’opérateur égal lors de la surcharge addition et de soustraction|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marquer les assemblys avec CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marquer les assemblys avec ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marquer les attributs avec AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Définir des accesseurs pour les arguments d’attribut|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Les indexeurs ne doivent pas être multidimensionnels|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utilisez les propriétés lorsque cela est approprié|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Remplacer les arguments répétitifs par un tableau params|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Les paramètres par défaut ne doivent pas être utilisés|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marquer les enums avec FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Enum storage doit être Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Utiliser des événements lorsque cela est approprié|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Ne pas intercepter des types d’exception générale|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implémenter des constructeurs d’exception standard|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Types imbriqués ne doivent pas être visibles|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Les implémentations ICollection ont des membres fortement typés|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Substituer les méthodes sur les types comparable|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Les énumérateurs doivent être fortement typés.|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Les listes sont fortement typées.|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Fournir un message ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utilisez l’argument de chaîne ou intégral pour les indexeurs|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Propriétés ne doivent pas être écriture seule|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Ne pas surcharger l’opérateur égal à sur les types référence|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Ne pas déclarer les membres protégés dans les types sealed|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Ne pas déclarer les membres virtuels dans les types sealed|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Déclarez les types dans les espaces de noms|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Ne pas déclarer de champs d’instances visibles|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Types de conteneurs statiques doivent être sealed|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Types de conteneurs statiques ne doivent pas avoir de constructeurs|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Paramètres URI ne doivent pas être des chaînes|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Valeurs ne doivent pas être des chaînes de retour URI|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Propriétés URI ne doivent pas être des chaînes|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Surcharges d’URI de chaîne appellent les surcharges de System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Les types ne doivent pas étendre certains types de base|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Les membres ne doivent pas exposer certains types concrets|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Exceptions doivent être publiques|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Les noms de variables ne doivent pas correspondre aux noms de champs|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Éviter l’excès de complexité|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Les identificateurs doivent pas différer uniquement par leur casse|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Les identificateurs ne doivent pas correspondre aux mots clés|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Passez en revue les paramètres inutilisés|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Supprimez les variables locales inutilisées|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Évitez le surplus de variables locales|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Initialiser les champs statiques de type référence en ligne|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Évitez le recours à du code privé|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Évitez les classes internes non instanciées|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Évitez les attributs unsealed|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Préférez des tableaux en escalier multidimensionnels|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Remplacez equals et l’opérateur égal à sur les types valeur|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Propriétés ne doivent pas retourner de tableaux|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Vérifier la présence de chaînes vides à l’aide de la longueur de chaîne|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Marquez les membres comme static|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Évitez les champs privés inutilisés|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ne levez pas de types d’exceptions réservés|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilisez des équivalents managés de l’API Win32|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Instanciez les exceptions d’argument|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Les champs non constants ne doivent pas être visibles|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Ne marquez pas les enums avec FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Ne pas lever d’exceptions dans les clauses d’exception|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Les finaliseurs doivent être protégés.|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Ne réduisez pas la visibilité des membres hérités|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Les membres doivent différer par type de retour|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Remplacez equals lors de la surcharge l’opérateur égal|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Les surcharges d’opérateur ont nommées.|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Les opérateurs doivent contenir des surcharges symétriques|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Propriétés de la collection doivent être en lecture seule|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilisez params pour les arguments de variables|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passez des objets System.Uri à la place des chaînes|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fournir des méthodes de désérialisation pour les champs facultatifs|
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Éviter les espaces de noms comportant peu de types|
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Éviter les paramètres out|
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Éviter les interfaces vides|
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Ne pas passer de types par référence|
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Valider les arguments de méthodes publiques|
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Éviter l’excès d’héritage|
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Passez en revue les noms de champs trompeurs|
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Éviter le code|
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Éviter les couplages de classe excessifs|
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Ne nommez pas les valeurs enum 'Reserved'|
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Mots composés de chaînes de ressources doivent être correcte|
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Mots composés doivent être correcte|
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Chaînes de ressources doivent être correcte|
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Les identificateurs doivent être correctement orthographiés|
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Identificateurs ne doivent pas contenir des traits de soulignement|
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Identificateurs doivent être correcte|
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Les identificateurs doivent porter un suffixe correct|
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Identificateurs ne doivent pas porter un suffixe incorrect|
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|N’ajoutez pas de préfixe avec le nom de type, les valeurs enum|
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Les événements ne doivent pas avoir préfixe before ou after|
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Les énumérations d’indicateurs doivent avoir des noms au pluriel|
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Les identificateurs doivent porter un préfixe correct|
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Uniquement des enums FlagsAttribute doivent avoir des noms au pluriel|
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Les noms de paramètres ne doivent pas correspondre aux noms de membres|
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Identificateurs ne doivent pas contenir les noms de type|
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Les noms de propriétés ne doivent pas correspondre à des méthodes get|
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Identificateurs ne doivent pas porter un préfixe incorrect|
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Noms de types ne doivent pas correspondre aux espaces de noms|
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Les noms de paramètres doivent correspondre à la déclaration de base|
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Utilisez les termes par défaut|
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Les littéraux doivent être correctement orthographiés|