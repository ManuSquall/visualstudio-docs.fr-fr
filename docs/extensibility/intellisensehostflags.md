---
title: IntelliSenseHostFlags | Microsoft Docs
description: L’énumération IntelliSenseHostFlags spécifie les indicateurs d’hôte IntelliSense. Cet article décrit les valeurs enum.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IntellisenseHostFlags
helpviewer_keywords:
- IntelliSense, IntellisenseHostFlags enumeration
- IntellisenseHostFlags enumeration
ms.assetid: 0930640b-eb84-48ef-a8f7-d4268f55c99c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: af4683dede8a57b2d42acdf357808b465efb1e8e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869503"
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

## <a name="requirements"></a>Configuration requise
 SingleFileeditor. idl

## <a name="see-also"></a>Voir aussi
- <xref:Microsoft.VisualStudio.TextManager.Interop>
