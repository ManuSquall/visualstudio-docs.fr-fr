---
title: 'La fonction Modifier & Continuer n’est pas prise en charge pour F # | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ceb0ca767b1ac6364e103925fb86ed639c3d321d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62851162"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Opération Modifier &amp; Continuer non prise en charge pour F# #
L'opération Modifier &amp; Continuer n'est pas prise en charge lorsque vous déboguez du code F#. La modification du code F# pendant une session de débogage est possible mais doit être évitée. Les modifications du code ne sont pas appliquées pendant la session de débogage. Par conséquent, toute modification apportée au code F# pendant le débogage provoque l'absence de concordance entre le code source et le code débogué.
