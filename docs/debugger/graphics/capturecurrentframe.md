---
title: CaptureCurrentFrame | Microsoft Docs
description: Utilisez la méthode CaptureCurrentFrame de la classe Vsgdbg, pour capturer le reste du frame actuel dans le fichier journal de graphisme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 793d86ac7d23fa209560222415dce50f4e5ac508
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727942"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Capture le reste du frame actuel dans le fichier journal de graphisme.

## <a name="syntax"></a>Syntaxe

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Notes
 Si une autre capture est actuellement en cours, telle qu’une capture qui a été démarrée par la `BeginCapture` fonction, cette capture est terminée et enregistrée dans le journal de graphisme sous la forme d’un frame distinct. Immédiatement après, Graphics Diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré sous la forme d’un frame distinct. La fin du frame actuel est marquée par un appel à present.

 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer les informations graphiques, autrement dit, vous devez avoir appelé [init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `CaptureCurrentFrame` .

## <a name="see-also"></a>Voir aussi
- [Init](init.md)
- [BeginCapture](begincapture.md)