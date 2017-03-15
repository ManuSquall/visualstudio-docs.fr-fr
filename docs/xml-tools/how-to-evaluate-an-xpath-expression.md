---
title: "Proc&#233;dure&#160;: &#233;valuer une expression XPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 159ba4ef-75e4-4ac8-80dc-e064e0bec345
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: &#233;valuer une expression XPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez évaluer des expressions XPath à l'aide de la boîte de dialogue **Espion express**.L'expression XPath doit être valide par rapport à la recommandation du W3C sur XPath 1.0.Le contexte XSLT actuel, à savoir le nœud `self::node()` de la fenêtre **Variables locales**, constitue le contexte d'évaluation de l'expression XPath.  
  
 La liste suivante décrit les fonctions prises en charge lors de l'évaluation d'une expression XPath :  
  
-   Les fonctions XPath intégrées sont prises en charge.  
  
-   Les fonctions XSLT intégrées ne sont pas prises en charge.  
  
-   Les fonctions définies par l'utilisateur ne sont pas prises en charge.  
  
> [!NOTE]
>  La procédure suivante utilise les fichiers belowAvg.xsl et books.xml de la rubrique [Procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md).  
  
### Pour évaluer une expression XPath  
  
1.  Insérez un point d'arrêt à la balise de début `xsl:if`.  
  
2.  Cliquez sur le bouton **Débogage XSLT** dans la barre d'outils de l'éditeur XML.  
  
     Le débogueur démarre et s'arrête à la balise `xsl:if`.  
  
3.  Cliquez avec le bouton droit et sélectionnez **Espion express**.  
  
     La boîte de dialogue **Espion express** s'affiche.  
  
4.  Entrez `./price/text()` dans le champ **Expression** de la boîte de dialogue **Espion express** et cliquez sur **Réévaluer**.  
  
     Le prix du nœud book actuel s'affiche dans la zone **Valeur**.  
  
5.  Modifiez l'expression XPath en `./price/text() < $bookAverage` et cliquez sur **Réévaluer**.  
  
     La zone **Valeur** indique que l'expression XPath donne la valeur `true`.  
  
## Voir aussi  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)