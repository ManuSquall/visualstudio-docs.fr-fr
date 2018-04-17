---
title: Fonctions de raccordement de bloc client | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 711f7de86617f6574427a65c6efcef62c558306b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="client-block-hook-functions"></a>Fonctions de raccordement de bloc client
Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but. Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En d’autres termes, votre fonction de raccordement doit accepter un **void** pointeur au début du bloc d’allocation, avec une **size_t** type valeur qui indique la taille de l’allocation et retourner `void`. Pour le reste, son contenu dépend de vous.  
  
 Une fois que vous avez installé votre fonction de raccordement avec [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), elle sera appelée chaque fois qu’un `_CLIENT_BLOCK` bloc. Vous pouvez ensuite utiliser [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) pour obtenir des informations sur le type ou le sous-type des blocs enregistrée représente.  
  
 Le pointeur vers votre fonction que vous passez à `_CrtSetDumpClient` est de type **_CRT_DUMP_CLIENT**, comme défini dans CRTDBG. H :  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)