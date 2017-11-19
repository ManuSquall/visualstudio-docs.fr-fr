---
title: "L’activation de fonctionnalités de débogage dans Visual C++ (-D_DEBUG) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /D_DEBUG compiler option [C++]
- debugging [C++], enabling debug features
- debugging [MFC], enabling debug features
- assertions, enabling debug features
- D_DEBUG compiler option
- MFC libraries, debug version
- debug builds, MFC
- _DEBUG macro
ms.assetid: 276e2254-7274-435e-ba4d-67fcef4f33bc
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b762f34df693ac3b5992d0b1e9c2ba4fa6fb8cb8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Activation des fonctionnalités de débogage dans Visual C++ (/D_DEBUG)
Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], fonctionnalités de débogage telles que les assertions sont activées lorsque vous compilez votre programme avec le symbole **_DEBUG** défini. Vous pouvez définir **_DEBUG** de deux manières :  
  
-   Spécifiez **#define _DEBUG** dans votre code source, ou  
  
-   Spécifiez le **/D_DEBUG** option du compilateur. (Si vous créez votre projet dans Visual Studio à l’aide des Assistants, **/D_DEBUG** est définie automatiquement dans la configuration Debug.)  
  
 Lorsque **_DEBUG** est défini, le compilateur compile les sections de code entourées par **#ifdef _DEBUG** et `#endif`.  
  
 La configuration Debug d'un programme MFC doit être liée à une version Debug de la bibliothèque MFC. Les fichiers d’en-tête MFC déterminent la version appropriée de la bibliothèque MFC à lier avec basé sur les symboles que vous avez définis, tels que **_DEBUG** et **_UNICODE**. Pour plus d’informations, consultez [Versions de bibliothèque MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)