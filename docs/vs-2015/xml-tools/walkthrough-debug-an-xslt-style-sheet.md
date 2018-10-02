---
title: 'Procédure pas à pas : Déboguer une feuille de Style XSLT | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 969bccce307683252c695ebe1d337aa08b04d022
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492796"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procédure pas à pas : déboguer une feuille de style XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT. Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code. La feuille de style recherche tous les livres coûtant moins que le prix moyen du livre.  
  
### <a name="to-prepare-for-this-walkthrough"></a>Pour vous préparer à cette procédure  
  
1.  Fermez les solutions ouvertes.  
  
2.  Copiez les deux fichiers exemples vers votre ordinateur local.  
  
## <a name="start-debugging"></a>Lancement du débogage  
  
#### <a name="to-start-debugging"></a>Pour démarrer le débogage  
  
1.  À partir de la **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.  
  
2.  Recherchez le fichier belowAvg.xsl et cliquez sur **Open**.  
  
     La feuille de style s'ouvre dans l'éditeur XML.  
  
3.  Cliquez sur le bouton Parcourir (**...** ) sur le **entrée** champ de la fenêtre de propriétés de document.  
  
4.  Recherchez le fichier books.xml et cliquez sur **Open**.  
  
     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.  
  
5.  Avec le bouton droit le `xsl:if` balise de début, pointez sur **point d’arrêt**, puis cliquez sur **insérer un point d’arrêt**.  
  
6.  Cliquez sur le **débogage XSLT** dans la barre d’outils de l’éditeur XML.  
  
 Le processus de débogage commence, ouvrant plusieurs nouvelles fenêtres utilisées par le débogueur.  
  
 Il existe deux fenêtres qui affichent le document d'entrée et la feuille de style. Le débogueur utilise ces fenêtres pour afficher l'état actuel de l'exécution. Le débogueur est positionné sur l'élément `xsl:if` de la feuille de style et sur le premier nœud book du fichier books.xml.  
  
 La fenêtre Variables locales affiche toutes les variables locales et leur valeur actuelle. Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.  
  
 Le **sortie XSLT** fenêtre affiche la sortie de la transformation XSL. Cette fenêtre est distincte de la **sortie de Visual Studio** fenêtre.  
  
## <a name="watch-window"></a>Fenêtre Espion  
  
#### <a name="to-use-the-watch-window"></a>Pour utiliser la fenêtre Espion  
  
1.  À partir de la **déboguer** menu, pointez sur **Windows**, pointez sur **espion**, puis cliquez sur **Espion 1**.  
  
     La fenêtre Espion 1 s'affiche.  
  
2.  Type `$bookAverage` dans le **nom** champ et appuyez sur ENTRÉE.  
  
     La valeur de la variable `$bookAverage` s'affiche dans la fenêtre.  
  
3.  Type `self::node()` dans le **nom** champ et appuyez sur ENTRÉE.  
  
     `self::node()` est une expression XPath qui évalue le nœud de contexte actuel. La valeur de l'expression XPath `self::node()` est le premier nœud book. Cette valeur change à mesure que la transformation progresse.  
  
4.  Développez le nœud `self::node()`, puis le nœud `price`.  
  
     La valeur du prix du livre s'affiche et vous pouvez la comparer facilement à celle de `$bookAverage`. Puisque le prix du livre est inférieur à la moyenne, la condition `xsl:if` doit se vérifier.  
  
## <a name="step-through-the-code"></a>Parcours du code pas à pas  
 Le débogueur permet d'exécuter le code ligne par ligne.  
  
#### <a name="to-step-through-the-code"></a>Pour parcourir le code pas à pas  
  
1.  Appuyez sur **F5** pour continuer.  
  
     Puisque le premier nœud book répond à la condition `xsl:if`, il est ajouté à la fenêtre de sortie XSL. Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant placé sur le deuxième nœud book dans le fichier books.xml.  
  
     Dans la fenêtre Espion1, la valeur `self::node()` devient le second nœud book. En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.  
  
2.  Appuyez sur **F5** pour continuer.  
  
     Puisque le second nœud book ne répond pas à la condition `xsl:if`, il n'est pas ajouté à la fenêtre de sortie XSL. Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant placé sur le troisième nœud `book` dans le fichier books.xml.  
  
     Dans la fenêtre Espion1, la valeur `self::node()` devient le troisième nœud book. En examinant la valeur de l'élément `price`, vous pouvez constater que le prix est inférieur à la moyenne, donc la condition `xsl:if` doit se vérifier.  
  
3.  Appuyez sur **F5** pour continuer.  
  
     Puisque la condition `xsl:if` s'est vérifiée, le troisième livre est ajouté à la fenêtre de sortie XSL. Tous les livres du document XML ont été traités et le débogueur s'arrête.  
  
## <a name="sample-files"></a>Fichiers exemples  
 La procédure pas à pas utilise les deux fichiers suivants.  
  
### <a name="belowavgxsl"></a>belowAvg.xsl  
  
```  
<?xml version='1.0'?>  
<xsl:stylesheet version="1.0"  
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  <xsl:output method="xml" encoding="utf-8"/>  
  <xsl:template match="/">  
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>  
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>  
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>  
    <books>  
      <!--Books That Cost Below Average-->  
      <xsl:for-each select="/bookstore/book">  
        <xsl:if test="price < $bookAverage">  
          <xsl:copy-of select="."/>  
        </xsl:if>  
      </xsl:for-each>  
    </books>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
### <a name="booksxml"></a>books.xml  
  
```  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database -->  
<bookstore>  
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">  
    <title>The Autobiography of Benjamin Franklin</title>  
    <author>  
      <first-name>Benjamin</first-name>  
      <last-name>Franklin</last-name>  
    </author>  
    <price>8.99</price>  
  </book>  
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">  
    <title>The Confidence Man</title>  
    <author>  
      <first-name>Herman</first-name>  
      <last-name>Melville</last-name>  
    </author>  
    <price>11.99</price>  
  </book>  
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">  
    <title>The Gorgias</title>  
    <author>  
      <name>Plato</name>  
    </author>  
    <price>9.99</price>  
  </book>  
</bookstore>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage XSLT](../xml-tools/debugging-xslt.md)

