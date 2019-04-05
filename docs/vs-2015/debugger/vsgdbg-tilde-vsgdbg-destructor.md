---
title: 'VsgDbg :: ~ VsgDbg (destructeur) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58949745"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Détruit une instance de la `VsgDbg` classe. Si les informations graphiques sont activement en cours d’enregistrement, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisés lors de la capture activement les informations graphiques sont libérées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg::VsgDbg, constructeur](../debugger/vsgdbg-vsgdbg-constructor.md)
