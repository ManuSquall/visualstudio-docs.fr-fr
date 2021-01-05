---
title: Copier (capture par programmation) | Microsoft Docs
description: Utilisez la méthode Copy de la classe Vsgdbg, pour copier le contenu du fichier journal Graphics (. vsglog) actif dans un nouveau fichier.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 126b1d7a2fa9064a343e7eadbe83dd1eeecccb83
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97727842"
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

## <a name="remarks"></a>Remarques
 Pour copier les informations graphiques dans un nouveau fichier, vous devez déjà avoir capturé des informations graphiques. dans le cas contraire, rien ne se passe.