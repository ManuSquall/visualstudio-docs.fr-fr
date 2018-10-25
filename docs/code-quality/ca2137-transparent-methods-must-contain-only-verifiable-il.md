---
title: 'CA2137 : Les méthodes transparentes doivent contenir uniquement des IL vérifiables'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2137
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 131824b22291acb0b83af6ff24e9751a98db3ed1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845333"
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
 Cette règle se déclenche lorsque le code transparent de sécurité tente d’exécuter du code MSIL (Microsoft Intermediate Language) non vérifiable. Toutefois, la règle ne contient pas de vérificateur IL (Intermediate Language) complet, et à la place utilise l’heuristique pour intercepter la plupart des violations de vérification MSIL.

 Pour être certain que votre code contient du code MSIL vérifiable uniquement, exécutez [Peverify.exe (outil PEVerify)](/dotnet/framework/tools/peverify-exe-peverify-tool) sur votre assembly. Exécutez PEVerify avec le **/ transparent** option qui limite la sortie aux seuls non vérifiable méthodes transparentes qui entraînerait une erreur. Si le / option transparente n’est pas utilisée, PEVerify vérifie également des méthodes critiques qui peuvent contenir du code non vérifiable.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> d’attribut, ou supprimez le code non vérifiable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 La méthode dans cet exemple utilise du code non vérifiable et doit être marquée avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

 [!code-csharp[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]