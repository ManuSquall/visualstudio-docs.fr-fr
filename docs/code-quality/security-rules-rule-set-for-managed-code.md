---
title: Ensemble de règles des règles de sécurité pour le code managé
ms.date: 11/04/2016
description: En savoir plus sur l’ensemble de règles des règles de sécurité pour l’analyse du code hérité Visual Studio. Consultez les descriptions des règles qui se concentrent sur les problèmes de sécurité potentiels.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 32237eb1229e28d1077b2eec8586f52151d69c2d
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436951"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Ensemble de règles des règles de sécurité pour le code managé

Utilisez le jeu de règles des règles de sécurité Microsoft pour l’analyse du code hérité afin d’optimiser le nombre de problèmes de sécurité potentiels signalés.

|Règle|Description|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|Vérifier si les requêtes SQL présentent des failles de sécurité|
|[CA2102](../code-quality/ca2102.md)|Interceptez les exceptions non CLSCompliant dans les gestionnaires généraux|
|[CA2103](../code-quality/ca2103.md)|Vérifiez la sécurité impérative|
|[CA2104](../code-quality/ca2104.md)|Ne déclarez pas les types référence mutables en lecture seule|
|[CA2105](../code-quality/ca2105.md)|Les champs de tableau ne doivent pas être en lecture seule|
|[CA2106](../code-quality/ca2106.md)|Assertions sécurisées|
|[CA2107](../code-quality/ca2107.md)|Passez en revue l'utilisation des méthodes Deny et PermitOnly|
|[CA2108](../code-quality/ca2108.md)|Vérifiez la sécurité déclarative dans les types valeur|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Passez en revue les gestionnaires d'événements visibles|
|[CA2111](../code-quality/ca2111.md)|Les pointeurs ne doivent pas être visibles|
|[CA2112](../code-quality/ca2112.md)|Les types sécurisés ne doivent pas exposer de champs|
|[CA2114](../code-quality/ca2114.md)|La sécurité de la méthode doit être un sur-ensemble du type|
|[CA2115](../code-quality/ca2115.md)|Appelez GC.KeepAlive lorsque vous utilisez des ressources natives|
|[CA2116](../code-quality/ca2116.md)|Les méthodes APTCA doivent uniquement appeler des méthodes APTCA|
|[CA2117](../code-quality/ca2117.md)|Les types APTCA doivent uniquement étendre des types de base APTCA|
|[CA2118](../code-quality/ca2118.md)|Vérifier l'utilisation de SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Scellez les méthodes qui satisfont les interfaces privées|
|[CA2120](../code-quality/ca2120.md)|Sécurisez les constructeurs de sérialisation|
|[CA2121](../code-quality/ca2121.md)|Les constructeurs statiques doivent être privés|
|[CA2122](../code-quality/ca2122.md)|N'exposez pas indirectement des méthodes avec des demandes de liaison|
|[CA2123](../code-quality/ca2123.md)|Les demandes de liaison de substitution doivent être identiques au composant de base|
|[CA2124](../code-quality/ca2124.md)|Incluez dans un wrapper les clauses finally vulnérables dans un bloc try externe|
|[CA2126](../code-quality/ca2126.md)|Les demandes de liaison de type exigent des demandes d'héritage|
|[CA2130](../code-quality/ca2130.md)|Les constantes critiques de sécurité doivent être transparentes|
|[CA2131](../code-quality/ca2131.md)|Les types critiques de sécurité ne peuvent pas participer à l'équivalence des types|
|[CA2132](../code-quality/ca2132.md)|Les constructeurs par défaut doivent être au moins aussi critiques que les constructeurs par défaut de type de base|
|[CA2133](../code-quality/ca2133.md)|Les délégués doivent lier les méthodes avec une transparence cohérente|
|[CA2134](../code-quality/ca2134.md)|La transparence des méthodes doit rester cohérente lors de la substitution de méthodes de base|
|[CA2135](../code-quality/ca2135.md)|Les assemblys de niveau 2 ne doivent pas contenir de LinkDemands|
|[CA2136](../code-quality/ca2136.md)|Les membres ne doivent pas avoir d'annotations de transparence conflictuelles|
|[CA2137](../code-quality/ca2137.md)|Les méthodes transparentes doivent contenir uniquement des IL vérifiables|
|[CA2138](../code-quality/ca2138.md)|Les méthodes transparentes ne doivent pas appeler les méthodes ayant l'attribut SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Les méthodes transparentes ne peuvent pas utiliser l'attribut HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|Le code transparent ne doit pas faire référence à des éléments critiques de sécurité|
|[CA2141](../code-quality/ca2141.md)|Les méthodes transparentes ne répondent pas aux LinkDemands|
|[CA2142](../code-quality/ca2142.md)|Le code transparent ne doit pas être protégé avec des LinkDemands|
|[CA2143](../code-quality/ca2143.md)|Les méthodes transparentes ne doivent pas utiliser de demandes de sécurité|
|[CA2144](../code-quality/ca2144.md)|Le code transparent ne doit pas charger d'assemblys depuis des tableaux d'octets|
|[CA2145](../code-quality/ca2145.md)|Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Les types doivent être au moins aussi critiques que les types de base et les interfaces|
|[CA2147](../code-quality/ca2147.md)|Les méthodes transparentes ne peuvent pas utiliser d’assertions de sécurité|
|[CA2149](../code-quality/ca2149.md)|Les méthodes transparentes ne doivent pas appeler du code natif|
|[CA2210](../code-quality/ca2210.md)|Les assemblys doivent porter des noms forts valides|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|N’utilisez pas le désérialiseur non sécurisé BinaryFormatter|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|N’appelez pas BinaryFormatter.Deserialize sans définir BinaryFormatter.Binder au préalable|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|Vérifiez que BinaryFormatter.Binder est défini avant d’appeler BinaryFormatter.Deserialize|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|N’utilisez pas le désérialiseur non sécurisé LosFormatter|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|N’utilisez pas le désérialiseur non sécurisé NetDataContractSerializer|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|Ne désérialisez pas sans définir d’abord NetDataContractSerializer.Binder|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Vérifiez que NetDataContractSerializer.Binder est défini avant la désérialisation|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|N’utilisez pas le désérialiseur non sécurisé ObjectStateFormatter|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|Ne désérialisez avec JavaScriptSerializer à l’aide de SimpleTypeResolver|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Assurez-vous que JavaScriptSerializer n’est pas initialisé avec SimpleTypeResolver avant la désérialisation|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|Passez en revue le code pour détecter les vulnérabilités de l’injection SQL|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|Passez en revue le code pour détecter les vulnérabilités des scripts XSS|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Passez en revue le code pour détecter les vulnérabilités de l’injection de chemin de fichier|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Passez en revue le code pour détecter les vulnérabilités sur la divulgation d’informations|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|Passez en revue le code pour détecter les vulnérabilités de l’injection LDAP|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|Passez en revue le code pour détecter les vulnérabilités de l’injection de commande de processus|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Passez en revue le code pour détecter les vulnérabilités de la redirection ouverte|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|Passez en revue le code pour détecter les vulnérabilités de l’injection XPath|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|Passez en revue le code pour détecter les vulnérabilités de l’injection XML|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|Passez en revue le code pour détecter les vulnérabilités de l’injection XAML|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|Passez en revue le code pour détecter les vulnérabilités de l’injection de DLL|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Passez en revue le code pour détecter les vulnérabilités de l’injection regex|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Ne pas utiliser de modes de chiffrement non sécurisés|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Ne pas coder en dur le certificat|