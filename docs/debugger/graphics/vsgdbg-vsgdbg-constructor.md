---
title: VsgDbg::VsgDbg (constructeur) | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7231e0cc5c9d5946fabe504c16813ea47b24bdbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
Construit une instance de la `VsgDbg` classe avec ou sans la préparer le composant dans l’application de graphics diagnostics pour activement capturer et enregistrer des informations graphiques par défaut, en fonction du paramètre booléen spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bDefaultInit`  
 `true`Pour spécifier que le composant dans l’application de graphics diagnostics doit être préparé à activement capturer et enregistrer des informations graphiques ; `false` pour spécifier que l’application ne doit pas être préparée activement capturer et enregistrer des informations graphiques pour l’instant.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le constructeur est appelé avec `bDefaultInit` la valeur `true`, le nom de fichier du fichier journal de graphisme est déterminé par la façon dont le `DONT_SAVE_VSGLOG_TO_TEMP` et `VSG_DEFAULT_RUN_FILENAME` symboles de préprocesseur sont définies avant `vsgcapture.h` est inclus dans votre application.  
  
 Lorsque le constructeur est appelé avec `bDefaultInit` la valeur `false`, le composant dans l’application de graphics diagnostics peut être préparé à activement capturer et enregistrer des informations graphiques ultérieurement en appelant le `Init` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg :: ~ VsgDbg (destructeur)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)