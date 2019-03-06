---
title: Encodages et sauts de ligne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 88f04720610bad5064f7f9d7a43beef2410b045f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54787464"
---
# <a name="encodings-and-line-breaks"></a>Encodages et sauts de ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser les paramètres **Options d’enregistrement de fichier/avancées** pour déterminer le type de caractères de saut de ligne que vous souhaitez. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.  
  
> [!NOTE]
>  Si vous avez certains types de paramètres de développement (Visual Basic, F#, développement web), vous pouvez ne pas voir **Options d’enregistrement avancées** dans le menu. Pour modifier vos paramètres (en spécifiant par exemple Général), ouvrez **Outils / Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Dans Visual Studio, les caractères suivants sont interprétés comme des sauts de ligne :  
  
- CRLF : retour chariot + saut de ligne, caractères Unicode 000D + 000A  
  
- LF : saut de ligne, caractère Unicode 000A  
  
- NEL : ligne suivante, caractère Unicode 0085  
  
- LS : séparateur de ligne, caractère Unicode 2028  
  
- PS : séparateur de paragraphe, caractère Unicode 2029  
  
  Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.  
  
  Lorsque vous ouvrez un fichier qui a des caractères de saut de ligne différents, vous pouvez voir une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.
