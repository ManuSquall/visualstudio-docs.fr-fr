---
title: 'CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: e0571656905642b9f8bdd12a93a8aa83256124f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145 : Les méthodes transparentes ne doivent pas être décorées avec SuppressUnmanagedCodeSecurityAttribute
|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|  
|CheckId|CA2145|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode transparente, une méthode qui est marquée avec la <xref:System.Security.SecuritySafeCriticalAttribute> méthode ou un type qui contient une méthode est marqué avec la <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut.  
  
## <a name="rule-description"></a>Description de la règle  
 Les méthodes décorées avec le <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> attribut ont un LinkDemand implicit sur toute méthode qui l’appelle. Ce LinkDemand requiert que le code appelant soit critique de sécurité. Marquage de la méthode qui utilise SuppressUnmanagedCodeSecurity avec le <xref:System.Security.SecurityCriticalAttribute> attribut rend cette spécification plus évidente pour les appelants de la méthode.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez la méthode ou de type avec le <xref:System.Security.SecurityCriticalAttribute> attribut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]  
  
### <a name="comments"></a>Commentaires