---
title: 'Comment : activer et désactiver modifier & continuer | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 2c8486bdcd7bc737d3851eabd88734df4efd80b7
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430535"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Comment : activer et désactiver modifier & Continuer (C#, VB,) C++

Vous pouvez désactiver ou activer **modifier & continuer** dans la boîte de dialogue **options** de Visual Studio au moment du Design. **Modifier et Continuer** ne fonctionne que dans les versions Debug. Pour plus d’informations, consultez [Modifier et Continuer](../debugger/edit-and-continue.md).

Pour Native C++, **Modifier & Continuer** requiert l’utilisation de l’option `/INCREMENTAL`. Pour plus d’informations sur la configuration C++requise pour les fonctionnalités dans, consultez ce [billet de blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) et [Modifier &C++continuer ()](../debugger/edit-and-continue-visual-cpp.md).

**Pour activer ou désactiver modifier & Continuer :**

1. Si vous êtes dans une session de débogage, arrêtez le débogage (**Déboguer** > **arrêter le débogage** ou **Shift**+**F5**).

1. Dans **outils** > **options** > (ou **déboguer**les**options** > ) > **débogage** > **général**, sélectionnez **Modifier & Continuer** dans le volet droit.

    > [!NOTE]
    > Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace](../debugger/intellitrace.md).

1. Pour C++ code, vérifiez que l’option **activer Native modifier & Continuer** est sélectionnée et définissez les options supplémentaires :
    - **Appliquer les changements en continuant (natif uniquement)**

      Si cette option est sélectionnée, Visual Studio compile et applique automatiquement les modifications de code lorsque vous continuez le débogage à partir d’un état d’arrêt. Dans le cas contraire, vous pouvez choisir d’appliquer les modifications à l’aide de **Debug** > **appliquer les modifications du code**.

    - **Signaler le code périmé (natif uniquement)**

      Si cette option est sélectionnée, les avertissements relatifs au code périmé s’affichent.

1. Cliquez sur **OK**.
