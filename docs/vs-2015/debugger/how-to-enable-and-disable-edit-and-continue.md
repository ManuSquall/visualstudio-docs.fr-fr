---
title: 'Comment : activer et désactiver Modifier & Continuer | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57a9ec8b8e25da6edb36e1983e45f7bb78251208
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47500924"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Comment : activer et désactiver Modifier & Continuer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : activer et désactiver Modifier & Continuer](https://docs.microsoft.com/visualstudio/debugger/how-to-enable-and-disable-edit-and-continue).  
  
Vous pouvez désactiver ou Activer Modifier & Continuer dans les **Options** boîte de dialogue au moment du design. Vous ne pouvez pas modifier ce paramètre pendant le débogage.  
  
 Modifier & Continuer ne fonctionne que dans les versions Debug. Pour C++ natif, Modifier & Continuer exige l'option /INCREMENTAL.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier & Continuer  
  
1.  Ouvrir la page options débogage (**Outils / Options / débogage**).  
  
2.  Faites défiler jusqu'à **Modifier & Continuer** catégorie.  
  
3.  Pour activer, sélectionnez le **Activer Modifier & Continuer** case à cocher. Pour désactiver, désactivez la case à cocher.  
  
    > [!NOTE]
    >  Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace configurer](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Cliquez sur **OK**.  
  
 Pour plus d’informations sur ces options, consultez [général, débogage, boîte de dialogue Options](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer](../debugger/edit-and-continue.md)



