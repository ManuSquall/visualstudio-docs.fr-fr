---
title: "Ensemble de r&#232;gles des r&#232;gles recommand&#233;es manag&#233;es pour le code manag&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Ensemble de r&#232;gles des r&#232;gles recommand&#233;es manag&#233;es pour le code manag&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez utiliser l'ensemble de Règles Microsoft Managées Recommandées pour vous concentrer sur les problèmes les plus critiques dans votre code managé, notamment les failles de sécurité potentielles, les arrêts brutaux d'application, et d'autres erreurs importantes de logique et de conception.  Vous devez inclure cet ensemble de règles dans tout ensemble de règles personnalisées que vous créez pour vos projets.  
  
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
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|Les méthodes transparentes peuvent ne pas utiliser d'assertions de sécurité|  
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