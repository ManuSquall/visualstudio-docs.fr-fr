---
title: 'Débogage de F # | Microsoft Docs'
description: 'Passez en revue la liste des différences entre le débogage de F # et le débogage d’autres langages managés dans Visual Studio.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d2fed2765d04fa55c790afb7251a24b98a4d74f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872623"
---
# <a name="debugging-f"></a>Débogage de F\#
Le débogage de F# est semblable au débogage de tout langage managé, à quelques exceptions près :

- La fenêtre **Automatique** n’affiche pas les variables F#.

- L'opération Modifier &amp; Continuer n'est pas prise en charge pour F# La modification du code F# pendant une session de débogage est possible mais doit être évitée. Dans la mesure où les modifications du code ne sont pas appliquées pendant la session de débogage, le fait de modifier le code F# lors du débogage provoquera une incompatibilité entre le code source et le code débogué.

- Le débogueur ne reconnaît pas les expressions F#. Pour entrer une expression dans une fenêtre du débogueur ou une boîte de dialogue lors du débogage de F#, vous devez traduire l'expression en syntaxe C#. Lorsque vous traduisez une expression F# en syntaxe C#, assurez-vous que C# utilise == comme opérateur de comparaison d'égalité et que F# utilise un signe = unique.

## <a name="see-also"></a>Voir aussi
- [Débogage du code managé](../debugger/debugging-managed-code.md)
