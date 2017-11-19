---
title: "Débogage de F # | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51eaed204db7b50e75a18dfac104a00546770abc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-f"></a>Débogage de F#
Le débogage de F# est semblable au débogage de tout langage managé, à quelques exceptions près :  
  
-   Le **automatique** fenêtre n’affiche pas les variables F #.  
  
-   L'opération Modifier & Continuer n'est pas prise en charge pour F# La modification du code F# pendant une session de débogage est possible mais doit être évitée. Dans la mesure où les modifications du code ne sont pas appliquées pendant la session de débogage, le fait de modifier le code F# lors du débogage provoquera une incompatibilité entre le code source et le code débogué.  
  
-   Le débogueur ne reconnaît pas les expressions F#. Pour entrer une expression dans une fenêtre du débogueur ou une boîte de dialogue lors du débogage de F#, vous devez traduire l'expression en syntaxe C#. Lorsque vous traduisez une expression F# en syntaxe C#, assurez-vous que C# utilise == comme opérateur de comparaison d'égalité et que F# utilise un signe = unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code managé](../debugger/debugging-managed-code.md)
