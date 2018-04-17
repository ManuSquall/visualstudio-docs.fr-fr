---
title: 'Comment : activer et désactiver modifier et continuer (c#, VB, C++) | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: c63f629bd0ba67156395b7bf1f1e142355ae9981
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-enable-and-disable-edit-and-continue-c-vb-c"></a>Comment : activer et désactiver modifier et continuer (c#, VB, C++)
Vous pouvez désactiver ou Activer Modifier & Continuer dans la **Options** boîte de dialogue au moment du design. Vous ne pouvez pas modifier ce paramètre pendant le débogage.  
  
Modifier & Continuer ne fonctionne que dans les versions Debug. Pour C++ natif, Modifier & Continuer exige l'option /INCREMENTAL. Pour plus d’informations sur les spécifications de fonctionnalités en C++, consultez ce [billet de blog](https://blogs.msdn.microsoft.com/vcblog/2016/07/01/c-edit-and-continue-in-visual-studio-2015-update-3/) et [Modifier & Continuer (Visual C++)](../debugger/edit-and-continue-visual-cpp.md).
  
#### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier & Continuer  
  
1.  Si vous êtes dans une session de débogage, arrêtez le débogage (**MAJ + F5**).

2.  Ouvrir la page options débogage (**Outils > Options > débogage**).
  
3.  Sélectionnez **général**et faites défiler jusqu'à **Modifier & Continuer** catégorie (volet droit).  
  
4.  Pour activer, activez la **Activer Modifier & Continuer** case à cocher. Pour désactiver, désactivez la case à cocher.  
  
    > [!NOTE]
    >  Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace](../debugger/intellitrace.md).

5. (C++) Pour activer, activez **activer modifier et continuer natif**. Pour désactiver, désactivez la case à cocher.

6. (C++) Définir des options supplémentaires pour le code natif.

    - **Appliquer les modifications en continuant (natif uniquement)**  
        Visual Studio compile et applique automatiquement les modifications de code en attente apportées lors de la poursuite du processus après un arrêt. Si non est sélectionné, vous pouvez choisir d’appliquer les modifications à l’aide de l’élément « Appliquer les modifications du Code » dans le menu Déboguer.  
  
    - **Signaler le code périmé (natif uniquement)**  
        Obtenez des avertissements concernant le code périmé. 
  
7.  Cliquez sur **OK**.    
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer](../debugger/edit-and-continue.md)