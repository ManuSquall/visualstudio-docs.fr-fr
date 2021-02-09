---
title: VsgDbg::VsgDbg (Constructor) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 466c64f3b055eef3629f0f4666529f1be4247f42
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861333"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg, constructeur
Construit une instance de la `VsgDbg` classe avec ou sans préparer le composant dans l’application de Graphics Diagnostics pour capturer et enregistrer activement les informations graphiques par défaut, en fonction du paramètre booléen spécifié.

## <a name="syntax"></a>Syntaxe

```C++
VsgDbg(
  bDefaultInit
);
```

#### <a name="parameters"></a>Paramètres
 `bDefaultInit``true`pour spécifier que le composant dans l’application de Graphics Diagnostics doit être préparé pour capturer et enregistrer activement les informations graphiques ; `false` pour spécifier que l’application ne doit pas être préparée à capturer et enregistrer activement les informations graphiques pour l’instant.

## <a name="remarks"></a>Remarques
 Lorsque le constructeur est appelé avec la `bDefaultInit` valeur `true` , le nom de fichier du fichier journal de graphisme est déterminé par la façon dont les `DONT_SAVE_VSGLOG_TO_TEMP` `VSG_DEFAULT_RUN_FILENAME` symboles de préprocesseur et sont définis avant `vsgcapture.h` d’être inclus dans votre application.

 Lorsque le constructeur est appelé avec `bDefaultInit` défini sur `false` , le composant dans l’application de Graphics Diagnostics peut être préparé pour capturer et enregistrer activement les informations graphiques ultérieurement en appelant la `Init` fonction.

## <a name="see-also"></a>Voir aussi
- [VsgDbg::~VsgDbg, destructeur](vsgdbg-tilde-vsgdbg-destructor.md)
- [Init](init.md)
- [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)
- [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)