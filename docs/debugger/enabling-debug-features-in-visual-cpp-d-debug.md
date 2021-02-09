---
title: Activation des fonctionnalités de débogage dans les projets C++ (-D_DEBUG) | Microsoft Docs
description: Dans Visual C++ vous activez les fonctionnalités de débogage en définissant _DEBUG. Apprenez à effectuer cette opération et découvrez comment lier un programme MFC pour le déboguer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: c0a8941fbda263ce3a2345a135594d2f9eec87e9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871895"
---
# <a name="enabling-debug-features-in-c-projects-d_debug"></a>Activation des fonctionnalités de débogage dans les projets C++ (/D_DEBUG)
En [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], les fonctionnalités de débogage comme les assertions sont activées quand vous compilez votre programme avec le symbole **_DEBUG** défini. Vous pouvez définir **_DEBUG** de deux façons différentes :

- Spécifiez **#define _DEBUG** dans votre code source, ou

- Spécifiez l’option du compilateur **/D_DEBUG**. (Si vous créez votre projet dans Visual Studio à l’aide d’Assistants, **/D_DEBUG** est défini automatiquement dans la configuration Debug.)

  Quand **_DEBUG** est défini, le compilateur compile les sections de code entourées par **#ifdef _DEBUG** et `#endif`.

  La configuration Debug d'un programme MFC doit être liée à une version Debug de la bibliothèque MFC. Les fichiers d’en-tête MFC déterminent la version appropriée de la bibliothèque MFC à laquelle il faut se lier, en fonction des symboles que vous avez définis, par exemple **_DEBUG** et **_UNICODE**. Pour plus d’informations, consultez [Versions de la bibliothèque MFC](/cpp/mfc/mfc-library-versions).

## <a name="see-also"></a>Voir aussi
- [Débogage du code natif](../debugger/debugging-native-code.md)
- [Paramètres de projet pour une configuration Debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)