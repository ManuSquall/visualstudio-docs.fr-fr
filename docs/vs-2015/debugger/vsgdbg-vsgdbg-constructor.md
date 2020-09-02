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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157439"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Construit une instance de la `VsgDbg` classe avec ou sans préparer le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques par défaut, en fonction du paramètre booléen spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bDefaultInit`  
 `true` pour spécifier que le composant dans l’application de Graphics Diagnostics doit être préparé pour capturer et enregistrer activement les informations graphiques ; `false` pour spécifier que l’application ne doit pas être préparée à capturer et enregistrer activement les informations graphiques pour l’instant.  
  
## <a name="remarks"></a>Notes  
 Lorsque le constructeur est appelé avec la `bDefaultInit` valeur `true` , le nom de fichier du fichier journal de graphisme est déterminé par la façon dont les `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` symboles de préprocesseur et sont définis avant `vsgcapture.h` d’être inclus dans votre application.  
  
 Lorsque le constructeur est appelé avec `bDefaultInit` défini sur `false` , le composant dans l’application de Graphics Diagnostics peut être préparé pour capturer et enregistrer activement les informations graphiques ultérieurement en appelant la `Init` fonction.  
  
## <a name="see-also"></a>Voir aussi  
 [Vsgdbg, :: ~ Vsgdbg, (destructeur)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Rein](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
