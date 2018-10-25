---
title: 'CA2122 : N’exposez pas indirectement des méthodes avec des demandes de liaison | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 563805fdd8ba8c30e9fb241cc24136ad0c9e9e06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912836"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122 : N'exposez pas indirectement des méthodes avec des demandes de liaison
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un membre public ou protégé a un [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) et est appelée par un membre qui n’effectue pas les vérifications de sécurité.

## <a name="rule-description"></a>Description de la règle
 Une demande de liaison vérifie uniquement les autorisations de l’appelant immédiat. Si un membre `X` n’effectue aucune des demandes de sécurité de ses appelants et appelle un code protégé par une demande de liaison, un appelant sans l’autorisation nécessaire peut utiliser `X` pour accéder au membre protégé.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Ajouter une sécurité [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) ou demande de liaison au membre afin qu’il ne fournit plus accès non sécurisé au membre protégé par demande de liaison.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Pour supprimer sans risque un avertissement de cette règle, il se peut que vous devez vous assurer que votre code n’accorde pas ses appelants accès à des opérations ou des ressources qui peuvent être utilisées dans une action destructrice.

## <a name="example"></a>Exemple
 Les exemples suivants montrent une bibliothèque qui viole la règle et une application qui montre la faiblesse de la bibliothèque. L’exemple de bibliothèque fournit deux méthodes qui ensemble enfreignent la règle. Le `EnvironmentSetting` méthode est sécurisée par une demande de liaison pour un accès illimité aux variables d’environnement. Le `DomainInformation` méthode n’effectue aucune des demandes de sécurité de ses appelants avant d’appeler `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Exemple
 L’application suivante appelle le membre de bibliothèque non sécurisé.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Cet exemple produit la sortie suivante.

 **Valeur de membre : seattle.corp.contoso.com**
## <a name="see-also"></a>Voir aussi
 [Instructions de codage sécurisé](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [demandes de liaison](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [données et modélisation](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



