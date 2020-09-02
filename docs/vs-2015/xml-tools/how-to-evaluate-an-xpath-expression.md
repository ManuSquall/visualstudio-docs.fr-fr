---
title: 'Comment : évaluer une expression XPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ecec9004506a9bd05d3d773e44bb264af363f96f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670865"
---
# <a name="how-to-evaluate-an-xpath-expression"></a>Procédure : évaluer une expression XPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez évaluer des expressions XPath à l’aide de la boîte de dialogue **Espion express** . L’expression XPath doit être valide par rapport à la recommandation du W3C sur XPath 1.0. Le contexte XSLT actuel, autrement dit le `self::node()` nœud dans la fenêtre **variables locales** , fournit le contexte d’évaluation de l’expression XPath.

 La liste suivante décrit les fonctions prises en charge lors de l'évaluation d'une expression XPath :

- Les fonctions XPath intégrées sont prises en charge.

- Les fonctions XSLT intégrées ne sont pas prises en charge.

- Les fonctions définies par l'utilisateur ne sont pas prises en charge.

> [!NOTE]
> La procédure suivante utilise les fichiers belowAvg. xsl et books.xml de la rubrique [procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) .

### <a name="to-evaluate-an-xpath-expression"></a>Pour évaluer une expression XPath

1. Insérez un point d’arrêt à l’étiquette de début `xsl:if`.

2. Cliquez sur le bouton **Déboguer xsl** dans la barre d’outils de l’éditeur XML.

     Le débogueur démarre et s'arrête à la balise `xsl:if`.

3. Cliquez avec le bouton droit et sélectionnez **Espion express**.

     La boîte de dialogue **Espion express** s’affiche.

4. Entrez `./price/text()` dans le champ **expression** de la boîte de dialogue **Espion express** , puis cliquez sur **réévaluer**.

     Le prix du nœud book actuel s’affiche dans la zone **valeur** .

5. Modifiez l’expression XPath en `./price/text() < $bookAverage` et cliquez sur **réévaluer**.

     La zone **valeur** indique que l’expression XPath prend la valeur `true` .

## <a name="see-also"></a>Voir aussi
 [Débogage XSLT](../xml-tools/debugging-xslt.md)
