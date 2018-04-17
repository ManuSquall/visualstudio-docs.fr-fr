---
title: 'CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 83c366bb69e25d128b190a9ee8b192f13cf61013
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables
|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode contient du code non vérifiable ou retourne un type par référence.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle se déclenche lorsque le code transparent de sécurité tente d'exécuter du code MSIL (Microsoft Intermediate Language) non vérifiable. Toutefois, la règle ne contient pas de vérificateur IL (Intermediate Language) complet, et à la place utilise l’heuristique pour intercepter la plupart des violations de vérification MSIL.  
  
 Pour être certain que votre code contient du code MSIL vérifiable uniquement, exécutez [Peverify.exe (outil PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) sur votre assembly. Exécutez PEVerify avec la **/ transparent** option qui limite la sortie uniquement non vérifiable les méthodes transparentes qui entraînerait une erreur. Si le / option transparente n’est pas utilisée, PEVerify vérifie également des méthodes critiques qui peuvent contenir du code non vérifiable.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> d’attribut, ou supprimez le code non vérifiable.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 La méthode dans cet exemple utilise du code non vérifiable et doit être marquée avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.  
  
 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]