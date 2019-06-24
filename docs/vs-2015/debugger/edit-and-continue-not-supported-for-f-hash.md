---
title: Modifier & Continuer non prise en charge pour F# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a4fef61335679e3f82d5916726981e003bf9c332
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62428455"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Opération Modifier &amp; Continuer non prise en charge pour F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'opération Modifier &amp; Continuer n'est pas prise en charge lorsque vous déboguez du code F#. La modification du code F# pendant une session de débogage est possible mais doit être évitée. Les modifications du code ne sont pas appliquées pendant la session de débogage. Par conséquent, toute modification apportée au code F# pendant le débogage provoque l'absence de concordance entre le code source et le code débogué.
