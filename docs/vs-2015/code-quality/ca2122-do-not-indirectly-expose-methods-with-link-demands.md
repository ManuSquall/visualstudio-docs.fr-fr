---
title: 'CA2122 : n’exposez pas indirectement des méthodes avec des demandes de liaison | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544324"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122 : N'exposez pas indirectement des méthodes avec des demandes de liaison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause :
 Un membre public ou protégé a des [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) et est appelé par un membre qui n’effectue aucune vérification de sécurité.

## <a name="rule-description"></a>Description de la règle
 Une demande de liaison vérifie uniquement les autorisations de l’appelant immédiat. Si un membre `X` ne fait aucune demande de sécurité de ses appelants et appelle du code protégé par une demande de liaison, un appelant sans l’autorisation nécessaire peut utiliser `X` pour accéder au membre protégé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Ajoutez des données de sécurité [et une modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) ou une demande de liaison au membre afin qu’il ne fournisse plus d’accès non sécurisé au membre protégé à la demande de liaison.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, vous devez vous assurer que votre code n’accorde pas à ses appelants l’accès aux opérations ou aux ressources qui peuvent être utilisées de manière destructrice.

## <a name="example"></a>Exemple
 Les exemples suivants illustrent une bibliothèque qui enfreint la règle et une application qui illustre la faiblesse de la bibliothèque. L’exemple de bibliothèque fournit deux méthodes qui enfreignent ensemble la règle. La `EnvironmentSetting` méthode est sécurisée par une demande de liaison pour un accès illimité aux variables d’environnement. La `DomainInformation` méthode ne fait aucune demande de sécurité de ses appelants avant d’appeler `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante appelle le membre de bibliothèque non sécurisé.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Cet exemple produit la sortie suivante.

 **Valeur du membre non sécurisé : seattle.corp.contoso.com**
## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé les](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [demandes de liaison](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [de données et de modélisation](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
