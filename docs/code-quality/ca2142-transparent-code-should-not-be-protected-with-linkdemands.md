---
title: "CA2142 : Le code Transparent ne doit pas être protégé avec des LinkDemands | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d0b9712ec0ed9d5ecd8e76b1ecf208505f07623
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142 : Le code transparent ne doit pas être protégé avec des LinkDemands
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode transparente requiert un <xref:System.Security.Permissions.SecurityAction> ou autres à la demande de sécurité.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle se déclenche sur les méthodes transparentes qui requièrent l'accès de LinkDemands. Le code transparent de sécurité ne doit pas être responsable de la vérification de la sécurité d'une opération. Par conséquent, il ne doit pas demander d'autorisations. Étant donné que les méthodes transparentes sont supposées pour être neutre de sécurité, ils ne doivent pas être décisions de sécurité. En outre, code critique sécurisé, qui à des décisions de sécurité, ne doit pas compter sur une telle décision précédemment appliquées au code transparent.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez la demande de liaison sur la méthode transparente ou marquez la méthode avec <xref:System.Security.SecuritySafeCriticalAttribute> attribut si elle exécute sécurité vérifie, telles que les demandes de sécurité.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la règle déclenche la méthode, car la méthode est transparente et est marquée avec un LinkDemand <xref:System.Security.PermissionSet> qui contient un <xref:System.Security.Permissions.SecurityAction>.  
  
 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Ne supprimez aucun avertissement de cette règle.