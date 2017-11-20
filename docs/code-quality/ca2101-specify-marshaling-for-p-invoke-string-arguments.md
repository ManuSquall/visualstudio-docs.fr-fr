---
title: "CA2101 : Spécifiez le marshaling pour les arguments de chaîne P-Invoke | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SpecifyMarshalingForPInvokeStringArguments
- CA2101
helpviewer_keywords:
- CA2101
- SpecifyMarshalingForPInvokeStringArguments
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a759662b35024add1666e99c89433f0b369676b7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca2101-specify-marshaling-for-pinvoke-string-arguments"></a>CA2101 : Spécifiez le marshaling pour les arguments de chaîne P/Invoke
|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Catégorie|Microsoft.Globalization|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un appel de membre autorise les appelants partiellement approuvés, a un paramètre de chaîne et ne marshale pas explicitement la chaîne.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsque vous convertissez à partir d’Unicode en ANSI, il est possible que tous les caractères Unicode peuvent être représentés dans une page de codes ANSI spécifique. *Le mappage ajusté* essaie de résoudre ce problème en remplaçant un caractère qui ne peut pas être représenté. L’utilisation de cette fonctionnalité peut provoquer une faille de sécurité potentiel, car vous ne pouvez pas contrôler le caractère qui est choisi. Par exemple, un code malveillant pourrait créer intentionnellement une chaîne Unicode qui contient des caractères qui ne figurent pas dans une page de codes spécifique, qui sont converties en caractères spéciaux de système de fichiers tels que '..' ou '/'. Notez également que les vérifications de sécurité pour les caractères spéciaux se produisent fréquemment avant la chaîne est convertie au format ANSI.  
  
 Mappage le mieux adapté est la valeur par défaut pour la conversion non managée, WChar en Mo. Sauf si vous désactivez explicitement le mappage ajusté, votre code peut contenir une faille de sécurité exploitable en raison de ce problème.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, marshaler explicitement des types de données chaîne.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre une méthode qui enfreint cette règle, puis indique comment corriger la violation.  
  
 [!code-csharp[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]