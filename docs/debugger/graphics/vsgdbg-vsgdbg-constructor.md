---
title: VsgDbg::VsgDbg (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b4c4c987bd0f44f6b8a4bad945d249aaf832fc57
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035274"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
Construit une instance de la `VsgDbg` classe avec ou sans la préparer le composant dans l’application de graphics diagnostics pour capturer et enregistrer des informations graphiques par défaut, en fonction du paramètre booléen spécifié activement.  
  
## <a name="syntax"></a>Syntaxe  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bDefaultInit`  
 `true` Pour spécifier que le composant dans l’application de graphics diagnostics doit être préparée à activement capturer et enregistrer des informations graphiques ; `false` pour spécifier que l’application ne doit pas être préparée activement capturer et enregistrer des informations graphiques pour l’instant.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le constructeur est appelé avec `bDefaultInit` définie sur `true`, le nom de fichier du fichier journal de graphisme est déterminé par la façon dont le `DONT_SAVE_VSGLOG_TO_TEMP` et `VSG_DEFAULT_RUN_FILENAME` définies avant les symboles du préprocesseur `vsgcapture.h` est inclus dans votre application.  
  
 Lorsque le constructeur est appelé avec `bDefaultInit` définie sur `false`, le composant dans l’application de graphics diagnostics peut être préparé à activement capturer et enregistrer des informations graphiques ultérieurement en appelant le `Init` (fonction).  
  
## <a name="see-also"></a>Voir aussi  
 [VsgDbg::~VsgDbg (destructeur)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)