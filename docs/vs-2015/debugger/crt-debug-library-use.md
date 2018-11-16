---
title: Utilisation de la bibliothèque de débogage CRT | Microsoft Docs
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
manager: ghogen
ms.openlocfilehash: c6bba5b9c1b9d65c867176ac72c0641fac4cd286
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817644"
---
# <a name="crt-debug-library-use"></a>Utilisation de la bibliothèque de débogage CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La bibliothèque Runtime C assure une prise en charge complète du débogage. Pour utiliser une des bibliothèques de débogage CRT, vous devez le lier avec [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) et compilez avec **/MDd**, **/MTd**, ou **/LDd**.  
  
## <a name="remarks"></a>Notes  
 Les principales définitions et macros pour le débogage CRT se trouvent dans le fichier d'en-tête CRTDBG.h.  
  
 Les fonctions dans les bibliothèques de débogage CRT sont compilées avec les informations de débogage ([/Z7, / Zd, / Zi, /ZI (Format des informations de débogage)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) et sans optimisation. Certaines fonctions contiennent des assertions pour vérifier les paramètres qui leur sont passés ; en outre, le code source est fourni. Avec ce code source, vous pouvez effectuer un pas à pas détaillé dans les fonctions CRT pour vérifier qu'elles opèrent comme prévu et rechercher les paramètres ou les états de mémoire incorrects. (Une partie de la technologie CRT est propriétaire et ne fournit pas le code source pour la gestion des exceptions, la virgule flottante et quelques autres routines.)  
  
 Lorsque vous installez Visual C++, vous avez la possibilité d'installer le code source de la bibliothèque Runtime C sur votre disque dur. Si vous n'installez pas le code source, vous aurez besoin du CD-ROM pour un pas à pas détaillé dans les fonctions CRT.  
  
 Pour plus d’informations sur les différentes bibliothèques Runtime, vous pouvez utiliser, consultez [les bibliothèques Runtime C](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Utiliser la bibliothèque Runtime)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)



