---
title: 'CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
helpviewer_keywords:
- DoNotHardcodeLocaleSpecificStrings
- CA1302
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f01bcbf0d717ff8728d87b55f2cfd1c7c5af34d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1302-do-not-hardcode-locale-specific-strings"></a>CA1302 : Ne pas coder en dur les chaînes spécifiques aux paramètres régionaux
|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Category|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode utilise un littéral de chaîne qui représente la partie du chemin d’accès de certains dossiers système.  
  
## <a name="rule-description"></a>Description de la règle  
 Le <xref:System.Environment.SpecialFolder?displayProperty=fullName> énumération contient des membres qui font référence à des dossiers système spéciaux. Les emplacements de ces dossiers peuvent avoir des valeurs différentes sur différents systèmes d’exploitation, l’utilisateur peut modifier certains des emplacements, et ces derniers sont localisés. Un exemple d’un dossier spécial est le dossier système, qui est « C:\WINDOWS\system32 » sur [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)] mais « C:\WINNT\system32 » sur [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)]. Le <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> méthode retourne les emplacements qui sont associés les <xref:System.Environment.SpecialFolder> énumération. Les emplacements qui sont retournées par <xref:System.Environment.GetFolderPath%2A> sont localisés et appropriés pour l’ordinateur en cours d’exécution.  
  
 Cette règle de segmentation en unités lexicales les chemins d’accès du dossier qui sont récupérés à l’aide de la <xref:System.Environment.GetFolderPath%2A> méthode dans les niveaux de répertoires séparés. Chaque littéral de chaîne est comparé aux jetons. Si une correspondance est trouvée, il est supposé que la méthode de générer une chaîne qui fait référence à l’emplacement du système qui est associé au jeton. Pour la portabilité et l’adaptabilité, utilisez la <xref:System.Environment.GetFolderPath%2A> méthode pour récupérer les emplacements des dossiers système spéciaux au lieu d’utiliser des littéraux de chaîne.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, extraire l’emplacement à l’aide de la <xref:System.Environment.GetFolderPath%2A> (méthode).  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si le littéral de chaîne n’est pas utilisé pour faire référence à un des emplacements du système qui est associé à la <xref:System.Environment.SpecialFolder> énumération.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère le chemin d’accès du dossier application data commun, qui génère trois avertissements de cette règle. Ensuite, l’exemple récupère le chemin d’accès à l’aide de la <xref:System.Environment.GetFolderPath%2A> (méthode).  
  
 [!code-csharp[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA1303 : Ne passez pas des littéraux comme paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)