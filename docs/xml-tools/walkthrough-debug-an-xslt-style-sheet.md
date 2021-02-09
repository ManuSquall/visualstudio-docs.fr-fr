---
title: Déboguer les feuilles de style XSLT
description: Découvrez comment utiliser le débogueur XSLT dans Visual Studio pour déboguer une feuille de style XSLT en suivant les étapes décrites dans cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: how-to
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7935abf4bee4d7f9532ca1dfae0b7105c42067d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875157"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procédure pas à pas : Déboguer une feuille de style XSLT

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT. Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code. Le débogueur vous permet d’exécuter le code ligne par ligne.

Pour préparer cette procédure pas à pas, commencez par copier les deux [exemples de fichiers](#sample-files) sur votre ordinateur local. L’une est la feuille de style, et l’autre est le fichier XML que nous allons utiliser comme entrée de la feuille de style. Dans cette procédure pas à pas, la feuille de style que nous utilisons recherche tous les livres dont le coût est inférieur au prix moyen des livres.

> [!NOTE]
> Le débogueur XSLT n’est disponible que dans les éditions Professional et Enterprise de Visual Studio.

## <a name="start-debugging"></a>Démarrer le débogage

1. Dans le menu **fichier** , choisissez **ouvrir** un  >  **fichier**.

2. Recherchez le fichier *Below-Average. xsl* , puis choisissez **ouvrir**.

   La feuille de style s’ouvre dans l’éditeur XML.

3. Cliquez sur le bouton Parcourir (**...**) dans le champ **entrée** de la fenêtre Propriétés du document. (Si la fenêtre **Propriétés** n’est pas visible, cliquez avec le bouton droit n’importe où sur le fichier ouvert dans l’éditeur, puis choisissez **Propriétés**.)

4. Recherchez le fichier *books.xml* , puis choisissez **ouvrir**.

   Cela définit le fichier de document source utilisé pour la transformation XSLT.

5. Définissez un [point d’arrêt](../debugger/using-breakpoints.md) sur la ligne 12 de *Below-Average. xsl*. Pour ce faire, vous pouvez procéder de plusieurs façons :

   - Cliquez dans la marge de l’éditeur à la ligne 12.

   - Cliquez n’importe où sur la ligne 12, puis appuyez sur **F9**.

   - Cliquez avec le bouton droit sur la `xsl:if` balise de début, puis choisissez **point d’arrêt**  >  **Insérer un point d’arrêt**.

      ![Insérer un point d’arrêt dans un fichier XSL dans Visual Studio](media/insert-breakpoint.PNG)

6. Dans la barre de menus, choisissez **XML**  >  **Démarrer le débogage XSLT** (ou appuyez sur **ALT** + **F5**).

   Le processus de débogage démarre.

   Dans l’éditeur, le débogueur est positionné sur l' `xsl:if` élément de la feuille de style. Un autre fichier nommé *below-average.xml* s’ouvre dans l’éditeur. Il s’agit du fichier de sortie qui sera rempli à mesure que chaque nœud du fichier d’entrée *books.xml* est traité.

   Les fenêtres **automatique**, **variables locales** et **Espion 1** s’affichent en bas de la fenêtre de Visual Studio. La fenêtre variables **locales** affiche toutes les variables locales et leurs valeurs actuelles. Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.

## <a name="watch-window"></a>Fenêtre Espion

Nous allons ajouter deux variables à la fenêtre **Espion 1** afin que nous puissions examiner leurs valeurs lors du traitement du fichier d’entrée. (Vous pouvez également utiliser la fenêtre **variables locales** pour examiner les valeurs si les variables que vous souhaitez surveiller sont déjà présentes).

1. Dans le menu **Déboguer** , choisissez espion **Windows**  >  **Watch**  >  **1**.

   La fenêtre **Espion 1** devient visible.

2. Tapez `$bookAverage` dans le champ **nom** , puis appuyez sur **entrée**.

   La valeur de la `$bookAverage` variable s’affiche dans le champ **valeur** .

3. Sur la ligne suivante, tapez `self::node()` dans le champ **nom** , puis appuyez sur **entrée**.

   `self::node()` expression XPath qui prend la valeur du nœud de contexte actuel. La valeur de l'expression XPath `self::node()` est le premier nœud book. Cette valeur change à mesure que la transformation progresse.

4. Développez le `self::node()` nœud, puis développez le nœud dont la valeur est `price` .

   ![Fenêtre Espion lors du débogage XSLT dans Visual Studio](media/xslt-debugging-watch-window.png)

   Vous pouvez voir la valeur du prix du livre pour le nœud de livre actuel et la comparer à la `$bookAverage` valeur. Étant donné que le prix du livre est inférieur à la moyenne, la `xsl:if` condition doit être correctement exécutée lorsque vous poursuivez le processus de débogage.

## <a name="step-through-the-code"></a>Parcourir le code

1. Appuyez sur **F5** pour continuer.

   Étant donné que le premier nœud book `xsl:if` a respecté la condition, le nœud book est ajouté au fichier de sortie *below-average.xml* . Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débogueur est maintenant positionné sur le deuxième nœud book dans le fichier *books.xml* .

   Dans la fenêtre **Espion 1** , la `self::node()` valeur devient le deuxième nœud book. En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.

2. Appuyez sur **F5** pour continuer.

   Étant donné que le deuxième nœud book ne remplit pas la `xsl:if` condition, le nœud book n’est pas ajouté au fichier de sortie *below-average.xml* . Le débogueur continue à s’exécuter jusqu’à ce qu’il soit de nouveau positionné sur l' `xsl:if` élément dans la feuille de style. Le débogueur est maintenant positionné sur le troisième `book` nœud dans le fichier *books.xml* .

   Dans la fenêtre **Espion 1** , la `self::node()` valeur devient le troisième nœud de livre. En examinant la valeur de l' `price` élément, vous pouvez déterminer que le prix est inférieur à la moyenne. La `xsl:if` condition doit être correctement exécutée.

3. Appuyez sur **F5** pour continuer.

   Étant donné que la `xsl:if` condition a été satisfaite, le troisième livre est ajouté au fichier de sortie *below-average.xml* . Tous les livres du document XML ont été traités et le débogueur s'arrête.

## <a name="sample-files"></a>Exemple de fichiers

La procédure pas à pas utilise les deux fichiers suivants.

### <a name="below-averagexsl"></a>Below-Average. Xsl

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
