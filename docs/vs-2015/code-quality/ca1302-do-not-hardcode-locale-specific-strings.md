---
title: 'CA1302 : ne pas coder en dur les chaînes spécifiques aux paramètres régionaux | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6e16fff154b5c0df660b06e5bf9e9e838762adff
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661476"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Une méthode utilise un littéral de chaîne qui représente une partie du chemin d’accès de certains dossiers système.

## <a name="rule-description"></a>Description de la règle
 L’énumération <xref:System.Environment.SpecialFolder?displayProperty=fullName> contient des membres qui font référence à des dossiers système spéciaux. Les emplacements de ces dossiers peuvent avoir des valeurs différentes sur différents systèmes d’exploitation, l’utilisateur peut modifier certains des emplacements, et les emplacements sont localisés. Un exemple de dossier spécial est le dossier système, qui est « C:\WINDOWS\system32 » sur [!INCLUDE[winxp](../includes/winxp-md.md)] mais « C:\WINNT\system32 » sur [!INCLUDE[win2kfamily](../includes/win2kfamily-md.md)]. La méthode <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> retourne les emplacements associés à l’énumération <xref:System.Environment.SpecialFolder>. Les emplacements retournés par <xref:System.Environment.GetFolderPath%2A> sont localisés et appropriés pour l’ordinateur en cours d’exécution.

 Cette règle régit les chemins d’accès aux dossiers qui sont récupérés à l’aide de la méthode <xref:System.Environment.GetFolderPath%2A> dans des niveaux de répertoire distincts. Chaque littéral de chaîne est comparé aux jetons. Si une correspondance est trouvée, il est supposé que la méthode génère une chaîne qui fait référence à l’emplacement système associé au jeton. Pour la portabilité et l’adaptabilité, utilisez la méthode <xref:System.Environment.GetFolderPath%2A> pour récupérer les emplacements des dossiers système spéciaux au lieu d’utiliser des littéraux de chaîne.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, récupérez l’emplacement à l’aide de la méthode <xref:System.Environment.GetFolderPath%2A>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si le littéral de chaîne n’est pas utilisé pour faire référence à l’un des emplacements système associés à l’énumération <xref:System.Environment.SpecialFolder>.

## <a name="example"></a>Exemple
 L’exemple suivant génère le chemin d’accès du dossier Common Application Data, qui génère trois avertissements à partir de cette règle. Ensuite, l’exemple récupère le chemin d’accès à l’aide de la méthode <xref:System.Environment.GetFolderPath%2A>.

 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/cs/FxCop.Globalization.HardcodedLocaleStrings.cs#1)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Globalization.HardcodedLocaleStrings/vb/FxCop.Globalization.HardcodedLocaleStrings.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA1303 : Ne passez pas des littéraux comme paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)
