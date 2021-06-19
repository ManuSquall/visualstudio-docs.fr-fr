---
title: Boîte de dialogue Microsoft Visual Studio débogueur (exception levée) | Microsoft Docs
titleSuffix: ''
description: 'Découvrez ce qu’il faut faire lorsqu’une exception se produit et que votre programme doit gérer. Vous pouvez : 1) arrêter dans le débogueur ; 2) continuer ; ou 3) ignorer.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7a4b92a3ec5c6876fae3054b692ff46f26e82cd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387045"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Débogueur Microsoft Visual Studio (Exception levée) (boîte de dialogue)
Une exception s'est produite dans votre programme. Cette boîte de dialogue indique le type d'exception levé. Votre code doit gérer cette exception. Pour ce faire, vous avez le choix entre les options suivantes :

 **Arrêter** Permet à l’exécution de s’arrêter dans le débogueur. Le gestionnaire d'exceptions n'est pas appelé avant l'arrêt. Si vous poursuivez l'exécution après l'arrêt, le gestionnaire d'exceptions est appelé.

 **Continuer** Permet à l’exécution de se poursuivre, en donnant au gestionnaire d’exceptions la possibilité de gérer l’exception. Cette option n'est pas disponible pour certains types d'exceptions. **Continue** autorise l’application à continuer. Dans une application native, l'exception est de nouveau levée. Dans une application managée, cela entraîne l'arrêt du programme ou la gestion de l'exception par une application hôte.

> [!NOTE]
> Vous ne pouvez pas continuer l'exécution à la suite de la levée d'une exception non traitée dans du code managé. Si vous sélectionnez **Continue** après une exception non gérée dans du code managé, le débogage s’arrête.

 **Ignorer** Permet à l’exécution de se poursuivre sans appeler le gestionnaire d’exceptions. Comme le gestionnaire d'exceptions n'est pas appelé, il risque de s'ensuivre des conséquences indésirables, notamment de nouvelles exceptions et des erreurs. Cette option n'est pas disponible pour certains types d'exceptions.

## <a name="see-also"></a>Voir aussi
- [Gestion des exceptions avec le débogueur](../debugger/managing-exceptions-with-the-debugger.md)
- [Meilleures pratiques pour les exceptions](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Gestion des exceptions](/cpp/extensions/exception-handling-cpp-component-extensions)