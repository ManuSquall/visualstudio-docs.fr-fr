---
title: 'Vsgdbg, :: ~ Vsgdbg, (destructeur) | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200299"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg, destructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Détruit une instance de la `VsgDbg` classe. Si des informations graphiques sont activement enregistrées, le fichier journal de graphisme est finalisé et fermé, et les ressources qui ont été utilisées lors de la capture active des informations graphiques sont publiées.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg::VsgDbg, constructeur](../debugger/vsgdbg-vsgdbg-constructor.md)
