---
title: L’activation de fonctionnalités de débogage dans Visual C++ (-D_DEBUG) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: 772467caf74a381fc2ef5cc74e8e31bf2ff0503c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949615"
---
# <a name="enabling-debug-features-in-visual-c-ddebug"></a>Activation des fonctionnalités de débogage dans Visual C++ (/D_DEBUG)
Dans [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], fonctionnalités de débogage telles que les assertions sont activées lorsque vous compilez votre programme avec le symbole **_DEBUG** défini. Vous pouvez définir **_DEBUG** de deux manières :  
  
- Spécifiez **#define _DEBUG** dans votre code source, ou  
  
- Spécifiez le **/D_DEBUG** option du compilateur. (Si vous créez votre projet dans Visual Studio à l’aide des Assistants, **/D_DEBUG** est définie automatiquement dans la configuration Debug.)  
  
  Lorsque **_DEBUG** est défini, le compilateur compile les sections de code entourées par **#ifdef _DEBUG** et `#endif`.  
  
  La configuration Debug d'un programme MFC doit être liée à une version Debug de la bibliothèque MFC. Les fichiers d’en-tête MFC déterminent la version correcte de la bibliothèque MFC relier à l’aide basée sur les symboles que vous avez défini, tel que **_DEBUG** et **_UNICODE**. Pour plus d’informations, consultez [Versions de la bibliothèque MFC](/cpp/mfc/mfc-library-versions).  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage du code natif](../debugger/debugging-native-code.md)   
 [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)