---
title: 'CA1415 : déclarer correctement les appels P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9931d29c818d95785146558637c32237e2c5276
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547847"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415 : Déclarer correctement les méthodes P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture : si P/Invoke qui déclare le paramètre ne peut pas être affiché à l’extérieur de l’assembly. Avec rupture : si l’appel P/Invoke qui déclare le paramètre peut être affiché à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Une méthode d’appel de code non managé est déclarée de manière incorrecte.

## <a name="rule-description"></a>Description de la règle
 Une méthode d’appel de plateforme accède au code non managé et est définie à l’aide du `Declare` mot clé dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ou <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Actuellement, cette règle recherche des déclarations de méthode d’appel de code non managé qui ciblent des fonctions Win32 qui ont un pointeur vers un paramètre de structure OVERLAPPED et le paramètre managé correspondant n’est pas un pointeur vers une <xref:System.Threading.NativeOverlapped?displayProperty=fullName> structure.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, déclarez correctement la méthode d’appel de code non managé.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre des méthodes d’appel de code non managé qui violent la règle et satisfont à la règle.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DeclarePInvokes/cs/FxCop.Interoperability.DeclarePInvokes.cs#1)]

## <a name="see-also"></a>Voir aussi
 [Interopération avec du code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
