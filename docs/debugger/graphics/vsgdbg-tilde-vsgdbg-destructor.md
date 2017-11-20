---
title: "VsgDbg :: ~ VsgDbg (destructeur) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8d34fc9ac09f944fea44baff3ceea4a121a8009
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
Détruit une instance de la `VsgDbg` classe. Si les informations graphiques sont activement en cours d’enregistrement, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisés lors de la capture activement les informations graphiques sont libérées.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg::VsgDbg, constructeur](vsgdbg-vsgdbg-constructor.md)