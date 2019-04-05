---
title: 'Procédure : Activer et désactiver Modifier & Continuer | Microsoft Docs'
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
ms.openlocfilehash: 0fe1af00bde865b98fb165efe109fe1bb5cabd49
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "59001081"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Procédure : Activer et désactiver Modifier & Continuer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez désactiver ou Activer Modifier & Continuer dans les **Options** boîte de dialogue au moment du design. Vous ne pouvez pas modifier ce paramètre pendant le débogage.  
  
 Modifier &amp; Continuer ne fonctionne que dans les versions Debug. Pour C++ natif, Modifier &amp; Continuer exige l'option /INCREMENTAL.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Pour activer ou désactiver Modifier &amp; Continuer  
  
1. Ouvrir la page options débogage (**Outils / Options / débogage**).  
  
2. Faites défiler jusqu'à **Modifier & Continuer** catégorie.  
  
3. Pour activer, sélectionnez le **Activer Modifier & Continuer** case à cocher. Pour désactiver, désactivez la case à cocher.  
  
   > [!NOTE]
   >  Si IntelliTrace est activé et si vous collectez des événements et des informations d’appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées. Pour plus d’informations, consultez [IntelliTrace configurer](http://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Cliquez sur **OK**.  
  
   Pour plus d’informations sur ces options, consultez [général, débogage, boîte de dialogue Options](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Modifier & Continuer](../debugger/edit-and-continue.md)
