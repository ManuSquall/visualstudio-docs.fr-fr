---
title: 'La fonction Modifier & Continuer n’est pas prise en charge pour F # | Microsoft Docs'
description: 'Modifier & Continuer n’est pas pris en charge pour le débogage F #. Les modifications apportées au code pendant le débogage ne sont pas appliquées à la source, de sorte que le code en cours de débogage ne correspondra pas à la source.'
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863086"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Opération Modifier &amp; Continuer non prise en charge pour F# #
L'opération Modifier &amp; Continuer n'est pas prise en charge lorsque vous déboguez du code F#. La modification du code F# pendant une session de débogage est possible mais doit être évitée. Les modifications du code ne sont pas appliquées pendant la session de débogage. Par conséquent, toute modification apportée au code F# pendant le débogage provoque l'absence de concordance entre le code source et le code débogué.
