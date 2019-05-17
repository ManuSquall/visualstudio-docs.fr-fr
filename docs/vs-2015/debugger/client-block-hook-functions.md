---
title: Fonctions de raccordement de bloc client | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65702324"
---
# <a name="client-block-hook-functions"></a>Fonctions de raccordement de bloc client
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but. Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En d’autres termes, votre fonction de raccordement doit accepter un pointeur **void** vers le début du bloc d’allocation, avec une valeur de type **size_t** indiquant la taille de l’allocation, et retourner `void`. Pour le reste, son contenu dépend de vous.  
  
 Une fois que vous avez installé votre fonction de raccordement avec [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), elle est appelée à chaque vidage d’un bloc `_CLIENT_BLOCK`. Vous pouvez alors utiliser [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) pour obtenir des informations sur le type ou le sous-type des blocs ayant fait l’objet d’un vidage.  
  
 Le pointeur vers votre fonction passé à `_CrtSetDumpClient` est du type **_CRT_DUMP_CLIENT**, comme défini dans CRTDBG.H :  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
