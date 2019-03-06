---
title: Copier (Capture par programmation) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56719078"
---
# <a name="copy-programmatic-capture"></a>Copier (capture par programmation)
Copie le contenu du fichier journal (.vsglog) tracé actif dans un nouveau fichier.

## <a name="syntax"></a>Syntaxe

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Paramètres
 `szNewVSGLog` Le nom de fichier du nouveau fichier journal graphics.

## <a name="remarks"></a>Remarques
 Pour copier les informations graphiques dans un nouveau fichier, doit déjà avoir capturé des informations graphiques ; Sinon, rien ne se produit.