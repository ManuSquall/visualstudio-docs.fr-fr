---
title: IntelliSenseHostFlags | Microsoft Docs
description: L’énumération IntelliSenseHostFlags spécifie les indicateurs d’hôte IntelliSense. Cet article décrit les valeurs enum.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 33345f86c69d0faeaa5863534e21eca5ecc176cc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902616"
---
# <a name="intellisensehostflags"></a>IntelliSenseHostFlags
Spécifie les indicateurs d'hôte IntelliSense.

## <a name="syntax"></a>Syntaxe

```cpp
enum IntellisenseHostFlags
{
    IHF_READONLYCONTEXT      = 0x00000001
    IHF_NOSEPARATESUBJECT    = 0x00000002
    IHF_SINGLELINESUBJECT    = 0x00000004
    IHF_FORCECOMMITTOCONTEXT = 0x00000008
    IHF_OVERTYPE             = 0x00000010
};
```

### <a name="parameters"></a>Paramètres

|Membres|Description|
|-------------|-----------------|
|`IHF_READONLYCONTEXT`|La mémoire tampon de contexte est en lecture seule.|
|`IHF_NOSEPARATESUBJECT`|Aucun texte d’objet. La mémoire tampon de contexte contient IntelliSense-Target (implique `!IHF_READONLYCONTEXT` ).|
|`IHF_SINGLELINESUBJECT`|Le texte de l’objet ne prend pas en charge plusieurs lignes.|
|`IHF_FORCECOMMITTOCONTEXT`|Comme pour `CanCommitIntoReadOnlyBuffer`.|
|`IHF_OVERTYPE`|La modification (dans l’objet ou le contexte) doit être effectuée en mode de Refrappe.|

## <a name="requirements"></a>Spécifications
 SingleFileeditor. idl

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop>
