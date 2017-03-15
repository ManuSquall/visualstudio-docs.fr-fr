---
title: "Ensemble de r&#232;gles des r&#232;gles de s&#233;curit&#233; pour le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# Ensemble de r&#232;gles des r&#232;gles de s&#233;curit&#233; pour le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous devez inclure l'ensemble de Règles de sécurité Microsoft pour optimiser le nombre de problèmes de sécurité éventuels qui sont détectés.  
  
|Règle|Description|  
|-----------|-----------------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|CA2100 : Rechercher des failles de sécurité dans des requêtes SQL|  
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
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sécurité de la méthode doit être un sur\-ensemble du type|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|Appelez GC.KeepAlive lorsque vous utilisez des ressources natives|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|CA2118 : Révision de l'utilisation de SuppressUnmanagedCodeSecurityAttribute|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|Scellez les méthodes qui satisfont les interfaces privées|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|Sécurisez les constructeurs de sérialisation|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|Les constructeurs statiques doivent être privés|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Les demandes de liaison de surcharge doivent être identiques au composant de base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|Les demandes de liaison de types nécessitent des demandes d'héritage|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|Les constantes critiques de sécurité doivent être transparentes|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|Les méthodes doivent garder une transparence consistente lors de la surcharge de méthodes de base|  
|[CA2135](../Topic/CA2135:%20Level%202%20assemblies%20should%20not%20contain%20LinkDemands.md)|Les assemblies de niveau 2 ne doivent pas contenir de LinkDemands|  
|[CA2136](../Topic/CA2136:%20Members%20should%20not%20have%20conflicting%20transparency%20annotations.md)|Les membres ne doivent pas avoir d'annotations de transparence conflictuelles|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|  
|[CA2139](../Topic/CA2139:%20Transparent%20methods%20may%20not%20use%20the%20HandleProcessCorruptingExceptions%20attribute.md)|Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|  
|[CA2143](../Topic/CA2143:%20Transparent%20methods%20should%20not%20use%20security%20demands.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|Le code transparent ne doit pas charger d'assemblies depuis des tableaux d'octets|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes ne peuvent pas utiliser d'assertions de sécurité|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|Les méthodes transparentes ne doivent pas appeler du code natif|  
|[CA2210](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|CA2210 : Les assemblys doivent porter des noms forts valides|