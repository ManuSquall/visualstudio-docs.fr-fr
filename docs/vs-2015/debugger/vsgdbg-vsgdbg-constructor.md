---
title: VsgDbg::VsgDbg (constructeur) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2a35443dbf4fc413908c61e989d2138122c0991
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47503252"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [VsgDbg::VsgDbg (constructeur)](https://docs.microsoft.com/visualstudio/debugger/graphics/vsgdbg-vsgdbg-constructor).  
  
Construit une instance de la `VsgDbg` classe avec ou sans la préparer le composant dans l’application de graphics diagnostics pour capturer et enregistrer des informations graphiques par défaut, en fonction du paramètre booléen spécifié activement.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bDefaultInit`  
 `true` Pour spécifier que le composant dans l’application de graphics diagnostics doit être préparée à activement capturer et enregistrer des informations graphiques ; `false` pour spécifier que l’application ne doit pas être préparée activement capturer et enregistrer des informations graphiques pour l’instant.  
  
## <a name="remarks"></a>Notes  
 Lorsque le constructeur est appelé avec `bDefaultInit` définie sur `true`, le nom de fichier du fichier journal de graphisme est déterminé par la façon dont le `DONT_SAVE_VSGLOG_TO_TEMP` et `VSG_DEFAULT_RUN_FILENAME` définies avant les symboles du préprocesseur `vsgcapture.h` est inclus dans votre application.  
  
 Lorsque le constructeur est appelé avec `bDefaultInit` définie sur `false`, le composant dans l’application de graphics diagnostics peut être préparé à activement capturer et enregistrer des informations graphiques ultérieurement en appelant le `Init` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg :: ~ VsgDbg (destructeur)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



