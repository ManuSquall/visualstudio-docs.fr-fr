---
title: "CA1302&#160;: Ne pas coder en dur les cha&#238;nes sp&#233;cifiques aux param&#232;tres r&#233;gionaux | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
helpviewer_keywords: 
  - "DoNotHardcodeLocaleSpecificStrings"
  - "CA1302"
ms.assetid: 05ed134a-837d-43d7-bf97-906edeac44ce
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1302&#160;: Ne pas coder en dur les cha&#238;nes sp&#233;cifiques aux param&#232;tres r&#233;gionaux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotHardcodeLocaleSpecificStrings|  
|CheckId|CA1302|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode utilise un littéral de chaîne qui représente une partie du chemin d'accès à certains dossiers système.  
  
## Description de la règle  
 L'énumération <xref:System.Environment.SpecialFolder?displayProperty=fullName> contient des membres qui font référence à des dossiers système spéciaux.  Les emplacements de ces dossiers peuvent avoir des valeurs divergentes selon le système d'exploitation ; l'utilisateur peut modifier certains des emplacements, et ces derniers sont localisés.  Un exemple d'un dossier spécial est le dossier système, qui est « C:\\WINDOWS\\system32 » sur [!INCLUDE[winxp](../code-quality/includes/winxp_md.md)], mais "C:\\WINNT\\system32" sur [!INCLUDE[win2kfamily](../code-quality/includes/win2kfamily_md.md)].  La méthode <xref:System.Environment.GetFolderPath%2A?displayProperty=fullName> retourne les emplacements associés à l'énumération <xref:System.Environment.SpecialFolder>.  Les emplacements retournés par <xref:System.Environment.GetFolderPath%2A> sont localisés et adaptés à l'ordinateur en cours d'exécution.  
  
 Cette règle régit sous forme de jeton les chemins d'accès aux dossiers récupérés par le biais de la méthode <xref:System.Environment.GetFolderPath%2A> dans différents niveaux de répertoires séparés.  Chaque littéral de chaîne est comparé aux jetons.  Si une correspondance est trouvée, la méthode est censée générer une chaîne qui fait référence à l'emplacement système associé au jeton.  Par souci de portabilité et d'adaptabilité, utilisez la méthode <xref:System.Environment.GetFolderPath%2A> pour récupérer les emplacements des dossiers système spéciaux, au lieu d'utiliser des littéraux de chaîne.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, récupérez l'emplacement à l'aide de la méthode <xref:System.Environment.GetFolderPath%2A>.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le littéral de chaîne n'est pas utilisé pour référencer l'un des emplacements système associés à l'énumération <xref:System.Environment.SpecialFolder>.  
  
## Exemple  
 L'exemple suivant génère le chemin d'accès au dossier Application Data commun, qui génère trois avertissements issus de cette règle.  Ensuite, l'exemple récupère le chemin d'accès à l'aide de la méthode <xref:System.Environment.GetFolderPath%2A>.  
  
 [!code-cs[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/CSharp/ca1302-do-not-hardcode-locale-specific-strings_1.cs)]
 [!code-vb[FxCop.Globalization.HardcodedLocaleStrings#1](../code-quality/codesnippet/VisualBasic/ca1302-do-not-hardcode-locale-specific-strings_1.vb)]  
  
## Règles connexes  
 [CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)