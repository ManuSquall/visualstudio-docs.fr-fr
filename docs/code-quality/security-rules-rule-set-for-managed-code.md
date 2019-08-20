---
title: Ensemble de règles des règles de sécurité pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1131f9cf0e77fd4fe68e4bc5c033491aa6dd34e1
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69585188"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de sécurité pour le code managé

Utilisez le jeu de règles des règles de sécurité Microsoft pour l’analyse du code hérité afin d’optimiser le nombre de problèmes de sécurité potentiels signalés.

|Règle|Description|
|----------|-----------------|
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Vérifier si les requêtes SQL présentent des failles de sécurité|
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux|
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|Vérifiez la sécurité impérative|
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|Ne déclarez pas les types référence mutables en lecture seule|
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|Les champs de tableau ne doivent pas être en lecture seule|
|[CA2106](../code-quality/ca2106-secure-asserts.md)|Assertions sécurisées|
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|Passez en revue l'utilisation des méthodes Deny et PermitOnly|
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|Passez en revue les gestionnaires d'événements visibles|
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|Les types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sécurité de la méthode doit être un sur-ensemble du type|
|[CA2115](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)|Appelez GC.KeepAlive lorsque vous utilisez des ressources natives|
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|Vérifier l'utilisation de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Scellez les méthodes qui satisfont les interfaces privées|
|[CA2120](../code-quality/ca2120-secure-serialization-constructors.md)|Sécurisez les constructeurs de sérialisation|
|[CA2121](../code-quality/ca2121-static-constructors-should-be-private.md)|Les constructeurs statiques doivent être privés|
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de substitution doivent être identiques au composant de base|
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Les demandes de liaison de type exigent des demandes d'héritage|
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Les constantes critiques de sécurité doivent être transparentes|
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types|
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base|
|[CA2135](../code-quality/ca2135-level-2-assemblies-should-not-contain-linkdemands.md)|Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands|
|[CA2136](../code-quality/ca2136-members-should-not-have-conflicting-transparency-annotations.md)|Les membres ne doivent pas avoir d'annotations de transparence conflictuelles|
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute.md)|Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|
|[CA2143](../code-quality/ca2143-transparent-methods-should-not-use-security-demands.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Le code transparent ne doit pas charger d'assemblys depuis des tableaux d'octets|
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité|
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler du code natif|
|[CA2210](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Les assemblys doivent porter des noms forts valides|
|[CA2300](ca2300-do-not-use-insecure-deserializer-binaryformatter.md)|N’utilisez pas le désérialiseur non sécurisé BinaryFormatter|
|[CA2301](ca2301-do-not-call-binaryformatter-deserialize-without-first-setting-binaryformatter-binder.md)|N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable|
|[CA2302](ca2302-ensure-binaryformatter-binder-is-set-before-calling-binaryformatter-deserialize.md)|Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize|
|[CA2305](ca2305-do-not-use-insecure-deserializer-losformatter.md)|N’utilisez pas le désérialiseur non sécurisé LosFormatter|
|[CA2310](ca2310-do-not-use-insecure-deserializer-netdatacontractserializer.md)|N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer|
|[CA2311](ca2311-do-not-deserialize-without-first-setting-netdatacontractserializer-binder.md)|Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder|
|[CA2312](ca2312-ensure-netdatacontractserializer-binder-is-set-before-deserializing.md)|Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation|
|[CA2315](ca2315-do-not-use-insecure-deserializer-objectstateformatter.md)|N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter|
|[CA2321](ca2321.md)|Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver|
|[CA2322](ca2322.md)|Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation|
|[CA3001](../code-quality/ca3001-review-code-for-sql-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection SQL|
|[CA3002](../code-quality/ca3002-review-code-for-xss-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités des scripts XSS|
|[CA3003](../code-quality/ca3003-review-code-for-file-path-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier|
|[CA3004](../code-quality/ca3004-review-code-for-information-disclosure-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations|
|[CA3005](../code-quality/ca3005-review-code-for-ldap-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP|
|[CA3006](../code-quality/ca3006-review-code-for-process-command-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus|
|[CA3007](../code-quality/ca3007-review-code-for-open-redirect-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte|
|[CA3008](../code-quality/ca3008-review-code-for-xpath-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection XPath|
|[CA3009](../code-quality/ca3009-review-code-for-xml-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection XML|
|[CA3010](../code-quality/ca3010-review-code-for-xaml-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection XAML|
|[CA3011](../code-quality/ca3011-review-code-for-dll-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL|
|[CA3012](../code-quality/ca3012-review-code-for-regex-injection-vulnerabilities.md)|Passez en revue le code pour détecter les vulnérabilités de l’injection regex|
