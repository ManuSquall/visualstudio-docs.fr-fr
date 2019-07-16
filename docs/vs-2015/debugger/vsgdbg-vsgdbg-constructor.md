---
title: VsgDbg::VsgDbg (Constructor) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157439"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 [VsgDbg::~VsgDbg (destructeur)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
