---
title: 'CA2137 : les méthodes transparentes doivent contenir uniquement un IL vérifiable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6219acde1f62c946e08325f4764dc49dde461d2f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546573"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|TransparentMethodsMustBeVerifiable|
|CheckId|CA2137|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Une méthode contient du code non vérifiable ou retourne un type par référence.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche lorsque le code transparent de sécurité tente d’exécuter du code MSIL (Microsoft Intermediate Language) non vérifiable. Toutefois, la règle ne contient pas de vérificateur IL (Intermediate Language) complet, et à la place utilise l’heuristique pour intercepter la plupart des violations de vérification MSIL.

 Pour être certain que votre code contient uniquement du code MSIL vérifiable, exécutez [Peverify.exe (outil PEVerify)](https://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) sur votre assembly. Exécutez PEVerify avec l’option **/transparent** , qui limite la sortie aux méthodes transparentes non vérifiables qui provoquent une erreur. Si l’option/transparent n’est pas utilisée, PEVerify vérifie également les méthodes critiques autorisées à contenir du code non vérifiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode avec <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attribut ou, ou supprimez le code non vérifiable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 La méthode dans cet exemple utilise du code non vérifiable et doit être marquée avec l' <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> attribut ou.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]
