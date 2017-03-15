---
title: "Utilisation de la biblioth&#232;que de d&#233;bogage CRT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.debug.runtime"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "/DEBUG (option de l'Éditeur de liens C++)"
  - "/LDd (fonction du compilateur C++)"
  - "/MDd (option du compilateur C++)"
  - "/MTd (option du compilateur C++)"
  - "crtdbg.h (fichier)"
  - "bibliothèque de débogage"
  - "DEBUG (option de l'Éditeur de liens C++)"
  - "déboguer (CRT), bibliothèque de débogage CRT"
  - "LDd (fonction du compilateur C++)"
  - "bibliothèques, bibliothèque de débogage CRT"
  - "MDd (option du compilateur C++)"
  - "MTd (option du compilateur C++)"
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilisation de la biblioth&#232;que de d&#233;bogage CRT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La bibliothèque Runtime C assure une prise en charge complète du débogage.  Pour utiliser l'une des bibliothèques de débogage CRT, vous devez effectuer une liaison avec [\/DEBUG](/visual-cpp/build/reference/debug-generate-debug-info) et une compilation avec **\/MDd**, **\/MTd** ou **\/LDd**.  
  
## Remarques  
 Les principales définitions et macros pour le débogage CRT se trouvent dans le fichier d'en\-tête CRTDBG.h.  
  
 Les fonctions dans les bibliothèques de débogage CRT sont compilées avec des informations de débogage \([\/Z7, \/Zd, \/Zi, \/ZI \(Format des informations de débogage\)](/visual-cpp/build/reference/z7-zi-zi-debug-information-format)\) et sans optimisation.  Certaines fonctions contiennent des assertions pour vérifier les paramètres qui leur sont passés ; en outre, le code source est fourni.  Avec ce code source, vous pouvez effectuer un pas à pas détaillé dans les fonctions CRT pour vérifier qu'elles opèrent comme prévu et rechercher les paramètres ou les états de mémoire incorrects. \(Une partie de la technologie CRT est propriétaire et ne fournit pas le code source pour la gestion des exceptions, la virgule flottante et quelques autres routines.\)  
  
 Lorsque vous installez Visual C\+\+, vous avez la possibilité d'installer le code source de la bibliothèque Runtime C sur votre disque dur.  Si vous n'installez pas le code source, vous aurez besoin du CD\-ROM pour un pas à pas détaillé dans les fonctions CRT.  
  
 Pour plus d'informations sur les différentes bibliothèques Runtime que vous pouvez utiliser, consultez [Bibliothèques Runtime C](/visual-cpp/c-runtime-library/crt-library-features).  
  
## Voir aussi  
 [Techniques de débogage CRT](../debugger/crt-debugging-techniques.md)   
 [\/MD, \/MT, \/LD \(Utiliser la bibliothèque Runtime\)](/visual-cpp/build/reference/md-mt-ld-use-run-time-library)