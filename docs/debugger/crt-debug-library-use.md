---
title: Utilisation de la bibliothèque de débogage CRT | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 9434be46f357a97ad01f10ceec184ebe6c52eb43
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56624163"
---
# <a name="crt-debug-library-use"></a>Utilisation de la bibliothèque de débogage CRT
La bibliothèque Runtime C assure une prise en charge complète du débogage. Pour utiliser une des bibliothèques de débogage CRT, vous devez le lier avec [/DEBUG](/cpp/build/reference/debug-generate-debug-info) et compilez avec **/MDd**, **/MTd**, ou **/LDd**.

## <a name="remarks"></a>Remarques
 Les principales définitions et macros pour le débogage CRT se trouvent dans le fichier d'en-tête CRTDBG.h.

 Les fonctions dans les bibliothèques de débogage CRT sont compilées avec des informations de débogage ([/Z7, /Zd, /Zi, /ZI (Format des informations de débogage)](/cpp/build/reference/z7-zi-zi-debug-information-format)) et sans optimisation. Certaines fonctions contiennent des assertions pour vérifier les paramètres qui leur sont passés ; en outre, le code source est fourni. Avec ce code source, vous pouvez effectuer un pas à pas détaillé dans les fonctions CRT pour vérifier qu'elles opèrent comme prévu et rechercher les paramètres ou les états de mémoire incorrects. (Une partie de la technologie CRT est propriétaire et ne fournit pas le code source pour la gestion des exceptions, la virgule flottante et quelques autres routines.)

 Lorsque vous installez Visual C++, vous avez la possibilité d'installer le code source de la bibliothèque Runtime C sur votre disque dur. Si vous n'installez pas le code source, vous aurez besoin du CD-ROM pour un pas à pas détaillé dans les fonctions CRT.

 Pour plus d’informations sur les différentes bibliothèques Runtime que vous pouvez utiliser, consultez [Bibliothèques Runtime C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Voir aussi

- [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](/cpp/build/reference/md-mt-ld-use-run-time-library)