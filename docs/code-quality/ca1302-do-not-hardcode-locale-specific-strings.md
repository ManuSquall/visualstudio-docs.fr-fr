---
title: 'CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 69b6256f2c6ae54467eb21cc17d50119b3c67a9f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235175"
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux

|||
|-|-|
|TypeName|DoNotHardcodeLocaleSpecificStrings|
|CheckId|CA1302|
|Category|Microsoft. Globalization|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Une méthode utilise un littéral de chaîne qui représente une partie du chemin d’accès de certains dossiers système.

## <a name="rule-description"></a>Description de la règle
L' <xref:System.Environment.SpecialFolder?displayProperty=fullName> énumération contient des membres qui font référence à des dossiers système spéciaux. Les emplacements de ces dossiers peuvent avoir des valeurs différentes sur différents systèmes d’exploitation, l’utilisateur peut modifier certains des emplacements, et les emplacements sont localisés. Un exemple de dossier spécial est le dossier système, qui est « C:\Windows\System32 » sur [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] , mais « C:\Winnt\System32 [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]». La <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> méthode retourne les emplacements associés à l' <xref:System.Environment.SpecialFolder> énumération. Les emplacements retournés par <xref:System.Environment.GetFolderPath%2A> sont localisés et appropriés pour l’ordinateur en cours d’exécution.

Cette règle régit les chemins d’accès des dossiers qui sont récupérés à l’aide de la <xref:System.Environment.GetFolderPath%2A> méthode dans des niveaux de répertoire distincts. Chaque littéral de chaîne est comparé aux jetons. Si une correspondance est trouvée, il est supposé que la méthode génère une chaîne qui fait référence à l’emplacement système associé au jeton. Pour la portabilité et l’adaptabilité, <xref:System.Environment.GetFolderPath%2A> utilisez la méthode pour récupérer les emplacements des dossiers système spéciaux au lieu d’utiliser des littéraux de chaîne.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, récupérez l’emplacement à l' <xref:System.Environment.GetFolderPath%2A> aide de la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Il est possible de supprimer sans risque un avertissement de cette règle si le littéral de chaîne n’est pas utilisé pour faire référence à l’un des emplacements système <xref:System.Environment.SpecialFolder> associés à l’énumération.

## <a name="example"></a>Exemple
L’exemple suivant génère le chemin d’accès du dossier Common Application Data, qui génère trois avertissements à partir de cette règle. Ensuite, l’exemple récupère le chemin d’accès à l' <xref:System.Environment.GetFolderPath%2A> aide de la méthode.

[!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
[!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]

## <a name="related-rules"></a>Règles associées
[CA1303 Ne pas passer de littéraux en tant que paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)