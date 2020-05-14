---
title: Feuilles de style Debug XSLT
ms.date: 03/05/2019
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd5882cc606bf241a281940464ba028e77986807
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301719"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Procédure pas à pas: Debug une feuille de style XSLT

Les étapes de cette procédure pas à pas montrent comment utiliser le débogueur XSLT. Elles comprennent l'affichage des variables, la définition de points d'arrêt et le parcours pas à pas du code. Le débbuggeur vous permet d’exécuter le code une ligne à la fois.

Pour vous préparer à cette procédure pas à pas, copiez d’abord les deux [fichiers d’échantillons](#sample-files) sur votre ordinateur local. L’une est la feuille de style, et l’autre est le fichier XML que nous allons utiliser comme entrée à la feuille de style. Dans cette procédure pas à pas, la feuille de style que nous utilisons trouve tous les livres dont le coût est inférieur au prix moyen du livre.

> [!NOTE]
> Le débbugger XSLT n’est disponible que dans l’édition Enterprise de Visual Studio.

## <a name="start-debugging"></a>Démarrer le débogage

1. Dans le menu **Fichier,** choisissez **Open** > **File**.

2. Localiser le fichier *ci-dessous-moyenne.xsl* et choisir **Open**.

   La feuille de style s’ouvre dans l’éditeur XML.

3. Cliquez sur le bouton de navigation (**...**) sur le champ **d’entrée** de la fenêtre des propriétés du document. (Si la fenêtre **Propriétés** n’est pas visible, cliquez à droite n’importe où sur le fichier ouvert dans l’éditeur, puis choisissez **propriétés**.)

4. Localiser le fichier *books.xml,* puis choisir **Open**.

   Cela définit le fichier de document source qui est utilisé pour la transformation XSLT.

5. Définissez un [point d’arrêt](../debugger/using-breakpoints.md) sur la ligne 12 de *below-average.xsl*. Vous pouvez le faire de l’une des multiples façons :

   - Cliquez sur la marge de l’éditeur sur la ligne 12.

   - Cliquez n’importe où sur la ligne 12, puis appuyez sur **F9**.

   - Cliquez à `xsl:if` droite sur l’étiquette de démarrage, puis choisissez **Breakpoint** > **Insert Breakpoint**.

      ![Insérez le point d’arrêt dans le fichier XSL dans Visual Studio](media/insert-breakpoint.PNG)

6. Sur la barre de menu, choisissez **XML** > **Start XSLT Debugging** (ou, appuyez sur **Alt**+**F5**).

   Le processus de débogage commence.

   Dans l’éditeur, le débbuggeur `xsl:if` est positionné sur l’élément de la feuille de style. Un autre fichier nommé *ci-dessous-average.xml s’ouvre* dans l’éditeur; c’est le fichier de sortie qui sera peuplé comme chaque nœud dans le fichier d’entrée *books.xml* est traitée.

   Les **Autos**, **Les sections locales**et les fenêtres **Watch 1** apparaissent au bas de la fenêtre Visual Studio. La fenêtre local affiche toutes les variables **locales** et leurs valeurs actuelles. Cela comprend les variables définies dans la feuille de style ainsi que celles que le débogueur utilise pour assurer le suivi des nœuds actuellement dans le contexte.

## <a name="watch-window"></a>Fenêtre Espion

Nous ajouterons deux variables à la fenêtre **Watch 1** afin que nous puissions examiner leurs valeurs au fur et à mesure que le fichier d’entrée est traité. (Vous pouvez également utiliser la fenêtre **Locals** pour examiner les valeurs si les variables que vous voulez regarder sont déjà là.)

1. Dans le menu **Debug,** choisissez **Windows** > **Watch** > **Watch 1**.

   La fenêtre **Watch 1** devient visible.

2. Tapez `$bookAverage` dans le champ **nom,** puis appuyez **sur Entrez**.

   La valeur `$bookAverage` des écrans variables dans le champ **De** valeur.

3. Sur la ligne `self::node()` suivante, tapez dans le champ **Nom,** puis appuyez **sur Enter**.

   `self::node()`est une expression XPath qui évalue au nœud de contexte actuel. La valeur de l'expression XPath `self::node()` est le premier nœud book. Cette valeur change à mesure que la transformation progresse.

4. Élargir `self::node()` le nœud, puis élargir le nœud qui est la valeur est `price`.

   ![Regarder la fenêtre pendant le débogage XSLT dans Visual Studio](media/xslt-debugging-watch-window.png)

   Vous pouvez voir la valeur du prix du livre pour `$bookAverage` le nœud de livre actuel et le comparer à la valeur. Parce que le prix du `xsl:if` livre est inférieur à la moyenne, la condition devrait réussir lorsque vous continuez le processus de débogage.

## <a name="step-through-the-code"></a>Passez à travers le code

1. Appuyez **sur F5** pour continuer.

   Parce que le premier nœud de livre satisfait à la `xsl:if` condition, le nœud de livre est ajouté au fichier de sortie inférieur à la *moyenne.xml.* Le débogueur continue l'exécution jusqu'à ce qu'il se repositionne sur l'élément `xsl:if` de la feuille de style. Le débbuggeur est maintenant positionné sur le nœud de deuxième livre dans le fichier *books.xml.*

   Dans la fenêtre Watch `self::node()` **1,** la valeur change au deuxième nœud de livre. En examinant la valeur de l'élément price, vous pouvez constater que le prix est supérieur à la moyenne, donc la condition `xsl:if` ne doit pas se vérifier.

2. Appuyez **sur F5** pour continuer.

   Parce que le nœud `xsl:if` de deuxième livre ne répond pas à la condition, le nœud de livre n’est pas ajouté au fichier de sortie *ci-dessous-moyenne.xml.* Le débbuggeur continue d’exécuter jusqu’à `xsl:if` ce qu’il soit positionné à nouveau sur l’élément dans la feuille de style. Le débbuggeur est maintenant positionné `book` sur le troisième nœud dans le fichier *books.xml.*

   Dans la fenêtre Watch `self::node()` **1,** la valeur change au nœud du troisième livre. En examinant la `price` valeur de l’élément, vous pouvez déterminer que le prix est inférieur à la moyenne. La `xsl:if` condition devrait réussir.

3. Appuyez **sur F5** pour continuer.

   Puisque `xsl:if` la condition était satisfaite, le troisième livre est ajouté au fichier de sortie inférieur à *la moyenne.xml.* Tous les livres du document XML ont été traités et le débogueur s'arrête.

## <a name="sample-files"></a>Exemple de fichiers

La procédure pas à pas utilise les deux fichiers suivants.

### <a name="below-averagexsl"></a>en dessous de la moyenne.xsl

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
