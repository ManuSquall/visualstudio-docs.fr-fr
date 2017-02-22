---
title: "Proc&#233;dure&#160;: utiliser des points d&#39;arr&#234;t avec XSLT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: bf7bbc2c-71dc-4cac-a6fc-add6b27d92ed
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: utiliser des points d&#39;arr&#234;t avec XSLT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez définir des points d'arrêt dans une feuille de style XSLT ou dans le document source XML.Si vous définissez un point d'arrêt sur une balise, lors de l'exécution, le point d'arrêt est déplacé vers l'instruction suivante qui possède des informations de ligne source.  
  
 Pour plus d'informations, consultez [Debugging Basics: Breakpoints](http://msdn.microsoft.com/fr-fr/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e).  
  
## Définir un point d'arrêt dans une feuille de style  
 Des points d'arrêt peuvent être définis pour les balises de début, les balises de fin et les nœuds de texte d'une feuille de style XSLT.Les points d'arrêt peuvent également être définis sur du code dans un bloc de script.  
  
#### Pour définir un point d'arrêt dans une feuille de style  
  
1.  Ouvrez une feuille de style dans l'éditeur XML.  
  
2.  Placez le curseur à l'emplacement du point d'arrêt, cliquez avec le bouton droit, pointez sur **Point d'arrêt** et cliquez sur **Insérer un point d'arrêt**.  
  
3.  Cliquez sur le bouton Parcourir \(**...**\) dans le champ **Entrée** de la fenêtre de propriétés du document.  
  
4.  Recherchez le document source XML, puis cliquez sur **Ouvrir**.  
  
     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.  
  
5.  Cliquez sur le bouton **Débogage XSLT** dans la barre d'outils de l'éditeur XML.  
  
## Définir un point d'arrêt dans un document source XML  
 Les points d'arrêt peuvent être définis sur des éléments, des attributs, un nœud d'espace de noms, des commentaires, une instruction de traitement et des nœuds de texte d'un document source XML.Il est impossible de définir un point d'arrêt sur le nœud de document ou sur un nœud d'espace de noms hérité de l'élément parent.  
  
#### Pour définir un point d'arrêt dans un document source XML  
  
1.  Ouvrez le document XML dans l'éditeur XML.  
  
2.  Placez le curseur à l'emplacement du point d'arrêt, cliquez avec le bouton droit, pointez sur **Point d'arrêt** et cliquez sur **Insérer un point d'arrêt**.  
  
3.  Cliquez sur le bouton Parcourir \(**...**\) dans le champ **Feuille de style** de la fenêtre de propriétés du document.  
  
4.  Recherchez le document source XML, puis cliquez sur **Ouvrir**.  
  
     Vous définissez ainsi le document source à utiliser pour la transformation XSLT.  
  
5.  Cliquez sur le bouton **Débogage XSLT** dans la barre d'outils de l'éditeur XML.  
  
## Voir aussi  
 [Procédure pas à pas : déboguer une feuille de style XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)