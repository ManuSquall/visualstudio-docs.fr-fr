---
title: "Activation des fonctionnalit&#233;s de d&#233;bogage dans Visual C++ (/D_DEBUG) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/D_DEBUG (option du compilateur C++)"
  - "_DEBUG (macro)"
  - "assertions, activer les fonctionnalités de débogage"
  - "D_DEBUG (option du compilateur)"
  - "versions debug, MFC"
  - "déboguer (C++), activer les fonctionnalités de débogage"
  - "déboguer (MFC), activer les fonctionnalités de débogage"
  - "bibliothèques MFC, versions debug"
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Activation des fonctionnalit&#233;s de d&#233;bogage dans Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)], les fonctionnalités de débogage telles que les assertions sont activées lorsque vous compilez votre programme à l'aide du symbole **\_DEBUG** défini.  Vous pouvez définir **\_DEBUG** de deux façons différentes :  
  
-   Spécifiez **\#define \_DEBUG** dans votre code source, ou  
  
-   Spécifiez l'option du compilateur **\/D\_DEBUG**. \(Si vous créez votre projet dans Visual Studio à l'aide d'Assistants, **\/D\_DEBUG**  est défini automatiquement dans la configuration Debug.\)  
  
 Lorsque **\_DEBUG** est défini, le compilateur compile les sections de code entourées par **\#ifdef \_DEBUG** et `#endif`.  
  
 La configuration Debug d'un programme MFC doit être liée à une version Debug de la bibliothèque MFC.  Les fichiers d'en\-tête MFC déterminent la version appropriée de la bibliothèque MFC à laquelle il faut se lier, en fonction des symboles que vous avez définis, par exemple **\_DEBUG** et **\_UNICODE**.  Pour plus d'informations, consultez [Versions de la bibliothèque MFC](/visual-cpp/mfc/mfc-library-versions).  
  
## Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres de projet pour une configuration Debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)