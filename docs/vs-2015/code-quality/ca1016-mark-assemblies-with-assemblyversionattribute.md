---
title: 'Ca1016 : marquer les assemblys avec AssemblyVersionAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 97bd41e51c8d6b5415ffb91c5696c7055f46cf7c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545403"
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016 : Marquer les assemblys avec AssemblyVersionAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|MarkAssembliesWithAssemblyVersion|
|CheckId|CA1016|
|Category|Microsoft. Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 L’assembly n’a pas de numéro de version.

## <a name="rule-description"></a>Description de la règle
 L’identité d’un assembly est composée des informations suivantes :

- Nom de l'assembly

- Numéro de version

- Culture

- Clé publique (pour les assemblys avec nom fort).

  Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] utilise le numéro de version pour identifier un assembly de manière unique, et créer une liaison avec des types présents dans des assemblys à nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un numéro de version à l’assembly à l’aide de l' <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attribut. Consultez l’exemple qui suit.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas un avertissement de cette règle pour les assemblys utilisés par des tiers ou dans un environnement de production.

## <a name="example"></a>Exemple
 L’exemple suivant montre un assembly auquel l' <xref:System.Reflection.AssemblyVersionAttribute> attribut est appliqué.

 [!code-cpp[FxCop.Design.AssembliesVersion#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cpp/FxCop.Design.AssembliesVersion.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/cs/FxCop.Design.AssembliesVersion.cs#1)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesVersion/vb/FxCop.Design.AssembliesVersion.vb#1)]

## <a name="see-also"></a>Voir aussi
 Contrôle de [version des assemblys](https://msdn.microsoft.com/library/775ad4fb-914f-453c-98ef-ce1089b6f903) [Comment : créer une stratégie d’éditeur](https://msdn.microsoft.com/library/8046bc5d-2fa9-4277-8a5e-6dcc96c281d9)
