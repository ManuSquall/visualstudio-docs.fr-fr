---
title: Déboguer des feuilles de style XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e787ca3d2d29f04d6af27a5f36f1f84c9d0bc9f4
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526631"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procédure pas à pas : Déboguer une feuille de style XSLT

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT. Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code. Le débogueur vous permet d’exécuter le code ligne par ligne à la fois.

Pour préparer cette procédure pas à pas, tout d’abord copier les deux [exemples de fichiers](#sample-files) sur votre ordinateur local. Une est la feuille de style et une est le fichier XML que nous allons utiliser comme entrée pour la feuille de style. Dans cette procédure pas à pas, nous utilisons la feuille de style recherche tous les livres dont le coût est inférieur au prix moyen d’un livre.

> [!NOTE]
> Le débogueur XSLT est uniquement disponible dans l’édition Enterprise de Visual Studio.

## <a name="start-debugging"></a>Démarrer le débogage

1. À partir de la **fichier** menu, choisissez **Open** > **fichier**.

2. Recherchez le *ci-dessous average.xsl* de fichier et choisissez **Open**.

   La feuille de style s’ouvre dans l’éditeur XML.

3. Cliquez sur le bouton Parcourir (**...** ) sur le **entrée** champ de la fenêtre de propriétés de document. (Si le **propriétés** fenêtre n’est pas visible, cliquez n’importe où sur le fichier ouvert dans l’éditeur, puis choisissez **propriétés**.)

4. Recherchez le *books.xml* de fichiers, puis choisissez **Open**.

   Cela définit le fichier du document source qui est utilisé pour la transformation XSLT.

5. Définir un [point d’arrêt](../debugger/using-breakpoints.md) de la ligne 12 de *ci-dessous average.xsl*. Vous pouvez effectuer cela de plusieurs manières :

   - Cliquez dans la marge de l’éditeur sur la ligne 12.

   - Cliquez n’importe où sur la ligne 12, puis appuyez sur **F9**.

   - Cliquez sur le `xsl:if` balise de début, puis choisissez **point d’arrêt** > **insérer un point d’arrêt**.

      ![Insérer un point d’arrêt dans le fichier XSL dans Visual Studio](media/insert-breakpoint.PNG)

6. Dans la barre de menus, choisissez **XML** > **démarrer le débogage XSLT** (ou appuyez sur **Alt**+**F5**).

   Le processus de débogage commence.

   Dans l’éditeur, le débogueur est positionné sur le `xsl:if` élément de la feuille de style. Un autre fichier nommé *ci-dessous average.xml* s’ouvre dans l’éditeur ; c’est le fichier de sortie qui sera rempli en tant que chaque nœud dans le fichier d’entrée *books.xml* est traité.

   Le **automatique**, **variables locales**, et **Espion 1** windows apparaissent au bas de la fenêtre Visual Studio. Le **variables locales** fenêtre affiche toutes les variables locales et leurs valeurs actuelles. Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.

## <a name="watch-window"></a>Fenêtre Espion

Nous allons ajouter deux variables pour le **Espion 1** fenêtre afin de nous pouvons examiner leurs valeurs que le fichier d’entrée est traité. (Vous pouvez également utiliser le **variables locales** fenêtre afin d’examiner les valeurs si les variables que vous souhaitez regarder existent déjà.)

1. À partir de la **déboguer** menu, choisissez **Windows** > **espion** > **Espion 1**.

   Le **Espion 1** fenêtre devient visible.

2. Type `$bookAverage` dans le **nom** champ, puis appuyez sur **entrée**.

   La valeur de la `$bookAverage` variable s’affiche dans le **valeur** champ.

3. Sur la ligne suivante, tapez `self::node()` dans le **nom** champ, puis appuyez sur **entrée**.

   `self::node()` est une expression XPath qui évalue le nœud de contexte actuel. La valeur de l'expression XPath `self::node()` est le premier nœud book. Cette valeur change à mesure que la transformation progresse.

4. Développez le `self::node()` nœud, puis développez le nœud qui a la valeur est `price`.

   ![Fenêtre Espion pendant le débogage XSLT dans Visual Studio](media/xslt-debugging-watch-window.png)

   Vous pouvez afficher la valeur du prix du livre pour le nœud book actuel et la comparer à la `$bookAverage` valeur. Étant donné que le prix du livre est inférieur à la moyenne, le `xsl:if` condition doit réussir lorsque vous reprenez le processus de débogage.

## <a name="step-through-the-code"></a>Parcourir le code

1. Appuyez sur **F5** pour continuer.

   Étant donné que le premier nœud book répond le `xsl:if` condition, il est ajouté à la *ci-dessous average.xml* fichier de sortie. Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant placé sur le second nœud book dans le *books.xml* fichier.

   Dans le **Espion 1** fenêtre, le `self::node()` change de valeur pour le second nœud book. En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.

2. Appuyez sur **F5** pour continuer.

   Étant donné que le second nœud book ne répond pas à la `xsl:if` condition, le nœud book n’est pas ajouté à la *ci-dessous average.xml* fichier de sortie. Le débogueur continue à s’exécuter jusqu'à ce qu’il est positionné à nouveau sur le `xsl:if` élément dans la feuille de style. Le débogueur est maintenant placé sur le troisième `book` nœud dans le *books.xml* fichier.

   Dans le **Espion 1** fenêtre, le `self::node()` valeur devient le troisième nœud book. En examinant la valeur de la `price` élément, vous pouvez déterminer que le prix est inférieur à la moyenne. Le `xsl:if` condition doit réussir.

3. Appuyez sur **F5** pour continuer.

   Étant donné que le `xsl:if` condition est remplie, le troisième livre est ajouté à la *ci-dessous average.xml* fichier de sortie. Tous les livres du document XML ont été traités et le débogueur s'arrête.

## <a name="sample-files"></a>Exemples de fichiers

La procédure pas à pas utilise les deux fichiers suivants.

### <a name="below-averagexsl"></a>below-average.xsl

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
        <xsl:if test="price &lt; $bookAverage">
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