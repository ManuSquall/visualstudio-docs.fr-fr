---
title: Fonctions de raccordement de bloc client | Microsoft Docs
description: Écrire une fonction de raccordement de bloc client pour valider ou signaler le contenu des données stockées dans des blocs _CLIENT_BLOCK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 720087e3c109c6dec4db06d993d0357dc1eddcd4
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729013"
---
# <a name="client-block-hook-functions"></a>Fonctions de raccordement de bloc client
Si vous voulez valider ou reporter le contenu des données stockées dans des blocs `_CLIENT_BLOCK`, vous pouvez écrire une fonction spécialement dans ce but. Cette fonction doit avoir un prototype similaire au suivant, défini dans CRTDBG.H :

```cpp
void YourClientDump(void *, size_t)
```

 En d’autres termes, votre fonction de raccordement doit accepter un pointeur **void** vers le début du bloc d’allocation, avec une valeur de type **size_t** indiquant la taille de l’allocation, et retourner `void`. Pour le reste, son contenu dépend de vous.

 Une fois que vous avez installé votre fonction de raccordement avec [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), elle est appelée à chaque vidage d’un bloc `_CLIENT_BLOCK`. Vous pouvez alors utiliser [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) pour obtenir des informations sur le type ou le sous-type des blocs ayant fait l’objet d’un vidage.

 Le pointeur vers votre fonction passé à `_CrtSetDumpClient` est du type **_CRT_DUMP_CLIENT**, comme défini dans CRTDBG.H :

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Voir aussi

- [Écriture de la fonction de raccordement de débogage](../debugger/debug-hook-function-writing.md)
- [Exemple de crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)