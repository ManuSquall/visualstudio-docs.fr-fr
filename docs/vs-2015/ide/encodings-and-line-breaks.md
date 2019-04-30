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
ms.openlocfilehash: 6ceec5e44ade219f069e72f712129a137d70875f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437520"
---
# <a name="encodings-and-line-breaks"></a>Encodages et sauts de ligne
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans Visual Studio, vous pouvez utiliser les paramètres **Options d’enregistrement de fichier/avancées** pour déterminer le type de caractères de saut de ligne que vous souhaitez. Vous pouvez également modifier l’encodage d’un fichier avec les mêmes paramètres.  
  
> [!NOTE]
> Si vous avez certains types de paramètres de développement (Visual Basic, F#, développement web), vous pouvez ne pas voir **Options d’enregistrement avancées** dans le menu. Pour modifier vos paramètres (en spécifiant par exemple Général), ouvrez **Outils / Importation et exportation de paramètres**. Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Dans Visual Studio, les caractères suivants sont interprétés comme des sauts de ligne :  
  
- CRLF : Retour chariot + saut de ligne, caractères Unicode 000D + 000A  
  
- LF : Saut de ligne, caractère Unicode 000A  
  
- NEL : Ligne suivante, caractère Unicode 0085  
  
- LS : Séparateur de ligne, caractère Unicode 2028  
  
- PS : Séparateur de paragraphe, caractère Unicode 2029  
  
  Du texte copié à partir d’autres applications conserve les caractères d’encodage et de saut de ligne d’origine. Par exemple, lorsque vous copiez du texte à partir du Bloc-notes pour le coller dans un fichier texte dans Visual Studio, le texte a les mêmes paramètres que dans le Bloc-notes.  
  
  Lorsque vous ouvrez un fichier qui a des caractères de saut de ligne différents, vous pouvez voir une boîte de dialogue qui vous demande si les caractères de saut de ligne incohérents doivent être normalisés, ainsi que le type de saut de ligne à choisir.
