---
title: Ensemble de règles de règles de conception de base pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d51796f7575e3dd5766655661927dfd520935c02
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585086"
---
# <a name="basic-design-guideline-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de conception de base pour le code managé

Vous pouvez utiliser l’ensemble de règles des règles de conception de base de Microsoft pour vous concentrer sur la compréhension et l’utilisation de votre code. Vous devez inclure cet ensemble de règles si votre projet inclut du code de bibliothèque ou si vous souhaitez appliquer les meilleures pratiques pour le code qui est facile à gérer.

Les règles de conception de base incluent toutes les règles dans l’ensemble de règles des [règles recommandées managées](managed-recommended-rules-rule-set-for-managed-code.md) .

Le tableau suivant décrit toutes les règles de l’ensemble de règles des règles de conception de base de Microsoft.

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
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Les champs de type valeur doivent être portables|
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Les déclarations P/Invoke doivent être portables|
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ne définissez pas un verrou sur des objets à identité faible|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Vérifier si les requêtes SQL présentent des failles de sécurité|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Les types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sécurité de la méthode doit être un sur-ensemble du type|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de substitution doivent être identiques au composant de base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Les demandes de liaison de type exigent des demandes d'héritage|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler du code natif|
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Levez à nouveau une exception pour conserver les détails de la pile|
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Ne pas supprimer d'objets plusieurs fois|
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Initialisez les champs statiques des types valeur en ligne|
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Ne marquez pas les composants pris en charge avec webMethod|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Les champs pouvant être supprimés doivent l’être|
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|N'appelez pas de méthodes substituables dans les constructeurs|
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Les types pouvant être supprimés doivent déclarer un finaliseur|
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|Les finaliseurs doivent appeler le finaliseur de leur classe de base|
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implémentez des constructeurs de sérialisation|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals|
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Marquez les points d'entrée Windows Forms avec STAThread|
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Marquez tous les champs non sérialisés|
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Appelez les méthodes de la classe de base sur les types ISerializable|
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Marquer les types ISerializable avec SerializableAttribute|
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implémentez les méthodes de sérialisation comme il se doit|
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implémentez ISerializable comme il se doit|
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Indiquer le nombre correct d'arguments dans les méthodes de mise en forme|
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Effectuez correctement des tests NaN|
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Ne pas déclarer de membres statiques sur les types génériques|
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Ne pas exposer de listes génériques|
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Utiliser les instances du gestionnaire d'événements génériques|
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Les méthodes génériques doivent fournir un paramètre de type|
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Éviter les paramètres excessifs sur les types génériques|
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Ne pas imbriquer les types génériques dans les signatures de membre|
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utiliser des classes génériques lorsque cela est approprié|
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Les enums doivent avoir la valeur zéro|
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Les collections doivent implémenter une interface générique|
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Si possible, transmettez les types de base en tant que paramètres|
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|Les types abstract ne doivent pas avoir de constructeurs|
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Surchargez l'opérateur égal lors de la surcharge de l'opérateur d'addition et de soustraction|
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Marquer les assemblys avec CLSCompliantAttribute|
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Marquer les assemblys avec ComVisibleAttribute|
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Marquer les attributs avec AttributeUsageAttribute|
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Définir des accesseurs pour les arguments d'attribut|
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Les indexeurs ne doivent pas être multidimensionnels|
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utiliser les propriétés lorsque cela est approprié|
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Remplacer les arguments répétitifs par un tableau params|
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Les paramètres par défaut ne doivent pas être utilisés|
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Marquer les enums avec FlagsAttribute|
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|Enum Storage doit être Int32|
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Utiliser des événements lorsque cela est approprié|
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Ne pas intercepter des types d'exception générale|
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implémenter des constructeurs d'exception standard|
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Les types imbriqués ne doivent pas être visibles|
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Les implémentations ICollection possèdent des membres fortement typés|
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Substituer les méthodes sur les types Comparable|
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Les énumérateurs doivent être fortement typés|
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Les listes sont fortement typées|
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Fournir un message ObsoleteAttribute|
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utiliser un argument de chaîne ou intégral pour les indexeurs|
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Les propriétés ne doivent pas être en écriture seule|
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Ne pas surcharger l'opérateur égal à sur les types référence|
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Ne pas déclarer les membres protégés dans les types sealed|
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Ne pas déclarer les membres virtuels dans les types sealed|
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Déclarer les types dans des espaces de noms|
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Ne pas déclarer de champs d'instances visibles|
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Les types de conteneurs statiques doivent être sealed|
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Les types de conteneurs statiques ne doivent pas comporter de constructeur|
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Les paramètres URI ne doivent pas être des chaînes|
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Les valeurs de retour URI ne doivent pas être des chaînes|
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Les propriétés URI ne doivent pas être des chaînes|
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Les surcharges d'URI de chaîne appellent les surcharges de System.Uri|
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Les types ne doivent pas étendre certains types de base|
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Les membres ne doivent pas exposer certains types concrets|
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Les exceptions doivent être publiques|
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|Les noms de variables ne doivent pas être identiques aux noms de champs|
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Éviter l'excès de complexité|
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Les identificateurs ne doivent pas différer uniquement par leur casse|
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Les identificateurs ne doivent pas correspondre à des mots clés|
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Passez en revue les paramètres inutilisés|
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Supprimez les variables locales inutilisées|
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Évitez le surplus de variables locales|
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Initialisez les champs statiques de type référence en ligne|
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Évitez le recours à du code privé non appelé|
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Évitez les classes internes non instanciées|
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Évitez les attributs unsealed|
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Utilisez des tableaux en escalier à la place de tableaux multidimensionnels|
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Remplacez Equals et l'opérateur égal à dans les types valeur|
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Les propriétés ne doivent pas retourner des tableaux|
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Vérifiez la présence de chaînes vides par la longueur de chaîne|
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Marquez les membres comme static|
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Évitez les champs privés inutilisés|
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Ne levez pas des types d'exceptions réservés|
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilisez des équivalents managés de l'API Win32|
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Instanciez les exceptions d'argument comme il se doit|
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Les champs non constants ne doivent pas être visibles|
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Ne marquez pas les enums avec l'attribut FlagsAttribute|
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Ne pas lever d'exceptions dans les clauses d'exception|
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Les finaliseurs doivent être protégés|
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Ne réduisez pas la visibilité des membres hérités|
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Les membres ne doivent pas différer uniquement par leur type de retour|
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Remplacez Equals au moment de surcharger l'opérateur égal|
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Les surcharges d'opérateur offrent d'autres méthodes nommées|
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Les opérateurs doivent contenir des surcharges symétriques|
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Les propriétés de collection doivent être en lecture seule|
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilisez le mot clé params pour les arguments de variables|
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passez des objets System.Uri à la place de chaînes|
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Spécifiez des méthodes de désérialisation pour les champs facultatifs|