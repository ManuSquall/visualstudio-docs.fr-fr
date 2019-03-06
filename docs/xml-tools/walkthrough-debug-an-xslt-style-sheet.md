---
title: "Procédure pas à pas : débogage d'une feuille de style XSLT"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e04a2baa31c9fbcd7dd9c2ceeba7ed0840e8b28
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930075"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procédure pas à pas : Déboguer une feuille de style XSLT

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT. Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code. La feuille de style recherche tous les livres coûtant moins que le prix moyen du livre.

## <a name="to-prepare-for-this-walkthrough"></a>Pour vous préparer à cette procédure

1.  Fermez les solutions ouvertes.

2.  Copiez les deux fichiers exemples vers votre ordinateur local.

## <a name="start-debugging"></a>Démarrer le débogage

### <a name="to-start-debugging"></a>Pour démarrer le débogage

1.  À partir de la **fichier** menu, pointez sur **Open**, puis cliquez sur **fichier**.

2.  Recherchez le *belowAvg.xsl* de fichier et cliquez sur **Open**.

     La feuille de style s'ouvre dans l'éditeur XML.

3.  Cliquez sur le bouton Parcourir (**...** ) sur le **entrée** champ de la fenêtre de propriétés de document.

4.  Recherchez le *books.xml* de fichier et cliquez sur **Open**.

     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.

5.  Avec le bouton droit le `xsl:if` balise de début, pointez sur **point d’arrêt**, puis cliquez sur **insérer un point d’arrêt**.

6.  Cliquez sur le **débogage XSLT** dans la barre d’outils de l’éditeur XML.

Le processus de débogage commence, ouvrant plusieurs nouvelles fenêtres utilisées par le débogueur.

Il existe deux fenêtres qui affichent le document d'entrée et la feuille de style. Le débogueur utilise ces fenêtres pour afficher l'état actuel de l'exécution. Le débogueur est positionné sur le `xsl:if` élément de la feuille de style et sur le premier nœud book dans le *books.xml* fichier.

Le **variables locales** fenêtre affiche toutes les variables locales et leurs valeurs actuelles. Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.

Le **sortie XSLT** fenêtre affiche la sortie de la transformation XSL. Cette fenêtre est distincte de la **sortie de Visual Studio** fenêtre.

## <a name="watch-window"></a>Fenêtre Espion

### <a name="to-use-the-watch-window"></a>Pour utiliser la fenêtre Espion

1.  À partir de la **déboguer** menu, pointez sur **Windows**, pointez sur **espion**, puis cliquez sur **Espion 1**.

     Cela rend la **Espion 1** fenêtre visible.

2.  Type `$bookAverage` dans le **nom** champ et appuyez sur **entrée**.

     La valeur de la variable `$bookAverage` s'affiche dans la fenêtre.

3.  Type `self::node()` dans le **nom** champ et appuyez sur **entrée**.

     `self::node()` est une expression XPath qui évalue le nœud de contexte actuel. La valeur de l'expression XPath `self::node()` est le premier nœud book. Cette valeur change à mesure que la transformation progresse.

4.  Développez le nœud `self::node()`, puis le nœud `price`.

     La valeur du prix du livre s'affiche et vous pouvez la comparer facilement à celle de `$bookAverage`. Puisque le prix du livre est inférieur à la moyenne, la condition `xsl:if` doit se vérifier.

## <a name="step-through-the-code"></a>Parcourir le code
 Le débogueur permet d'exécuter le code ligne par ligne.

### <a name="to-step-through-the-code"></a>Pour parcourir le code pas à pas

1.  Appuyez sur **F5** pour continuer.

     Étant donné que le premier nœud book répond le `xsl:if` condition, il est ajouté à la **sortie XSLT** fenêtre. Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant placé sur le second nœud book dans le *books.xml* fichier.

     Dans le **Espion 1** fenêtre le `self::node()` change de valeur pour le second nœud book. En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.

2.  Appuyez sur **F5** pour continuer.

     Étant donné que le second nœud book ne répond pas à la `xsl:if` condition, le nœud book n’est pas ajouté à la **sortie XSLT** fenêtre. Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant placé sur le troisième `book` nœud dans le *books.xml* fichier.

     Dans le **Espion 1** fenêtre le `self::node()` valeur devient le troisième nœud book. En examinant la valeur de l'élément `price`, vous pouvez constater que le prix est inférieur à la moyenne, donc la condition `xsl:if` doit se vérifier.

3.  Appuyez sur **F5** pour continuer.

     Étant donné que le `xsl:if` condition est remplie, le troisième livre est ajouté à la **sortie XSLT** fenêtre. Tous les livres du document XML ont été traités et le débogueur s'arrête.

## <a name="sample-files"></a>Exemples de fichiers

La procédure pas à pas utilise les deux fichiers suivants.

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
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

```xml
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

- [Débogage XSLT](../xml-tools/debugging-xslt.md)