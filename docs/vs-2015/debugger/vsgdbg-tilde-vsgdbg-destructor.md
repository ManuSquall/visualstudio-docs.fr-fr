---
title: 'VsgDbg :: ~ VsgDbg (destructeur) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed5e53aee9bed8ee070011de1a44001b910066a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501305"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [VsgDbg :: ~ VsgDbg (destructeur)](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-tilde-vsgdbg-destructor).  
  
Détruit une instance de la `VsgDbg` classe. Si les informations graphiques sont activement en cours d’enregistrement, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisés lors de la capture activement les informations graphiques sont libérées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg::VsgDbg, constructeur](../debugger/vsgdbg-vsgdbg-constructor.md)



