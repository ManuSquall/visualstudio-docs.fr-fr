---
title: 'Comment : activer et désactiver modifier & continuer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65689265"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Comment : activer et désactiver Modifier &amp; Continuer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez désactiver ou activer modifier & continuer dans la boîte de dialogue **options** au moment de la conception. Vous ne pouvez pas modifier ce paramètre pendant le débogage.  
  
 Modifier &amp; Continuer ne fonctionne que dans les versions Debug. Pour C++ natif, Modifier &amp; Continuer exige l'option /INCREMENTAL.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier &amp; Continuer  
  
1. Ouvrez la page Options de débogage (**Outils/Options/débogage**).  
  
2. Faites défiler jusqu’à la catégorie **modifier & continuer** .  
  
3. Pour activer, activez la case à cocher **activer modifier et continuer** . Pour désactiver, désactivez la case à cocher.  
  
   > [!NOTE]
   > Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [configurer IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Cliquez sur **OK**.  
  
   Pour plus d’informations sur ces options, consultez [général, débogage, boîte de dialogue Options](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier &amp; Continuer](../debugger/edit-and-continue.md)
