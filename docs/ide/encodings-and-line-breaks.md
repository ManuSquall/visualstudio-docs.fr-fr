---
title: "Encodages et sauts de ligne | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: fr-fr
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>Encodages et sauts de ligne
Dans Visual Studio, vous pouvez utiliser les paramètres **Options d’enregistrement de fichier/avancées** pour déterminer le type de caractères de saut de ligne que vous souhaitez. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.  
  
> [!NOTE]
>  Si vous avez certains types de paramètres de développement (Visual Basic, F#, développement web), vous pouvez ne pas voir **Options d’enregistrement avancées** dans le menu. Pour modifier vos paramètres (en spécifiant par exemple Général), ouvrez **Outils / Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Dans Visual Studio, les caractères suivants sont interprétés comme des sauts de ligne :  
  
-   CRLF : retour chariot + saut de ligne, caractères Unicode 000D + 000A  
  
-   LF : saut de ligne, caractère Unicode 000A  
  
-   NEL : ligne suivante, caractère Unicode 0085  
  
-   LS : séparateur de ligne, caractère Unicode 2028  
  
-   PS : séparateur de paragraphe, caractère Unicode 2029  
  
 Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.  
  
 Lorsque vous ouvrez un fichier qui a des caractères de saut de ligne différents, vous pouvez voir une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.
