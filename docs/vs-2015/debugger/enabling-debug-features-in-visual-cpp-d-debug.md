---
title: L’activation de fonctionnalités de débogage dans Visual C++ (-D_DEBUG) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67de755105f30ee4a88daeef26bc29bc9841ae39
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501938"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Activation des fonctionnalités de débogage dans Visual C++ (/D_DEBUG)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [l’activation des fonctionnalités de débogage dans Visual C++ (-D_DEBUG)](https://docs.microsoft.com/visualstudio/debugger/enabling-debug-features-in-visual-cpp-d-debug).  
  
Dans [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], fonctionnalités de débogage telles que les assertions sont activées lorsque vous compilez votre programme avec le symbole **_DEBUG** défini. Vous pouvez définir **_DEBUG** de deux manières :  
  
-   Spécifiez **#define _DEBUG** dans votre code source, ou  
  
-   Spécifiez le **/D_DEBUG** option du compilateur. (Si vous créez votre projet dans Visual Studio à l’aide des Assistants, **/D_DEBUG** est définie automatiquement dans la configuration Debug.)  
  
 Lorsque **_DEBUG** est défini, le compilateur compile les sections de code entourées par **#ifdef _DEBUG** et `#endif`.  
  
 La configuration Debug d'un programme MFC doit être liée à une version Debug de la bibliothèque MFC. Les fichiers d’en-tête MFC déterminent la version correcte de la bibliothèque MFC relier à l’aide basée sur les symboles que vous avez défini, tel que **_DEBUG** et **_UNICODE**. Pour plus d’informations, consultez [Versions de la bibliothèque MFC](http://msdn.microsoft.com/library/3d7a8ae1-e276-4cf8-ba63-360c2f85ad0e).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)



