---
title: 'CA1500 : Les noms de variables ne doivent pas correspondre aux noms de champ | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fdac60aa7b3fb37f45cff7c1c9e5f17920efed18
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173938"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio 2017, consultez [CA1500 : les noms de variables ne doivent pas correspondre aux noms de champs](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names) sur docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Category|Microsoft.Maintainability|  
|Modification avec rupture|Lorsqu’il est déclenché sur un paramètre qui porte le même nom en tant que champ :<br /><br /> Sans rupture - Si le champ et la méthode qui déclare le paramètre ne sont pas visibles en dehors de l’assembly, quelle que soit la modification effectuée.<br />Rupture - Si vous modifiez le nom du champ et pouvez être consultés en dehors de l’assembly.<br />-Modification avec rupture - Si vous modifiez le nom du paramètre et la méthode qui le déclare peut être consultée en dehors de l’assembly.<br /><br /> Lorsqu’il est déclenché sur une variable locale qui a le même nom en tant que champ :<br /><br /> Sans rupture - Si le champ ne peut pas être visible en dehors de l’assembly, quelle que soit la modification effectuée.<br />Sans rupture - Si vous modifiez le nom de la variable locale et que vous ne modifiez pas le nom du champ.<br />-Modification avec rupture - Si vous modifiez le nom du champ et que vous pouvez le constater en dehors de l’assembly.|  
  
## <a name="cause"></a>Cause  
 Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant. Pour intercepter les variables locales qui enfreignent la règle, l’assembly testé doit être construit à l’aide des informations de débogage et le fichier de base de données (.pdb) du programme associé doit être disponible.  
  
## <a name="rule-description"></a>Description de la règle  
 Lorsque le nom d’un champ d’instance correspond à un paramètre ou un nom de variable locale, le champ d’instance est accessible à l’aide de la `this` (`Me` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) mot clé à l’intérieur du corps de méthode. Lors de la maintenance du code, il est facile de les oublier cette différence et supposent que la paramètre ou la variable locale fait référence au champ d’instance, ce qui entraîne des erreurs. Cela est vrai en particulier pour les corps de méthode longs.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, renommez le paramètre/variable ou le champ.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre deux violations de la règle.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

