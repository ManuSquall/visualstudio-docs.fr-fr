---
title: 'CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 77ff02a0db733c3151f4faccd00e07518d61e600
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588066"
---
# <a name="ca2137-transparent-methods-must-contain-only-verifiable-il"></a>CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2137 : les méthodes transparentes doivent contenir uniquement des IL vérifiables](https://docs.microsoft.com/visualstudio/code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il).

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

 Pour être certain que votre code contient du code MSIL vérifiable uniquement, exécutez [Peverify.exe (outil PEVerify)](http://msdn.microsoft.com/library/f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa) sur votre assembly. Exécutez PEVerify avec le **/ transparent** option qui limite la sortie aux seuls non vérifiable méthodes transparentes qui entraînerait une erreur. Si le / option transparente n’est pas utilisée, PEVerify vérifie également des méthodes critiques qui peuvent contenir du code non vérifiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> d’attribut, ou supprimez le code non vérifiable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 La méthode dans cet exemple utilise du code non vérifiable et doit être marquée avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2137.transparentmethodsmustbeverifiable/cs/ca2137 - transparentmethodsmustbeverifiable.cs#1)]



