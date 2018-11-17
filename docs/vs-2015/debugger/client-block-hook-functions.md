---
title: Fonctions de raccordement de bloc client | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 2b16dc9eaff974e98e411d4f49d8aed6f9f656e8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773936"
---
# <a name="client-block-hook-functions"></a>Fonctions de raccordement de bloc client
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but. Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 En d’autres termes, votre fonction de raccordement doit accepter un **void** pointeur vers le début du bloc d’allocation, avec une **size_t** type valeur qui indique la taille de l’allocation et de retourner `void`. Pour le reste, son contenu dépend de vous.  
  
 Une fois que vous avez installé votre fonction de raccordement avec [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), elle sera appelée chaque fois qu’un `_CLIENT_BLOCK` bloc. Vous pouvez ensuite utiliser [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) pour obtenir des informations sur le type ou le sous-type des blocs sauvegardées.  
  
 Le pointeur vers votre fonction que vous passez à `_CrtSetDumpClient` est de type **_CRT_DUMP_CLIENT**, tel que défini dans CRTDBG. H :  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Écriture de fonctions de raccordement de débogage](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2, exemple](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)



