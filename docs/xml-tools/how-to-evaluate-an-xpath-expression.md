---
title: Évaluer une expression XPath pendant le débogage
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1585b54d084e3471583f9388d63f5c17e65fc3a7
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526320"
---
# <a name="evaluate-xpath-expressions"></a>Évaluer des expressions XPath

Vous pouvez évaluer des expressions XPath à l’aide de la **Espion express** fenêtre pendant le débogage. L’expression XPath doit être valide par rapport à la recommandation du W3C sur XPath 1.0. Le contexte XSLT actuel (autrement dit, le `self::node()` nœud dans le **variables locales** fenêtre) fournit le contexte d’évaluation de l’expression XPath.

Lorsque vous évaluez une expression XPath :

- Les fonctions XPath intégrées sont prises en charge.

- Les fonctions XSLT intégrées et les fonctions définies par l’utilisateur ne sont pas pris en charge.

> [!NOTE]
> Débogage XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="evaluate-an-xpath-expression"></a>Évaluer une expression XPath

La procédure suivante utilise le *ci-dessous average.xsl* et *books.xml* fichiers à partir de la [procédure pas à pas : Déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md#sample-files) page.

1. Insérez un point d’arrêt à l’étiquette de début `xsl:if`.

2. Pour démarrer le débogage, choisissez **XML** > **démarrer le débogage XSLT** sur la barre de menus (ou appuyez sur **Alt**+**F5** ).

   Le débogueur démarre et s'arrête à la balise `xsl:if`.

3. Avec le bouton droit et sélectionnez **Espion express**.

   Le **Espion express** fenêtre s’ouvre.

4. Entrez `./price/text()` dans le **Expression** champ la **Espion express** boîte de dialogue zone, puis choisissez **réévaluer**.

   Le prix du nœud book actuel s’affiche dans le **valeur** boîte.

   ![Évaluer une expression XPath dans la fenêtre Espion express](media/quickwatch-price.png)

5. Modifier l’expression XPath pour `./price/text() < $bookAverage` et cliquez sur **réévaluer**.

   Le **valeur** boîte montre que l’expression XPath a la valeur `true`.

## <a name="see-also"></a>Voir aussi

- [Débogage XSLT](../xml-tools/debugging-xslt.md)