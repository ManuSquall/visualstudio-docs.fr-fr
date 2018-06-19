---
title: Représentations DateTime et TimeSpan Windows Runtime | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime dates and times
- TimeSpan [JavaScript]
- DateTime [JavaScript]
ms.assetid: 9743e9ac-9054-463e-8264-427183e4905f
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3d7c394b57eb0215e3dff857d935b367e602c2b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
ms.locfileid: "24571419"
---
# <a name="windows-runtime-datetime-and-timespan-representations"></a>Représentations DateTime et TimeSpan Windows Runtime
La représentation JavaScript des dates et des heures diffère de la version Windows Runtime. La structure [DateTime](http://msdn.microsoft.com/library/windows/apps/windows.foundation.datetime.aspx) Windows Runtime est représentée en JavaScript comme une [Date](../javascript/reference/date-object-javascript.md) avec un magasin de stockage correspondant aux données `DateTime` (et avec une plage et une précision différentes de l’objet `Date` en JavaScript). Si vous modifiez cet objet `Date` personnalisé, il devient un objet `Date` JavaScript standard et perd sa précision. Les valeurs `Date` en JavaScript peuvent être passées à un objet Windows Runtime `DateTime` et leur plage sera vérifiée, ce qui peut générer des exceptions de marshaling.  
  
 La structure [TimeSpan](http://msdn.microsoft.com/en-us/c5defb66-819c-4796-85b5-07ed249a5d86) Windows Runtime est convertie en millisecondes et retournée sous la forme d’un nombre JavaScript.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de Windows Runtime dans JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)