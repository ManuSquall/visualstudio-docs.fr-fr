---
title: 'Comment : utiliser des points d’arrêt avec XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0519c3ab19e7d36aa26ea2f462c8a4571b9f8b32
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656308"
---
# <a name="how-to-use-breakpoints-with-xslt"></a>Procédure : utiliser des points d'arrêt avec XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez définir des points d'arrêt dans une feuille de style XSLT ou dans le document source XML. Si vous définissez un point d'arrêt sur une balise, lors de l'exécution, le point d'arrêt est déplacé vers l'instruction suivante qui possède des informations de ligne source.

 Pour plus d’informations, consultez [concepts de base du débogage : points d’arrêt](https://msdn.microsoft.com/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).

## <a name="set-a-breakpoint-in-a-style-sheet"></a>Définir un point d'arrêt dans une feuille de style
 Des points d’arrêt peuvent être définis pour les étiquettes de début, les étiquettes de fin et les nœuds de texte d’une feuille de style XSLT. Les points d'arrêt peuvent également être définis sur du code dans un bloc de script.

#### <a name="to-set-a-breakpoint-in-a-style-sheet"></a>Pour définir un point d'arrêt dans une feuille de style

1. Ouvrez une feuille de style dans l'éditeur XML.

2. Placez le curseur à l’emplacement du point d’arrêt, cliquez avec le bouton droit, pointez sur point d' **arrêt**, puis cliquez sur **Insérer un point d’arrêt**.

3. Cliquez sur le bouton Parcourir (**...**) dans le champ **entrée** de la fenêtre Propriétés du document.

4. Recherchez le document source XML, puis cliquez sur **ouvrir**.

     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.

5. Cliquez sur le bouton **Déboguer xsl** dans la barre d’outils de l’éditeur XML.

## <a name="set-a-breakpoint-in-an-xml-source-document"></a>Définir un point d'arrêt dans un document source XML
 Les points d'arrêt peuvent être définis sur des éléments, des attributs, un nœud d'espace de noms, des commentaires, une instruction de traitement et des nœuds de texte d'un document source XML. Il est impossible de définir un point d'arrêt sur le nœud de document ou sur un nœud d'espace de noms hérité de l'élément parent.

#### <a name="to-set-a-breakpoint-in-an-xml-source-document"></a>Pour définir un point d'arrêt dans un document source XML

1. Ouvrez le document XML dans l'éditeur XML.

2. Placez le curseur à l’emplacement du point d’arrêt, cliquez avec le bouton droit, pointez sur point d' **arrêt**, puis cliquez sur **Insérer un point d’arrêt**.

3. Cliquez sur le bouton Parcourir (**...**) dans le champ **feuille de style** de la fenêtre Propriétés du document.

4. Recherchez le document source XML, puis cliquez sur **ouvrir**.

     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.

5. Cliquez sur le bouton **Déboguer xsl** dans la barre d’outils de l’éditeur XML.

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
