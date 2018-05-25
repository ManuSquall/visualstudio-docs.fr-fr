---
title: "Procédure : utiliser des points d'arrêt avec XSLT"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 430b7f14f35506b45fe73be47d056cdd7b6a9c95
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Comment : utiliser des points d’arrêt avec XSLT

Vous pouvez définir des points d'arrêt dans une feuille de style XSLT ou dans le document source XML. Si vous définissez un point d’arrêt sur une étiquette, lors de l’exécution, le point d’arrêt est déplacé vers l’instruction suivante qui possède des informations de ligne source.

Pour plus d’informations, consultez [éléments fondamentaux du débogage : points d’arrêt](../debugger/using-breakpoints.md).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Définir un point d’arrêt dans une feuille de style

Des points d’arrêt peuvent être définis pour les étiquettes de début, les étiquettes de fin et les nœuds de texte d’une feuille de style XSLT. Les points d'arrêt peuvent également être définis sur du code dans un bloc de script.

### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Pour définir un point d'arrêt dans une feuille de style

1.  Ouvrez une feuille de style dans l'éditeur XML.

2.  Placez le curseur à l’emplacement du point d’arrêt, avec le bouton droit, pointez sur **point d’arrêt**, puis cliquez sur **insérer un point d’arrêt**.

3.  Cliquez sur le bouton Parcourir (**...** ) sur le **entrée** champ de la fenêtre de propriétés de document.

4.  Recherchez le document source XML et cliquez sur **ouvrir**.

     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.

5.  Cliquez sur le **débogage XSLT** dans la barre d’outils de l’éditeur XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Définir un point d’arrêt dans un document source XML

Les points d'arrêt peuvent être définis sur des éléments, des attributs, un nœud d'espace de noms, des commentaires, une instruction de traitement et des nœuds de texte d'un document source XML. Il est impossible de définir un point d'arrêt sur le nœud de document ou sur un nœud d'espace de noms hérité de l'élément parent.

### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Pour définir un point d'arrêt dans un document source XML

1.  Ouvrez le document XML dans l'éditeur XML.

2.  Placez le curseur à l’emplacement du point d’arrêt, avec le bouton droit, pointez sur **point d’arrêt**, puis cliquez sur **insérer un point d’arrêt**.

3.  Cliquez sur le bouton Parcourir (**...** ) sur le **Stylesheet** champ de la fenêtre de propriétés de document.

4.  Recherchez le document source XML et cliquez sur **ouvrir**.

     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.

5.  Cliquez sur le **débogage XSLT** dans la barre d’outils de l’éditeur XML.

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)