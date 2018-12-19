---
title: 'Procédure : Activer et désactiver Modifier & Continuer | Microsoft Docs'
ms.custom: seodec18
ms.date: 10/04/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 0b5fbc7ee0f2d85c72ccda75bc2e8531419d52e3
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051385"
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Procédure : Activer et désactiver Modifier & Continuer (C#, VB, C++)

Vous pouvez activer ou désactiver **Modifier & Continuer** dans Visual Studio **Options** boîte de dialogue au moment du design. **Modifier et Continuer** ne fonctionne que dans les versions Debug. Pour plus d’informations, consultez [Modifier et Continuer](../debugger/edit-and-continue.md). 
  
Pour C++ natif, **Modifier & Continuer** nécessite que vous utilisiez le `/INCREMENTAL` option. Pour plus d’informations sur les fonctionnalités requises en C++, consultez ce [billet de blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) et [Modifier & Continuer (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
**Pour activer ou désactiver Modifier & Continuer :**  
  
1.  Si vous êtes dans une session de débogage, arrêtez le débogage (**déboguer** > **arrêter le débogage** ou **MAJ**+**F5**) .

1.  Dans **outils** > **Options** > (ou **déboguer** > **Options**) > **dedébogage**  >  **Général**, sélectionnez **Modifier & Continuer** dans le volet droit.  
  
    > [!NOTE]
    >  Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace](../debugger/intellitrace.md).
    
1.  Pour le code C++, assurez-vous que **activer modifier et continuer natif** est sélectionné et définissez les options supplémentaires :
    - **Appliquer les changements en continuant (natif uniquement)**  
      
      Si sélectionné, Visual Studio compile automatiquement et applique les modifications du code lorsque vous continuez le débogage à partir d’un état d’arrêt. Sinon, vous pouvez choisir d’appliquer les modifications à l’aide de **déboguer** > **appliquer les modifications du Code**.  
      
    - **Signaler le code périmé (natif uniquement)**  
      
      Si sélectionné, d’avertissements concernant le code périmé. 
  
1.  Cliquez sur **OK**.    
