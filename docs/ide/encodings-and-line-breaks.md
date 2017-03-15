---
title: "Encodages et sauts de ligne | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.Encoding"
helpviewer_keywords: 
  - "éditeurs, sauts de ligne"
  - "encoder"
  - "caractères de saut de ligne"
  - "sauts de ligne"
  - "Visual Studio, encoder"
  - "Visual Studio, caractères de saut de ligne"
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Encodages et sauts de ligne
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser la  **Options d'enregistrement de fichier Advanced** paramètres afin de déterminer le type de saut de ligne de caractères que vous souhaitez.  Vous pouvez également modifier l'encodage d'un fichier avec les mêmes paramètres.  
  
> [!NOTE]
>  Si vous disposez de certains types de paramètres de développement \(Visual Basic, F\#, Web Development\) vous ne voyiez pas  **Options d'enregistrement avancées** dans le menu.  Pour modifier vos paramètres \(par exemple comptabilité\), ouvrez  **Outils \/ importation et exportation de paramètres**.  Pour plus informations, consultez  [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Dans Visual Studio, les caractères suivants sont interprétés comme des sauts de ligne :  
  
-   CRLF : retour chariot \+ saut de ligne, caractères Unicode 000D \+  
  
-   LF : saut de ligne, caractère Unicode 000 a  
  
-   NEL : ligne suivante, caractère Unicode 0085  
  
-   LS : séparateur de ligne, caractère Unicode 2028  
  
-   PS : séparateur de paragraphe, caractère Unicode 2029  
  
 Texte qui est copié à partir d'autres applications conserve les caractères de saut de ligne et de codage d'origine.  Par exemple, lorsque vous copiez du texte à partir du bloc\-notes et collez dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres qu'il avait dans le bloc\-notes.  
  
 Lorsque vous ouvrez un fichier qui comporte un caractère de saut de ligne différents, vous pouvez voir une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérentes doivent être normalisés et quel type de sauts de ligne à choisir.