---
title: 'VsgDbg :: ~ VsgDbg (destructeur) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60dbd0a82bf5fc648982a7ab4a1d71854cfb27bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806722"
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



