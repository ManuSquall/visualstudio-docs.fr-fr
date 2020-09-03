---
title: Bibliothèque de débogage CRT utiliser | Microsoft Docs
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20aeee220bec600c2232286d18600b04201ad03b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72745607"
---
# <a name="crt-debug-library-use"></a>Utilisation de la bibliothèque de débogage CRT
La bibliothèque Runtime C assure une prise en charge complète du débogage. Pour utiliser l’une des bibliothèques de débogage CRT, vous devez effectuer une liaison avec [/Debug](/cpp/build/reference/debug-generate-debug-info) et compiler avec **/MDD**, **/MTD**ou **/LDD**.

## <a name="remarks"></a>Notes
 Les principales définitions et macros pour le débogage CRT se trouvent dans le fichier d'en-tête CRTDBG.h.

 Les fonctions dans les bibliothèques de débogage CRT sont compilées avec des informations de débogage ([/Z7, /Zd, /Zi, /ZI (Format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format)) et sans optimisation. Certaines fonctions contiennent des assertions pour vérifier les paramètres qui leur sont passés ; en outre, le code source est fourni. Avec ce code source, vous pouvez effectuer un pas à pas détaillé dans les fonctions CRT pour vérifier qu'elles opèrent comme prévu et rechercher les paramètres ou les états de mémoire incorrects. (Une partie de la technologie CRT est propriétaire et ne fournit pas le code source pour la gestion des exceptions, la virgule flottante et quelques autres routines.)

 Pour plus d’informations sur les différentes bibliothèques Runtime que vous pouvez utiliser, consultez [Bibliothèques Runtime C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Voir aussi

- [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)
- [/MD,/MT,/LD (utiliser la bibliothèque Runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library)