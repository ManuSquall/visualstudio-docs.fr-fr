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
ms.openlocfilehash: ec67013b41a5ec8876866044355534c42bfe2ee0
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56720729"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Capture le reste de l’image actuelle dans le fichier journal de graphiques.

## <a name="syntax"></a>Syntaxe

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Remarques
 Si une autre capture est actuellement en cours d’exécution, comme une capture qui a été démarrée par le `BeginCapture` (fonction) — cette capture est terminée et enregistrée dans le journal de graphisme en tant qu’un frame distinct. Immédiatement par la suite, graphics diagnostics commence à capturer le reste de l’image actuelle, qui est également enregistré comme une trame distincte. Fin de l’image actuelle est marquée par un appel à présenter.

 Pour capturer un frame, vous devez préparer votre application pour capturer et enregistrer des informations graphiques, autrement dit, vous devez appeler [Init](init.md) via une instance de la `VsgDbg` classe avant d’appeler `CaptureCurrentFrame`.

## <a name="see-also"></a>Voir aussi
- [Init](init.md)
- [BeginCapture](begincapture.md)