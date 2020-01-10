---
title: Ensemble de règles des règles recommandées managées pour le code managé
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 875f6b3aba88fa3786e4c303f23072e586c4848d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587340"
---
# <a name="managed-recommended-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles recommandées managées pour le code managé

Utilisez l’ensemble de règles des règles recommandées gérées par Microsoft pour vous concentrer sur les problèmes les plus critiques dans votre code géré, y compris les failles de sécurité potentielles, les blocages d’application et d’autres erreurs importantes de logique et de conception. Cet ensemble de règles comprend toutes les règles de l’ensemble de règles [règles minimales gérées](managed-minimum-rules-rule-set-for-managed-code.md) .

Incluez cet ensemble de règles dans tout ensemble de règles personnalisées que vous créez pour vos projets.

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
