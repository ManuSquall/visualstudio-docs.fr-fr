---
title: Activer et désactiver modifier & continuer | Microsoft Docs
description: Découvrez comment désactiver et activer modifier & continuer dans les options Visual Studio au moment du Design. Modifier &amp; Continuer ne fonctionne que dans les versions Debug.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/04/2018
ms.topic: how-to
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
ms.openlocfilehash: 02356a407acc97b60f05641359c32305323f162e
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903530"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Comment : activer et désactiver modifier & Continuer (C#, VB, C++)

Vous pouvez désactiver ou activer **modifier & continuer** dans la boîte de dialogue **options** de Visual Studio au moment du Design. **Modifier & continuer** fonctionne uniquement dans les versions Debug. Pour plus d’informations, consultez [Modifier et Continuer](../debugger/edit-and-continue.md).

Pour C++ natif, l’option **modifier & continuer** requiert l’utilisation de l' `/INCREMENTAL` option. Pour plus d’informations sur les spécifications de fonctionnalités en C++, consultez ce [billet de blog](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/) et [modifier & continuer (c++)](../debugger/edit-and-continue-visual-cpp.md).

**Pour activer ou désactiver modifier & Continuer :**

1. Si vous êtes dans une session de débogage, arrêtez le débogage (**Déboguer**  >  **arrêter le débogage** ou **MAJ** + **F5**).

1. Dans **Outils**  >  **options** > (ou options de **débogage**  >  ) > **débogage**  >  **général**, sélectionnez **Modifier & Continuer** dans le volet droit.

    > [!NOTE]
    > Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace](../debugger/intellitrace.md).

1. Pour le code C++, assurez-vous que l’option **activer le mode natif modifier & continuer** est sélectionnée et définissez les options supplémentaires :
    - **Appliquer les modifications à la poursuite de l’application (natif uniquement)**

      Si cette option est sélectionnée, Visual Studio compile et applique automatiquement les modifications de code lorsque vous continuez le débogage à partir d’un état d’arrêt. Dans le cas contraire, vous pouvez choisir d’appliquer les modifications à l’aide du **débogage**  >  **appliquer les modifications du code**.

    - **Signaler le code périmé (natif uniquement)**

      Si cette option est sélectionnée, les avertissements relatifs au code périmé s’affichent.

1. Cliquez sur **OK**.
