---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736135"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Capture le reste du frame actuel dans le fichier journal de graphisme.

## <a name="syntax"></a>Syntaxe

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Notes
 Si une autre capture est actuellement en cours (par exemple, une capture qui a été démarrée par la fonction `BeginCapture`), cette capture est terminée et enregistrée dans le journal de graphisme sous la forme d’un frame distinct. Immédiatement après, Graphics Diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré sous la forme d’un frame distinct. La fin du frame actuel est marquée par un appel à present.

 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer les informations graphiques, autrement dit, vous devez avoir appelé [init](init.md) via une instance de la classe `VsgDbg` avant d’appeler `CaptureCurrentFrame`.

## <a name="see-also"></a>Voir aussi
- [Init](init.md)
- [BeginCapture](begincapture.md)