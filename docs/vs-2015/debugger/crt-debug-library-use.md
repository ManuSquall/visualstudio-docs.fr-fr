---
title: Bibliothèque de débogage CRT utiliser | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697856"
---
# <a name="crt-debug-library-use"></a>Utilisation de la bibliothèque de débogage CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La bibliothèque Runtime C assure une prise en charge complète du débogage. Pour utiliser l’une des bibliothèques de débogage CRT, vous devez effectuer une liaison avec [/Debug](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) et compiler avec **/MDD**, **/MTD**ou **/LDD**.  
  
## <a name="remarks"></a>Notes  
 Les principales définitions et macros pour le débogage CRT se trouvent dans le fichier d'en-tête CRTDBG.h.  
  
 Les fonctions dans les bibliothèques de débogage CRT sont compilées avec des informations de débogage ([/Z7, /Zd, /Zi, /ZI (Format des informations de débogage)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) et sans optimisation. Certaines fonctions contiennent des assertions pour vérifier les paramètres qui leur sont passés ; en outre, le code source est fourni. Avec ce code source, vous pouvez effectuer un pas à pas détaillé dans les fonctions CRT pour vérifier qu'elles opèrent comme prévu et rechercher les paramètres ou les états de mémoire incorrects. (Une partie de la technologie CRT est propriétaire et ne fournit pas le code source pour la gestion des exceptions, la virgule flottante et quelques autres routines.)  
  
 Lorsque vous installez Visual C++, vous avez la possibilité d'installer le code source de la bibliothèque Runtime C sur votre disque dur. Si vous n'installez pas le code source, vous aurez besoin du CD-ROM pour un pas à pas détaillé dans les fonctions CRT.  
  
 Pour plus d’informations sur les différentes bibliothèques Runtime que vous pouvez utiliser, consultez [Bibliothèques Runtime C](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)   
 [/MD,/MT,/LD (utiliser la bibliothèque Runtime)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
