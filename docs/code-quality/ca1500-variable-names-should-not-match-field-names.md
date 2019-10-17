---
title: 'CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 3f7e8b0021fc3c318389aa3d6d3f53391b71351f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72443965"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs

|||
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|En cas de déclenchement sur un paramètre portant le même nom qu’un champ :<br /><br /> -Sans rupture : si le champ et la méthode qui déclarent le paramètre ne peuvent pas être vus à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br />-Break : Si vous modifiez le nom du champ et que vous pouvez le voir à l’extérieur de l’assembly.<br />-Break : Si vous modifiez le nom du paramètre et que la méthode qui le déclare peut être affichée à l’extérieur de l’assembly.<br /><br /> En cas de déclenchement sur une variable locale qui porte le même nom qu’un champ :<br /><br /> -Sans rupture : si le champ ne peut pas être affiché à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br />-Sans rupture : Si vous modifiez le nom de la variable locale et que vous ne modifiez pas le nom du champ.<br />-Break : Si vous modifiez le nom du champ et qu’il est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause

Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant. Pour intercepter les variables locales qui violent la règle, l’assembly testé doit être généré à l’aide des informations de débogage et le fichier de base de données du programme (. pdb) associé doit être disponible.

## <a name="rule-description"></a>Description de la règle

Lorsque le nom d’un champ d’instance correspond à un paramètre ou à un nom de variable locale, le champ d’instance est accessible à l’aide du mot clé `this` (`Me` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) lorsqu’il est dans le corps de la méthode. Lors de la maintenance du code, il est facile d’oublier cette différence et de supposer que la variable locale/de paramètre fait référence au champ d’instance, ce qui génère des erreurs. Cela est vrai surtout pour les corps de méthode longs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, renommez le paramètre/la variable ou le champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple

L’exemple suivant montre deux violations de la règle.

[!code-vb[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/VisualBasic/ca1500-variable-names-should-not-match-field-names_1.vb)]
[!code-csharp[FxCop.Maintainability.VarMatchesField#1](../code-quality/codesnippet/CSharp/ca1500-variable-names-should-not-match-field-names_1.cs)]
