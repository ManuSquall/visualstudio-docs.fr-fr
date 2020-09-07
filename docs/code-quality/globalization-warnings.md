---
title: Avertissements liés à la globalisation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd215a8b5c8dfb5905117638883d94d09268ce3d
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509846"
---
# <a name="globalization-warnings"></a>Avertissements liés à la globalisation
Les avertissements de globalisation prennent en charge des bibliothèques et des applications mondialisables.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1303 : Ne pas passer de littéraux en paramètres localisés](../code-quality/ca1303.md)|Une méthode visible de l’extérieur passe un littéral de chaîne en tant que paramètre à une méthode ou un constructeur .NET, et cette chaîne doit être localisable.|
|[CA1304 : Spécifier CultureInfo](../code-quality/ca1304.md)|Une méthode ou un constructeur appelle un membre présentant une surcharge qui accepte un paramètre System.Globalization.CultureInfo, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre CultureInfo. Lorsqu'un objet CultureInfo ou System.IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|
|[CA1305 : Spécifier IFormatProvider](../code-quality/ca1305.md)|Une méthode ou un constructeur appelle un ou plusieurs membres présentant des surcharges qui acceptent un paramètre System.IFormatProvider, et la méthode ou le constructeur n'appelle pas la surcharge qui prend le paramètre IFormatProvider. Lorsqu'un objet System.Globalization.CultureInfo ou IFormatProvider n'est pas fourni, la valeur par défaut fournie par le membre surchargé peut ne pas avoir l'effet escompté selon les différents paramètres régionaux.|
|[CA1306 : Définir les paramètres régionaux pour les types de données](../code-quality/ca1306.md)|Les paramètres régionaux déterminent des éléments de présentation des données spécifiques à la culture, telles que la mise en forme utilisée pour les valeurs numériques, les symboles monétaires et l'ordre de tri. Lorsque vous créez un DataTable ou un DataSet, vous devez définir les paramètres régionaux explicitement.|
|[CA1307 : Spécifier StringComparison pour clarifier](../code-quality/ca1307.md)|Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison.|
|[CA1308 : Normaliser les chaînes en majuscules](../code-quality/ca1308.md)|Les chaînes doivent être normalisées en majuscules. En cas de conversion en minuscules, un petit groupe de caractères ne peut pas faire un aller-retour.|
|[CA1309 : Utiliser StringComparison avec la valeur Ordinal](../code-quality/ca1309.md)|Opération de comparaison de chaînes non linguistique qui n'affecte pas la valeur Ordinal ou OrdinalIgnoreCase au paramètre StringComparison. En affectant explicitement au paramètre la valeur StringComparison.Ordinal ou StringComparison.OrdinalIgnoreCase, votre code gagne souvent en rapidité, tout en devenant plus correct et plus fiable.|
|[CA1310 : Spécifier StringComparison pour corriger](../code-quality/ca1310.md)|Une opération de comparaison de chaînes utilise une surcharge de méthode qui ne définit pas de paramètre StringComparison et utilise par défaut la comparaison de chaînes propre à la culture.|
|[CA2101 : spécifiez le marshaling pour les arguments de chaîne P/Invoke](../code-quality/ca2101.md)|Un membre d’appel de code non managé autorise les appelants de confiance partielle, a un paramètre de chaîne et ne marshale pas explicitement la chaîne. Cela peut provoquer une faille de sécurité potentielle.|
