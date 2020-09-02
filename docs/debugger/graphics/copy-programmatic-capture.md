---
title: Copier (capture par programmation) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3a888605cfae6b5430782defd198f83988c31870
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62895952"
---
# <a name="copy-programmatic-capture"></a>Copier (capture par programmation)
Copie le contenu du fichier journal de graphisme actif (. vsglog) dans un nouveau fichier.

## <a name="syntax"></a>Syntaxe

```C++
void Copy(
  wchar_t const * szNewVSGLog
);
```

#### <a name="parameters"></a>Paramètres
 `szNewVSGLog` Nom de fichier du nouveau fichier journal de graphisme.

## <a name="remarks"></a>Notes
 Pour copier les informations graphiques dans un nouveau fichier, vous devez déjà avoir capturé des informations graphiques. dans le cas contraire, rien ne se passe.