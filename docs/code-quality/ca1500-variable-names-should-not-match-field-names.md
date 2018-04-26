---
title: 'CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa5c015205b5e325cfba06bb433c44ecc0631d5b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs
|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Lorsqu’il est déclenché sur un paramètre qui porte le même nom qu’un champ :<br /><br /> -Non rupture - Si le champ et la méthode qui déclare le paramètre ne peut pas être visible à l’extérieur de l’assembly, quelle que soit la modification effectuée.<br />Rupture - Si vous modifiez le nom du champ et pouvez être consultés à l’extérieur de l’assembly.<br />-Modification avec rupture - Si vous modifiez le nom du paramètre et la méthode qui le déclare peut être consultée à l’extérieur de l’assembly.<br /><br /> Lorsqu’il est déclenché sur une variable locale qui porte le même nom qu’un champ :<br /><br /> Sans rupture - Si le champ ne peut pas être visible à l’extérieur de l’assembly, quelle que soit la modification effectuée.<br />Sans rupture - Si vous modifiez le nom de la variable locale et que vous ne modifiez pas le nom du champ.<br />-Modification avec rupture - Si vous modifiez le nom du champ et que vous pouvez le constater en dehors de l’assembly.|

## <a name="cause"></a>Cause
 Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant. Pour intercepter les variables locales qui enfreignent la règle, l’assembly testé doit être construit à l’aide des informations de débogage et le fichier de base de données (.pdb) de programme associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
 Lorsque le nom d’un champ d’instance correspond à un paramètre ou un nom de variable locale, le champ d’instance est accessible à l’aide de la `this` (`Me` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) (mot clé) à l’intérieur du corps de la méthode. Lors de la gestion du code, il est facile de les oublier cette différence et supposent que la paramètre ou la variable locale fait référence au champ d’instance, ce qui entraîne des erreurs. Cela est vrai, en particulier pour les corps de méthode longs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez le paramètre/variable ou le champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux violations de la règle.

 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]