---
title: "CA1303 : Ne pas transmettre des littéraux localisées comme paramètres | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Do not pass literals as localized parameters
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
helpviewer_keywords:
- DoNotPassLiteralsAsLocalizedParameters
- CA1303
ms.assetid: 904d284e-76d0-4b8f-a4df-0094de8d7aac
caps.latest.revision: "22"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 361155e9d46e4f71ddc61775f56105cedb5d18b9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1303-do-not-pass-literals-as-localized-parameters"></a>CA1303 : Ne pas transmettre des littéraux en tant que paramètres localisés
|||  
|-|-|  
|TypeName|DoNotPassLiteralsAsLocalizedParameters|  
|CheckId|CA1303|  
|Category|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Une méthode passe une littéral de chaîne en tant que paramètre à un constructeur ou une méthode dans le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] bibliothèque de classes et cette chaîne doit être localisable.  
  
 Cet avertissement est déclenché lorsqu’une chaîne littérale est passée comme valeur pour un paramètre ou une propriété et un ou plusieurs des cas suivants sont vrai :  
  
-   Le <xref:System.ComponentModel.LocalizableAttribute> attribut du paramètre ou de propriété est définie sur true.  
  
-   Le nom de paramètre ou la propriété contient « Texte », « Message » ou « Caption ».  
  
-   Le nom du paramètre de chaîne qui est passé à une méthode Console.Write ou Console.WriteLine est « value » ou « format ».  
  
## <a name="rule-description"></a>Description de la règle  
 Littéraux de chaîne qui sont incorporés dans le code source sont difficiles à localiser.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le littéral de chaîne par une chaîne récupérée via une instance de la <xref:System.Resources.ResourceManager> classe.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si la bibliothèque de code n’est pas localisée, ou si la chaîne n’est pas exposée à l’utilisateur final ou un développeur à l’aide de la bibliothèque de code.  
  
 Les utilisateurs peuvent éliminer le bruit sur les méthodes qui ne doivent pas être passées des chaînes localisées, soit en renommant le paramètre ou la propriété nommée, ou en marquant ces éléments comme conditionnels.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui lève une exception lorsqu’un de ses deux arguments sont hors limites. Pour le premier argument, le constructeur de l’exception est passé à une chaîne littérale, ce qui enfreint cette règle. Pour le second argument, le constructeur reçoit correctement une chaîne récupérée via un <xref:System.Resources.ResourceManager>.  
  
 [!code-cpp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CPP/ca1303-do-not-pass-literals-as-localized-parameters_1.cpp)]
 [!code-vb[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/VisualBasic/ca1303-do-not-pass-literals-as-localized-parameters_1.vb)]
 [!code-csharp[FxCop.Globalization.DoNotPassLiterals#1](../code-quality/codesnippet/CSharp/ca1303-do-not-pass-literals-as-localized-parameters_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Ressources dans des applications de bureau](/dotnet/framework/resources/index)