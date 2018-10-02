---
title: Définir des règles de règles de vérification étendue pour le code managé | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b181f5b-6c7a-4e46-a783-360e1da427a0
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: aa22234c797a47fba945ba65343532df3565aefc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47506435"
---
# <a name="extended-correctness-rules-rule-set-for-managed-code"></a>Ensemble de règles de règles de vérification étendue pour le code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [règle de règles de vérification étendue définie pour le code managé](https://docs.microsoft.com/visualstudio/code-quality/extended-correctness-rules-rule-set-for-managed-code).  
  
L’ensemble de règles de règles de vérification étendue Microsoft optimise les erreurs de l’utilisation de logique et framework qui sont signalés par l’analyse du code. Accentuation supplémentaire est placée sur les scénarios spécifiques tels que l’interopérabilité COM et des applications mobiles. Vous devez envisager d’inclure cette règle définie si une de ces scénarios s’applique à votre projet ou pour trouver d’autres problèmes dans votre projet.  
  
 L’ensemble de règles de règles de vérification étendue Microsoft inclut les règles qui sont définies dans la règle de règles de vérification de base de Microsoft. Les règles de vérification de base inclut les règles qui sont définies dans la règle de règles minimales recommandées par Microsoft. Pour plus d’informations, consultez [base règles de vérification définie pour le code managé](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md) et [gérés recommandé de règles défini pour le code managé](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)  
  
 Le tableau suivant décrit toutes les règles dans l’ensemble de règles de règles de vérification étendue Microsoft.  
  
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
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Déclarer correctement les P/Invoke|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Supprimez les finaliseurs vides|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Champs de type valeur doivent être portables|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Les déclarations P/Invoke doivent être portables|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Ne verrouillez pas sur des objets à identité faible|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Passez en revue les requêtes SQL pour les failles de sécurité|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Spécifiez le marshaling pour les arguments de chaîne P/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Types sécurisés ne doivent pas exposer de champs|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|Sécurité de la méthode doit être un sur-ensemble du type|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N’exposez pas indirectement des méthodes avec des demandes de liaison|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Demandes de liaison de remplacement doivent être identiques de base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Wrapper finally vulnérables clauses dans externe try|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Demandes de liaison de type nécessitent des demandes d’héritage|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Types critiques de sécurité ne peuvent pas participer l’équivalence des types|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier aux méthodes avec une transparence cohérente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Méthodes doit rester une transparence cohérente lors de la substitution des méthodes de base|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler de méthodes avec l’attribut SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Méthodes transparentes ne répondent pas aux LinkDemands|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Types doivent être au moins aussi critiques que leurs types de base et les interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser de sécurité des assertions|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Méthodes transparentes ne doivent pas appeler du code natif|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Lever à nouveau pour conserver les détails de la pile|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Ne pas supprimer des objets plusieurs fois|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Initialiser des champs statiques de type valeur en ligne|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Ne marquez pas les composants pris en charge avec WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Champs supprimables doivent être supprimés.|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|N’appelez pas de méthodes substituables dans les constructeurs|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|Les types supprimables doivent déclarer un finaliseur|  
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
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Les enums doivent avoir la valeur zéro|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Surchargez l’opérateur égal lors de la surcharge addition et de soustraction|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Ne pas transmettre des littéraux en tant que paramètres localisés|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Normaliser les chaînes en majuscules|  
|[CA1806](../code-quality/ca1806-do-not-ignore-method-results.md)|N’ignorez pas les résultats de la méthode|  
|[CA1816](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Appelez GC. SuppressFinalize correctement|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Propriétés ne doivent pas retourner de tableaux|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Test de chaînes vides à l’aide de la longueur de chaîne|  
|[CA1903](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Utiliser uniquement l’API du framework cible|  
|[CA2004](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Supprimez les appels à GC. KeepAlive|  
|[CA2006](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Utilisez SafeHandle pour encapsuler les ressources natives|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Ne déclarez pas les types référence mutables uniquement en lecture|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Champs de tableau ne doivent pas être en lecture seule|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Assertions sécurisées|  
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Appelez GC. KeepAlive lors de l’utilisation des ressources natives|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Scellez les méthodes qui satisfont les interfaces privées|  
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Constructeurs de sérialisation sécurisé|  
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Les constructeurs statiques doivent être privés|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Les constantes critiques de sécurité doivent être transparentes|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilisez des équivalents managés de l’API Win32|  
|[CA2215](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|Méthodes Dispose doivent appeler dispose de la classe de base|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|Les finaliseurs doivent être protégés|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Ne réduisez pas la visibilité des membres hérités|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|Les membres doivent différer par type de retour|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Remplacez equals lors de la surcharge l’opérateur égal|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Les opérateurs doivent contenir des surcharges symétriques|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Propriétés de collection doivent être en lecture seule|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fournir des méthodes de désérialisation pour les champs facultatifs|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implémenter des constructeurs d’exception standard|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Paramètres de l’URI ne doivent pas être de chaînes|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Les valeurs doivent être pas des chaînes de retour URI|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Propriétés de l’URI ne doivent pas être de chaînes|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Surcharges d’URI de chaîne appellent les surcharges de System.Uri|  
|[CA1402](../code-quality/ca1402-avoid-overloads-in-com-visible-interfaces.md)|Éviter les surcharges dans les interfaces COM visibles|  
|[CA1406](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)|Éviter les arguments Int64 pour les clients Visual Basic 6|  
|[CA1407](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)|Éviter les membres statiques dans les types visibles par COM|  
|[CA1408](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)|Ne pas utiliser AutoDual ClassInterfaceType|  
|[CA1409](../code-quality/ca1409-com-visible-types-should-be-creatable.md)|Types visibles par COM doivent pouvoir être créés|  
|[CA1411](../code-quality/ca1411-com-registration-methods-should-not-be-visible.md)|Méthodes d’inscription COM ne doivent pas être visibles|  
|[CA1412](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)|Marquer les Interfaces ComSource comme IDispatch|  
|[CA1413](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)|Évitez les champs non publics dans les types valeur visibles par COM|  
|[CA1414](../code-quality/ca1414-mark-boolean-p-invoke-arguments-with-marshalas.md)|Marquer les arguments P/Invoke booléens comme MarshalAs|  
|[CA1600](../code-quality/ca1600-do-not-use-idle-process-priority.md)|N’utilisez pas de priorité de processus inactif|  
|[CA1601](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|Ne pas utiliser de minuteries qui empêchent les changements d’état d’alimentation|  
|[CA1824](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Marquer les assemblys avec NeutralResourcesLanguageAttribute|  
|[CA2001](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Évitez d’appeler des méthodes|  
|[CA2003](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Ne traitez pas les fibres comme des threads|  
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Assemblys de niveau 2 ne doivent pas contenir de LinkDemands|  
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Membres ne doivent pas avoir des annotations de transparence conflictuelles|  
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Méthodes transparentes ne peuvent pas utiliser l’attribut HandleProcessCorruptingExceptions|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|  
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Le code transparent ne doit pas charger les assemblys à partir de tableaux d’octets|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|Les littéraux doivent être correctement orthographiés|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|Les champs non constants ne doivent pas être visibles|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Ne pas marquer les enums avec FlagsAttribute|  
|[CA2218](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|Remplacez GetHashCode au moment de remplacer Equals|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Ne levez pas d’exceptions dans les clauses d’exception|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Surcharges d’opérateur ont d’autres méthodes nommées|  
|[CA2228](../code-quality/ca2228-do-not-ship-unreleased-resource-formats.md)|Ne sont pas fournies de formats de ressources non commercialisés|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilisez params pour les arguments de variables|  
|[CA2233](../code-quality/ca2233-operations-should-not-overflow.md)|Opérations ne doivent pas déborder|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passez des objets System.Uri au lieu de chaînes|  
|[CA2243](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|Littéraux de chaîne d’attribut doivent être analysés correctement|



