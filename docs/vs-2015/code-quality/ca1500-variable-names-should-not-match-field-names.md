---
title: 'Ca1500 : les noms de variables ne doivent pas correspondre aux noms de champs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9565bc1ae3166c0475e8af7f0fde381497309b01
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547912"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500 : Les noms de variables ne doivent pas être identiques aux noms de champs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [ca1500 : les noms de variables ne doivent pas correspondre aux noms de champs](/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names).

|Élément|Valeur|
|-|-|
|TypeName|VariableNamesShouldNotMatchFieldNames|
|CheckId|CA1500|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|En cas de déclenchement sur un paramètre portant le même nom qu’un champ :<br /><br /> -Sans rupture : si le champ et la méthode qui déclarent le paramètre ne peuvent pas être vus à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br />-Break : Si vous modifiez le nom du champ et que vous pouvez le voir à l’extérieur de l’assembly.<br />-Break : Si vous modifiez le nom du paramètre et que la méthode qui le déclare peut être affichée à l’extérieur de l’assembly.<br /><br /> En cas de déclenchement sur une variable locale qui porte le même nom qu’un champ :<br /><br /> -Sans rupture : si le champ ne peut pas être affiché à l’extérieur de l’assembly, quelle que soit la modification que vous apportez.<br />-Sans rupture : Si vous modifiez le nom de la variable locale et que vous ne modifiez pas le nom du champ.<br />-Break : Si vous modifiez le nom du champ et qu’il est visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Une méthode d’instance déclare un paramètre ou une variable locale dont le nom correspond à un champ d’instance du type déclarant. Pour intercepter les variables locales qui violent la règle, l’assembly testé doit être généré à l’aide des informations de débogage et le fichier de base de données du programme (. pdb) associé doit être disponible.

## <a name="rule-description"></a>Description de la règle
 Lorsque le nom d’un champ d’instance correspond à un paramètre ou à un nom de variable locale, le champ d’instance est accessible à l’aide du `this` `Me` mot clé (en) à l' [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] intérieur du corps de la méthode. Lors de la maintenance du code, il est facile d’oublier cette différence et de supposer que la variable locale/de paramètre fait référence au champ d’instance, ce qui génère des erreurs. Cela est vrai surtout pour les corps de méthode longs.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez le paramètre/la variable ou le champ.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre deux violations de la règle.

 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]
